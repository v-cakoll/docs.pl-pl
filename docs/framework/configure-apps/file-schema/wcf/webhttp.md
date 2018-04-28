---
title: '&lt;webHttp&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bf92421d09f25c760f8edc5062b7b7d6276902f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="ltwebhttpgt"></a>&lt;webHttp&gt;
Ten element Określa <xref:System.ServiceModel.Description.WebHttpBehavior> dla punktu końcowego za pośrednictwem konfiguracji. To zachowanie, gdy jest używany w połączeniu z [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe zapewnia model programowania sieci Web do [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<webHttp >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Jeśli ta właściwość jest równa `true`, infrastruktura WCF Określa format najlepszy do użycia. Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności. Automatyczne wybieranie formatu można włączyć programowo lub przy użyciu konfiguracji.|  
|defaultBodyStyle|Określa domyślny styl treści zwróconych komunikatów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle> i [formatowania HTTP sieci Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Określa domyślny format odpowiedzi wychodzących dla wiadomości. Aby uzyskać więcej informacji, zobacz [formatowania HTTP sieci Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|Właściwość faultExceptionEnabled|Pobiera lub ustawia flagę określającą, czy wyjątek FaultException występuje podczas wystąpił wewnętrzny błąd serwera (kod stanu HTTP: 500) występuje.|  
|helpEnabled|Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zestaw zachowania punktu końcowego.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Obsługa integracji AJAX i notacji JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
