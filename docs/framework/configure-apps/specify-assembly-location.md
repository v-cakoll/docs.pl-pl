---
title: Określanie lokalizacji zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646029"
---
# <a name="specifying-an-assemblys-location"></a>Określanie lokalizacji zestawu
Istnieją dwa sposoby określania lokalizacji zestawu:  
  
- Za pomocą [ \<codeBase>](./file-schema/runtime/codebase-element.md) element.  
  
- Za pomocą [ \<sondowania>](./file-schema/runtime/probing-element.md) element.  
  
 Narzędzia [konfiguracji programu .NET Framework Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) można również użyć do określenia lokalizacji zestawu lub określenia lokalizacji środowiska wykonawczego języka wspólnego do sondowania zestawów.  
  
## <a name="using-the-codebase-element"></a>Korzystanie \<z elementu codeBase>  
 Można użyć ** \<codeBase>** element tylko w konfiguracji komputera lub plików zasad wydawcy, które również przekierowywać wersję zestawu. Gdy środowisko wykonawcze określa, która wersja zestawu do użycia, stosuje ustawienie podstawowe kodu z pliku, który określa wersję. Jeśli nie ma podstawy kodu, sondy środowiska wykonawczego dla zestawu w normalny sposób. Aby uzyskać szczegółowe informacje, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).  
  
 W poniższym przykładzie pokazano, jak określić lokalizację zestawu.  
  
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
  
 Atrybut **wersji** jest wymagany dla wszystkich zestawów o silnej nazwie, ale należy go pominąć w przypadku zestawów, które nie mają silnej nazwy. Element ** \<codeBase>** wymaga atrybutu **href.** Nie można określić zakresów wersji w ** \<elemencie codeBase>.**  
  
> [!NOTE]
> Jeśli dostarczasz wskazówkę podstawową kodu dla zestawu, który nie ma silnej nazwy, wskazówka musi wskazywać na bazę aplikacji lub podkatalog katalogu podstawowego aplikacji.  
  
## <a name="using-the-probing-element"></a>Korzystanie \<z elementu> sondowania  
 Środowisko wykonawcze lokalizuje zestawy, które nie mają podstawy kodu przez sondowanie. Aby uzyskać więcej informacji na temat sondowania, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Można użyć [ \<sondowania>](./file-schema/runtime/probing-element.md) element w pliku konfiguracji aplikacji, aby określić podkatalogów środowiska wykonawczego należy szukać podczas lokalizowania zestawu. W poniższym przykładzie pokazano, jak określić katalogi, które należy przeszukać w czasie wykonywania.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Atrybut **privatePath** zawiera katalogi, które środowisko wykonawcze powinno wyszukiwać zestawy. Jeśli aplikacja znajduje się w folderze C:\Program Files\MyApp, środowisko wykonawcze będzie szukać zestawów, które nie określają bazy kodu w folderze C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3. Katalogi określone w **privatePath** muszą być podkatalogami katalogu podstawowego aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Zestawy w środowisku .NET](../../standard/assembly/index.md)
- [Programowanie za pomocą zestawów](../../standard/assembly/index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)
- [Konfigurowanie aplikacji za pomocą plików konfiguracji](index.md)
