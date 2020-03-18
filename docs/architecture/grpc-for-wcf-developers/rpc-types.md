---
title: Rodzaje RPC - gRPC dla programistów WCF
description: Przegląd rodzajów zdalnego wywołania procedury obsługiwane przez WCF i ich odpowiedniki w gRPC
ms.date: 09/02/2019
ms.openlocfilehash: b9d4ce7cae693ed7904229483cbccfe3b299b640
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401684"
---
# <a name="types-of-rpc"></a><span data-ttu-id="ac2a1-103">Typy zdalnych wywołań procedur</span><span class="sxs-lookup"><span data-stu-id="ac2a1-103">Types of RPC</span></span>

<span data-ttu-id="ac2a1-104">Jako deweloper Windows Communication Foundation (WCF) prawdopodobnie jesteś przyzwyczajony do obsługi następujących typów wywołań procedury zdalnej (RPC):</span><span class="sxs-lookup"><span data-stu-id="ac2a1-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of remote procedure call (RPC):</span></span>

- <span data-ttu-id="ac2a1-105">Prośba/odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ac2a1-105">Request/reply</span></span>
- <span data-ttu-id="ac2a1-106">Dupleksu:</span><span class="sxs-lookup"><span data-stu-id="ac2a1-106">Duplex:</span></span>
  - <span data-ttu-id="ac2a1-107">Dwupoziomowy sposób jednokierunkowy z sesją</span><span class="sxs-lookup"><span data-stu-id="ac2a1-107">One-way duplex with session</span></span>
  - <span data-ttu-id="ac2a1-108">Pełny dupleks z sesją</span><span class="sxs-lookup"><span data-stu-id="ac2a1-108">Full duplex with session</span></span>
- <span data-ttu-id="ac2a1-109">Jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="ac2a1-109">One-way</span></span>

<span data-ttu-id="ac2a1-110">Istnieje możliwość mapowania tych typów RPC dość naturalnie do istniejących koncepcji gRPC.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts.</span></span> <span data-ttu-id="ac2a1-111">W tym rozdziale przyjrzymy się z kolei każdemu z tych obszarów.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-111">This chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="ac2a1-112">[W rozdziale 5](migrate-wcf-to-grpc.md) zostaną szczegółowo zbadane podobne przykłady.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-112">[Chapter 5](migrate-wcf-to-grpc.md) will explore similar examples in greater depth.</span></span>

| <span data-ttu-id="ac2a1-113">WCF</span><span class="sxs-lookup"><span data-stu-id="ac2a1-113">WCF</span></span> | <span data-ttu-id="ac2a1-114">gRPC</span><span class="sxs-lookup"><span data-stu-id="ac2a1-114">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="ac2a1-115">Regularne żądanie/odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ac2a1-115">Regular request/reply</span></span> | <span data-ttu-id="ac2a1-116">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="ac2a1-116">Unary</span></span> |
| <span data-ttu-id="ac2a1-117">Usługa dupleksu z sesją przy użyciu interfejsu wywołania odwróconego klienta</span><span class="sxs-lookup"><span data-stu-id="ac2a1-117">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="ac2a1-118">Przesyłanie strumieniowe serwera</span><span class="sxs-lookup"><span data-stu-id="ac2a1-118">Server streaming</span></span> |
| <span data-ttu-id="ac2a1-119">Pełna usługa dupleksu z sesją</span><span class="sxs-lookup"><span data-stu-id="ac2a1-119">Full duplex service with session</span></span> | <span data-ttu-id="ac2a1-120">Dwukierunkowe przesyłanie strumieniowe</span><span class="sxs-lookup"><span data-stu-id="ac2a1-120">Bidirectional streaming</span></span> |
| <span data-ttu-id="ac2a1-121">Operacje jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="ac2a1-121">One-way operations</span></span> | <span data-ttu-id="ac2a1-122">Przesyłanie strumieniowe klienta</span><span class="sxs-lookup"><span data-stu-id="ac2a1-122">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="ac2a1-123">Prośba/odpowiedź</span><span class="sxs-lookup"><span data-stu-id="ac2a1-123">Request/reply</span></span>

<span data-ttu-id="ac2a1-124">W przypadku prostych metod żądania/odpowiedzi, które przyjmują i zwracają niewielkie ilości danych, użyj najprostszego wzorca gRPC, unary RPC.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-124">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

