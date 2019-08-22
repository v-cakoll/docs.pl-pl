---
title: <webProxyScript>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 8a77c2567401fd80e355bb7fcee17b6684653ebe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659046"
---
# <a name="webproxyscript-element-network-settings"></a>\<webProxyScript >, element (Ustawienia sieci)
Konfiguruje charakterystyki skryptu służącego do odnajdywania serwerów proxy sieci Web.  
  
 \<> konfiguracji  
\<system.net>  
\<settings>  
\<webProxyScript>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`downloadTimeout`|Określa maksymalny czas pobierania skryptu w godzinach, minutach i sekundach. Wartość domyślna to minutę.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień sieci](index.md)
