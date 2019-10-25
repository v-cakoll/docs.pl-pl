---
title: Typy RPC-gRPC dla deweloperów WCF
description: Przegląd typów zdalnego wywołania procedury obsługiwanego przez program WCF i ich odpowiedników w gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ce5bf03b01dff3f7bb201ff08c9065abc2e58360
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846228"
---
# <a name="types-of-rpc"></a>Typy zdalnych wywołań procedur

Jako deweloper Windows Communication Foundation (WCF) prawdopodobnie używasz następujących typów zdalnego wywołania procedury (RPC):

- Żądanie/odpowiedź
- Stron
  - Jednokierunkowa dupleks z sesją
  - Pełny dupleks z sesją
- Jednokierunkowe

Istnieje możliwość mapowania tych typów RPC w sposób naturalny do istniejących koncepcji gRPC, a ten rozdział będzie wyglądać na każdej z tych obszarów z kolei. Podobne przykłady zostaną omówione na znacznie większej głębokości w [rozdziale 5](migrate-wcf-to-grpc.md).

| WCF | gRPC |
| --- | ---- |
| Regularne żądanie/odpowiedź | Jednostk |
| Usługa dupleksowa z sesją przy użyciu interfejsu wywołania zwrotnego klienta | Przesyłanie strumieniowe serwera |
| Usługa pełnego dupleksu z sesją | Przesyłanie strumieniowe dwukierunkowe |
| Operacje jednokierunkowe | Przesyłanie strumieniowe klienta |

## <a name="requestreply"></a>Żądanie/odpowiedź

W przypadku prostych metod żądania/odpowiedzi, które pobierają i zwracają małe ilości danych, należy użyć najprostszego wzorca gRPC, jednoargumentowego wywołania RPC.

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

Jak widać, implementacja metody gRPC jednoargumentowej usługi RPC jest bardzo podobna do implementowania operacji WCF, z wyjątkiem tego, że z gRPC przesłonić metodę klasy bazowej zamiast implementować interfejs. Należy pamiętać, że na serwerze gRPC metody podstawowe zawsze zwracają <xref:System.Threading.Tasks.Task%601>, chociaż klient zapewnia metody asynchroniczne i blokujące do wywoływania usługi.

## <a name="wcf-duplex-one-way-to-client"></a>Tryb dupleksu WCF — jednokierunkowe dla klienta

Aplikacje WCF (z pewnymi powiązaniami) mogą utworzyć trwałe połączenie między klientem i serwerem, a serwer może asynchronicznie wysyłać dane do klienta do momentu zamknięcia połączenia przy użyciu *interfejsu wywołania zwrotnego* określonego w <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> wartość.

usługi gRPC Services zapewniają podobną funkcjonalność przy użyciu strumieni komunikatów. Strumienie nie mapują *dokładnie* na usługi WCF w warunkach implementacji, ale można osiągnąć te same wyniki.

### <a name="grpc-streaming"></a>gRPC Streaming

Program gRPC obsługuje tworzenie strumieni trwałych z klienta na serwer oraz z serwera na klienta. Oba typy strumieni mogą być aktywne współbieżnie; jest to nazywane dwukierunkową transmisją. Strumienie mogą służyć do dowolnych, asynchronicznych komunikatów w czasie lub do przekazywania dużych zestawów danych, które są zbyt duże, aby generować i wysyłać w ramach pojedynczego żądania lub odpowiedzi.

Poniższy przykład przedstawia serwer RPC przesyłania strumieniowego serwera.

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

Ten strumień serwera może być wykorzystany z aplikacji klienckiej, jak pokazano w poniższym kodzie:

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
> Wywołania RPC przesyłania strumieniowego serwera są przydatne w przypadku usług w stylu subskrypcji, a także do wysyłania bardzo dużych zestawów danych, gdy byłyby one niewydajne lub niemożliwe do skompilowania całego DataSet w pamięci. Jednak odpowiedzi na przesyłanie strumieniowe nie są tak szybkie jak wysyłanie `repeated` pól w pojedynczym komunikacie, więc w przypadku małych zestawów danych nie należy używać przesyłania strumieniowego.

### <a name="differences-to-wcf"></a>Różnice w programie WCF

Usługa WCF Duplex korzysta z interfejsu wywołania zwrotnego klienta, który może mieć wiele metod. Usługa przesyłania strumieniowego serwera gRPC może wysyłać komunikaty tylko przez jeden strumień. Jeśli potrzebujesz wielu metod, użyj typu komunikatu z [dowolnym polem lub jednym z pól](protobuf-any-oneof.md) , aby wysłać różne komunikaty, a następnie napisz kod w kliencie, aby je obsłużyć.

W programie WCF Klasa [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) z sesją jest utrzymywana, dopóki połączenie nie zostanie zamknięte, a wiele metod może być wywoływanych w ramach sesji. W gRPC `Task` zwrócone przez metodę implementacji nie powinny zostać ukończone do momentu zamknięcia połączenia.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Operacje jednokierunkowe w programie WCF i gRPC Streaming klienta

Funkcja WCF oferuje jednokierunkowe operacje (oznaczone `[OperationContract(IsOneWay = true)]`), które zwracają potwierdzenie specyficzne dla transportu. metody usługi gRPC zawsze zwracają odpowiedź, nawet jeśli są puste, a klient zawsze powinien oczekiwać na tę odpowiedź. W przypadku komunikatów w stylu "Uruchom i zapomnij" w programie gRPC można utworzyć usługę przesyłania strumieniowego klienta.

### <a name="thing_logproto"></a>thing_log. proto

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a>ThingLogService.cs

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

### <a name="thinglog-client-example"></a>Przykład klienta ThingLog

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

Ponownie wywołania RPC przesyłania strumieniowego klientów mogą być używane do obsługi komunikatów na potrzeby uruchamiania i zapomnień, jak pokazano w poprzednim przykładzie, ale również do wysyłania bardzo dużych zestawów danych do serwera. To samo ostrzeżenie o wydajności dotyczy: w przypadku mniejszych zestawów danych Użyj `repeated` pól w zwykłych wiadomościach.

## <a name="wcf-full-duplex-services"></a>Usługi WCF Full Duplex

Powiązanie dupleksowe WCF obsługuje wiele operacji jednokierunkowych w interfejsie usługi i interfejsie wywołania zwrotnego klienta, co pozwala na ciągłe konwersacje między klientem i serwerem. gRPC obsługuje coś podobnego do dwukierunkowych wywołań RPC przesyłania strumieniowego, gdzie oba parametry są oznaczone modyfikatorem `stream`.

### <a name="chatproto"></a>Chat. proto

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a>ChatterService.cs

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

W poprzednim przykładzie widać, że metoda implementacji odbiera strumień żądania (`IAsyncStreamReader<MessageRequest>`) i strumień odpowiedzi (`IServerStreamWriter<MessageResponse>`) i może odczytywać i zapisywać komunikaty do momentu zamknięcia połączenia.

### <a name="chatter-client"></a>Klient rozmawiający

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
>[Poprzedni](wcf-bindings.md)
>[Następny](metadata.md)
