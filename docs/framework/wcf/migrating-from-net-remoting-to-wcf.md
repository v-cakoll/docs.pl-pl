---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 8dcc019017195fd55231fbea3493d4c53d500cb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183962"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrowanie z programu .NET Remoting do programu WCF
W tym artykule opisano sposób migracji aplikacji, która używa programu .NET Remoting do używania programu Windows Communication Foundation (WCF). Porównuje podobne pojęcia między tymi produktami, a następnie opisuje, jak wykonać kilka typowych scenariuszy komunikacji zdalnej w WCF.  
  
 .NET Remoting jest starszy produkt, który jest obsługiwany tylko dla zgodności z powrotem. Nie jest bezpieczny w środowiskach zaufania mieszanego, ponieważ nie może utrzymać oddzielnych poziomów zaufania między klientem a serwerem. Na przykład nigdy nie należy udostępniać punktu końcowego .NET Remoting do Internetu lub niezaufanych klientów. Firma Microsoft zaleca, aby istniejące aplikacje komunikacji zdalnej były migrowane do nowszych i bezpieczniejszych technologii. Jeśli projekt aplikacji używa tylko protokołu HTTP i jest restful, zalecamy ASP.NET interfejsu API sieci Web. Aby uzyskać więcej informacji, zobacz ASP.NET interfejsu API sieci Web. Jeśli aplikacja jest oparta na soap lub wymaga protokołów innych niż Http, takich jak TCP, zaleca się WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porównywanie komunikacji zdalnej .NET z WCF  
 W tej sekcji porównuje podstawowe bloki konstrukcyjne .NET Remoting z ich odpowiednikami WCF. Użyjemy tych bloków konstrukcyjnych później do utworzenia niektórych typowych scenariuszy klient-serwer w WCF. Na poniższym wykresie podsumowano główne podobieństwa i różnice między .NET Remoting i WCF.  
  
||Wywołaniem funkcji zdalnych .NET|WCF|  
|-|-------------------|---------|  
|Typ serwera|Podklasa MarshalByRefObject|Oznacz za pomocą atrybutu [ServiceContract]|  
|Operacje serwisowe|Metody publiczne typu serwera|Oznacz za pomocą atrybutu [OperationContract]|  
|Serializacja|ISerializable lub [Serializable]|DataContractSerializer lub XmlSerializer|  
|Obiekty przekazywane|Wartość według wartości lub odwołanie|Tylko wartość według wartości|  
|Błędy/wyjątki|Dowolny wyjątek, który można szeregizać|> faultcontract\<TDetail|  
|Obiekty serwera proxy klienta|Silnie wpisane przezroczyste serwery proxy są tworzone automatycznie z MarshalByRefObjects|Silnie typizowane serwery proxy są generowane na\<żądanie przy użyciu kanału ChannelFactory TChannel>|  
|Wymagana platforma|Zarówno klient, jak i serwer muszą używać systemu operacyjnego Microsoft I .NET|Wieloplatformowość|  
|Format wiadomości|Private|Normy branżowe (SOAP, WS-*, itp.)|  
  
### <a name="server-implementation-comparison"></a>Porównanie implementacji serwera  
  
#### <a name="creating-a-server-in-net-remoting"></a>Tworzenie serwera w systemie remoting .NET  
 .NET Typy serwerów remoting musi pochodzić z MarshalByRefObject i zdefiniować metody, które klient może wywołać, jak poniżej:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Publiczne metody tego typu serwera stają się kontraktem publicznym dostępnym dla klientów.  Nie ma separacji między interfejsem publicznym serwera i jego implementacji — jeden typ obsługuje zarówno.  
  
 Po zdefiniowaniu typu serwera można go udostępnić klientom, na przykład w poniższym przykładzie:  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),
    "RemotingServer",
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 Istnieje wiele sposobów, aby udostępnić typ komunikacji zdalnej jako serwer, w tym przy użyciu plików konfiguracyjnych. To tylko jeden z przykładów.  
  
