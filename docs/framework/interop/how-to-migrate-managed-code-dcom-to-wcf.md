---
title: 'Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74acea566e4b0e407e86cb67d3f521f18c2d68af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643065"
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Instrukcje: Migrowanie zarządzanego kodu DCOM do WCF
Windows Communication Foundation (WCF) jest rozwiązaniem zalecane i bezpieczne za pośrednictwem rozproszonych Component Object Model (DCOM) dla kodu zarządzanego wywołań między serwerami i klientami w środowisku rozproszonym. W tym artykule pokazano, jak można przeprowadzić migrację kodu z modelu DCOM do WCF w następujących scenariuszach.  
  
- Usługa zdalna zwraca obiekt przez wartość do klienta  
  
- Klient wysyła przez wartość obiektu do usługi zdalnej  
  
- Usługa zdalna zwraca obiekt przez odwołanie do klienta  
  
 Ze względów bezpieczeństwa wysyłanie przez — odwołanie do obiektu z klienta do usługi jest niedozwolone w programie WCF. Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć programu WCF za pomocą usługi duplex.  Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Aby uzyskać więcej informacji na temat tworzenia usług WCF i klientów dla tych usług, zobacz [programowanie WCF Basic](../../../docs/framework/wcf/basic-wcf-programming.md), [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md), i [kompilowanie klientów](../../../docs/framework/wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>DCOM przykładowy kod  
 W tych scenariuszach interfejsów modelu DCOM, które zostały przedstawione przy użyciu usługi WCF mają następującą strukturę:  
  
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
  
## <a name="the-service-returns-an-object-by-value"></a>Usługa zwraca obiekt przez wartość  
 W tym scenariuszu było wywołanie usługi i jej metoda zwraca obiekt, który jest przekazywany przez wartość z serwera do klienta. Ten scenariusz przedstawia następujące wywołania modelu COM:  
  
```csharp  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 W tym scenariuszu klient otrzymuje kopię po deserializacji obiektu ze zdalnej usługi. Klient może interakcyjnie przeprowadzić ta lokalna kopia bez wywołań zwrotnych do usługi.  Innymi słowy klient ma żadnej gwarancji, że usługa nie będzie angażowany w jakikolwiek sposób, po wywołaniu metod w lokalnej kopii. Usługi WCF zawsze zwraca obiekty z usługi według wartości, więc w poniższych krokach opisano tworzenie usługi WCF regularne.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Krok 1. Zdefiniuj interfejs usługi WCF  
 Zdefiniuj interfejs publiczny dla usługi WCF i oznacz go za pomocą [<xref:System.ServiceModel.ServiceContractAttribute>] atrybutu.  Oznacz metody ma zostać uwidoczniona dla klientów z [<xref:System.ServiceModel.OperationContractAttribute>] atrybutu. Poniższy przykład pokazuje, przy użyciu tych atrybutów do identyfikowania interfejsu po stronie serwera i klienta można wywoływać metod interfejsu. Metody używane w tym scenariuszu jest wyświetlany czcionką pogrubioną.  
  
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
  
### <a name="step-2-define-the-data-contract"></a>Krok 2. Definiowanie kontraktu danych  
 Następnie należy utworzyć kontraktu danych dla usługi, w której opisano, jak dane będą wymieniane między usługą i jej klientów.  Klasy, które opisano w kontraktu danych powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataContractAttribute>] atrybutu. Indywidualne właściwości lub pól mają być widoczne dla klienta i serwera powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataMemberAttribute>] atrybutu. Jeśli chcesz, aby typy pochodzące z klasy w kontraktu danych, które mają być dozwolone, należy zidentyfikować je za pomocą [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu. Usługi WCF będzie tylko serializacji lub deserializacji, typy w interfejsie usługi i zidentyfikowane jako znanych typów. Jeśli spróbujesz użyć typu, który nie jest znany typ, wystąpi wyjątek.  
  
 Aby uzyskać więcej informacji na temat kontraktów danych zobacz [kontraktów danych](../../../docs/framework/wcf/samples/data-contracts.md).  
  
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
  
### <a name="step-3-implement-the-wcf-service"></a>Krok 3. Implementowanie usługi WCF  
 Następnie należy zaimplementować klasę usługi WCF, który implementuje interfejs, który został zdefiniowany w poprzednim kroku.  
  
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
  
### <a name="step-4-configure-the-service-and-the-client"></a>Krok 4. Konfigurowanie usługi i klienta  
 Aby uruchomić usługę WCF, należy zadeklarować punktu końcowego uwidocznionego interfejsu usług pod określonym adresem URL używa określonego powiązania WCF. Powiązanie określa szczegóły transportu, kodowanie i protokołu dla klientów i serwera, do komunikowania się. Zazwyczaj dodajesz powiązań do pliku konfiguracyjnego projektu usługi (web.config). Na poniższym obrazie przedstawiono wpis powiązania usługi przykładu:  
  
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
  
 Następnie należy skonfigurować klienta do dopasowania informacje o powiązaniu, określony przez usługę. Aby to zrobić, Dodaj następujący element do klienta pliku konfiguracji aplikacji (app.config).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a>Krok 5. Uruchom usługę  
 Na koniec można samodzielnie go umieścić w aplikacji konsoli, dodając następujące wiersze do usługi app Service i uruchamianie aplikacji. Aby uzyskać więcej informacji na temat innych sposobów hostowania aplikacji usługi WCF [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).  
  
```csharp  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Krok 6. Wywołania usługi przez klienta  
 Aby wywołać usługę od klienta, musisz tworzenie fabryki kanałów dla usługi i żądania kanał, który umożliwi bezpośrednio wywołać `GetCustomer` metoda bezpośrednio z klienta. Kanał implementuje interfejs usługi i obsługuje podstawowej logiki żądanie/nietypizowana odpowiedź dla Ciebie.  Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedzi usługi.  
  
```csharp  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Klient wysyła obiekt przez wartość do serwera  
 W tym scenariuszu klient przesyła dany obiekt z serwerem przez wartość. Oznacza to, że serwer otrzyma kopię po deserializacji obiektu.  Serwer można wywoływać metody dla tej kopii i zapewniona jest bez wywołania zwrotnego do kodu klienta. Jak wspomniano wcześniej, normalne WCF wymiany danych są przez wartość.  Gwarantuje to, że wywołanie metody w jednej z tych obiektów jest wykonywana lokalnie tylko — nie wywoła kodu na komputerze klienckim.  
  
 Ten scenariusz przedstawia następujące wywołanie metody COM:  
  
```csharp  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 W tym scenariuszu ten sam kontrakt interfejsu i danych usługi jak pokazano w pierwszym przykładzie. Ponadto klienta i usługi zostaną skonfigurowane w taki sam sposób. W tym przykładzie zostanie utworzona kanał Wyślij obiektu i uruchom ten sam sposób. Jednak w tym przykładzie utworzysz klienta, który wywołuje usługę, przekazując obiekt przez wartość. Metoda usługi, którego klient będzie wywoływać w kontrakcie usługi jest wyświetlany czcionką pogrubioną:  
  
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
 W poniższym kodzie, jak klient tworzy nowy obiekt klienta przez wartość, tworzy kanał do komunikowania się z `ICustomerManager` usługi, a następnie wysyła obiekt klienta.  
  
 Obiekt klienta będą serializowane i wysyłane do usługi, w których jest ona przeprowadzona przez usługę do nowej kopii tego obiektu.  Wszystkie metody, które wywołuje usługę, dla tego obiektu zostanie wykonana tylko lokalnie na serwerze. Należy pamiętać, że ten kod ilustruje wysyłania typem pochodnym jest (`PremiumCustomer`).  Kontrakt usługi oczekuje `Customer` obiekt, ale dane usługi kontraktu używa [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu, aby wskazać, że `PremiumCustomer` jest też dozwolony.  Usługi WCF zakończy się niepowodzeniem próby serializacji lub deserializacji dowolny inny typ za pośrednictwem tego interfejsu usługi.  
  
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
 W tym scenariuszu aplikacja kliencka nawiązuje połączenie usługi zdalnej, a metoda zwraca obiekt, który jest przekazywany przez odwołanie usługi do klienta.  
  
 Jak wspomniano wcześniej, usługi WCF zawsze zwracają obiekt przez wartość.  Jednak można osiągnąć podobny efekt, za pomocą <xref:System.ServiceModel.EndpointAddress10> klasy.  <xref:System.ServiceModel.EndpointAddress10> Jest obiektem serializacji przez wartość, która może służyć przez klienta do uzyskiwania obiektu sesji przez odwołanie, na serwerze.  
  
 Zachowanie obiektu przez odwołanie w programie WCF przedstawione w tym scenariuszu jest inny niż model DCOM.  W modelu DCOM Serwer może zwrócić obiekt przez odniesienie do klienta bezpośrednio, a klient może wywołać metody tego obiektu, które wykonania na serwerze.  W programie WCF jednak obiekt zwrócony jest zawsze przez wartość.  Klient musi podjąć tego obiektu przez wartość, reprezentowane przez <xref:System.ServiceModel.EndpointAddress10> i użyć go do utworzenia własnego obiektu sesji przez odwołanie.  Wykonywanie wywołań metod klienta w obiekcie sesji na serwerze. Innymi słowy ten obiekt przez odwołanie w programie WCF jest normalne usługi WCF, który jest skonfigurowany jako sesji.  
  
 W programie WCF sesja jest sposób korelacji wielu komunikatów przesyłanych między dwoma punktami końcowymi.  Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesji zostanie nawiązane między klientem a serwerem.  Klient użyje jednego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej jednej sesji. Przekroczono kontraktów WCF są podobne do wzorców żądań/odpowiedzi nawiązaniem połączenia sieciowego.  
  
 Ten scenariusz jest reprezentowany przez następującą metodę modelu DCOM.  
  
```csharp  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Krok 1. Zdefiniuj interfejs usługi Sessionful WCF i implementacja  
 Najpierw należy zdefiniować interfejsu usługi WCF, która zawiera obiekt sesji.  
  
 W tym kodzie obiekt sesji jest oznaczona atrybutem `ServiceContract` atrybut, który identyfikuje ją jako regularnych interface usługi WCF.  Ponadto <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwość jest ustawiona, aby wskazać, będzie on sesji usługi.  
  
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
  
 Usługa jest oznaczona atrybutem [ServiceBehavior], a jego właściwość InstanceContextMode właściwością InstanceContextMode.PerSessions do wskazania, że unikatowego wystąpienia tego typu powinny być tworzone dla każdej sesji.  
  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Krok 2. Zdefiniuj usługę WCF fabryki dla obiektu sesji  
 Usługa, która tworzy obiekt sesji należy zdefiniowane i zaimplementowane. Poniższy kod pokazuje, jak to zrobić. Ten kod tworzy innej usługi WCF, która zwraca <xref:System.ServiceModel.EndpointAddress10> obiektu.  Jest to format możliwy do serializacji dla punktu końcowego usługi mogą użyć do utworzenia obiektu sesji pełnej.  
  
```csharp  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Poniżej przedstawiono implementację tej usługi. Ta implementacja obsługuje pojedyncze fabryki kanałów, aby utworzyć obiekty sesji.  Gdy `GetInstanceAddress` jest wywoływana, tworzy kanał i tworzy <xref:System.ServiceModel.EndpointAddress10> obiektu, który wskazuje na zdalny adres skojarzony z tym kanałem.   <xref:System.ServiceModel.EndpointAddress10> jest typem danych, które mogą być zwrócone do klienta przez wartość.  
  
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
  
### <a name="step-3-configure-and-start-the-wcf-services"></a>Krok 3. Konfigurowanie i uruchamianie usług WCF  
 Aby zapewnić obsługę tych usług, należy wprowadzić następujące dodatki do pliku konfiguracji serwera (web.config).  
  
1. Dodaj `<client>` sekcja, która opisuje punktu końcowego dla obiektu sesji.  W tym scenariuszu serwer działa jako klient i musi być skonfigurowany, aby włączyć tę opcję.  
  
2. W `<services>` sekcji, Zadeklaruj punktów końcowych usługi dla obiektu ustawień fabrycznych i sessionful.  Dzięki temu klient do komunikacji z punktami końcowymi usługi, uzyskiwanie <xref:System.ServiceModel.EndpointAddress10> i utworzyć kanału sesji.  
  
 Poniżej przedstawiono przykładowy plik konfiguracji przy użyciu tych ustawień:  
  
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
  
 Dodaj następujące wiersze do aplikacji konsoli, na potrzeby samodzielnego hostowania usług i uruchomić aplikację.  
  
```csharp  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Krok 4. Konfigurowanie klienta i wywołać usługę  
 Skonfiguruj klienta do komunikowania się z usługami WCF, wprowadzając następujące wpisy w pliku konfiguracyjnym aplikacji projektu (app.config).  
  
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
  
 Aby wywołać usługę, Dodaj kod do klienta, aby wykonać następujące czynności:  
  
1. Utwórz kanał `ISessionBoundFactory` usługi.  
  
2. Wywoływanie przy użyciu kanału `ISessionBoundFactory` usługi Uzyskaj <xref:System.ServiceModel.EndpointAddress10> obiektu.  
  
3. Użyj <xref:System.ServiceModel.EndpointAddress10> próba utworzenia kanału do uzyskiwania obiektu sesji.  
  
4. Wywołaj `SetCurrentValue` i `GetCurrentValue` używane w wielu wywołań metody, aby zademonstrować, pozostaje on tego samego wystąpienia obiektu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Projektowanie i implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Kompilowanie klientów](../../../docs/framework/wcf/building-clients.md)
- [Usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md)
