---
title: Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
description: Dowiedz się, jak zaimplementować interfejsy zachowań w aplikacjach WCF i dodać je do opisu lub punktu końcowego usługi albo programowo lub w pliku konfiguracji.
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: fc297f593b744d69cb09a33be6816fb646f88b67
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247588"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
Zachowania umożliwiają modyfikowanie zachowania domyślnego i Dodawanie rozszerzeń niestandardowych, które sprawdzają i weryfikują konfigurację usługi lub modyfikują zachowanie środowiska uruchomieniowego w aplikacjach klienckich i usług Windows Communication Foundation (WCF). W tym temacie opisano interfejsy zachowań, sposób ich implementacji oraz sposób ich dodawania do opisu usługi (w aplikacji usługi) lub punktu końcowego (w aplikacji klienckiej) programowo lub w pliku konfiguracji. Aby uzyskać więcej informacji o używaniu zachowań dostarczonych przez system, zobacz [Określanie zachowania usługi w czasie wykonywania](../specifying-service-run-time-behavior.md) i [Określanie zachowania klienta w czasie wykonywania](../specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Zachowania  
 Typy zachowań są dodawane do obiektów opisu punktu końcowego usługi lub usługi (odpowiednio do usługi lub klienta) przed użyciem tych obiektów przez Windows Communication Foundation (WCF), aby utworzyć środowisko uruchomieniowe, które wykonuje usługę WCF lub klienta WCF. Gdy te zachowania są wywoływane podczas procesu konstruowania środowiska uruchomieniowego, są w stanie uzyskać dostęp do właściwości i metod środowiska uruchomieniowego, które modyfikują środowisko uruchomieniowe skonstruowane przez kontrakt, powiązania i adresy.  
  
### <a name="behavior-methods"></a>Metody zachowań  
 Wszystkie zachowania mają `AddBindingParameters` metodę, `ApplyDispatchBehavior` metodę, `Validate` metodę i `ApplyClientBehavior` metodę z jednym wyjątkiem: ponieważ <xref:System.ServiceModel.Description.IServiceBehavior> nie można wykonać w kliencie, nie implementuje `ApplyClientBehavior` .  
  
- Użyj `AddBindingParameters` metody, aby zmodyfikować lub dodać obiekty niestandardowe do kolekcji, do której niestandardowe powiązania mogą uzyskać dostęp do ich użycia podczas konstruowania środowiska uruchomieniowego. Na przykład, w jaki sposób określono wymagania dotyczące ochrony, które mają wpływ na sposób kompilowania kanału, ale nie są znane przez dewelopera kanału.  
  
- Użyj `Validate` metody, aby sprawdzić drzewo opisu i odpowiedni obiekt środowiska uruchomieniowego, aby upewnić się, że jest on zgodny z określonym zestawem kryteriów.  
  
- Użyj `ApplyDispatchBehavior` metod i, `ApplyClientBehavior` Aby przejrzeć drzewo opis i zmodyfikować środowisko uruchomieniowe dla określonego zakresu w usłudze lub kliencie. Można także również wstawiać obiekty rozszerzeń.  
  
    > [!NOTE]
    > Chociaż drzewo opisu jest dostępne w tych metodach, jest przeznaczone tylko do celów badawczych. Jeśli drzewo opisów jest modyfikowane, zachowanie jest niezdefiniowane.  
  
 Właściwości, które można modyfikować, oraz interfejsy dostosowywania, które można zaimplementować, są dostępne za pomocą klas środowiska uruchomieniowego usługi i klienta. Typy usług są <xref:System.ServiceModel.Dispatcher.DispatchRuntime> <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasami i. Typy klientów są <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.ClientOperation> klasami i. <xref:System.ServiceModel.Dispatcher.ClientRuntime>Klasy i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> to punkty wejścia rozszerzalności umożliwiające dostęp odpowiednio do właściwości środowiska uruchomieniowego i kolekcji rozszerzeń dla całego klienta i usługi. Podobnie <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy i właściwości środowiska uruchomieniowego operacji usługi i kolekcji rozszerzeń są odpowiednio uwidaczniane. Można jednak uzyskać dostęp do szerszego obiektu środowiska uruchomieniowego w zakresie z obiektu środowiska uruchomieniowego operacji i odwrotnie, jeśli jest to konieczne.  
  
> [!NOTE]
> Aby zapoznać się z omówieniem właściwości środowiska uruchomieniowego i typów rozszerzeń, których można użyć w celu zmodyfikowania zachowania klienta, zobacz [Rozszerzanie klientów](extending-clients.md). Omówienie właściwości środowiska uruchomieniowego i typów rozszerzeń, których można użyć w celu zmodyfikowania zachowania wykonywania dyspozytora usługi, znajdziesz w temacie [rozszerzanie elementów wysyłających](extending-dispatchers.md).  
  
 Większość użytkowników programu WCF nie współdziała bezpośrednio ze środowiskiem uruchomieniowym. zamiast nich używają podstawowych konstrukcji programistycznych, takich jak punkty końcowe, kontrakty, powiązania, adresy i atrybuty zachowań dla klas lub zachowań w plikach konfiguracyjnych. Te konstrukcje składają się na *drzewo opisów*, która stanowi kompletną specyfikację konstruowania środowiska uruchomieniowego w celu obsługi usługi lub klienta opisanego przez drzewo opisu.  
  
 W programie WCF istnieją cztery rodzaje zachowań:  
  
- Zachowania usługi ( <xref:System.ServiceModel.Description.IServiceBehavior> typy) umożliwiają dostosowanie całego środowiska uruchomieniowego usługi, w tym <xref:System.ServiceModel.ServiceHostBase> .  
  
- Zachowania punktów końcowych ( <xref:System.ServiceModel.Description.IEndpointBehavior> typy) umożliwiają dostosowanie punktów końcowych usługi i skojarzonych z nimi <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiektów.  
  
- Zachowania kontraktowe ( <xref:System.ServiceModel.Description.IContractBehavior> typy) umożliwiają dostosowanie zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas i w aplikacjach klientów, jak i usług.  
  
- Zachowania operacji ( <xref:System.ServiceModel.Description.IOperationBehavior> typy) umożliwiają <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> ponowne dostosowanie klas i, w przypadku klienta i usługi.  
  
 Można dodać te zachowania do różnych obiektów opisu przez zaimplementowanie atrybutów niestandardowych, używanie plików konfiguracji aplikacji lub bezpośrednio przez dodanie ich do kolekcji zachowań na odpowiednim obiekcie opisu. Należy jednak dodać do opisu usługi lub obiektu opisu punktu końcowego usługi przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601> .  
  
### <a name="behavior-scopes"></a>Zakresy zachowań  
 Istnieją cztery typy zachowań, z których każdy odpowiada konkretnemu zakresowi dostępu do środowiska uruchomieniowego.  
  
#### <a name="service-behaviors"></a>Zachowania usługi  
 Zachowania usługi, które implementują <xref:System.ServiceModel.Description.IServiceBehavior> , są podstawowym mechanizmem, za pomocą którego można modyfikować całe środowisko uruchomieniowe usługi. Istnieją trzy mechanizmy dodawania zachowań usługi do usługi.  
  
1. Użycie atrybutu w klasie usługi.  Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany, <xref:System.ServiceModel.ServiceHost> implementacja używa odbicia w celu odnalezienia zestawu atrybutów dla typu usługi. Jeśli którykolwiek z tych atrybutów jest implementacją programu <xref:System.ServiceModel.Description.IServiceBehavior> , są one dodawane do kolekcji zachowań w systemie <xref:System.ServiceModel.Description.ServiceDescription> . Dzięki temu te zachowania mogą uczestniczyć w konstruowaniu czasu wykonywania usługi.  
  
2. Programistyczne Dodawanie zachowania do kolekcji zachowań w <xref:System.ServiceModel.Description.ServiceDescription> . Można to osiągnąć przy użyciu następujących wierszy kodu:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementacja niestandardowa <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , która rozszerza konfigurację. Umożliwia to korzystanie z zachowania usługi z plików konfiguracji aplikacji.  
  
 Przykłady zachowań usługi w programie WCF obejmują <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybut, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> i <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.  
  
#### <a name="contract-behaviors"></a>Zachowania kontraktów  
 Zachowania kontraktowe, które implementują interfejs, służą do rozbudowania <xref:System.ServiceModel.Description.IContractBehavior> środowiska wykonawczego klienta i usługi w ramach kontraktu.  
  
 Istnieją dwa mechanizmy dodawania zachowań kontraktu do kontraktu.  Pierwszy mechanizm polega na utworzeniu atrybutu niestandardowego, który będzie używany w interfejsie kontraktu. Gdy interfejs kontraktu jest przenoszona do programu <xref:System.ServiceModel.ServiceHost> lub a <xref:System.ServiceModel.ChannelFactory%601> , WCF bada atrybuty interfejsu. Jeśli atrybuty są implementacjami programu <xref:System.ServiceModel.Description.IContractBehavior> , są one dodawane do kolekcji zachowań na <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> utworzonej dla tego interfejsu.  
  
 Można również zaimplementować <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> w atrybucie zachowanie niestandardowej kontraktu. W takim przypadku zachowanie jest następujące w przypadku zastosowania do:  
  
 • Interfejs kontraktu. W takim przypadku zachowanie jest stosowane do wszystkich kontraktów tego typu w dowolnym punkcie końcowym, a WCF ignoruje wartość <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> właściwości.  
  
 • Klasa usługi. W takim przypadku zachowanie jest stosowane tylko do punktów końcowych, których kontrakt jest wartością <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> właściwości.  
  
 • Klasa wywołania zwrotnego. W takim przypadku zachowanie jest stosowane do punktu końcowego klienta dupleksowego i WCF ignoruje wartość <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> właściwości.  
  
 Drugim mechanizmem jest dodanie zachowania do kolekcji zachowań w <xref:System.ServiceModel.Description.ContractDescription> .  
  
 Przykłady zachowań kontraktu w programie WCF obejmują <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atrybut. Więcej informacji i przykład można znaleźć w temacie Reference.  
  
#### <a name="endpoint-behaviors"></a>Zachowania punktu końcowego  
 Zachowania punktu końcowego, które implementują <xref:System.ServiceModel.Description.IEndpointBehavior> , są podstawowym mechanizmem, za pomocą którego można modyfikować cały czas wykonywania usługi lub klienta dla określonego punktu końcowego.  
  
 Istnieją dwa mechanizmy dodawania do usługi zachowań punktów końcowych.  
  
1. Dodaj zachowanie do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwości.  
  
2. Implementowanie niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , który rozszerza konfigurację.  
  
 Więcej informacji i przykład można znaleźć w temacie Reference.  
  
#### <a name="operation-behaviors"></a>Zachowania operacji  
 Zachowania operacji, które implementują <xref:System.ServiceModel.Description.IOperationBehavior> interfejs, służą do rozszerania zarówno klienta, jak i usługi środowiska uruchomieniowego dla każdej operacji.  
  
 Istnieją dwa mechanizmy dodawania zachowań operacji do operacji. Pierwszy mechanizm polega na utworzeniu atrybutu niestandardowego, który będzie używany w metodzie, która modeluje operację. Gdy operacja jest dodawana do albo <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.ChannelFactory> , WCF dodaje wszelkie <xref:System.ServiceModel.Description.IOperationBehavior> atrybuty do kolekcji zachowań na <xref:System.ServiceModel.Description.OperationDescription> utworzonej dla tej operacji.  
  
 Drugim mechanizmem jest bezpośrednie dodanie zachowania do kolekcji zachowań na skonstruowanej <xref:System.ServiceModel.Description.OperationDescription> .  
  
 Przykłady zachowań operacji w programie WCF obejmują <xref:System.ServiceModel.OperationBehaviorAttribute> i <xref:System.ServiceModel.TransactionFlowAttribute> .  
  
 Więcej informacji i przykład można znaleźć w temacie Reference.  
  
### <a name="using-configuration-to-create-behaviors"></a>Używanie konfiguracji do tworzenia zachowań  
 Zachowanie usługi i punktu końcowego oraz kontrakty mogą być przeznaczone do określenia w kodzie lub przy użyciu atrybutów; można skonfigurować tylko zachowania usługi i punktu końcowego za pomocą aplikacji lub plików konfiguracji sieci Web. Uwidacznianie zachowań przy użyciu atrybutów pozwala deweloperom określić zachowanie w czasie kompilacji, którego nie można dodać, usunąć ani zmodyfikować w czasie wykonywania. Jest to często odpowiednie dla zachowań, które są zawsze wymagane do poprawnego działania usługi (na przykład parametrów związanych z transakcjami do <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> atrybutu). Udostępnianie zachowań przy użyciu konfiguracji pozwala deweloperom na pozostawienie specyfikacji i konfiguracji tych zachowań dla użytkowników, którzy wdrażają usługę. Jest to odpowiednie dla zachowań, które są opcjonalnymi składnikami lub inną konfigurację specyficzną dla wdrożenia, na przykład czy metadane są uwidocznione dla usługi lub określonej konfiguracji autoryzacji dla usługi.  
  
> [!NOTE]
> Można również użyć zachowań, które obsługują konfigurację, aby wymusić zasady aplikacji firmowych, wstawiając je do pliku konfiguracji machine.config i blokując te elementy w dół. Aby uzyskać opis i przykład, zobacz [jak: blokowanie punktów końcowych w przedsiębiorstwie](how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Aby uwidocznić zachowanie przy użyciu konfiguracji, Deweloper musi utworzyć klasę pochodną, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> a następnie zarejestrować to rozszerzenie w konfiguracji.  
  
 Poniższy przykład kodu pokazuje, jak <xref:System.ServiceModel.Description.IEndpointBehavior> implementuje <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> :  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 Aby system konfiguracji ładował niestandardowy <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , musi być zarejestrowany jako rozszerzenie. Poniższy przykład kodu pokazuje plik konfiguracji dla poprzedniego zachowania punktu końcowego:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Gdzie `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` jest typem rozszerzenia zachowania i `HostApplication` jest nazwą zestawu, do którego została skompilowana Ta klasa.  
  
### <a name="evaluation-order"></a>Kolejność oceny  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>I <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> są odpowiedzialne za tworzenie środowiska uruchomieniowego z modelu programowania i opisu. Zachowania, jak opisano wcześniej, przyczyniają się do tego procesu kompilacji w ramach usługi, punktu końcowego, kontraktu i operacji.  
  
 <xref:System.ServiceModel.ServiceHost>Stosuje zachowania w następującej kolejności:  
  
1. Usługa  
  
2. Kontrakt  
  
3. Endpoint  
  
4. Operacja  
  
 W ramach dowolnej kolekcji zachowań nie jest gwarantowane zamówienie.  
  
 <xref:System.ServiceModel.ChannelFactory%601>Stosuje zachowania w następującej kolejności:  
  
1. Kontrakt  
  
2. Endpoint  
  
3. Operacja  
  
 W ramach jakiejkolwiek kolekcji zachowań ponownie nie zagwarantowana jest żadna kolejność.  
  
### <a name="adding-behaviors-programmatically"></a>Programistyczne Dodawanie zachowań  
 Właściwości <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> w aplikacji usługi nie mogą być modyfikowane po <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metodzie <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> . Niektóre elementy członkowskie, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> Właściwość i `AddServiceEndpoint` metody w <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> , zgłaszają wyjątek, jeśli zostały zmodyfikowane po tym punkcie. Inne umożliwiają modyfikowanie ich, ale wynik jest niezdefiniowany.  
  
 Analogicznie, na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wartości nie mogą być modyfikowane po wywołaniu metody <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> . <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType>Właściwość zgłasza wyjątek, jeśli został zmodyfikowany przez ten punkt, ale inne wartości opisu klienta można modyfikować bez błędu. Jednak wynik jest niezdefiniowany.  
  
 Niezależnie od tego, czy dla usługi lub klienta zaleca się zmodyfikowanie opisu przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> .  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Reguły dziedziczenia dla atrybutów zachowania  
 Wszystkie cztery typy zachowań można wypełnić przy użyciu atrybutów — zachowania usługi i zachowania umowy. Ponieważ atrybuty są zdefiniowane dla obiektów zarządzanych i elementów członkowskich, a obiekty zarządzane i członkowie obsługują dziedziczenie, należy zdefiniować sposób działania atrybutów zachowania w kontekście dziedziczenia.  
  
 Na wysokim poziomie reguła dotyczy określonego zakresu (na przykład usługi, kontraktu lub operacji), ale stosowane są wszystkie atrybuty zachowań w hierarchii dziedziczenia dla tego zakresu. Jeśli istnieją dwa atrybuty zachowań tego samego typu, używany jest tylko typ pochodny.  
  
#### <a name="service-behaviors"></a>Zachowania usługi  
 Dla danej klasy usługi są stosowane wszystkie atrybuty zachowania usługi dla tej klasy oraz obiekty nadrzędne tej klasy. Jeśli ten sam typ atrybutu jest stosowany w wielu miejscach w hierarchii dziedziczenia, zostanie użyty typ najbardziej pochodny.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Na przykład w poprzednim przypadku usługa B zostaje zakończona z <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.Single> , <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> trybem <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> i <xref:System.ServiceModel.ConcurrencyMode> z <xref:System.ServiceModel.ConcurrencyMode.Single> . <xref:System.ServiceModel.ConcurrencyMode>Jest <xref:System.ServiceModel.ConcurrencyMode.Single> , ponieważ <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybut w usłudze B jest w "bardziej pochodny" niż w usłudze A.  
  
#### <a name="contract-behaviors"></a>Zachowania kontraktów  
 Dla danego kontraktu są stosowane wszystkie atrybuty zachowań kontraktu w tym interfejsie i w obiektach nadrzędnych tego interfejsu. Jeśli ten sam typ atrybutu jest stosowany w wielu miejscach w hierarchii dziedziczenia, zostanie użyty typ najbardziej pochodny.  
  
#### <a name="operation-behaviors"></a>Zachowania operacji  
 Jeśli dana operacja nie przesłania istniejącej operacji abstrakcyjnej lub wirtualnej, nie są stosowane żadne reguły dziedziczenia.  
  
 Jeśli operacja zastąpi istniejącą operację, zostaną zastosowane wszystkie atrybuty zachowania operacji dla tej operacji i dla elementów nadrzędnych tej operacji.  Jeśli ten sam typ atrybutu jest stosowany w wielu miejscach w hierarchii dziedziczenia, zostanie użyty typ najbardziej pochodny.
