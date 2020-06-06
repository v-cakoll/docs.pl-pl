---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854797"
---
# \<webHttpEndpoint>
Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym [\<webHttpBinding>](webhttpbinding.md) powiązaniem, które automatycznie dodaje [\<webHttp>](webhttp.md) zachowanie. Użyj tego punktu końcowego podczas pisania usługi REST.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Wartość logiczna wskazująca, czy jest włączone automatyczne Wybieranie formatu.<br /><br /> Po włączeniu automatycznego wybierania formatu infrastruktura analizuje `Accept` nagłówek komunikatu żądania i określa najbardziej odpowiedni format odpowiedzi. Jeśli w `Accept` nagłówku nie określono odpowiedniego formatu odpowiedzi, infrastruktura używa `Content-Type` komunikatu żądania lub domyślnego formatu odpowiedzi operacji.|  
|defaultOutgoingResponseFormat|Atrybut, który określa domyślny format odpowiedzi wychodzącej. Ten atrybut jest <xref:System.ServiceModel.Web.WebMessageFormat> typu|  
|helpEnabled|Wartość logiczna wskazująca, czy strona pomocy protokołu HTTP jest włączona dla punktu końcowego.|  
|WebEndpointType|Ciąg określający typ punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
