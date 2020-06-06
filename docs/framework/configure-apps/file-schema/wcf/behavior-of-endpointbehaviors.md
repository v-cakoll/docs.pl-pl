---
title: <behavior> dla <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140811"
---
# <a name="behavior-of-endpointbehaviors"></a>\<behavior> dla \<endpointBehaviors>
`behavior`Element zawiera kolekcję ustawień zachowania punktu końcowego. Każde działanie jest indeksowane według jego `name`. Punkty końcowe mogą łączyć się z każdym zachowaniem przy użyciu tej nazwy. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|name|Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie. Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta w usłudze.|  
|[\<callbackDebug>](callbackdebug.md)|Określa debugowanie usługi dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).|  
|[\<callbackTimeouts>](callbacktimeouts.md)|Określa limit czasu dla wywołania zwrotnego klienta.|  
|[\<clientVia>](clientvia.md)|Określa trasę, którą powinien wykonać wiadomość.|  
|[\<dataContractSerializer>](datacontractserializer.md)|Zawiera dane konfiguracyjne dla elementu DataContractSerializer.|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|Określa zachowanie punktu końcowego, które umożliwia usłudze wysyłanie odpowiedzi asynchronicznie.|  
|[\<enableWebScript>](enablewebscript.md)|Włącza zachowanie punktu końcowego, który umożliwia korzystanie z usługi z ASP.NET AJAX stron sieci Web. Zachowanie powinno być używane tylko w połączeniu ze \<webHttpBinding> standardowym powiązaniem lub \<webMessageEncoding> elementem powiązania.|  
|[\<endpointDiscovery>](endpointdiscovery.md)|Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.|  
|[\<soapProcessing>](soapprocessing.md)|Definiuje zachowanie punktu końcowego klienta używane do organizowania komunikatów między różnymi typami powiązań i wersjami komunikatów.|  
|[\<synchronousReceive>](synchronousreceive-element.md)|Określa zachowanie w czasie wykonywania w przypadku otrzymywania wiadomości w usłudze lub aplikacji klienckiej. Nie ma żadnych atrybutów ani elementów podrzędnych.|  
|[\<transactedBatching>](transactedbatching.md)|Określa, czy przetwarzanie wsadowe transakcji jest obsługiwane dla operacji odbioru.|  
|[\<webHttp>](webhttp.md)|Określa WebHttpBehavior w punkcie końcowym za pomocą konfiguracji. Takie zachowanie, gdy jest używane w połączeniu ze \<webHttpBinding> standardowym powiązaniem, umożliwia model programowania sieci Web dla usługi WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|Kolekcja elementów zachowania punktu końcowego.|
