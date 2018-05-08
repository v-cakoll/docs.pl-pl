---
title: 'Instrukcje: migrowanie zarządzanego kodu DCOM do WCF'
ms.date: 03/30/2017
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 187bff7c75ba2a0887e3c5728a484a9231936511
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a>Instrukcje: migrowanie zarządzanego kodu DCOM do WCF
Windows Communication Foundation (WCF) jest rozwiązaniem zalecanym i bezpieczne za pośrednictwem rozproszonej Component Object Model (DCOM) dla kodu zarządzanego połączeń między serwerami i klientami w środowisku rozproszonym. W tym artykule przedstawiono sposób można migrować kodu z modelu DCOM do WCF w następujących scenariuszach.  
  
-   Usługa zdalnego zwraca obiekt przez wartość do klienta  
  
-   Klient wysyła obiektu przez wartość do zdalnej usługi  
  
-   Zdalna usługa zwraca obiekt przez odwołanie do klienta  
  
 Ze względów bezpieczeństwa wysyłania przez — odwołanie do obiektu z klienta do usługi jest niedozwolone w programie WCF. Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć w programie WCF, za pomocą usługi duplex.  Aby uzyskać więcej informacji na temat usługi dwukierunkowe, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Aby uzyskać więcej informacji na temat tworzenia usług WCF i klientów dla tych usług, zobacz [podstawowe programowania WCF](../../../docs/framework/wcf/basic-wcf-programming.md), [projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md), i [kompilowanie klientów](../../../docs/framework/wcf/building-clients.md).  
  
## <a name="dcom-example-code"></a>DCOM przykładowy kod  
 W tych sytuacjach interfejsów modelu DCOM, które zostały przedstawione za pomocą usługi WCF ma następującą strukturę:  
  
```  
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
 W tym scenariuszu należy wywołanie usługi, a metoda zwraca obiekt, który jest przekazywany przez wartość z serwera do klienta. Ten scenariusz przedstawia następujące wywołanie COM:  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 W tym scenariuszu klient odbiera kopię zdeserializowany obiekt z usługi zdalnej. Klient może współdziałać z lokalnej kopii bez wywołań zwrotnych do usługi.  Innymi słowy klienta jest gwarancji, że usługa nie zostanie zaangażowane w dowolny sposób, wywołanego metody kopii. WCF zawsze zwraca obiekty z usługi wg wartości, więc w poniższych krokach opisano tworzenie regularne usługi WCF.  
  
### <a name="step-1-define-the-wcf-service-interface"></a>Krok 1: Definiowanie interfejsu usługi WCF  
 Zdefiniuj publiczny interfejs dla usługi WCF i oznacz ją z [<xref:System.ServiceModel.ServiceContractAttribute>] atrybutu.  Oznacz metody chcesz udostępnić klientom z [<xref:System.ServiceModel.OperationContractAttribute>] atrybutu. W poniższym przykładzie pokazano, za pomocą tych atrybutów do identyfikowania interfejsu po stronie serwera i klienta można wywoływać metod interfejsu. Metody używane w tym scenariuszu są pogrubione.  
  
```  
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
  
