---
title: Nazwy zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 499a64362f7a23f0c4c595469fceaa1612bf44dd
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567350"
---
# <a name="assembly-names"></a>Nazwy zestawów
Nazwa zestawu jest przechowywana w metadanych i ma znaczny wpływ na zakres zestawu i użycie przez aplikację. Zestaw o silnej nazwie ma w pełni kwalifikowaną nazwę, która zawiera nazwę zestawu, kulturę, klucz publiczny i numer wersji. Jest to często określane jako nazwa wyświetlana, a dla załadowanych zestawów można uzyskać za pomocą <xref:System.Reflection.Assembly.FullName%2A> właściwości.  
  
 Środowisko uruchomieniowe używa tych informacji do lokalizowania zestawu i odróżnienia go od innych zestawów o tej samej nazwie. Na przykład zestaw `myTypes` o silnej nazwie może mieć następującą w pełni kwalifikowaną nazwę:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  Architektura procesora jest dodawana do tożsamości zestawu w .NET Framework w wersji 2,0, aby zezwolić na wersje zestawów dla konkretnych procesorów. Można tworzyć wersje zestawu, którego tożsamość różni się tylko architekturą procesora, na przykład 32-bitowe i 64-bitowe wersje dla procesora. Architektura procesora nie jest wymagana w przypadku silnych nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 W tym przykładzie w pełni kwalifikowana nazwa wskazuje, że `myTypes` zestaw ma silną nazwę z tokenem klucza publicznego, ma wartość kultury dla języka angielskiego USA i ma numer wersji 1.0.1234.0. Jego architekturą procesora jest "MSIL", co oznacza, że będzie ona skompilowana do kodu 32-bitowego lub 64-bitowego kodu, w zależności od systemu operacyjnego i procesora.  
  
 Kod, który żąda typów w zestawie, musi używać w pełni kwalifikowanej nazwy zestawu. Jest to nazywane w pełni kwalifikowanym powiązaniem. Częściowe powiązanie, które określa tylko nazwę zestawu, jest niedozwolone podczas odwoływania się do zestawów w .NET Framework.  
  
 Wszystkie odwołania do zestawów, które składają się na .NET Framework, również muszą zawierać w pełni kwalifikowaną nazwę zestawu. Na przykład, aby odwołać się do zestawu System. Data .NET Framework w wersji 1,0, będzie obejmował:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Należy zauważyć, że wersja odpowiada numerowi wersji wszystkich zestawów .NET Framework, które zostały dostarczone z .NET Framework wersja 1,0. Dla zestawów .NET Framework wartość kultury jest zawsze neutralna, a klucz publiczny jest taki sam, jak pokazano w powyższym przykładzie.  
  
 Na przykład, aby dodać odwołanie do zestawu w pliku konfiguracji w celu skonfigurowania odbiornika śledzenia, należy uwzględnić w pełni kwalifikowaną nazwę zestawu .NET Framework systemu:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Środowisko uruchomieniowe traktuje nazwy zestawów jako nieuwzględniające wielkości liter podczas tworzenia powiązania z zestawem, ale zachowuje wszelkie przypadki użycia w nazwie zestawu. Kilka narzędzi w Windows SDK obsługują nazwy zestawów jako uwzględniające wielkość liter. Aby uzyskać najlepsze wyniki, Zarządzaj nazwami zestawów, tak jakby były rozróżniane wielkości liter.  
  
## <a name="naming-application-components"></a>Nazywanie składników aplikacji  
 Środowisko uruchomieniowe nie uwzględnia nazwy pliku podczas określania tożsamości zestawu. Tożsamość zestawu, która składa się z nazwy zestawu, wersji, kultury i silnej nazwy, musi być jasne dla środowiska uruchomieniowego.  
  
 Na przykład jeśli masz zestaw o nazwie webassembly. exe, który odwołuje się do zestawu o nazwie Moja Assembly. dll, powiązanie jest wykonywane prawidłowo, jeśli zostanie wykonany plik. exe. Jeśli jednak inna aplikacja wykonuje plik z rozszerzeniem. exe przy użyciu metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, środowisko uruchomieniowe określa, że "fragment" jest już załadowany, gdy plik. exe żąda powiązania z "webassembly". W takim przypadku plik. dll nie jest nigdy ładowany. Ponieważ obiekt <xref:System.TypeLoadException> webassembly. exe nie zawiera żądanego typu, występuje.  
  
 Aby uniknąć tego problemu, upewnij się, że zestawy, które tworzą aplikację, nie mają tej samej nazwy zestawu lub Umieść zestawy o tej samej nazwie w różnych katalogach.  
  
> [!NOTE]
>  Jeśli zestaw o silnej nazwie zostanie umieszczony w globalnej pamięci podręcznej zestawów, nazwa pliku zestawu musi być zgodna z nazwą zestawu (nie dotyczy to rozszerzenia nazwy pliku, takiego jak exe lub dll). Na przykład, jeśli nazwa pliku zestawu to plik. dll, nazwa zestawu musi być obiektem. Zestawy prywatne wdrożone tylko w katalogu głównym aplikacji mogą mieć nazwę zestawu inną niż nazwa pliku.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)
- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
