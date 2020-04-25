---
title: Kontekst niezawodnej instancji
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 604a617dc03bf06b71fe3019b58b2161216ee3e0
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141185"
---
# <a name="durable-instance-context"></a>Kontekst niezawodnej instancji

Ten przykład pokazuje, jak dostosować środowisko uruchomieniowe programu Windows Communication Foundation (WCF) w celu włączenia trwałych kontekstów wystąpień. Używa SQL Server 2005 jako magazynu zapasowego (w tym przypadku SQL Server 2005 Express). Zapewnia również sposób dostępu do niestandardowych mechanizmów magazynowania.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Ten przykład obejmuje Rozszerzanie warstwy kanału i warstwy modelu usług WCF. W związku z tym należy zrozumieć podstawowe koncepcje przed przejściem do szczegółów implementacji.

Nietrwałe konteksty wystąpień można często znaleźć w rzeczywistych scenariuszach. Na przykład aplikacja koszyka zakupów umożliwia wstrzymywanie zakupów w połowie i kontynuowanie pracy w innym dniu. W związku z tym, gdy będziemy odwiedzać koszyk następnym dniem, zostanie przywrócony oryginalny kontekst. Należy pamiętać, że aplikacja koszyka zakupów (na serwerze) nie utrzymuje wystąpienia koszyka zakupów, gdy nastąpi odłączenie. Zamiast tego zachowuje swój stan w postaci trwałego nośnika magazynu i używa go podczas konstruowania nowego wystąpienia dla przywróconego kontekstu. W związku z tym wystąpienie usługi, które może być usługą dla tego samego kontekstu, nie jest takie samo jak poprzednie wystąpienie (to oznacza, że nie ma tego samego adresu pamięci).

Trwały kontekst wystąpienia jest możliwy przez niewielki protokół, który wymienia identyfikator kontekstu między klientem a usługą. Ten identyfikator kontekstu jest tworzony na kliencie i przesyłany do usługi. Po utworzeniu wystąpienia usługi środowisko uruchomieniowe programu próbuje załadować stan trwały, który odnosi się do tego identyfikatora kontekstu z magazynu trwałego (domyślnie jest to baza danych SQL Server 2005). Jeśli żaden stan nie jest dostępny, nowe wystąpienie ma stan domyślny. Implementacja usługi używa atrybutu niestandardowego do oznaczania operacji, które zmieniają stan implementacji usługi, aby środowisko uruchomieniowe mógł zapisać wystąpienie usługi po wywołaniu.

Zgodnie z powyższym opisem, dwa kroki można łatwo rozróżnić, aby osiągnąć cel:

1. Zmień komunikat, który przechodzi do sieci, aby przenieść identyfikator kontekstu.

2. Zmień lokalne zachowanie usługi, aby zaimplementować logikę wystąpień niestandardowych.

Ponieważ pierwszy na liście ma wpływ na komunikaty w sieci, należy wdrożyć jako kanał niestandardowy i podłączyć do warstwy kanału. Ta ostatnia ma wpływ tylko na lokalne zachowanie usługi i dlatego można ją zaimplementować, rozszerzając kilka punktów rozszerzalności usługi. W następnych sekcjach omówiono wszystkie te rozszerzenia.

## <a name="durable-instancecontext-channel"></a>Trwały kanał InstanceContext

Pierwszym krokiem, aby sprawdzić, jest rozszerzenie warstwy kanału. Pierwszym krokiem w pisaniu niestandardowego kanału jest podjęcie decyzji dotyczącej struktury komunikacji kanału. Gdy jest wprowadzany nowy protokół sieci, kanał powinien współpracować z niemal każdym innym kanałem w stosie kanałów. W związku z tym powinien obsługiwać wszystkie wzorce wymiany komunikatów. Jednak podstawowe funkcje kanału są takie same, niezależnie od ich struktury komunikacji. Dokładniej niż w przypadku klienta należy napisać identyfikator kontekstu do komunikatów i z usługi, który powinien odczytać ten identyfikator kontekstu z komunikatów i przekazać go do górnego poziomu. Z tego powodu `DurableInstanceContextChannelBase` Klasa jest tworzona, która działa jako abstrakcyjna klasa bazowa dla wszystkich implementacji trwałego kanału kontekstu wystąpienia. Ta klasa zawiera funkcje zarządzania komputerem o wspólnym stanie oraz dwóch chronionych elementów członkowskich do zastosowania i odczytu informacji kontekstowych do i z komunikatów.

