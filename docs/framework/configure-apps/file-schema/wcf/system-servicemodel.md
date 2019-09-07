---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399446"
---
# <a name="systemservicemodel"></a>\<system.serviceModel>
Ta sekcja konfiguracji zawiera wszystkie elementy konfiguracji programu Windows Communication Foundation (WCF).  

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp; **\<> System. serviceModel**  
  
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
|[\<> zachowań](behaviors.md)|Ta sekcja definiuje dwie kolekcje podrzędne o `endpointBehaviors` nazwach i `serviceBehaviors`.  Każda kolekcja definiuje elementy zachowań używane odpowiednio przez punkty końcowe i usługi. Każdy element zachowanie jest określony przez jego unikatowy `name` atrybutu.|  
|[\<> powiązań](bindings.md)|Ta sekcja zawiera kolekcję powiązań standardowych i niestandardowych. Każdy wpis jest identyfikowany przez jego `name`unikatowy. Usługi używają powiązań przez łączenie ich przy użyciu `name`.|  
|[\<> klienta](client.md)|Ta sekcja zawiera listę punktów końcowych używanych przez klienta do nawiązywania połączenia z usługą.|  
|[\<comContracts>](comcontracts.md)|Ta sekcja zawiera definicje umów COM włączonych dla usług WCF i współdziałania z modelem COM.|  
|[\<commonBehaviors >](commonbehaviors.md)|Tę sekcję można zdefiniować tylko w pliku Machine. config. Definiuje dwie kolekcje podrzędne o `endpointBehaviors` nazwach `serviceBehaviors`i.  Każda kolekcja definiuje elementy zachowań używane przez wszystkie punkty końcowe i usługi WCF odpowiednio na maszynie.  Jeśli zachowanie jest zdefiniowane w obu `<commonBehaviors>` `<behaviors>` sekcjach \<, zachowanie w sekcji zachowań > ma pierwszeństwo.|  
|[\<> diagnostyki](diagnostics.md)|Ta sekcja zawiera ustawienia funkcji diagnostyki WCF. Użytkownik może włączyć/wyłączyć śledzenie, liczniki wydajności i dostawcę WMI, a także może dodawać niestandardowe filtry komunikatów.|  
|[\<> rozszerzeń](extensions-section.md)|Ta sekcja zawiera kolekcję rozszerzeń, które umożliwiają użytkownikowi tworzenie powiązań zdefiniowanych przez użytkownika, zachowań i innych aspektów rozszerzeń.|  
|[\<protocolMapping >](protocolmapping.md)|Ta sekcja definiuje zestaw domyślnego mapowania protokołów między schematami protokołu transportowego (np. http, net. TCP, net. pipe itp.) i powiązania WCF.|  
|[\<> routingu](routing.md)|Ta sekcja definiuje zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu definiujące docelowe punkty końcowe do wysyłania komunikatów, gdy filtruje dopasowania.|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|W tej sekcji zdefiniowano typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu. Jeśli ta sekcja jest pusta, używany jest typ domyślny.|  
|[\<> usług](services.md)|Sekcja zawiera kolekcję usług. Dla każdej usługi zdefiniowanej w zestawie ten element zawiera `service` element określający ustawienia dla usługi.|  
|[\<standardEndpoints >](standardendpoints.md)|Ta sekcja definiuje zbiór standardowych punktów końcowych, które są wstępnie skonfigurowanymi punktami końcowymi wielokrotnego użytku. Standardowy punkt końcowy będzie miał co najmniej jeden atrybut Address, Binding i Contract ustawiony na wartość stałą. Na przykład w punkcie końcowym odnajdywania kontrakt jest ustalony. Możesz również użyć standardowych punktów końcowych, aby zwiększyć punkt końcowy usługi z nowymi właściwościami podobnymi do definiowania powiązań niestandardowych.|
|[\<Śledzenie >](tracking-of-wcf.md)|W tej sekcji zdefiniowano ustawienia śledzenia dla usługi przepływu pracy.|

### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<> konfiguracji|Element główny dla wszystkich elementów konfiguracji w PLiku konfiguracji PLatformy .NET.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja WCF nie dodaje elementów do sekcji konfiguracji innych produktów.  
  
 Usługi WCF są zdefiniowane w `services` sekcji pliku konfiguracji. Zestaw może zawierać dowolną liczbę usług. Każda usługa ma swoją własną `service` sekcję konfiguracyjną. Sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.  
  
 Wymagany jest tylko `name` atrybut usługi.  Domyślnie nazwa usługi opisuje źródłowy typ CLR używany do implementowania usługi. można jednak zmienić właściwość ConfigurationName w <xref:System.ServiceModel.ServiceContractAttribute> celu zastąpienia wymagania dotyczącego typu CLR.  
  
 `behaviorConfiguration` Atrybut jest opcjonalny. Identyfikuje zachowanie usługi używane przez usługę. Zachowanie określone przez ten atrybut musi łączyć się z zachowaniem usługi zdefiniowanym w zakresie tego samego pliku konfiguracji (tj. tym samym lub plikiem nadrzędnym).  
  
 Każda usługa ujawnia jeden lub więcej punktów końcowych zdefiniowanych `endpoint` w elemencie. Każdy punkt końcowy ma własny adres i powiązanie. Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku.  
  
 Powiązania są połączone z punktami końcowymi przez kombinację `name` atrybutów `bindingConfiguration`i. `binding` Atrybut określa, w którym sekcji jest zdefiniowane powiązanie. `bindingConfiguration` Atrybut definiuje skonfigurowane powiązanie w sekcji powiązania. Sekcja powiązania może definiować kilka skonfigurowanych powiązań.  
  
## <a name="example"></a>Przykład  
 Jest to przykład pliku konfiguracji WCF.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
