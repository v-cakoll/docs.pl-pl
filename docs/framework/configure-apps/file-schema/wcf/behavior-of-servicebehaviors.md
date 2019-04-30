---
title: <behavior> dla <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 89ad23a801abce9b2fe409b7e7acb1f5e9c2ac55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701102"
---
# <a name="behavior-of-servicebehaviors"></a>\<zachowanie > z \<serviceBehaviors >
`behavior` Element zawiera zbiór ustawień dotyczących zachowania usługi. Każde działanie jest indeksowane według jego `name`. Usługi można połączyć każdego zachowanie za pomocą tej nazwy `behaviorConfiguration` atrybutu [ \<punktu końcowego >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu. Dzięki temu punktów końcowych udostępnić typowych konfiguracji zachowanie bez ponownego definiowania ustawień. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
>  Zachowanie elementy specyficzne dla działań przepływu pracy Windows, takich jak [ \<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) elementu są udokumentowane w artykule [ \<zachowanie > z \< serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) strony.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie. Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|Zawiera dane konfiguracyjne dla elementu DataContractSerializer.|  
|[\<persistenceProvider>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|Określa typ implementacji dostawcy stanów stałych do użycia, jak również limit czasu na potrzeby operacji trwałości.|  
|[\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|Udostępnia wykonawczej usługa routingu umożliwia dynamiczne modyfikowanie konfiguracji routingu.|  
|[\<serviceAuthenticationManager>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|Udostępnia element konfiguracji przepływu pracy, który ustanawia na poziomie usługi ważności transmisji, wiadomości lub inicjatora...|  
|[\<serviceAuthorization>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|Określa ustawienia, które zezwalają na dostęp do operacji usługi.|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
|[\<serviceDebug>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|Określa funkcje informacji pomocy i debugowania dla usługi Windows Communication Foundation (WCF).|  
|[\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|Określa wykrywalność usługi punktów końcowych.|  
|[\<serviceMetadata>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|Określa publikację usługi metadanych i skojarzonych informacji.|  
|[\<serviceSecurityAudit>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|Określa ustawienia, które włączają inspekcję zdarzeń zabezpieczeń podczas operacji usługi.|  
|[\<serviceThrottling>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|Określa mechanizm ograniczania przepustowości usługi WCF.|  
|[\<serviceTimeouts>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|Określa limit czasu usługi.|  
|[\<workflowRuntime>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|Określa ustawienia dla wystąpienia środowiska wykonawczego przepływów pracy do hostowania usługi WCF opartego o przepływ pracy.|  
|[\<useRequestHeadersForMetadataAddress>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|Kolekcja elementów zachowanie usługi.|
