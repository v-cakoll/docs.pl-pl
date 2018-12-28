---
title: '&lt;relativebindforresources —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1933fad8ea87351a56fcc7dd4a4fd67e890b58f5
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613898"
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativebindforresources —&gt; — Element
Optymalizuje sondy dla zestawów satelickich.  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<relativebindforresources — > Element  
  
## <a name="syntax"></a>Składnia  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe języka wspólnego optymalizuje sondy dla zestawów satelickich.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko wykonawcze nie optymalizuje sondy dla zestawów satelickich. Jest to wartość domyślna.|  
|`true`|Środowisko uruchomieniowe optymalizuje sondy dla zestawów satelickich.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, Menedżer zasobów sondy dla zasobów, zgodnie z opisem w [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tematu. Oznacza to, że po sondy usługi Resource Manager dla konkretnej wersji zlokalizowanych zasobów, jego może Szukaj w globalnej pamięci podręcznej, poszukaj w folderze kodu aplikacji — zapytania bazowego, Instalator Windows specyficzne dla kultury zestawy satelickie i podnieść <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń. `<relativeBindForResources>` Element optymalizuje sposób, w którym Menedżer zasobów sondy dla zestawów satelickich. Go może poprawić wydajność podczas sondowania dla zasobów w następujących warunkach:  
  
-   Podczas wdrażania w tej samej lokalizacji co zestawu kodu w zestawie satelickim. Innymi słowy Jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej, zestawy satelickie należy także zainstalować istnieje. Jeśli zestaw kodu jest zainstalowana w bazie kodu aplikacji, zestawy satelickie musi również zainstalowany w folderze specyficzne dla kultury bazy kodu.  
  
-   Gdy Instalator Windows nie jest używana lub jest tylko rzadko używane do instalowania zestawów satelickich na żądanie.  
  
-   Gdy kod aplikacji nie obsługuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
 Ustawienie `enabled` atrybutu `<relativeBindForResources>` elementu `true` optymalizuje sondy usługi Resource Manager dla zestawów satelickich w następujący sposób:  
  
-   Lokalizacja zestawu kodu nadrzędnego używa do sondowania dla zestawu satelickiego.  
  
-   Nie odpytuje Instalatora Windows dla zestawów satelickich.  
  
-   Zgłaszaj <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
- [Opakowanie i wdrażanie zasobów](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
