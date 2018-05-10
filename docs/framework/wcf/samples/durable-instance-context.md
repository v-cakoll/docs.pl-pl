---
title: Kontekst niezawodnej instancji
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: fb331fc0e5f384f0ffb268c1c6f7a5ffc99478ec
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="durable-instance-context"></a>Kontekst niezawodnej instancji
W tym przykładzie pokazano, jak dostosować włączyć kontekst niezawodnej instancji środowiska uruchomieniowego systemu Windows Communication Foundation (WCF). SQL Server 2005 używa jako magazynu zapasowego, jego (SQL Server 2005 Express w tym przypadku). Jednak umożliwia także sposób uzyskać dostępu do magazynu niestandardowych mechanizmów.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład obejmuje zarówno warstwie kanału, jak i warstwy modelu usług WCF. W związku z tym należy zrozumieć podstawowe pojęcia przed przejściem do szczegóły implementacji.  
  
 Konteksty wystąpienia trwałych znajduje się w rzeczywistych scenariuszach bardzo często. Na przykład aplikację koszyka zakupów ma możliwość wstrzymać zakupy w połowie za pośrednictwem i kontynuować go innym dnia. Tak, aby po firma Microsoft odwiedź koszyka następnego dnia, naszych oryginalnego kontekst został przywrócony. Należy pamiętać, że aplikacja koszyka zakupów (na serwerze) nie przechowuje wystąpienie koszyka zakupów odłączeniu możemy są. Zamiast tego utrwala swój stan na trwałe nośników i używa go podczas tworzenia nowego wystąpienia dla kontekstu przywrócone. W związku z tym wystąpienie usługi, która może obsłużyć tego samego kontekstu nie jest taka sama jak poprzedniego wystąpienia (to znaczy, że nie ma ten sam adres pamięci).  
  
 Kontekst niezawodnej instancji jest możliwe przez małe protokół, który wymienia identyfikator kontekstu między klientem a usługą. Ten identyfikator kontekstu jest tworzony na kliencie i przesyłane do usługi. Po utworzeniu wystąpienia usługi, czas wykonywania usługi próbuje załadować stan utrwalony odpowiadający ten identyfikator kontekstu z magazynu trwałego (domyślnie jest bazą danych programu SQL Server 2005). Jeśli stan nie jest dostępny nowe wystąpienie ma stanu domyślnego. Implementacji usługi używa atrybutu niestandardowego, aby oznaczyć działania, zmienić stan wdrożenia usługi, dzięki czemu środowiska uruchomieniowego można zapisać wystąpienia usługi po wywołaniu ich.  
  
 W opisie poprzednich aby osiągnąć łatwo można rozróżnić dwa kroki:  
  
1.  Zmień komunikat, który przechodzi umieszczonego do przenoszenia identyfikatora kontekstu.  
  
2.  Zmień zachowanie lokalnej usługi do zaimplementowania niestandardowej logiki wystąpień.  
  
 Ponieważ pierwsza z nich na liście dotyczy wiadomości przesyłania powinny zostać wdrożone jako niestandardowy kanał i można podłączyć do warstwy kanału. Drugie wpływa tylko na zachowanie lokalnej usługi i może być implementowana przez rozszerzenie kilka punktów rozszerzalności usługi. W kolejnych sekcjach kilka omówiono każdego z tych rozszerzeń.  
  
## <a name="durable-instancecontext-channel"></a>Niezawodny kanał InstanceContext  
 Przede wszystkim należy przyjrzeć się to rozszerzenie warstwy kanału. Pierwszą czynnością przy tworzeniu niestandardowym kanale jest podjęcie decyzji, struktura komunikacji kanału. Ponieważ wprowadzono nowy Protokół kanału powinien współpracować z prawie każdego innego kanału w stosie kanału. W związku z tym go powinien obsługiwać wszystkie wzorce wymiany wiadomości. Jednak do podstawowych funkcji kanał jest taki sam, niezależnie od jego struktury komunikacji. W szczególności od klienta go zapisać identyfikator kontekstu w wiadomości i z usługi należy przeczytać ten identyfikator kontekstu z wiadomości i przekaż go do wyższe poziomy. Z tego powodu `DurableInstanceContextChannelBase` utworzyć działającego jako abstrakcyjna klasa podstawowa dla wszystkich implementacji kanału kontekst niezawodnej instancji klasy. Ta klasa zawiera typowe funkcje zarządzania maszyny stanu i dwa chronionych elementów członkowskich, aby zastosować i przeczytaj informacje o kontekście do i z wiadomości.  
  
