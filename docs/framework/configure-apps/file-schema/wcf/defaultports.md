---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2c742f98315c0e497ac4117953424bae913cb5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614500"
---
# <a name="ltdefaultportsgt"></a>&lt;defaultPorts&gt;
Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<useRequestHeadersForMetadataAddress>  
\<defaultPorts>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dodaj > z \<defaultPorts >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|Domyślny punkt końcowy komunikacji, aplikacja kliencka nasłuchuje.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Lista domyślnych portów.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
