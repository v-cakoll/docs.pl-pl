---
title: Nazwy zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bdd27511de18c6cb119ddbf8621c43606c82ad4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195829"
---
# <a name="assembly-names"></a>Nazwy zestawów
Nazwa zestawu jest przechowywany w metadanych i ma znaczny wpływ na zakres zestawu i użycia przez aplikację. Zestawu z silną nazwą ma w pełni kwalifikowana nazwa, która zawiera nazwę zestawu, kultury, klucz publiczny i numer wersji. Jest to często określane jako wyświetlaną nazwę i dla zestawów załadowanych można uzyskać za pomocą <xref:System.Reflection.Assembly.FullName%2A> właściwości.  
  
 Środowisko wykonawcze używa tych informacji, aby zlokalizować zestawu i odróżnić go od innych zestawów o takiej samej nazwie. Na przykład o nazwie zestawu z silną nazwą `myTypes` może mieć następującej nazwy FQDN:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  Architektura procesora jest dodawana do tożsamości zestawu w .NET Framework w wersji 2.0, aby umożliwić specyficznych dla procesora wersje zestawów. Można utworzyć wersji zestawu, którego tożsamość różni się tylko architektury procesora, na przykład 32-bitowych i 64-bitowych wersjach specyficznych dla procesora. Architektura procesora nie jest wymagane silne nazwy. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 W tym przykładzie w pełni kwalifikowana nazwa wskazuje, że `myTypes` zestaw z silną nazwą przy użyciu tokenu klucza publicznego, ma wartość kultury dla tego języka i numerem wersji 1.0.1234.0. Jego architektura procesora jest "msil", co oznacza, że będzie on just-in-time (JIT)-kompilowane do kodu 32-bitowego lub 64-bitowego kodu w zależności od systemu operacyjnego i procesora.  
  
 Kod, który żąda typy w zestawie, należy użyć w pełni kwalifikowanej nazwy zestawu. Jest to powiązanie w pełni kwalifikowana. Częściowe powiązania, który określa nazwę zestawu, nie jest dozwolone podczas odwoływania się do zestawów .NET Framework.  
  
 Wszystkie odwołania do zestawów do zestawów, które składają się na programie .NET Framework również musi zawierać w pełni kwalifikowana nazwa zestawu. Na przykład aby odwoływać się do zestawu System.Data .NET Framework w wersji 1.0 zadania obejmują:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Należy pamiętać, że wersja odpowiada numer wersji wszystkich zestawów .NET Framework, które są dostarczane z programem .NET Framework w wersji 1.0. Dla zestawów .NET Framework wartość kultury jest zawsze neutralne i klucz publiczny jest taki sam, jak pokazano w powyższym przykładzie.  
  
 Na przykład aby dodać odwołanie do zestawu w pliku konfiguracji, aby skonfigurować odbiornik śledzenia, należy dołączyć w pełni kwalifikowaną nazwę systemu zestawu .NET Framework:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Środowisko uruchomieniowe traktuje nazwy zestawu jako bez uwzględniania wielkości liter, podczas tworzenia wiązania do zestawu, ale zachowuje, niezależnie od przypadku jest używany w nazwie zestawu. Niektóre narzędzia [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] obsługi nazw zestawów jako wielkość liter. Aby uzyskać najlepsze wyniki Zarządzanie nazw zestawów tak, jakby były uwzględniana wielkość liter.  
  
## <a name="naming-application-components"></a>Nadawanie nazw składników aplikacji  
 Środowisko wykonawcze nie należy wziąć pod uwagę nazwę pliku podczas ustalania tożsamości zestawu. Tożsamość zestawu, który składa się z nazwy zestawu, wersji, kultury i silnej nazwy, musi być czysty do środowiska uruchomieniowego.  
  
 Na przykład jeśli zestaw o nazwie myAssembly.exe odwołujący się do zestawu o nazwie myAssembly.dll, powiązanie występuje poprawnie jeśli wykonywane myAssembly.exe. Jednakże jeśli inna aplikacja wykonuje myAssembly.exe przy użyciu metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, środowisko wykonawcze określa, że "myAssembly" jest już załadowana w momencie myAssembly.exe żądania powiązania "myAssembly." W tym przypadku myAssembly.dll nigdy nie został załadowany. Ponieważ myAssembly.exe nie zawiera żądanego typu <xref:System.TypeLoadException> występuje.  
  
 Aby uniknąć tego problemu, upewnij się, nie mają taką samą nazwę zestawu lub umieść zestawów o takiej samej nazwie w różnych katalogach zestawów, które składają się na aplikację.  
  
> [!NOTE]
>  Jeśli zestaw o silnej nazwie zostanie umieszczone w globalnej pamięci podręcznej, nazwa pliku zestawu musi być zgodna z nazwy zestawu (nie w tym rozszerzenie nazwy pliku, na przykład .exe lub .dll). Na przykład jeśli nazwa pliku zestawu jest myAssembly.dll, nazwa zestawu musi być myAssembly. Zestawy prywatne wdrożone tylko w katalogu głównym aplikacji może mieć nazwy zestawu, który różni się od nazwy pliku.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)
- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