<span data-ttu-id="ac2a1-125">Jak widać, implementowanie metody usługi RPC unary gRPC jest podobny do implementowania operacji WCF.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-125">As you can see, implementing a gRPC unary RPC service method is similar to implementing a WCF operation.</span></span> <span data-ttu-id="ac2a1-126">Różnica polega na tym, że w przypadku gRPC można zastąpić metodę klasy podstawowej zamiast implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-126">The difference is that with gRPC, you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="ac2a1-127">Na serwerze metody podstawowe gRPC <xref:System.Threading.Tasks.Task%601>zawsze zwracają , chociaż klient udostępnia zarówno metody asynchroniczne, jak i blokujące wywołanie usługi.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-127">On the server, gRPC base methods always return <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="ac2a1-128">Dupleks WCF, jeden sposób na klienta</span><span class="sxs-lookup"><span data-stu-id="ac2a1-128">WCF duplex, one way to client</span></span>

<span data-ttu-id="ac2a1-129">Aplikacje WCF (z pewnymi powiązaniami) można utworzyć trwałe połączenie między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-129">WCF applications (with certain bindings) can create a persistent connection between client and server.</span></span> <span data-ttu-id="ac2a1-130">Serwer może asynchronicznie wysyłać dane do klienta, dopóki połączenie nie zostanie zamknięte, przy użyciu *interfejsu wywołania odwróconego* określonego we <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-130">The server can asynchronously send data to the client until the connection is closed, by using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="ac2a1-131">Usługi gRPC zapewniają podobną funkcjonalność ze strumieniami wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-131">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="ac2a1-132">Strumienie nie *mapują dokładnie* do usług dupleksu WCF pod względem implementacji, ale można osiągnąć te same wyniki.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-132">Streams don't map *exactly* to WCF duplex services in terms of implementation, but you can achieve the same results.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="ac2a1-133">przesyłanie strumieniowe gRPC</span><span class="sxs-lookup"><span data-stu-id="ac2a1-133">gRPC streaming</span></span>

<span data-ttu-id="ac2a1-134">gRPC obsługuje tworzenie strumieni trwałych z klienta na serwer i z serwera na klienta.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-134">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="ac2a1-135">Oba typy strumienia mogą być aktywne jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-135">Both types of stream can be active concurrently.</span></span> <span data-ttu-id="ac2a1-136">Ta zdolność jest nazywana dwukierunkowym przesyłaniem strumieniowym.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-136">This ability is called bidirectional streaming.</span></span>

<span data-ttu-id="ac2a1-137">Strumieni można używać do dowolnego, asynchronicznego przesyłania wiadomości w czasie.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-137">You can use streams for arbitrary, asynchronous messaging over time.</span></span> <span data-ttu-id="ac2a1-138">Lub można ich używać do przekazywania dużych zestawów danych, które są zbyt duże, aby wygenerować i wysłać w jednym żądaniu lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-138">Or you can use them for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="ac2a1-139">W poniższym przykładzie przedstawiono serwer-streaming RPC.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-139">The following example shows a server-streaming RPC.</span></span>

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

<span data-ttu-id="ac2a1-140">Ten strumień serwera może być używany z aplikacji klienckiej, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ac2a1-140">This server stream can be consumed from a client application, as shown in the following code:</span></span>

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> <span data-ttu-id="ac2a1-141">RPC przesyłania strumieniowego serwera są przydatne w przypadku usług w stylu subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-141">Server-streaming RPCs are useful for subscription-style services.</span></span> <span data-ttu-id="ac2a1-142">Są one również przydatne do wysyłania dużych zestawów danych, gdy byłoby nieefektywne lub niemożliwe do utworzenia całego zestawu danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-142">They're also useful for sending large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="ac2a1-143">Jednak odpowiedzi przesyłania strumieniowego nie `repeated` jest tak szybki, jak wysyłanie pól w jednej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-143">However, streaming responses isn't as fast as sending `repeated` fields in a single message.</span></span> <span data-ttu-id="ac2a1-144">Z reguły przesyłania strumieniowego nie powinny być używane dla małych zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-144">As a rule, streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-from-wcf"></a><span data-ttu-id="ac2a1-145">Różnice od WCF</span><span class="sxs-lookup"><span data-stu-id="ac2a1-145">Differences from WCF</span></span>

