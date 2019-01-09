---
title: '&lt;webScriptEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: beb17d4ccc39bcca30e97d4f0df47c797cde6216
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148776"
---
# <a name="ltwebscriptendpointgt"></a>&lt;webScriptEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, który automatycznie dodaje [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie. Używanie tego punktu końcowego, gdy tworzysz usługę, która jest wywoływana z poziomu aplikacji ASP.NET AJAX.  
  
\<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|webEndpointType|Ciąg, który określa typ punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
