---
title: '&lt;webproxyscript —&gt; — Element (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6843662b73f6b7d45dd12616f5118569a2d19975
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754509"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a>&lt;webproxyscript —&gt; — Element (ustawienia sieciowe)
Konfiguruje właściwości skryptu używana do wykrywania, serwer proxy sieci Web.  
  
 \<Konfiguracja >  
\<system.net>  
\<Ustawienia >  
\<webproxyscript — >  
  
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
|`downloadTimeout`|Określa maksymalny czas, który można pobrać skryptu w godziny, minuty i sekundy. Wartość domyślna to jedna minuta.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
