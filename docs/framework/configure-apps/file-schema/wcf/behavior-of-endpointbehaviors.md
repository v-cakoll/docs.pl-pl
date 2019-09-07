---
title: <behavior> dla <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 81c9ec7bd82fa0b947e438632b293ab9110067f5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398236"
---
# <a name="behavior-of-endpointbehaviors"></a>\<zachowanie > \<endpointBehaviors >
`behavior` Element zawiera kolekcję ustawień zachowania punktu końcowego. Każde działanie jest indeksowane według jego `name`. Punkty końcowe mogą łączyć się z każdym zachowaniem przy użyciu tej nazwy. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zachowania**  
  
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
|nazwa|Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie. Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta w usłudze.|  
|[\<callbackDebug>](callbackdebug.md)|Określa debugowanie usługi dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).|  
|[\<callbackTimeouts>](callbacktimeouts.md)|Określa limit czasu dla wywołania zwrotnego klienta.|  
|[\<clientVia >](clientvia.md)|Określa trasę, którą powinien wykonać wiadomość.|  
|[\<dataContractSerializer>](datacontractserializer.md)|Zawiera dane konfiguracyjne dla elementu DataContractSerializer.|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|Określa zachowanie punktu końcowego, które umożliwia usłudze wysyłanie odpowiedzi asynchronicznie.|  
|[\<enableWebScript >](enablewebscript.md)|Włącza zachowanie punktu końcowego, który umożliwia korzystanie z usługi z ASP.NET AJAX stron sieci Web. Zachowanie powinno być używane tylko w połączeniu ze \<standardowym powiązaniem WebHttpBinding > \<lub elementem powiązania > webMessageEncoding.|  
|[\<endpointDiscovery >](endpointdiscovery.md)|Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.|  
|[\<soapProcessing >](soapprocessing.md)|Definiuje zachowanie punktu końcowego klienta używane do organizowania komunikatów między różnymi typami powiązań i wersjami komunikatów.|  
|[\<synchronousReceive >](synchronousreceive-element.md)|Określa zachowanie w czasie wykonywania w przypadku otrzymywania wiadomości w usłudze lub aplikacji klienckiej. Nie ma żadnych atrybutów ani elementów podrzędnych.|  
|[\<transactedBatching >](transactedbatching.md)|Określa, czy przetwarzanie wsadowe transakcji jest obsługiwane dla operacji odbioru.|  
|[\<webHttp>](webhttp.md)|Określa WebHttpBehavior w punkcie końcowym za pomocą konfiguracji. Takie zachowanie, gdy jest \<używane w połączeniu z standardowym powiązaniem WebHttpBinding >, włącza model programowania sieci Web dla usługi WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endpointBehaviors >](endpointbehaviors.md)|Kolekcja elementów zachowania punktu końcowego.|
