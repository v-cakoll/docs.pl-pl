---
title: '&lt;klienta&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d52d74c36ea1b1d722d781f554f8cc6691d53e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientgt"></a>&lt;klienta&gt;
`client` Element definiuje listę punktów końcowych, które klient może nawiązać połączenia.  
  
 \<System. ServiceModel >  
\<Klient >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>  
    <client>  
        <endpoint>  
        </endpoint>  
                <metadata>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<punkt końcowy >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Zawiera kolekcję elementów punktu końcowego, określające punkty końcowe, które ten klient może nawiązać połączenia.|  
|[\<metadane >](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|Zawiera ustawienia dla przetwarzania metadanych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Element główny wszystkich elementów konfiguracji systemu Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Uwagi  
 `client` Sekcja definiuje listę punktów końcowych, które klient może nawiązać połączenie. Każdy punkt końcowy wymienione w sekcji klienta definiuje własną powiązanie, zachowania i kontraktu. Jest unikatowo identyfikowana przez kombinację `name` i `contract` atrybutów. Określa kod klienta `name` nawiązać połączenia z punktu końcowego usługi, który implementuje klienta. Jeśli `name` atrybut nie jest określony, punkt końcowy działa jako domyślnego punktu końcowego dla kontraktu ją implementuje.  
  
 Ponadto w tej sekcji również określa ustawienia dla przetwarzania metadanych.  
  
## <a name="example"></a>Przykład  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [Konfiguracja klienta programu WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienci](../../../../../docs/framework/wcf/feature-details/clients.md)