<span data-ttu-id="ac2a1-146">Usługa dupleksu WCF używa interfejsu wywołania odwróconego klienta, który może mieć wiele metod.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-146">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="ac2a1-147">Usługa przesyłania strumieniowego serwera gRPC może wysyłać wiadomości tylko za pomocą jednego strumienia.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-147">A gRPC server-streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="ac2a1-148">Jeśli potrzebujesz wielu metod, użyj typu wiadomości z [dowolnym polem lub jednym z pól,](protobuf-any-oneof.md) aby wysyłać różne wiadomości i napisać kod w kliencie, aby je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-148">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="ac2a1-149">W WCF [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) klasy z sesji jest utrzymywana przy życiu, dopóki połączenie jest zamknięte.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-149">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed.</span></span> <span data-ttu-id="ac2a1-150">Wiele metod można wywołać w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-150">Multiple methods can be called within the session.</span></span> <span data-ttu-id="ac2a1-151">W gRPC, `Task` że zwraca metodę implementacji nie należy kończyć, dopóki połączenie zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-151">In gRPC, the `Task` that the implementation method returns shouldn't finish until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="ac2a1-152">Operacje jednokierunkowe WCF i przesyłanie strumieniowe klienta gRPC</span><span class="sxs-lookup"><span data-stu-id="ac2a1-152">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="ac2a1-153">WCF zapewnia operacje jednokierunkowe `[OperationContract(IsOneWay = true)]`(oznaczone) które zwracają potwierdzenie specyficzne dla transportu.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-153">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="ac2a1-154">Metody serwisu gRPC zawsze zwracają odpowiedź, nawet jeśli jest pusta.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-154">gRPC service methods always return a response, even if it's empty.</span></span> <span data-ttu-id="ac2a1-155">Klient powinien zawsze oczekiwać na tę odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-155">The client should always await that response.</span></span> <span data-ttu-id="ac2a1-156">W przypadku stylu "fire-and-forget" wiadomości w gRPC można utworzyć usługę przesyłania strumieniowego klienta.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-156">For the "fire-and-forget" style of messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="ac2a1-157">thing_log.proto</span><span class="sxs-lookup"><span data-stu-id="ac2a1-157">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="ac2a1-158">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="ac2a1-158">ThingLogService.cs</span></span>

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a><span data-ttu-id="ac2a1-159">Przykład klienta ThingLog</span><span class="sxs-lookup"><span data-stu-id="ac2a1-159">ThingLog client example</span></span>

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

<span data-ttu-id="ac2a1-160">Do obsługi komunikatów fire-and-forget można używać strumieniowania klientów do obsługi komunikatów fire-and-forget, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-160">You can use client-streaming RPCs for fire-and-forget messaging, as shown in the previous example.</span></span> <span data-ttu-id="ac2a1-161">Można ich również używać do wysyłania bardzo dużych zestawów danych do serwera.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-161">You can also use them for sending very large datasets to the server.</span></span> <span data-ttu-id="ac2a1-162">Dotyczy to samo ostrzeżenie dotyczące wydajności: w `repeated` przypadku mniejszych zestawów danych należy używać pól w zwykłych wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-162">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="ac2a1-163">Usługi pełnego dupleksu WCF</span><span class="sxs-lookup"><span data-stu-id="ac2a1-163">WCF full-duplex services</span></span>

<span data-ttu-id="ac2a1-164">Powiązanie dupleksu WCF obsługuje wiele operacji jednokierunkowych zarówno w interfejsie usługi, jak i w interfejsie wywołania wywołania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-164">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface.</span></span> <span data-ttu-id="ac2a1-165">Ta obsługa umożliwia ciągłe konwersacje między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-165">This support allows ongoing conversations between client and server.</span></span> <span data-ttu-id="ac2a1-166">gRPC obsługuje coś podobnego z dwukierunkowymi strumieniowymi rpc, `stream` gdzie oba parametry są oznaczone modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-166">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="ac2a1-167">czat.proto</span><span class="sxs-lookup"><span data-stu-id="ac2a1-167">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="ac2a1-168">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="ac2a1-168">ChatterService.cs</span></span>

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

<span data-ttu-id="ac2a1-169">W poprzednim przykładzie widać, że metoda implementacji odbiera`IAsyncStreamReader<MessageRequest>`zarówno strumień żądania`IServerStreamWriter<MessageResponse>`( ) i strumień odpowiedzi ( ).</span><span class="sxs-lookup"><span data-stu-id="ac2a1-169">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`).</span></span> <span data-ttu-id="ac2a1-170">Metoda może odczytywać i zapisywać wiadomości, dopóki połączenie nie zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-170">The method can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="ac2a1-171">Klient chatter</span><span class="sxs-lookup"><span data-stu-id="ac2a1-171">Chatter client</span></span>

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
><span data-ttu-id="ac2a1-172">[Poprzedni](wcf-bindings.md)
>[następny](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="ac2a1-172">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
