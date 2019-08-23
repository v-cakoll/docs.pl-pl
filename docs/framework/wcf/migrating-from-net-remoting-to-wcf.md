---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 71e26ddd93605b02031aecba280e382528378ba6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943036"
---
# <a name="migrating-from-net-remoting-to-wcf"></a>Migrowanie z programu .NET Remoting do programu WCF
W tym artykule opisano sposób migracji aplikacji, która używa usług komunikacji zdalnej .NET do korzystania z Windows Communication Foundation (WCF). Porównuje podobne koncepcje tych produktów, a następnie opisuje sposób wykonywania kilku typowych scenariuszy komunikacji zdalnej w programie WCF.  
  
 Komunikacja zdalna .NET to starszy produkt, który jest obsługiwany tylko w celu zapewnienia zgodności z poprzednimi wersjami. Nie jest on zabezpieczony w środowiskach z zaufaniem mieszanym, ponieważ nie może zachować oddzielnych poziomów zaufania między klientem i serwerem. Na przykład nigdy nie należy ujawniać punktu końcowego komunikacji zdalnej platformy .NET z Internetem lub niezaufanym klientom. Zalecamy Migrowanie istniejących aplikacji zdalnych do nowszych i bardziej bezpiecznych technologii. Jeśli projekt aplikacji używa tylko protokołu HTTP i jest RESTful, zalecamy ASP.NET Web API. Aby uzyskać więcej informacji, zobacz ASP.NET Web API. Jeśli aplikacja jest oparta na protokole SOAP lub wymaga protokołów innych niż http, takich jak TCP, zalecamy korzystanie z programu WCF.  

## <a name="comparing-net-remoting-to-wcf"></a>Porównanie komunikacji zdalnej .NET z usługą WCF  
 Ta sekcja zawiera porównanie podstawowych bloków konstrukcyjnych komunikacji zdalnej .NET z ich odpowiednikami WCF. Będziemy używać tych bloków konstrukcyjnych później, aby utworzyć niektóre typowe scenariusze serwera klienta w programie WCF. Poniższy wykres podsumowuje główne podobieństwa i różnice między usługami zdalnymi i WCF platformy .NET.  
  
||Wywołaniem funkcji zdalnych .NET|WCF|  
|-|-------------------|---------|  
|Typ serwera|MarshalByRefObject podklasy|Oznacz przy użyciu atrybutu [ServiceContract]|  
|Operacje usługi|Metody publiczne na serwerze typu|Oznacz przy użyciu atrybutu [OperationContract]|  
|Serializacja|ISerializable lub [Serializable]|DataContractSerializer lub XmlSerializer|  
|Obiekty zakończone|Według wartości lub według odwołania|Tylko według wartości|  
|Błędy/wyjątki|Dowolny wyjątek możliwy do serializacji|FaultContract\<TDetail>|  
|Obiekty serwera proxy klienta|Przezroczyste obiekty pośredniczące o jednoznacznie określonym typie są tworzone automatycznie z MarshalByRefObjects|Serwery proxy o jednoznacznie określonym typie są generowane na żądanie przy\<użyciu elementu ChannelFactory TChannel >|  
|Wymagana platforma|Zarówno klient, jak i serwer muszą korzystać z systemów operacyjnych Microsoft i .NET|Wiele platform|  
|Format wiadomości|Private|Standardy branżowe (SOAP, WS-* itp.)|  
  
### <a name="server-implementation-comparison"></a>Porównanie implementacji serwera  
  
#### <a name="creating-a-server-in-net-remoting"></a>Tworzenie serwera w usłudze komunikacja zdalna .NET  
 Typy serwerów komunikacji zdalnej platformy .NET muszą pochodzić od MarshalByRefObject i definiować metody, które klient może wywołać, tak jak w przypadku następujących:  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Publiczne metody tego typu serwera stają się kontraktem publicznym dostępnym dla klientów.  Nie ma rozdzielania między interfejsem publicznym serwera a jego implementacją — jeden typ obsługuje obie.  
  
 Po zdefiniowaniu typu serwera można go udostępnić klientom, tak jak w poniższym przykładzie:  
  
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
  
 Istnieje wiele sposobów zapewnienia, że typ komunikacji zdalnej jest dostępny jako serwer, w tym przy użyciu plików konfiguracyjnych. Jest to tylko jeden przykład.  
  