```  
class DurableInstanceContextChannelBase  
{  
  //…  
  protected void ApplyContext(Message message)  
  {  
    //…              
  }  
  protected string ReadContextId(Message message)  
  {  
    //…              
  }  
}  
```  
  
 Te dwie metody należy korzystać z `IContextManager` implementacje do zapisu i odczytu identyfikator kontekstu do lub z komunikatu. (`IContextManager` jest niestandardowy interfejs używany do definiowania kontrakt dla wszystkich menedżerów kontekstu.) Kanał można dołączyć identyfikator kontekstu niestandardowego nagłówka SOAP lub nagłówka pliku cookie HTTP. Każda implementacja menedżera kontekstu dziedziczy `ContextManagerBase` klasy, która zawiera typowe funkcje menedżerom kontekstu. `GetContextId` Metoda ta klasa służy do pochodzą z Identyfikatorem kontekstu z klienta. Jeśli kontekst, w których identyfikator jest pochodzi po raz pierwszy, ta metoda zapisuje do pliku tekstowego, którego nazwa jest tworzony za pomocą adresu zdalnego punktu końcowego (nieprawidłowy plik znaków nazwy w typowych identyfikatory URI są zastępowane @ znaków).  
  
 Później, gdy do tego samego zdalny punkt końcowy wymagany jest identyfikator kontekstu, sprawdza, czy istnieje odpowiedni plik. Jeśli tak, odczytuje identyfikator kontekstu i zwraca. W przeciwnym razie zwraca identyfikator nowo wygenerowanym kontekście i zapisuje go w pliku. Z konfiguracji domyślnej pliki te są umieszczane w katalogu o nazwie ContextStore, który znajduje się w katalogu temp bieżącego użytkownika. Ta lokalizacja jest jednak można skonfigurować za pomocą elementu powiązania.  
  
 Konfiguruje się mechanizm używany do transportu identyfikator kontekstu. Go można albo zapisania nagłówka pliku cookie HTTP lub niestandardowy nagłówek SOAP. Niestandardowe podejście nagłówek SOAP sprawia, że możliwość korzystania z protokołów innych niż HTTP (np. TCP lub Named Pipes) tego protokołu. Istnieją dwie klasy, a mianowicie `MessageHeaderContextManager` i `HttpCookieContextManager`, który implementuje te dwie opcje.  
  
 Oba identyfikator kontekstu do zapisu komunikatu odpowiednio. Na przykład `MessageHeaderContextManager` klasy zapisuje go do nagłówka SOAP w `WriteContext` metody.  
  
