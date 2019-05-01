---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: c6bc16e97a87461be7b2c4877777329a0005a497
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955236"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrowanie z programu .NET Remoting do programu WCF
W tym artykule opisano sposób migrowania aplikacji korzystającej z wywołaniem funkcji zdalnych .NET do użycia usług Windows Communication Foundation (WCF). Jego porównuje podobne pojęcia między tymi produktami, a następnie w tym artykule opisano sposób wykonywania kilku typowych scenariuszy komunikacji zdalnej programu WCF.  
  
 Wywołaniem funkcji zdalnych .NET jest starszy produkt, który jest obsługiwany tylko w przypadku zgodności z poprzednimi wersjami. Nie jest bezpieczny w środowiskach mieszanych zaufania, ponieważ nie można zachować, poziomy zaufania oddzielne między klientem i serwerem. Na przykład nigdy nie powinny ujawniać punkt końcowy wywołaniem funkcji zdalnych .NET do Internetu lub niezaufanego klientami. Firma Microsoft zaleca Remoting istniejące aplikacje można migrować do nowszych i bardziej bezpieczne technologii. Jeśli projekt aplikacji używa tylko protokołu HTTP i jest zgodne ze specyfikacją REST, firma Microsoft zaleca interfejsu API sieci Web platformy ASP.NET. Aby uzyskać więcej informacji zobacz interfejs API sieci Web platformy ASP.NET. Jeśli aplikacja jest oparta na SOAP lub wymaga protokołów innych niż Http, takich jak TCP, firma Microsoft zaleca WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porównywanie .NET Remoting do programu WCF  
 W tej sekcji przedstawiono porównanie podstawowych bloków konstrukcyjnych wywołaniem funkcji zdalnych .NET przy użyciu ich odpowiedników WCF. Firma Microsoft użyje tych bloków konstrukcyjnych później utworzyć kilka typowych scenariuszy, klient serwer programu WCF. Poniższy wykres zawiera podsumowanie głównych podobieństwa i różnice między wywołaniem funkcji zdalnych .NET i usługi WCF.  
  
||Wywołaniem funkcji zdalnych .NET|WCF|  
|-|-------------------|---------|  
|Typ serwera|Podklasy MarshalByRefObject|Oznacz za pomocą atrybutu [ServiceContract]|  
|Operacje usługi|Metody publiczne na typ serwera|Oznacz za pomocą atrybutu [elementu OperationContract]|  
|Serializacja|Typ iSerializable lub [Serializable]|DataContractSerializer, lub elementu XmlSerializer|  
|Obiekty przekazany|Przez wartość lub przez odwołanie|Przez wartość tylko|  
|Błędy/wyjątków|Każdy wyjątek, możliwy do serializacji|FaultContract\<TDetail>|  
|Obiekty serwera proxy klienta|Silnie typizowane przezroczystych obiektów proxy są tworzone automatycznie na podstawie MarshalByRefObjects|Silnie typizowane serwery proxy są generowane na żądanie przy użyciu elementu ChannelFactory\<TChannel >|  
|Platforma wymagane|Zarówno klient, jak i serwera, należy użyć OS firmy Microsoft i platformy .NET|Dla wielu platform|  
|Format komunikatu|Private|Standardy branżowe (protokołu SOAP, WS-*, itp.)|  
  
### <a name="server-implementation-comparison"></a>Porównanie wdrożenia serwera  
  
#### <a name="creating-a-server-in-net-remoting"></a>Tworzenie serwera w wywołaniem funkcji zdalnych .NET  
 Typy serwerów wywołaniem funkcji zdalnych .NET musi pochodzić od elementu MarshalByRefObject i definiowania metod, które klient może wywołać, jak pokazano poniżej:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Metody publiczne ten typ serwera stanie zamówienia publicznego dostępne dla klientów.  Brak oddzielenie interfejsu publicznego serwera i jego wdrożenie — jeden typ obsługuje obie.  
  
 Po zdefiniowaniu typ serwera może on dostępne dla klientów, jak pokazano w poniższym przykładzie:  
  
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
  
 Istnieje wiele sposobów, aby udostępnić typ usług zdalnych jako serwer, w tym za pomocą plików konfiguracji. Jest to tylko jeden przykład.  
  