#### <a name="creating-a-server-in-wcf"></a>Tworzenie serwera w programie WCF  
 Odpowiedni krok w programie WCF obejmuje tworzenie dwóch typów — publicznego "kontraktu usług" i konkretnej implementacji. Pierwszy jest zadeklarowany jako interfejs oznaczony przy użyciu [ServiceContract]. Metody dostępne dla klientów są oznaczone atrybutem [OperationContract]:  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Implementacja serwera jest definiowana w oddzielnym konkretnym klasie, jak w poniższym przykładzie:  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 Po zdefiniowaniu tych typów serwer WCF można udostępnić klientom, jak w poniższym przykładzie:  
  
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
> Protokół TCP jest używany w obu przykładach, aby zachować je tak jak to możliwe. Zapoznaj się z tematami dotyczącymi scenariusza w dalszej części tego tematu, aby poznać przykłady użycia protokołu HTTP.  
  
 Istnieje wiele sposobów konfigurowania i hostowania usług WCF. Jest to tylko jeden przykład, znany jako "samodzielny". Więcej informacji znajduje się w następujących tematach:  
  
- [Instrukcje: Definiowanie kontraktu usługi](how-to-define-a-wcf-service-contract.md)  
  
- [Konfigurowanie usług za pomocą plików konfiguracji](configuring-services-using-configuration-files.md)  
  
