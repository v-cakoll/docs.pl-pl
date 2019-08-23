---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 78788f9dfbf6cdf3439fd6e33eddfe721e49840d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931256"
---
# <a name="mexendpoint"></a>\<mexEndpoint>
Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem kontraktem IMetadataExchange. Ponieważ wszystkie punkty końcowe wymiany metadanych określają kontraktem IMetadataExchange jako kontrakt, można użyć tego standardowego punktu zamiast definiować go dla siebie.  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg określający nazwę konfiguracji standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).|
