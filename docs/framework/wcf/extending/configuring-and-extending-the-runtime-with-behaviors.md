---
title: Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 71057ec219f46cb8b51eb9b44d8b93af540d1b01
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344250"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a>Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań
Zachowania umożliwiają modyfikowanie zachowania domyślnego i dodać niestandardowych rozszerzeń, które Inspekcja i sprawdź poprawność konfiguracji usługi lub modyfikowanie zachowania w czasie wykonywania w aplikacji klienta i usługi Windows Communication Foundation (WCF). W tym temacie opisano interfejsów zachowanie, jak je wdrożyć i jak je dodać do opisu usługi (w aplikacji usługi) lub punktu końcowego (w aplikacji klienckiej) programowo, albo w pliku konfiguracji. Aby uzyskać więcej informacji na temat za pomocą zachowań dostarczane przez system, zobacz [Określanie zachowania środowiska uruchomieniowego usługi](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) i [Określanie zachowania środowiska uruchomieniowego klienta](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).  
  
## <a name="behaviors"></a>Zachowania  
 Zachowanie typy są dodawane do usługi lub obiektów opis punktu końcowego usługi (na usługi lub klienta, odpowiednio) przed tymi obiektami są używane przez Windows Communication Foundation (WCF) do tworzenia środowiska uruchomieniowego, które wykonuje usługi WCF lub klienta programu WCF. Wywołanego tych zachowań w procesie tworzenia środowiska uruchomieniowego są następnie uzyskać dostęp do środowiska uruchomieniowego właściwości i metod, które modyfikują tworzony przez adresy kontraktu, powiązania i środowiska uruchomieniowego.  
  
### <a name="behavior-methods"></a>Zachowanie metody  
 Ma wszystkie zachowania `AddBindingParameters` metody `ApplyDispatchBehavior` metody `Validate` metody i `ApplyClientBehavior` metody z jednym wyjątkiem: Ponieważ <xref:System.ServiceModel.Description.IServiceBehavior> nie można wykonać na kliencie nie implementuje on `ApplyClientBehavior`.  
  
-   Użyj `AddBindingParameters` metodę, aby zmodyfikować lub dodać niestandardowe obiekty na kolekcję powiązań niestandardowych mającej dostęp do własnego użytku, gdy środowisko uruchomieniowe jest konstruowany. Na przykład, to w jaki sposób są określone wymagania dotyczące ochrony, który mają wpływ na sposób kanał został opracowany, ale nie są znane przez dewelopera kanału.  
  
-   Użyj `Validate` metody badania opis drzewa i odpowiedni obiekt środowiska uruchomieniowego, aby upewnić się, że jest zgodny z pewne określone kryteria.  
  
-   Użyj `ApplyDispatchBehavior` i `ApplyClientBehavior` metody do sprawdzenia opis drzewa i modyfikowania środowiska uruchomieniowego dla określonego zakresu na usługi lub klienta. Można także wstawić także obiekty rozszerzeń.  
  
    > [!NOTE]
    >  Drzewo opis znajduje się w tych metod, ale jest do zbadania tylko. W przypadku modyfikowania drzewa opis zachowanie jest niezdefiniowane.  
  
 Właściwości można modyfikować i interfejsy dostosowania, które można zaimplementować są dostępne za pośrednictwem klasy środowiska wykonawczego usługi i klienta. Typy usług są <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy. Typy klientów są <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.ClientOperation> klasy. <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klasy są punkty wejścia rozszerzalności, dostęp do właściwości dla całej klienta oraz obejmujących całą usługę środowiska uruchomieniowego i rozszerzenia kolekcji, odpowiednio. Podobnie <xref:System.ServiceModel.Dispatcher.ClientOperation> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy ujawnić operacji klienta, właściwości środowiska uruchomieniowego operacji usług i rozszerzenia kolekcji, odpowiednio. Możliwe, jednak dostęp do szerszego zakresu środowiska uruchomieniowego obiektów z operacji środowiska uruchomieniowego obiektów i na odwrót, jeśli muszą być.  
  
