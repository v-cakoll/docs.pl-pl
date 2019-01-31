---
title: <add> z <contractTypeNames>
ms.date: 03/30/2017
ms.assetid: 03aff6be-5dfb-4a64-ada3-e36227cd43c7
ms.openlocfilehash: fa67d2ec21494bb3d84861f4c2e2e39151aac28f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253722"
---
# <a name="add-of-contracttypenames"></a>\<Dodaj > z \<contractTypeNames >
Element konfiguracji, który określa nazwę kontraktu usługi wyszukane i kryteria zwykle używana podczas wyszukiwania dla usługi. Jeśli określono więcej niż jedną nazwę kontraktu, odpowie tylko punkty końcowe usługi dopasowanie wszystkich umów. Należy pamiętać, że w Windows Communication Foundation (WCF), punkt końcowy może obsługiwać tylko jednego kontraktu.  
  
 \<system.ServiceModel>  
\<standardEndpoints>  
  
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
              <add name="String" namespace="String" />
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
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg określający nazwę typu kontraktu.|  
|— przestrzeń nazw|Ciąg, który określa obszar nazw typu kontraktu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<contractTypeNames>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Kolekcja nazw typów kontraktu.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
- <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>
