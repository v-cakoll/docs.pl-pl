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
# <a name="types-of-rpc"></a>Typy zdalnych wywołań procedur

Jako deweloper Windows Communication Foundation (WCF) prawdopodobnie jesteś przyzwyczajony do obsługi następujących typów wywołań procedury zdalnej (RPC):

- Prośba/odpowiedź
- Dupleksu:
  - Dwupoziomowy sposób jednokierunkowy z sesją
  - Pełny dupleks z sesją
- Jednokierunkowe

Istnieje możliwość mapowania tych typów RPC dość naturalnie do istniejących koncepcji gRPC. W tym rozdziale przyjrzymy się z kolei każdemu z tych obszarów. [W rozdziale 5](migrate-wcf-to-grpc.md) zostaną szczegółowo zbadane podobne przykłady.

| WCF | gRPC |
| --- | ---- |
| Regularne żądanie/odpowiedź | Jednoargumentowy |
| Usługa dupleksu z sesją przy użyciu interfejsu wywołania odwróconego klienta | Przesyłanie strumieniowe serwera |
| Pełna usługa dupleksu z sesją | Dwukierunkowe przesyłanie strumieniowe |
| Operacje jednokierunkowe | Przesyłanie strumieniowe klienta |

## <a name="requestreply"></a>Prośba/odpowiedź

W przypadku prostych metod żądania/odpowiedzi, które przyjmują i zwracają niewielkie ilości danych, użyj najprostszego wzorca gRPC, unary RPC.

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

Jak widać, implementowanie metody usługi RPC unary gRPC jest podobny do implementowania operacji WCF. Różnica polega na tym, że w przypadku gRPC można zastąpić metodę klasy podstawowej zamiast implementować interfejs. Na serwerze metody podstawowe gRPC <xref:System.Threading.Tasks.Task%601>zawsze zwracają , chociaż klient udostępnia zarówno metody asynchroniczne, jak i blokujące wywołanie usługi.

## <a name="wcf-duplex-one-way-to-client"></a>Dupleks WCF, jeden sposób na klienta

Aplikacje WCF (z pewnymi powiązaniami) można utworzyć trwałe połączenie między klientem a serwerem. Serwer może asynchronicznie wysyłać dane do klienta, dopóki połączenie nie zostanie zamknięte, przy użyciu *interfejsu wywołania odwróconego* określonego we <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości.

Usługi gRPC zapewniają podobną funkcjonalność ze strumieniami wiadomości. Strumienie nie *mapują dokładnie* do usług dupleksu WCF pod względem implementacji, ale można osiągnąć te same wyniki.

### <a name="grpc-streaming"></a>przesyłanie strumieniowe gRPC

gRPC obsługuje tworzenie strumieni trwałych z klienta na serwer i z serwera na klienta. Oba typy strumienia mogą być aktywne jednocześnie. Ta zdolność jest nazywana dwukierunkowym przesyłaniem strumieniowym.

Strumieni można używać do dowolnego, asynchronicznego przesyłania wiadomości w czasie. Lub można ich używać do przekazywania dużych zestawów danych, które są zbyt duże, aby wygenerować i wysłać w jednym żądaniu lub odpowiedzi.

W poniższym przykładzie przedstawiono serwer-streaming RPC.

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

Ten strumień serwera może być używany z aplikacji klienckiej, jak pokazano w następującym kodzie:

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
> RPC przesyłania strumieniowego serwera są przydatne w przypadku usług w stylu subskrypcji. Są one również przydatne do wysyłania dużych zestawów danych, gdy byłoby nieefektywne lub niemożliwe do utworzenia całego zestawu danych w pamięci. Jednak odpowiedzi przesyłania strumieniowego nie `repeated` jest tak szybki, jak wysyłanie pól w jednej wiadomości. Z reguły przesyłania strumieniowego nie powinny być używane dla małych zestawów danych.

### <a name="differences-from-wcf"></a>Różnice od WCF

Usługa dupleksu WCF używa interfejsu wywołania odwróconego klienta, który może mieć wiele metod. Usługa przesyłania strumieniowego serwera gRPC może wysyłać wiadomości tylko za pomocą jednego strumienia. Jeśli potrzebujesz wielu metod, użyj typu wiadomości z [dowolnym polem lub jednym z pól,](protobuf-any-oneof.md) aby wysyłać różne wiadomości i napisać kod w kliencie, aby je obsłużyć.

W WCF [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) klasy z sesji jest utrzymywana przy życiu, dopóki połączenie jest zamknięte. Wiele metod można wywołać w ramach sesji. W gRPC, `Task` że zwraca metodę implementacji nie należy kończyć, dopóki połączenie zostanie zamknięte.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Operacje jednokierunkowe WCF i przesyłanie strumieniowe klienta gRPC

WCF zapewnia operacje jednokierunkowe `[OperationContract(IsOneWay = true)]`(oznaczone) które zwracają potwierdzenie specyficzne dla transportu. Metody serwisu gRPC zawsze zwracają odpowiedź, nawet jeśli jest pusta. Klient powinien zawsze oczekiwać na tę odpowiedź. W przypadku stylu "fire-and-forget" wiadomości w gRPC można utworzyć usługę przesyłania strumieniowego klienta.

### <a name="thing_logproto"></a>thing_log.proto

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

Do obsługi komunikatów fire-and-forget można używać strumieniowania klientów do obsługi komunikatów fire-and-forget, jak pokazano w poprzednim przykładzie. Można ich również używać do wysyłania bardzo dużych zestawów danych do serwera. Dotyczy to samo ostrzeżenie dotyczące wydajności: w `repeated` przypadku mniejszych zestawów danych należy używać pól w zwykłych wiadomościach.

## <a name="wcf-full-duplex-services"></a>Usługi pełnego dupleksu WCF

Powiązanie dupleksu WCF obsługuje wiele operacji jednokierunkowych zarówno w interfejsie usługi, jak i w interfejsie wywołania wywołania przez klienta. Ta obsługa umożliwia ciągłe konwersacje między klientem a serwerem. gRPC obsługuje coś podobnego z dwukierunkowymi strumieniowymi rpc, `stream` gdzie oba parametry są oznaczone modyfikatorem.

### <a name="chatproto"></a>czat.proto

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

W poprzednim przykładzie widać, że metoda implementacji odbiera`IAsyncStreamReader<MessageRequest>`zarówno strumień żądania`IServerStreamWriter<MessageResponse>`( ) i strumień odpowiedzi ( ). Metoda może odczytywać i zapisywać wiadomości, dopóki połączenie nie zostanie zamknięte.

### <a name="chatter-client"></a>Klient chatter

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
>[następny](metadata.md)