```csharp
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

Te dwie metody wykorzystują `IContextManager` implementacje do zapisu i odczytywania identyfikatora kontekstu do lub z wiadomości. (`IContextManager` jest interfejsem niestandardowym używanym do definiowania kontraktu dla wszystkich menedżerów kontekstu). Kanał może zawierać identyfikator kontekstu w niestandardowym nagłówku protokołu SOAP lub w nagłówku pliku cookie protokołu HTTP. Każda implementacja Menedżera kontekstu dziedziczy z `ContextManagerBase` klasy, która zawiera typowe funkcje dla wszystkich menedżerów kontekstu. `GetContextId` Metoda w tej klasie jest używana do pochodzenie identyfikatora kontekstu od klienta. Gdy identyfikator kontekstu pochodzi po raz pierwszy, ta metoda zapisuje je w pliku tekstowym, którego nazwa jest zbudowana przez zdalny adres punktu końcowego (nieprawidłowe znaki nazwy pliku w typowych identyfikatorach URI są zastępowane znakami @).

Później, gdy identyfikator kontekstu jest wymagany dla tego samego zdalnego punktu końcowego, sprawdza, czy odpowiedni plik istnieje. W takim przypadku odczytuje identyfikator kontekstu i zwraca. W przeciwnym razie zwraca nowo wygenerowany identyfikator kontekstu i zapisuje go do pliku. W przypadku konfiguracji domyślnej te pliki są umieszczane w katalogu o nazwie ContextStore, który znajduje się w katalogu tymczasowym bieżącego użytkownika. Jednak tę lokalizację można skonfigurować przy użyciu elementu Binding.

Mechanizm służący do transportowania identyfikatora kontekstu można skonfigurować. Może być zapisany w nagłówku pliku cookie HTTP lub do niestandardowego nagłówka SOAP. Podejście niestandardowego nagłówka SOAP umożliwia korzystanie z tego protokołu z protokołami innymi niż HTTP (na przykład TCP lub nazwane potoki). Istnieją dwie klasy, a mianowicie `MessageHeaderContextManager` i `HttpCookieContextManager`, które implementują te dwie opcje.

Oba z nich zapisują odpowiednio identyfikator kontekstu do wiadomości. Na przykład `MessageHeaderContextManager` Klasa zapisuje ją w NAGŁÓWKU protokołu SOAP w `WriteContext` metodzie.

```csharp
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

Obie metody `ApplyContext` i `ReadContextId` w `DurableInstanceContextChannelBase` klasie wywołują odpowiednio `IContextManager.ReadContext` i. `IContextManager.WriteContext` Jednak te Menedżery kontekstu nie są tworzone bezpośrednio przez `DurableInstanceContextChannelBase` klasę. Zamiast tego używa `ContextManagerFactory` klasy do wykonania tego zadania.

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

`ApplyContext` Metoda jest wywoływana przez kanały wysyłania. Wprowadza identyfikator kontekstu do wiadomości wychodzących. `ReadContextId` Metoda jest wywoływana przez kanały odbierające. Ta metoda zapewnia, że identyfikator kontekstu jest dostępny w wiadomościach przychodzących i dodaje go do `Properties` kolekcji `Message` klasy. Zgłasza również `CommunicationException` w przypadku awarii odczytywanie identyfikatora kontekstu, a tym samym powoduje przerwanie działania kanału.

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

Przed kontynuowaniem należy zrozumieć użycie `Properties` kolekcji w `Message` klasie. Zazwyczaj ta `Properties` kolekcja jest używana podczas przekazywania danych z niższych do górnych poziomów z warstwy kanału. W ten sposób wymagane dane można zapewnić na górne poziomy w spójny sposób, niezależnie od szczegółów protokołu. Innymi słowy Warstwa kanału może wysyłać i odbierać identyfikator kontekstu jako nagłówek protokołu SOAP lub nagłówek pliku cookie protokołu HTTP. Nie jest jednak konieczne, aby poznać te szczegóły na górnych poziomach, ponieważ warstwa kanału udostępnia te informacje w `Properties` kolekcji.

