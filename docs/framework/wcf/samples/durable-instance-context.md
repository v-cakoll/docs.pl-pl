---
title: Kontekst niezawodnej instancji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4f1f3f9e840ba422e327792ec2b0554fad45902
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="durable-instance-context"></a><span data-ttu-id="95eef-102">Kontekst niezawodnej instancji</span><span class="sxs-lookup"><span data-stu-id="95eef-102">Durable Instance Context</span></span>
<span data-ttu-id="95eef-103">W tym przykładzie pokazano, jak dostosować [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] środowiska wykonawczego, aby włączyć kontekst niezawodnej instancji.</span><span class="sxs-lookup"><span data-stu-id="95eef-103">This sample demonstrates how to customize the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] runtime to enable durable instance contexts.</span></span> <span data-ttu-id="95eef-104">SQL Server 2005 używa jako magazynu zapasowego, jego (SQL Server 2005 Express w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="95eef-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="95eef-105">Jednak umożliwia także sposób uzyskać dostępu do magazynu niestandardowych mechanizmów.</span><span class="sxs-lookup"><span data-stu-id="95eef-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95eef-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="95eef-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="95eef-107">Ten przykład obejmuje zarówno warstwie kanału, jak i warstwy modelu usług z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95eef-107">This sample involves extending both the channel layer and the service model layer of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="95eef-108">W związku z tym należy zrozumieć podstawowe pojęcia przed przejściem do szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="95eef-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="95eef-109">Konteksty wystąpienia trwałych znajduje się w rzeczywistych scenariuszach bardzo często.</span><span class="sxs-lookup"><span data-stu-id="95eef-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="95eef-110">Na przykład aplikację koszyka zakupów ma możliwość wstrzymać zakupy w połowie za pośrednictwem i kontynuować go innym dnia.</span><span class="sxs-lookup"><span data-stu-id="95eef-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="95eef-111">Tak, aby po firma Microsoft odwiedź koszyka następnego dnia, naszych oryginalnego kontekst został przywrócony.</span><span class="sxs-lookup"><span data-stu-id="95eef-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="95eef-112">Należy pamiętać, że aplikacja koszyka zakupów (na serwerze) nie przechowuje wystąpienie koszyka zakupów odłączeniu możemy są.</span><span class="sxs-lookup"><span data-stu-id="95eef-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="95eef-113">Zamiast tego utrwala swój stan na trwałe nośników i używa go podczas tworzenia nowego wystąpienia dla kontekstu przywrócone.</span><span class="sxs-lookup"><span data-stu-id="95eef-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="95eef-114">W związku z tym wystąpienie usługi, która może obsłużyć tego samego kontekstu nie jest taka sama jak poprzedniego wystąpienia (to znaczy, że nie ma ten sam adres pamięci).</span><span class="sxs-lookup"><span data-stu-id="95eef-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="95eef-115">Kontekst niezawodnej instancji jest możliwe przez małe protokół, który wymienia identyfikator kontekstu między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="95eef-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="95eef-116">Ten identyfikator kontekstu jest tworzony na kliencie i przesyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="95eef-117">Po utworzeniu wystąpienia usługi, czas wykonywania usługi próbuje załadować stan utrwalony odpowiadający ten identyfikator kontekstu z magazynu trwałego (domyślnie jest bazą danych programu SQL Server 2005).</span><span class="sxs-lookup"><span data-stu-id="95eef-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="95eef-118">Jeśli stan nie jest dostępny nowe wystąpienie ma stanu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="95eef-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="95eef-119">Implementacji usługi używa atrybutu niestandardowego, aby oznaczyć działania, zmienić stan wdrożenia usługi, dzięki czemu środowiska uruchomieniowego można zapisać wystąpienia usługi po wywołaniu ich.</span><span class="sxs-lookup"><span data-stu-id="95eef-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="95eef-120">W opisie poprzednich aby osiągnąć łatwo można rozróżnić dwa kroki:</span><span class="sxs-lookup"><span data-stu-id="95eef-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1.  <span data-ttu-id="95eef-121">Zmień komunikat, który przechodzi umieszczonego do przenoszenia identyfikatora kontekstu.</span><span class="sxs-lookup"><span data-stu-id="95eef-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2.  <span data-ttu-id="95eef-122">Zmień zachowanie lokalnej usługi do zaimplementowania niestandardowej logiki wystąpień.</span><span class="sxs-lookup"><span data-stu-id="95eef-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="95eef-123">Ponieważ pierwsza z nich na liście dotyczy wiadomości przesyłania powinny zostać wdrożone jako niestandardowy kanał i można podłączyć do warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="95eef-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="95eef-124">Drugie wpływa tylko na zachowanie lokalnej usługi i może być implementowana przez rozszerzenie kilka punktów rozszerzalności usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="95eef-125">W kolejnych sekcjach kilka omówiono każdego z tych rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="95eef-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="95eef-126">Niezawodny kanał InstanceContext</span><span class="sxs-lookup"><span data-stu-id="95eef-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="95eef-127">Przede wszystkim należy przyjrzeć się to rozszerzenie warstwy kanału.</span><span class="sxs-lookup"><span data-stu-id="95eef-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="95eef-128">Pierwszą czynnością przy tworzeniu niestandardowym kanale jest podjęcie decyzji, struktura komunikacji kanału.</span><span class="sxs-lookup"><span data-stu-id="95eef-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="95eef-129">Ponieważ wprowadzono nowy Protokół kanału powinien współpracować z prawie każdego innego kanału w stosie kanału.</span><span class="sxs-lookup"><span data-stu-id="95eef-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="95eef-130">W związku z tym go powinien obsługiwać wszystkie wzorce wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="95eef-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="95eef-131">Jednak do podstawowych funkcji kanał jest taki sam, niezależnie od jego struktury komunikacji.</span><span class="sxs-lookup"><span data-stu-id="95eef-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="95eef-132">W szczególności od klienta go zapisać identyfikator kontekstu w wiadomości i z usługi należy przeczytać ten identyfikator kontekstu z wiadomości i przekaż go do wyższe poziomy.</span><span class="sxs-lookup"><span data-stu-id="95eef-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="95eef-133">Z tego powodu `DurableInstanceContextChannelBase` utworzyć działającego jako abstrakcyjna klasa podstawowa dla wszystkich implementacji kanału kontekst niezawodnej instancji klasy.</span><span class="sxs-lookup"><span data-stu-id="95eef-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="95eef-134">Ta klasa zawiera typowe funkcje zarządzania maszyny stanu i dwa chronionych elementów członkowskich, aby zastosować i przeczytaj informacje o kontekście do i z wiadomości.</span><span class="sxs-lookup"><span data-stu-id="95eef-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
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
  
 <span data-ttu-id="95eef-135">Te dwie metody należy korzystać z `IContextManager` implementacje do zapisu i odczytu identyfikator kontekstu do lub z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="95eef-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="95eef-136">(`IContextManager` jest niestandardowy interfejs używany do definiowania kontrakt dla wszystkich menedżerów kontekstu.) Kanał można dołączyć identyfikator kontekstu niestandardowego nagłówka SOAP lub nagłówka pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="95eef-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="95eef-137">Każda implementacja menedżera kontekstu dziedziczy `ContextManagerBase` klasy, która zawiera typowe funkcje menedżerom kontekstu.</span><span class="sxs-lookup"><span data-stu-id="95eef-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="95eef-138">`GetContextId` Metoda ta klasa służy do pochodzą z Identyfikatorem kontekstu z klienta.</span><span class="sxs-lookup"><span data-stu-id="95eef-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="95eef-139">Jeśli kontekst, w których identyfikator jest pochodzi po raz pierwszy, ta metoda zapisuje do pliku tekstowego, którego nazwa jest tworzony za pomocą adresu zdalnego punktu końcowego (nieprawidłowy plik znaków nazwy w typowych identyfikatory URI są zastępowane @ znaków).</span><span class="sxs-lookup"><span data-stu-id="95eef-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="95eef-140">Później, gdy do tego samego zdalny punkt końcowy wymagany jest identyfikator kontekstu, sprawdza, czy istnieje odpowiedni plik.</span><span class="sxs-lookup"><span data-stu-id="95eef-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="95eef-141">Jeśli tak, odczytuje identyfikator kontekstu i zwraca.</span><span class="sxs-lookup"><span data-stu-id="95eef-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="95eef-142">W przeciwnym razie zwraca identyfikator nowo wygenerowanym kontekście i zapisuje go w pliku.</span><span class="sxs-lookup"><span data-stu-id="95eef-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="95eef-143">Z konfiguracji domyślnej pliki te są umieszczane w katalogu o nazwie ContextStore, który znajduje się w katalogu temp bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="95eef-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="95eef-144">Ta lokalizacja jest jednak można skonfigurować za pomocą elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="95eef-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="95eef-145">Konfiguruje się mechanizm używany do transportu identyfikator kontekstu.</span><span class="sxs-lookup"><span data-stu-id="95eef-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="95eef-146">Go można albo zapisania nagłówka pliku cookie HTTP lub niestandardowy nagłówek SOAP.</span><span class="sxs-lookup"><span data-stu-id="95eef-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="95eef-147">Niestandardowe podejście nagłówek SOAP sprawia, że możliwość korzystania z protokołów innych niż HTTP (np. TCP lub Named Pipes) tego protokołu.</span><span class="sxs-lookup"><span data-stu-id="95eef-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="95eef-148">Istnieją dwie klasy, a mianowicie `MessageHeaderContextManager` i `HttpCookieContextManager`, który implementuje te dwie opcje.</span><span class="sxs-lookup"><span data-stu-id="95eef-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="95eef-149">Oba identyfikator kontekstu do zapisu komunikatu odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="95eef-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="95eef-150">Na przykład `MessageHeaderContextManager` klasy zapisuje go do nagłówka SOAP w `WriteContext` metody.</span><span class="sxs-lookup"><span data-stu-id="95eef-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
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
  
 <span data-ttu-id="95eef-151">Zarówno `ApplyContext` i `ReadContextId` metod w `DurableInstanceContextChannelBase` klasy wywołania `IContextManager.ReadContext` i `IContextManager.WriteContext`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="95eef-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="95eef-152">Jednak te menedżerów kontekstu nie są bezpośrednio tworzone przez `DurableInstanceContextChannelBase` klasy.</span><span class="sxs-lookup"><span data-stu-id="95eef-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="95eef-153">Zamiast tego używa `ContextManagerFactory` klasę, aby wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="95eef-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="95eef-154">`ApplyContext` Metoda jest wywoływana przez wysyłanie kanałów.</span><span class="sxs-lookup"><span data-stu-id="95eef-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="95eef-155">Identyfikator kontekstu w komunikatach wychodzących go injects.</span><span class="sxs-lookup"><span data-stu-id="95eef-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="95eef-156">`ReadContextId` Metoda jest wywoływana przez kanały odbierania.</span><span class="sxs-lookup"><span data-stu-id="95eef-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="95eef-157">Ta metoda gwarantuje, że identyfikator kontekstu jest dostępny w komunikatach przychodzących i dodaje go do `Properties` Kolekcja `Message` klasy.</span><span class="sxs-lookup"><span data-stu-id="95eef-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="95eef-158">Również zgłasza `CommunicationException` w przypadku awarii odczytać Identyfikatora kontekstu i w związku z tym powoduje, że kanał przerwanie.</span><span class="sxs-lookup"><span data-stu-id="95eef-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="95eef-159">Przed kontynuowaniem, ważne jest, aby zrozumieć użycie `Properties` kolekcji w `Message` klasy.</span><span class="sxs-lookup"><span data-stu-id="95eef-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="95eef-160">Zwykle to `Properties` kolekcja jest używana, gdy przekazywanie danych z niższym na wyższe poziomy w warstwie kanału.</span><span class="sxs-lookup"><span data-stu-id="95eef-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="95eef-161">W ten sposób żądanych danych można podać na wyższe poziomy w sposób ciągły, niezależnie od tego, szczegóły protokołu.</span><span class="sxs-lookup"><span data-stu-id="95eef-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="95eef-162">Innymi słowy warstwie kanału wysyłać i odbierać identyfikator kontekstu jako nagłówka SOAP lub nagłówka pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="95eef-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="95eef-163">Ale nie jest niezbędna dla wyższe poziomy wiedzieć o te informacje, ponieważ w warstwie kanału sprawia, że te informacje są dostępne w `Properties` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95eef-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="95eef-164">Teraz z `DurableInstanceContextChannelBase` klasy w miejscu wszystkich dziesięciu niezbędne interfejsów (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, Musi być implementowana IDuplexChannel, IDuplexSessionChannel).</span><span class="sxs-lookup"><span data-stu-id="95eef-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="95eef-165">Są one podobne do każdej dostępnej wymiany komunikatów (datagram, jednostronny, dupleks i ich warianty sesyjnych).</span><span class="sxs-lookup"><span data-stu-id="95eef-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="95eef-166">Każda z tych implementacji dziedziczyć klasy podstawowej opisany powyżej i wywołania `ApplyContext` i `ReadContexId` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="95eef-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="95eef-167">Na przykład `DurableInstanceContextOutputChannel` — która implementuje interfejs IOutputChannel - wywołuje `ApplyContext` metody z każdej metody, która wysyła komunikaty.</span><span class="sxs-lookup"><span data-stu-id="95eef-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="95eef-168">Z drugiej strony `DurableInstanceContextInputChannel` — z zaimplementowanym `IInputChannel` interface - wywołania `ReadContextId` metody w każdej metodzie, który odbiera komunikaty.</span><span class="sxs-lookup"><span data-stu-id="95eef-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="95eef-169">Oprócz tego tych implementacji kanału delegowanie wywołań metod do kanału znajdującą się pod nimi w stosie kanału.</span><span class="sxs-lookup"><span data-stu-id="95eef-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="95eef-170">Przekroczono wariantów jednak podstawowa logika, aby upewnić się, że identyfikator kontekstu są wysyłane i jest do odczytu tylko dla pierwszego komunikat, który powoduje, że sesja ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="95eef-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="95eef-171">Implementacje tych kanałów jest następnie dodawana do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska uruchomieniowego kanału przez `DurableInstanceContextBindingElement` klasy i `DurableInstanceContextBindingElementSection` odpowiednio klasy.</span><span class="sxs-lookup"><span data-stu-id="95eef-171">These channel implementations are then added to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="95eef-172">Zobacz [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanału przykładowej dokumentacji więcej szczegółów na temat elementów wiązania i powiązania elementu sekcje.</span><span class="sxs-lookup"><span data-stu-id="95eef-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="95eef-173">Rozszerzenia warstwy modelu usług</span><span class="sxs-lookup"><span data-stu-id="95eef-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="95eef-174">Teraz, identyfikator kontekstu ma pokonać za pośrednictwem warstwy kanału, można zaimplementować zachowanie usługi do dostosowywania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95eef-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="95eef-175">W tym przykładzie Menedżer magazynowania służy do ładowania i zapisać stanu z lub do magazynu trwałego.</span><span class="sxs-lookup"><span data-stu-id="95eef-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="95eef-176">Jak opisano wcześniej, w tym przykładzie przedstawiono Menedżer magazynowania, który używa programu SQL Server 2005 jako jego magazynu zapasowego.</span><span class="sxs-lookup"><span data-stu-id="95eef-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="95eef-177">Jednak również jest możliwie dodanie mechanizmów magazynu niestandardowego do tego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="95eef-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="95eef-178">W tym celu interfejs publiczny jest zadeklarowana, musi być implementowana przez wszystkich menedżerów magazynu.</span><span class="sxs-lookup"><span data-stu-id="95eef-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="95eef-179">`SqlServerStorageManager` Klasa zawiera domyślne `IStorageManager` implementacji.</span><span class="sxs-lookup"><span data-stu-id="95eef-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="95eef-180">W jego `SaveInstance` metody dany obiekt jest zserializowanym przy użyciu elementu XmlSerializer i jest zapisywana w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="95eef-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
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
  
 <span data-ttu-id="95eef-181">W `GetInstance` — metoda odczytu danych serializacji dla Identyfikatora podanego kontekstu i utworzone na podstawie jego obiekt jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="95eef-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="95eef-182">Użytkownicy tych magazynu menedżerów nie powinien bezpośrednio utworzyć ich wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95eef-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="95eef-183">Używają `StorageManagerFactory` klasy, która abstracts z szczegóły tworzenie Menedżera magazynu.</span><span class="sxs-lookup"><span data-stu-id="95eef-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="95eef-184">Ta klasa ma jeden statyczny element członkowski `GetStorageManager`, co powoduje wystąpienie typu Menedżera danego magazynu.</span><span class="sxs-lookup"><span data-stu-id="95eef-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="95eef-185">Jeśli parametr typu jest `null`, ta metoda tworzy wystąpienie domyślne `SqlServerStorageManager` klasy i zwraca go.</span><span class="sxs-lookup"><span data-stu-id="95eef-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="95eef-186">Jest również sprawdzane danego typu, aby upewnić się, że implementuje `IStorageManager` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95eef-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
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
  
 <span data-ttu-id="95eef-187">Zaimplementowano infrastruktury wymaganej do odczytu i zapisu z magazynu trwałego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95eef-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="95eef-188">Teraz czynności niezbędnych do zmiany zachowania usługi muszą zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="95eef-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="95eef-189">W pierwszym kroku procesu mamy do zapisania Identyfikatora kontekstu, która pochodzi za pośrednictwem warstwy kanału do bieżącego obiektu InstanceContext.</span><span class="sxs-lookup"><span data-stu-id="95eef-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="95eef-190">Obiekt InstanceContext jest składnika środowiska uruchomieniowego, który pełni rolę łącza między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dyspozytora i wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-190">InstanceContext is a runtime component that acts as the link between the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatcher and the service instance.</span></span> <span data-ttu-id="95eef-191">Może służyć do dodatkowych stanie i zachowanie do wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="95eef-192">Jest to konieczne, ponieważ w komunikacie sesyjnych identyfikator kontekstu jest wysyłane tylko z pierwszego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="95eef-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="95eef-193">umożliwia rozszerzanie jej składnika środowiska wykonawczego InstanceContext przez dodanie nowego stanu i zachowanie przy użyciu jego wzorca rozszerzonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="95eef-193"> allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="95eef-194">Wzorzec extensible obiekt jest używany w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wydłużyć istniejące klasy środowiska uruchomieniowego z nowych funkcji lub dodawania nowych funkcji stanu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="95eef-194">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="95eef-195">Istnieją trzy interfejsy we wzorcu rozszerzonego obiektu - interfejs IExtensibleObject\<T >, IExtension\<T >, a IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="95eef-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
-   <span data-ttu-id="95eef-196">Interfejs IExtensibleObject\<T > Interfejs jest implementowany przez obiekty, które umożliwia rozszerzenia umożliwiające dostosowanie ich funkcje.</span><span class="sxs-lookup"><span data-stu-id="95eef-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
-   <span data-ttu-id="95eef-197">IExtension\<T > Interfejs jest implementowany przez obiekty, które mają rozszerzenia klasy typu T.</span><span class="sxs-lookup"><span data-stu-id="95eef-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
-   <span data-ttu-id="95eef-198">IExtensionCollection\<T > interfejsu jest kolekcją IExtensions, która umożliwia pobieranie IExtensions według typu.</span><span class="sxs-lookup"><span data-stu-id="95eef-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="95eef-199">W związku z tym klasy InstanceContextExtension należy utworzyć implementuje interfejs IExtension, który definiuje stan wymagane do zapisania identyfikatora kontekstu.</span><span class="sxs-lookup"><span data-stu-id="95eef-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="95eef-200">Ta klasa udostępnia także stanu do przechowywania magazynu Menedżera używane.</span><span class="sxs-lookup"><span data-stu-id="95eef-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="95eef-201">Po zapisaniu nowy stan nie powinny być go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="95eef-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="95eef-202">W związku z tym stan ma być dostarczana i zapisywane do wystąpienia w czasie, które są skonstruowane i następnie dostępna tylko za pomocą właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="95eef-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
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
  
 <span data-ttu-id="95eef-203">Klasa InstanceContextInitializer implementuje interfejs IInstanceContextInitializer i dodaje do kolekcji rozszerzenia InstanceContext budowany rozszerzenie kontekstu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95eef-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
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
  
 <span data-ttu-id="95eef-204">Zgodnie z wcześniejszym opisem identyfikator kontekstu zostanie odczytany z `Properties` Kolekcja `Message` klasy i przekazany do konstruktora klasy extension.</span><span class="sxs-lookup"><span data-stu-id="95eef-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="95eef-205">Oznacza to, jak informacje może być wymieniane między warstwami w sposób ciągły.</span><span class="sxs-lookup"><span data-stu-id="95eef-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="95eef-206">Następnym krokiem ważne zastępuje procesu tworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-206">The next important step is overriding the service instance creation process.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="95eef-207">Umożliwia Implementowanie niestandardowego wystąpienia zachowania i przechwytywanie je do środowiska uruchomieniowego przy użyciu interfejsu IInstanceProvider.</span><span class="sxs-lookup"><span data-stu-id="95eef-207"> allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="95eef-208">Nowe `InstanceProvider` zaimplementowana jest klasa, aby wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="95eef-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="95eef-209">W Konstruktorze jest akceptowany oczekiwano od dostawcy wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="95eef-210">Później służy to tworzenia nowych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="95eef-210">Later this is used to create new instances.</span></span> <span data-ttu-id="95eef-211">W `GetInstance` tworzone jest wystąpienie Menedżera magazynu implementacji wyszukiwanie trwałego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95eef-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="95eef-212">Jeśli zmienna zwraca `null` utworzone nowe wystąpienie typu usługi i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="95eef-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="95eef-213">Ważne następnym krokiem jest zainstalowanie `InstanceContextExtension`, `InstanceContextInitializer` i `InstanceProvider` klasy w czasie wykonywania modelu usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="95eef-214">Atrybut niestandardowy może służyć do oznaczenie klasy implementacji usługi do zainstalowania zachowanie.</span><span class="sxs-lookup"><span data-stu-id="95eef-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="95eef-215">`DurableInstanceContextAttribute` Zawiera implementację tego atrybutu i implementuje `IServiceBehavior` interfejs do rozszerzania środowiska uruchomieniowego całej usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="95eef-216">Ta klasa ma właściwość, która akceptuje typ Menedżera magazynu, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="95eef-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="95eef-217">W ten sposób wykonania pozwala użytkownikom na określenie własnych `IStorageManager` implementacji jako parametr tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="95eef-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="95eef-218">W `ApplyDispatchBehavior` implementacji `InstanceContextMode` bieżącego `ServiceBehavior` atrybutu jest weryfikowany.</span><span class="sxs-lookup"><span data-stu-id="95eef-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="95eef-219">Jeśli ta właściwość jest ustawiona na pojedyncze, włączanie trwałe wystąpień nie jest możliwe i `InvalidOperationException` jest generowany, by powiadomić hosta.</span><span class="sxs-lookup"><span data-stu-id="95eef-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
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
  
 <span data-ttu-id="95eef-220">Po tym wystąpienia Menedżera magazynowania, wystąpienie kontekstu inicjatora i dostawcy wystąpienia są tworzone i zainstalowane w `DispatchRuntime` utworzone dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="95eef-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
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
  
 <span data-ttu-id="95eef-221">W podsumowaniu wykonanej do tej pory w tym przykładzie ma utworzyło kanału, który jest włączony protokół przewodowy niestandardowych dla programu exchange identyfikator kontekstu niestandardowe, a także zastępuje domyślne zachowanie można załadować wystąpienia z magazynu trwałego wystąpień.</span><span class="sxs-lookup"><span data-stu-id="95eef-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="95eef-222">Pozostała to sposób Zapisz do magazynu trwałego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="95eef-223">Jak wspomniano wcześniej, jest już wymagane funkcje można zapisać stanu w `IStorageManager` implementacji.</span><span class="sxs-lookup"><span data-stu-id="95eef-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="95eef-224">Mamy teraz należy zintegrować to z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="95eef-224">We now must integrate this with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime.</span></span> <span data-ttu-id="95eef-225">Inny atrybut jest wymagany, które mają zastosowanie do metody w klasie implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="95eef-226">Ten atrybut powinien można zastosować do metody, które spowodują zmianę stanu wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="95eef-227">`SaveStateAttribute` Klasa implementuje tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="95eef-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="95eef-228">Implementuje również `IOperationBehavior` klasę, aby zmodyfikować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska uruchomieniowego dla każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="95eef-228">It also implements `IOperationBehavior` class to modify the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime for each operation.</span></span> <span data-ttu-id="95eef-229">Gdy metoda jest oznaczona atrybutem, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wywołuje środowiska uruchomieniowego `ApplyBehavior` metoda podczas odpowiednie `DispatchOperation` jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="95eef-229">When a method is marked with this attribute, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="95eef-230">W tej implementacji metody jest pojedynczy wiersz kodu:</span><span class="sxs-lookup"><span data-stu-id="95eef-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="95eef-231">Ta instrukcja tworzy wystąpienie `OperationInvoker` typu, a następnie przypisuje go do `Invoker` właściwość `DispatchOperation` tworzona.</span><span class="sxs-lookup"><span data-stu-id="95eef-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="95eef-232">`OperationInvoker` Klasy jest otoki dla wywołującego operacji domyślny utworzony dla `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="95eef-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="95eef-233">Ta klasa implementuje `IOperationInvoker` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95eef-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="95eef-234">W `Invoke` implementacji metody wywołania metody rzeczywistego jest delegowane do wywoływania operacji wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="95eef-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="95eef-235">Jednak przed zwracania wyników Menedżer magazynowania w `InstanceContext` służy do zapisania wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
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
  
## <a name="using-the-extension"></a><span data-ttu-id="95eef-236">Przy użyciu rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="95eef-236">Using the Extension</span></span>  
 <span data-ttu-id="95eef-237">Kanał warstwy i usługi warstwy rozszerzeń modelu są wykonywane, a teraz mogą być używane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95eef-237">Both the channel layer and service model layer extensions are done and they can now be used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span> <span data-ttu-id="95eef-238">Usługi trzeba dodać do stosu kanału, za pomocą niestandardowego powiązania kanału, a następnie oznaczenie klasy implementacji usługi z odpowiednich atrybutów.</span><span class="sxs-lookup"><span data-stu-id="95eef-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
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
  
 <span data-ttu-id="95eef-239">Aplikacje klienckie należy dodać DurableInstanceContextChannel do stosu kanału, za pomocą niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="95eef-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="95eef-240">Aby skonfigurować kanał deklaratywnie w pliku konfiguracji, sekcja element powiązania ma ma zostać dodany do kolekcji rozszerzeń element powiązania.</span><span class="sxs-lookup"><span data-stu-id="95eef-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="95eef-241">Element powiązania można teraz używać z niestandardowego powiązania, podobnie jak inne elementy Powiązanie standardowe:</span><span class="sxs-lookup"><span data-stu-id="95eef-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
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
  
## <a name="conclusion"></a><span data-ttu-id="95eef-242">Wniosek</span><span class="sxs-lookup"><span data-stu-id="95eef-242">Conclusion</span></span>  
 <span data-ttu-id="95eef-243">W tym przykładzie pokazano sposób tworzenia kanału protokołu niestandardowego oraz jak dostosować zachowanie usługi, aby ją włączyć.</span><span class="sxs-lookup"><span data-stu-id="95eef-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="95eef-244">Rozszerzenie można dodatkowo zwiększyć, umożliwiając użytkownikom określanie `IStorageManager` wdrożenia przy użyciu sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="95eef-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="95eef-245">Dzięki temu można modyfikować magazynu zapasowego bez konieczności ponownego kompilowania kodu usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="95eef-246">Ponadto użytkownik może próbować Implementowanie klasy (na przykład `StateBag`), który hermetyzuje stan wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="95eef-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="95eef-247">Tej klasy jest odpowiedzialny za utrwalanie stanu zawsze, gdy zmieni się.</span><span class="sxs-lookup"><span data-stu-id="95eef-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="95eef-248">W ten sposób możesz uniknąć używania `SaveState` atrybutu i dokładniej wykonywania utrwalanie pracy (na przykład można utrwalić stanu, gdy stan faktycznie zostanie zmieniona zamiast zapisywać dokument każdorazowo po metodę o `SaveState` atrybutu wywołuje się).</span><span class="sxs-lookup"><span data-stu-id="95eef-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="95eef-249">Po uruchomieniu próbki następujące dane wyjściowe są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="95eef-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="95eef-250">Klient dodaje dwa elementy do jego koszyk i następnie pobiera listę elementów w jego koszyk z usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="95eef-251">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="95eef-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="95eef-252">Ponowne tworzenie usługi spowoduje zastąpienie pliku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="95eef-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="95eef-253">Aby przyjrzeć się stanu zachowanego przez wiele przebiegów próbki, należy nie odbudować próbki między działa.</span><span class="sxs-lookup"><span data-stu-id="95eef-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95eef-254">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="95eef-254">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="95eef-255">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95eef-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="95eef-256">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95eef-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="95eef-257">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95eef-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95eef-258">SQL Server 2005 lub SQL Express 2005, aby uruchomić ten przykład, użytkownik musi być uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="95eef-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="95eef-259">Jeśli używasz programu SQL Server 2005, należy zmodyfikować konfigurację parametrów połączenia usługi.</span><span class="sxs-lookup"><span data-stu-id="95eef-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="95eef-260">Podczas uruchamiania między komputerami, programu SQL Server jest wymagana tylko na komputerze z serwerem.</span><span class="sxs-lookup"><span data-stu-id="95eef-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95eef-261">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="95eef-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95eef-262">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="95eef-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="95eef-263">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="95eef-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95eef-264">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="95eef-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a><span data-ttu-id="95eef-265">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95eef-265">See Also</span></span>
