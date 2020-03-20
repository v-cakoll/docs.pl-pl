---
title: 'Instrukcje: migrowanie zarządzanego kodu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
ms.openlocfilehash: 2576e88c25ae381e90ec7d613efb648048145b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181392"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Instrukcje: migrowanie zarządzanego kodu DCOM do WCF
Windows Communication Foundation (WCF) jest zalecanym i bezpiecznym wyborem w stosunku do modelu DCOM (Distributed Component Object Model) dla wywołań kodu zarządzanego między serwerami i klientami w środowisku rozproszonym. W tym artykule pokazano, jak przeprowadzić migrację kodu z dcom do WCF dla następujących scenariuszy.  
  
- Usługa zdalna zwraca klientowi wartość po wartości obiektu  
  
- Klient wysyła obiekt według wartości do usługi zdalnej  
  
- Usługa zdalna zwraca obiekt przez odwołanie do klienta  
  
 Ze względów bezpieczeństwa wysyłanie obiektu przez odwołanie od klienta do usługi nie jest dozwolone w WCF. Scenariusz, który wymaga konwersacji tam iz powrotem między klientem a serwerem można osiągnąć w WCF przy użyciu usługi dupleksu.  Aby uzyskać więcej informacji na temat usług dupleksu, zobacz [Usługi dupleksu](../wcf/feature-details/duplex-services.md).  
  
 Aby uzyskać więcej informacji na temat tworzenia usług WCF i klientów dla tych usług, zobacz [Podstawowe programowanie WCF,](../wcf/basic-wcf-programming.md) [projektowanie i wdrażanie usług](../wcf/designing-and-implementing-services.md)oraz budowanie [klientów](../wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>Przykładowy kod DCOM  
 W tych scenariuszach interfejsy DCOM, które są zilustrowane przy użyciu WCF mają następującą strukturę:  
  
```csharp  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a>Usługa zwraca obiekt według wartości  
 W tym scenariuszu należy wywołać usługę i metoda zwraca obiekt, który jest przekazywany przez wartość z serwera do klienta. W tym scenariuszu przedstawiono następujące wywołanie COM:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 W tym scenariuszu klient odbiera deserializowane kopię obiektu z usługi zdalnej. Klient może wchodzić w interakcje z tej kopii lokalnej bez wywoływania z powrotem do usługi.  Innymi słowy klient ma gwarancję, że usługa nie będzie w żaden sposób zaangażowany, gdy metody na kopii lokalnej są wywoływane. WCF zawsze zwraca obiekty z usługi według wartości, więc następujące kroki opisują tworzenie zwykłej usługi WCF.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Krok 1: Zdefiniuj interfejs usługi WCF  
 Zdefiniuj interfejs publiczny dla usługi WCF i oznacz go atrybutem [<xref:System.ServiceModel.ServiceContractAttribute>] .  Oznacz metody, które chcesz udostępnić<xref:System.ServiceModel.OperationContractAttribute>klientom za pomocą atrybutu [ ]. Poniższy przykład pokazuje przy użyciu tych atrybutów do identyfikowania interfejsu po stronie serwera i metod interfejsu, które klient może wywołać. Metoda używana w tym scenariuszu jest pokazana pogrubioną czcionką.  
  
```csharp  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a>Krok 2: Zdefiniuj kontrakt na dane  
 Następnie należy utworzyć umowę danych dla usługi, która opisze, jak dane będą wymieniane między usługą i jej klientami.  Klasy opisane w umowie danych powinny być<xref:System.Runtime.Serialization.DataContractAttribute>oznaczone atrybutem [ ]. Poszczególne właściwości lub pola, które mają być widoczne zarówno dla<xref:System.Runtime.Serialization.DataMemberAttribute>klienta, jak i dla serwera, powinny być oznaczone atrybutem [ ]. Jeśli chcesz, aby typy pochodzące z klasy w umowie danych były<xref:System.Runtime.Serialization.KnownTypeAttribute>dozwolone, należy je zidentyfikować za pomocą atrybutu [ ]. WCF będzie tylko serializacji lub deserializacji typów w interfejsie usługi i typów identyfikowanych jako znane typy. Jeśli spróbujesz użyć typu, który nie jest znanym typem, wystąpi wyjątek.  
  
 Aby uzyskać więcej informacji na temat kontraktów danych, zobacz [Kontrakty danych](../wcf/samples/data-contracts.md).  
  
```csharp  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a>Krok 3: Zaimplementowanie usługi WCF  
 Następnie należy zaimplementować klasę usługi WCF, która implementuje interfejs zdefiniowany w poprzednim kroku.  
  
```csharp  
public class CustomerService: ICustomerManager
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a>Krok 4: Konfigurowanie usługi i klienta  
 Aby uruchomić usługę WCF, należy zadeklarować punkt końcowy, który udostępnia tego interfejsu usługi przy określonym adresie URL przy użyciu określonego powiązania WCF. Powiązanie określa szczegóły transportu, kodowania i protokołu dla klientów i serwera do komunikowania się. Zazwyczaj dodajesz powiązania do pliku konfiguracyjnego projektu usługi (web.config). Poniżej przedstawiono wpis powiązania dla przykładowej usługi:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Następnie należy skonfigurować klienta, aby dopasować informacje wiązania określone przez usługę. Aby to zrobić, dodaj następujące elementy do pliku konfiguracji aplikacji klienta (app.config).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"
                address="http://localhost:8083/CustomerManager"
                binding="basicHttpBinding"
                contract="Shared.ICustomerManager"/>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a>Krok 5: Uruchom usługę  
 Na koniec można samodzielnie hostować go w aplikacji konsoli, dodając następujące wiersze do aplikacji usługi i uruchamiając aplikację. Aby uzyskać więcej informacji na temat innych sposobów hostowania aplikacji usługi WCF, [Hosting Services](../wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Krok 6: Wywołanie usługi z klienta  
 Aby wywołać usługę z klienta, należy utworzyć fabrykę kanałów dla usługi i zażądać kanału, `GetCustomer` który umożliwi bezpośrednie wywołanie metody bezpośrednio od klienta. Kanał implementuje interfejs usługi i obsługuje podstawowej logiki żądania/odpowiedzi dla Ciebie.  Zwracana wartość z tego wywołania metody jest deserializowane kopię odpowiedzi usługi.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Klient wysyła obiekt według wartości do serwera  
 W tym scenariuszu klient wysyła obiekt do serwera, wartość według wartości. Oznacza to, że serwer otrzyma deserialiętowaną kopię obiektu.  Serwer może wywołać metody na tej kopii i mieć gwarancję, że nie ma wywołania zwrotnego do kodu klienta. Jak wspomniano wcześniej, normalna wymiana danych WCF jest wartością według wartości.  Gwarantuje to, że wywoływanie metod na jednym z tych obiektów jest wykonywane tylko lokalnie — nie będzie wywoływać kodu na kliencie.  
  
 W tym scenariuszu przedstawiono następujące wywołanie metody COM:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 W tym scenariuszu używa tego samego interfejsu usługi i umowy danych, jak pokazano w pierwszym przykładzie. Ponadto klient i usługa zostaną skonfigurowane w ten sam sposób. W tym przykładzie tworzony jest kanał, aby wysłać obiekt i uruchomić w ten sam sposób. Jednak w tym przykładzie utworzysz klienta, który wywołuje usługę, przekazując obiekt według wartości. Metoda usługi, która klient wywoła w umowie serwisowej, jest pogrubiona:  
  
```csharp  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Dodaj kod do klienta, który wysyła obiekt według wartości  
 Poniższy kod pokazuje, jak klient tworzy nowy obiekt klienta według wartości, tworzy kanał do komunikowania się z usługą `ICustomerManager` i wysyła do niego obiekt klienta.  
  
 Obiekt klienta zostanie szeregizowany i wysłany do usługi, gdzie jest deserializowany przez usługę do nowej kopii tego obiektu.  Wszystkie metody, które usługa wywołuje na ten obiekt będzie wykonywany tylko lokalnie na serwerze. Należy pamiętać, że ten kod ilustruje wysyłanie`PremiumCustomer`typu pochodnego ( ).  Umowa serwisowa oczekuje `Customer` obiektu, ale umowa danych usługi<xref:System.Runtime.Serialization.KnownTypeAttribute>używa atrybutu `PremiumCustomer` [ ] do wskazania, że jest również dozwolone.  WCF zakończy się niepowodzeniem próby serializacji lub deserializacji dowolnego innego typu za pośrednictwem tego interfejsu usługi.  
  
```csharp  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a>Usługa zwraca obiekt przez odwołanie  
 W tym scenariuszu aplikacja kliencka wywołuje usługę zdalną, a metoda zwraca obiekt, który jest przekazywany przez odwołanie z usługi do klienta.  
  
 Jak wspomniano wcześniej, usługi WCF zawsze zwracają obiekt według wartości.  Jednak można osiągnąć podobny wynik przy <xref:System.ServiceModel.EndpointAddress10> użyciu klasy.  Jest <xref:System.ServiceModel.EndpointAddress10> serializable przez wartość obiektu, który może być używany przez klienta do uzyskania sessionful przez obiekt odwołania na serwerze.  
  
 Zachowanie obiektu według odwołania w WCF pokazane w tym scenariuszu różni się od DCOM.  W DCOM serwer może zwrócić obiekt odwołania bezpośrednio do klienta, a klient może wywołać metody tego obiektu, które są wykonywane na serwerze.  W WCF, jednak obiekt zwracany jest zawsze wartość według wartości.  Klient musi podjąć, że obiekt według <xref:System.ServiceModel.EndpointAddress10> wartości, reprezentowane przez i używać go do tworzenia własnych sessionful obiektu przez odwołanie.  Metoda klienta wywołuje obiekt sesji wykonywane na serwerze. Innymi słowy ten obiekt według odwołania w WCF jest normalną usługą WCF, która jest skonfigurowana do sesji.  
  
 W WCF sesji jest sposobem korelowania wielu komunikatów wysyłanych między dwoma punktami końcowymi.  Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, zostanie ustanowiona sesja między klientem a serwerem.  Klient użyje pojedynczego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej pojedynczej sesji. Umowy WCF sessionful są podobne do wzorców żądania/odpowiedzi sieci zorientowanych na połączenie.  
  
 Ten scenariusz jest reprezentowany przez następującą metodę DCOM.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Krok 1: Zdefiniuj interfejs i implementację usługi Sessionful WCF  
 Najpierw zdefiniuj interfejs usługi WCF, który zawiera obiekt sessionful.  
  
 W tym kodzie sessionful obiekt `ServiceContract` jest oznaczony atrybutem, który identyfikuje go jako zwykły interfejs usługi WCF.  Ponadto właściwość <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> jest ustawiona, aby wskazać, że będzie to usługa sesyjna.  
  
```csharp  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 Poniższy kod przedstawia implementację usługi.  
  
 Usługa jest oznaczona atrybutem [ServiceBehavior], a jego właściwość InstanceContextMode ustawiona na InstanceContextMode.PerSessions wskazuje, że dla każdej sesji powinno zostać utworzone unikatowe wystąpienie tego typu.  
  
```csharp  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
    public class MySessionBoundObject : ISessionBoundObject  
    {  
        private string _value;  
  
        public string GetCurrentValue()  
        {  
            return _value;  
        }  
  
        public void SetCurrentValue(string val)  
        {  
            _value = val;  
        }  
  
    }  
```  
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Krok 2: Zdefiniuj usługę fabryczną WCF dla obiektu sesyjnego  
 Usługa, która tworzy obiekt sessionful musi być zdefiniowane i zaimplementowane. Poniższy kod pokazuje, jak to zrobić. Ten kod tworzy inną usługę WCF, która zwraca obiekt. <xref:System.ServiceModel.EndpointAddress10>  Jest to serializable formie punktu końcowego można użyć do utworzenia obiektu pełnej sesji.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Poniżej przedstawiono implementację tej usługi. Ta implementacja utrzymuje fabrykę pojedynczego kanału do tworzenia obiektów sesji.  Po `GetInstanceAddress` wywołaniu tworzy kanał i <xref:System.ServiceModel.EndpointAddress10> tworzy obiekt, który wskazuje adres zdalny skojarzony z tym kanałem.   <xref:System.ServiceModel.EndpointAddress10>jest typem danych, który może być zwracany do wartości klienta według wartości.
  
```csharp  
public class SessionBoundFactory : ISessionBoundFactory  
    {  
        public static ChannelFactory<ISessionBoundObject> _factory =
            new ChannelFactory<ISessionBoundObject>("sessionbound");  
  
        public SessionBoundFactory()  
        {  
        }  
  
        public EndpointAddress10 GetInstanceAddress()  
        {  
            IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
            return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
        }  
    }  
```  
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Krok 3: Konfigurowanie i uruchamianie usług WCF  
 Aby obsługiwać te usługi, należy wprowadzić następujące dodatki do pliku konfiguracyjnego serwera (web.config).  
  
1. Dodaj `<client>` sekcję opisującą punkt końcowy dla obiektu sesji.  W tym scenariuszu serwer działa również jako klient i musi być skonfigurowany, aby to włączyć.  
  
2. W `<services>` sekcji zadeklarować punkty końcowe usługi dla obiektu fabrycznego i sessionful.  Dzięki temu klient do komunikowania się z <xref:System.ServiceModel.EndpointAddress10> punktami końcowymi usługi, uzyskać i utworzyć kanał sessionful.  
  
 Poniżej przedstawiono przykładowy plik konfiguracyjny z następującymi ustawieniami:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"  
                address="net.tcp://localhost:8081/SessionBoundObject"  
                binding="netTcpBinding"  
                contract="Shared.ISessionBoundObject"/>  
    </client>  
  
    <services>  
      <service name="Server.MySessionBoundObject">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                  binding="netTcpBinding"
                  contract="Shared.ISessionBoundObject" />  
      </service>  
      <service name="Server.SessionBoundFactory">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                  binding="netTcpBinding"
                  contract="Shared.ISessionBoundFactory" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Dodaj następujące wiersze do aplikacji konsoli, aby samodzielnie hostować usługę i uruchomić aplikację.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Krok 4: Skonfiguruj klienta i zadzwoń do usługi  
 Skonfiguruj klienta do komunikowania się z usługami WCF, wykonując następujące wpisy w pliku konfiguracji aplikacji projektu (app.config).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"
                address="net.tcp://localhost:8081/SessionBoundObject"
                binding="netTcpBinding"
                contract="Shared.ISessionBoundObject"/>  
      <endpoint name="factory"
                address="net.tcp://localhost:8081/SessionBoundFactory"
                binding="netTcpBinding"
                contract="Shared.ISessionBoundFactory"/>  
    </client>
  </system.serviceModel>  
</configuration>  
```  
  
 Aby wywołać usługę, dodaj kod do klienta, aby wykonać następujące czynności:  
  
1. Utwórz kanał `ISessionBoundFactory` do usługi.  
  
2. Użyj kanału do wywołania `ISessionBoundFactory` usługi <xref:System.ServiceModel.EndpointAddress10> uzyskać obiekt.  
  
3. Użyj, <xref:System.ServiceModel.EndpointAddress10> aby utworzyć kanał, aby uzyskać obiekt sesji.  
  
4. Wywołanie `SetCurrentValue` `GetCurrentValue` i metody, aby zademonstrować, że pozostaje to samo wystąpienie obiektu jest używany w wielu wywołań.  
  
```csharp  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Podstawy programowania przy użyciu programu WCF](../wcf/basic-wcf-programming.md)
- [Projektowanie i implementowanie usług](../wcf/designing-and-implementing-services.md)
- [Kompilowanie klientów](../wcf/building-clients.md)
- [Usługi dwukierunkowe](../wcf/feature-details/duplex-services.md)