Teraz z `DurableInstanceContextChannelBase` klasą w miejscu należy zaimplementować wszystkie dziesięć niezbędnych interfejsów (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel). Są one podobne do wszystkich dostępnych wzorców wymiany komunikatów (datagram, jednostronne, dupleks i ich wariantów sesji). Każda z tych implementacji dziedziczy opisywaną wcześniej klasę bazową, `ApplyContext` a `ReadContextId` następnie wywołuje i odpowiednio. Na przykład, `DurableInstanceContextOutputChannel` który implementuje interfejs IOutputChannel — wywołuje `ApplyContext` metodę z każdej metody, która wysyła komunikaty.

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

Z drugiej strony — który `DurableInstanceContextInputChannel` implementuje `IInputChannel` interfejs — wywołuje `ReadContextId` metodę w każdej metodzie, która odbiera komunikaty.

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

Niezależnie od tego te implementacje kanałów delegują wywołania metod do kanału poniżej w stosie kanału. Jednak warianty sesji mają podstawową logikę, aby upewnić się, że identyfikator kontekstu jest wysyłany i jest tylko do odczytu dla pierwszej wiadomości, która powoduje utworzenie sesji.

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

Te implementacje kanałów są następnie dodawane do środowiska uruchomieniowego kanału WCF `DurableInstanceContextBindingElement` zgodnie z `DurableInstanceContextBindingElementSection` odpowiednio klasą i klasą. Więcej informacji na temat elementów powiązania i elementów powiązania można znaleźć w dokumentacji przykładowej kanału [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) .

## <a name="service-model-layer-extensions"></a>Rozszerzenia warstwy modelu usług

Teraz, gdy identyfikator kontekstu został przesłany przez warstwę kanału, można zaimplementować zachowanie usługi, aby dostosować Tworzenie wystąpienia. W tym przykładzie Menedżer magazynu jest używany do ładowania i zapisywania stanu z lub do magazynu trwałego. Jak wyjaśniono wcześniej, ten przykład udostępnia Menedżera magazynu, który używa SQL Server 2005 jako magazynu zapasowego. Można jednak dodać do tego rozszerzenia niestandardowe mechanizmy pamięci masowej. Aby to zrobić, należy zadeklarować interfejs publiczny, który musi zostać zaimplementowany przez wszystkich menedżerów magazynu.

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

`SqlServerStorageManager` Klasa zawiera implementację domyślną `IStorageManager` . W swojej `SaveInstance` metodzie dany obiekt jest serializowany przy użyciu elementu XmlSerializer i jest zapisywany w bazie danych SQL Server.

```csharp
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

W `GetInstance` metodzie odczytane są dane serializowane dla danego identyfikatora kontekstu, a obiekt zbudowany z niego jest zwracany do obiektu wywołującego.

```csharp
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

Użytkownicy tych menedżerów magazynu nie muszą bezpośrednio tworzyć wystąpień. Używają `StorageManagerFactory` klasy, które są abstrakcyjne ze szczegółowych informacji o tworzeniu Menedżera magazynu. Ta klasa ma jeden statyczny element `GetStorageManager`członkowski, który tworzy wystąpienie danego typu Menedżera magazynu. Jeśli parametr type ma `null`wartość, ta metoda tworzy wystąpienie klasy domyślnej `SqlServerStorageManager` i zwraca ją. Sprawdza również poprawność danego typu, aby upewnić się, że `IStorageManager` implementuje interfejs.

