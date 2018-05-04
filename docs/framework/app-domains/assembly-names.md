---
title: Nazwy zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e1ab9609fe6b2c1e232f188db8306fc05828285
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="assembly-names"></a>Nazwy zestawów
Nazwa zestawu jest przechowywany w metadanych i ma znaczny wpływ na zakres zestawu i używany przez aplikację. Zestawu z silną nazwą ma nazwę FQDN, która zawiera nazwę zestawu, kultury, klucz publiczny i numer wersji. Jest to często określane jako wyświetlana nazwa i dla zestawów załadowanych można uzyskać za pomocą <xref:System.Reflection.Assembly.FullName%2A> właściwości.  
  
 Środowisko uruchomieniowe używa tych informacji do lokalizowania zestawu i odróżnienia go od innych zestawów o takiej samej nazwie. Na przykład o nazwie zestawu z silną nazwą `myTypes` może mieć następujące nazwy FQDN:  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  Architektura procesora jest dodawany do tożsamości zestawu w .NET Framework w wersji 2.0, aby umożliwić specyficznych dla procesora wersje zestawów. Można utworzyć wersji zestawu, którego tożsamość różni się tylko do architektury procesora, na przykład 32-bitowe i 64-bitowe wersje specyficznych dla procesora. Architektura procesora nie jest wymagane dla silnej nazwy. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.  
  
 W tym przykładzie w pełni kwalifikowana nazwa wskazuje, że `myTypes` zestaw ma silną nazwę z tokenem klucza publicznego, ma wartość kultury dla tego języka i ma numer wersji 1.0.1234.0. Jego architektura procesora jest "msil", co oznacza, że będzie on just-in-time (JIT)-skompilowany kod 32-bitowy lub 64-bitowego kodu w zależności od systemu operacyjnego i procesora.  
  
 Kod, który żąda typów w zestawie, należy użyć nazwy zestawu w pełni kwalifikowana. Jest to pełna powiązania. Częściowe powiązania, który określa nazwę zestawu, nie jest dozwolona, gdy odwołania do zestawów w programie .NET Framework.  
  
 Wszystkie odwołania do zestawów do zestawów, które składają się na programie .NET Framework również musi zawierać pełną nazwę zestawu. Na przykład aby odwoływać się do zestawu system.dane .NET Framework w wersji 1.0 to:  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 Należy pamiętać, że wersja odpowiada numer wersji wszystkie zestawy .NET Framework dostarczonych z programem .NET Framework w wersji 1.0. Dla zestawów platformy .NET Framework wartość kultury jest zawsze neutralnego, a klucz publiczny jest taka sama, jak pokazano w przykładzie powyżej.  
  
 Na przykład aby dodać odwołania do zestawu w pliku konfiguracji, aby skonfigurować odbiornik śledzenia, należy umieścić w pełni kwalifikowanej nazwy systemu zestawu .NET Framework:  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Środowisko uruchomieniowe traktuje nazwy zestawu jako bez uwzględniania wielkości liter podczas wiązania z zestawem, ale zachowuje niezależnie od przypadku jest używany w nazwie zestawu. Niektóre narzędzia [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] obsługi nazwy zestawu jako wielkość liter. Aby uzyskać najlepsze wyniki Zarządzanie nazw zestawów tak, jakby były z uwzględnieniem wielkości liter.  
  
## <a name="naming-application-components"></a>Nazewnictwo składników aplikacji  
 Środowisko uruchomieniowe nie należy wziąć pod uwagę nazwa pliku podczas określania tożsamości zestawu. Tożsamość zestawu, który składa się z nazwy zestawu, wersję, kulturę i silnej nazwy, musi być czysty do środowiska wykonawczego.  
  
 Na przykład jeśli masz zestawu o nazwie myAssembly.exe odwołujących się do zestawu o nazwie myAssembly.dll powiązania występuje poprawnie Jeśli wykonanie myAssembly.exe. Jednak jeśli inna aplikacja wykonuje myAssembly.exe przy użyciu metody <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, środowisko uruchomieniowe Określa, że "myAssembly" jest już załadowana myAssembly.exe żądanie powiązania "myAssembly". W takim przypadku myAssembly.dll nigdy nie została załadowana. Ponieważ myAssembly.exe nie zawiera żądanego typu <xref:System.TypeLoadException> występuje.  
  
 Aby uniknąć tego problemu, upewnij się, nie mają taką samą nazwę zestawu lub umieść zestawów o tej samej nazwie w różnych katalogach zestawy, które składają się na aplikację.  
  
> [!NOTE]
>  Jeśli umieścisz zestawu z silną nazwą w globalnej pamięci podręcznej zestawów, nazwę pliku zestawu musi odpowiadać nazwie zestawu (nie w tym rozszerzenie nazwy pliku, takie jak .exe lub .dll). Na przykład jeśli nazwa pliku zestawu jest myAssembly.dll, nazwa zestawu musi być myAssembly. Zestawy prywatne wdrażane tylko w katalogu głównym aplikacji może mieć nazwę zestawu, która różni się od nazwy pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: określanie w pełni kwalifikowanej nazwy zestawu](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
