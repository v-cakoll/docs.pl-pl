---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc45511e0e7b4644704a834f0bc08d64ff3367f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpendpointgt"></a>&lt;webHttpEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, które automatycznie dodaje [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie. Podczas zapisywania usługi REST, należy używać tego punktu końcowego.  
  
\<System. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Wartość logiczna wskazująca, czy jest włączone automatyczne wybieranie formatu.<br /><br /> Włączenie automatycznego wyboru formatu infrastruktury analizuje `Accept` nagłówka komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi. Jeśli `Accept` nagłówka nie określa formatu odpowiedniego odpowiedzi, korzysta z infrastruktury `Content-Type` komunikat żądania lub domyślny format odpowiedzi operacji.|  
|defaultOutgoingResponseFormat|Atrybut, który określa domyślny format odpowiedzi wychodzącej. Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu|  
|helpEnabled|Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączone dla punktu końcowego.|  
|webEndpointType|Ciąg określający typ punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