```csharp
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

Zaimplementowano niezbędną infrastrukturę do odczytu i zapisu wystąpień z magazynu trwałego. Teraz należy wykonać niezbędne kroki w celu zmiany zachowania usługi.

Pierwszym krokiem tego procesu jest zapisanie identyfikatora kontekstu, który pochodzi z warstwy kanału do bieżącej klasy InstanceContext. InstanceContext to składnik środowiska uruchomieniowego, który działa jako link między dyspozytorem programu WCF i wystąpieniem usługi. Może służyć do zapewnienia dodatkowego stanu i zachowania do wystąpienia usługi. Jest to niezbędne, ponieważ podczas komunikacji z sesją identyfikator kontekstu jest wysyłany tylko z pierwszą wiadomością.

Usługa WCF pozwala rozszerzyć swój składnik środowiska uruchomieniowego InstanceContext przez dodanie nowego stanu i zachowania przy użyciu jego wzorca rozszerzalnych obiektów. Rozszerzalny wzór obiektu jest używany w programie WCF do rozszerzania istniejących klas środowiska uruchomieniowego o nowe funkcje lub do dodawania nowych funkcji stanu do obiektu. W wzorcu rozszerzalnych obiektów istnieją trzy interfejsy — Interfejs IExtensibleObject\<t>, IExtension\<t> i IExtensionCollection\<t>:

- Interfejs Interfejs IExtensibleObject\<T> jest implementowany przez obiekty, które umożliwiają dostosowanie ich funkcjonalności.

- Interfejs IExtension\<T> jest implementowany przez obiekty, które są rozszerzeniami klas typu T.

- Interfejs IExtensionCollection\<T> jest kolekcją IExtensions, która umożliwia pobieranie IExtensions według ich typu.

W związku z tym należy utworzyć klasę InstanceContextExtension, która implementuje interfejs IExtension i definiuje stan wymagany do zapisania identyfikatora kontekstu. Ta klasa udostępnia również stan przechowywania używanego Menedżera magazynu. Po zapisaniu nowego stanu nie powinno być możliwe jego zmodyfikowanie. W związku z tym stan jest dostarczany i zapisywany w wystąpieniu podczas jego konstruowania, a następnie dostępny tylko przy użyciu właściwości tylko do odczytu.

```csharp
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

Klasa InstanceContextInitializer implementuje interfejs IInstanceContextInitializer i dodaje rozszerzenie kontekstu wystąpienia do kolekcji rozszerzeń dla konstruowanej metody InstanceContext.

```csharp
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

Zgodnie z wcześniejszym opisem identyfikator kontekstu jest odczytywany `Properties` z kolekcji `Message` klasy i przekazywać do konstruktora klasy rozszerzenia. Pokazuje to, jak informacje mogą być wymieniane między warstwami w spójny sposób.

Następnym ważnym krokiem jest zastąpienie procesu tworzenia wystąpienia usługi. Usługa WCF umożliwia wdrażanie niestandardowych zachowań tworzenia wystąpień i przełączanie ich do środowiska uruchomieniowego przy użyciu interfejsu IInstanceProvider. Nowa `InstanceProvider` Klasa została zaimplementowana w celu wykonania tego zadania. W konstruktorze oczekiwano typu usługi od dostawcy wystąpień. W dalszej części tego służy do tworzenia nowych wystąpień. W `GetInstance` implementacji jest tworzone wystąpienie Menedżera magazynu, w którym jest wyszukiwane utrwalone wystąpienie. Jeśli zwróci `null` , nowe wystąpienie typu usługi jest tworzone i zwracane do obiektu wywołującego.

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

Następnym ważnym krokiem jest zainstalowanie `InstanceContextExtension`klas `InstanceContextInitializer` i `InstanceProvider` w środowisku uruchomieniowym modelu usług. Atrybut niestandardowy może służyć do oznaczania klas implementacji usługi, aby można było zainstalować zachowanie. `DurableInstanceContextAttribute` Zawiera implementację tego atrybutu i implementuje `IServiceBehavior` interfejs, aby zwiększyć cały czas wykonywania usługi.

Ta klasa ma właściwość akceptującą typ Menedżera magazynu, który ma być używany. W ten sposób implementacja umożliwia użytkownikom określenie własnych `IStorageManager` implementacji jako parametru tego atrybutu.

W `ApplyDispatchBehavior` implementacji `InstanceContextMode` bieżące `ServiceBehavior` atrybuty są weryfikowane. Jeśli ta właściwość jest ustawiona na wartość singleton, włączenie trwałego wystąpienia nie jest możliwe `InvalidOperationException` i zostanie zgłoszone w celu powiadomienia hosta.

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

Po wykonaniu tych wystąpień Menedżer magazynu, inicjator kontekstu wystąpienia i dostawca wystąpienia zostaną utworzone i zainstalowane w `DispatchRuntime` każdym punkcie końcowym.

```csharp
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

W skrócie do tej pory ten przykład wygenerował kanał, który włączył niestandardowy protokół transmisji do niestandardowego identyfikatora kontekstu, a także zastępuje domyślne zachowanie tworzenia wystąpienia w celu załadowania wystąpień z magazynu trwałego.