### <a name="step-2-define-the-data-contract"></a>Krok 2: Definiowanie kontraktu danych  
 Następnie należy utworzyć kontrakt danych dla usługi, w której opisano, jak dane będą wymieniane między usługą i klientów.  Klasy opisane w kontraktu danych powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataContractAttribute>] atrybutu. Indywidualne właściwości lub pola mają być widoczne dla klienta i serwera powinien być oznaczony przez [<xref:System.Runtime.Serialization.DataMemberAttribute>] atrybutu. Jeśli chcesz typów pochodnych klasy w kontrakcie danych mogą być musi zidentyfikować je za pomocą [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu. Usługi WCF zostaną tylko serializacji lub deserializacji typy w interfejsie usługi i zidentyfikowane jako znanych typów. Przy próbie Użyj typu, który nie jest znanym typem, wystąpi wyjątek.  
  
 Aby uzyskać więcej informacji na temat kontraktów danych, zobacz [kontraktów danych](../../../docs/framework/wcf/samples/data-contracts.md).  
  
```  
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
  
### <a name="step-3-implement-the-wcf-service"></a>Krok 3: Implementowanie usługi WCF  
 Następnie należy zaimplementować klasy usługi WCF, który implementuje interfejs, który został zdefiniowany w poprzednim kroku.  
  
```  
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
 Aby uruchomić usługi WCF, należy zadeklarować punktu końcowego, który uwidacznia interfejs tej usługi pod określonym adresem URL używa określonego powiązania WCF. Powiązanie określa szczegóły transportu, kodowanie i protokół dla klientów i serwerów, które do komunikacji. Zazwyczaj można dodać powiązania do pliku konfiguracyjnego projektu usługi (web.config). Poniżej przedstawiono wpis powiązanie, na przykład usługi:  
  
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
  
 Następnie należy skonfigurować klienta do dopasowania informacje o powiązaniu, określony przez usługę. Aby to zrobić, dodaj następującą wartość do pliku konfiguracyjnego (app.config) aplikacji klienta.  
  
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
  
### <a name="step-5-run-the-service"></a>Krok 5: Uruchom usługę  
 Na koniec można samodzielnie obsługiwać go w aplikacji konsoli dodając następujące wiersze do usługi app Service i uruchamianie aplikacji. Aby uzyskać więcej informacji na temat innych sposobów hostowania aplikacji usługi WCF [Hosting usług](../../../docs/framework/wcf/hosting-services.md).  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a>Krok 6: Wywołania usługi z klienta  
 Aby wywołać usługę od klienta, należy utworzyć fabryki kanałów dla usługi i żądania kanału, który umożliwi bezpośrednio wywoływać `GetCustomer` metody bezpośrednio z klienta. Kanał implementuje interfejs usługi i obsługuje podstawowej logiki żądania/odpowiedzi dla Ciebie.  Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedzi usługi.  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a>Klient wysyła obiekt przez wartości z serwerem  
 W tym scenariuszu urządzenie klienta wysyła obiekt do serwera, przez wartość. Oznacza to, że serwer otrzyma kopię zdeserializowany obiekt.  Serwer można wywoływać metod w tej kopii i można zagwarantować, że nie istnieje żadne wywołanie zwrotne do kodu klienta. Jak wspomniano wcześniej, normalne WCF wymiany danych są przez wartość.  Gwarantuje to, że wywołanie metod na jednym z tych obiektów jest wykonywana lokalnie tylko — nie wywoła kodu na kliencie.  
  
 Ten scenariusz przedstawia następujące wywołanie metody COM:  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 W tym scenariuszu używa tego samego interfejsu i danych kontraktu usługi jak pokazano w pierwszym przykładzie. Ponadto klienta i usługi zostaną skonfigurowane w taki sam sposób. W tym przykładzie jest tworzony kanał, do Przenieś obiekt, a następnie uruchom ten sam sposób. Jednak w tym przykładzie utworzysz klienta, który wywołuje usługę, przekazywanie obiektu przez wartość. Metody usługi, które klient nawiąże połączenie w kontrakcie usługi jest wyświetlane wytłuszczonym drukiem:  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a>Dodawanie kodu do klienta, który wysyła obiektu przez wartość  
 Poniższy kod przedstawia sposób klient tworzy nowy obiekt klienta przez wartość tworzy kanał do komunikacji z `ICustomerManager` usługi i wysyła do niego obiekt klienta.  
  
 Obiekt klienta będą serializowane i wysyłane do usługi, w którym jest deserializacji przez usługę do nowej kopii tego obiektu.  Wszystkie metody wywołuje usługę dla tego obiektu będą wykonywane tylko lokalnie na serwerze. Należy pamiętać, że ten kod ilustruje wysyłania typem pochodnym jest (`PremiumCustomer`).  Kontrakt usługi oczekuje `Customer` obiekt, ale dane usługi należy Zwiń używa [<xref:System.Runtime.Serialization.KnownTypeAttribute>] atrybutu, aby wskazać, że `PremiumCustomer` również jest dozwolone.  Usługi WCF zakończy się niepowodzeniem prób do serializacji lub deserializacji innego typu, za pośrednictwem tego interfejsu usługi.  
  
```  
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
 W tym scenariuszu aplikacji klienckiej nawiązuje połączenie z usługą zdalnego i metoda zwraca obiekt, który jest przekazywana przez odwołanie z usługi do klienta.  
  
 Jak wspomniano wcześniej, usługi WCF zawsze zwraca obiekt przez wartość.  Jednak można uzyskać podobny efekt za pomocą <xref:System.ServiceModel.EndpointAddress10> klasy.  <xref:System.ServiceModel.EndpointAddress10> Jest obiektem serializacji przez wartość używaną przez klienta można uzyskać obiektu sesyjnych przez odwołania na serwerze.  
  
 Zachowanie obiektu przez odwołanie w programie WCF wyświetlane w tym scenariuszu są inne niż modelu DCOM.  W modelu DCOM Serwer może zwrócić przez odwołanie obiektu do klienta bezpośrednio, a klient może wywołać metody tego obiektu, które wykonania na serwerze.  W programie WCF jednak obiektu zwróconego jest zawsze przez wartość.  Klient musi mieć przez wartość tego obiektu, w reprezentowany przez <xref:System.ServiceModel.EndpointAddress10> i użyć go do tworzenia własnego obiektu sesyjnych przez odwołanie.  Wywołania metody klienta w obiekcie sesyjnych wykonania na serwerze. Innymi słowy ten obiekt przez odwołanie w programie WCF jest normalne usługi WCF, który jest skonfigurowany tak, aby sesyjnych.  
  
 W programie WCF sesja jest sposób korelacji wiele komunikatów przesyłanych między dwoma punktami końcowymi.  Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesja zostanie nawiązane między klientem a serwerem.  Klient będzie używać jednego wystąpienia unikatowy obiektu po stronie serwera dla wszystkich jego interakcji w tym jednej sesji. Przekroczono kontrakty WCF są podobne do wzorców żądanie/odpowiedź nawiązaniem połączenia sieciowego.  
  
 Ten scenariusz jest reprezentowana przez następującą metodę modelu DCOM.  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a>Krok 1: Definiowanie interfejsu usługi Sessionful WCF i wdrażania  
 Najpierw należy zdefiniować interfejsu usługi WCF, która zawiera obiekt sesyjnych.  
  
 W tym kodzie sesyjnych obiekt jest oznaczony atrybutem `ServiceContract` atrybut, który identyfikuje ją jako regularne interfejsu usługi WCF.  Ponadto <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> właściwość jest ustawiona na wskazują, będzie on zamykania usługi.  
  
```  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 Poniższy kod przedstawia implementacji usługi.  
  
 Usługa jest oznaczona atrybutem [ServiceBehavior] i jego właściwość InstanceContextMode ustawioną InstanceContextMode.PerSessions w celu wskazania, że unikatowe wystąpienie tego typu powinny być tworzone dla każdej sesji.  
  
```  
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
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a>Krok 2: Definiowanie usługi fabryka WCF dla obiekt zamykania  
 Usługa, która tworzy obiekt sesyjnych musi zdefiniowany i zaimplementowana. Poniższy kod przedstawia, jak to zrobić. Ten kod tworzy innej usługi WCF, która zwraca <xref:System.ServiceModel.EndpointAddress10> obiektu.  Jest to format możliwy do serializacji dla punktu końcowego może użyć do utworzenia obiektu sesji pełnej.  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 Poniżej znajduje się wdrożenia tej usługi. Ta implementacja obsługuje pojedyncze fabryki kanałów do tworzenia obiektów sesyjnych.  Gdy `GetInstanceAddress` jest nazywane, tworzy kanału i tworzy <xref:System.ServiceModel.EndpointAddress10> obiekt, który wskazuje zdalny adres skojarzony z tym kanale.   <xref:System.ServiceModel.EndpointAddress10> ma typ danych, który może być zwracany do klienta przez wartość.  
  
```  
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
 Aby zapewnić obsługę tych usług, należy wprowadzić następujące dodatki do pliku konfiguracji serwera (web.config).  
  
1.  Dodaj `<client>` opisy punktu końcowego dla obiektu sesyjnych.  W tym scenariuszu serwer działa jako klient i musi być skonfigurowany, aby je włączyć.  
  
2.  W `<services>` sekcji, Zadeklaruj punktów końcowych usługi dla obiekt fabryki i sessionful.  Dzięki temu klient do komunikacji z punktami końcowymi usługi, uzyskać <xref:System.ServiceModel.EndpointAddress10> i utworzyć podczas zamykania kanału sesji.  
  
 Oto przykładowy plik konfiguracji przy użyciu tych ustawień:  
  
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
  
 Dodaj następujące wiersze do aplikacji konsoli, w celu hosta samodzielnego usługi i uruchomić aplikację.  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a>Krok 4: Konfigurowanie klienta i wywołania tej usługi  
 Konfigurowanie klienta do komunikowania się z usługi WCF, wprowadzając następujące wpisy w pliku konfiguracji projektu aplikacji (app.config).  
  
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
  
 Do wywołania tej usługi, należy dodać kodu do klienta, aby wykonać następujące czynności:  
  
1.  Tworzenie kanału do `ISessionBoundFactory` usługi.  
  
2.  Użyj kanału do wywołania `ISessionBoundFactory` usługi Uzyskaj <xref:System.ServiceModel.EndpointAddress10> bbject.  
  
3.  Użyj <xref:System.ServiceModel.EndpointAddress10> do utworzenia kanału do uzyskania zamykania obiektu.  
  
4.  Wywołanie `SetCurrentValue` i `GetCurrentValue` używane w wielu wywołań metody, aby zademonstrować pozostaje w tym samym wystąpieniu obiektu.  
  
```  
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
 [Podstawy programowania przy użyciu programu WCF](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Projektowanie i implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Kompilowanie klientów](../../../docs/framework/wcf/building-clients.md)  
 [Usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md)
