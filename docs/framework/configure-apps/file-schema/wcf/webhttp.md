---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940504"
---
# <a name="webhttp"></a>\<webHttp>
Ten element określa <xref:System.ServiceModel.Description.WebHttpBehavior> punkt końcowy za pomocą konfiguracji. Takie zachowanie, gdy jest [ \<](webhttpbinding.md) używane w połączeniu z standardowym powiązaniem WebHttpBinding >, włącza model programowania sieci Web dla usługi Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
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
|automaticFormatSelectionEnabled|Jeśli ta właściwość jest ustawiona na `true`, Infrastruktura WCF określa najlepszy format do użycia. Automatyczne wybieranie formatu jest domyślnie wyłączone w celu zapewnienia zgodności z poprzednimi wersjami. Automatyczne wybieranie formatu można włączyć programowo lub za pomocą konfiguracji.|  
|defaultBodyStyle|Określa domyślny styl treści zwróconych komunikatów. Aby uzyskać więcej informacji, <xref:System.ServiceModel.Web.WebMessageBodyStyle> Zobacz i [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.|  
|defaultOutgoingResponseFormat|Określa domyślny format odpowiedzi wychodzącej dla komunikatów. Aby uzyskać więcej informacji, zobacz temat [Formatowanie http sieci Web](../../../wcf/feature-details/wcf-web-http-formatting.md)w programie WCF.|  
|faultExceptionEnabled|Pobiera lub ustawia flagę określającą, czy element FaultException jest generowany w przypadku wewnętrznego błędu serwera (kod stanu HTTP: 500) występuje.|  
|helpEnabled|Pobiera lub ustawia wartość określającą, czy strona pomocy jest włączona.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zestaw zachowań punktów końcowych.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Obsługa integracji AJAX i notacji JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
