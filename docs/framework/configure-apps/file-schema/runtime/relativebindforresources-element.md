---
title: "&lt;relativebindforresources —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ffd5b62e0759b3a4f97e105e884912a41f0117de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativebindforresources —&gt; — Element
Optymalizuje sondy zestawów satelickich.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<relativebindforresources — > — Element  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe języka wspólnego optymalizuje sondy zestawów satelickich.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko uruchomieniowe nie zoptymalizować badanie zestawów satelickich. Jest to wartość domyślna.|  
|`true`|Środowisko uruchomieniowe optymalizuje sondy zestawów satelickich.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, Menedżer zasobów sondy dla zasobów, zgodnie z opisem w [pakowanie i wdrażanie zasobów](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tematu. To oznacza, że podczas badania Menedżera zasobów dla określonej wersji zlokalizowanych zasobów, jego może Szukaj w globalnej pamięci podręcznej zestawów, poszukaj w folderze określonej kultury w podstawowej, zapytania kodu aplikacji Instalatora Windows zestawy satelickie i podnieść <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń. `<relativeBindForResources>` Sposób, w którym Menedżer zasobów sondy zestawów satelickich optymalizuje elementu. Go może poprawić wydajność podczas badania zasobów w następujących warunkach:  
  
-   Podczas wdrażania zestawu satelickiego w tej samej lokalizacji co zestaw kodu. Innymi słowy Jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej zestawów, zestawy satelickie należy także zainstalować istnieje. Po zainstalowaniu zestawu kodu w kodzie aplikacji podstawowe zestawy satelickie należy także zainstalować w folderze określonej kultury w bazie kodu.  
  
-   Gdy Instalator Windows nie jest używana lub jest rzadko używana dla instalacji zestawów satelickich na żądanie.  
  
-   Jeśli kod aplikacji nie obsługuje <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
 Ustawienie `enabled` atrybutu `<relativeBindForResources>` elementu `true` optymalizuje sondowania Menedżera zasobów dla zestawów satelickich w następujący sposób:  
  
-   Badanie dla zestawu satelickiego używa lokalizacji zestawu kod nadrzędny.  
  
-   Nie odpytuje Instalatora Windows zestawów satelickich.  
  
-   Nie zgłaszał <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Opakowanie i wdrażanie zasobów](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
