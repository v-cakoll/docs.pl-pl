---
title: <relativeBindForResources>, element
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153909"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> Element
Optymalizuje sondę dla zestawów satelitowych.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko wykonawcze języka wspólnego optymalizuje sondę dla zestawów satelickich.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko wykonawcze nie optymalizuje sondy dla zestawów satelitowych. Jest to wartość domyślna.|  
|`true`|Środowisko wykonawcze optymalizuje sondę dla zestawów satelitowych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, Menedżer zasobów sonduje zasoby, zgodnie z dokumentami w temacie [Pakowanie i wdrażanie zasobów.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) Oznacza to, że gdy Menedżer zasobów sonduje dla określonej zlokalizowanej wersji zasobu, może wyglądać w globalnej pamięci podręcznej zestawów, szukać w folderze <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> specyficznym dla kultury w bazie kodu aplikacji, wysyłać zapytania instalatora Windows dla zestawów satelickich i podnosić zdarzenie. Element `<relativeBindForResources>` optymalizuje sposób, w jaki Resource Manager sondy dla zestawów satelitowych. Może poprawić wydajność podczas sondowania zasobów w następujących warunkach:  
  
- Gdy zestaw satelitów jest wdrażany w tej samej lokalizacji co zestaw kodu. Innymi słowy, jeśli zestaw kodu jest zainstalowany w globalnej pamięci podręcznej zestawów, zestawy satelickiego muszą być również zainstalowane tam. Jeśli zestaw kodu jest zainstalowany w bazie kodu aplikacji, zestawy satelickiego muszą być również zainstalowane w folderze specyficznym dla kultury w bazie kodu.  
  
- Gdy Instalator Windows nie jest używany lub jest używany rzadko do instalacji na żądanie zestawów satelickich.  
  
- Gdy kod aplikacji nie <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> obsługuje zdarzenia.  
  
 Ustawienie `enabled` atrybutu elementu `<relativeBindForResources>` w `true` celu optymalizacji sondy Menedżera zasobów dla zestawów satelitowych w następujący sposób:  
  
- Używa lokalizacji zestawu kodu nadrzędnego do sondowania dla zestawu satelickiego.  
  
- Nie wysyła kwerendy Instalatora Windows dla zestawów satelickich.  
  
- Nie podnosi <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia.  
  
## <a name="see-also"></a>Zobacz też

- [Opakowanie i wdrażanie zasobów](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
