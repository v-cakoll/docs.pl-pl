---
title: '&lt;system.serviceModel&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: c2f4a0787f6027d7f57891d4e219758c4a7054ff
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145851"
---
# <a name="ltsystemservicemodelgt"></a>&lt;system.serviceModel&gt;
Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracyjne ServiceModel Windows Communication Foundation (WCF).  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowania >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Ta sekcja definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każdej kolekcji definiuje zachowanie elementy używane przez punkty końcowe i usługi, odpowiednio. Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ta sekcja przetrzymuje kolekcję powiązań standardowych i niestandardowych. Każdy wpis jest określony przez jego unikatowy `name`. Usługi używają powiązania, łącząc je za pomocą `name`.|  
|[\<Klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Ta sekcja zawiera listę punktów końcowych, których klient używa do łączenia się z usługą.|  
|[\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Ta sekcja definiuje kontrakty COM włączone dla usługi WCF i COM interop.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|W tej sekcji można zdefiniować tylko w pliku machine.config. Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każdej kolekcji definiuje zachowanie elementy używane przez wszystkie punkty końcowe WCF i usługi na maszynie, odpowiednio.  Jeśli to zachowanie jest zdefiniowany w obu `<commonBehaviors>` i `<behaviors>` sekcje zachowanie w \<zachowania > sekcji otrzymuje preferencji.|  
|[\<Diagnostyka >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Ta sekcja zawiera ustawienia dla funkcji diagnostyki platformy WCF. Użytkownik mogą włączać i wyłączać śledzenia, liczniki wydajności i dostawcy WMI i można dodać niestandardowy komunikat filtrów.|  
|[\<Rozszerzenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Ta sekcja zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Ta sekcja definiuje zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.|  
|[\<Routing >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Ta sekcja definiuje zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych, aby wysyłać komunikaty do kiedy tabele Filtr dopasowuje wartość.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Ta sekcja definiuje typ usługi, którą Środowisko hostingu środowiskowego dla danego transportu. Jeśli w tej sekcji jest pusta, używany jest domyślny typ.|  
|[\<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Sekcja zawiera kolekcję usług. Dla każdej usługi zdefiniowane w zestawie, ten element zawiera `service` element określający ustawienia usługi.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Ta sekcja definiuje zbiór standardowych punktów końcowych, które są do ponownego użycia wstępnie skonfigurowanymi punktami końcowymi. Standardowy punkt końcowy będzie mieć jeden lub więcej adresów, powiązania i atrybuty kontraktu ustawiona na wartość stałą. Na przykład punkt końcowy odnajdywania kontrakt jest stała. Standardowe punkty końcowe umożliwia również rozszerzenie punkt końcowy usługi z nowymi właściwościami podobne do definiowania powiązań niestandardowych.|
|[\<Śledzenie >](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|Ta sekcja definiuje ustawienia śledzenia dla usługi przepływu pracy.|

### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<Konfiguracja >|Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.|  
  
## <a name="remarks"></a>Uwagi  
 Usługi WCF nie powoduje dodania elementów konfiguracji w sekcjach dotyczących innych produktów.  
  
 Usługi WCF są zdefiniowane w `services` sekcję pliku konfiguracji. Zestaw może zawierać dowolną liczbę usług. Każda usługa ma swoje własne `service` sekcji konfiguracji. Sekcji i jego zawartości definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.  
  
 Tylko usługi `name` atrybut jest wymagany.  Domyślnie, nazwa usługi w tym artykule opisano podstawowy typ środowiska CLR, używany do implementowania usługi; jednak Właściwość ConfigurationName może ulec zmianie po <xref:System.ServiceModel.ServiceContractAttribute> Aby przesłonić wymaganie typu CLR.  
  
 `behaviorConfiguration` Atrybut jest opcjonalny. Identyfikuje zachowanie usługi, używanych przez usługę. Zachowanie określone przez atrybut ten należy połączyć zachowanie usługi zdefiniowane w zakresie tego samego pliku konfiguracji (tj. tego samego pliku lub pliku nadrzędnego).  
  
 Każda usługa udostępnia jedną lub więcej punktów końcowych zdefiniowanych w `endpoint` elementu. Każdy punkt końcowy ma swój własny adres i powiązanie. Wszystkie powiązania używane w pliku konfiguracyjnym musi być zdefiniowany w zakresie pliku.  
  
 Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`. `binding` Atrybut definiuje, w której sekcji zdefiniowano powiązania. `bindingConfiguration` Atrybut definiuje, które skonfigurowanego powiązania w ramach sekcji powiązania jest używany. Sekcja powiązania można zdefiniować kilka skonfigurowanego powiązania.  
  
## <a name="example"></a>Przykład  
 To jest przykładowy plik konfiguracji usługi WCF.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
