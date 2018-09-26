---
title: Określanie zestawu&#39;lokalizacji s
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8fedec60b6152e77d6f99bf55cf11ec909fa8f80
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083718"
---
# <a name="specifying-an-assembly39s-location"></a>Określanie zestawu&#39;lokalizacji s
Istnieją dwa sposoby, aby określić lokalizację zestawu:  
  
-   Za pomocą [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.  
  
-   Za pomocą [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu.  
  
 Można również użyć [narzędzia .NET Framework Configuration Tool (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) Aby określić inną lokalizację zestawu lub określić inną lokalizację dla środowiska uruchomieniowego języka wspólnego sondowania dla zestawów.  
  
## <a name="using-the-codebase-element"></a>Za pomocą \<codeBase > Element  
 Możesz użyć  **\<codeBase >** elementu tylko w konfiguracji lub wydawcy zasad plików maszyny, które również przekierowanie wersji zestawu. Środowisko wykonawcze określa, jakiego zestawu należy użyć, stosuje się ustawienie baza kodu z pliku, który określa wersję. Jeśli nie baza kodu jest zaznaczone, środowisko uruchomieniowe sondy dla zestawu w normalny sposób. Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Poniższy przykład pokazuje sposób określania lokalizacji zestawu.  
  
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
  
 **Wersji** atrybut jest wymagany dla wszystkich zestawów o silnej nazwie, ale należy pominąć dla zestawów, które są nie o silnej nazwie. **\<CodeBase >** element wymaga **href** atrybutu. Nie można określić wersji zakresów w  **\<codeBase >** elementu.  
  
> [!NOTE]
>  Jeśli są podawania wskazówką podstawowego kodu dla zestawu, który nie jest, o silnych nazwach, wskazówka musi wskazywać podstawy aplikacji lub podkatalogiem katalogu podstawowego aplikacji.  
  
## <a name="using-the-probing-element"></a>Za pomocą \<sondowanie > Element  
 Środowisko uruchomieniowe lokalizuje zestawy, które nie mają kodu bazowego sondowanie. Aby uzyskać więcej informacji na temat badania, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Możesz użyć [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu w pliku konfiguracyjnym aplikacji, aby określić środowisko uruchomieniowe ma poszukiwać podczas lokalizowania zestawu podkatalogów. Poniższy przykład pokazuje, jak można określić katalogi, których środowisko uruchomieniowe ma wyszukiwać.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath** atrybut zawiera katalogi, które środowisko wykonawcze powinno poszukać zestawów. Jeśli aplikacja znajduje się w lokalizacji C:\Program Files\MyApp, środowisko uruchomieniowe będzie szukać zestawów, które nie określisz bazy kodu w C:\Program Files\MyApp\Bin C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3. Katalogi określone w **privatePath** musi być podkatalogi katalogu podstawowego aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurowanie aplikacji programu .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
