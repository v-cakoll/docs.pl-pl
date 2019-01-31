---
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 7677d7f4c0ef7927fd50885bb887dccaa62a27b4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286796"
---
# <a name="standardendpoints"></a>\<standardEndpoints>
Ta sekcja konfiguracji umożliwia zdefiniowanie kolekcji standardowych punktów końcowych, które są do ponownego użycia wstępnie skonfigurowanymi punktami końcowymi. Standardowy punkt końcowy będzie mieć jeden lub więcej adresów, powiązania i atrybuty kontraktu ustawiona na wartość stałą. Na przykład punkt końcowy odnajdywania kontrakt jest stała. Standardowe punkty końcowe umożliwia również rozszerzenie punkt końcowy usługi z nowymi właściwościami podobne do definiowania powiązań niestandardowych.  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym. Usługa może opcjonalnie ogłaszają jego dostępność, wysyłając anonse online i offline, po otwarciu lub zamknięciu odpowiednio. Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elementu i używa AnnouncementClient przeprowadzić anonsów. Klient chcą nasłuchiwanie anonsu z innej usługi faktycznie działa jako usługa WCF; dlatego musisz skonfigurować punkty końcowe anonsu dla tego klienta w [ \<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji.|  
|[\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania. Po dodaniu do konfiguracji usługi, określa, gdzie nasłuchiwać komunikatów odnajdywania. Po dodaniu do konfiguracji klienta określa, gdzie wysyłać zapytania odnajdywania.|  
|[\<dynamicEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.|  
|[\<mexEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem IMetadataExchange. Ponieważ wszystkie punkty końcowe wymiany metadanych określić IMetadataExchange jako ich kontraktu, możesz użyć tego standardowego punktu, zamiast definiować po jednym dla siebie.|  
|[\<udpAnnoucementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Definiuje standardowy punkt końcowy, który jest używany przez usługi do wysłania komunikatów Anons z powiązania protokołu UDP. Ma stały kontraktu i obsługuje dwie wersje odnajdywania. Ponadto ma stałym powiązaniem UDP oraz domyślną wartość adresu określonych w specyfikacji WS-Discovery (WS-Discovery kwietnia 2005 lub w wersji 1.1 protokołu WS-Discovery). Możesz określić adres multiemisji na potrzeby wysyłania i odbierania wiadomości anonsów.|  
|[\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Definiuje standardowy punkt końcowy, który jest wstępnie konfigurowany dla operacji odnajdowania za pośrednictwem protokołu UDP powiązania multiemisji. Ten punkt końcowy ma stały kontraktu i obsługuje dwie wersje protokołu WS Discovery. Ponadto ma stały powiązanie protokołu UDP oraz domyślny adres określonych w specyfikacji WS-Discovery (WS-Discovery kwietnia 2005 lub w wersji 1.1 protokołu WS-Discovery).|  
|[\<webHttpEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, który automatycznie dodaje [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) zachowanie. Używanie tego punktu końcowego podczas pisania usługi REST.|  
|[\<webScriptEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) powiązania, który automatycznie dodaje [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie. Używanie tego punktu końcowego, gdy tworzysz usługę, która jest wywoływana z poziomu aplikacji ASP.NET AJAX.|  
|[\<workflowControlEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|Definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchamianie, wstrzymywanie, zakończenia itp).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<system.ServiceModel>|Element główny wszystkich elementów konfiguracji programu WCF.|  
  
## <a name="see-also"></a>Zobacz także
- [Standardowe punkty końcowe](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
