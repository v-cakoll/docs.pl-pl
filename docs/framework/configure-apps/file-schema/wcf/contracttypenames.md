---
title: '&lt;contractTypeNames&gt;'
ms.date: 03/30/2017
ms.assetid: 5ec5efc6-87f8-4160-9be0-dcd2e01df3df
ms.openlocfilehash: 60647e6ec31e7228f09d084ff669a1829770ca14
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144734"
---
# <a name="ltcontracttypenamesgt"></a>&lt;contractTypeNames&gt;
Sekcja konfiguracji, który określa listę nazw typu umowy, które są nazwy kontraktów usług wyszukane, i kryteria zwykle używana podczas wyszukiwania dla usługi. Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów. Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Nazwa typu, który kontrakt jest właściwością, która odwołuje się do zestawu kryteriów zwykle używana podczas wyszukiwania dla usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<kryteria znajdowania >](../../../../../docs/framework/configure-apps/file-schema/wcf/findcriteria.md)|Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odkrywania. Kryteria mogą być grupowane w kryteriach wyszukiwania (Określanie usług szukasz) i Znajdź kryteriów zakończenia (ile wyszukiwanie powinno trwać).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>  
 <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElementCollection>