```  
public override void WriteContext(Message message)  
{  
  string contextId = this.GetContextId();  
  
  MessageHeader contextHeader =  
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,  
      DurableInstanceContextUtility.HeaderNamespace,  
      contextId,   
      true);  
  
  message.Headers.Add(contextHeader);  
}   
```  
  
 Zarówno `ApplyContext` i `ReadContextId` metod w `DurableInstanceContextChannelBase` klasy wywołania `IContextManager.ReadContext` i `IContextManager.WriteContext`odpowiednio. Jednak te menedżerów kontekstu nie są bezpośrednio tworzone przez `DurableInstanceContextChannelBase` klasy. Zamiast tego używa `ContextManagerFactory` klasę, aby wykonać to zadanie.  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 `ApplyContext` Metoda jest wywoływana przez wysyłanie kanałów. Identyfikator kontekstu w komunikatach wychodzących go injects. `ReadContextId` Metoda jest wywoływana przez kanały odbierania. Ta metoda gwarantuje, że identyfikator kontekstu jest dostępny w komunikatach przychodzących i dodaje go do `Properties` Kolekcja `Message` klasy. Również zgłasza `CommunicationException` w przypadku awarii odczytać Identyfikatora kontekstu i w związku z tym powoduje, że kanał przerwanie.  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 Przed kontynuowaniem, ważne jest, aby zrozumieć użycie `Properties` kolekcji w `Message` klasy. Zwykle to `Properties` kolekcja jest używana, gdy przekazywanie danych z niższym na wyższe poziomy w warstwie kanału. W ten sposób żądanych danych można podać na wyższe poziomy w sposób ciągły, niezależnie od tego, szczegóły protokołu. Innymi słowy warstwie kanału wysyłać i odbierać identyfikator kontekstu jako nagłówka SOAP lub nagłówka pliku cookie HTTP. Ale nie jest niezbędna dla wyższe poziomy wiedzieć o te informacje, ponieważ w warstwie kanału sprawia, że te informacje są dostępne w `Properties` kolekcji.  
  
 Teraz z `DurableInstanceContextChannelBase` klasy w miejscu wszystkich dziesięciu niezbędne interfejsów (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Musi być implementowana IDuplexChannel, IDuplexSessionChannel). Są one podobne do każdej dostępnej wymiany komunikatów (datagram, jednostronny, dupleks i ich warianty sesyjnych). Każda z tych implementacji dziedziczyć klasy podstawowej opisany powyżej i wywołania `ApplyContext` i `ReadContexId` odpowiednio. Na przykład `DurableInstanceContextOutputChannel` — która implementuje interfejs IOutputChannel - wywołuje `ApplyContext` metody z każdej metody, która wysyła komunikaty.  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 Z drugiej strony `DurableInstanceContextInputChannel` — z zaimplementowanym `IInputChannel` interface - wywołania `ReadContextId` metody w każdej metodzie, który odbiera komunikaty.  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 Oprócz tego tych implementacji kanału delegowanie wywołań metod do kanału znajdującą się pod nimi w stosie kanału. Przekroczono wariantów jednak podstawowa logika, aby upewnić się, że identyfikator kontekstu są wysyłane i jest do odczytu tylko dla pierwszego komunikat, który powoduje, że sesja ma zostać utworzony.  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 Implementacje tych kanałów jest następnie dodawana do środowiska wykonawczego kanału WCF przez `DurableInstanceContextBindingElement` klasy i `DurableInstanceContextBindingElementSection` odpowiednio klasy. Zobacz [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanału przykładowej dokumentacji więcej szczegółów na temat elementów wiązania i powiązania elementu sekcje.  
  
## <a name="service-model-layer-extensions"></a>Rozszerzenia warstwy modelu usług  
 Teraz, identyfikator kontekstu ma pokonać za pośrednictwem warstwy kanału, można zaimplementować zachowanie usługi do dostosowywania wystąpienia. W tym przykładzie Menedżer magazynowania służy do ładowania i zapisać stanu z lub do magazynu trwałego. Jak opisano wcześniej, w tym przykładzie przedstawiono Menedżer magazynowania, który używa programu SQL Server 2005 jako jego magazynu zapasowego. Jednak również jest możliwie dodanie mechanizmów magazynu niestandardowego do tego rozszerzenia. W tym celu interfejs publiczny jest zadeklarowana, musi być implementowana przez wszystkich menedżerów magazynu.  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 `SqlServerStorageManager` Klasa zawiera domyślne `IStorageManager` implementacji. W jego `SaveInstance` metody dany obiekt jest zserializowanym przy użyciu elementu XmlSerializer i jest zapisywana w bazie danych programu SQL Server.  
  
```  
XmlSerializer serializer = new XmlSerializer(state.GetType());  
string data;  
  
using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))  
{  
    serializer.Serialize(writer, state);  
    data = writer.ToString();  
}  
  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";  
  
    using (SqlCommand command = new SqlCommand(update, connection))  
    {  
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
  
        int rows = command.ExecuteNonQuery();  
  
        if (rows == 0)  
        {  
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";  
            command.CommandText = insert;  
            command.ExecuteNonQuery();  
        }  
    }  
}  
```  
  
 W `GetInstance` — metoda odczytu danych serializacji dla Identyfikatora podanego kontekstu i utworzone na podstawie jego obiekt jest zwracany do obiektu wywołującego.  
  
```  
object data;  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";  
    using (SqlCommand command = new SqlCommand(select, connection))  
    {  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
        data = command.ExecuteScalar();  
    }  
}  
  
if (data != null)  
{  
    XmlSerializer serializer = new XmlSerializer(type);  
    using (StringReader reader = new StringReader((string)data))  
    {  
        object instance = serializer.Deserialize(reader);  
        return instance;  
    }  
}  
```  
  
 Użytkownicy tych magazynu menedżerów nie powinien bezpośrednio utworzyć ich wystąpienia. Używają `StorageManagerFactory` klasy, która abstracts z szczegóły tworzenie Menedżera magazynu. Ta klasa ma jeden statyczny element członkowski `GetStorageManager`, co powoduje wystąpienie typu Menedżera danego magazynu. Jeśli parametr typu jest `null`, ta metoda tworzy wystąpienie domyślne `SqlServerStorageManager` klasy i zwraca go. Jest również sprawdzane danego typu, aby upewnić się, że implementuje `IStorageManager` interfejsu.  
  
```  
public static IStorageManager GetStorageManager(Type storageManagerType)  
{  
IStorageManager storageManager = null;  
  
if (storageManagerType == null)  
{  
    return new SqlServerStorageManager();  
}  
else  
{  
    object obj = Activator.CreateInstance(storageManagerType);  
  
    // Throw if the specified storage manager type does not  
    // implement IStorageManager.  
    if (obj is IStorageManager)  
    {  
        storageManager = (IStorageManager)obj;  
    }  
    else  
    {  
        throw new InvalidOperationException(  
                  ResourceHelper.GetString("ExInvalidStorageManager"));  
    }  
  
    return storageManager;  
}                  
}   
```  
  
 Zaimplementowano infrastruktury wymaganej do odczytu i zapisu z magazynu trwałego wystąpienia. Teraz czynności niezbędnych do zmiany zachowania usługi muszą zostać pobrane.  
  
 W pierwszym kroku procesu mamy do zapisania Identyfikatora kontekstu, która pochodzi za pośrednictwem warstwy kanału do bieżącego obiektu InstanceContext. Obiekt InstanceContext jest składnika środowiska uruchomieniowego, który pełni rolę łącza między dyspozytora WCF i wystąpienie usługi. Może służyć do dodatkowych stanie i zachowanie do wystąpienia usługi. Jest to konieczne, ponieważ w komunikacie sesyjnych identyfikator kontekstu jest wysyłane tylko z pierwszego komunikatu.  
  
 Usługi WCF umożliwia rozszerzanie jej składnika środowiska wykonawczego InstanceContext przez dodanie nowego stanu i zachowanie przy użyciu jego wzorca rozszerzonego obiektu. Wzorzec extensible obiekt jest używany w programie WCF wydłużyć istniejące klasy środowiska uruchomieniowego z nowych funkcji lub dodawania nowych funkcji stanu do obiektu. Istnieją trzy interfejsy we wzorcu rozszerzonego obiektu - interfejs IExtensibleObject\<T >, IExtension\<T >, a IExtensionCollection\<T >:  
  
-   Interfejs IExtensibleObject\<T > Interfejs jest implementowany przez obiekty, które umożliwia rozszerzenia umożliwiające dostosowanie ich funkcje.  
  
-   IExtension\<T > Interfejs jest implementowany przez obiekty, które mają rozszerzenia klasy typu T.  
  
-   IExtensionCollection\<T > interfejsu jest kolekcją IExtensions, która umożliwia pobieranie IExtensions według typu.  
  
 W związku z tym klasy InstanceContextExtension należy utworzyć implementuje interfejs IExtension, który definiuje stan wymagane do zapisania identyfikatora kontekstu. Ta klasa udostępnia także stanu do przechowywania magazynu Menedżera używane. Po zapisaniu nowy stan nie powinny być go zmodyfikować. W związku z tym stan ma być dostarczana i zapisywane do wystąpienia w czasie, które są skonstruowane i następnie dostępna tylko za pomocą właściwości tylko do odczytu.  
  
```  
// Constructor  
public DurableInstanceContextExtension(string contextId,   
            IStorageManager storageManager)  
{  
    this.contextId = contextId;  
    this.storageManager = storageManager;              
}  
  
// Read only properties  
public string ContextId  
{  
    get { return this.contextId; }  
}  
  
public IStorageManager StorageManager  
{  
    get { return this.storageManager; }              
}   
```  
  
 Klasa InstanceContextInitializer implementuje interfejs IInstanceContextInitializer i dodaje do kolekcji rozszerzenia InstanceContext budowany rozszerzenie kontekstu wystąpienia.  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
    string contextId =   
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];  
  
    DurableInstanceContextExtension extension =  
                new DurableInstanceContextExtension(contextId,   
                     storageManager);  
    instanceContext.Extensions.Add(extension);  
}  
```  
  
 Zgodnie z wcześniejszym opisem identyfikator kontekstu zostanie odczytany z `Properties` Kolekcja `Message` klasy i przekazany do konstruktora klasy extension. Oznacza to, jak informacje może być wymieniane między warstwami w sposób ciągły.  
  
 Następnym krokiem ważne zastępuje procesu tworzenia wystąpienia usługi. Usługi WCF umożliwia Implementowanie niestandardowego wystąpienia zachowania i przechwytywanie je do środowiska uruchomieniowego przy użyciu interfejsu IInstanceProvider. Nowe `InstanceProvider` zaimplementowana jest klasa, aby wykonać to zadanie. W Konstruktorze jest akceptowany oczekiwano od dostawcy wystąpienia typu usługi. Później służy to tworzenia nowych wystąpień. W `GetInstance` tworzone jest wystąpienie Menedżera magazynu implementacji wyszukiwanie trwałego wystąpienia. Jeśli zmienna zwraca `null` utworzone nowe wystąpienie typu usługi i zwracany do obiektu wywołującego.  
  
```  
public object GetInstance(InstanceContext instanceContext, Message message)  
{  
    object instance = null;  
  
