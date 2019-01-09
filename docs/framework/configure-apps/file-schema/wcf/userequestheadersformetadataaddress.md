---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: bcbf1c633e0796c6056759dfbb55014838e0e293
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151413"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a>&lt;useRequestHeadersForMetadataAddress&gt;
Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.  
  
\<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<useRequestHeadersForMetadataAddress >  
  
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
|[\<defaultPorts >](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
