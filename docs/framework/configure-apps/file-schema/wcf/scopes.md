---
title: '&lt;zakresy&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b35696cbecb0badf397d6d48e7c97aae3d0232e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltscopesgt"></a>&lt;zakresy&gt;
Zawiera kolekcję elementów konfiguracji określającą niestandardowy zakres identyfikatorów URI, który może służyć do filtrowania punktów końcowych usługi podczas zapytania.  
  
\<System. ServiceModel >  
\<zachowania >  
\<endpointBehaviors >  
\<zachowanie >  
\<endpointDiscovery >  
\<zakresy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|[\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|Dodaje zakres informacji dla punktu końcowego, który może być używana w dopasowaniu kryteriów dla znajdowanej usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
