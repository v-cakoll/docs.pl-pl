---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02bf740794b1551d3b130922939dbb27e572578e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemservicemodelgt"></a>&lt;system.serviceModel&gt;
Ta sekcja konfiguracji zawiera wszystkie [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] elementy konfiguracyjne ServiceModel.  
  
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
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowania >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Ta sekcja definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każda kolekcja definiuje elementy zachowanie odpowiednio używane przez punkty końcowe i usług. Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ta sekcja przetrzymuje kolekcję powiązań standardowych i niestandardowych. Każdy wpis jest identyfikowany przez jego unikatowy `name`. Usługi używają powiązania łącząc je za pomocą `name`.|  
|[\<Klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Ta sekcja zawiera listę punktów końcowych, które klient używa do łączenia się z usługą.|  
|[\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Ta sekcja definiuje kontrakty COM włączone dla usługi WCF i COM interop.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|W tej sekcji można zdefiniować tylko w pliku machine.config. Definiuje dwie kolekcje elementów podrzędnych o nazwie `endpointBehaviors` i `serviceBehaviors`.  Każda kolekcja definiuje używane przez wszystkie elementy zachowanie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] punktów końcowych i usług na komputerze odpowiednio.  Jeśli to zachowanie jest zdefiniowany zarówno `<commonBehaviors>` i `<behaviors>` sekcje zachowanie w \<zachowania > sekcji podano preferencji.|  
|[\<Rozszerzenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Ta sekcja zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.|  
|[\<Diagnostyka >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Ta sekcja zawiera ustawienia dla funkcji diagnostyki usługi WCF. Użytkownik może Włączanie/wyłączanie śledzenia, liczniki wydajności i dostawcy WMI i dodać filtry niestandardowe komunikatów.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Ta sekcja definiuje zestawu domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF.|  
|[\<Routing >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Ta sekcja definiuje zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabele definiują docelowych punktów końcowych do wysyłania komunikatów do gdy kryteria filtru.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Ta sekcja definiuje typ usługi, którą Środowisko hostingu środowiskowego dla danego transportu. Jeśli w tej sekcji jest pusta, domyślny typ jest używany.|  
|[\<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Sekcja zawiera kolekcję usług. Dla każdej usługi zdefiniowane w zestawie, ten element zawiera `service` element Określanie ustawień usługi.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Ta sekcja definiuje kolekcji standardowych punktów końcowych, które są do ponownego użycia wstępnie skonfigurowanymi punktami końcowymi. Standardowy punkt końcowy będzie mieć jeden lub więcej z address, binding i atrybuty kontraktu ustawioną wartością stałą. Na przykład w punkcie końcowym odnajdywania kontrakt jest stała. Umożliwia także standardowych punktów końcowych do rozszerzenia punktu końcowego usługi z nowymi właściwościami podobne do definiowania niestandardowego powiązania.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<Konfiguracja >|Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nie dodać elementy do sekcji konfiguracji innych produktów.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]usługi są zdefiniowane w `services` sekcji pliku konfiguracji. Zestaw może zawierać dowolną liczbę usług. Każda usługa ma własną `service` sekcji konfiguracji. Sekcji i jego zawartości definiowanie kontraktu usługi, zachowania i punkty końcowe określonej usługi.  
  
 Tylko usługi `name` atrybut jest wymagany.  Domyślnie nazwa usługi w tym artykule opisano podstawowy typ CLR używane do implementowania usługi; Jednak możesz zmienić właściwość ConfigurationName na <xref:System.ServiceModel.ServiceContractAttribute> Aby przesłonić wymaganie typu CLR.  
  
 `behaviorConfiguration` Atrybutu jest opcjonalny. Identyfikuje zachowanie usługi używane przez usługę. Zachowanie określonego przez tego atrybutu musi połączyć zachowania usługi, zdefiniowanego w zakresie pliku konfiguracyjnym (tj. tego samego pliku lub pliku nadrzędnego).  
  
 Każda usługa przedstawia jedną lub więcej punktów końcowych zdefiniowanych w `endpoint` elementu. Każdy punkt końcowy ma własny adres i powiązanie. Wszystkie powiązania używane w pliku konfiguracji musi być zdefiniowana w zakresie pliku.  
  
 Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`. `binding` Atrybut definiuje, w której sekcji zdefiniowano powiązania. `bindingConfiguration` Atrybut definiuje, które skonfigurowanego powiązania w sekcji binding jest używany. Powiązania sekcji można określić kilka skonfigurowanego powiązania.  
  
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
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
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