> [!NOTE]
>  Omówienie środowiska uruchomieniowego, właściwości i typy rozszerzeń, których można użyć, aby zmienić zachowanie wykonywania klienta, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md). Omówienie środowiska uruchomieniowego, właściwości i typy rozszerzeń, które można użyć, aby zmodyfikować zachowanie wykonania dyspozytora usługi, zobacz [rozszerzanie dyspozytorów](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
 Większość użytkowników usługi WCF nie wchodzą w interakcje ze środowiskiem uruchomieniowym bezpośrednio; Zamiast tego użyć core programowania modelu konstrukcji, takich jak punkty końcowe, kontrakty, powiązania, adresów i zachowanie atrybuty klasy lub zachowania w plikach konfiguracji. Te konstrukcje tworzą *drzewa opis*, czyli pełną specyfikację tworzenia środowiska uruchomieniowego pod kątem obsługi usługi lub klienta opisanego przez drzewo opis.  
  
 Istnieją cztery rodzaje zachowań w programie WCF:  
  
-   Usługa zachowania (<xref:System.ServiceModel.Description.IServiceBehavior> typy) umożliwiają dostosowanie środowiska uruchomieniowego całej usługi, w tym <xref:System.ServiceModel.ServiceHostBase>.  
  
-   Zachowań punktu końcowego (<xref:System.ServiceModel.Description.IEndpointBehavior> typy) umożliwiają dostosowanie punkty końcowe usługi i ich skojarzone <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> obiektów.  
  
-   Kontrakt zachowania (<xref:System.ServiceModel.Description.IContractBehavior> typy) umożliwiają dostosowanie zarówno <xref:System.ServiceModel.Dispatcher.ClientRuntime> i <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klas w aplikacji klienta i usługi, odpowiednio.  
  
-   Operacja zachowania (<xref:System.ServiceModel.Description.IOperationBehavior> typy) umożliwiają dostosowanie <xref:System.ServiceModel.Dispatcher.ClientOperation> i <xref:System.ServiceModel.Dispatcher.DispatchOperation> klasy ponownie na kliencie i usługi.  
  
 Można dodać te zachowania do różnych obiektów, opis, implementując atrybuty niestandardowe, za pomocą plików konfiguracji aplikacji, lub bezpośrednio przez dodanie ich do kolekcji zachowań w obiekcie odpowiedni opis. Muszą jednak być dodane do opisu usługi lub obiektu opis punktu końcowego usługi przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601>.  
  
### <a name="behavior-scopes"></a>Zachowanie zakresów  
 Istnieją cztery typy zachowanie, z których każdy odnosi się do określonego zakresu dostęp do środowiska uruchomieniowego.  
  
#### <a name="service-behaviors"></a>Zachowania usług  
 Zachowania usług, które implementują <xref:System.ServiceModel.Description.IServiceBehavior>, są podstawowym mechanizmem za pomocą którego możesz zmodyfikować środowisko uruchomieniowe całą usługę. Istnieją trzy mechanizmy dodawania zachowania usługi z usługą.  
  
1. Za pomocą atrybutu dla klasy usługi.  Gdy <xref:System.ServiceModel.ServiceHost> jest konstruowany <xref:System.ServiceModel.ServiceHost> implementacja używa odbicia, aby odnaleźć zestaw atrybutów w typie usługi. Jeśli którekolwiek z tych atrybutów są implementacje <xref:System.ServiceModel.Description.IServiceBehavior>, są one dodawane do kolekcji zachowań na <xref:System.ServiceModel.Description.ServiceDescription>. Dzięki temu te zachowania, aby wziąć udział w konstrukcji usługi czasu wykonywania.  
  
2. Programowe Dodawanie zachowania do kolekcji zachowań na <xref:System.ServiceModel.Description.ServiceDescription>. Można to zrobić, z następującymi wierszami kodu:  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. Implementowanie niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> rozszerzający konfiguracji. To umożliwia zachowanie usługi z plików konfiguracji aplikacji.  
  
 Przykłady usługi zachowań w programie WCF <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>i <xref:System.ServiceModel.Description.ServiceMetadataBehavior> zachowanie.  
  
#### <a name="contract-behaviors"></a>Zachowania kontraktu  
 Kontrakt zachowań, które implementują <xref:System.ServiceModel.Description.IContractBehavior> interfejsu, służą do rozszerzania środowiska uruchomieniowego klienta i usługi dla kontraktu.  
  
 Istnieją dwa mechanizmy Dodawanie zachowań Umowa na umowę.  Pierwszy mechanizm polega na utworzeniu atrybutu niestandardowego, który ma być używany w interfejsie kontraktu. Kiedy interfejsu kontraktu jest przekazywana do obu <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601>, WCF sprawdza atrybutów w interfejsie. Jeśli jakiekolwiek atrybuty stanowią implementacje <xref:System.ServiceModel.Description.IContractBehavior>, te są dodawane do kolekcji zachowań na <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> utworzone dla tego interfejsu.  
  
 Możesz również wdrożyć <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> atrybutu zachowanie niestandardowe kontraktu. W takim przypadku zachowanie wynosi po zastosowaniu do:  
  
 •Podstawowy interfejsu kontraktu. W takim przypadku zachowanie jest stosowany do wszystkich zamówień tego typu w dowolnym punkcie końcowym i WCF ignoruje wartość <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> właściwości.  
  
 Klasa usługi •podstawowy. W takim przypadku zachowanie jest stosowane tylko do punktów końcowych kontrakt jest wartością <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> właściwości.  
  
 Klasa wywołania zwrotnego •podstawowy. W takim przypadku zachowanie jest stosowany do punktu końcowego dwukierunkowego klienta i WCF ignoruje wartość <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> właściwości.  
  
 Drugi mechanizm jest dodanie zachowania do kolekcji zachowań na <xref:System.ServiceModel.Description.ContractDescription>.  
  
 Przykłady zamówienia zachowania w programie WCF <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> atrybutu. Aby uzyskać więcej informacji i obejrzeć przykład zobacz temat referencyjny.  
  
#### <a name="endpoint-behaviors"></a>Zachowań punktu końcowego  
 Zachowań punktu końcowego, które implementują <xref:System.ServiceModel.Description.IEndpointBehavior>, są podstawowym mechanizmem za pomocą którego można zmodyfikować całej usługi lub klienta wykonawczego dla określonego punktu końcowego.  
  
 Istnieją dwa mechanizmy dodawania zachowań punktu końcowego usługi.  
  
1. Dodawanie zachowania do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwości.  
  
2. Implementowanie niestandardowego <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> rozszerzający konfiguracji.  
  
 Aby uzyskać więcej informacji i obejrzeć przykład zobacz temat referencyjny.  
  
#### <a name="operation-behaviors"></a>Operacja zachowania  
 Operacja zachowań, które implementują <xref:System.ServiceModel.Description.IOperationBehavior> interfejsu, służą do rozszerzania obsługi klienta i usługi dla każdej operacji.  
  
 Istnieją dwa mechanizmy dodawania zachowania operacji z operacją. Pierwszy mechanizm polega na utworzeniu atrybutu niestandardowego, który ma być używany w metodzie, który modeluje operacji. Po dodaniu operacji do jednej <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory>, WCF, dodaje dowolne <xref:System.ServiceModel.Description.IOperationBehavior> atrybuty do kolekcji zachowań na <xref:System.ServiceModel.Description.OperationDescription> utworzone dla tej operacji.  
  
 Drugi mechanizm jest przez bezpośrednie dodanie zachowania kolekcji zachowań na skonstruowany <xref:System.ServiceModel.Description.OperationDescription>.  
  
 Przykłady operacji zachowań w programie WCF <xref:System.ServiceModel.OperationBehaviorAttribute> i <xref:System.ServiceModel.TransactionFlowAttribute>.  
  
 Aby uzyskać więcej informacji i obejrzeć przykład zobacz temat referencyjny.  
  
### <a name="using-configuration-to-create-behaviors"></a>Za pomocą konfiguracji do tworzenia zachowań  
 Usługi i punktu końcowego i kontrakt zachowania może przez przeznaczone do można określić w kodzie lub za pomocą atrybutów, a można skonfigurować tylko zachowania usługi i punktu końcowego przy użyciu aplikacji lub pliki konfiguracji sieci Web. Udostępnianie zachowania za pomocą atrybutów pozwala deweloperom na określenie zachowania w czasie kompilacji, który nie może zostać dodane, usunięte lub zmodyfikowany w czasie wykonywania. Często jest to odpowiednie dla zachowania, które zawsze są wymagane do poprawnego działania usługi (na przykład transakcji powiązanych z parametrami <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> atrybutu). Udostępnianie zachowania za pomocą konfiguracji umożliwia deweloperom pozostawić specyfikacji i konfiguracji tych zachowań do tych, którzy wdrażają usługi. Jest to odpowiednie dla zachowania, które są opcjonalne składniki lub inna konfiguracja charakterystyczne dla wdrożenia, takie jak czy metadanych jest uwidaczniany dla usługi lub konfiguracji określonego autoryzacji dla usługi.  
  
> [!NOTE]
>  Można także użyć zachowań, które obsługują konfigurację, aby wymusić zasady aplikacji firmy przez wstawianie je do pliku machine.config w konfiguracji i blokowanie tych elementów. Aby uzyskać opis i obejrzeć przykład, zobacz [jak: Blokowanie punktów końcowych w przedsiębiorstwie](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
 Aby udostępnić za pomocą konfiguracji zachowanie, deweloper musi utworzyć klasę pochodną z <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> , a następnie zarejestruj tego rozszerzenia z konfiguracją.  
  
 Poniższy kod przedstawia przykład sposobu <xref:System.ServiceModel.Description.IEndpointBehavior> implementuje <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:  
  
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
  
 Aby system konfiguracji można załadować niestandardowej <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, musi być zarejestrowana jako rozszerzenie. Poniższy przykład kodu pokazuje poprzedni zachowanie punktu końcowego w pliku konfiguracji:  
  
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
  
 Gdzie `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` jest typ rozszerzenia zachowania i `HostApplication` to nazwa zestawu, do którego został wcześniej skompilowany tej klasy.  
  
### <a name="evaluation-order"></a>Kolejność obliczania  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> i <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> są zobowiązani do tworzenia środowiska uruchomieniowego z modelu programowania i opis. Zachowań, jak opisano wcześniej, Współtworzenie tworzących proces na usługi, punkt końcowy, kontrakt i operacji.  
  
 <xref:System.ServiceModel.ServiceHost> Stosuje zachowań w następującej kolejności:  
  
1. Usługa  
  
2. Kontrakt  
  
3. Punkt końcowy  
  
4. Operacja  
  
 W dowolnej kolekcji zachowań kolejność nie jest gwarantowana.  
  
 <xref:System.ServiceModel.ChannelFactory%601> Stosuje zachowań w następującej kolejności:  
  
1. Kontrakt  
  
2. Punkt końcowy  
  
3. Operacja  
  
 W dowolnej kolekcji zachowań, ponownie, nie kolejność jest zachowywana.  
  
### <a name="adding-behaviors-programmatically"></a>Programowe Dodawanie zachowań  
 Właściwości <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> w usłudze aplikacji nie mogą zostać zmodyfikowane subsequent do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> metody <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Niektóre elementy członkowskie, takich jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> właściwości i `AddServiceEndpoint` metod <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, zgłosić wyjątek, jeśli zmodyfikowane poza tym punktem. Inne pozwala na ich modyfikować, ale wynik jest niezdefiniowany.  
  
 Podobnie, na komputerze klienckim <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> wartości nie mogą zostać zmodyfikowane po wywołaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> Właściwość zgłasza wyjątek, jeśli zmodyfikowane poza ten punkt, ale inne wartości Opis klienta można zmodyfikować bez błędów. Jednakże, wynik jest niezdefiniowane.  
  
 Czy usługi lub klienta, zalecane jest zmodyfikowanie opis przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.  
  
### <a name="inheritance-rules-for-behavior-attributes"></a>Reguły dziedziczenia dla atrybutów zachowania  
 Wszystkie cztery rodzaje zachowania można wypełnić przy użyciu atrybutów — zachowania usług i zachowania kontraktu. Ponieważ zdefiniowanych atrybutów w zarządzanych obiektów i elementów członkowskich i zarządzanych obiektów i elementów członkowskich obsługują dziedziczenia, jest konieczne jest określenie, jak atrybutów zachowania działają w kontekście dziedziczenia.  
  
 Na wysokim poziomie reguła jest, że dla określonego zakresu (na przykład usługi, umowy lub operacji), wszystkie atrybuty zachowanie w hierarchii dziedziczenia dla tego zakresu są stosowane. Jeśli istnieją dwa atrybuty zachowanie tego samego typu, jest używany tylko najczęściej stosowanego typu pochodnego.  
  
#### <a name="service-behaviors"></a>Zachowania usług  
 Dla klasy danej usługi wszystkie atrybuty zachowanie usługi dla tej klasy, a także na elementy nadrzędne tej klasy są stosowane. Jeśli ten sam typ atrybutu jest stosowana w wielu miejscach w hierarchii dziedziczenia, jest używany najczęściej stosowanego typu pochodnego.  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 Na przykład w przypadku poprzedniego usługa B kończy <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.Single>, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> tryb <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, a <xref:System.ServiceModel.ConcurrencyMode> z <xref:System.ServiceModel.ConcurrencyMode.Single>. <xref:System.ServiceModel.ConcurrencyMode> Jest <xref:System.ServiceModel.ConcurrencyMode.Single>, ponieważ <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybut w usłudze B jest "bardziej pochodnego" niż na usługi A.  
  
#### <a name="contract-behaviors"></a>Zachowania kontraktu  
 Dla danego kontraktu wszystkie umowy atrybutów zachowania na interfejs, które są stosowane na elementów nadrzędnych tego interfejsu. Jeśli ten sam typ atrybutu jest stosowana w wielu miejscach w hierarchii dziedziczenia, jest używany najczęściej stosowanego typu pochodnego.  
  
#### <a name="operation-behaviors"></a>Operacja zachowania  
 Jeśli danej operacji nie zastępuje istniejące abstrakcyjny ani wirtualnych operacji, mają zastosowanie reguły nie dziedziczenia.  
  
 Jeśli operacja zastąpić istniejącej operacji, a następnie wszystkie atrybuty zachowanie operacji na tę operację i elementy nadrzędne danej operacji, zostaną zastosowane.  Jeśli ten sam typ atrybutu jest stosowana w wielu miejscach w hierarchii dziedziczenia, jest używany najczęściej stosowanego typu pochodnego.
