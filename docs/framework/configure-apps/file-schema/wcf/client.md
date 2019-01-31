---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 93365c109f015b2ec72b5216dcb8c46258d022e2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280907"
---
# <a name="client"></a>\<client>
`client` Element definiuje listę punktów końcowych, które klient może połączyć się z.  
  
 \<system.ServiceModel>  
\<client>  
  
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
|[\<punkt końcowy >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Zawiera kolekcję elementów punktu końcowego, które określają punktów końcowych, które ten klient może połączyć się z.|  
|[\<metadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|Zawiera ustawienia dla przetwarzania metadanych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|Element główny wszystkich elementów konfiguracji usługi Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Uwagi  
 `client` Sekcji definiuje listę punktów końcowych, które klient może nawiązać połączenia. Każdy punkt końcowy na liście w sekcji klienta definiuje swój własny powiązania, zachowanie i umowy. Jest unikatowo identyfikowana przez kombinację `name` i `contract` atrybutów. Określa kod klienta `name` połączyć się z punktem końcowym usługi, który implementuje klienta. Jeśli `name` atrybut zostanie pominięty, punkt końcowy działa jako domyślny punkt końcowy dla kontraktu go implementuje.  
  
 Ponadto w tej sekcji określa również ustawienia dla przetwarzania metadanych.  
  
## <a name="example"></a>Przykład  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [Konfiguracja klienta programu WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [Klienci](../../../../../docs/framework/wcf/feature-details/clients.md)
