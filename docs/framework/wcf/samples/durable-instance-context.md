---
title: Kontekst niezawodnej instancji
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 9981c4293f651bce3a0abaa3e0243d0d656ff257
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841454"
---
# <a name="durable-instance-context"></a><span data-ttu-id="412c8-102">Kontekst niezawodnej instancji</span><span class="sxs-lookup"><span data-stu-id="412c8-102">Durable Instance Context</span></span>
<span data-ttu-id="412c8-103">Niniejszy przykład pokazuje sposób dostosowywania środowiska uruchomieniowego Windows Communication Foundation (WCF), aby włączyć kontekst niezawodnej instancji.</span><span class="sxs-lookup"><span data-stu-id="412c8-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="412c8-104">Jako jej zapasowy magazyn (SQL Server 2005 Express w tym przypadku) używa programu SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="412c8-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="412c8-105">Jednak także zapewnia możliwość dostępu do magazynu niestandardowego mechanizmów.</span><span class="sxs-lookup"><span data-stu-id="412c8-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="412c8-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="412c8-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="412c8-107">Ten przykład obejmuje rozszerzanie warstwy kanału i warstwy modelu usług WCF.</span><span class="sxs-lookup"><span data-stu-id="412c8-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="412c8-108">Dlatego jest niezbędne do zrozumienia podstawowych pojęć przed przejściem do szczegółów implementacji.</span><span class="sxs-lookup"><span data-stu-id="412c8-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="412c8-109">Kontekst niezawodnej instancji znajdują się w rzeczywistych scenariuszach bardzo często.</span><span class="sxs-lookup"><span data-stu-id="412c8-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="412c8-110">Uwzględnić aplikację zakupową koszyka na przykład, ma możliwość wstrzymania widoczny w połowie zakupów za pośrednictwem i kontynuować kolejny dzień.</span><span class="sxs-lookup"><span data-stu-id="412c8-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="412c8-111">Dlatego, że gdy odwiedza koszyka następnego dnia, zostanie przywrócony naszych oryginalnego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="412c8-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="412c8-112">Należy zauważyć, że aplikacji koszyka zakupów, (na serwerze) nie są zachowywane wystąpienie koszyka zakupów podczas, gdy firma Microsoft jest odłączony.</span><span class="sxs-lookup"><span data-stu-id="412c8-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="412c8-113">Zamiast tego będzie się powtarzał stanu do nośnika trwałego magazynu i używa go podczas tworzenia nowego wystąpienia dla kontekstu przywrócona.</span><span class="sxs-lookup"><span data-stu-id="412c8-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="412c8-114">W związku z tym wystąpienie usługi, która może obsłużyć na tym samym kontekście nie jest taka sama jak poprzednie wystąpienie (oznacza to, że nie ma tego samego adresu pamięci).</span><span class="sxs-lookup"><span data-stu-id="412c8-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="412c8-115">Kontekst niezawodnej instancji jest możliwe dzięki małej protokołu, który wymienia identyfikator kontekstu między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="412c8-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="412c8-116">Ten identyfikator kontekstu jest tworzony na komputerze klienckim i przesyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="412c8-117">Po utworzeniu wystąpienia usługi, środowisko wykonawcze usług próbuje załadować utrwalonego stanu, który odnosi się do tego Identyfikatora kontekstu z magazynu trwałego (domyślnie jest bazę danych programu SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="412c8-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="412c8-118">Jeśli stan nie jest dostępne nowe wystąpienie ma stanu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="412c8-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="412c8-119">Implementacji usługi używa atrybutu niestandardowego, aby oznaczyć operacje, aby zmienić stan wdrożenia usługi, dzięki czemu środowisko uruchomieniowe można zapisać wystąpienia usługi po ich wywoływania.</span><span class="sxs-lookup"><span data-stu-id="412c8-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="412c8-120">Według opisu w poprzednich do osiągnięcia celu, łatwo można wyróżnić dwa kroki:</span><span class="sxs-lookup"><span data-stu-id="412c8-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1.  <span data-ttu-id="412c8-121">Zmienić komunikat, który przechodzi na potrzeby przesyłu, żeby identyfikator kontekstu.</span><span class="sxs-lookup"><span data-stu-id="412c8-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2.  <span data-ttu-id="412c8-122">Zmień zachowanie lokalnej usługi, aby zaimplementować logikę niestandardową wystąpień.</span><span class="sxs-lookup"><span data-stu-id="412c8-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="412c8-123">Ponieważ pierwszy z nich na liście ma wpływ na wiadomości na łączu powinny zostać wdrożone jako niestandardowy kanał i być podłączony do warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="412c8-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="412c8-124">Ten ostatni ma wpływ tylko na zachowanie lokalnej usługi i może być implementowana przez rozszerzenie kilka punktów rozszerzeń usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="412c8-125">W kolejnych sekcjach opisano każdy z tych rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="412c8-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="412c8-126">Trwałość InstanceContext kanału</span><span class="sxs-lookup"><span data-stu-id="412c8-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="412c8-127">Najpierw Przyjrzyj się to rozszerzenie warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="412c8-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="412c8-128">Pierwszym krokiem w niestandardowym kanale w pisaniu jest podjęcie decyzji, struktura komunikacji kanału.</span><span class="sxs-lookup"><span data-stu-id="412c8-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="412c8-129">Jak wprowadzono nowy protokół przewodowy kanał powinny współpracować z prawie każdego innego kanału w stosie kanału.</span><span class="sxs-lookup"><span data-stu-id="412c8-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="412c8-130">W związku z tym go powinien obsługiwać wszystkie wzorce wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="412c8-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="412c8-131">Jednak podstawowe funkcje kanału jest taki sam, niezależnie od jego strukturę komunikacji.</span><span class="sxs-lookup"><span data-stu-id="412c8-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="412c8-132">W szczególności od klienta jego powinien zapisać identyfikator kontekstu do wiadomości i z usługi należy przeczytać ten identyfikator kontekstu od wiadomości i przekazać go do wyższych poziomów.</span><span class="sxs-lookup"><span data-stu-id="412c8-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="412c8-133">Z tego powodu `DurableInstanceContextChannelBase` klasa jest tworzona, który działa jako abstrakcyjna klasa bazowa dla wszystkich implementacjach kanału kontekst niezawodnej instancji.</span><span class="sxs-lookup"><span data-stu-id="412c8-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="412c8-134">Ta klasa zawiera typowe funkcje zarządzania maszyny stanu i dwa chronionych elementów członkowskich, aby zastosować i przeczytaj informacje o kontekście do i z wiadomości.</span><span class="sxs-lookup"><span data-stu-id="412c8-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
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
  
 <span data-ttu-id="412c8-135">Te dwie metody użytkowania `IContextManager` implementacji do zapisu i odczytu identyfikator kontekstu do lub z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="412c8-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="412c8-136">(`IContextManager` jest niestandardowy interfejs używany do definiowania kontrakt dla wszystkich menedżerów kontekstu.) Kanał można dołączyć identyfikator kontekstu w niestandardowy nagłówek SOAP lub w nagłówku pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="412c8-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="412c8-137">Każda implementacja menedżera kontekstowego dziedziczy `ContextManagerBase` klasę, która zawiera funkcje wspólne dla wszystkich menedżerów kontekstu.</span><span class="sxs-lookup"><span data-stu-id="412c8-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="412c8-138">`GetContextId` Metody tej klasy jest używany tak, jakby pochodził identyfikator kontekstu od klienta.</span><span class="sxs-lookup"><span data-stu-id="412c8-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="412c8-139">Jeśli kontekst, w których identyfikator jest tworzone po raz pierwszy, ta metoda zapisuje do pliku tekstowego, którego nazwa jest tworzona przy użyciu adresu zdalnego punktu końcowego (nieprawidłowy plik znaków nazwy w typowych identyfikatorów URI są zastępowane @ Zn.).</span><span class="sxs-lookup"><span data-stu-id="412c8-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="412c8-140">Później podczas identyfikator kontekstu jest wymagany do tego samego zdalnego punktu końcowego, sprawdza, czy istnieje odpowiedni plik.</span><span class="sxs-lookup"><span data-stu-id="412c8-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="412c8-141">Jeśli tak jest, odczytuje identyfikator kontekstu i zwraca.</span><span class="sxs-lookup"><span data-stu-id="412c8-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="412c8-142">W przeciwnym razie zwraca identyfikator nowo wygenerowane kontekstu i zapisuje go do pliku.</span><span class="sxs-lookup"><span data-stu-id="412c8-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="412c8-143">W przypadku domyślnej konfiguracji tych plików są umieszczane w katalogu o nazwie ContextStore, która znajduje się w katalogu tymczasowym bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="412c8-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="412c8-144">Jednak ta lokalizacja jest można skonfigurować za pomocą elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="412c8-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="412c8-145">Mechanizm służący do transportu kontekstowy identyfikator jest konfigurowany.</span><span class="sxs-lookup"><span data-stu-id="412c8-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="412c8-146">Jego można albo zapisywane do nagłówka pliku cookie HTTP lub niestandardowy nagłówek SOAP.</span><span class="sxs-lookup"><span data-stu-id="412c8-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="412c8-147">Niestandardowe podejście nagłówek SOAP umożliwia tego protokołu za pomocą protokołów innych niż HTTP (na przykład, TCP lub Named Pipes).</span><span class="sxs-lookup"><span data-stu-id="412c8-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="412c8-148">Istnieją dwie klasy, a mianowicie `MessageHeaderContextManager` i `HttpCookieContextManager`, która implementuje te dwie opcje.</span><span class="sxs-lookup"><span data-stu-id="412c8-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="412c8-149">Obydwaj zapisu identyfikator kontekstu do wiadomości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="412c8-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="412c8-150">Na przykład `MessageHeaderContextManager` klasy zapisuje go do nagłówka SOAP w `WriteContext` metody.</span><span class="sxs-lookup"><span data-stu-id="412c8-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
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
  
 <span data-ttu-id="412c8-151">Zarówno `ApplyContext` i `ReadContextId` metody `DurableInstanceContextChannelBase` wywołać klasy `IContextManager.ReadContext` i `IContextManager.WriteContext`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="412c8-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="412c8-152">Jednak te menedżerów kontekstu nie są bezpośrednio tworzone przez `DurableInstanceContextChannelBase` klasy.</span><span class="sxs-lookup"><span data-stu-id="412c8-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="412c8-153">Zamiast tego używa `ContextManagerFactory` klasie w celu wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="412c8-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="412c8-154">`ApplyContext` Metoda jest wywoływana przez wysyłanie kanałów.</span><span class="sxs-lookup"><span data-stu-id="412c8-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="412c8-155">Wprowadza ona identyfikator kontekstu do wiadomości wychodzących.</span><span class="sxs-lookup"><span data-stu-id="412c8-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="412c8-156">`ReadContextId` Metoda jest wywoływana przez odbieranie kanałów.</span><span class="sxs-lookup"><span data-stu-id="412c8-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="412c8-157">Ta metoda zapewnia, że identyfikator kontekstu jest dostępny w wiadomości przychodzących i dodaje go do `Properties` zbiór `Message` klasy.</span><span class="sxs-lookup"><span data-stu-id="412c8-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="412c8-158">Zgłasza również `CommunicationException` w razie awarii można odczytać Identyfikatora kontekstu i dlatego powoduje, że kanał przerwanie.</span><span class="sxs-lookup"><span data-stu-id="412c8-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="412c8-159">Zanim przejdziesz dalej, jest ważne, aby zrozumieć wykorzystanie `Properties` kolekcji w `Message` klasy.</span><span class="sxs-lookup"><span data-stu-id="412c8-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="412c8-160">Zwykle to `Properties` kolekcja jest używana, gdy przekazywanie danych od niższych do wyższych poziomów z warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="412c8-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="412c8-161">W ten sposób żądane dane można przekazać do wyższych poziomów w spójny sposób niezależnie od tego, szczegóły protokołu.</span><span class="sxs-lookup"><span data-stu-id="412c8-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="412c8-162">Innymi słowy warstwy kanału można wysyłać i odbierać identyfikator kontekstu jako nagłówek SOAP lub nagłówka pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="412c8-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="412c8-163">Ale nie jest konieczne wyższe poziomy wiedzieć o te informacje, ponieważ warstwy kanału sprawia, że te informacje są dostępne w `Properties` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="412c8-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="412c8-164">Teraz dzięki `DurableInstanceContextChannelBase` klasy w miejscu wszystkie dziesięć niezbędne interfejsy (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Można zaimplementować IDuplexChannel, IDuplexSessionChannel).</span><span class="sxs-lookup"><span data-stu-id="412c8-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="412c8-165">Są one podobne do każdego wymiany dostępnego komunikatu (datagram, jednostronny, komunikacja dwukierunkowa i ich warianty sesji).</span><span class="sxs-lookup"><span data-stu-id="412c8-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="412c8-166">Każda z tych implementacji dziedziczą z klasy bazowej, opisany wcześniej i wywołania `ApplyContext` i `ReadContexId` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="412c8-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="412c8-167">Na przykład `DurableInstanceContextOutputChannel` — który implementuje interfejs IOutputChannel - wywołuje `ApplyContext` metody z każdej metody, która wysyła komunikaty.</span><span class="sxs-lookup"><span data-stu-id="412c8-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="412c8-168">Z drugiej strony `DurableInstanceContextInputChannel` — które implementują `IInputChannel` interface - wywołania `ReadContextId` metody w każdej metody, która odbiera komunikaty.</span><span class="sxs-lookup"><span data-stu-id="412c8-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="412c8-169">Niezależnie od tego tych implementacji kanału delegowanie wywołań metod do kanału pod nimi w stosie kanału.</span><span class="sxs-lookup"><span data-stu-id="412c8-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="412c8-170">Przekroczono wariantów jednak podstawową logikę, aby upewnić się, że identyfikator kontekstu jest wysyłana i jest tylko do odczytu dla pierwszego komunikatu, który powoduje, że sesja ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="412c8-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="412c8-171">Tych implementacji kanału zostaną następnie dodane do środowiska uruchomieniowego kanału WCF, `DurableInstanceContextBindingElement` klasy i `DurableInstanceContextBindingElementSection` klasy odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="412c8-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="412c8-172">Zobacz [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanału przykładowa dokumentacja, aby uzyskać więcej szczegółów na temat elementów wiązania i powiązania sekcje elementu.</span><span class="sxs-lookup"><span data-stu-id="412c8-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="412c8-173">Rozszerzenia warstwy modelu usług</span><span class="sxs-lookup"><span data-stu-id="412c8-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="412c8-174">Teraz, gdy identyfikator kontekstu ma przejść przez warstwy kanału, można zaimplementować zachowanie usługi do dostosowywania procesu tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="412c8-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="412c8-175">W tym przykładzie Menedżer magazynowania służy do ładowania i Zapisz stan z lub do magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="412c8-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="412c8-176">Jak wyjaśniono wcześniej, w tym przykładzie przedstawiono Menedżer magazynowania, który używa programu SQL Server 2005 jako jego magazyn zapasowy.</span><span class="sxs-lookup"><span data-stu-id="412c8-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="412c8-177">Jednak użytkownik może również dodać mechanizmów magazynu niestandardowego do tego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="412c8-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="412c8-178">W tym interfejs publiczny jest zadeklarowana, muszą być zaimplementowane przez wszystkich menedżerów magazynu.</span><span class="sxs-lookup"><span data-stu-id="412c8-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="412c8-179">`SqlServerStorageManager` Klasy zawiera domyślną `IStorageManager` implementacji.</span><span class="sxs-lookup"><span data-stu-id="412c8-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="412c8-180">W jego `SaveInstance` metody dany obiekt jest serializowana, przy użyciu elementu XmlSerializer i jest zapisywany w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="412c8-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
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
  
 <span data-ttu-id="412c8-181">W `GetInstance` metoda serializowane dane do odczytu dla Identyfikatora podanym kontekście i obiekt skonstruowany z niego jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="412c8-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="412c8-182">Użytkownicy tych magazynu menedżerów nie powinien bezpośrednio utworzyć ich wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="412c8-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="412c8-183">Używają `StorageManagerFactory` klasy, która przenosi dane tworzenie Menedżera magazynu.</span><span class="sxs-lookup"><span data-stu-id="412c8-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="412c8-184">Ta klasa ma jeden statyczny element członkowski `GetStorageManager`, która tworzy wystąpienie typu Menedżera magazynowania.</span><span class="sxs-lookup"><span data-stu-id="412c8-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="412c8-185">Jeśli parametr typu jest `null`, ta metoda tworzy wystąpienie domyślne `SqlServerStorageManager` klasy i zwraca go.</span><span class="sxs-lookup"><span data-stu-id="412c8-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="412c8-186">Również sprawdza poprawność danego typu, aby upewnić się, że implementuje `IStorageManager` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="412c8-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
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
  
 <span data-ttu-id="412c8-187">Zaimplementowano infrastruktury wymaganej do odczytu i zapisu wystąpienia z magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="412c8-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="412c8-188">Teraz niezbędne kroki, aby zmienić zachowanie usługi muszą zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="412c8-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="412c8-189">W pierwszym kroku tego procesu trzeba zapisać identyfikator kontekstu, który pochodzi za pośrednictwem warstwy kanału do bieżącego obiektu InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="412c8-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="412c8-190">Obiekt InstanceContext jest składnika środowiska uruchomieniowego, który działa jako łącze między dyspozytora WCF i wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="412c8-191">Umożliwia zapewnienie dodatkowy stan i zachowanie do wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="412c8-192">Jest to ważne, ponieważ w ramach sesji komunikacji identyfikator kontekstu są wysyłane tylko w przypadku pierwszego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="412c8-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 <span data-ttu-id="412c8-193">Usługi WCF umożliwia rozszerzanie jego składnika środowiska wykonawczego typu InstanceContext przez dodanie nowego Państwa i zachowanie przy użyciu jego wzorzec extensible object.</span><span class="sxs-lookup"><span data-stu-id="412c8-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="412c8-194">Wzorzec extensible object jest używany w programie WCF, albo rozszerzanie istniejących klas środowiska uruchomieniowego przy użyciu nowych funkcji lub dodać nowe funkcje stan z obiektem.</span><span class="sxs-lookup"><span data-stu-id="412c8-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="412c8-195">Istnieją trzy interfejsy we wzorcu extensible object - IExtensibleObject\<T >, IExtension\<T >, a IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="412c8-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
-   <span data-ttu-id="412c8-196">IExtensibleObject\<T > Interfejs jest implementowany przez obiekty, które umożliwia rozszerzenia umożliwiające dostosowanie ich funkcje.</span><span class="sxs-lookup"><span data-stu-id="412c8-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
-   <span data-ttu-id="412c8-197">IExtension\<T > Interfejs jest implementowany przez obiekty, które mają rozszerzenia klas typu T.</span><span class="sxs-lookup"><span data-stu-id="412c8-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
-   <span data-ttu-id="412c8-198">IExtensionCollection\<T > Interfejs jest zbiorem IExtensions, która umożliwia pobieranie IExtensions według ich typu.</span><span class="sxs-lookup"><span data-stu-id="412c8-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="412c8-199">W związku z tym klasę InstanceContextExtension powinny zostać utworzone implementuje interfejs IExtension, który definiuje wymagany stan do zapisania identyfikatora kontekstu.</span><span class="sxs-lookup"><span data-stu-id="412c8-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="412c8-200">Ta klasa udostępnia także stanu do przechowywania magazynu manager używane.</span><span class="sxs-lookup"><span data-stu-id="412c8-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="412c8-201">Po zapisaniu nowego stanu nie powinna być go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="412c8-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="412c8-202">W związku z tym stan ma być dostarczana i zapisywane do wystąpienia w czasie, który jest zbudowany, a następnie dostępny tylko za pomocą właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="412c8-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
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
  
 <span data-ttu-id="412c8-203">Klasa InstanceContextInitializer implementuje interfejs IInstanceContextInitializer i dodaje do kolekcji rozszerzeń typu InstanceContext budowany rozszerzenie kontekstu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="412c8-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
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
  
 <span data-ttu-id="412c8-204">Zgodnie z wcześniejszym opisem identyfikator kontekstu są odczytywane z `Properties` zbiór `Message` klasy i przekazany do konstruktora klasy extension.</span><span class="sxs-lookup"><span data-stu-id="412c8-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="412c8-205">W tym przykładzie pokazano, jak informacje mogą być wymieniane między warstwami w spójny sposób.</span><span class="sxs-lookup"><span data-stu-id="412c8-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="412c8-206">Następnym krokiem ważne zastępują procesu tworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="412c8-207">Usługi WCF umożliwia Implementowanie zachowań niestandardowych podczas tworzenia wystąpienia i przechwytywanie je do środowiska uruchomieniowego przy użyciu interfejsu IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="412c8-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="412c8-208">Nowy `InstanceProvider` klasy zaimplementowany, aby wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="412c8-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="412c8-209">W Konstruktorze jest akceptowana oczekiwano od dostawcy wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="412c8-210">Później służy do tworzenia nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="412c8-210">Later this is used to create new instances.</span></span> <span data-ttu-id="412c8-211">W `GetInstance` tworzone jest wystąpienie Menedżera magazynu implementacji szukasz utrwalonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="412c8-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="412c8-212">Jeśli zostanie zwrócona `null` , a następnie nowe wystąpienie typu usługi jest tworzone i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="412c8-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="412c8-213">Dalej ważnym krokiem jest zainstalowanie `InstanceContextExtension`, `InstanceContextInitializer` i `InstanceProvider` klas w czasie wykonywania modelu usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="412c8-214">Niestandardowy atrybut może służyć do oznaczania zachowanie podczas instalowania klasy implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="412c8-215">`DurableInstanceContextAttribute` Zawiera implementację tego atrybutu i implementuje `IServiceBehavior` interfejsu, aby rozszerzyć środowisko uruchomieniowe całą usługę.</span><span class="sxs-lookup"><span data-stu-id="412c8-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="412c8-216">Ta klasa posiada właściwości, które akceptuje typ Menedżera magazynu do użycia.</span><span class="sxs-lookup"><span data-stu-id="412c8-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="412c8-217">W ten sposób implementacji umożliwia użytkownikom określenie własnych `IStorageManager` implementacji jako parametr tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="412c8-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="412c8-218">W `ApplyDispatchBehavior` implementacji `InstanceContextMode` bieżącego `ServiceBehavior` atrybutu jest weryfikowana.</span><span class="sxs-lookup"><span data-stu-id="412c8-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="412c8-219">Jeśli ta właściwość jest ustawiona na pojedyncze, umożliwiając niezawodne tworzenie wystąpienia nie jest możliwe i `InvalidOperationException` jest zgłaszany w celu powiadomienia hosta.</span><span class="sxs-lookup"><span data-stu-id="412c8-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
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
  
 <span data-ttu-id="412c8-220">Po tym wystąpienia Menedżera magazynu, wystąpienia kontekstu inicjatora i dostawca wystąpień są tworzone i zainstalowane w `DispatchRuntime` utworzone dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="412c8-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
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
  
 <span data-ttu-id="412c8-221">W podsumowaniu do tej pory w tym przykładzie tworzył kanału, który jest włączony protokół przewodowy niestandardowe wymiana identyfikator kontekstu niestandardowe, a także zastępuje domyślne zachowanie, aby załadować wystąpień z magazynu trwałego wystąpień.</span><span class="sxs-lookup"><span data-stu-id="412c8-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="412c8-222">Zachowasz pozostałe jest sposób można zapisać wystąpienia usługi w magazynie trwałym.</span><span class="sxs-lookup"><span data-stu-id="412c8-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="412c8-223">Jak wspomniano wcześniej, jest już wymaganych funkcji, która ma być zapisany stan w `IStorageManager` implementacji.</span><span class="sxs-lookup"><span data-stu-id="412c8-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="412c8-224">Firma Microsoft teraz muszą zintegrować to ze środowiskiem uruchomieniowym usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="412c8-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="412c8-225">Inny atrybut jest wymagany, które mają zastosowanie do metody w klasie implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="412c8-226">Ten atrybut powinien ma zostać zastosowany do metody, które zmieniają stan wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="412c8-227">`SaveStateAttribute` Klasa implementuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="412c8-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="412c8-228">Implementuje także `IOperationBehavior` klasy, aby zmodyfikować środowisko wykonawcze programu WCF dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="412c8-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="412c8-229">Gdy metoda jest oznaczona za pomocą tego atrybutu, środowisko wykonawcze programu WCF wywołuje `ApplyBehavior` metody podczas odpowiednie `DispatchOperation` jest budowany.</span><span class="sxs-lookup"><span data-stu-id="412c8-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="412c8-230">W tej implementacji metoda ma nawet jednego wiersza kodu:</span><span class="sxs-lookup"><span data-stu-id="412c8-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="412c8-231">Ta instrukcja tworzy wystąpienie `OperationInvoker` typu, a następnie przypisuje go do `Invoker` właściwość `DispatchOperation` budowany.</span><span class="sxs-lookup"><span data-stu-id="412c8-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="412c8-232">`OperationInvoker` Klasy jest otoką element wywołujący operacji domyślne, które zostały utworzone dla `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="412c8-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="412c8-233">Ta klasa implementuje `IOperationInvoker` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="412c8-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="412c8-234">W `Invoke` implementacji metody wywołania metody rzeczywisty jest delegowane do wywoływania operacji wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="412c8-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="412c8-235">Jednak przed zwracania wyników Menedżer magazynowania w `InstanceContext` służy do zapisania wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
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
  
## <a name="using-the-extension"></a><span data-ttu-id="412c8-236">Przy użyciu rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="412c8-236">Using the Extension</span></span>  
 <span data-ttu-id="412c8-237">Zarówno warstwy kanału i rozszerzenia warstwy modelu usług są wykonywane, i ich można teraz używać w aplikacjach usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="412c8-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="412c8-238">Usługi trzeba dodać kanał do stosu kanału, za pomocą niestandardowego powiązania, a następnie oznacz klas implementacji usług z odpowiednimi atrybutami.</span><span class="sxs-lookup"><span data-stu-id="412c8-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
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
  
 <span data-ttu-id="412c8-239">Aplikacje klienckie należy dodać DurableInstanceContextChannel do stosu kanału, za pomocą niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="412c8-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="412c8-240">Aby skonfigurować kanał deklaratywnie w pliku konfiguracji, sekcja element powiązania ma ma zostać dodany do kolekcji rozszerzenia elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="412c8-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="412c8-241">Element powiązania można teraz za pomocą niestandardowego powiązania, podobnie jak inne elementy powiązania standardowe:</span><span class="sxs-lookup"><span data-stu-id="412c8-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
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
  
## <a name="conclusion"></a><span data-ttu-id="412c8-242">Wniosek</span><span class="sxs-lookup"><span data-stu-id="412c8-242">Conclusion</span></span>  
 <span data-ttu-id="412c8-243">W tym przykładzie pokazano sposób tworzenia kanału protokołu niestandardowego i jak dostosować zachowanie usługi, aby ją włączyć.</span><span class="sxs-lookup"><span data-stu-id="412c8-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="412c8-244">Rozszerzenie można dodatkowo zwiększyć, umożliwiając użytkownikom określanie `IStorageManager` wdrożenia przy użyciu sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="412c8-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="412c8-245">Dzięki temu można modyfikować magazyn zapasowy bez konieczności ponownego kompilowania kodu usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="412c8-246">Ponadto użytkownik może próbować Implementowanie klasy (na przykład `StateBag`), która hermetyzuje stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="412c8-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="412c8-247">Ta klasa jest odpowiedzialne za utrwalanie stanu zawsze wtedy, gdy zmienia się.</span><span class="sxs-lookup"><span data-stu-id="412c8-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="412c8-248">W ten sposób możesz uniknąć używania `SaveState` atrybutu i wykonywania pracy utrwalanie dokładniej (na przykład można utrwalić stanu rzeczywiście zmiana stanu zamiast zapisywać każdym razem gdy metody z `SaveState` atrybutu wywołuje się).</span><span class="sxs-lookup"><span data-stu-id="412c8-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="412c8-249">Po uruchomieniu przykładu, następujące dane wyjściowe są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="412c8-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="412c8-250">Klient dodaje dwa elementy do jego koszyka zakupów i następnie pobiera listę elementów w jego koszyk sklepowy z usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="412c8-251">Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="412c8-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="412c8-252">Ponowne tworzenie usługi zastępuje plik bazy danych.</span><span class="sxs-lookup"><span data-stu-id="412c8-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="412c8-253">Aby obserwować stanu zachowanego wielu uruchomień próbki, należy nie ponownie skompiluj przykładowy między działa.</span><span class="sxs-lookup"><span data-stu-id="412c8-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="412c8-254">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="412c8-254">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="412c8-255">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="412c8-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="412c8-256">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="412c8-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="412c8-257">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="412c8-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="412c8-258">Musi działać program SQL Server 2005 lub SQL Express 2005, aby uruchomić ten przykład.</span><span class="sxs-lookup"><span data-stu-id="412c8-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="412c8-259">Jeśli używasz programu SQL Server 2005, należy zmodyfikować konfigurację parametrów połączenia usługi.</span><span class="sxs-lookup"><span data-stu-id="412c8-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="412c8-260">Podczas uruchamiania między komputerami, programu SQL Server jest wymagana tylko na komputerze z serwerem.</span><span class="sxs-lookup"><span data-stu-id="412c8-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="412c8-261">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="412c8-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="412c8-262">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="412c8-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="412c8-263">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="412c8-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="412c8-264">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="412c8-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
