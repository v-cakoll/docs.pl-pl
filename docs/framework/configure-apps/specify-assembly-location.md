---
title: Określanie lokalizacji zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 43cd1d0edbb607f69f27661aae3372e93564b3b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932335"
---
# <a name="specifying-an-assemblys-location"></a>Określanie lokalizacji zestawu
Istnieją dwa sposoby określania lokalizacji zestawu:  
  
- Używanie bazowej [ >elementu.\<](./file-schema/runtime/codebase-element.md)  
  
- Korzystanie z [ \<elementu > sondowania](./file-schema/runtime/probing-element.md) .  
  
 Można również użyć [Narzędzia konfiguracji .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) , aby określić lokalizacje zestawów lub określić lokalizacje dla środowiska uruchomieniowego języka wspólnego do sondowania dla zestawów.  
  
## <a name="using-the-codebase-element"></a>\<Używanie bazowej > elementu  
 Można użyć  **\<bazowej >** elementu tylko w pliku konfiguracji komputera lub zasad wydawcy, który również przekieruje wersję zestawu. Gdy środowisko uruchomieniowe określa wersję zestawu, która ma być używana, stosuje ustawienia podstawowe kodu z pliku, który określa wersję. Jeśli nie wskazano żadnego kodu bazowego, sondy środowiska uruchomieniowego dla zestawu w normalny sposób. Aby uzyskać szczegółowe informacje, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Poniższy przykład pokazuje, jak określić lokalizację zestawu.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Atrybut **Version** jest wymagany dla wszystkich zestawów o silnych nazwach, ale powinien być pominięty dla zestawów, które nie mają silnej nazwy. **\<CodeBase>** element wymaga **href** atrybutu. Nie można określić zakresów wersji w  **\<ścieżce bazowej >** elementu.  
  
> [!NOTE]
> Jeśli dostarczasz wskazówkę bazową kodu dla zestawu, który nie ma silnej nazwy, Wskazówka musi wskazywać na bazę aplikacji lub podkatalog katalogu podstawowego aplikacji.  
  
## <a name="using-the-probing-element"></a>\<Używanie elementu > sondowania  
 Środowisko uruchomieniowe lokalizuje zestawy, które nie mają bazy kodu przy użyciu sondowania. Aby uzyskać więcej informacji na temat sondowania, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Można użyć [ \<elementu > sondowania](./file-schema/runtime/probing-element.md) w pliku konfiguracyjnym aplikacji, aby określić podkatalogi, które środowisko uruchomieniowe ma przeszukiwać podczas lokalizowania zestawu. Poniższy przykład pokazuje, jak określić katalogi, które mają być wyszukiwane przez środowisko uruchomieniowe.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Atrybut **PrivatePath** zawiera katalogi, w których środowisko uruchomieniowe ma wyszukiwać zestawy. Jeśli aplikacja znajduje się w katalogu C:\Program Files\MyApp, środowisko uruchomieniowe będzie szukać zestawów, które nie określają bazy kodu w folderze C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3. Katalogi określone w **PrivatePath** muszą być podkatalogami katalogu podstawowego aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Zestawy w środowisku uruchomieniowym CLR](../app-domains/assemblies-in-the-common-language-runtime.md)
- [Programowanie za pomocą zestawów](../app-domains/programming-with-assemblies.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji przy użyciu plików konfiguracji](index.md)
