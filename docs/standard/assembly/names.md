---
title: Nazwy zestawów
description: Dowiedz się więcej o nazwach zestawów .NET i ich wpływie na zakres zestawu i użyciu aplikacji, a następnie Dowiedz się więcej na temat właściwości FullName.
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: 5a499f4f04c84de8d6542d7107d7a707b808e47f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379884"
---
# <a name="assembly-names"></a>Nazwy zestawów
Nazwa zestawu jest przechowywana w metadanych i ma znaczny wpływ na zakres zestawu i użycie przez aplikację. Zestaw o silnej nazwie ma w pełni kwalifikowaną nazwę, która zawiera nazwę zestawu, kulturę, klucz publiczny i numer wersji. Jest to często określane jako nazwa wyświetlana, a dla załadowanych zestawów można uzyskać za pomocą <xref:System.Reflection.Assembly.FullName%2A> właściwości.

 Środowisko uruchomieniowe używa tych informacji do lokalizowania zestawu i odróżnienia go od innych zestawów o tej samej nazwie. Na przykład zestaw o silnej nazwie `myTypes` może mieć następującą w pełni kwalifikowaną nazwę:

```
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil
```

> [!NOTE]
> Architektura procesora jest dodawana do tożsamości zestawu w .NET Framework w wersji 2,0, aby zezwolić na wersje zestawów dla konkretnych procesorów. Można tworzyć wersje zestawu, którego tożsamość różni się tylko architekturą procesora, na przykład 32-bitowe i 64-bitowe wersje dla procesora. Architektura procesora nie jest wymagana w przypadku silnych nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.

 W tym przykładzie w pełni kwalifikowana nazwa wskazuje, że `myTypes` zestaw ma silną nazwę z tokenem klucza publicznego, ma wartość kultury dla języka angielskiego USA i ma numer wersji 1.0.1234.0. Jego architekturą procesora jest "MSIL", co oznacza, że będzie ona skompilowana do kodu 32-bitowego lub 64-bitowego kodu, w zależności od systemu operacyjnego i procesora.

 Kod, który żąda typów w zestawie, musi używać w pełni kwalifikowanej nazwy zestawu. Jest to nazywane w pełni kwalifikowanym powiązaniem. Częściowe powiązanie, które określa tylko nazwę zestawu, jest niedozwolone podczas odwoływania się do zestawów w .NET Framework.

 Wszystkie odwołania do zestawów, które składają się na .NET Framework, muszą również zawierać w pełni kwalifikowaną nazwę zestawu. Na przykład odwołanie do zestawu System. Data .NET Framework w wersji 1,0 obejmie:

```
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
```

 Należy zauważyć, że wersja odpowiada numerowi wersji wszystkich zestawów .NET Framework, które zostały dostarczone z .NET Framework wersja 1,0. Dla zestawów .NET Framework wartość kultury jest zawsze neutralna, a klucz publiczny jest taki sam, jak pokazano w powyższym przykładzie.

 Na przykład, aby dodać odwołanie do zestawu w pliku konfiguracji w celu skonfigurowania odbiornika śledzenia, należy uwzględnić w pełni kwalifikowaną nazwę zestawu .NET Framework systemu:

```xml
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />
```

> [!NOTE]
> Środowisko uruchomieniowe traktuje nazwy zestawów jako nieuwzględniające wielkości liter podczas tworzenia powiązania z zestawem, ale zachowuje wszelkie przypadki użycia w nazwie zestawu. Kilka narzędzi w Windows SDK obsługują nazwy zestawów jako uwzględniające wielkość liter. Aby uzyskać najlepsze wyniki, Zarządzaj nazwami zestawów, tak jakby były rozróżniane wielkości liter.

## <a name="name-application-components"></a>Nazwa składników aplikacji
 Środowisko uruchomieniowe nie uwzględnia nazwy pliku podczas określania tożsamości zestawu. Tożsamość zestawu, która składa się z nazwy zestawu, wersji, kultury i silnej nazwy, musi być jasne dla środowiska uruchomieniowego.

 Na przykład jeśli masz zestaw o nazwie *webassembly. exe* , który odwołuje się do zestawu o nazwie Moja *Assembly. dll*, powiązanie jest wykonywane prawidłowo, jeśli zostanie wykonany *plik. exe*. Jeśli jednak inna aplikacja wykonuje *plik z rozszerzeniem. exe* przy użyciu metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> , środowisko uruchomieniowe określa, że `myAssembly` jest już załadowany, gdy program *webassembly. exe* żąda powiązania z `myAssembly` . W takim przypadku *plik. dll* nie jest nigdy ładowany. Ponieważ obiekt *webassembly. exe* nie zawiera żądanego typu, <xref:System.TypeLoadException> występuje.

 Aby uniknąć tego problemu, upewnij się, że zestawy, które tworzą aplikację, nie mają tej samej nazwy zestawu lub Umieść zestawy o tej samej nazwie w różnych katalogach.

> [!NOTE]
> W .NET Framework, jeśli zestaw o silnej nazwie zostanie umieszczony w globalnej pamięci podręcznej zestawów, nazwa pliku zestawu musi być zgodna z nazwą zestawu, a nie z rozszerzeniem nazwy pliku, takim jak *exe* lub *dll*. Na przykład, jeśli nazwa pliku zestawu to plik. *dll*, nazwa zestawu musi być `myAssembly` . Zestawy prywatne wdrożone tylko w katalogu głównym aplikacji mogą mieć nazwę zestawu inną niż nazwa pliku.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu](find-fully-qualified-name.md)
- [Tworzenie zestawów](create.md)
- [Zestawy o silnych nazwach](strong-named.md)
- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Jak środowisko uruchomieniowe lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
