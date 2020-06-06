---
title: <behavior> dla <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139733"
---
# <a name="behavior-of-servicebehaviors"></a>\<behavior> dla \<serviceBehaviors>
`behavior` Element zawiera zbiór ustawień dotyczących zachowania usługi. Każde działanie jest indeksowane według jego `name`. Usługi mogą łączyć się z każdym zachowaniem za pomocą tej nazwy przy użyciu `behaviorConfiguration` atrybutu [\<endpoint>](endpoint-element.md) elementu. Dzięki temu punktów końcowych udostępnić typowych konfiguracji zachowanie bez ponownego definiowania ustawień. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
> Elementy zachowań specyficzne dla działań przepływu pracy systemu Windows, takie jak [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, są udokumentowane [ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) na stronie.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
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
|name|Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie. Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|Zawiera dane konfiguracyjne dla elementu DataContractSerializer.|  
|[\<persistenceProvider>](persistenceprovider.md)|Określa typ implementacji dostawcy trwałości, a także limit czasu na potrzeby operacji trwałości.|  
|[\<routing>](routing-of-servicebehavior.md)|Zapewnia dostęp do usługi routingu w czasie wykonywania w celu umożliwienia dynamicznej modyfikacji konfiguracji routingu.|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|Zawiera element konfiguracji przepływu pracy, który ustala na poziomie usługi ważność transmisji, wiadomości lub nadawcy.|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|Określa ustawienia, które zezwalają na dostęp do operacji usługi.|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.|  
|[\<serviceDebug>](servicedebug.md)|Określa funkcje debugowania i pomocy dla usługi Windows Communication Foundation (WCF).|  
|[\<serviceDiscovery>](servicediscovery.md)|Określa możliwość odnajdywania punktów końcowych usługi.|  
|[\<serviceMetadata>](servicemetadata.md)|Określa publikację metadanych usługi i skojarzonych z nią informacji.|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|Określa ustawienia, które włączają inspekcję zdarzeń zabezpieczeń podczas operacji usługi.|  
|[\<serviceThrottling>](servicethrottling.md)|Określa mechanizm ograniczania przepustowości usługi WCF.|  
|[\<serviceTimeouts>](servicetimeouts.md)|Określa limit czasu dla usługi.|  
|[\<workflowRuntime>](workflowruntime.md)|Określa ustawienia dla wystąpienia elementu WorkflowRuntime do hostowania usług WCF opartych na przepływie pracy.|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|Umożliwia pobieranie informacji o adresie metadanych z nagłówków komunikatów żądania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|Kolekcja elementów zachowanie usługi.|
