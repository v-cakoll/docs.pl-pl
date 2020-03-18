---
title: Nazwy zestawów
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 7a1a4d2512ebb002a3153fe2d51f47157136744d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733102"
---
# <a name="assembly-names"></a>Nazwy zestawów
Nazwa zestawu jest przechowywana w metadanych i ma znaczący wpływ na zakres zestawu i wykorzystania przez aplikację. Zestaw o silnej nazwie ma w pełni kwalifikowaną nazwę, która zawiera nazwę zestawu, kulturę, klucz publiczny i numer wersji. Jest to często określane jako nazwa wyświetlana, a dla załadowanych zestawów można uzyskać za pomocą <xref:System.Reflection.Assembly.FullName%2A> właściwości.

 Czas wykonywania używa tych informacji, aby zlokalizować zestaw i odróżnić go od innych zestawów o tej samej nazwie. Na przykład zestaw o silnej nazwie może `myTypes` mieć następującą w pełni kwalifikowaną nazwę:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> Architektura procesora jest dodawana do tożsamości zestawu w wersji .NET Framework 2.0, aby umożliwić wersje zestawów specyficzne dla procesora. Można utworzyć wersje zestawu, którego tożsamość różni się tylko architekturą procesora, na przykład wersjami 32-bitowymi i 64-bitowymi specyficznymi dla procesora. Architektura procesora nie jest wymagana dla silnych nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 W tym przykładzie w pełni kwalifikowana `myTypes` nazwa wskazuje, że zestaw ma silną nazwę z tokenem klucza publicznego, ma wartość kultury dla języka angielskiego amerykańskiego i ma numer wersji 1.0.1234.0. Jego architektura procesora jest "msil", co oznacza, że będzie just-in-time (JIT) skompilowany do kodu 32-bitowego lub 64-bitowego w zależności od systemu operacyjnego i procesora.

 Kod, który żąda typów w zestawie musi używać w pełni kwalifikowanej nazwy zestawu. Jest to nazywane w pełni kwalifikowane wiązanie. Częściowe powiązanie, które określa tylko nazwę zestawu, nie jest dozwolone podczas odwoływania się do zestawów w .NET Framework.

 Wszystkie odwołania do zestawu, które tworzą .NET Framework musi również zawierać w pełni kwalifikowaną nazwę zestawu. Na przykład odwołanie do zestawu System.Data .NET Framework dla wersji 1.0 będzie zawierać:

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 Należy zauważyć, że wersja odpowiada numer wersji wszystkich zestawów .NET Framework, które dostarczane z .NET Framework w wersji 1.0. W przypadku zestawów .NET Framework wartość kultury jest zawsze neutralna, a klucz publiczny jest taki sam, jak pokazano w powyższym przykładzie.

 Na przykład, aby dodać odwołanie do zestawu w pliku konfiguracji w celu skonfigurowania odbiornika śledzenia, należy dołączyć w pełni kwalifikowaną nazwę zestawu systemu .NET Framework:

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> Środowiska uruchomieniowego traktuje nazwy zestawów jako wielkość liter podczas wiązania z zestawem, ale zachowuje niezależnie od przypadku jest używany w nazwie zestawu. Kilka narzędzi w zestawie Windows SDK obsługuje nazwy zestawów jako rozróżniające wielkość liter. Aby uzyskać najlepsze wyniki, zarządzaj nazwami zestawów tak, jakby były uwzględniane wielkości liter.

## <a name="name-application-components"></a>Składniki aplikacji name
 Program runtime nie bierze pod uwagę nazwę pliku podczas określania tożsamości zestawu. Tożsamość zestawu, który składa się z nazwy zestawu, wersja, kultura i silna nazwa, musi być jasne dla czasu wykonywania.

 Na przykład jeśli masz zestaw o nazwie *myAssembly.exe,* który odwołuje się do zestawu o nazwie *myAssembly.dll*, powiązanie występuje poprawnie, jeśli wykonasz *myAssembly.exe*. Jeśli jednak inna aplikacja wykonuje *myAssembly.exe* przy użyciu <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>tej `myAssembly` metody, czas uruchomieniowy określa, `myAssembly`że jest już załadowany, gdy *myAssembly.exe* żąda powiązania z . W takim przypadku *myAssembly.dll* nigdy nie jest ładowany. Ponieważ *myAssembly.exe* nie zawiera żądanego <xref:System.TypeLoadException> typu, występuje.

 Aby uniknąć tego problemu, upewnij się, że zestawy, które tworzą aplikację nie mają tej samej nazwy zestawu lub zestawy o tej samej nazwie w różnych katalogach.

> [!NOTE]
> W platformie .NET Framework, jeśli zestaw o silnej nazwie zostanie umieszczony w globalnej pamięci podręcznej zestawów, nazwa pliku zestawu musi być zgodna z nazwą zestawu, nie wliczając rozszerzenia nazwy pliku, takiego jak *.exe* lub *.dll*. Na przykład jeśli nazwą pliku zestawu jest *myAssembly.dll,* nazwa `myAssembly`zestawu musi być . Zestawy prywatne wdrożone tylko w katalogu aplikacji głównej mogą mieć nazwę zestawu inną niż nazwa pliku.

## <a name="see-also"></a>Zobacz też

- [Jak: Określić w pełni kwalifikowaną nazwę zestawu](find-fully-qualified-name.md)
- [Tworzenie zestawów](create.md)
- [Zestawy o silnych nazwach](strong-named.md)
- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Jak program runtime lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