#### <a name="creating-a-server-in-wcf"></a>Tworzenie serwera w WCF  
 Równoważny krok w WCF polega na utworzeniu dwóch typów - publicznego "umowy o świadczenie usług" i konkretnej implementacji. Pierwszy jest zadeklarowany jako interfejs oznaczony jako [ServiceContract]. Metody dostępne dla klientów są oznaczone symbolem [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementacja serwera jest zdefiniowana w osobnej konkretnej klasie, jak w poniższym przykładzie:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Po zdefiniowaniu tych typów serwer WCF może być udostępniony klientom, na przykład w poniższym przykładzie:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> Protokół TCP jest używany w obu przykładach, aby zachować je tak podobne, jak to możliwe. Zapoznaj się z for-ów scenariusz w dalszej części tego tematu na przykłady przy użyciu protokołu HTTP.  
  
 Istnieje wiele sposobów konfigurowania i hostować usługi WCF. Jest to tylko jeden z przykładów, znany jako "self-hosted". Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
- [Instrukcje: definiowanie kontraktu usługi](how-to-define-a-wcf-service-contract.md)  
  
- [Konfigurowanie usług za pomocą plików konfiguracji](configuring-services-using-configuration-files.md)  
  
- [Usługi hostingowe](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porównanie implementacji klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Tworzenie klienta w sieci .NET Remoting  
 Po udostępnieniu obiektu serwera remotingu .NET może on być zużywany przez klientów, jak w poniższym przykładzie:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 RemotingServer wystąpienie zwrócone z Activator.GetObject() jest znany jako "przezroczysty serwer proxy." Implementuje publiczny interfejs API dla typu RemotingServer na kliencie, ale wszystkie metody wywołać obiekt serwera uruchomiony w innym procesie lub komputerze.  
  
#### <a name="creating-a-client-in-wcf"></a>Tworzenie klienta w WCF  
 Równoważny krok w WCF polega na użyciu fabryki kanałów, aby utworzyć serwer proxy jawnie. Podobnie jak funkcja komunikacji zdalnej, obiekt proxy może służyć do wywoływania operacji na serwerze, jak w poniższym przykładzie:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 W tym przykładzie pokazano programowania na poziomie kanału, ponieważ jest najbardziej podobny do przykładu komunikacji zdalnej. Dostępne jest również **podejście Dodaj odwołanie do usługi** w programie Visual Studio, które generuje kod w celu uproszczenia programowania klienta. Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
- [Programowanie na poziomie kanału klienta](./extending/client-channel-level-programming.md)  
  
- [Jak: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Użycie serializacji  
 Zarówno .NET Remoting i WCF używać serializacji do wysyłania obiektów między klientem a serwerem, ale różnią się one w tych ważnych sposobów:  
  
1. Używają różnych serializatorów i konwencji, aby wskazać, co do serializacji.  
  
2. .NET Remoting obsługuje serializacji "przez odwołanie", która umożliwia dostęp do metody lub właściwości w jednej warstwie do wykonania kodu w drugiej warstwie, która znajduje się poza granicami zabezpieczeń. Ta funkcja uwidacznia luki w zabezpieczeniach i jest jednym z głównych powodów, dla których punkty końcowe komunikacji zdalnej nigdy nie powinny być narażone na niezaufanych klientów.  
  
3. Serializacja używana przez remoting jest opt-out (jawnie wykluczyć, co nie serializacji) i WCF serializacji jest opt-in (jawnie oznaczyć, które elementy członkowskie do serializacji).  
  
#### <a name="serialization-in-net-remoting"></a>Serializacja w .NET Remoting  
 Funkcja .NET Remoting obsługuje dwa sposoby serializacji i deserializacji obiektów między klientem a serwerem:  
  
- *Według wartości* — wartości obiektu są serializowane między granicami warstwy, a nowe wystąpienie tego obiektu jest tworzone w innej warstwie. Wszelkie wywołania metod lub właściwości tego nowego wystąpienia są wykonywane tylko lokalnie i nie mają wpływu na oryginalny obiekt lub warstwę.  
  
- *Przez odwołanie* — specjalne "odwołanie do obiektu" jest serializowane w granicach warstwy. Gdy jedna warstwa współdziała z metodami lub właściwościami tego obiektu, komunikuje się z powrotem do oryginalnego obiektu w oryginalnej warstwie. Obiekty według odwołania mogą przepływać w każdym kierunku — serwer do klienta lub klient do serwera.  
  
 Typy według wartości w remoting są oznaczone atrybutem [Serializable] lub implementują ISerializable, jak w poniższym przykładzie:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Typy według odwołań pochodzą z MarshalByRefObject klasy, jak w poniższym przykładzie:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Jest niezwykle ważne, aby zrozumieć implikacje remoting przez odniesienia obiektów. Jeśli warstwa (klient lub serwer) wysyła obiekt według odwołania do innej warstwy, wszystkie wywołania metody są wykonywane z powrotem w warstwie posiadającej obiekt. Na przykład metody wywołujące klienta na obiekcie odwołania zwróconego przez serwer będą wykonywać kod na serwerze. Podobnie metody wywoływania serwera na obiektie według odwołania dostarczonych przez klienta wykona kod z powrotem na kliencie. Z tego powodu użycie funkcji .NET Remoting jest zalecane tylko w w pełni zaufanych środowiskach. Uwidacznianie publicznego punktu końcowego komunikacji zdalnej .NET na niezaufanych klientach spowoduje, że serwer komunikacji zdalnej będzie narażony na ataki.  
  
#### <a name="serialization-in-wcf"></a>Serializacja w WCF  
 WCF obsługuje tylko przez wartość serializacji. Najczęstszym sposobem definiowania typu do wymiany między klientem a serwerem jest jak w poniższym przykładzie:  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 Atrybut [DataContract] identyfikuje ten typ jako taki, który może być serializowany i deserializowany między klientem a serwerem. Atrybut [DataMember] identyfikuje poszczególne właściwości lub pola do serializacji.  
  
 Gdy WCF wysyła obiekt między warstwami, serializuje tylko wartości i tworzy nowe wystąpienie obiektu w innej warstwie. Wszelkie interakcje z wartościami obiektu występują tylko lokalnie — nie komunikują się z drugą warstwą sposób .NET Remoting przez odwołanie obiektów zrobić. Aby uzyskać więcej informacji, zobacz [Serializacja i deserializacja](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Możliwości obsługi wyjątków  
  
#### <a name="exceptions-in-net-remoting"></a>Wyjątki w obszarze .NET Remoting  
 Wyjątki generowane przez serwer komunikacji zdalnej są serializowane, wysyłane do klienta i generowane lokalnie na kliencie, jak każdy inny wyjątek. Wyjątki niestandardowe można utworzyć, klasyfikując typ wyjątku i oznaczając go za pomocą [Serializable].   Większość wyjątków framework są już oznaczone w ten sposób, dzięki czemu większość być generowane przez serwer, serializowane i ponownie generowane na kliencie. Chociaż ten projekt jest wygodny podczas tworzenia, informacje po stronie serwera mogą przypadkowo zostać ujawnione klientowi. Jest to jeden z wielu powodów, dla których program komunikacji zdalnej powinien być używany tylko w w pełni zaufanych środowiskach.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Wyjątki i usterki w WCF  
 WCF nie zezwala na arbitralne typy wyjątków mają być zwracane z serwera do klienta, ponieważ może to prowadzić do niezamierzonego ujawnienia informacji. Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, powoduje, że ogólne przeznaczenie FaultException do rzuconego na klienta. Ten wyjątek nie zawiera żadnych informacji, dlaczego i gdzie wystąpił problem, a dla niektórych aplikacji jest to wystarczające. Aplikacje, które muszą komunikować się z klientem bogatsze informacje o błędach, robią to, definiując kontrakt o usterki.  
  
 Aby to zrobić, należy najpierw utworzyć typ [DataContract] do przenoszenia informacji o usterce.  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 Określ kontrakt błędów do użycia dla każdej operacji serwisu.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Serwer zgłasza warunki błędu, rzucając FaultException.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {
        CustomerId = customerId,
        ErrorMessage = "Illegal customer Id"
    });  
```  
  
 I za każdym razem, gdy klient wysyła żądanie do serwera, może przechwytywać błędy jako normalne wyjątki.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 Aby uzyskać więcej informacji <xref:System.ServiceModel.FaultException>na temat kontraktów usterek, zobacz .  
  
### <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
  
#### <a name="security-in-net-remoting"></a>Zabezpieczenia w komunikacji zdalnej .NET  
 Niektóre kanały komunikacji zdalnej platformy .NET obsługują funkcje zabezpieczeń, takie jak uwierzytelnianie i szyfrowanie w warstwie kanału (IPC i TCP). Kanał HTTP opiera się na internetowych usługach informacyjnych (IIS) zarówno do uwierzytelniania, jak i szyfrowania. Pomimo tej pomocy należy rozważyć .NET Remoting niezabezpieczony protokół komunikacyjny i używać go tylko w w pełni zaufanych środowiskach. Nigdy nie udostępniaj publicznego punktu końcowego komunikacji zdalnej w Internecie lub niezaufanych klientów.  
  
#### <a name="security-in-wcf"></a>Zabezpieczenia w programie WCF  
 WCF został zaprojektowany z myślą o bezpieczeństwie, częściowo w celu wyeliminowania rodzajów luk znalezionych w .NET Remoting. WCF oferuje zabezpieczenia na poziomie transportu i wiadomości i oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej. Aby uzyskać więcej informacji, zobacz następujące tematy:  
  
- [Zabezpieczenia](./feature-details/security.md)  
  
- [Wskazówki dotyczące zabezpieczeń WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migracja do WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Dlaczego migracji z komunikacji zdalnej do WCF?  
  
- **.NET Remoting jest produktem starszej wersji.** Jak opisano w [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), jest uważany za produkt starszej wersji i nie jest zalecany do nowego rozwoju. WCF lub ASP.NET web API są zalecane dla nowych i istniejących aplikacji.  
  
- **WCF używa standardów międzyplatformowych.** WCF został zaprojektowany z myślą o interoperacyjności między platformami i obsługuje wiele standardów branżowych (SOAP, WS-Security, WS-Trust itp.). Usługa WCF może współpracować z klientami działającymi w systemach operacyjnych innych niż Windows. Komunikacji zdalnej został zaprojektowany przede wszystkim dla środowisk, w których zarówno serwer, jak i aplikacje klienckie są uruchamiane przy użyciu programu .NET Framework w systemie operacyjnym Windows.
  
- **WCF ma wbudowane zabezpieczenia.** WCF został zaprojektowany z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania, bezpieczeństwa na poziomie transportu, zabezpieczeń na poziomie wiadomości itp. Komunikacji zdalnej został zaprojektowany, aby ułatwić aplikacjom współdziałanie, ale nie został zaprojektowany, aby być bezpieczne w środowiskach niezaufanych. WCF został zaprojektowany do pracy w środowiskach zaufanych i niezaufanych.  
  
### <a name="migration-recommendations"></a>Zalecenia dotyczące migracji  
 Poniżej przedstawiono zalecane kroki migracji z .NET Remoting do WCF:  
  
- **Utwórz umowę serwisową.** Zdefiniuj typy interfejsów usługi i oznacz je atrybutem [ServiceContract]. Oznacz wszystkie metody, które klienci będą mogli wywołać za pomocą [OperationContract].  
  
- **Utwórz kontrakt na dane.** Zdefiniuj typy danych, które będą wymieniane między serwerem a klientem, i oznacz je atrybutem [DataContract]. Zaznacz wszystkie pola i właściwości, których klient będzie mógł używać z programem [DataMember].  
  
- **Utwórz kontrakt na usterkę (opcjonalnie).** Utwórz typy, które będą wymieniane między serwerem a klientem po napotkaniu błędów. Oznacz te typy za pomocą [DataContract] i [DataMember], aby były serializowalne. Dla wszystkich operacji usługi oznaczone jako [OperationContract], również oznaczyć je z [FaultContract], aby wskazać, które błędy mogą zwracać.  
  
- **Konfigurowanie i hostowania usługi.** Po utworzeniu umowy serwisowej następnym krokiem jest skonfigurowanie powiązania, aby udostępnić usługę w punkcie końcowym. Aby uzyskać więcej informacji, zobacz [Punkty końcowe: Adresy, Powiązania i Kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Po migracji aplikacji komunikacji zdalnej do WCF, nadal ważne jest, aby usunąć zależności na .NET Komunikacji zdalnej. Gwarantuje to, że wszelkie luki w zabezpieczeniach są usuwane z aplikacji. Te kroki obejmują następujące czynności:  
  
- **Zaprzestanie używania MarshalByRefObject.** Typu MarshalByRefObject istnieje tylko dla komunikacji zdalnej i nie jest używany przez WCF. Wszystkie typy aplikacji, które podklasy MarshalByRefObject powinny zostać usunięte lub zmienione.  
  
- **Zaprzestać używania [Serializable] i ISerializable.** Atrybut [Serializable] i interfejs ISerializable zostały pierwotnie zaprojektowane do serializacji typów w zaufanych środowiskach i są używane przez program Remoting. Serializacja WCF zależy od typów oznaczonych jako [DataContract] i [DataMember]. Typy danych używane przez aplikację powinny być modyfikowane w celu użycia [DataContract] i nie używać funkcji ISerializable lub [Serializable].  
  
### <a name="migration-scenarios"></a>Scenariusze migracji  
 Teraz zobaczmy, jak wykonać następujące typowe scenariusze komunikacji zdalnej w WCF:  
  
1. Serwer zwraca klientowi wartość po wartości obiektu  
  
2. Serwer zwraca obiekt przez odwołanie do klienta  
  
3. Klient wysyła obiekt według wartości do serwera  
  
> [!NOTE]
> Wysyłanie obiektu przez odwołanie od klienta do serwera nie jest dozwolone w WCF.  
  
 Podczas odczytywania tych scenariuszy, załóżmy, że nasze interfejsy linii bazowej dla .NET Komunikacji zdalnej wyglądają jak w poniższym przykładzie. Implementacja .NET Remoting nie jest w tym miejscu ważne, ponieważ chcemy zilustrować tylko sposób używania WCF do implementowania równoważnych funkcji.  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Scenariusz 1.  
 W tym scenariuszu pokazano serwer zwraca obiekt do klienta według wartości. WCF zawsze zwraca obiekty z serwera według wartości, więc następujące kroki po prostu opisują sposób tworzenia normalnej usługi WCF.  
  
1. Rozpocznij od zdefiniowania interfejsu publicznego dla usługi WCF i oznacz go atrybutem [ServiceContract]. Używamy [OperationContract] do identyfikowania metod po stronie serwera, które nasz klient wywoła.  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. Następnym krokiem jest utworzenie kontraktu danych dla tej usługi. Robimy to, tworząc klasy (nie interfejsy) oznaczone atrybutem [DataContract]. Poszczególne właściwości lub pola, które chcemy być widoczne zarówno dla klienta, jak i dla serwera, są oznaczone symbolem [DataMember]. Jeśli chcemy, aby typy pochodne były dozwolone, musimy użyć [KnownType] atrybut do ich identyfikacji. Jedynymi typami WCF pozwoli być serializowane lub deserialized dla tej usługi są te w interfejsie usługi i tych "znanych typów". Próba wymiany dowolnego innego typu, który nie znajduje się na tej liście, zostanie odrzucona.  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. Następnie zapewniamy implementację interfejsu usługi.  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. Aby uruchomić usługę WCF, musimy zadeklarować punkt końcowy, który udostępnia tego interfejsu usługi przy określonym adresie URL przy użyciu określonego powiązania WCF. Zazwyczaj odbywa się to przez dodanie następujących sekcji do pliku web.config projektu serwera.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. Usługę WCF można następnie uruchomić z następującym kodem:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Po uruchomieniu tego ServiceHost używa pliku web.config do ustanowienia właściwej umowy, powiązania i punktu końcowego. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie usług przy użyciu plików konfiguracyjnych](./configuring-services-using-configuration-files.md). Ten styl uruchamiania serwera jest znany jako własny hosting. Aby dowiedzieć się więcej o innych możliwościach obsługi usług WCF, zobacz [Usługi hostingowe](./hosting-services.md).  
  
6. App.config projektu klienta musi zadeklarować pasujące informacje o powiązaniach dla punktu końcowego usługi. Najprostszym sposobem, aby to zrobić w programie Visual Studio jest użycie **Dodaj service reference**, który automatycznie zaktualizuje plik app.config. Alternatywnie te same zmiany można dodać ręcznie.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     Aby uzyskać więcej informacji na temat **używania dodatku odwołania do usługi,** zobacz [Jak: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Teraz możemy wywołać usługę WCF z klienta. Robimy to, tworząc fabrykę kanałów dla tej usługi, prosząc ją o kanał i bezpośrednio wywołując metodę, którą chcemy na tym kanale. Możemy to zrobić, ponieważ kanał implementuje interfejs usługi i obsługuje podstawową logikę żądania/odpowiedzi dla nas. Zwracana wartość z tego wywołania metody jest deserializowanej kopii odpowiedzi serwera.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Obiekty zwracane przez WCF z serwera do klienta są zawsze według wartości. Obiekty są deserializowane kopie danych wysyłanych przez serwer. Klient może wywołać metody na tych kopiach lokalnych bez żadnego niebezpieczeństwa wywoływania kodu serwera za pomocą wywołań zwrotnych.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scenariusz 2: Serwer zwraca obiekt według odwołania  
 W tym scenariuszu pokazano serwer dostarczanie obiektu do klienta przez odwołanie. W .NET Remoting jest obsługiwany automatycznie dla dowolnego typu pochodzącego z MarshalByRefObject, który jest serializowany przez odwołanie. Przykładem tego scenariusza jest umożliwienie wielu klientom mieć niezależne sesyjne obiekty po stronie serwera. Jak wcześniej wspomniano, obiekty zwracane przez usługę WCF są zawsze według wartości, więc nie ma bezpośredniego odpowiednika obiektu przez odwołanie, ale jest <xref:System.ServiceModel.EndpointAddress10> możliwe, aby osiągnąć coś podobnego do semantyki przez odwołanie za pomocą obiektu. Jest to obiekt według wartości, który może być używany przez klienta do uzyskania sesyjnego obiektu po odwołań na serwerze. Dzięki temu scenariusz posiadania wielu klientów z niezależnymi obiektami po stronie serwera.  
  
1. Po pierwsze musimy zdefiniować kontrakt serwisowy WCF, który odpowiada samego obiektu sessionful.  
  
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
  
    > [!TIP]
    > Należy zauważyć, że obiekt sessionful jest oznaczony jako [ServiceContract], co czyni go normalnym interfejsem usługi WCF. Ustawienie SessionMode właściwość wskazuje, że będzie to usługa sesyjna. W WCF sesji jest sposobem korelowania wielu komunikatów wysyłanych między dwoma punktami końcowymi. Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, zostanie ustanowiona sesja między klientem a serwerem. Klient użyje pojedynczego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej pojedynczej sesji.  
  
2. Następnie musimy zapewnić implementację tego interfejsu usługi. Oznaczając go za pomocą [ServiceBehavior] i ustawiając InstanceContextMode, informujemy WCF, że chcemy użyć unikatowego wystąpienia tego typu dla każdej sesji.  
  
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
  
3. Teraz potrzebujemy sposobu, aby uzyskać wystąpienie tego obiektu sesji. Robimy to, tworząc inny interfejs usługi WCF, który zwraca Obiekt EndpointAddress10. Jest to serializable formie punktu końcowego, który klient może użyć do utworzenia obiektu sessionful.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     I wdrażamy tę usługę WCF:  
  
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
  
     Ta implementacja utrzymuje fabrykę pojedynczego kanału do tworzenia obiektów sesji. Gdy getInstanceAddress() jest wywoływana, tworzy kanał i tworzy EndpointAddress10 obiektu, który skutecznie wskazuje na adres zdalny skojarzony z tym kanałem. EndpointAddress10 jest po prostu typem danych, który może być zwracany do wartości klienta według wartości.  
  
4. Musimy zmodyfikować plik konfiguracyjny serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:  
  
    1. Zadeklaruj sekcję \<> klienta, która opisuje punkt końcowy dla obiektu sesji. Jest to konieczne, ponieważ serwer działa również jako klient w tej sytuacji.  
  
    2. Zadeklaruj punkty końcowe dla obiektu fabrycznego i sesyjnego. Jest to konieczne, aby umożliwić klientowi komunikować się z punktami końcowymi usługi, aby uzyskać EndpointAddress10 i utworzyć kanał sessionful.  
  
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
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
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
  
     A następnie możemy uruchomić te usługi:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Konfigurujemy klienta, deklarując te same punkty końcowe w pliku app.config projektu.  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
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
  
6. Aby utworzyć i używać tego obiektu sesyjnego, klient musi wykonać następujące kroki:  
  
    1. Utwórz kanał do usługi ISessionBoundFactory.  
  
    2. Użyj tego kanału, aby wywołać tę usługę, aby uzyskać EndpointAddress10.  
  
    3. EndpointAddress10 służy do tworzenia kanału w celu uzyskania obiektu sesji.  
  
    4. Interakcja z sessionful obiektu, aby zademonstrować, że pozostaje to samo wystąpienie w wielu wywołaniach.  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 WCF zawsze zwraca obiekty według wartości, ale jest możliwe do obsługi odpowiednika semantyki odwołania za pomocą EndpointAddress10. Dzięki temu klient żądać sesyjne wystąpienie usługi WCF, po czym można wchodzić w interakcje z nim, jak każda inna usługa WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scenariusz 3: Klient wysyła serwer jako wystąpienie według wartości  
 W tym scenariuszu pokazano klienta wysyłania wystąpienia obiektu nieizbowy do serwera według wartości. Ponieważ WCF wysyła tylko obiekty według wartości, w tym scenariuszu pokazuje normalne użycie WCF.  
  
1. Użyj tej samej usługi WCF ze scenariusza 1.  
  
2. Użyj klienta, aby utworzyć nowy obiekt według wartości (Klient), utworzyć kanał do komunikowania się z usługą ICustomerService i wysłać obiekt do niego.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {
   FirstName = "Bob",
   LastName = "Jones",
   CustomerId = 43,
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     Obiekt klienta zostanie szeregizowany i wysłany do serwera, gdzie jest deserializowany do nowej kopii tego obiektu.  
  
    > [!NOTE]
    > Ten kod ilustruje również wysyłanie typu pochodnego (PremiumCustomer). Interfejs usługi oczekuje Customer obiektu, ale [KnownType] atrybut w Customer klasy wskazane PremiumCustomer był również dozwolone. WCF zakończy się niepowodzeniem wszelkie próby serializacji lub deserializacji dowolnego innego typu za pośrednictwem tego interfejsu usługi.  
  
 Normalna wymiana danych WCF jest według wartości. Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych wykonuje tylko lokalnie — nie będzie wywoływać kodu w innej warstwie. Chociaż jest możliwe, aby osiągnąć coś jak obiekty odwołania zwracane *z* serwera, nie jest możliwe dla klienta, aby przekazać obiekt by-reference *do* serwera. Scenariusz, który wymaga konwersacji tam iz powrotem między klientem a serwerem można osiągnąć w WCF przy użyciu usługi dupleksu. Aby uzyskać więcej informacji, zobacz [Usługi dupleksu](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Podsumowanie  
 .NET Remoting to struktura komunikacji przeznaczona do użycia tylko w w pełni zaufanych środowiskach. Jest to produkt starszej wersji i obsługiwany tylko w celu zapewnienia zgodności z powrotem. Nie należy używać do tworzenia nowych aplikacji. Z drugiej strony WCF został zaprojektowany z myślą o bezpieczeństwie i jest zalecany dla nowych i istniejących aplikacji. Firma Microsoft zaleca migrację istniejących aplikacji komunikacji zdalnej w celu użycia interfejsu WCF lub ASP.NET interfejsu API sieci Web.
