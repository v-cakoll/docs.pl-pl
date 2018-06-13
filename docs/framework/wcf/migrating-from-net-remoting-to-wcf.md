---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 6041cd9ac066d932811cc489222c8cbf03debb75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509143"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrowanie z programu .NET Remoting do programu WCF
W tym artykule opisano sposób migracji aplikacji, która używa .NET Remoting do używania usług Windows Communication Foundation (WCF). Porównuje podobne pojęcia między tymi produktami, a następnie opisano, jak wykonać kilka typowych scenariuszy komunikacji zdalnej programu WCF.  
  
 .NET remoting jest starszy produkt, który jest obsługiwany tylko w przypadku zgodności z poprzednimi wersjami. Nie jest bezpieczne w środowiskach mieszanych zaufania, ponieważ nie można zachować poziomy zaufania oddzielne między klientem i serwerem. Na przykład nigdy nie powinny ujawniać punkt końcowy .NET Remoting do Internetu lub niezaufanego klientami. Zalecamy Remoting istniejące aplikacje można migrować do nowszej i bezpieczniejsze technologii. Jeśli aplikacja — projekt używa tylko protokołu HTTP i RESTful, firma Microsoft zaleca interfejsu API sieci Web platformy ASP.NET. Aby uzyskać więcej informacji zobacz interfejsu API sieci Web platformy ASP.NET. Jeśli aplikacja jest oparta na SOAP lub wymaga protokołów innych niż Http, takie jak protokół TCP, firma Microsoft zaleca WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porównywanie .NET Remoting do programu WCF  
 Ta sekcja porównuje podstawowe bloki konstrukcyjne .NET Remoting z ich odpowiedniki WCF. Te bloki konstrukcyjne zostanie wykorzystany później można utworzyć niektórych typowych scenariuszy klient serwer programu WCF. Poniższy schemat zawiera podsumowanie głównych podobieństwa i różnice funkcji zdalnych .NET i WCF.  
  
||Wywołaniem funkcji zdalnych .NET|WCF|  
|-|-------------------|---------|  
|Typ serwera|Podklasy elementu MarshalByRefObject|Oznacz z atrybutem [ServiceContract]|  
|Operacje usługi|Metody publiczne na typ serwera|Oznacz z atrybutem [OperationContract]|  
|Serializacja|ISerializable lub [Serializable]|DataContractSerializer, lub XmlSerializer|  
|Obiekty przekazany|Przez wartości lub według odwołania|Przez wartość tylko|  
|Błędy/wyjątków|Można serializować wyjątku|FaultContract\<TDetail>|  
|Obiekty serwera proxy klienta|Jednoznacznie przezroczysty serwery proxy są tworzone automatycznie na podstawie elementów MarshalByRefObjects|Jednoznacznie serwery proxy są generowane na żądanie przy użyciu elementu ChannelFactory\<TChannel >|  
|Platforma wymagane|Klienta i serwera, należy użyć programu Microsoft OS i .NET|Obsługujący wiele platform|  
|Format komunikatu|Private|Standardy branżowe (SOAP, WS-* itp.)|  
  
### <a name="server-implementation-comparison"></a>Porównanie implementacji serwera  
  
#### <a name="creating-a-server-in-net-remoting"></a>Tworzenie serwera w funkcji zdalnych .NET  
 Typy serwerów .NET remoting musi pochodzić od elementu MarshalByRefObject i definiowanie metod, które klient może wywoływać podobne do poniższych:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Metody publiczne tego typu serwera stają się publicznego kontraktu dostępne dla klientów.  Brak rozdzielenie interfejsu publicznego serwera i jego wdrożenie — jeden typ obsługuje zarówno.  
  
 Po zdefiniowaniu typu serwera, można go było dostępne dla klientów, takie jak w poniższym przykładzie:  
  
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
  
 Istnieje wiele sposobów, aby udostępnić typ usług zdalnych jako serwer, w tym za pomocą plików konfiguracji. To jest tylko jeden przykład.  
  