Po lewej stronie jest sposób zapisania wystąpienia usługi w magazynie trwałym. Jak wspomniano wcześniej, istnieje już wymagana funkcja, która umożliwia zapisanie stanu w `IStorageManager` implementacji. Teraz należy zintegrować ją z środowiskiem uruchomieniowym WCF. Wymagany jest inny atrybut, który ma zastosowanie do metod w klasie implementacji usługi. Ten atrybut powinien zostać zastosowany do metod, które zmieniają stan wystąpienia usługi.

`SaveStateAttribute` Klasa implementuje tę funkcję. Implementuje `IOperationBehavior` także klasę, aby zmodyfikować środowisko uruchomieniowe WCF dla każdej operacji. Gdy metoda jest oznaczona za pomocą tego atrybutu, środowisko uruchomieniowe WCF wywołuje `ApplyBehavior` metodę w trakcie `DispatchOperation` konstruowania. W tej implementacji metody istnieje pojedynczy wiersz kodu:

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

Ta instrukcja tworzy wystąpienie `OperationInvoker` typu i przypisuje je do `Invoker` właściwości, która `DispatchOperation` jest tworzona. `OperationInvoker` Klasa jest otoką dla operacji domyślnej Źródło utworzonej dla elementu `DispatchOperation`. Ta klasa implementuje `IOperationInvoker` interfejs. W implementacji `Invoke` metody rzeczywiste wywołanie metody jest delegowane do wewnętrznej operacji źródło. Jednak przed zwróceniem wyników Menedżer magazynu w programie `InstanceContext` jest używany do zapisania wystąpienia usługi.

```csharp
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

Zarówno Warstwa kanału, jak i rozszerzenia warstwy modelu usług są gotowe i mogą być używane w aplikacjach WCF. Usługi muszą dodać kanał do stosu kanału przy użyciu niestandardowego powiązania, a następnie oznaczyć klasy implementacji usługi odpowiednimi atrybutami.

```csharp
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

Aplikacje klienckie muszą dodać DurableInstanceContextChannel do stosu kanału przy użyciu niestandardowego powiązania. Aby skonfigurować kanał w sposób deklaratywny w pliku konfiguracji, należy dodać sekcję elementu powiązania do kolekcji rozszerzeń elementów powiązania.

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

Teraz element Binding może być używany z powiązaniem niestandardowym, podobnie jak inne standardowe elementy powiązania:

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

## <a name="conclusion"></a>Podsumowanie

Ten przykład przedstawia sposób tworzenia niestandardowego kanału protokołu i dostosowywania zachowania usługi, aby je włączyć.

Rozszerzenie można ulepszyć, umożliwiając użytkownikom określenie `IStorageManager` implementacji przy użyciu sekcji konfiguracji. Dzięki temu można zmodyfikować magazyn zapasowy bez ponownego kompilowania kodu usługi.

Ponadto można spróbować zaimplementować klasę (na przykład `StateBag`), która hermetyzuje stan wystąpienia. Ta klasa jest odpowiedzialna za utrwalanie stanu przy każdej zmianie. W `SaveState` ten sposób można uniknąć użycia atrybutu i bardziej precyzyjnie wykonywać działania utrwalania (na przykład można zachować stan, gdy stan zostanie rzeczywiście zmieniony, zamiast zapisywać go przy każdym wywołaniu metody z `SaveState` atrybutem).

Po uruchomieniu przykładu wyświetlane są następujące dane wyjściowe. Klient dodaje dwa elementy do koszyka zakupów, a następnie pobiera listę elementów w koszyku zakupów z usługi. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> Ponowne kompilowanie usługi zastępuje plik bazy danych. Aby obserwować stan zachowany przez wiele przebiegów próbki, pamiętaj, aby nie ponownie skompilować przykład między przebiegami.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!NOTE]
> Aby uruchomić ten przykład, musisz mieć uruchomioną SQL Server 2005 lub SQL Express 2005. W przypadku korzystania z SQL Server 2005 należy zmodyfikować konfigurację parametrów połączenia usługi. W przypadku uruchamiania wielu komputerów SQL Server jest wymagana tylko na komputerze serwera.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
