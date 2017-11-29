---
title: "Określenie zestawu &#39; s lokalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f747d921e9c131edaa8a1749c5adc5eae14623c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-an-assembly39s-location"></a>Określenie zestawu &#39; s lokalizacji
Istnieją dwa sposoby, aby określić lokalizację zestawu:  
  
-   Przy użyciu [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.  
  
-   Przy użyciu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu.  
  
 Można również użyć [narzędzia konfiguracji programu .NET Framework (Mscorcfg.msc)](http://msdn.microsoft.com/en-us/a7106c52-68da-490e-b129-971b2c743764) do określenia lokalizacji zestawu lub określić inną lokalizację dla plików wykonywalnych języka sondowania dla zestawów.  
  
## <a name="using-the-codebase-element"></a>Przy użyciu \<codeBase > — Element  
 Można użyć  **\<codeBase >** elementu tylko w maszynie konfiguracji lub wydawcy pliki zasad, które również przekierować wersja zestawu. Środowisko uruchomieniowe określa wersji zestawu do użycia, stosuje się ustawienie baza kodu z pliku, który określa wersję. Jeśli wskazuje nie ścieżki bazowej kodu środowiska uruchomieniowego sondy dla zestawu w zwykły sposób. Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Poniższy przykład przedstawia sposób określenia lokalizacji zestawu.  
  
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
  
 **Wersji** atrybut jest wymagany dla wszystkich zestawów o silnych nazwach, ale należy pominąć dla zestawów, które są nie o silnych nazwach. **\<CodeBase >** wymaga elementu **href** atrybutu. Nie można określić wersji zakresów w  **\<codeBase >** elementu.  
  
> [!NOTE]
>  Jeśli są udostępnia podstawowe wskazówkę dla zestawu, który nie jest o silnych nazwach, wskazówka musi wskazywać baza aplikacji lub podkatalogu podstawowego katalogu aplikacji.  
  
## <a name="using-the-probing-element"></a>Przy użyciu \<sondowanie > — Element  
 Środowisko uruchomieniowe lokalizuje zestawy, które nie mają bazy kodu przez sondowanie. Aby uzyskać więcej informacji na temat sondowania, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Można użyć [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu w pliku konfiguracji aplikacji, aby określić podkatalogi środowiska uruchomieniowego powinna przeszukać podczas lokalizowania zestawów. Poniższy przykład pokazuje, jak można określić katalogi, które powinna przeszukać środowiska uruchomieniowego.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **PrivatePath** atrybut zawiera katalogi, które środowiska uruchomieniowego ma poszukiwać zestawów. Jeśli aplikacja znajduje się w lokalizacji C:\Program Files\MyApp, zestawy, które nie zostanie określona ścieżka bazowa kodu w C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3 będzie szukać środowiska uruchomieniowego. Katalogach określonych w **privatePath** musi być podkatalogi podstawowego katalogu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy w środowisko uruchomieniowe języka wspólnego](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Jak lokalizuje zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Konfigurowanie aplikacji programu .NET Framework](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
