---
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 1451105f210f34747aca337b3279821f72a19080
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362698"
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
|[\<announcementEndpoint >](announcementendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym. Usługa może opcjonalnie ogłaszają jego dostępność, wysyłając anonse online i offline, po otwarciu lub zamknięciu odpowiednio. Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [ \<serviceDiscovery >](servicediscovery.md) elementu i używa AnnouncementClient przeprowadzić anonsów. Klient chcą nasłuchiwanie anonsu z innej usługi faktycznie działa jako usługa WCF; dlatego musisz skonfigurować punkty końcowe anonsu dla tego klienta w [ \<usługi >](services.md) sekcji.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania. Po dodaniu do konfiguracji usługi, określa, gdzie nasłuchiwać komunikatów odnajdywania. Po dodaniu do konfiguracji klienta określa, gdzie wysyłać zapytania odnajdywania.|  
|[\<dynamicEndpoint>](dynamicendpoint.md)|Ten element konfiguracji definiuje standardowy punkt końcowy, który zawiera informacje, aby umożliwić aplikacji funkcjonowanie jako program kliencki, który można znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.|  
|[\<mexEndpoint>](mexendpoint.md)|Definiuje standardowy punkt końcowy ze stałym kontraktem IMetadataExchange. Ponieważ wszystkie punkty końcowe wymiany metadanych określić IMetadataExchange jako ich kontraktu, możesz użyć tego standardowego punktu, zamiast definiować po jednym dla siebie.|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Definiuje standardowy punkt końcowy, który jest używany przez usługi do wysłania komunikatów Anons z powiązania protokołu UDP. Ma stały kontraktu i obsługuje dwie wersje odnajdywania. Ponadto ma stałym powiązaniem UDP oraz domyślną wartość adresu określonych w specyfikacji WS-Discovery (WS-Discovery kwietnia 2005 lub w wersji 1.1 protokołu WS-Discovery). Możesz określić adres multiemisji na potrzeby wysyłania i odbierania wiadomości anonsów.|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|Definiuje standardowy punkt końcowy, który jest wstępnie konfigurowany dla operacji odnajdowania za pośrednictwem protokołu UDP powiązania multiemisji. Ten punkt końcowy ma stały kontraktu i obsługuje dwie wersje protokołu WS Discovery. Ponadto ma stały powiązanie protokołu UDP oraz domyślny adres określonych w specyfikacji WS-Discovery (WS-Discovery kwietnia 2005 lub w wersji 1.1 protokołu WS-Discovery).|  
|[\<webHttpEndpoint>](webhttpendpoint.md)|Definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](webhttpbinding.md) powiązania, który automatycznie dodaje [ \<webHttp >](webhttp.md) zachowanie. Używanie tego punktu końcowego podczas pisania usługi REST.|  
|[\<webScriptEndpoint>](webscriptendpoint.md)|Definiuje standardowy punkt końcowy ze stałym [ \<webHttpBinding >](webhttpbinding.md) powiązania, który automatycznie dodaje [ \<enableWebScript >](enablewebscript.md) zachowanie. Używanie tego punktu końcowego, gdy tworzysz usługę, która jest wywoływana z poziomu aplikacji ASP.NET AJAX.|  
|[\<workflowControlEndpoint>](workflowcontrolendpoint.md)|Definiuje standardowy punkt końcowy do kontroli wykonania wystąpień przepływu pracy (Tworzenie, uruchamianie, wstrzymywanie, zakończenia itp).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<system.ServiceModel>|Element główny wszystkich elementów konfiguracji programu WCF.|  
  
## <a name="see-also"></a>Zobacz także
- [Standardowe punkty końcowe](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
