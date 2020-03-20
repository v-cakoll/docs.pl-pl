---
title: Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 67db06649d6059ff6b6e6fb8d84058621fcc7dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185652"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
Zachowania umożliwiają modyfikowanie zachowania domyślnego i dodawanie rozszerzeń niestandardowych, które sprawdzają i weryfikują konfigurację usługi lub modyfikują zachowanie środowiska uruchomieniowego w aplikacjach klienckich i usługowych programu Windows Communication Foundation (WCF). W tym temacie opisano interfejsy zachowania, jak je zaimplementować i jak dodać je do opisu usługi (w aplikacji usługi) lub punktu końcowego (w aplikacji klienckiej) programowo lub w pliku konfiguracyjnym. Aby uzyskać więcej informacji na temat używania zachowań dostarczonych przez system, zobacz [Określanie zachowania w czasie wykonywania usługi](../specifying-service-run-time-behavior.md) i [określanie zachowania w czasie wykonywania klienta](../specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Zachowania  
 Typy zachowań są dodawane do obiektów opisu usługi lub usługi (odpowiednio w usłudze lub kliencie), zanim te obiekty będą używane przez program Windows Communication Foundation (WCF) w celu utworzenia środowiska wykonawczego, który wykonuje usługę WCF lub klienta WCF. Gdy te zachowania są wywoływane podczas procesu budowy środowiska wykonawczego są one następnie w stanie uzyskać dostęp do właściwości środowiska wykonawczego i metod, które modyfikują środowisko uruchomieniowe skonstruowane przez kontrakt, powiązania i adresy.  
  
### <a name="behavior-methods"></a>Metody zachowania  
 Wszystkie zachowania mają `AddBindingParameters` metodę, `ApplyDispatchBehavior` metodę, `Validate` metodę i `ApplyClientBehavior` metodę z jednym <xref:System.ServiceModel.Description.IServiceBehavior> wyjątkiem: Ponieważ nie można `ApplyClientBehavior`wykonać w kliencie, nie implementuje .  
  
- Użyj `AddBindingParameters` metody, aby zmodyfikować lub dodać obiekty niestandardowe do kolekcji, do której niestandardowe powiązania mogą uzyskać dostęp do ich użycia podczas konstruowania środowiska wykonawczego. Na przykład w ten sposób określono wymagania dotyczące ochrony, które wpływają na sposób, w jaki kanał jest budowany, ale nie są znane przez dewelopera kanału.  
  
- Użyj `Validate` metody, aby zbadać drzewo opisu i odpowiedni obiekt środowiska uruchomieniowego, aby upewnić się, że jest zgodny z niektórymi kryteriami.  
  
- Użyj `ApplyDispatchBehavior` i `ApplyClientBehavior` metody, aby zbadać drzewo opisu i zmodyfikować środowisko uruchomieniowe dla określonego zakresu w usłudze lub klienta. Można również wstawiać obiekty pomocnicze.  
  
    > [!NOTE]
    > Chociaż drzewo opisu jest przewidziane w tych metodach, jest tylko do badania. Jeśli drzewo opisu jest modyfikowany, zachowanie jest niezdefiniowane.  
  
 Właściwości, które można modyfikować i interfejsy dostosowywania, które można zaimplementować są dostępne za pośrednictwem klasy środowiska uruchomieniowego usługi i klienta. Typy usług <xref:System.ServiceModel.Dispatcher.DispatchRuntime> są <xref:System.ServiceModel.Dispatcher.DispatchOperation> i klasy. Typy klientów <xref:System.ServiceModel.Dispatcher.ClientRuntime> są <xref:System.ServiceModel.Dispatcher.ClientOperation> i klasy. Klasy <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i klasy są punktami wejścia rozszerzalności, aby uzyskać dostęp do właściwości środowiska uruchomieniowego całego klienta i całej usługi oraz kolekcji rozszerzeń. Podobnie <xref:System.ServiceModel.Dispatcher.ClientOperation> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy uwidaczniają działania klienta i operacji działania usługi właściwości i kolekcje rozszerzeń, odpowiednio. Można jednak uzyskać dostęp do obiektu środowiska uruchomieniowego o szerszym zakresie z obiektu środowiska wykonawczego operacji i odwrotnie, jeśli zajdzie taka potrzeba.  
  
> [!NOTE]
> Aby zapoznać się z omówieniem właściwości środowiska uruchomieniowego i typów rozszerzeń, których można użyć do zmodyfikowania zachowania wykonywania klienta, zobacz [Rozszerzanie klientów](extending-clients.md). Aby zapoznać się z omówieniem właściwości środowiska uruchomieniowego i typów rozszerzeń, których można użyć do zmodyfikowania zachowania wykonywania dyspozytora usługi, zobacz [Rozszerzanie dyspozytorów](extending-dispatchers.md).  
  
 Większość użytkowników WCF nie wchodzi w interakcję ze środowiska wykonawczego bezpośrednio; zamiast tego używają podstawowych konstrukcji modelu programowania, takich jak punkty końcowe, kontrakty, powiązania, adresy i atrybuty zachowania na klasy lub zachowania w plikach konfiguracyjnych. Konstrukcje te tworzą *drzewo opisu*, który jest pełną specyfikacją konstruowania środowiska uruchomieniowego do obsługi usługi lub klienta opisanego przez drzewo opisu.  
  
 Istnieją cztery rodzaje zachowań w WCF:  
  
- Zachowania usługi<xref:System.ServiceModel.Description.IServiceBehavior> (typy) umożliwiają dostosowanie całego środowiska <xref:System.ServiceModel.ServiceHostBase>wykonawczego usługi, w tym .  
  
- Zachowania punktu końcowego (typy)<xref:System.ServiceModel.Description.IEndpointBehavior> umożliwiają dostosowywanie punktów końcowych <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> usługi i skojarzonych z nimi obiektów.  
  
- Zachowania kontraktów<xref:System.ServiceModel.Description.IContractBehavior> (typy) umożliwiają dostosowywanie zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> klas, jak i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas w aplikacjach klienckich i usługowych.  
  
- Zachowania operacji<xref:System.ServiceModel.Description.IOperationBehavior> (typy) umożliwiają <xref:System.ServiceModel.Dispatcher.ClientOperation> dostosowywanie <xref:System.ServiceModel.Dispatcher.DispatchOperation> i klasy, ponownie na kliencie i usłudze.  
  
 Można dodać te zachowania do różnych obiektów opisu, implementując atrybuty niestandardowe, przy użyciu plików konfiguracji aplikacji lub bezpośrednio, dodając je do kolekcji zachowań na odpowiedni obiekt opisu. Należy jednak dodać do opisu usługi lub obiektu opisu <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> punktu <xref:System.ServiceModel.ServiceHost> końcowego <xref:System.ServiceModel.ChannelFactory%601>usługi przed wywołaniem lub .  
  
### <a name="behavior-scopes"></a>Zakresy zachowań  
 Istnieją cztery typy zachowań, z których każdy odpowiada określonemu zakresowi dostępu do środowiska uruchomieniowego.  
  
#### <a name="service-behaviors"></a>Zachowania usług  
 Zachowania usługi, które <xref:System.ServiceModel.Description.IServiceBehavior>implementują , są podstawowym mechanizmem, za pomocą którego można zmodyfikować całe środowisko uruchomieniowe usługi. Istnieją trzy mechanizmy dodawania zachowań usługi do usługi.  
  
1. Za pomocą atrybutu w klasie usługi.  Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany, <xref:System.ServiceModel.ServiceHost> implementacja używa odbicia, aby odnajdować zestaw atrybutów na typ usługi. Jeśli którykolwiek z tych <xref:System.ServiceModel.Description.IServiceBehavior>atrybutów są implementacje , <xref:System.ServiceModel.Description.ServiceDescription>są one dodawane do kolekcji zachowań na . Dzięki temu te zachowania do udziału w budowie czasu wykonywania usługi.  
  
2. Programowo dodając zachowanie do kolekcji <xref:System.ServiceModel.Description.ServiceDescription>zachowań na . Można to osiągnąć za pomocą następujących wierszy kodu:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementowanie niestandardowego, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> który rozszerza konfigurację. Umożliwia to korzystanie z zachowania usługi z plików konfiguracyjnych aplikacji.  
  
 Przykłady zachowań usługi w WCF obejmują <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>atrybut, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> , i zachowanie.  
  
#### <a name="contract-behaviors"></a>Zachowania kontraktowe  
 Zachowania kontraktów, które <xref:System.ServiceModel.Description.IContractBehavior> implementują interfejs, są używane do rozszerzania środowiska uruchomieniowego klienta i usługi w całym kontrakcie.  
  
 Istnieją dwa mechanizmy dodawania zachowań kontraktowych do umowy.  Pierwszym mechanizmem jest utworzenie atrybutu niestandardowego, który ma być używany w interfejsie kontraktu. Gdy interfejs kontraktu jest przekazywana do a <xref:System.ServiceModel.ServiceHost> lub a <xref:System.ServiceModel.ChannelFactory%601>, WCF sprawdza atrybuty w interfejsie. Jeśli wszystkie atrybuty <xref:System.ServiceModel.Description.IContractBehavior>są implementacje , te są <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> dodawane do kolekcji zachowań na utworzone dla tego interfejsu.  
  
 Można również zaimplementować <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> atrybut zachowania umowy niestandardowej. W takim przypadku zachowanie jest następujące po zastosowaniu do:  
  
 •Interfejs umowy. W takim przypadku zachowanie jest stosowane do wszystkich kontraktów tego typu w dowolnym punkcie <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> końcowym i WCF ignoruje wartość właściwości.  
  
 •Klasa serwisowa. W takim przypadku zachowanie jest stosowane tylko do punktów końcowych, których <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> umowa jest wartością właściwości.  
  
 •Klasa wywołania zwrotnego. W takim przypadku zachowanie jest stosowane do punktu końcowego klienta dupleksu i <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> WCF ignoruje wartość właściwości.  
  
 Drugim mechanizmem jest dodanie zachowania do kolekcji <xref:System.ServiceModel.Description.ContractDescription>zachowań na .  
  
 Przykłady zachowań kontraktowych w WCF obejmują <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atrybut. Aby uzyskać więcej informacji i przykład, zobacz temat odwołania.  
  
#### <a name="endpoint-behaviors"></a>Zachowania punktów końcowych  
 Zachowania punktu końcowego, <xref:System.ServiceModel.Description.IEndpointBehavior>które implementują , są podstawowym mechanizmem, za pomocą którego można zmodyfikować cały czas wykonywania usługi lub klienta dla określonego punktu końcowego.  
  
 Istnieją dwa mechanizmy dodawania zachowań punktu końcowego do usługi.  
  
1. Dodaj zachowanie do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwości.  
  
2. Zaimplementuj niestandardowe, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> które rozszerza konfigurację.  
  
 Aby uzyskać więcej informacji i przykład, zobacz temat odwołania.  
  
#### <a name="operation-behaviors"></a>Zachowania operacyjne  
 Zachowania operacji, które <xref:System.ServiceModel.Description.IOperationBehavior> implementują interfejs, są używane do rozszerzenia środowiska uruchomieniowego klienta i usługi dla każdej operacji.  
  
 Istnieją dwa mechanizmy dodawania zachowań operacji do operacji. Pierwszym mechanizmem jest utworzenie atrybutu niestandardowego, który ma być używany w metodzie, która modeluje operację. Gdy operacja jest dodawana <xref:System.ServiceModel.ServiceHost> do <xref:System.ServiceModel.ChannelFactory>a lub a <xref:System.ServiceModel.Description.IOperationBehavior> , WCF dodaje <xref:System.ServiceModel.Description.OperationDescription> żadnych atrybutów do kolekcji zachowań na utworzone dla tej operacji.  
  
 Drugi mechanizm polega na bezpośrednim dodaniu zachowania do kolekcji <xref:System.ServiceModel.Description.OperationDescription>zachowań na skonstruowanym .  
  
 Przykłady zachowań operacji w WCF obejmują <xref:System.ServiceModel.OperationBehaviorAttribute> i <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Aby uzyskać więcej informacji i przykład, zobacz temat odwołania.  
  
### <a name="using-configuration-to-create-behaviors"></a>Tworzenie zachowań przy użyciu konfiguracji  
 Usługi i punktu końcowego i zachowań umowy można przez zaprojektowane do określenia w kodzie lub przy użyciu atrybutów; Tylko zachowania usługi i punktu końcowego można skonfigurować przy użyciu plików konfiguracyjnych aplikacji lub sieci Web. Uwidacznianie zachowań przy użyciu atrybutów umożliwia deweloperom określenie zachowania w czasie kompilacji, które nie może być dodane, usunięte lub zmodyfikowane w czasie wykonywania. Jest to często odpowiednie dla zachowań, które są zawsze wymagane dla prawidłowego działania usługi <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> (na przykład parametry związane z transakcjami do atrybutu). Uwidacznianie zachowań przy użyciu konfiguracji umożliwia deweloperom pozostawienie specyfikacji i konfiguracji tych zachowań tym, którzy wdrażają usługę. Jest to odpowiednie dla zachowań, które są składniki opcjonalne lub innej konfiguracji specyficzne dla wdrożenia, takich jak czy metadane są widoczne dla usługi lub konfiguracji określonej autoryzacji dla usługi.  
  
> [!NOTE]
> Można również użyć zachowań, które obsługują konfigurację, aby wymusić zasady aplikacji firmy, wstawiając je do pliku konfiguracji machine.config i blokując te elementy. Aby uzyskać opis i przykład, zobacz [Jak: Blokowanie punktów końcowych w przedsiębiorstwie](how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Aby udostępnić zachowanie przy użyciu konfiguracji, deweloper <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> musi utworzyć klasę pochodną, a następnie zarejestrować to rozszerzenie z konfiguracją.  
  
 Poniższy przykład kodu <xref:System.ServiceModel.Description.IEndpointBehavior> pokazuje, <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>jak implementuje:  
  
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
  
 Aby system konfiguracyjny miał <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>załadować niestandardowe, musi być zarejestrowany jako rozszerzenie. Poniższy przykład kodu przedstawia plik konfiguracyjny dla poprzedniego zachowania punktu końcowego:  
  
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
  
 Gdzie `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` jest typ rozszerzenia `HostApplication` zachowania i jest nazwą zestawu, do którego ta klasa została skompilowana.  
  
### <a name="evaluation-order"></a>Kolejność oceny  
 I <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> są odpowiedzialne za tworzenie środowiska wykonawczego z modelu programowania i opisu. Zachowania, jak opisano wcześniej, przyczyniają się do tego procesu kompilacji w usłudze, punkt końcowy, umowy i operacji.  
  
 Stosuje <xref:System.ServiceModel.ServiceHost> zachowania w następującej kolejności:  
  
1. Usługa  
  
2. Kontrakt  
  
3. Endpoint  
  
4. Operacja  
  
 W ramach dowolnej kolekcji zachowań nie jest gwarantowana żadna kolejność.  
  
 Stosuje <xref:System.ServiceModel.ChannelFactory%601> zachowania w następującej kolejności:  
  
1. Kontrakt  
  
2. Endpoint  
  
3. Operacja  
  
 W ramach dowolnej kolekcji zachowań, ponownie, nie ma zamówienia jest gwarantowana.  
  
### <a name="adding-behaviors-programmatically"></a>Programowe dodawanie zachowań  
 Właściwości aplikacji <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> w usłudze nie mogą być modyfikowane po zastosowaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metody na <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Niektóre elementy członkowskie, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> takie `AddServiceEndpoint` jak <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>właściwość i metody na i , zgłosić wyjątek, jeśli zmodyfikowane przeszłości tego punktu. Inne pozwalają na ich modyfikowanie, ale wynik jest nieokreślony.  
  
 Podobnie na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wartości nie mogą być modyfikowane <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> po <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>wywołaniu na . Właściwość <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> zgłasza wyjątek, jeśli zmodyfikowane przeszłości tego punktu, ale inne wartości opisu klienta mogą być modyfikowane bez błędu. Wynik jest jednak nieokreślony.  
  
 Niezależnie od tego, czy dotyczy usługi, czy klienta, <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>zaleca się zmodyfikowanie opisu przed wywołaniem .  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Reguły dziedziczenia dla atrybutów zachowania  
 Wszystkie cztery typy zachowań można wypełniać przy użyciu atrybutów — zachowania usługi i zachowania umowy. Ponieważ atrybuty są zdefiniowane w obiektach zarządzanych i członków, a obiekty zarządzane i elementy członkowskie obsługują dziedziczenie, konieczne jest zdefiniowanie działania atrybutów zachowania w kontekście dziedziczenia.  
  
 Na wysokim poziomie reguła jest taka, że dla określonego zakresu (na przykład usługi, umowy lub operacji), wszystkie atrybuty zachowania w hierarchii dziedziczenia dla tego zakresu są stosowane. Jeśli istnieją dwa atrybuty zachowania tego samego typu, używany jest tylko typ najbardziej pochodny.  
  
#### <a name="service-behaviors"></a>Zachowania usług  
 Dla danej klasy usługi wszystkie atrybuty zachowania usługi w tej klasie i na rodziców tej klasy są stosowane. Jeśli ten sam typ atrybutu jest stosowany w wielu miejscach w hierarchii dziedziczenia, używany jest typ najbardziej pochodny.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Na przykład w poprzednim przypadku usługa B kończy <xref:System.ServiceModel.InstanceContextMode> się <xref:System.ServiceModel.InstanceContextMode.Single>z <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> , <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>tryb <xref:System.ServiceModel.ConcurrencyMode> , <xref:System.ServiceModel.ConcurrencyMode.Single>i a . Is <xref:System.ServiceModel.ConcurrencyMode> <xref:System.ServiceModel.ConcurrencyMode.Single>, <xref:System.ServiceModel.ServiceBehaviorAttribute> ponieważ atrybut w usłudze B jest na "bardziej pochodne" niż w usłudze A.  
  
#### <a name="contract-behaviors"></a>Zachowania kontraktowe  
 W przypadku danego kontraktu są stosowane wszystkie atrybuty zachowania umowy w tym interfejsie i na wiązki łzowej tego interfejsu. Jeśli ten sam typ atrybutu jest stosowany w wielu miejscach w hierarchii dziedziczenia, używany jest typ najbardziej pochodny.  
  
#### <a name="operation-behaviors"></a>Zachowania operacyjne  
 Jeśli dana operacja nie zastępuje istniejącej operacji abstrakcyjnej lub wirtualnej, nie mają zastosowania żadne reguły dziedziczenia.  
  
 Jeśli operacja zastępuje istniejącą operację, stosowane są wszystkie atrybuty zachowania operacji w tej operacji i na elementach nadrzędnych tej operacji.  Jeśli ten sam typ atrybutu jest stosowany w wielu miejscach w hierarchii dziedziczenia, używany jest typ najbardziej pochodny.