#### <a name="creating-a-server-in-wcf"></a>Tworzenie serwera w programie WCF  
 Odpowiednik etapem WCF obejmuje tworzenie dwa typy — publiczny "kontraktu usługi" i konkretną implementację. Pierwszy jest zadeklarowany jako interfejs oznaczony atrybutem [ServiceContract]. Metody dostępne dla klientów są oznaczone ikoną z elementu [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementacji serwera jest zdefiniowany w oddzielnych klasą, podobnie jak w poniższym przykładzie:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Po zdefiniowaniu tych typów serwera WCF można udostępnić klientom, podobnie jak w poniższym przykładzie:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  TCP jest używany w obu przykładach, aby były jak najbardziej podobna. Zapoznaj się z przewodników scenariusz w dalszej części tego tematu, aby uzyskać przykłady pokazujące, przy użyciu protokołu HTTP.  
  
 Istnieje wiele sposobów, aby skonfigurować i do obsługi usług WCF. To jest tylko jeden przykład, nazywany "hosta samodzielnego". Więcej informacji znajduje się w następujących tematach:  
  
-   [Instrukcje: definiowanie kontraktu usługi](how-to-define-a-wcf-service-contract.md)  
  
-   [Konfigurowanie usług za pomocą plików konfiguracji](configuring-services-using-configuration-files.md)  
  
-   [Usługi hostingowe](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porównanie wdrożenia klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Tworzenie klienta w funkcji zdalnych .NET  
 Gdy obiekt serwera funkcji zdalnych .NET została udostępniona, mogą być używane przez klientów, takie jak w poniższym przykładzie:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 Wystąpienie RemotingServer zwrócony z Activator.GetObject() nazywa się "przezroczystego obiektu pośredniczącego." Implementuje publiczny interfejs API dla typu RemotingServer na kliencie, ale wszystkie metody wywołania obiektu serwera uruchomione na inny proces lub komputera.  
  
#### <a name="creating-a-client-in-wcf"></a>Tworzenie klienta w programie WCF  
 Odpowiednik etapem WCF polega na użyciu fabryki kanałów można jawnie utworzyć serwer proxy. Podobnie jak Remoting obiekt serwera proxy może służyć do wywołania operacji na serwerze, podobnie jak w poniższym przykładzie:  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 Ten przykład przedstawia programowania na poziomie kanału, ponieważ jest najbardziej podobny do komunikacji zdalnej. Jest dostępna również **Dodaj odwołanie do usługi** podejście w programie Visual Studio, który generuje kod, aby uprościć klienta programowania. Więcej informacji znajduje się w następujących tematach:  
  
-   [Programowanie na poziomie kanału klienta](./extending/client-channel-level-programming.md)  
  
-   [Porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Użycie serializacji  
 Zarówno funkcji zdalnych .NET, jak i WCF umożliwia wysyłanie obiektów między klientem i serwerem serializacji, ale różnią się one w tych sposobów:  
  
1.  Różnych serializatorów i konwencje związane z nich służy do wskazywania co do serializacji.  
  
2.  Funkcji zdalnych .NET obsługuje serializacji "przez odwołanie", umożliwiająca dostęp do metody lub właściwości na jedną warstwę na wykonanie kodu na inne warstwy, która jest poza granicami zabezpieczeń. Ta funkcja udostępnia luk w zabezpieczeniach i jest jednym z głównych powodów dlaczego punktów końcowych usług zdalnych nigdy nie powinny zostać ujawnione klientom niezaufanych.  
  
3.  Wypisz jest używane przez usługi zdalne serializacji (jawnie wykluczyć jakie nie można serializować) i serializacja WCF jest opcjonalnych (Oznacz jawnie członków do serializacji).  
  
#### <a name="serialization-in-net-remoting"></a>Serializacja w funkcji zdalnych .NET  
 Funkcji zdalnych .NET obsługuje dwa sposoby serializacji i deserializacji obiektów między klientem i serwerem:  
  
-   *Według wartości* — wartości obiektu są serializowane w granicach warstwy, a nowe wystąpienie tego obiektu jest tworzony na innej warstwie. Wszystkie wywołania metody lub właściwości tego nowego wystąpienia wykonanie tylko lokalnie i nie wpływają na oryginalny obiekt lub warstwy.  
  
-   *Przez odwołanie* — specjalnego "odwołanie do obiektu" jest serializowany w granicach warstwy. Gdy jedną warstwę użyje metody lub właściwości tego obiektu, komunikuje się wstecz do oryginalnego obiektu na warstwie oryginalnej. Obiekty-reference może przepływać w obu kierunkach — od serwera do klienta lub od klienta do serwera.  
  
 Typy według wartości w zdalnych są oznaczone atrybutem [Serializable] lub zaimplementuj element ISerializable, podobnie jak w poniższym przykładzie:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Typów przez odwołanie pochodzi od klasy MarshalByRefObject, podobnie jak w poniższym przykładzie:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Jest bardzo ważne, aby zrozumienie wpływu na zdalnych obiektów przez odwołanie. Każda warstwa (klienta lub serwera) wysyła obiektu przez odwołania do innych warstwy, wszystkie wywołania metody wykonywania do warstwy będący właścicielem obiektu. Na przykład klient wywoływania metod dla obiekt przez odwołanie zwrócone przez serwer będzie wykonanie kodu na serwerze. Podobnie serwer wywoływania metod dla obiekt przez odwołanie dostarczonych przez klienta będzie wykonywał kodu ponownie na kliencie. Z tego powodu zaleca się korzystanie z funkcji zdalnych .NET tylko w pełni zaufanym środowisku. Udostępnianie publiczny punkt końcowy .NET Remoting do niezaufani Klienci spowoduje, że serwer usług zdalnych narażony na ataki.  
  
#### <a name="serialization-in-wcf"></a>Serializacja w programie WCF  
 Usługi WCF obsługuje tylko przez wartość serializacji. Najczęściej do zdefiniowania typu do wymiany między klientem a serwerem jest podobnie jak w poniższym przykładzie:  
  
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
  
 Atrybut [DataContract] określa tego typu jako jeden serializacji i deserializacji między klientem i serwerem. Atrybut [DataMember] określa poszczególne właściwości lub pola do serializacji.  
  
 Gdy WCF wysyła obiektu między warstwami, serializuje tylko wartości i tworzy nowe wystąpienie obiektu na innej warstwie. Wszystkie interakcje z wartościami obiektu występują tylko lokalnie — nie komunikują się z warstwą obiektów przez odwołanie funkcji zdalnych .NET, jak. Więcej informacji znajduje się w następujących tematach:  
  
-   [Serializacja i deserializacja](./feature-details/serialization-and-deserialization.md)  
  
-   [Serializacja programu Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a>Możliwości obsługi wyjątków  
  
#### <a name="exceptions-in-net-remoting"></a>Wyjątki w funkcji zdalnych .NET  
 Wyjątki generowane przez serwer usług zdalnych są serializowane, wysłane do klienta i generowany lokalnie na komputerze klienckim, podobnie jak inne wyjątek. Niestandardowymi wyjątkami mogą być tworzone przez podrzędna classing typ wyjątku i oznaczenie go [SERIALIZABLE].   Większość wyjątków framework już zostały oznaczone w ten sposób, dzięki czemu większość zostanie wygenerowany przez serwer serializowane i zgłoszony ponownie na kliencie. Chociaż ten projekt jest wygodne podczas tworzenia, informacje po stronie serwera może przypadkowo ujawniane do klienta. Jest to jedna z wielu powodów zdalnych należy używać tylko w pełni zaufanym środowisku.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Wyjątków i błędów w programie WCF  
 Usługi WCF nie zezwala na typy wyjątków dowolnego ma zostać zwrócona z serwera do klienta, ponieważ połączenie może prowadzić do przypadkowym ujawnieniem. Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, powoduje ogólnego przeznaczenia FaultException zostanie wygenerowany na kliencie. Tego wyjątku nie zawiera żadnych informacji, dlaczego gdzie wystąpił problem i dla niektórych aplikacji jest wystarczająca. Aplikacje, które muszą komunikować się bardziej rozbudowane informacje o błędzie, czy klient to definiując kontrakt błędu.  
  
 Aby to zrobić, należy najpierw utworzyć typu [DataContract] do przenoszenia informacje o błędzie.  
  
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
  
 Określ kontrakt błędu dla każdej operacji usługi.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Serwer raportów błędów przez zgłaszanie zgłoszenie wyjątku FaultException.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 I zawsze, gdy klient wysyła żądanie do serwera, może przechwycić błędy jako wyjątki normalnego.  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 Aby uzyskać więcej informacji na temat kontraktów błędów zobacz <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
  
#### <a name="security-in-net-remoting"></a>Zabezpieczenia w funkcji zdalnych .NET  
 Niektórych funkcji zdalnych .NET kanały obsługuje funkcje zabezpieczeń, takich jak uwierzytelnianie i szyfrowanie w warstwie kanału (IPC i TCP). Kanał HTTP polega na Internet Information Services (IIS) dla uwierzytelniania i szyfrowania. Pomimo ta obsługa należy wziąć pod uwagę .NET Remoting protokołu komunikacyjnego niezabezpieczone i używać go tylko w pełni zaufanym środowisku. Nigdy nie uwidacznia publiczny punkt końcowy usług zdalnych do Internetu lub niezaufanego klientów.  
  
#### <a name="security-in-wcf"></a>Zabezpieczenia w programie WCF  
 WCF został opracowany z zabezpieczeniami, pamiętając, w części adresu rodzaje luk w zabezpieczeniach w funkcji zdalnych .NET. Usługi WCF oferuje zabezpieczeń na poziomie komunikatu i transportu i oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej. Więcej informacji znajduje się w następujących tematach:  
  
-   [Zabezpieczenia](./feature-details/security.md)  
  
-   [Wskazówki dotyczące zabezpieczeń programu WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migracja do programu WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Dlaczego migrację z usług zdalnych WCF?  
  
-   **.NET remoting jest starszej wersji produktu.** Zgodnie z opisem w [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), jest uznawane za starszej wersji produktu i nie jest zalecane w przypadku nowych wdrożeń. Usługi WCF lub interfejsu API sieci Web platformy ASP.NET są zalecane w przypadku nowych i istniejących aplikacji.  
  
-   **Usługi WCF używa standardów i platform.** WCF została zaprojektowana współdziałanie między platformami pamiętać i obsługuje wiele standardy branżowe (SOAP, WS-Security WS-Trust, itp.). Usługi WCF może współdziałać z klientów z systemem innym niż Windows w systemach operacyjnych. Usług zdalnych został zaprojektowany głównie dla środowisk, w którym aplikacje klienta i serwera uruchamiane przy użyciu programu .NET framework w systemie operacyjnym Windows.  
  
-   **Usługi WCF ma wbudowane zabezpieczenia.** Usługi WCF została zaprojektowana z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania zabezpieczeń na poziomie transportu, zabezpieczeniami na poziomie wiadomości itp. Komunikację zdalną zaprojektowano tak, aby ułatwić aplikacji współdziałanie, ale nie został zaprojektowany do zabezpieczenia w środowiskach niezaufanej. Usługi WCF został zaprojektowany do pracy w środowiskach zaufanej i niezaufanej.  
  
### <a name="migration-recommendations"></a>Zalecenia dotyczące migracji  
 Poniżej przedstawiono zalecane kroki, aby przeprowadzić migrację z programu .NET Remoting do programu WCF:  
  
-   **Tworzenie kontraktu usługi.** Definiowanie typów interfejsu użytkownika usługi i oznacz je za pomocą atrybutu [ServiceContract]. Oznacz wszystkie metody, których klienci będą mogli wywołana za pomocą elementu [OperationContract].  
  
-   **Tworzenie kontraktu danych.** Definiowanie typów danych, które będą wymieniane między serwerem a klientem i oznacz je za pomocą atrybutu [DataContract]. Oznacz wszystkie pola i właściwości, które klient będzie mogła korzystać z [DataMember].  
  
-   **Utwórz kontrakt błędu (opcjonalnie).** Tworzenie typów, które będą wymieniane między serwerem a klientem, gdy wystąpią błędy. Oznacz te typy z [DataContract] i [DataMember], aby je do serializacji. Dla wszystkich operacji usługi, które oznaczona atrybutem [OperationContract] również oznacz je za pomocą [obiekcie FaultContract], aby wskazać, które zwracają może błędy.  
  
-   **Konfigurowanie i obsługi usługi.** Po utworzeniu kontraktu usługi, następnym krokiem jest skonfigurować powiązanie do udostępnienia usługi w punkcie końcowym. Aby uzyskać więcej informacji, zobacz [punkty końcowe: adresy, wiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Po aplikacji usług zdalnych przeprowadzono migrację do programu WCF, należy nadal usuń zależności funkcji zdalnych .NET. Dzięki temu, że żadnych luk Remoting zostaną usunięte z aplikacji. Kroki te obejmują następujące czynności:  
  
-   **Zaprzestanie stosowania programu MarshalByRefObject.** Typ elementu MarshalByRefObject istnieje tylko w przypadku usług zdalnych i nie jest używany przez usługę WCF. Wszystkie typy aplikacji, które częściowej klasy MarshalByRefObject zostaje usunięty lub zmieniony. Typ elementu MarshalByRefObject istnieje tylko w przypadku usług zdalnych i nie jest używany przez usługę WCF. Wszystkie typy aplikacji, które częściowej klasy MarshalByRefObject zostaje usunięty lub zmieniony.  
  
-   **Zaprzestanie stosowania [Serializable] i interfejs ISerializable.** Atrybut [Serializable] i interfejsu ISerializable pierwotnie zostały zaprojektowane do serializacji typów w środowiskach zaufanych i są one używane w komunikacji zdalnej. Serializacja WCF polega na typy są oznaczonej jako [DataContract] i [DataMember]. Typy danych używany przez aplikację powinno zostać zmodyfikowane, aby użyć [DataContract] i nie należy używać interfejs ISerializable lub [Serializable]. Atrybut [Serializable] i interfejsu ISerializable pierwotnie zostały zaprojektowane do serializacji typów w środowiskach zaufanych i są one używane w komunikacji zdalnej. Serializacja WCF polega na typy są oznaczonej jako [DataContract] i [DataMember]. Typy danych używany przez aplikację powinno zostać zmodyfikowane, aby użyć [DataContract] i nie należy używać interfejs ISerializable lub [Serializable].  
  
### <a name="migration-scenarios"></a>Scenariusze migracji  
 Teraz zobaczmy, jak wykonywać następujące typowe scenariusze komunikacji zdalnej programu WCF:  
  
1.  Serwer zwraca obiekt przez wartość do klienta  
  
2.  Serwer zwraca obiekt przez odwołanie do klienta  
  
3.  Klient wysyła obiektu przez wartość do serwera  
  
> [!NOTE]
>  Wysyłanie przez — odwołanie do obiektu z klienta do serwera w programie WCF jest niedozwolone.  
  
 Podczas odczytu za pomocą tych scenariuszy, przyjęto założenie, że naszych interfejsów linii bazowej dla funkcji zdalnych .NET wyglądać jak w następującym przykładzie. Implementacja funkcji zdalnych .NET nie jest ważna w tym miejscu ponieważ chcemy, aby zilustrować tylko używają WCF do zaimplementowania równoważne funkcje.  
  
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
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a>Scenariusz 1: Usługa zwraca obiekt przez wartość  
 W tym scenariuszu pokazano, serwer, zwracając obiekt do klienta przez wartość. WCF zawsze zwraca obiekty z serwera wg wartości, więc w poniższych krokach opisano tylko sposób tworzenia normalnej usługi WCF.  
  
1.  Rozpocznij od zdefiniowania publiczny interfejs dla usługi WCF i oznacz ją atrybutem [ServiceContract]. Używamy [OperationContract] do identyfikowania metod po stronie serwera, który wywoła naszych klientów.  
  
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
  
2.  Następnym krokiem jest tworzenie kontraktu danych dla tej usługi. Firma Microsoft to zrobić, tworząc klasy (nie interfejsy) oznaczonej przez atrybut [DataContract]. Indywidualne właściwości lub pola, które chcemy się widoczne dla klienta i serwera są oznaczone [DataMember]. Jeśli chcemy typy pochodne mogą być możemy Użyj atrybutu [KnownType] w celu ich identyfikacji. Tylko typy WCF umożliwi serializacji lub deserializacji dla tej usługi, są lokalizacje w interfejsie usługi i te "znane typy". Podjęto próbę wymiany innego typu spoza tej listy zostaną odrzucone.  
  
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
  
3.  Następnie firma Microsoft udostępnia implementację interfejsu usługi.  
  
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
  
4.  Aby uruchomić usługę WCF, należy zadeklarować punktu końcowego, który uwidacznia interfejs tej usługi pod określonym adresem URL używa określonego powiązania WCF. Jest to zazwyczaj wykonywane przez dodanie sekcje do pliku web.config Projekt serwera.  
  
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
  
5.  Następnie można uruchomić usługi WCF z następującym kodem:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Po uruchomieniu tego elementu ServiceHost używa pliku web.config ustanowienie właściwego kontraktu, powiązania i punktu końcowego. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [Konfigurowanie usług za pomocą plików konfiguracji](./configuring-services-using-configuration-files.md). Ten styl uruchamiania serwera jest określany jako hostingu samodzielnego. Aby dowiedzieć się więcej na temat inne opcje hostingu usług WCF, zobacz [Hosting usług](./hosting-services.md).  
  
6.  App.config projektu klienta należy zadeklarować pasujące informacje o powiązaniu dla punktu końcowego usługi. Najprostszym sposobem, aby to zrobić w programie Visual Studio jest użycie **Dodaj odwołanie do usługi**, które będą automatycznie zaktualizować pliku app.config. Alternatywnie te same zmiany mogą być dodawane ręcznie.  
  
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
  
     Aby uzyskać więcej informacji o korzystaniu z **Dodaj odwołanie do usługi**, zobacz [porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7.  Teraz można nazywamy usługi WCF z klienta. Firma Microsoft to zrobić przez tworzenie fabryki kanałów dla tej usługi, podanie kanału i bezpośrednio wywołać metodę, którą chcemy udostępnić w tym kanale. Firma Microsoft może to zrobić, ponieważ kanału implementuje interfejs usługi i obsługuje podstawowej logiki żądania/odpowiedzi firmie Microsoft. Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedzi serwera.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 Obiekty zwrócone przez usługi WCF z serwera do klienta są zawsze przez wartość. Obiekty są zdeserializowany kopie danych wysłanych przez serwer. Klienta można wywoływać metod tych kopiami lokalnymi bez zagrożenia wywoływania kod serwera za pośrednictwem wywołania zwrotne.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scenariusz 2: Serwer zwraca obiekt przez odwołanie  
 W tym scenariuszu pokazano serwera podajesz obiekt do klienta przez odwołanie. W funkcji zdalnych .NET, to odbywa się automatycznie dla dowolnego typu pochodnego od elementu MarshalByRefObject, która jest serializowany przez odwołanie. Przykładem tego scenariusza jest stosowanie wielu klientów niezależne obiekty zamykania po stronie serwera. Jak wcześniej wspomniano, obiekty zwrócone przez usługę WCF są zawsze wg wartości, więc ma bezpośredniego odpowiednika obiektu przez odwołanie, ale można osiągnąć podobny do przy użyciu semantyki przez odwołanie <xref:System.ServiceModel.EndpointAddress10> obiektu. Jest to obiekt możliwy do serializacji przez wartość używaną przez klienta można uzyskać obiektu sesyjnych przez odwołania na serwerze. Dzięki temu scenariusz o wielu klientów obiektami niezależne zamykania po stronie serwera.  
  
1.  Najpierw musimy definiowanie kontraktu usługi WCF, która odpowiada obiekt sesyjnych.  
  
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
    >  Zwróć uwagę, że sesyjnych obiekt jest oznaczony atrybutem [ServiceContract], dzięki czemu zwykłym usługi WCF interfejs. Ustawienie wartość właściwości SessionMode właściwość wskazuje, że będzie on zamykania usługi. W programie WCF sesja jest sposób korelacji wiele komunikatów przesyłanych między dwoma punktami końcowymi. Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesja zostanie nawiązane między klientem a serwerem. Klient będzie używać jednego wystąpienia unikatowy obiektu po stronie serwera dla wszystkich jego interakcji w tym jednej sesji.  
  
2.  Następnie należy udostępnić implementację tego interfejsu usługi. Określające, o [ServiceBehavior] i ustawiając właściwość InstanceContextMode, możemy stwierdzić WCF, chcemy użyć unikatowego wystąpienia tego typu dla każdej sesji.  
  
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
  
3.  Teraz potrzebujemy sposób uzyskanie wystąpienia obiektu sesyjnych. Firma Microsoft to zrobić, tworząc inny interfejs usługi WCF zwraca obiekt EndpointAddress10. Jest to format możliwy do serializacji elementu punktu końcowego, który klient może używać do tworzenia obiektu sesyjnych.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     I wdrożymy tę usługę WCF:  
  
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
  
     Ta implementacja obsługuje pojedyncze fabryki kanałów do tworzenia obiektów sesyjnych. Po wywołaniu GetInstanceAddress() tworzy kanału i tworzy obiekt EndpointAddress10 skutecznie wskazujące zdalny adres skojarzony z tym kanale. EndpointAddress10 jest po prostu typu danych, który może być zwracany do klienta przez wartość.  
  
4.  Należy zmodyfikować pliku konfiguracji serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:  
  
    1.  Deklarowanie \<klienta > sekcji, która opisuje punktu końcowego dla obiektu sesyjnych. Jest to konieczne, ponieważ serwer działa również jako klient w tej sytuacji.  
  
    2.  Deklarowanie punktów końcowych dla obiekt fabryki i sessionful. Jest to konieczne umożliwić klientom komunikowanie się z punktami końcowymi usługi, aby uzyskać EndpointAddress10 i utworzyć podczas zamykania kanału sesji.  
  
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
  
     A następnie można uruchomić następujące usługi:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  Firma Microsoft Konfigurowanie klienta przez zadeklarowanie tych samym punktów końcowych w pliku app.config jego projektu.  
  
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
  
6.  W celu tworzenia i używania tego obiektu zamykania, klienta należy wykonać następujące czynności:  
  
    1.  Tworzenie kanału do usługi ISessionBoundFactory.  
  
    2.  Użyj tego kanału do wywołania tej usługi, aby uzyskać EndpointAddress10.  
  
    3.  EndpointAddress10 umożliwia tworzenie kanału można uzyskać obiektu sesyjnych.  
  
    4.  Interakcje z obiektu sesyjnych wykazanie, że to samo wystąpienie pozostaje w wielu wywołań.  
  
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
  
 Usługi WCF zawsze zwraca obiekty według wartości, ale istnieje możliwość obsługi odpowiednikiem semantyki przez odwołanie za pośrednictwem EndpointAddress10. Umożliwia klientowi żądanie sesyjnych wystąpienie usługi WCF, po którym może współdziałać z nim podobnie jak inne usługi WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scenariusz 3: Klient wysyła serwera wystąpienia przez wartość  
 W tym scenariuszu pokazano klienta, wysyłanie wystąpienia obiektu innego niż pierwotny do serwera przez wartość. Ponieważ WCF wysyła tylko obiekty według wartości, w tym scenariuszu pokazano normalnego użycia WCF.  
  
1.  Użyj tej samej usługi WCF z scenariusz 1.  
  
2.  Aby utworzyć nowy obiekt przez wartość (klienta), tworzenie kanału do komunikacji z usługą ICustomerService i wysłać do niego obiekt, użyj klienta.  
  
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
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     Obiekt klienta będą serializowane i wysyłane na serwer, gdzie jest ona przeprowadzona deserializacja nową kopię tego obiektu.  
  
    > [!NOTE]
    >  Ten kod przedstawia również wysyłanie typu pochodnego (PremiumCustomer). Interfejs usługi oczekuje obiektu klienta, ale atrybutu [KnownType] do klasy odbiorcy wskazał PremiumCustomer również jest dozwolone. Usługi WCF nie powiedzie się próba serializacji lub deserializacji innego typu, za pośrednictwem tego interfejsu usługi.  
  
 Normalny WCF wymiany danych są przez wartość. Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych jest wykonywana tylko lokalnie — nie wywoła kodu na innej warstwie. Gdy jest możliwość osiągnięcia przypominać zwracanych obiektów przez odwołanie *z* serwera, nie jest możliwe dla klienta w celu przekazania obiektu przez odwołanie *do* serwera. Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć w programie WCF, za pomocą usługi duplex. Aby uzyskać więcej informacji, zobacz [usługi dwukierunkowe](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Podsumowanie  
 .NET remoting to platforma komunikacji przeznaczony do użycia tylko w pełni zaufanym środowisku. Starszy produkt i jest obsługiwana tylko w przypadku zgodności z poprzednimi wersjami. Nie można stosować do tworzenia nowej aplikacji. Z drugiej strony WCF została zaprojektowana z myślą o bezpieczeństwie i jest zalecany dla nowych i istniejących aplikacji. Firma Microsoft zaleca się, czy istniejące aplikacji usług zdalnych można migrować zamiast tego użyć WCF lub interfejsu API sieci Web platformy ASP.NET.