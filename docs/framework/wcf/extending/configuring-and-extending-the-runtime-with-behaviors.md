---
title: Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: af95fa01fc9caffb8a4f0e85d3457c7f3fa60320
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
Zachowania umożliwiają modyfikowanie zachowania domyślnego i dodać niestandardowych rozszerzeń, które Inspekcja i sprawdź poprawność konfiguracji usługi lub modyfikowanie zachowania w czasie wykonywania w aplikacjach klienta i usługi Windows Communication Foundation (WCF). W tym temacie opisano interfejsów zachowanie, jak ich implementacji i sposobu dodawania ich do opisu usługi (w aplikacji usługi) lub punktu końcowego (w aplikacji klienckiej) programowo lub w pliku konfiguracji. Aby uzyskać więcej informacji na temat za pomocą zachowań dostarczane przez system, zobacz [Określanie zachowania środowiska uruchomieniowego usługi](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) i [Określanie zachowania środowiska uruchomieniowego klienta](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Zachowania  
 Zachowanie typy są dodawane do usługi lub obiektów opis punktu końcowego usługi (na usługi lub klienta, odpowiednio) przed te obiekty są wykorzystywane przez Windows Communication Foundation (WCF) do tworzenia środowisko uruchomieniowe, które wykonuje usługi WCF lub klienta programu WCF. Wywołanego te zachowania podczas procesu tworzenia środowiska uruchomieniowego są następnie dostęp do środowiska wykonawczego właściwości i metod, które modyfikują środowiska uruchomieniowego tworzony przez kontraktu, powiązania oraz adres.  
  
### <a name="behavior-methods"></a>Zachowanie metody  
 Ma wszystkie zachowania `AddBindingParameters` metody `ApplyDispatchBehavior` metody, `Validate` metody i `ApplyClientBehavior` metody z jednym wyjątkiem: ponieważ <xref:System.ServiceModel.Description.IServiceBehavior> nie można wykonać na kliencie nie implementuje on `ApplyClientBehavior`.  
  
-   Użyj `AddBindingParameters` metodę modyfikowanie lub dodawanie niestandardowych obiektów na kolekcję powiązań niestandardowych mogą uzyskiwać dostęp do ich używania, gdy jest tworzony przez środowisko uruchomieniowe. Na przykład, to w jaki sposób są określone wymagania dotyczące ochrony, który wpływa na sposób utworzeniu kanału, ale nie są znane przez dewelopera kanału.  
  
-   Użyj `Validate` metody do sprawdzenia drzewo opis i odpowiedni obiekt środowiska wykonawczego, aby upewnić się, że odpowiada pewne określone kryteria.  
  
-   Użyj `ApplyDispatchBehavior` i `ApplyClientBehavior` metody do sprawdzenia opis drzewa i zmodyfikować środowiska uruchomieniowego dla określonego zakresu na usługi lub klienta. Można także wstawić także obiekty rozszerzenia.  
  
    > [!NOTE]
    >  Drzewo opis znajduje się w tych metod, ale jest tylko badania. W przypadku modyfikacji drzewa opis zachowanie jest niezdefiniowany.  
  
 Właściwości można modyfikować i interfejsy dostosowania, które można zaimplementować są dostępne za pośrednictwem klasy środowiska uruchomieniowego usługi i klienta. Typy usługi <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy. Typy klientów są <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.ClientOperation> klasy. <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> punkty wejścia rozszerzeń dostępu do całej klienta oraz całej usługi czasu wykonywania właściwości i kolekcje rozszerzenia odpowiednio występują następujące klasy. Podobnie <xref:System.ServiceModel.Dispatcher.ClientOperation> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy ujawnia odpowiednio operacji klienta, właściwości czasu wykonywania operacji usług i kolekcji rozszerzeń. Można wykonywać następujące czynności, jednak dostęp szerszym zakresie środowiska uruchomieniowego obiekt z operacji środowiska uruchomieniowego obiektu i na odwrót, jeśli konieczne.  
  
> [!NOTE]
>  Omówienie środowiska uruchomieniowego właściwości i typy rozszerzeń, których można użyć, aby zmodyfikować sposób wykonywania klienta, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md). Omówienie środowiska uruchomieniowego właściwości i typy rozszerzeń, które umożliwia modyfikowanie zachowania wykonywania dyspozytora usługi, zobacz [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 Większość użytkowników usługi WCF nie wchodzą w interakcje ze środowiskiem uruchomieniowym bezpośrednio; Zamiast tego użyć core programowania konstrukcje modelu, takie jak punkty końcowe, kontrakty, powiązania, adresy i zachowanie atrybuty klasy lub zachowania w plikach konfiguracji. Konstrukcje te tworzą *drzewa opis*, który znajduje się pełna Specyfikacja konstruowania środowiska uruchomieniowego w celu obsługi usługi lub klienta opisanego przez drzewa opis.  
  
 Istnieją cztery rodzaje zachowania w programie WCF:  
  
-   Usługa zachowania (<xref:System.ServiceModel.Description.IServiceBehavior> typy) włączenia dostosowywania środowiska uruchomieniowego całej usługi, w tym <xref:System.ServiceModel.ServiceHostBase>.  
  
-   Zachowania punktu końcowego (<xref:System.ServiceModel.Description.IEndpointBehavior> typy) włączenia dostosowywania punktów końcowych usługi i skojarzone z nimi <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiektów.  
  
-   Zwiń zachowania (<xref:System.ServiceModel.Description.IContractBehavior> typy) włączenia dostosowywania, zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy w aplikacji klienta i usługi, odpowiednio.  
  
-   Operacja zachowania (<xref:System.ServiceModel.Description.IOperationBehavior> typy) Włącz dostosowywania <xref:System.ServiceModel.Dispatcher.ClientOperation> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy ponownie na kliencie i usługi.  
  
 Można dodać te zachowania do różnych obiektów opis zaimplementowanie atrybutów niestandardowych, za pomocą plików konfiguracji aplikacji, lub bezpośrednio przez dodanie ich do kolekcji zachowań opis obiektu. Musi jednak być dodane do opisu usługi lub obiektu opis punktu końcowego usługi przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Zachowanie zakresów  
 Istnieją cztery typy zachowanie, z których każdy odnosi się do określonego zakresu dostępu do środowiska wykonawczego.  
  
#### <a name="service-behaviors"></a>Zachowania usług  
 Zachowania usług, które implementują <xref:System.ServiceModel.Description.IServiceBehavior>, są podstawowy mechanizm, za pomocą którego zmodyfikować środowiska uruchomieniowego całej usługi. Istnieją trzy mechanizmy Dodawanie zachowań usługi z usługą.  
  
1.  Przy użyciu atrybutu dla klasy usługi.  Gdy <xref:System.ServiceModel.ServiceHost> jest tworzony <xref:System.ServiceModel.ServiceHost> implementacja używa odbicia do odnajdywania zestawu atrybutów w typie usługi. Jeśli te atrybuty będą implementacje <xref:System.ServiceModel.Description.IServiceBehavior>, są one dodawane do kolekcji zachowań na <xref:System.ServiceModel.Description.ServiceDescription>. Dzięki temu te zachowania, aby uczestniczyć w konstrukcji usługi czasu wykonywania.  
  
2.  Programowe Dodawanie zachowania do kolekcji zachowań na <xref:System.ServiceModel.Description.ServiceDescription>. Można to osiągnąć następujące wiersze kodu:  
  
    ```  
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3.  Implementowanie niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> który rozszerza konfiguracji. Umożliwia to korzystanie z zachowanie usługi z pliki konfiguracji aplikacji.  
  
 Przykłady zachowania usługi programu WCF <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>i <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.  
  
#### <a name="contract-behaviors"></a>Kontrakt zachowania  
 Zwiń zachowania, które implementują <xref:System.ServiceModel.Description.IContractBehavior> interfejsu, służą do rozszerzania środowiska uruchomieniowego klienta i usługi między kontrakt.  
  
 Istnieją dwa mechanizmy dodawania zachowania kontraktu do kontraktu.  Pierwszy mechanizmu polega na utworzeniu atrybutu niestandardowego ma być używany dla interfejsu kontraktu. Po użyciu interfejsu kontraktu jest przekazywany jako <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601>, WCF sprawdza atrybutów w interfejsie. Jeśli wszystkie atrybuty są implementacje <xref:System.ServiceModel.Description.IContractBehavior>, te są dodawane do kolekcji zachowań na <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> utworzone dla tego interfejsu.  
  
 Można też wdrożyć <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> na atrybut zachowanie niestandardowych kontraktu. W takim przypadku zachowanie następująco po zastosowaniu do:  
  
 •Podstawowy interfejsu kontraktu. W takim przypadku zachowanie jest stosowany do wszystkich umów tego typu dowolnego punktu końcowego i WCF ignoruje wartość <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> właściwości.  
  
 Klasa usługi •podstawowy. W takim przypadku zachowanie jest stosowane tylko do punktów końcowych z kontraktem jest wartością <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> właściwości.  
  
 Klasa wywołania zwrotnego •podstawowy. W takim przypadku zachowanie jest stosowany do punktu końcowego dupleksu klienta i WCF ignoruje wartość <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> właściwości.  
  
 Drugi mechanizm jest dodanie zachowania do kolekcji zachowań na <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Przykłady zachowania kontraktu w programie WCF <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atrybutu. Więcej informacji oraz przykład zobacz temat informacje.  
  
#### <a name="endpoint-behaviors"></a>Zachowania punktu końcowego  
 Zachowania punktu końcowego, które implementują <xref:System.ServiceModel.Description.IEndpointBehavior>, są podstawowym mechanizm, za pomocą którego można zmodyfikować całej usługi lub klienta wykonawczego dla określonego punktu końcowego.  
  
 Istnieją dwa mechanizmy dodawania zachowania punktu końcowego do usługi.  
  
1.  Dodawanie zachowania do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwości.  
  
2.  Implementowanie niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> który rozszerza konfiguracji.  
  
 Więcej informacji oraz przykład zobacz temat informacje.  
  
#### <a name="operation-behaviors"></a>Operacja zachowania  
 Operacja zachowania, które implementują <xref:System.ServiceModel.Description.IOperationBehavior> interfejsu, służą do rozszerzania środowiska uruchomieniowego klienta i usługi dla każdej operacji.  
  
 Istnieją dwa mechanizmy Dodawanie zachowań operacji do operacji. Pierwszy mechanizmu polega na utworzeniu atrybutu niestandardowego ma być używany dla metody, która modele operacji. Po dodaniu działania do albo <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory>, WCF dodaje wszelkie <xref:System.ServiceModel.Description.IOperationBehavior> atrybuty do kolekcji zachowań na <xref:System.ServiceModel.Description.OperationDescription> utworzone dla tej operacji.  
  
 Drugi mechanizm jest bezpośrednio dodając zachowania do kolekcji zachowań na skonstruowane <xref:System.ServiceModel.Description.OperationDescription>.  
  
 Przykłady zachowania operacji w programie WCF <xref:System.ServiceModel.OperationBehaviorAttribute> i <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Więcej informacji oraz przykład zobacz temat informacje.  
  
### <a name="using-configuration-to-create-behaviors"></a>Tworzenie zachowania przy użyciu konfiguracji  
 Usługi i punktu końcowego i kontrakt zachowania może przez zaprojektowane należy określić w kodzie lub przy użyciu atrybutów; za pomocą aplikacji lub pliki konfiguracji sieci Web można skonfigurować tylko zachowania usługi i punktu końcowego. Udostępnianie zachowania przy użyciu atrybutów umożliwia deweloperom określenie zachowania w czasie kompilacji, która nie można dodać, usunąć ani zmodyfikować w czasie wykonywania. Często jest to odpowiednie dla zachowania, które zawsze są wymagane do poprawnego działania usługi (na przykład dotyczące transakcji parametry <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> atrybutu). Udostępnianie zachowania przy użyciu konfiguracji umożliwia deweloperom pozostaw specyfikacji i konfiguracji tych zachowań do tych, którzy wdrażają usługi. Jest to odpowiednie dla zachowania, które są opcjonalne składniki lub inna konfiguracja charakterystyczne dla wdrożenia, takie jak czy metadane są ujawniane usługi lub konfiguracji określonego autoryzacji dla usługi.  
  
> [!NOTE]
>  Umożliwia także zachowania, które obsługuje konfigurację, aby wymusić zasady aplikacji firmy przez wstawianie ich do pliku machine.config konfiguracji oraz funkcja blokowania tych elementów. Opis i przykładem, zobacz [porady: blokady w dół punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Do udostępnienia zachowanie za pomocą konfiguracji, deweloper musi utworzyć klasy pochodnej z <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> i zarejestruj konfiguracji tego rozszerzenia.  
  
 Poniższy kod przedstawia przykład sposobu <xref:System.ServiceModel.Description.IEndpointBehavior> implementuje <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:  
  
```  
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
  
 Aby załadować niestandardowego systemu konfiguracji <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, musi być zarejestrowany jako rozszerzenie. Poniższy przykładowy kod przedstawia plik konfiguracji dla powyższych zachowania punktu końcowego:  
  
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
  
 Gdzie `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` jest typem rozszerzenia zachowania i `HostApplication` jest nazwą zestawu, do którego została skompilowana tej klasy.  
  
### <a name="evaluation-order"></a>Kolejność obliczania  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> i <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> są odpowiedzialne za tworzenie środowiska uruchomieniowego z modelu programowania i opis. Zachowania, jak opisano wcześniej, przyczyniają się do których proces usługi, punkt końcowy, kontrakt i operacja kompilacji.  
  
 <xref:System.ServiceModel.ServiceHost> Stosuje zachowania w następującej kolejności:  
  
1.  Usługa  
  
2.  Kontrakt  
  
3.  Punkt końcowy  
  
4.  Operacja  
  
 W żadnej kolekcji zachowań kolejność nie jest gwarantowana.  
  
 <xref:System.ServiceModel.ChannelFactory%601> Stosuje zachowania w następującej kolejności:  
  
1.  Kontrakt  
  
2.  Punkt końcowy  
  
3.  Operacja  
  
 W żadnej kolekcji zachowań ponownie, kolejność nie jest gwarantowana.  
  
### <a name="adding-behaviors-programmatically"></a>Dodawanie zachowań programowo  
 Właściwości <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> w usłudze aplikacji nie można modyfikować subsequent do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metoda <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Niektóre elementy, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> właściwości i `AddServiceEndpoint` metod <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, Zgłoś wyjątek, jeśli zmodyfikowane poza tego punktu. Inne pozwala na ich modyfikacji, ale wynik jest niezdefiniowany.  
  
 Podobnie, na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> nie można modyfikować wartości po wywołaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Właściwość zgłasza wyjątek w przypadku modyfikacji poza tym punktem, ale inne wartości klienta opis można zmodyfikować bez błędów. Wynik, jednak jest niezdefiniowany.  
  
 Czy dla usługi lub klienta, zalecane jest zmodyfikowanie opis przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Reguły dziedziczenia dla atrybutów zachowania  
 Wszystkie cztery typy zachowania można wypełniać za pomocą atrybutów — zachowania usługi i zachowania kontraktu. Atrybuty są zdefiniowane w zarządzanych obiektów i elementów członkowskich i zarządzanych obiektów i elementów członkowskich obsługuje dziedziczenia, dlatego jest konieczne jest określenie, jak atrybutów zachowania działają w kontekście dziedziczenia.  
  
 Na wysokim poziomie reguła jest, że dla określonego zakresu (na przykład usługi, kontrakt lub operacji), wszystkie atrybuty zachowanie w hierarchii dziedziczenia dla tego zakresu są stosowane. Jeśli istnieją dwa atrybuty zachowanie tego samego typu, jest używany tylko najczęściej stosowanego typu pochodnego.  
  
#### <a name="service-behaviors"></a>Zachowania usług  
 Dla klasy danej usługi wszystkie atrybuty zachowanie usługi dla tej klasy, a na nadrzędne dla tej klasy są stosowane. W przypadku zastosowania tego samego typu atrybutu w wielu miejscach w hierarchii dziedziczenia jest używana najczęściej stosowanego typu pochodnego.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Na przykład w przypadku poprzedniego usługi B kończy <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.Single>, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> tryb <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, a <xref:System.ServiceModel.ConcurrencyMode> z <xref:System.ServiceModel.ConcurrencyMode.Single>. <xref:System.ServiceModel.ConcurrencyMode> Jest <xref:System.ServiceModel.ConcurrencyMode.Single>, ponieważ <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu w usłudze B znajduje się na "bardziej pochodnego" niż na usługi A.  
  
#### <a name="contract-behaviors"></a>Kontrakt zachowania  
 Dla danego kontraktu wszystkie umowy atrybutów zachowania na interfejs i na nadrzędnych ten interfejs, są stosowane. W przypadku zastosowania tego samego typu atrybutu w wielu miejscach w hierarchii dziedziczenia jest używana najczęściej stosowanego typu pochodnego.  
  
#### <a name="operation-behaviors"></a>Operacja zachowania  
 Jeśli danej operacji nie przesłania operacji wirtualny lub abstrakcyjny istniejących, mają zastosowanie żadnych reguł dziedziczenia.  
  
 Jeśli operacja zastąpić istniejącą operację, a następnie wszystkie atrybuty zachowanie operacji na tej operacji i elementów nadrzędnych danej operacji, zostaną zastosowane.  W przypadku zastosowania tego samego typu atrybutu w wielu miejscach w hierarchii dziedziczenia jest używana najczęściej stosowanego typu pochodnego.
