---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 462a06e5a773310b6364838ae2ebc14da0a2ee1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925891"
---
# <a name="defaultports"></a>\<defaultPorts>
Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.  
  
\<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
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
|[\<Dodawanie > \<defaultPorts >](add-of-defaultports.md)|Domyślny punkt końcowy komunikacji, do którego nasłuchuje aplikacja kliencka.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|Lista domyślnych portów.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
