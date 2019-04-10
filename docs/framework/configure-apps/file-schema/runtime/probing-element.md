---
title: <probing> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9402c9f28c123affb7b90fc189484bb1fd43db46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210272"
---
# <a name="probing-element"></a>\<probing> Element
Określa podkatalogi podstawowej aplikacji dla środowiska uruchomieniowego języka wspólnego wyszukiwania podczas ładowania zestawów.  
  
 \<Konfiguracja >  
\<runtime>  
\<assemblybinding — >  
\<sondowanie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`privatePath`|Atrybut wymagany.<br /><br /> Określa podkatalogi katalogu podstawowego aplikacji, który może zawierać zestawów. Powinny one być poszczególnych podkatalogach średnikiem.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić podkatalogów podstawowej aplikacji, które środowisko wykonawcze powinno poszukać zestawów.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Określanie lokalizacji zestawu](../../../../../docs/framework/configure-apps/specify-assembly-location.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