    DurableInstanceContextExtension extension =  
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();  
  
    string contextId = extension.ContextId;  
    IStorageManager storageManager = extension.StorageManager;              
  
    instance = storageManager.GetInstance(contextId, serviceType);          
  
    if (instance == null)  
    {  
        instance = Activator.CreateInstance(serviceType);  
    }  
  
    return instance;  
}  
```  
  
 Ważne następnym krokiem jest zainstalowanie `InstanceContextExtension`, `InstanceContextInitializer` i `InstanceProvider` klasy w czasie wykonywania modelu usługi. Atrybut niestandardowy może służyć do oznaczenie klasy implementacji usługi do zainstalowania zachowanie. `DurableInstanceContextAttribute` Zawiera implementację tego atrybutu i implementuje `IServiceBehavior` interfejs do rozszerzania środowiska uruchomieniowego całej usługi.  
  
 Ta klasa ma właściwość, która akceptuje typ Menedżera magazynu, który ma być używany. W ten sposób wykonania pozwala użytkownikom na określenie własnych `IStorageManager` implementacji jako parametr tego atrybutu.  
  
 W `ApplyDispatchBehavior` implementacji `InstanceContextMode` bieżącego `ServiceBehavior` atrybutu jest weryfikowany. Jeśli ta właściwość jest ustawiona na pojedyncze, włączanie trwałe wystąpień nie jest możliwe i `InvalidOperationException` jest generowany, by powiadomić hosta.  
  
```  
ServiceBehaviorAttribute serviceBehavior =  
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();  
  
