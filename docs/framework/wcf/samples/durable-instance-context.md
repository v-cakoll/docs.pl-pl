---
title: Kontekst niezawodnej instancji
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 25772e7f119ddd5a144d223f402e815380b3eba5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990273"
---
# <a name="durable-instance-context"></a>Kontekst niezawodnej instancji
Niniejszy przykład pokazuje sposób dostosowywania środowiska uruchomieniowego Windows Communication Foundation (WCF), aby włączyć kontekst niezawodnej instancji. Jako jej zapasowy magazyn (SQL Server 2005 Express w tym przypadku) używa programu SQL Server 2005. Jednak także zapewnia możliwość dostępu do magazynu niestandardowego mechanizmów.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Ten przykład obejmuje rozszerzanie warstwy kanału i warstwy modelu usług WCF. Dlatego jest niezbędne do zrozumienia podstawowych pojęć przed przejściem do szczegółów implementacji.  
  
 Kontekst niezawodnej instancji znajdują się w rzeczywistych scenariuszach bardzo często. Uwzględnić aplikację zakupową koszyka na przykład, ma możliwość wstrzymania widoczny w połowie zakupów za pośrednictwem i kontynuować kolejny dzień. Dlatego, że gdy odwiedza koszyka następnego dnia, zostanie przywrócony naszych oryginalnego kontekstu. Należy zauważyć, że aplikacji koszyka zakupów, (na serwerze) nie są zachowywane wystąpienie koszyka zakupów podczas, gdy firma Microsoft jest odłączony. Zamiast tego będzie się powtarzał stanu do nośnika trwałego magazynu i używa go podczas tworzenia nowego wystąpienia dla kontekstu przywrócona. W związku z tym wystąpienie usługi, która może obsłużyć na tym samym kontekście nie jest taka sama jak poprzednie wystąpienie (oznacza to, że nie ma tego samego adresu pamięci).  
  
 Kontekst niezawodnej instancji jest możliwe dzięki małej protokołu, który wymienia identyfikator kontekstu między klientem a usługą. Ten identyfikator kontekstu jest tworzony na komputerze klienckim i przesyłane do usługi. Po utworzeniu wystąpienia usługi, środowisko wykonawcze usług próbuje załadować utrwalonego stanu, który odnosi się do tego Identyfikatora kontekstu z magazynu trwałego (domyślnie jest bazę danych programu SQL Server 2005). Jeśli stan nie jest dostępne nowe wystąpienie ma stanu domyślnego. Implementacji usługi używa atrybutu niestandardowego, aby oznaczyć operacje, aby zmienić stan wdrożenia usługi, dzięki czemu środowisko uruchomieniowe można zapisać wystąpienia usługi po ich wywoływania.  
  
 Według opisu w poprzednich do osiągnięcia celu, łatwo można wyróżnić dwa kroki:  
  
1. Zmienić komunikat, który przechodzi na potrzeby przesyłu, żeby identyfikator kontekstu.  
  
2. Zmień zachowanie lokalnej usługi, aby zaimplementować logikę niestandardową wystąpień.  
  
 Ponieważ pierwszy z nich na liście ma wpływ na wiadomości na łączu powinny zostać wdrożone jako niestandardowy kanał i być podłączony do warstwy kanału. Ten ostatni ma wpływ tylko na zachowanie lokalnej usługi i może być implementowana przez rozszerzenie kilka punktów rozszerzeń usługi. W kolejnych sekcjach opisano każdy z tych rozszerzeń.  
  
