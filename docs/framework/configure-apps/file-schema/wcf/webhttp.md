---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399165"
---
# \<webHttp>
Ten element określa <xref:System.ServiceModel.Description.WebHttpBehavior> punkt końcowy za pomocą konfiguracji. Takie zachowanie, które jest używane w połączeniu ze [\<webHttpBinding>](webhttpbinding.md) standardowym powiązaniem, umożliwia model programowania sieci Web dla usługi Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Jeśli ta właściwość jest ustawiona na `true` , Infrastruktura WCF określa najlepszy format do użycia. Automatyczne wybieranie formatu jest domyślnie wyłączone w celu zapewnienia zgodności z poprzednimi wersjami. Automatyczne wybieranie formatu można włączyć programowo lub za pomocą konfiguracji.|  
|defaultBodyStyle|Określa domyślny styl treści zwróconych komunikatów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle> i [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.|  
|defaultOutgoingResponseFormat|Określa domyślny format odpowiedzi wychodzącej dla komunikatów. Aby uzyskać więcej informacji, zobacz temat [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.|  
|faultExceptionEnabled|Pobiera lub ustawia flagę określającą, czy wyjątek FaultException występuje w przypadku wewnętrznego błędu serwera (kod stanu HTTP: 500).|  
|helpEnabled|Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Określa zestaw zachowań punktów końcowych.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Obsługa integracji AJAX i notacji JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
