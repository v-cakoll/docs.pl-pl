---
title: '&lt;workflowControlEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 9c641d4081d88b059e1d778f6383f85c064af7f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558673"
---
# <a name="ltworkflowcontrolendpointgt"></a>&lt;workflowControlEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchamianie, wstrzymywanie, zakończenia itp).  
  
\<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy. Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