#### <a name="creating-a-server-in-wcf"></a>Tworzenie serwera w programie WCF  
 Równoważne etapem WCF związane z utworzeniem dwa typy — publiczny "Umowa serwisowa" i wykonanie. Pierwszy jest zadeklarowany jako interfejs oznaczone atrybutem [ServiceContract]. Metody dostępne dla klientów są oznaczone za pomocą elementu [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementacja serwera jest zdefiniowana w osobnej klasy konkretnych, takich jak w poniższym przykładzie:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Po zdefiniowaniu typu serwera WCF mogą być udostępniane klientom, jak pokazano w poniższym przykładzie:  
  
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
>  TCP jest używany w obu przykładach, aby były jak najbardziej podobna. Zapoznaj się z przewodników scenariusza w dalszej części tego tematu, przykłady przy użyciu protokołu HTTP.  
  
 Istnieje wiele sposobów konfigurowania oraz obsługi usług WCF. Jest to tylko jeden przykład, znane jako "może być samodzielnie hostowane". Więcej informacji znajduje się w następujących tematach:  
  
- [Instrukcje: Definiowanie kontraktu usługi](how-to-define-a-wcf-service-contract.md)  
  
- [Konfigurowanie usług za pomocą plików konfiguracji](configuring-services-using-configuration-files.md)  
  
- [Usługi hostingowe](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porównanie wdrożenia klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Tworzenie klienta w wywołaniem funkcji zdalnych .NET  
 Gdy obiekt serwera wywołaniem funkcji zdalnych .NET został udostępniony, mogą być używane przez klientów, takie jak w poniższym przykładzie:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Wystąpienie RemotingServer zwróciło Activator.GetObject() jest nazywany "przezroczystym serwerem proxy." Implementuje publicznego interfejsu API dla typu RemotingServer na komputerze klienckim, ale wszystkie metody wywołania obiektu serwera uruchomionego w inny proces lub komputera.  
  
#### <a name="creating-a-client-in-wcf"></a>Tworzenie klienta programu WCF  
 Równoważne etapem WCF polega na tym, za pomocą fabryki kanałów, aby jawnie utworzyć serwer proxy. Podobnie jak obsługa zdalna obiekt serwera proxy może służyć do wywołania operacji na serwerze, podobnie jak w poniższym przykładzie:  
  
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
  
 Ten przykład przedstawia, programowanie na poziomie kanału, ponieważ jest najbardziej podobne do komunikacji zdalnej. Dostępne jest również **Dodaj odwołanie do usługi** podejście w programie Visual Studio generuje kod, aby uprościć programowanie klienta. Więcej informacji znajduje się w następujących tematach:  
  
- [Programowanie na poziomie kanału klienta](./extending/client-channel-level-programming.md)  
  
- [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Sposób użycia serializacji  
 Wywołaniem funkcji zdalnych .NET i usługi WCF umożliwia wysyłanie obiektów między klientem i serwerem serializacji, ale różnią się w tych ważnymi względami:  
  
1. Konwencje i różnych serializatory one służy do wskazywania, co do serializacji.  
  
2. Wywołaniem funkcji zdalnych .NET obsługuje serializacji "przez odwołanie", który umożliwia dostęp metody lub właściwości w jednej warstwy na wykonanie kodu na inne warstwy, która jest w granicach zabezpieczeń. Ta funkcja udostępnia luk w zabezpieczeniach i jest jednym z głównych powodów dlaczego punkty końcowe komunikacji zdalnej nigdy nie powinny zostać ujawnione klientom niezaufanych.  
  
3. Serializacja używana przez wywołaniem funkcji zdalnych uniezależnienia (jawnie wykluczone, jak nie można serializować) i WCF serializacji jest zoptymalizowany pod kątem (wyraźnie oznaczyć elementów członkowskich, które można serializować).  
  
#### <a name="serialization-in-net-remoting"></a>Serializacja w wywołaniem funkcji zdalnych .NET  
 Wywołaniem funkcji zdalnych .NET obsługuje dwie metody serializacji i deserializacji obiektów między klientem i serwerem:  
  
- *Według wartości* — wartości obiektu są serializowane w granicach warstwy i nowego wystąpienia tego obiektu jest tworzony w innej warstwie. Wszelkie wywołania metody lub właściwości tego nowego wystąpienia wykonanie tylko lokalnie i nie ma wpływu na oryginalny obiekt lub warstwy.  
  
- *Przez odwołanie* — specjalnego "odwołanie do obiektu" jest serializowane jako granice warstwy. Gdy jednej warstwy korzysta z metody lub właściwości tego obiektu, komunikuje się do oryginalnego obiektu, oryginalnym warstwy. Obiekty-reference może przepływać w dowolnym kierunku — od serwera do klienta lub od klienta do serwera.  
  
 Typy i wartości w komunikacji zdalnej są oznaczone atrybutem [Serializable] lub zaimplementować ISerializable, podobnie jak w poniższym przykładzie:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Typy niebędące odwołaniami pochodzi od klasy MarshalByRefObject, podobnie jak w poniższym przykładzie:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Jest to bardzo ważne umożliwić poznanie skutków obiektów przez odwołanie w komunikacji zdalnej. Jeśli każda warstwa (klienta lub serwera) wysyła obiekt przez odwołanie do innych warstwy, wszystkie wywołania metody wykonywania ponownie na warstwa będąca właścicielem obiektu. Na przykład klient, wywoływanie metod na obiekcie przez odwołanie, zwrócony przez serwer będzie wykonanie kodu na serwerze. Podobnie serwera, wywoływanie metod na obiekcie przez odwołanie, dostarczonych przez klienta będzie wykonywać kod ponownie na kliencie. Z tego powodu korzystanie z wywołaniem funkcji zdalnych .NET jest zalecane tylko w obrębie środowiska, w pełni zaufane. Udostępnianie publicznym punktem końcowym wywołaniem funkcji zdalnych .NET do niezaufani Klienci spowoduje, że serwer usług zdalnych narażony na ataki.  
  
#### <a name="serialization-in-wcf"></a>Serializacja w programie WCF  
 Usługi WCF obsługuje tylko przez wartość serializacji. Najbardziej typowym sposobem definiowania typu do wymiany między klientem a serwerem jest podobnie jak w poniższym przykładzie:  
  
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
  
 Atrybut [DataContract] określa tego typu jako jeden, który może być serializacji i deserializacji między klientem i serwerem. Atrybut [DataMember] identyfikuje poszczególne właściwości lub pól do serializacji.  
  
 Gdy WCF wysyła obiekt w warstwach, serializuje tylko wartości i tworzy nowe wystąpienie obiektu w innej warstwie. Wszystkie interakcje z wartościami obiektu występują tylko lokalnie — nie komunikują się z warstwą zrobić obiektów przez odwołanie wywołaniem funkcji zdalnych .NET. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Możliwości obsługi wyjątków  
  
#### <a name="exceptions-in-net-remoting"></a>Wyjątki w wywołaniem funkcji zdalnych .NET  
 Wyjątki zgłaszane przez serwer usług zdalnych są serializowane, wysłane do klienta, a następnie generowany lokalnie na komputerze klienckim, podobnie jak inne wyjątek. Niestandardowe wyjątki mogą być tworzone przez podrzędnych classing typ wyjątku i oznaczenie go przy użyciu [Serializable].   Większość wyjątków framework są już oznaczone w ten sposób, dzięki czemu większość zostanie wygenerowany przez serwer, serializowany i zgłoszony ponownie na kliencie. Chociaż ten projekt jest wygodne podczas tworzenia aplikacji, informacji po stronie serwera może przypadkowo ujawnione klienta. Jest to jedna z wielu powodów, które wywołaniem funkcji zdalnych należy używać tylko w pełni zaufanym środowisku.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Wyjątki i błędy w programie WCF  
 Usługi WCF nie zezwala na typy dowolnego wyjątków, które mają być zwracane przez serwer do klienta, ponieważ mogłoby doprowadzić do ujawnienia informacji przypadkowego. Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, powoduje ogólnego przeznaczenia FaultException — zostanie wygenerowany na komputerze klienckim. Dlaczego lub którym wystąpił problem, i dla niektórych aplikacji jest to wystarczające tego wyjątku nie zawiera żadnych informacji. Aplikacje, które muszą komunikować się bogatsze informacje o błędzie do zrobienia klienta to definiując kontrakt błędu.  
  
 Aby to zrobić, należy najpierw utworzyć typ [DataContract], żeby informacje o błędzie.  
  
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
  
 Serwer raportów warunki błędów, zgłaszając FaultException —.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 I zawsze wtedy, gdy klient wysyła żądanie do serwera, może to przechwycić błędy jako wyjątki normalny.  
  
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
  
 Aby uzyskać więcej informacji na temat umów błędów, zobacz <xref:System.ServiceModel.FaultException>.  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
  
#### <a name="security-in-net-remoting"></a>Zabezpieczenia w wywołaniem funkcji zdalnych .NET  
 Niektórych kanałów wywołaniem funkcji zdalnych .NET obsługuje funkcje zabezpieczeń, takie jak uwierzytelnianie i szyfrowanie w warstwie kanału (IPC i TCP). Kanał HTTP opiera się na Internet Information Services (IIS) dla uwierzytelniania i szyfrowania. Pomimo tej obsługi możesz należy wziąć pod uwagę wywołaniem funkcji zdalnych .NET protokołu komunikacyjnego niebezpieczne i używać go tylko w obrębie środowiska, w pełni zaufane. Nigdy nie ujawniają publicznym punktem końcowym komunikacji zdalnej do Internetu lub niezaufanego klientów.  
  
#### <a name="security-in-wcf"></a>Zabezpieczenia w programie WCF  
 Usługi WCF został opracowany z myślą o bezpieczeństwie, w części adresu rodzaje luk w zabezpieczeniach w wywołaniem funkcji zdalnych .NET. Usługi WCF oferuje zabezpieczenia na poziomie transportu i komunikat i oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej. Więcej informacji znajduje się w następujących tematach:  
  
- [Zabezpieczenia](./feature-details/security.md)  
  
- [Wskazówki dotyczące zabezpieczeń programu WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrowanie do programu WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Dlaczego warto przeprowadzić migrację z Remoting do programu WCF?  
  
- **Wywołaniem funkcji zdalnych .NET jest starszy produkt.** Zgodnie z opisem w [wywołaniem funkcji zdalnych .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), są traktowane jako starszy produkt i nie jest zalecane w przypadku nowych wdrożeń. Usługi WCF lub Web API platformy ASP.NET są zalecane w przypadku nowych i istniejących aplikacji.  
  
- **Usługi WCF używa standardów dla wielu platform.** Program WCF zaprojektowano pod kątem współdziałania dla wielu platform, należy pamiętać i obsługuje wiele standardów branżowych (protokołu SOAP, WS-Security WS-Trust, itp.). Usługa WCF może współpracować z klientami, działających w systemach operacyjnych innych niż Windows. Komunikacja zdalna została zaprojektowana głównie dla środowisk, w którym serwer i klient aplikacje są uruchamiane przy użyciu programu .NET framework w systemie operacyjnym Windows.  
  
- **Usługi WCF ma wbudowane zabezpieczenia.** Usługi WCF została zaprojektowana z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania, zabezpieczenia na poziomie transportu, zabezpieczenia na poziomie komunikatu itp. Komunikacja zdalna zaprojektowano tak, aby ułatwić aplikacji pod kątem współdziałania, ale nie był projektowany do zabezpieczenia w środowiskach innych niż zaufane. Usługi WCF był projektowany do pracy w środowiskach zaufanej i niezaufanej.  
  
### <a name="migration-recommendations"></a>Zalecenia dotyczące migracji  
 Poniżej przedstawiono zalecane kroki, aby migrować z programu .NET Remoting do programu WCF:  
  
- **Tworzenie kontraktu usługi.** Definiowanie typów interfejsu użytkownika usługi i oznacz je za pomocą atrybutu [ServiceContract]. Oznacz wszystkie metody, których klienci będą mogły wywołać za pomocą elementu [OperationContract].  
  
- **Tworzenie kontraktu danych.** Definiowanie typów danych, które będą wymieniane między serwerem a klientem i oznacz je za pomocą atrybutu [DataContract]. Oznacz wszystkie pola i właściwości klienta zostaną dozwolone za pomocą [DataMember].  
  
- **Utworzyć kontrakt błędu (opcjonalnie).** Tworzenie typów, które będą wymieniane między serwerem a klientem, gdy wystąpią błędy. Należy oznaczyć te typy z [DataContract] i [DataMember] były możliwe do serializacji. Dla wszystkich operacji usługi, które zostały oznaczone za pomocą elementu [OperationContract] również oznacz je za pomocą [FaultContract] do sygnalizowania błędów, które zwracają może.  
  
- **Skonfiguruj i obsługi usługi.** Po utworzeniu kontraktu usługi, następnym krokiem jest skonfigurować powiązanie, aby udostępnić usługę w punkcie końcowym. Aby uzyskać więcej informacji, zobacz [punktów końcowych: Adresy, powiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Po migracji aplikacji usług zdalnych do programu WCF jest nadal ważne usunąć zależności między wywołaniem funkcji zdalnych .NET. Daje to gwarancję, że wszystkie luki w zabezpieczeniach z wywołaniem funkcji zdalnych są usuwane z aplikacji. Kroki te obejmują następujące czynności:  
  
- **Przestać korzystać ze MarshalByRefObject.** Typ elementu MarshalByRefObject istnieje tylko dla niego komunikację zdalną i nie jest używany przez architekturę WCF. Wszystkie typy aplikacji, które podrzędnych klasy MarshalByRefObject powinny być usunięte lub zmienione.  
  
- **Zaprzestanie użytkowania [Serializable] i interfejs ISerializable.** Atrybut [Serializable] i interfejs ISerializable zostały pierwotnie zaprojektowane do serializacji typów w środowiskach zaufanych i są one używane przez komunikację zdalną. Serializacja WCF opiera się na typy, które są oznaczone [DataContract] i [DataMember]. Powinien być modyfikowany typów danych używanych przez aplikację, aby użyć [DataContract] i nie należy używać interfejsu ISerializable lub [Serializable].  
  
### <a name="migration-scenarios"></a>Scenariusze migracji  
 Teraz zobaczmy, jak wykonywać następujące typowe scenariusze komunikacji zdalnej programu WCF:  
  
1. Serwer zwraca obiekt przez wartość do klienta  
  
2. Serwer zwraca obiekt przez odwołanie do klienta  
  
3. Klient wysyła obiekt przez wartość do serwera  
  
> [!NOTE]
>  Wysyłanie przez — odwołanie do obiektu z klienta do serwera w programie WCF jest niedozwolone.  
  
 Podczas odczytywania za pośrednictwem tych scenariuszy, zakłada się, że nasze interfejsy punktu odniesienia dla wywołaniem funkcji zdalnych .NET wyglądać jak w poniższym przykładzie. Implementacja wywołaniem funkcji zdalnych .NET nie jest ważna w tym miejscu, ponieważ chcemy zilustrować, lecz jak używać usługi WCF do zaimplementowania równoważne funkcje.  
  
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
 Ten scenariusz pokazuje serwera zwrócenie obiektu, do klienta przez wartość. Usługi WCF zawsze zwraca obiekty z serwera według wartości, więc w poniższych krokach opisano tylko sposób budowania normalne usługi WCF.  
  
1. Rozpocznij od zdefiniowania interfejsu publicznego dla usługi WCF i oznacz ją atrybutem [ServiceContract]. [Elementu OperationContract] są używane do identyfikowania metod po stronie serwera, który wywoła naszych klientów.  
  
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
  
2. Następnym krokiem jest tworzenie kontraktu danych dla tej usługi. Możemy to zrobić przez utworzenie klas (nie interfejsy) oznaczona przez atrybut [DataContract]. Indywidualne właściwości lub pola, które chcemy, aby widoczne dla klienta i serwera są oznaczone [DataMember]. Jeśli chcemy, aby typy pochodne, które mają być dozwolone, będziemy Użyj atrybutu [element KnownType] umożliwiający ich zidentyfikowanie. Jedyne typy WCF pozwoli serializowany lub deserializowany dla tej usługi są w interfejsie usługi i te "znane typy". Podjęto próbę wymiany innego typu, nie ma na tej liście będą odrzucane.  
  
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
  
3. Następnie firma Microsoft oferuje implementację interfejsu usługi.  
  
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
  
4. Aby uruchomić usługę WCF, należy zadeklarować punktu końcowego uwidocznionego interfejsu usług pod określonym adresem URL używa określonego powiązania WCF. Zazwyczaj jest to wykonywane, dodając poniższe sekcje w pliku web.config projektu serwera.  
  
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
  
5. Następnie można uruchomić usługi WCF z następującym kodem:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Po uruchomieniu tego elementu ServiceHost, używa pliku web.config można ustanowić prawidłowego kontraktu, powiązania i punktu końcowego. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie usług za pomocą plików konfiguracji](./configuring-services-using-configuration-files.md). Uruchamianie serwera ten styl jest określany jako hostingu samodzielnego. Aby dowiedzieć się więcej na temat innych opcji do hostowania usług WCF, zobacz [usług obsługującego](./hosting-services.md).  
  
6. Projekt klienta w pliku app.config, należy zadeklarować pasujące informacje o powiązaniu dla punktu końcowego usługi. Najprostszym sposobem, aby to zrobić w programie Visual Studio jest użycie **Dodaj odwołanie do usługi**, który automatycznie aktualizuje plik app.config. Te same zmiany można również dodać ręcznie.  
  
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
  
     Aby uzyskać więcej informacji o korzystaniu z **Dodaj odwołanie do usługi**, zobacz [jak: Dodawanie, aktualizowanie lub usuwanie odwołań usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).  
  
7. Teraz możemy wywołać usługi WCF z klienta. Możemy to zrobić, tworząc fabryki kanałów dla tej usługi, o kanału i bezpośrednio wywołać metodę, którą chcemy, aby w tym kanale. Możemy to zrobić, ponieważ implementuje interfejs usługi w kanale i obsługuje podstawowej logiki żądanie/nietypizowana odpowiedź dla nas. Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedź serwera.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Obiekty zwrócone przez architekturę WCF z serwera do klienta są zawsze przez wartość. Obiekty są zdeserializowany kopie danych wysłanych przez serwer. Klient może wywoływać metody te kopiami lokalnymi bez zagrożenia wywoływania kod serwera za pomocą wywołania zwrotne.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scenariusz 2: Serwer zwraca obiekt przez odwołanie  
 Ten scenariusz pokazuje serwera, podając obiekt do klienta przez odwołanie. W wywołaniem funkcji zdalnych .NET, to odbywa się automatycznie dla wszystkich typów pochodnych MarshalByRefObject, który jest serializowany przez odwołanie. Przykładem tego scenariusza jest zezwolenie klientom wiele niezależnych sesji obiektów po stronie serwera. Jak wcześniej wspomniano, obiekty zwrócone przez usługę WCF zawsze według wartości, więc ma bezpośredniego odpowiednika obiektu przez odwołanie, ale można osiągnąć podobny do przy użyciu semantyki przez odwołanie <xref:System.ServiceModel.EndpointAddress10> obiektu. Jest to obiekt możliwy do serializacji według wartości, który może służyć przez klienta do uzyskiwania obiektu sesji przez odwołanie, na serwerze. Dzięki temu scenariusz posiadanie wielu klientów obiektami niezależnie od sesji po stronie serwera.  
  
1. Najpierw musimy definiowanie kontraktu usługi WCF, która odnosi się do samego obiektu sesji.  
  
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
    >  Zwróć uwagę, że obiekt sesji jest oznaczona atrybutem [ServiceContract], dzięki czemu normalne interfejsu usługi WCF. Ustawienie SessionMode właściwość wskazuje, że będzie on sesji usługi. W programie WCF sesja jest sposób korelacji wielu komunikatów przesyłanych między dwoma punktami końcowymi. Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesji zostanie nawiązane między klientem a serwerem. Klient użyje jednego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach tej jednej sesji.  
  
2. Następnie należy udostępnić implementację tego interfejsu usługi. Oznaczającą, za pomocą [ServiceBehavior] i ustawiając właściwość InstanceContextMode, o WCF że chcemy użyć unikatowego wystąpienia tego typu dla każdej sesji.  
  
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
  
3. Teraz musimy sposobem uzyskania wystąpienie tego obiektu sesji. Możemy to zrobić, tworząc inny interfejs usługi WCF, która zwraca obiekt EndpointAddress10. Jest to format możliwy do serializacji punktu końcowego, który klient może używać do utworzenia obiektu sesji.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     I firma Microsoft zaimplementowania tej usługi WCF:  
  
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
  
     Ta implementacja obsługuje pojedyncze fabryki kanałów, aby utworzyć obiekty sesji. Po wywołaniu GetInstanceAddress() tworzy kanał i tworzy obiekt EndpointAddress10 skutecznie wskazujący zdalny adres skojarzony z tym kanałem. EndpointAddress10 jest po prostu typu danych, które mogą być zwrócone do klienta przez wartość.  
  
4. Należy zmodyfikować plik konfiguracji serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:  
  
    1. Zadeklaruj \<klienta > sekcji, która opisuje punktu końcowego dla obiektu sesji. Jest to konieczne, ponieważ serwer działa również jako klient w tej sytuacji.  
  
    2. Zadeklaruj punktów końcowych dla obiektu ustawień fabrycznych i sessionful. Jest to konieczne umożliwić klientowi komunikowanie się z punktami końcowymi usługi do uzyskania EndpointAddress10 i tworzenia kanału sesji.  
  
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
  
     A następnie Zaczniemy tych usług:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Możemy skonfigurować klienta przez zadeklarowanie te tymi samymi punktami końcowymi w pliku app.config jego projektu.  
  
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
  
6. Aby można było utworzyć i używać tego obiektu sesji, klient musi wykonaj następujące czynności:  
  
    1. Utwórz kanał w usłudze ISessionBoundFactory.  
  
    2. Do wywołania tej usługi w celu uzyskania EndpointAddress10 przy użyciu tego kanału.  
  
    3. Próba utworzenia kanału do uzyskiwania obiektu sesji, należy użyć EndpointAddress10.  
  
    4. Wchodzić w interakcje z obiektem sesji wykazanie, że będzie tego samego wystąpienia w wielu wywołań.  
  
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
  
 Usługi WCF zawsze zwraca obiekty według wartości, ale istnieje możliwość obsługi wielokrotność semantyki przez odwołanie za pomocą EndpointAddress10. Umożliwia klientowi żądanie sesji wystąpienie usługi WCF, po upływie którego go mogą wchodzić w interakcje z nią podobnie jak inne usługi WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scenariusz 3: Klient wysyła serwer wystąpienie przez wartość  
 Ten scenariusz pokazuje klienta wysyłania wystąpienia obiektu niepodstawowe do serwera przez wartość. Ponieważ WCF wysyła tylko obiektów według wartości, w tym scenariuszu pokazano normalnego użycia usługi WCF.  
  
1. Użyj tej samej usługi WCF z scenariusz 1.  
  
2. Aby utworzyć nowy obiekt przez wartość (klienta), utworzenia kanału do komunikacji z usługą ICustomerService i wysyłać obiekt, korzystając z klienta.  
  
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
  
     Obiekt klienta będą serializowane i wysyłane do serwera, gdzie jest ona przeprowadzona deserializacja nową kopię tego obiektu.  
  
    > [!NOTE]
    >  Ten kod ilustruje także wysyłanie typu pochodnego (PremiumCustomer). Interfejs usługi oczekuje obiektu klienta, ale atrybut [element KnownType] w klasie klienta wskazał PremiumCustomer również był dozwolony. Usługi WCF zakończy się niepowodzeniem próby serializacji lub deserializacji dowolny inny typ za pomocą tego interfejsu usługi.  
  
 Normalny WCF wymiany danych są według wartości. Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych wykonuje tylko lokalnie — nie wywoła kodu w innej warstwie. Choć jest możliwe osiągnąć podobny zwracanych obiektów przez odwołanie *z* server, nie jest możliwe dla klienta do przekazania obiektu przez odwołanie *do* serwera. Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć programu WCF za pomocą usługi duplex. Aby uzyskać więcej informacji, zobacz [usługi dwukierunkowe](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Podsumowanie  
 Wywołaniem funkcji zdalnych .NET to platforma komunikacji, może być używany tylko w obrębie środowiska, w pełni zaufane. Jest starszy produkt i obsługiwany tylko w przypadku zgodności z poprzednimi wersjami. Nie można stosować do tworzenia nowych aplikacji. Z drugiej strony WCF została zaprojektowana z myślą o bezpieczeństwie i jest zalecane w przypadku nowych i istniejących aplikacji. Firma Microsoft zaleca, aby istniejący aplikacji usług zdalnych można migrować zamiast tego użyć WCF lub Web API platformy ASP.NET.
