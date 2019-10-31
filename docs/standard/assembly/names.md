---
title: Nazwy zestawów
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: a35be7c2a2cb4b499496f526d263bb1825a3614b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107130"
---
# <a name="assembly-names"></a>Nazwy zestawów
Nazwa zestawu jest przechowywana w metadanych i ma znaczny wpływ na zakres zestawu i użycie przez aplikację. Zestaw o silnej nazwie ma w pełni kwalifikowaną nazwę, która zawiera nazwę zestawu, kulturę, klucz publiczny i numer wersji. Jest to często określane jako nazwa wyświetlana, a dla załadowanych zestawów można uzyskać za pomocą właściwości <xref:System.Reflection.Assembly.FullName%2A>.  
  
 Środowisko uruchomieniowe używa tych informacji do lokalizowania zestawu i odróżnienia go od innych zestawów o tej samej nazwie. Na przykład zestaw o silnej nazwie o nazwie `myTypes` może mieć następującą w pełni kwalifikowaną nazwę:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
> Architektura procesora jest dodawana do tożsamości zestawu w .NET Framework w wersji 2,0, aby zezwolić na wersje zestawów dla konkretnych procesorów. Można tworzyć wersje zestawu, którego tożsamość różni się tylko architekturą procesora, na przykład 32-bitowe i 64-bitowe wersje dla procesora. Architektura procesora nie jest wymagana w przypadku silnych nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 W tym przykładzie w pełni kwalifikowana nazwa wskazuje, że zestaw `myTypes` ma silną nazwę z tokenem klucza publicznego, ma wartość kultury dla języka angielskiego USA i ma numer wersji 1.0.1234.0. Jego architekturą procesora jest "MSIL", co oznacza, że będzie ona skompilowana do kodu 32-bitowego lub 64-bitowego kodu, w zależności od systemu operacyjnego i procesora.  
  
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
  
 Na przykład jeśli masz zestaw o nazwie *webassembly. exe* , który odwołuje się do zestawu o nazwie Moja *Assembly. dll*, powiązanie jest wykonywane prawidłowo, jeśli zostanie wykonany *plik. exe*. Jeśli jednak inna aplikacja wykonuje *plik webassembly. exe* przy użyciu metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, środowisko uruchomieniowe określa, że `myAssembly` jest już załadowana, gdy program *webassembly. exe* żąda powiązania do `myAssembly`. W takim przypadku *plik. dll* nie jest nigdy ładowany. Ponieważ obiekt *webassembly. exe* nie zawiera żądanego typu, występuje <xref:System.TypeLoadException>.  
  
 Aby uniknąć tego problemu, upewnij się, że zestawy, które tworzą aplikację, nie mają tej samej nazwy zestawu lub Umieść zestawy o tej samej nazwie w różnych katalogach.  
  
> [!NOTE]
> W .NET Framework, jeśli zestaw o silnej nazwie zostanie umieszczony w globalnej pamięci podręcznej zestawów, nazwa pliku zestawu musi być zgodna z nazwą zestawu, a nie z rozszerzeniem nazwy pliku, takim jak *exe* lub *dll*. Na przykład, jeśli nazwa pliku zestawu to plik *. dll*, nazwa zestawu musi być `myAssembly`. Zestawy prywatne wdrożone tylko w katalogu głównym aplikacji mogą mieć nazwę zestawu inną niż nazwa pliku.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu](find-fully-qualified-name.md)
- [Tworzenie zestawów](create.md)
- [Zestawy o silnych nazwach](strong-named.md)
- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Jak środowisko uruchomieniowe lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Program z zestawami](program.md)
