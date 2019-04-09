---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 795e61b9054d2ea9276970988018c50099bcbe17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129652"
---
# <a name="webhttp"></a>\<webHttp>
Ten element Określa <xref:System.ServiceModel.Description.WebHttpBehavior> w punkcie końcowym za pośrednictwem konfiguracji. To zachowanie, gdy jest używana w połączeniu z [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) Powiązanie standardowe, umożliwia modelu programowania w sieci Web dla usługi Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<webHttp>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Jeśli ta właściwość jest równa `true`, infrastruktura WCF Określa format najlepszy do użycia. Automatyczne wybieranie formatu jest domyślnie wyłączona dla zapewnienia zgodności. Można włączyć automatyczne wybieranie formatu programowo lub za pomocą konfiguracji.|  
|defaultBodyStyle|Określa domyślny styl treści zwróconych komunikatów. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Web.WebMessageBodyStyle> i [WCF Web HTTP formatowanie](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Określa domyślny format odpowiedzi wychodzących dla wiadomości. Aby uzyskać więcej informacji, zobacz [WCF Web HTTP formatowanie](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Pobiera lub ustawia flagę określającą, czy wyjątek FaultException podczas wystąpił wewnętrzny błąd serwera (kod stanu HTTP: 500) występuje.|  
|helpEnabled|Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zestaw zachowań punktu końcowego.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Obsługa integracji AJAX i notacji JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