if (serviceBehavior != null &&  
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)  
{  
    throw new InvalidOperationException(  
       ResourceHelper.GetString("ExSingeltonInstancingNotSupported"));  
}  
```  
  
 Po tym wystąpienia Menedżera magazynowania, wystąpienie kontekstu inicjatora i dostawcy wystąpienia są tworzone i zainstalowane w `DispatchRuntime` utworzone dla każdego punktu końcowego.  
  
```  
IStorageManager storageManager =   
    StorageManagerFactory.GetStorageManager(storageManagerType);  
  
InstanceContextInitializer contextInitializer =  
    new InstanceContextInitializer(storageManager);  
  
InstanceProvider instanceProvider =  
    new InstanceProvider(description.ServiceType);  
  
foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
{  
    ChannelDispatcher cd = cdb as ChannelDispatcher;  
  
    if (cd != null)  
    {  
        foreach (EndpointDispatcher ed in cd.Endpoints)  
        {  
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);  
            ed.DispatchRuntime.InstanceProvider = instanceProvider;  
        }  
    }  
}  
```  
  
 W podsumowaniu wykonanej do tej pory w tym przykładzie ma utworzyło kanału, który jest włączony protokół przewodowy niestandardowych dla programu exchange identyfikator kontekstu niestandardowe, a także zastępuje domyślne zachowanie można załadować wystąpienia z magazynu trwałego wystąpień.  
  
 Pozostała to sposób Zapisz do magazynu trwałego wystąpienia usługi. Jak wspomniano wcześniej, jest już wymagane funkcje można zapisać stanu w `IStorageManager` implementacji. Mamy teraz należy zintegrować to ze środowiskiem uruchomieniowym WCF. Inny atrybut jest wymagany, które mają zastosowanie do metody w klasie implementacji usługi. Ten atrybut powinien można zastosować do metody, które spowodują zmianę stanu wystąpienia usługi.  
  
 `SaveStateAttribute` Klasa implementuje tę funkcję. Implementuje również `IOperationBehavior` klasę, aby zmodyfikować środowiska uruchomieniowego WCF dla każdej operacji. Podczas metoda jest oznaczona atrybutem tego atrybutu, wywołuje środowiska uruchomieniowego WCF `ApplyBehavior` metoda podczas odpowiednie `DispatchOperation` jest tworzona. W tej implementacji metody jest pojedynczy wiersz kodu:  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 Ta instrukcja tworzy wystąpienie `OperationInvoker` typu, a następnie przypisuje go do `Invoker` właściwość `DispatchOperation` tworzona. `OperationInvoker` Klasy jest otoki dla wywołującego operacji domyślny utworzony dla `DispatchOperation`. Ta klasa implementuje `IOperationInvoker` interfejsu. W `Invoke` implementacji metody wywołania metody rzeczywistego jest delegowane do wywoływania operacji wewnętrznej. Jednak przed zwracania wyników Menedżer magazynowania w `InstanceContext` służy do zapisania wystąpienia usługi.  
  
```  
object result = innerOperationInvoker.Invoke(instance,  
    inputs, out outputs);  
  
