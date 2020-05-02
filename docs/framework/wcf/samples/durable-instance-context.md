---
title: Kontekst niezawodnej instancji
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: d70617fef7ebe0a94e22e858ee403d5d4f1840e3
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728407"
---
# <a name="durable-instance-context"></a><span data-ttu-id="a3e06-102">Kontekst niezawodnej instancji</span><span class="sxs-lookup"><span data-stu-id="a3e06-102">Durable Instance Context</span></span>

<span data-ttu-id="a3e06-103">Ten przykład pokazuje, jak dostosować środowisko uruchomieniowe programu Windows Communication Foundation (WCF) w celu włączenia trwałych kontekstów wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a3e06-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="a3e06-104">Używa SQL Server 2005 jako magazynu zapasowego (w tym przypadku SQL Server 2005 Express).</span><span class="sxs-lookup"><span data-stu-id="a3e06-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="a3e06-105">Zapewnia również sposób dostępu do niestandardowych mechanizmów magazynowania.</span><span class="sxs-lookup"><span data-stu-id="a3e06-105">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="a3e06-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a3e06-107">Ten przykład obejmuje Rozszerzanie warstwy kanału i warstwy modelu usług WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e06-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="a3e06-108">W związku z tym należy zrozumieć podstawowe koncepcje przed przejściem do szczegółów implementacji.</span><span class="sxs-lookup"><span data-stu-id="a3e06-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="a3e06-109">Nietrwałe konteksty wystąpień można często znaleźć w rzeczywistych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="a3e06-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="a3e06-110">Aplikacja koszyka, na przykład, ma możliwość wstrzymania zakupów w połowie i kontynuowania w innym dniu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-110">A shopping cart application, for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="a3e06-111">W związku z tym, gdy będziemy odwiedzać koszyk następnym dniem, zostanie przywrócony oryginalny kontekst.</span><span class="sxs-lookup"><span data-stu-id="a3e06-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="a3e06-112">Należy pamiętać, że aplikacja koszyka zakupów (na serwerze) nie utrzymuje wystąpienia koszyka zakupów, gdy nastąpi odłączenie.</span><span class="sxs-lookup"><span data-stu-id="a3e06-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="a3e06-113">Zamiast tego zachowuje swój stan w postaci trwałego nośnika magazynu i używa go podczas konstruowania nowego wystąpienia dla przywróconego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="a3e06-114">W związku z tym wystąpienie usługi, które może być usługą dla tego samego kontekstu, nie jest takie samo jak poprzednie wystąpienie (to oznacza, że nie ma tego samego adresu pamięci).</span><span class="sxs-lookup"><span data-stu-id="a3e06-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="a3e06-115">Trwały kontekst wystąpienia jest możliwy przez niewielki protokół, który wymienia identyfikator kontekstu między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="a3e06-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="a3e06-116">Ten identyfikator kontekstu jest tworzony na kliencie i przesyłany do usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="a3e06-117">Po utworzeniu wystąpienia usługi środowisko uruchomieniowe programu próbuje załadować stan trwały, który odnosi się do tego identyfikatora kontekstu z magazynu trwałego (domyślnie jest to baza danych SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="a3e06-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="a3e06-118">Jeśli żaden stan nie jest dostępny, nowe wystąpienie ma stan domyślny.</span><span class="sxs-lookup"><span data-stu-id="a3e06-118">If no state is available, the new instance has its default state.</span></span> <span data-ttu-id="a3e06-119">Implementacja usługi używa atrybutu niestandardowego do oznaczania operacji, które zmieniają stan implementacji usługi, aby środowisko uruchomieniowe mógł zapisać wystąpienie usługi po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="a3e06-120">Zgodnie z powyższym opisem, dwa kroki można łatwo rozróżnić, aby osiągnąć cel:</span><span class="sxs-lookup"><span data-stu-id="a3e06-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="a3e06-121">Zmień komunikat, który przechodzi do sieci, aby przenieść identyfikator kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-121">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="a3e06-122">Zmień lokalne zachowanie usługi, aby zaimplementować logikę wystąpień niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a3e06-122">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="a3e06-123">Ponieważ pierwszy na liście ma wpływ na komunikaty w sieci, powinien zostać zaimplementowany jako kanał niestandardowy i podłączony do warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="a3e06-123">Because the first one in the list affects the messages on the wire, it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="a3e06-124">Ta ostatnia ma wpływ tylko na lokalne zachowanie usługi i dlatego można ją zaimplementować, rozszerzając kilka punktów rozszerzalności usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="a3e06-125">W następnych sekcjach omówiono wszystkie te rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a3e06-125">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="a3e06-126">Trwały kanał InstanceContext</span><span class="sxs-lookup"><span data-stu-id="a3e06-126">Durable InstanceContext Channel</span></span>

<span data-ttu-id="a3e06-127">Pierwszym krokiem, aby sprawdzić, jest rozszerzenie warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="a3e06-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="a3e06-128">Pierwszym krokiem w pisaniu niestandardowego kanału jest podjęcie decyzji dotyczącej struktury komunikacji kanału.</span><span class="sxs-lookup"><span data-stu-id="a3e06-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="a3e06-129">Gdy jest wprowadzany nowy protokół sieci, kanał powinien współpracować z niemal każdym innym kanałem w stosie kanałów.</span><span class="sxs-lookup"><span data-stu-id="a3e06-129">As a new wire protocol is being introduced, the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="a3e06-130">W związku z tym powinien obsługiwać wszystkie wzorce wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a3e06-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="a3e06-131">Jednak podstawowe funkcje kanału są takie same, niezależnie od ich struktury komunikacji.</span><span class="sxs-lookup"><span data-stu-id="a3e06-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="a3e06-132">Dokładniej niż w przypadku klienta należy napisać identyfikator kontekstu do komunikatów i z usługi, który powinien odczytać ten identyfikator kontekstu z komunikatów i przekazać go do górnego poziomu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="a3e06-133">Z tego powodu `DurableInstanceContextChannelBase` Klasa jest tworzona, która działa jako abstrakcyjna klasa bazowa dla wszystkich implementacji trwałego kanału kontekstu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a3e06-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="a3e06-134">Ta klasa zawiera funkcje zarządzania komputerem o wspólnym stanie oraz dwóch chronionych elementów członkowskich do zastosowania i odczytu informacji kontekstowych do i z komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a3e06-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

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

<span data-ttu-id="a3e06-135">Te dwie metody wykorzystują `IContextManager` implementacje do zapisu i odczytywania identyfikatora kontekstu do lub z wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a3e06-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="a3e06-136">(`IContextManager` jest interfejsem niestandardowym używanym do definiowania kontraktu dla wszystkich menedżerów kontekstu). Kanał może zawierać identyfikator kontekstu w niestandardowym nagłówku protokołu SOAP lub w nagłówku pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="a3e06-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in an HTTP cookie header.</span></span> <span data-ttu-id="a3e06-137">Każda implementacja Menedżera kontekstu dziedziczy z `ContextManagerBase` klasy, która zawiera typowe funkcje dla wszystkich menedżerów kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="a3e06-138">`GetContextId` Metoda w tej klasie jest używana do pochodzenie identyfikatora kontekstu od klienta.</span><span class="sxs-lookup"><span data-stu-id="a3e06-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="a3e06-139">Gdy identyfikator kontekstu pochodzi po raz pierwszy, ta metoda zapisuje je w pliku tekstowym, którego nazwa jest zbudowana przez zdalny adres punktu końcowego (nieprawidłowe znaki nazwy pliku w typowych identyfikatorach URI są zastępowane znakami @).</span><span class="sxs-lookup"><span data-stu-id="a3e06-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="a3e06-140">Później, gdy identyfikator kontekstu jest wymagany dla tego samego zdalnego punktu końcowego, sprawdza, czy odpowiedni plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="a3e06-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="a3e06-141">W takim przypadku odczytuje identyfikator kontekstu i zwraca.</span><span class="sxs-lookup"><span data-stu-id="a3e06-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="a3e06-142">W przeciwnym razie zwraca nowo wygenerowany identyfikator kontekstu i zapisuje go do pliku.</span><span class="sxs-lookup"><span data-stu-id="a3e06-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="a3e06-143">W przypadku konfiguracji domyślnej te pliki są umieszczane w katalogu o nazwie ContextStore, który znajduje się w katalogu tymczasowym bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a3e06-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user's temp directory.</span></span> <span data-ttu-id="a3e06-144">Jednak tę lokalizację można skonfigurować przy użyciu elementu Binding.</span><span class="sxs-lookup"><span data-stu-id="a3e06-144">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="a3e06-145">Mechanizm służący do transportowania identyfikatora kontekstu można skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="a3e06-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="a3e06-146">Może być zapisany w nagłówku pliku cookie HTTP lub do niestandardowego nagłówka SOAP.</span><span class="sxs-lookup"><span data-stu-id="a3e06-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="a3e06-147">Podejście niestandardowego nagłówka SOAP umożliwia korzystanie z tego protokołu z protokołami innymi niż HTTP (na przykład TCP lub nazwane potoki).</span><span class="sxs-lookup"><span data-stu-id="a3e06-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="a3e06-148">Istnieją dwie klasy, a mianowicie `MessageHeaderContextManager` i `HttpCookieContextManager`, które implementują te dwie opcje.</span><span class="sxs-lookup"><span data-stu-id="a3e06-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="a3e06-149">Oba z nich zapisują odpowiednio identyfikator kontekstu do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a3e06-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="a3e06-150">Na przykład `MessageHeaderContextManager` Klasa zapisuje ją w NAGŁÓWKU protokołu SOAP w `WriteContext` metodzie.</span><span class="sxs-lookup"><span data-stu-id="a3e06-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

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

<span data-ttu-id="a3e06-151">Obie metody `ApplyContext` i `ReadContextId` w `DurableInstanceContextChannelBase` klasie wywołują odpowiednio `IContextManager.ReadContext` i. `IContextManager.WriteContext`</span><span class="sxs-lookup"><span data-stu-id="a3e06-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="a3e06-152">Jednak te Menedżery kontekstu nie są tworzone bezpośrednio przez `DurableInstanceContextChannelBase` klasę.</span><span class="sxs-lookup"><span data-stu-id="a3e06-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="a3e06-153">Zamiast tego używa `ContextManagerFactory` klasy do wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="a3e06-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="a3e06-154">`ApplyContext` Metoda jest wywoływana przez kanały wysyłania.</span><span class="sxs-lookup"><span data-stu-id="a3e06-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="a3e06-155">Wprowadza identyfikator kontekstu do wiadomości wychodzących.</span><span class="sxs-lookup"><span data-stu-id="a3e06-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="a3e06-156">`ReadContextId` Metoda jest wywoływana przez kanały odbierające.</span><span class="sxs-lookup"><span data-stu-id="a3e06-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="a3e06-157">Ta metoda zapewnia, że identyfikator kontekstu jest dostępny w wiadomościach przychodzących i dodaje go do `Properties` kolekcji `Message` klasy.</span><span class="sxs-lookup"><span data-stu-id="a3e06-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="a3e06-158">Zgłasza również `CommunicationException` w przypadku awarii odczytywanie identyfikatora kontekstu, a tym samym powoduje przerwanie działania kanału.</span><span class="sxs-lookup"><span data-stu-id="a3e06-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="a3e06-159">Przed kontynuowaniem należy zrozumieć użycie `Properties` kolekcji w `Message` klasie.</span><span class="sxs-lookup"><span data-stu-id="a3e06-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="a3e06-160">Zazwyczaj ta `Properties` kolekcja jest używana podczas przekazywania danych z niższych do górnych poziomów z warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="a3e06-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="a3e06-161">W ten sposób wymagane dane można zapewnić na górne poziomy w spójny sposób, niezależnie od szczegółów protokołu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="a3e06-162">Innymi słowy Warstwa kanału może wysyłać i odbierać identyfikator kontekstu jako nagłówek protokołu SOAP lub nagłówek HTTP cookie.</span><span class="sxs-lookup"><span data-stu-id="a3e06-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or an HTTP cookie header.</span></span> <span data-ttu-id="a3e06-163">Nie jest jednak konieczne, aby poznać te szczegóły na górnych poziomach, ponieważ warstwa kanału udostępnia te informacje w `Properties` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a3e06-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="a3e06-164">Teraz z `DurableInstanceContextChannelBase` klasą w miejscu należy zaimplementować wszystkie dziesięć niezbędnych interfejsów (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel).</span><span class="sxs-lookup"><span data-stu-id="a3e06-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="a3e06-165">Są one podobne do wszystkich dostępnych wzorców wymiany komunikatów (datagram, jednostronne, dupleks i ich wariantów sesji).</span><span class="sxs-lookup"><span data-stu-id="a3e06-165">They resemble every available message exchange pattern (datagram, simplex, duplex, and their sessionful variants).</span></span> <span data-ttu-id="a3e06-166">Każda z tych implementacji dziedziczy klasę bazową opisaną wcześniej i wywołuje `ApplyContext` i `ReadContextId` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a3e06-166">Each of these implementations inherits the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="a3e06-167">Na przykład, `DurableInstanceContextOutputChannel` który implementuje interfejs IOutputChannel — wywołuje `ApplyContext` metodę z każdej metody, która wysyła komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a3e06-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="a3e06-168">Z drugiej strony `DurableInstanceContextInputChannel` — który implementuje `IInputChannel` interfejs — wywołuje `ReadContextId` metodę w każdej metodzie, która odbiera komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a3e06-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method, which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="a3e06-169">Niezależnie od tego te implementacje kanałów delegują wywołania metod do kanału poniżej w stosie kanału.</span><span class="sxs-lookup"><span data-stu-id="a3e06-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="a3e06-170">Jednak warianty sesji mają podstawową logikę, aby upewnić się, że identyfikator kontekstu jest wysyłany i jest tylko do odczytu dla pierwszej wiadomości, która powoduje utworzenie sesji.</span><span class="sxs-lookup"><span data-stu-id="a3e06-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="a3e06-171">Te implementacje kanałów są następnie dodawane do środowiska uruchomieniowego kanału WCF `DurableInstanceContextBindingElement` zgodnie z `DurableInstanceContextBindingElementSection` odpowiednio klasą i klasą.</span><span class="sxs-lookup"><span data-stu-id="a3e06-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="a3e06-172">Więcej informacji na temat elementów powiązania i elementów powiązania można znaleźć w dokumentacji przykładowej kanału [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) .</span><span class="sxs-lookup"><span data-stu-id="a3e06-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="a3e06-173">Rozszerzenia warstwy modelu usług</span><span class="sxs-lookup"><span data-stu-id="a3e06-173">Service Model Layer Extensions</span></span>

<span data-ttu-id="a3e06-174">Teraz, gdy identyfikator kontekstu został przesłany przez warstwę kanału, można zaimplementować zachowanie usługi, aby dostosować Tworzenie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a3e06-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="a3e06-175">W tym przykładzie Menedżer magazynu jest używany do ładowania i zapisywania stanu z lub do magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="a3e06-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="a3e06-176">Jak wyjaśniono wcześniej, ten przykład udostępnia Menedżera magazynu, który używa SQL Server 2005 jako magazynu zapasowego.</span><span class="sxs-lookup"><span data-stu-id="a3e06-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="a3e06-177">Można jednak dodać do tego rozszerzenia niestandardowe mechanizmy pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="a3e06-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="a3e06-178">Aby to zrobić, należy zadeklarować interfejs publiczny, który musi zostać zaimplementowany przez wszystkich menedżerów magazynu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="a3e06-179">`SqlServerStorageManager` Klasa zawiera implementację domyślną `IStorageManager` .</span><span class="sxs-lookup"><span data-stu-id="a3e06-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="a3e06-180">W swojej `SaveInstance` metodzie dany obiekt jest serializowany przy użyciu elementu XmlSerializer i jest zapisywany w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3e06-180">In its `SaveInstance` method, the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

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

<span data-ttu-id="a3e06-181">W `GetInstance` metodzie dane serializowane są odczytywane dla danego identyfikatora kontekstu, a obiekt zbudowany z niego jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a3e06-181">In the `GetInstance` method, the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

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

<span data-ttu-id="a3e06-182">Użytkownicy tych menedżerów magazynu nie muszą bezpośrednio tworzyć wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a3e06-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="a3e06-183">Używają `StorageManagerFactory` klasy, które są abstrakcyjne ze szczegółowych informacji o tworzeniu Menedżera magazynu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="a3e06-184">Ta klasa ma jeden statyczny element `GetStorageManager`członkowski, który tworzy wystąpienie danego typu Menedżera magazynu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="a3e06-185">Jeśli parametr type ma `null`wartość, ta metoda tworzy wystąpienie klasy domyślnej `SqlServerStorageManager` i zwraca ją.</span><span class="sxs-lookup"><span data-stu-id="a3e06-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="a3e06-186">Sprawdza również poprawność danego typu, aby upewnić się, że `IStorageManager` implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="a3e06-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

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

<span data-ttu-id="a3e06-187">Zaimplementowano niezbędną infrastrukturę do odczytu i zapisu wystąpień z magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="a3e06-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="a3e06-188">Teraz należy wykonać niezbędne kroki w celu zmiany zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-188">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="a3e06-189">Pierwszym krokiem tego procesu jest zapisanie identyfikatora kontekstu, który pochodzi z warstwy kanału do bieżącej klasy InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="a3e06-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="a3e06-190">InstanceContext to składnik środowiska uruchomieniowego, który działa jako link między dyspozytorem programu WCF i wystąpieniem usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="a3e06-191">Może służyć do zapewnienia dodatkowego stanu i zachowania do wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="a3e06-192">Jest to niezbędne, ponieważ podczas komunikacji z sesją identyfikator kontekstu jest wysyłany tylko z pierwszą wiadomością.</span><span class="sxs-lookup"><span data-stu-id="a3e06-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="a3e06-193">Usługa WCF pozwala rozszerzyć swój składnik środowiska uruchomieniowego InstanceContext przez dodanie nowego stanu i zachowania przy użyciu jego wzorca rozszerzalnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a3e06-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="a3e06-194">Rozszerzalny wzór obiektu jest używany w programie WCF do rozszerzania istniejących klas środowiska uruchomieniowego o nowe funkcje lub do dodawania nowych funkcji stanu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="a3e06-195">W wzorcu rozszerzalnych obiektów istnieją trzy interfejsy — Interfejs IExtensibleObject\<t>, IExtension\<t> i IExtensionCollection\<t>:</span><span class="sxs-lookup"><span data-stu-id="a3e06-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="a3e06-196">Interfejs Interfejs IExtensibleObject\<T> jest implementowany przez obiekty, które umożliwiają dostosowanie ich funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="a3e06-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="a3e06-197">Interfejs IExtension\<T> jest implementowany przez obiekty, które są rozszerzeniami klas typu T.</span><span class="sxs-lookup"><span data-stu-id="a3e06-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="a3e06-198">Interfejs IExtensionCollection\<T> jest kolekcją IExtensions, która umożliwia pobieranie IExtensions według ich typu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="a3e06-199">W związku z tym należy utworzyć klasę InstanceContextExtension, która implementuje interfejs IExtension i definiuje stan wymagany do zapisania identyfikatora kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="a3e06-200">Ta klasa udostępnia również stan przechowywania używanego Menedżera magazynu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="a3e06-201">Po zapisaniu nowego stanu nie powinno być możliwe jego zmodyfikowanie.</span><span class="sxs-lookup"><span data-stu-id="a3e06-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="a3e06-202">W związku z tym stan jest dostarczany i zapisywany w wystąpieniu podczas jego konstruowania, a następnie dostępny tylko przy użyciu właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

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

<span data-ttu-id="a3e06-203">Klasa InstanceContextInitializer implementuje interfejs IInstanceContextInitializer i dodaje rozszerzenie kontekstu wystąpienia do kolekcji rozszerzeń dla konstruowanej metody InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="a3e06-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

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

<span data-ttu-id="a3e06-204">Zgodnie z wcześniejszym opisem identyfikator kontekstu jest odczytywany `Properties` z kolekcji `Message` klasy i przekazywać do konstruktora klasy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a3e06-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="a3e06-205">Pokazuje to, jak informacje mogą być wymieniane między warstwami w spójny sposób.</span><span class="sxs-lookup"><span data-stu-id="a3e06-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="a3e06-206">Następnym ważnym krokiem jest zastąpienie procesu tworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="a3e06-207">Usługa WCF umożliwia wdrażanie niestandardowych zachowań tworzenia wystąpień i przełączanie ich do środowiska uruchomieniowego przy użyciu interfejsu IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="a3e06-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="a3e06-208">Nowa `InstanceProvider` Klasa została zaimplementowana w celu wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="a3e06-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="a3e06-209">Typ usługi oczekiwany przez dostawcę wystąpienia jest akceptowany w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="a3e06-209">The service type expected from the instance provider is accepted in the constructor.</span></span> <span data-ttu-id="a3e06-210">W dalszej części tego służy do tworzenia nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a3e06-210">Later this is used to create new instances.</span></span> <span data-ttu-id="a3e06-211">W `GetInstance` implementacji zostanie utworzone wystąpienie Menedżera magazynu z wyszukiwaniem utrwalonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a3e06-211">In the `GetInstance` implementation, an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="a3e06-212">W przypadku powrotu `null`zostanie utworzone nowe wystąpienie typu usługi i zwrócone do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a3e06-212">If it returns `null`, then a new instance of the service type is instantiated and returned to the caller.</span></span>

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

<span data-ttu-id="a3e06-213">Następnym ważnym krokiem jest zainstalowanie klas `InstanceContextExtension`, `InstanceContextInitializer`, i `InstanceProvider` w środowisku uruchomieniowym modelu usług.</span><span class="sxs-lookup"><span data-stu-id="a3e06-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer`, and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="a3e06-214">Atrybut niestandardowy może służyć do oznaczania klas implementacji usługi, aby można było zainstalować zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a3e06-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="a3e06-215">`DurableInstanceContextAttribute` Zawiera implementację tego atrybutu i implementuje `IServiceBehavior` interfejs, aby zwiększyć cały czas wykonywania usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="a3e06-216">Ta klasa ma właściwość akceptującą typ Menedżera magazynu, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="a3e06-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="a3e06-217">W ten sposób implementacja umożliwia użytkownikom określenie własnych `IStorageManager` implementacji jako parametru tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-217">In this way, the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="a3e06-218">W `ApplyDispatchBehavior` implementacji `InstanceContextMode` bieżący `ServiceBehavior` atrybut jest weryfikowany.</span><span class="sxs-lookup"><span data-stu-id="a3e06-218">In the `ApplyDispatchBehavior` implementation, the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="a3e06-219">Jeśli ta właściwość jest ustawiona na wartość singleton, włączenie trwałego wystąpienia nie jest możliwe `InvalidOperationException` i zostanie zgłoszone w celu powiadomienia hosta.</span><span class="sxs-lookup"><span data-stu-id="a3e06-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

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

<span data-ttu-id="a3e06-220">Po wykonaniu tych wystąpień Menedżer magazynu, inicjator kontekstu wystąpienia i dostawca wystąpienia zostaną utworzone i zainstalowane w `DispatchRuntime` każdym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="a3e06-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

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

<span data-ttu-id="a3e06-221">W skrócie do tej pory ten przykład wygenerował kanał, który włączył niestandardowy protokół transmisji do niestandardowego identyfikatora kontekstu, a także zastępuje domyślne zachowanie tworzenia wystąpienia w celu załadowania wystąpień z magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="a3e06-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="a3e06-222">Po lewej stronie jest sposób zapisania wystąpienia usługi w magazynie trwałym.</span><span class="sxs-lookup"><span data-stu-id="a3e06-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="a3e06-223">Jak wspomniano wcześniej, istnieje już wymagana funkcja, która umożliwia zapisanie stanu w `IStorageManager` implementacji.</span><span class="sxs-lookup"><span data-stu-id="a3e06-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="a3e06-224">Teraz należy zintegrować ją z środowiskiem uruchomieniowym WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e06-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="a3e06-225">Wymagany jest inny atrybut, który ma zastosowanie do metod w klasie implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="a3e06-226">Ten atrybut powinien zostać zastosowany do metod, które zmieniają stan wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="a3e06-227">`SaveStateAttribute` Klasa implementuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="a3e06-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="a3e06-228">Implementuje `IOperationBehavior` także klasę, aby zmodyfikować środowisko uruchomieniowe WCF dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="a3e06-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="a3e06-229">Gdy metoda jest oznaczona za pomocą tego atrybutu, środowisko uruchomieniowe WCF wywołuje `ApplyBehavior` metodę w trakcie `DispatchOperation` konstruowania.</span><span class="sxs-lookup"><span data-stu-id="a3e06-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="a3e06-230">W tej implementacji metody istnieje pojedynczy wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="a3e06-230">There is a single line of code in this method implementation:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="a3e06-231">Ta instrukcja tworzy wystąpienie `OperationInvoker` typu i przypisuje je do `Invoker` właściwości, która `DispatchOperation` jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="a3e06-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="a3e06-232">`OperationInvoker` Klasa jest otoką dla operacji domyślnej Źródło utworzonej dla elementu `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="a3e06-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="a3e06-233">Ta klasa implementuje `IOperationInvoker` interfejs.</span><span class="sxs-lookup"><span data-stu-id="a3e06-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="a3e06-234">W implementacji `Invoke` metody rzeczywiste wywołanie metody jest delegowane do wewnętrznej operacji źródło.</span><span class="sxs-lookup"><span data-stu-id="a3e06-234">In the `Invoke` method implementation, the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="a3e06-235">Jednak przed zwróceniem wyników Menedżer magazynu w programie `InstanceContext` jest używany do zapisania wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

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

## <a name="using-the-extension"></a><span data-ttu-id="a3e06-236">Przy użyciu rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="a3e06-236">Using the Extension</span></span>

<span data-ttu-id="a3e06-237">Zarówno Warstwa kanału, jak i rozszerzenia warstwy modelu usług są gotowe i mogą być używane w aplikacjach WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e06-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="a3e06-238">Usługi muszą dodać kanał do stosu kanału przy użyciu niestandardowego powiązania, a następnie oznaczyć klasy implementacji usługi odpowiednimi atrybutami.</span><span class="sxs-lookup"><span data-stu-id="a3e06-238">Services must add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

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

<span data-ttu-id="a3e06-239">Aplikacje klienckie muszą dodać DurableInstanceContextChannel do stosu kanału przy użyciu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a3e06-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="a3e06-240">Aby skonfigurować kanał w sposób deklaratywny w pliku konfiguracji, należy dodać sekcję elementu powiązania do kolekcji rozszerzeń elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="a3e06-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

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

<span data-ttu-id="a3e06-241">Teraz element Binding może być używany z powiązaniem niestandardowym, podobnie jak inne standardowe elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="a3e06-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

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

## <a name="conclusion"></a><span data-ttu-id="a3e06-242">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="a3e06-242">Conclusion</span></span>

<span data-ttu-id="a3e06-243">Ten przykład przedstawia sposób tworzenia niestandardowego kanału protokołu i dostosowywania zachowania usługi, aby je włączyć.</span><span class="sxs-lookup"><span data-stu-id="a3e06-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="a3e06-244">Rozszerzenie można ulepszyć, umożliwiając użytkownikom określenie `IStorageManager` implementacji przy użyciu sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a3e06-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="a3e06-245">Dzięki temu można zmodyfikować magazyn zapasowy bez ponownego kompilowania kodu usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="a3e06-246">Ponadto można spróbować zaimplementować klasę (na przykład `StateBag`), która hermetyzuje stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a3e06-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="a3e06-247">Ta klasa jest odpowiedzialna za utrwalanie stanu przy każdej zmianie.</span><span class="sxs-lookup"><span data-stu-id="a3e06-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="a3e06-248">W `SaveState` ten sposób można uniknąć użycia atrybutu i bardziej precyzyjnie wykonywać działania utrwalania (na przykład można zachować stan, gdy stan zostanie rzeczywiście zmieniony, zamiast zapisywać go przy każdym wywołaniu metody z `SaveState` atrybutem).</span><span class="sxs-lookup"><span data-stu-id="a3e06-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="a3e06-249">Po uruchomieniu przykładu wyświetlane są następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a3e06-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="a3e06-250">Klient dodaje dwa elementy do koszyka zakupów, a następnie pobiera listę elementów w koszyku zakupów z usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="a3e06-251">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="a3e06-251">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="a3e06-252">Ponowne kompilowanie usługi zastępuje plik bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a3e06-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="a3e06-253">Aby obserwować stan zachowany przez wiele przebiegów próbki, pamiętaj, aby nie ponownie skompilować przykład między przebiegami.</span><span class="sxs-lookup"><span data-stu-id="a3e06-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a3e06-254">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a3e06-254">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a3e06-255">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3e06-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a3e06-256">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3e06-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="a3e06-257">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a3e06-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a3e06-258">Aby uruchomić ten przykład, musisz mieć uruchomioną SQL Server 2005 lub SQL Express 2005.</span><span class="sxs-lookup"><span data-stu-id="a3e06-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="a3e06-259">W przypadku korzystania z SQL Server 2005 należy zmodyfikować konfigurację parametrów połączenia usługi.</span><span class="sxs-lookup"><span data-stu-id="a3e06-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="a3e06-260">W przypadku uruchamiania wielu komputerów SQL Server jest wymagana tylko na komputerze serwera.</span><span class="sxs-lookup"><span data-stu-id="a3e06-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3e06-261">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a3e06-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a3e06-262">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a3e06-262">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a3e06-263">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a3e06-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a3e06-264">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a3e06-264">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
