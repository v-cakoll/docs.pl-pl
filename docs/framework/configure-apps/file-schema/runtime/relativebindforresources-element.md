---
title: <relativeBindForResources>, element
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1ac2900707ddb39c62b34b0ebfbc4547cdd2653
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252360"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> Element
Optymalizuje sondę dla zestawów satelickich.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe języka wspólnego optymalizuje sondę dla zestawów satelickich.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko uruchomieniowe nie optymalizuje sondy dla zestawów satelickich. Jest to wartość domyślna.|  
|`true`|Środowisko uruchomieniowe optymalizuje sondę dla zestawów satelickich.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, Menedżer zasobów sondy dla zasobów, zgodnie z opisem w temacie [pakowanie i wdrażanie zasobów](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) . Oznacza to, że podczas Menedżer zasobów sond dla konkretnej zlokalizowanej wersji zasobu może on wyglądać w globalnej pamięci podręcznej zestawów, wyszukać w folderze specyficznym dla kultury w bazie kodu aplikacji, Instalator Windows zapytań dla zestawów satelickich i podnieść <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenie. `<relativeBindForResources>` Element optymalizuje sposób, w jaki Menedżer zasobów sondy dla zestawów satelickich. Może zwiększyć wydajność podczas sondowania zasobów w następujących warunkach:  
  
- Gdy zestaw satelicki zostanie wdrożony w tej samej lokalizacji co zestaw kodu. Innymi słowy, jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej zestawów, należy również zainstalować w tym miejscu zestawy satelickie. Jeśli zestaw kodu jest zainstalowany w bazie kodu aplikacji, zestawy satelickie muszą być również zainstalowane w folderze specyficznym dla kultury w bazie kodu.  
  
- Gdy Instalator Windows nie jest używany lub jest używany rzadko w przypadku instalacji zestawów satelitarnych na żądanie.  
  
- Gdy kod aplikacji nie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> obsługuje zdarzenia.  
  
 `enabled` Ustawienie atrybutu `<relativeBindForResources>` elementu w celu `true` optymalizacji sondy Menedżer zasobów dla zestawów satelickich w następujący sposób:  
  
- Używa lokalizacji zestawu kodu nadrzędnego do sondowania dla zestawu satelickiego.  
  
- Nie bada Instalator Windows dla zestawów satelickich.  
  
- Nie zgłasza <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia.  
  
## <a name="see-also"></a>Zobacz także

- [Opakowanie i wdrażanie zasobów](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