// Save the instance using the storage manager saved in the   
// current InstanceContext.  
InstanceContextExtension extension =  
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();  
  
extension.StorageManager.SaveInstance(extension.ContextId, instance);  
return result;  
```  
  
## <a name="using-the-extension"></a>Przy użyciu rozszerzenia  
 Zarówno warstwy kanału i rozszerzeń warstwy modelu usług są wykonywane, i teraz można używać w aplikacji WCF. Usługi trzeba dodać do stosu kanału, za pomocą niestandardowego powiązania kanału, a następnie oznaczenie klasy implementacji usługi z odpowiednich atrybutów.  
  
```  
[DurableInstanceContext]  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class ShoppingCart : IShoppingCart  
{  
//…  
     [SaveState]  
     public int AddItem(string item)  
     {  
         //…  
     }  
//…  
 }  
```  
  
 Aplikacje klienckie należy dodać DurableInstanceContextChannel do stosu kanału, za pomocą niestandardowego powiązania. Aby skonfigurować kanał deklaratywnie w pliku konfiguracji, sekcja element powiązania ma ma zostać dodany do kolekcji rozszerzeń element powiązania.  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 Element powiązania można teraz używać z niestandardowego powiązania, podobnie jak inne elementy Powiązanie standardowe:  
  
```xml  
<bindings>  
 <customBinding>  
   <binding name="TextOverHttp">  
     <durableInstanceContext contextType="HttpCookie"/>             
     <reliableSession />  
     <textMessageEncoding />  
     <httpTransport />  
   </binding>  
 </customBinding>  
</bindings>  
```  
  
## <a name="conclusion"></a>Wniosek  
 W tym przykładzie pokazano sposób tworzenia kanału protokołu niestandardowego oraz jak dostosować zachowanie usługi, aby ją włączyć.  
  
 Rozszerzenie można dodatkowo zwiększyć, umożliwiając użytkownikom określanie `IStorageManager` wdrożenia przy użyciu sekcji konfiguracji. Dzięki temu można modyfikować magazynu zapasowego bez konieczności ponownego kompilowania kodu usługi.  
  
 Ponadto użytkownik może próbować Implementowanie klasy (na przykład `StateBag`), który hermetyzuje stan wystąpienia. Tej klasy jest odpowiedzialny za utrwalanie stanu zawsze, gdy zmieni się. W ten sposób możesz uniknąć używania `SaveState` atrybutu i dokładniej wykonywania utrwalanie pracy (na przykład można utrwalić stanu, gdy stan faktycznie zostanie zmieniona zamiast zapisywać dokument każdorazowo po metodę o `SaveState` atrybutu wywołuje się).  
  
 Po uruchomieniu próbki następujące dane wyjściowe są wyświetlane. Klient dodaje dwa elementy do jego koszyk i następnie pobiera listę elementów w jego koszyk z usługi. Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  Ponowne tworzenie usługi spowoduje zastąpienie pliku bazy danych. Aby przyjrzeć się stanu zachowanego przez wiele przebiegów próbki, należy nie odbudować próbki między działa.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  SQL Server 2005 lub SQL Express 2005, aby uruchomić ten przykład, użytkownik musi być uruchomiona. Jeśli używasz programu SQL Server 2005, należy zmodyfikować konfigurację parametrów połączenia usługi. Podczas uruchamiania między komputerami, programu SQL Server jest wymagana tylko na komputerze z serwerem.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a>Zobacz też