## <a name="durable-instancecontext-channel"></a>Trwałość InstanceContext kanału  
 Najpierw Przyjrzyj się to rozszerzenie warstwy kanału. Pierwszym krokiem w niestandardowym kanale w pisaniu jest podjęcie decyzji, struktura komunikacji kanału. Jak wprowadzono nowy protokół przewodowy kanał powinny współpracować z prawie każdego innego kanału w stosie kanału. W związku z tym go powinien obsługiwać wszystkie wzorce wymiany komunikatów. Jednak podstawowe funkcje kanału jest taki sam, niezależnie od jego strukturę komunikacji. W szczególności od klienta jego powinien zapisać identyfikator kontekstu do wiadomości i z usługi należy przeczytać ten identyfikator kontekstu od wiadomości i przekazać go do wyższych poziomów. Z tego powodu `DurableInstanceContextChannelBase` klasa jest tworzona, który działa jako abstrakcyjna klasa bazowa dla wszystkich implementacjach kanału kontekst niezawodnej instancji. Ta klasa zawiera typowe funkcje zarządzania maszyny stanu i dwa chronionych elementów członkowskich, aby zastosować i przeczytaj informacje o kontekście do i z wiadomości.  
  
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
  
 Te dwie metody użytkowania `IContextManager` implementacji do zapisu i odczytu identyfikator kontekstu do lub z komunikatu. (`IContextManager` jest niestandardowy interfejs używany do definiowania kontrakt dla wszystkich menedżerów kontekstu.) Kanał można dołączyć identyfikator kontekstu w niestandardowy nagłówek SOAP lub w nagłówku pliku cookie HTTP. Każda implementacja menedżera kontekstowego dziedziczy `ContextManagerBase` klasę, która zawiera funkcje wspólne dla wszystkich menedżerów kontekstu. `GetContextId` Metody tej klasy jest używany tak, jakby pochodził identyfikator kontekstu od klienta. Jeśli kontekst, w których identyfikator jest tworzone po raz pierwszy, ta metoda zapisuje do pliku tekstowego, którego nazwa jest tworzona przy użyciu adresu zdalnego punktu końcowego (nieprawidłowy plik znaków nazwy w typowych identyfikatorów URI są zastępowane @ Zn.).  
  
 Później podczas identyfikator kontekstu jest wymagany do tego samego zdalnego punktu końcowego, sprawdza, czy istnieje odpowiedni plik. Jeśli tak jest, odczytuje identyfikator kontekstu i zwraca. W przeciwnym razie zwraca identyfikator nowo wygenerowane kontekstu i zapisuje go do pliku. W przypadku domyślnej konfiguracji tych plików są umieszczane w katalogu o nazwie ContextStore, która znajduje się w katalogu tymczasowym bieżącego użytkownika. Jednak ta lokalizacja jest można skonfigurować za pomocą elementu powiązania.  
  
 Mechanizm służący do transportu kontekstowy identyfikator jest konfigurowany. Jego można albo zapisywane do nagłówka pliku cookie HTTP lub niestandardowy nagłówek SOAP. Niestandardowe podejście nagłówek SOAP umożliwia tego protokołu za pomocą protokołów innych niż HTTP (na przykład, TCP lub Named Pipes). Istnieją dwie klasy, a mianowicie `MessageHeaderContextManager` i `HttpCookieContextManager`, która implementuje te dwie opcje.  
  
 Obydwaj zapisu identyfikator kontekstu do wiadomości odpowiednio. Na przykład `MessageHeaderContextManager` klasy zapisuje go do nagłówka SOAP w `WriteContext` metody.  
  
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
  
 Zarówno `ApplyContext` i `ReadContextId` metody `DurableInstanceContextChannelBase` wywołać klasy `IContextManager.ReadContext` i `IContextManager.WriteContext`, odpowiednio. Jednak te menedżerów kontekstu nie są bezpośrednio tworzone przez `DurableInstanceContextChannelBase` klasy. Zamiast tego używa `ContextManagerFactory` klasie w celu wykonania tego zadania.  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 `ApplyContext` Metoda jest wywoływana przez wysyłanie kanałów. Wprowadza ona identyfikator kontekstu do wiadomości wychodzących. `ReadContextId` Metoda jest wywoływana przez odbieranie kanałów. Ta metoda zapewnia, że identyfikator kontekstu jest dostępny w wiadomości przychodzących i dodaje go do `Properties` zbiór `Message` klasy. Zgłasza również `CommunicationException` w razie awarii można odczytać Identyfikatora kontekstu i dlatego powoduje, że kanał przerwanie.  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 Zanim przejdziesz dalej, jest ważne, aby zrozumieć wykorzystanie `Properties` kolekcji w `Message` klasy. Zwykle to `Properties` kolekcja jest używana, gdy przekazywanie danych od niższych do wyższych poziomów z warstwy kanału. W ten sposób żądane dane można przekazać do wyższych poziomów w spójny sposób niezależnie od tego, szczegóły protokołu. Innymi słowy warstwy kanału można wysyłać i odbierać identyfikator kontekstu jako nagłówek SOAP lub nagłówka pliku cookie HTTP. Ale nie jest konieczne wyższe poziomy wiedzieć o te informacje, ponieważ warstwy kanału sprawia, że te informacje są dostępne w `Properties` kolekcji.  
  
 Teraz dzięki `DurableInstanceContextChannelBase` klasy w miejscu wszystkie dziesięć niezbędne interfejsy (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Można zaimplementować IDuplexChannel, IDuplexSessionChannel). Są one podobne do każdego wymiany dostępnego komunikatu (datagram, jednostronny, komunikacja dwukierunkowa i ich warianty sesji). Każda z tych implementacji dziedziczą z klasy bazowej, opisany wcześniej i wywołania `ApplyContext` i `ReadContexId` odpowiednio. Na przykład `DurableInstanceContextOutputChannel` — który implementuje interfejs IOutputChannel - wywołuje `ApplyContext` metody z każdej metody, która wysyła komunikaty.  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 Z drugiej strony `DurableInstanceContextInputChannel` — które implementują `IInputChannel` interface - wywołania `ReadContextId` metody w każdej metody, która odbiera komunikaty.  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 Niezależnie od tego tych implementacji kanału delegowanie wywołań metod do kanału pod nimi w stosie kanału. Przekroczono wariantów jednak podstawową logikę, aby upewnić się, że identyfikator kontekstu jest wysyłana i jest tylko do odczytu dla pierwszego komunikatu, który powoduje, że sesja ma zostać utworzony.  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 Tych implementacji kanału zostaną następnie dodane do środowiska uruchomieniowego kanału WCF, `DurableInstanceContextBindingElement` klasy i `DurableInstanceContextBindingElementSection` klasy odpowiednio. Zobacz [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanału przykładowa dokumentacja, aby uzyskać więcej szczegółów na temat elementów wiązania i powiązania sekcje elementu.  
  
## <a name="service-model-layer-extensions"></a>Rozszerzenia warstwy modelu usług  
 Teraz, gdy identyfikator kontekstu ma przejść przez warstwy kanału, można zaimplementować zachowanie usługi do dostosowywania procesu tworzenia wystąpienia. W tym przykładzie Menedżer magazynowania służy do ładowania i Zapisz stan z lub do magazynu trwałego. Jak wyjaśniono wcześniej, w tym przykładzie przedstawiono Menedżer magazynowania, który używa programu SQL Server 2005 jako jego magazyn zapasowy. Jednak użytkownik może również dodać mechanizmów magazynu niestandardowego do tego rozszerzenia. W tym interfejs publiczny jest zadeklarowana, muszą być zaimplementowane przez wszystkich menedżerów magazynu.  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 `SqlServerStorageManager` Klasy zawiera domyślną `IStorageManager` implementacji. W jego `SaveInstance` metody dany obiekt jest serializowana, przy użyciu elementu XmlSerializer i jest zapisywany w bazie danych programu SQL Server.  
  
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
  
 W `GetInstance` metoda serializowane dane do odczytu dla Identyfikatora podanym kontekście i obiekt skonstruowany z niego jest zwracany do obiektu wywołującego.  
  
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
  
 Użytkownicy tych magazynu menedżerów nie powinien bezpośrednio utworzyć ich wystąpienia. Używają `StorageManagerFactory` klasy, która przenosi dane tworzenie Menedżera magazynu. Ta klasa ma jeden statyczny element członkowski `GetStorageManager`, która tworzy wystąpienie typu Menedżera magazynowania. Jeśli parametr typu jest `null`, ta metoda tworzy wystąpienie domyślne `SqlServerStorageManager` klasy i zwraca go. Również sprawdza poprawność danego typu, aby upewnić się, że implementuje `IStorageManager` interfejsu.  
  
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
  
 Zaimplementowano infrastruktury wymaganej do odczytu i zapisu wystąpienia z magazynu trwałego. Teraz niezbędne kroki, aby zmienić zachowanie usługi muszą zostać pobrane.  
  
 W pierwszym kroku tego procesu trzeba zapisać identyfikator kontekstu, który pochodzi za pośrednictwem warstwy kanału do bieżącego obiektu InstanceContext. Obiekt InstanceContext jest składnika środowiska uruchomieniowego, który działa jako łącze między dyspozytora WCF i wystąpienie usługi. Umożliwia zapewnienie dodatkowy stan i zachowanie do wystąpienia usługi. Jest to ważne, ponieważ w ramach sesji komunikacji identyfikator kontekstu są wysyłane tylko w przypadku pierwszego komunikatu.  
  
 Usługi WCF umożliwia rozszerzanie jego składnika środowiska wykonawczego typu InstanceContext przez dodanie nowego Państwa i zachowanie przy użyciu jego wzorzec extensible object. Wzorzec extensible object jest używany w programie WCF, albo rozszerzanie istniejących klas środowiska uruchomieniowego przy użyciu nowych funkcji lub dodać nowe funkcje stan z obiektem. Istnieją trzy interfejsy we wzorcu extensible object - IExtensibleObject\<T >, IExtension\<T >, a IExtensionCollection\<T >:  
  
- IExtensibleObject\<T > Interfejs jest implementowany przez obiekty, które umożliwia rozszerzenia umożliwiające dostosowanie ich funkcje.  
  
- IExtension\<T > Interfejs jest implementowany przez obiekty, które mają rozszerzenia klas typu T.  
  
- IExtensionCollection\<T > Interfejs jest zbiorem IExtensions, która umożliwia pobieranie IExtensions według ich typu.  
  
 W związku z tym klasę InstanceContextExtension powinny zostać utworzone implementuje interfejs IExtension, który definiuje wymagany stan do zapisania identyfikatora kontekstu. Ta klasa udostępnia także stanu do przechowywania magazynu manager używane. Po zapisaniu nowego stanu nie powinna być go zmodyfikować. W związku z tym stan ma być dostarczana i zapisywane do wystąpienia w czasie, który jest zbudowany, a następnie dostępny tylko za pomocą właściwości tylko do odczytu.  
  
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
  
 Klasa InstanceContextInitializer implementuje interfejs IInstanceContextInitializer i dodaje do kolekcji rozszerzeń typu InstanceContext budowany rozszerzenie kontekstu wystąpienia.  
  
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
  
 Zgodnie z wcześniejszym opisem identyfikator kontekstu są odczytywane z `Properties` zbiór `Message` klasy i przekazany do konstruktora klasy extension. W tym przykładzie pokazano, jak informacje mogą być wymieniane między warstwami w spójny sposób.  
  
 Następnym krokiem ważne zastępują procesu tworzenia wystąpienia usługi. Usługi WCF umożliwia Implementowanie zachowań niestandardowych podczas tworzenia wystąpienia i przechwytywanie je do środowiska uruchomieniowego przy użyciu interfejsu IInstanceProvider. Nowy `InstanceProvider` klasy zaimplementowany, aby wykonać to zadanie. W Konstruktorze jest akceptowana oczekiwano od dostawcy wystąpienia typu usługi. Później służy do tworzenia nowych wystąpień. W `GetInstance` tworzone jest wystąpienie Menedżera magazynu implementacji szukasz utrwalonego wystąpienia. Jeśli zostanie zwrócona `null` , a następnie nowe wystąpienie typu usługi jest tworzone i zwracany do wywołującego.  
  
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
  
 Dalej ważnym krokiem jest zainstalowanie `InstanceContextExtension`, `InstanceContextInitializer` i `InstanceProvider` klas w czasie wykonywania modelu usługi. Niestandardowy atrybut może służyć do oznaczania zachowanie podczas instalowania klasy implementacji usługi. `DurableInstanceContextAttribute` Zawiera implementację tego atrybutu i implementuje `IServiceBehavior` interfejsu, aby rozszerzyć środowisko uruchomieniowe całą usługę.  
  
 Ta klasa posiada właściwości, które akceptuje typ Menedżera magazynu do użycia. W ten sposób implementacji umożliwia użytkownikom określenie własnych `IStorageManager` implementacji jako parametr tego atrybutu.  
  
 W `ApplyDispatchBehavior` implementacji `InstanceContextMode` bieżącego `ServiceBehavior` atrybutu jest weryfikowana. Jeśli ta właściwość jest ustawiona na pojedyncze, umożliwiając niezawodne tworzenie wystąpienia nie jest możliwe i `InvalidOperationException` jest zgłaszany w celu powiadomienia hosta.  
  
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
  
 Po tym wystąpienia Menedżera magazynu, wystąpienia kontekstu inicjatora i dostawca wystąpień są tworzone i zainstalowane w `DispatchRuntime` utworzone dla każdego punktu końcowego.  
  
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
  
 W podsumowaniu do tej pory w tym przykładzie tworzył kanału, który jest włączony protokół przewodowy niestandardowe wymiana identyfikator kontekstu niestandardowe, a także zastępuje domyślne zachowanie, aby załadować wystąpień z magazynu trwałego wystąpień.  
  
 Zachowasz pozostałe jest sposób można zapisać wystąpienia usługi w magazynie trwałym. Jak wspomniano wcześniej, jest już wymaganych funkcji, która ma być zapisany stan w `IStorageManager` implementacji. Firma Microsoft teraz muszą zintegrować to ze środowiskiem uruchomieniowym usługi WCF. Inny atrybut jest wymagany, które mają zastosowanie do metody w klasie implementacji usługi. Ten atrybut powinien ma zostać zastosowany do metody, które zmieniają stan wystąpienia usługi.  
  
 `SaveStateAttribute` Klasa implementuje tę funkcję. Implementuje także `IOperationBehavior` klasy, aby zmodyfikować środowisko wykonawcze programu WCF dla każdej operacji. Gdy metoda jest oznaczona za pomocą tego atrybutu, środowisko wykonawcze programu WCF wywołuje `ApplyBehavior` metody podczas odpowiednie `DispatchOperation` jest budowany. W tej implementacji metoda ma nawet jednego wiersza kodu:  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 Ta instrukcja tworzy wystąpienie `OperationInvoker` typu, a następnie przypisuje go do `Invoker` właściwość `DispatchOperation` budowany. `OperationInvoker` Klasy jest otoką element wywołujący operacji domyślne, które zostały utworzone dla `DispatchOperation`. Ta klasa implementuje `IOperationInvoker` interfejsu. W `Invoke` implementacji metody wywołania metody rzeczywisty jest delegowane do wywoływania operacji wewnętrznej. Jednak przed zwracania wyników Menedżer magazynowania w `InstanceContext` służy do zapisania wystąpienia usługi.  
  
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
 Zarówno warstwy kanału i rozszerzenia warstwy modelu usług są wykonywane, i ich można teraz używać w aplikacjach usługi WCF. Usługi trzeba dodać kanał do stosu kanału, za pomocą niestandardowego powiązania, a następnie oznacz klas implementacji usług z odpowiednimi atrybutami.  
  
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
  
 Aplikacje klienckie należy dodać DurableInstanceContextChannel do stosu kanału, za pomocą niestandardowego powiązania. Aby skonfigurować kanał deklaratywnie w pliku konfiguracji, sekcja element powiązania ma ma zostać dodany do kolekcji rozszerzenia elementu powiązania.  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 Element powiązania można teraz za pomocą niestandardowego powiązania, podobnie jak inne elementy powiązania standardowe:  
  
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
 W tym przykładzie pokazano sposób tworzenia kanału protokołu niestandardowego i jak dostosować zachowanie usługi, aby ją włączyć.  
  
 Rozszerzenie można dodatkowo zwiększyć, umożliwiając użytkownikom określanie `IStorageManager` wdrożenia przy użyciu sekcji konfiguracji. Dzięki temu można modyfikować magazyn zapasowy bez konieczności ponownego kompilowania kodu usługi.  
  
 Ponadto użytkownik może próbować Implementowanie klasy (na przykład `StateBag`), która hermetyzuje stan wystąpienia. Ta klasa jest odpowiedzialne za utrwalanie stanu zawsze wtedy, gdy zmienia się. W ten sposób możesz uniknąć używania `SaveState` atrybutu i wykonywania pracy utrwalanie dokładniej (na przykład można utrwalić stanu rzeczywiście zmiana stanu zamiast zapisywać każdym razem gdy metody z `SaveState` atrybutu wywołuje się).  
  
 Po uruchomieniu przykładu, następujące dane wyjściowe są wyświetlane. Klient dodaje dwa elementy do jego koszyka zakupów i następnie pobiera listę elementów w jego koszyk sklepowy z usługi. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  Ponowne tworzenie usługi zastępuje plik bazy danych. Aby obserwować stanu zachowanego wielu uruchomień próbki, należy nie ponownie skompiluj przykładowy między działa.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Musi działać program SQL Server 2005 lub SQL Express 2005, aby uruchomić ten przykład. Jeśli używasz programu SQL Server 2005, należy zmodyfikować konfigurację parametrów połączenia usługi. Podczas uruchamiania między komputerami, programu SQL Server jest wymagana tylko na komputerze z serwerem.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
