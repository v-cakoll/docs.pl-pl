---
title: '&lt;behavior&gt; w &lt;endpointBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: e275fbc1b14469553094a4df838930be53937de2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363302"
---
# <a name="ltbehaviorgt-of-ltendpointbehaviorsgt"></a>&lt;behavior&gt; w &lt;endpointBehaviors&gt;
`behavior` Element zawiera kolekcję ustawień zachowania dla punktu końcowego. Każde działanie jest indeksowane według jego `name`. Punkty końcowe można połączyć z każdym zachowanie za pośrednictwem tej nazwy. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
  
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
|nazwa|Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie. Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Określa poświadczenia używane do uwierzytelniania klienta do usługi.|  
|[\<callbackDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbackdebug.md)|Określa usługę debugowania dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).|  
|[\<callbackTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbacktimeouts.md)|Określa limit czasu dla wywołania zwrotnego klienta.|  
|[\<clientVia >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientvia.md)|Określa, że powinno zająć trasy wiadomości.|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer.md)|Zawiera dane konfiguracyjne dla elementu DataContractSerializer.|  
|[\<dispatcherSynchronization >](../../../../../docs/framework/configure-apps/file-schema/wcf/dispatchersynchronization.md)|Określa zachowanie punktu końcowego, który włącza usługę Aby wysłać odpowiedzi asynchronicznie.|  
|[\<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)|Włącza zachowanie punktu końcowego, który pozwala na korzystanie z usługi z ASP.NET AJAX stron sieci web. Zachowanie należy używać tylko w połączeniu z albo \<webHttpBinding > Powiązanie standardowe, lub \<webMessageEncoding > elementu powiązania.|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|Określa różne ustawienia odkrywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszystkich jego rozszerzenia niestandardowe dla jego metadanych.|  
|[\<soapProcessing >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)|Określa zachowanie punktu końcowego klienta używany do organizowania wiadomości między inne powiązanie typy i wersje komunikatów.|  
|[\<synchronousReceive >](../../../../../docs/framework/configure-apps/file-schema/wcf/synchronousreceive-element.md)|Określa zachowanie czasu wykonania do odbierania wiadomości w aplikacji usługi lub klienta. Nie ma żadnych atrybutów ani elementów podrzędnych.|  
|[\<transactedBatching >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactedbatching.md)|Określa, czy transakcja tworzenia plików wsadowych jest obsługiwane dla operacji odbioru.|  
|[\<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)|Określa WebHttpBehavior dla punktu końcowego za pośrednictwem konfiguracji. To zachowanie, gdy jest używany w połączeniu z \<webHttpBinding > Powiązanie standardowe zapewnia model programowania sieci Web dla usługi WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<endpointBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|Kolekcja elementów zachowania punktu końcowego.|