- [Usługi hostingowe](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a>Porównanie implementacji klienta  
  
#### <a name="creating-a-client-in-net-remoting"></a>Tworzenie klienta w usłudze komunikacja zdalna .NET  
 Po udostępnieniu obiektu serwera komunikacji zdalnej platformy .NET może on być używany przez klientów, taki jak w poniższym przykładzie:  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 Wystąpienie RemotingServer zwróciło element aktywator. GetObject () jest znany jako "przezroczysty serwer proxy". Implementuje on publiczny interfejs API dla typu RemotingServer na kliencie, ale wszystkie metody wywołują obiekt serwera uruchomiony w innym procesie lub na maszynie.  
  
#### <a name="creating-a-client-in-wcf"></a>Tworzenie klienta w programie WCF  
 Odpowiedni krok w programie WCF polega na użyciu fabryki kanałów w celu jawnego utworzenia serwera proxy. Podobnie jak w przypadku komunikacji zdalnej, obiekt serwera proxy może służyć do wywoływania operacji na serwerze, jak w poniższym przykładzie:  
  
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
  
 W tym przykładzie przedstawiono Programowanie na poziomie kanału, ponieważ jest ono najbardziej podobne do przykładu komunikacji zdalnej. Dostępna jest również Metoda **Dodaj odwołanie do usługi** w programie Visual Studio, która generuje kod upraszczający programowanie klientów. Więcej informacji znajduje się w następujących tematach:  
  
- [Programowanie na poziomie kanału klienta](./extending/client-channel-level-programming.md)  
  
- [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania do usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a>Użycie serializacji  
 Zarówno komunikacja zdalna .NET, jak i WCF używają serializacji do przesyłania obiektów między klientem a serwerem, ale różnią się następującymi sposobami:  
  
1. Wykorzystują różne serializatory i konwencje w celu wskazania, co należy serializować.  
  
2. Komunikacja zdalna platformy .NET obsługuje serializację "przywoływane", który umożliwia dostęp do metody lub właściwości w jednej warstwie w celu wykonywania kodu w innej warstwie, która znajduje się w granicach zabezpieczeń. Ta funkcja udostępnia luki w zabezpieczeniach i jest jednym z głównych powodów, dla których punkty końcowe komunikacji zdalnej nigdy nie mają być ujawniane niezaufanym klientom.  
  
3. Serializacja używana przez funkcję komunikacji zdalnej jest niezależna (jawnie wyklucza to, co nie jest serializowane) i Serializacja WCF jest niezależna (jawnie Oznacz członków do serializacji).  
  
#### <a name="serialization-in-net-remoting"></a>Serializacja w komunikacji zdalnej .NET  
 Komunikacja zdalna platformy .NET obsługuje dwa sposoby serializacji i deserializacji obiektów między klientem a serwerem:  
  
- *Według wartości* — wartości obiektu są serializowane w granicach warstwy, a nowe wystąpienie tego obiektu jest tworzone w innej warstwie. Wszystkie wywołania metod lub właściwości tego nowego wystąpienia są wykonywane tylko lokalnie i nie wpływają na oryginalny obiekt lub warstwę.  
  
- *Według odwołania* — specjalne "odwołanie do obiektu" jest serializowane między granicami warstwy. Gdy jedna warstwa współdziała z metodami lub właściwościami tego obiektu, komunikuje się z powrotem do oryginalnego obiektu w oryginalnej warstwie. Obiekty przez odwołanie mogą przepływać w dowolnym kierunku — serwer do klienta lub z klientem do serwera.  
  
 Typy według wartości w ramach usług zdalnych są oznaczone atrybutem [Serializable] lub implementuje interfejs ISerializable, tak jak w poniższym przykładzie:  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Typy odwołań pochodnych pochodzą od klasy MarshalByRefObject, jak w poniższym przykładzie:  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 Niezwykle ważne jest, aby zrozumieć konsekwencje dotyczące obiektów odwołujących się do komunikacji zdalnej. Jeśli jedna z warstw (klienta lub serwera) wysyła obiekt przez odwołanie do innej warstwy, wszystkie wywołania metod są wykonywane z powrotem do warstwy będącej właścicielem obiektu. Na przykład wywoływanie metod przez klienta na obiektach przez odwołanie przez serwer spowoduje wykonanie kodu na serwerze. Podobnie serwer wywołujący metody dla obiektu przez odwołanie dostarczone przez klienta spowoduje wykonanie kodu z powrotem na kliencie. Z tego powodu zaleca się używanie komunikacji zdalnej platformy .NET tylko w środowiskach w pełni zaufanych. Ujawnienie publicznego punktu końcowego komunikacji zdalnej .NET do niezaufanych klientów spowoduje, że serwer komunikacji zdalnej będzie narażony na ataki.  
  
#### <a name="serialization-in-wcf"></a>Serializacja w programie WCF  
 WCF obsługuje tylko serializacji według wartości. Najbardziej typowym sposobem zdefiniowania typu do wymiany między klientem a serwerem jest jak w poniższym przykładzie:  
  
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
  
 Atrybut [DataContract] identyfikuje ten typ jako taki, który może być serializowany i deserializowany między klientem i serwerem. Atrybut [DataMember] identyfikuje poszczególne właściwości lub pola do serializacji.  
  
 Gdy WCF wysyła obiekt między warstwami, serializować tylko wartości i tworzy nowe wystąpienie obiektu na drugiej warstwie. Wszystkie interakcje z wartościami obiektu są wykonywane tylko lokalnie — nie komunikują się z drugą warstwą, tak jak obiekty referencyjne komunikacji zdalnej przez platformę .NET. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](./feature-details/serialization-and-deserialization.md).  
  
### <a name="exception-handling-capabilities"></a>Możliwości obsługi wyjątków  
  
#### <a name="exceptions-in-net-remoting"></a>Wyjątki w komunikacji zdalnej .NET  
 Wyjątki zgłoszone przez serwer usług zdalnych są serializowane, wysyłane do klienta i zgłaszane lokalnie na kliencie, podobnie jak każdy inny wyjątek. Wyjątki niestandardowe można utworzyć przez podklasę typu wyjątku i oznaczenie go przy użyciu [Serializable].   Większość wyjątków Framework została już oznaczona w ten sposób, co pozwala na to, aby większość zgłaszać serwerowi, serializować i ponownie wygenerowane na kliencie. Chociaż ten projekt jest wygodny podczas programowania, informacje po stronie serwera mogą zostać przypadkowo ujawnione dla klienta. Jest to jedna z wielu powodów, dla których komunikacja zdalna powinna być używana tylko w w pełni zaufanych środowiskach.  
  
#### <a name="exceptions-and-faults-in-wcf"></a>Wyjątki i błędy w programie WCF  
 Funkcja WCF nie zezwala na Zwracanie żadnych typów wyjątków z serwera do klienta, ponieważ może to prowadzić do przypadkowego ujawnienia informacji. Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, spowoduje to, że na kliencie zostanie zgłoszony błąd ogólnego przeznaczeniaexception. Ten wyjątek nie zawiera żadnych informacji o tym, dlaczego wystąpił problem, i w przypadku niektórych aplikacji, które są wystarczające. Aplikacje, które muszą przekazać bogatsze informacje o błędzie do klienta, można to zrobić, definiując umowę o błędzie.  
  
 W tym celu należy najpierw utworzyć typ [DataContract], aby przenieść informacje o błędzie.  
  
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
  
 Określ kontrakt błędu, który ma być używany dla każdej operacji usługi.  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 Serwer zgłasza warunki błędów, zgłaszając wyjątek FaultException.  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 Gdy klient wysyła żądanie do serwera, może przechwytywać błędy jako normalne wyjątki.  
  
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
  
 Aby uzyskać więcej informacji na temat umów dotyczących <xref:System.ServiceModel.FaultException>błędów, zobacz.  
  
### <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
  
#### <a name="security-in-net-remoting"></a>Zabezpieczenia w komunikacji zdalnej .NET  
 Niektóre kanały komunikacji zdalnej .NET obsługują funkcje zabezpieczeń, takie jak uwierzytelnianie i szyfrowanie, w warstwie kanału (IPC i TCP). Kanał HTTP opiera się na Internet Information Services (IIS) do uwierzytelniania i szyfrowania. Pomimo tego wsparcia należy rozważyć użycie przez program .NET zdalnej protokołu komunikacyjnego i używanie go tylko w środowiskach w pełni zaufanych. Nigdy nie ujawniaj publicznego punktu końcowego komunikacji zdalnej dla Internetu lub niezaufanych klientów.  
  
#### <a name="security-in-wcf"></a>Zabezpieczenia w programie WCF  
 Funkcja WCF została zaprojektowana z myślą o bezpieczeństwie, w części dotyczącej rodzaju luk w zabezpieczeniach platformy .NET. Usługa WCF oferuje zabezpieczenia zarówno na poziomie transportu, jak i komunikatów, a ponadto oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej. Więcej informacji znajduje się w następujących tematach:  
  
- [Zabezpieczenia](./feature-details/security.md)  
  
- [Wskazówki dotyczące zabezpieczeń programu WCF](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a>Migrowanie do programu WCF  
  
### <a name="why-migrate-from-remoting-to-wcf"></a>Dlaczego należy przeprowadzić migrację z usług zdalnych do WCF?  
  
- **Komunikacja zdalna .NET to starszy produkt.** Zgodnie z opisem w [komunikacji zdalnej .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), jest uznawany za starszy produkt i nie jest zalecany w przypadku nowych rozwiązań programistycznych. W przypadku nowych i istniejących aplikacji zaleca się używanie interfejsu API sieci Web WCF lub ASP.NET.  
  
- **Funkcja WCF stosuje standardy dla wielu platform.** Program WCF został zaprojektowany z myślą o współdziałaniu między platformami i obsługuje wiele standardów branżowych (SOAP, WS-Security, WS-Trust itp.). Usługa WCF może współpracować z klientami uruchomionymi w systemach operacyjnych innych niż Windows. Komunikacja zdalna została zaprojektowana głównie dla środowisk, w których zarówno serwer, jak i aplikacje klienckie działają przy użyciu programu .NET Framework w systemie operacyjnym Windows.  
  
- **Funkcja WCF ma wbudowane zabezpieczenia.** Funkcja WCF została zaprojektowana z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania, zabezpieczeń na poziomie transportu, zabezpieczeń na poziomie komunikatów itp. Komunikacja zdalna została zaprojektowana w celu ułatwienia współpracy aplikacji, ale nie została zaprojektowana w taki sposób, aby była zabezpieczona w środowiskach niezaufanych. Funkcja WCF została zaprojektowana tak, aby działała zarówno w środowiskach zaufanych, jak i niezaufanych.  
  
### <a name="migration-recommendations"></a>Zalecenia dotyczące migracji  
 Poniżej przedstawiono zalecane kroki migracji z komunikacji zdalnej platformy .NET do programu WCF:  
  
- **Utwórz kontrakt usługi.** Zdefiniuj typy interfejsów usługi i oznacz je atrybutem [ServiceContract]. Oznacz wszystkie metody, które będą mogły być wywoływane przez klientów [OperationContract].  
  
- **Utwórz kontrakt danych.** Zdefiniuj typy danych, które będą wymieniane między serwerem a klientem i oznacz je atrybutem [DataContract]. Oznacz wszystkie pola i właściwości, których klient będzie mógł używać z [DataMember].  
  
- **Utwórz kontrakt błędu (opcjonalnie).** Utwórz typy, które będą wymieniane między serwerem a klientem po napotkaniu błędów. Oznacz te typy elementami [DataContract] i [DataMember], aby je serializować. Dla wszystkich operacji usługi, które zostały oznaczone za pomocą elementu [OperationContract], należy również oznaczyć je jako [FaultContract], aby wskazać, które błędy mogą zostać zwrócone.  
  
- **Skonfigurowanie i Hostowanie usługi.** Po utworzeniu kontraktu usługi następnym krokiem jest skonfigurowanie powiązania, aby uwidocznić usługę w punkcie końcowym. Aby uzyskać więcej informacji, [Zobacz punkty końcowe: Adresy, powiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).  
  
 Po przeprowadzeniu migracji aplikacji zdalnej do programu WCF nadal trzeba usunąć zależności dotyczące komunikacji zdalnej platformy .NET. Dzięki temu wszystkie luki w zabezpieczeniach zdalnych zostaną usunięte z aplikacji. Następujące kroki obejmują:  
  
- **Zaprzestanie korzystania z MarshalByRefObject.** Typ MarshalByRefObject istnieje tylko w przypadku komunikacji zdalnej i nie jest używany przez WCF. Wszystkie typy aplikacji, które podklasy MarshalByRefObject należy usunąć lub zmienić.  
  
- **Zaprzestanie używania [Serializable] i ISerializable.** Atrybut [Serializable] i interfejs ISerializable zostały pierwotnie zaprojektowane do serializacji typów w zaufanych środowiskach i są używane przez funkcję komunikacji zdalnej. Serializacja WCF opiera się na typach oznaczonych za pomocą elementu [DataContract] i [DataMember]. Typy danych używane przez aplikację należy zmodyfikować tak, aby używały elementu [DataContract], a nie do użycia interfejsu ISerializable lub [Serializable].  
  
### <a name="migration-scenarios"></a>Scenariusze migracji  
 Teraz zobaczmy, jak wykonywać następujące typowe scenariusze komunikacji zdalnej w programie WCF:  
  
1. Serwer zwraca obiekt przez wartość do klienta  
  
2. Serwer zwraca obiekt przez odwołanie do klienta  
  
3. Klient wysyła obiekt według wartości do serwera  
  
> [!NOTE]
> Wysyłanie obiektu przez odwołanie z klienta do serwera nie jest dozwolone w programie WCF.  
  
 Podczas czytania w tych scenariuszach Załóżmy, że nasze interfejsy bazowe dla komunikacji zdalnej platformy .NET wyglądają jak w poniższym przykładzie. Implementacja komunikacji zdalnej platformy .NET nie jest ważna w tym miejscu, ponieważ chcemy zilustrować, jak używać programu WCF do implementowania równoważnej funkcjonalności.  
  
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
 W tym scenariuszu zademonstrowano serwer zwracający obiekt do klienta przez wartość. Program WCF zawsze zwraca obiekty z serwera według wartości, dlatego w następujących krokach opisano sposób tworzenia normalnej usługi WCF.  
  
1. Zacznij od zdefiniowania interfejsu publicznego dla usługi WCF i oznacz go atrybutem [ServiceContract]. Używamy [OperationContract], aby identyfikować metody po stronie serwera, które będą wywoływane przez klienta.  
  
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
  
2. Następnym krokiem jest utworzenie kontraktu danych dla tej usługi. W tym celu należy utworzyć klasy (nie interfejsy) oznaczone za pomocą atrybutu [DataContract]. Poszczególne właściwości lub pola, które mają być widoczne dla klienta i serwera, są oznaczone za pomocą [DataMember]. Jeśli chcemy, aby typy pochodne były dozwolone, należy użyć atrybutu [KnownType], aby je zidentyfikować. Jedyne typy WCF umożliwią serializacji lub deserializacji dla tej usługi są te w interfejsie usługi i tych "znanych typach". Próba wymiany dowolnego innego typu, którego nie ma na liście, zostanie odrzucona.  
  
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
  
3. Następnie udostępnimy implementację interfejsu usługi.  
  
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
  
4. Aby uruchomić usługę WCF, musimy zadeklarować punkt końcowy, który ujawnia ten interfejs usługi w określonym adresie URL przy użyciu określonego powiązania WCF. Zwykle jest to wykonywane przez dodanie poniższych sekcji do pliku Web. config projektu serwera.  
  
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
  
5. Następnie można uruchomić usługę WCF przy użyciu następującego kodu:  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     Po uruchomieniu tego elementu ServiceHost używa on pliku Web. config w celu ustanowienia właściwego kontraktu, powiązania i punktu końcowego. Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Konfigurowanie usług przy użyciu plików konfiguracji](./configuring-services-using-configuration-files.md). Ten styl uruchamiania serwera jest znany jako samohosting. Aby dowiedzieć się więcej o innych opcjach hostingu usług WCF, zobacz [usługi hostingu](./hosting-services.md).  
  
6. Plik App. config projektu klienta musi deklarować pasujące informacje o powiązaniu dla punktu końcowego usługi. Najprostszym sposobem wykonania tej czynności w programie Visual Studio jest użycie **Dodaj odwołanie do usługi**, która spowoduje automatyczne zaktualizowanie pliku App. config. Alternatywnie te same zmiany można dodać ręcznie.  
  
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
  
     Aby uzyskać więcej informacji okorzystaniu z [Dodaj odwołanie do usługi, zobacz How to: Dodaj, zaktualizuj lub usuń odwołanie](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)do usługi.  
  
7. Teraz możemy wywołać usługę WCF od klienta. Możemy to zrobić, tworząc fabrykę kanałów dla tej usługi, zwracając ją na kanał i bezpośrednio wywołując metodę, którą chcemy w tym kanale. Można to zrobić, ponieważ kanał implementuje interfejs usługi i obsługuje podstawową logikę żądania/odpowiedzi. Wartością zwracaną z tego wywołania metody jest deserializowana kopia odpowiedzi serwera.  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 Obiekty zwracane przez WCF z serwera do klienta są zawsze przez wartość. Obiekty są deserializowanymi kopiami danych wysyłanych przez serwer. Klient może wywoływać metody dla tych kopii lokalnych bez jakichkolwiek zagrożeń związanych z wywoływaniem kodu serwera za pomocą wywołań zwrotnych.  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a>Scenariusz 2: Serwer zwraca obiekt przez odwołanie  
 W tym scenariuszu pokazano serwer dostarczający obiekt do klienta przez odwołanie. W przypadku komunikacji zdalnej .NET jest to obsługiwane automatycznie dla dowolnego typu pochodnego od MarshalByRefObject, który jest serializowany przez odwołanie. Przykładem tego scenariusza jest umożliwienie wielu klientom niezależnych obiektów po stronie serwera. Jak wspomniano wcześniej, obiekty zwrócone przez usługę WCF są zawsze przez wartość, więc nie istnieje bezpośredni odpowiednik obiektu przez odwołanie, ale możliwe jest osiągnięcie czegoś podobnego do semantyki odniesienia przy użyciu <xref:System.ServiceModel.EndpointAddress10> obiektu. Jest to obiekt możliwy do serializacji przez wartość, który może być używany przez klienta w celu uzyskania na serwerze sesji na podstawie obiektu referencyjnego. Dzięki temu scenariusz ma wiele klientów z niezależnymi obiektami po stronie serwera.  
  
1. Najpierw należy zdefiniować kontrakt usługi WCF, który odpowiada obiektowi sesji.  
  
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
    >  Zwróć uwagę, że obiekt sesji jest oznaczony za pomocą elementu [ServiceContract], co sprawia, że jest to normalny interfejs usługi WCF. Ustawienie właściwości SessionMode wskazuje, że będzie ona usługą sesji. W programie WCF sesja jest sposobem skorelowania wielu wiadomości przesyłanych między dwoma punktami końcowymi. Oznacza to, że gdy klient uzyska połączenie z tą usługą, zostanie ustanowiona sesja między klientem a serwerem. Klient będzie używać jednego unikatowego wystąpienia obiektu po stronie serwera dla wszystkich jego interakcji w ramach jednej sesji.  
  
2. Następnie musimy wprowadzić implementację tego interfejsu usługi. Wskazując, że za pomocą [ServiceBehavior] i ustawiając właściwość InstanceContextmode, będziemy informować, że firma Microsoft chce użyć unikatowego wystąpienia tego typu dla każdej sesji.  
  
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
  
3. Teraz potrzebujemy metody uzyskania wystąpienia tego obiektu sesji. W tym celu należy utworzyć inny interfejs usługi WCF, który zwraca obiekt EndpointAddress10. Jest to możliwy do serializacji formularz punktu końcowego, którego może użyć klient do utworzenia obiektu sesji.  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     I implementujemy tę usługę WCF:  
  
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
  
     Ta implementacja obsługuje pojedyncze fabryki kanałów do tworzenia obiektów sesji. Gdy wywoływana jest GetInstanceAddress (), tworzy kanał i tworzy obiekt EndpointAddress10, który efektywnie wskazuje adres zdalny skojarzony z tym kanałem. EndpointAddress10 jest po prostu typem danych, który może być zwracany do klienta przez wartość.  
  
4. Musimy zmodyfikować plik konfiguracji serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:  
  
    1. Zadeklaruj sekcję > klienta opisującą punkt końcowy dla obiektu sesji. \< Jest to konieczne, ponieważ serwer działa również jako klient w takiej sytuacji.  
  
    2. Zadeklaruj punkty końcowe dla obiektu fabryki i sesji. Jest to konieczne, aby umożliwić klientowi komunikowanie się z punktami końcowymi usługi w celu uzyskania EndpointAddress10 i utworzenia kanału sesji.  
  
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
  
     A następnie możemy uruchomić następujące usługi:  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. Skonfigurujemy klienta, deklarując te same punkty końcowe w pliku App. config projektu.  
  
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
  
6. Aby można było utworzyć ten obiekt sesji i używać go, klient musi wykonać następujące czynności:  
  
    1. Utwórz kanał usługi ISessionBoundFactory.  
  
    2. Użyj tego kanału do wywołania tej usługi w celu uzyskania EndpointAddress10.  
  
    3. Użyj EndpointAddress10, aby utworzyć kanał, aby uzyskać obiekt sesji.  
  
    4. Pracuj z obiektem Session, aby pokazać, że pozostaje w tym samym wystąpieniu w wielu wywołaniach.  
  
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
  
 Funkcja WCF zawsze zwraca obiekty według wartości, ale istnieje możliwość obsługi równoważnej semantyki przez odwołanie za pomocą EndpointAddress10. Pozwala to klientowi na zażądanie wystąpienia usługi WCF, po którym może ona współistnieć z nim, podobnie jak w przypadku każdej innej usługi WCF.  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a>Scenariusz 3: Klient wysyła serwer a wystąpienie przez wartość  
 W tym scenariuszu przedstawiono klienta wysyłającego wystąpienie obiektu niepierwotnego do serwera przez wartość. Ponieważ WCF wysyła tylko obiekty według wartości, w tym scenariuszu pokazano normalne użycie programu WCF.  
  
1. Użyj tej samej usługi WCF w scenariuszu 1.  
  
2. Użyj klienta programu, aby utworzyć nowy obiekt według wartości (klienta), utworzyć kanał do komunikacji z usługą ICustomerService i wysłać do niego obiekt.  
  
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
  
     Obiekt klienta zostanie Zserializowany i wysłany do serwera, gdzie zostaje rozszeregowany do nowej kopii tego obiektu.  
  
    > [!NOTE]
    > Ten kod ilustruje również wysyłanie typu pochodnego (PremiumCustomer). Interfejs usługi oczekuje obiektu klienta, ale atrybut [KnownType] w klasie Customer wskazujący PremiumCustomer był również dozwolony. W przypadku programu WCF próba serializacji lub deserializacji dowolnego innego typu za poorednictwem tego interfejsu usługi jest niemożliwa.  
  
 Normalne wymianę danych WCF są według wartości. Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych jest wykonywane tylko lokalnie — nie wywoła kodu w drugiej warstwie. Chociaż możliwe jest osiągnięcie obiektów, takich jak obiekty referencyjne, zwracanych *z* serwera, nie jest możliwe, aby klient przeszedł obiekt przez odwołanie *do* serwera. Scenariusz, który wymaga konwersacji między klientem a serwerem można osiągnąć w programie WCF przy użyciu usługi dupleksowej. Aby uzyskać więcej informacji, zobacz [usługi dupleksowe](./feature-details/duplex-services.md).  
  
## <a name="summary"></a>Podsumowanie  
 Komunikacja zdalna .NET to struktura komunikacji przeznaczona do użycia tylko w środowiskach w pełni zaufanych. Jest to starszy produkt i jest obsługiwany tylko w celu zapewnienia zgodności z poprzednimi wersjami. Nie należy używać go do kompilowania nowych aplikacji. Z kolei platforma WCF została zaprojektowana z myślą o bezpieczeństwie i jest zalecana w przypadku nowych i istniejących aplikacji. Firma Microsoft zaleca, aby w zamian przeprowadzić migrację istniejących aplikacji zdalnych do korzystania z interfejsu API sieci Web WCF lub ASP.NET.
