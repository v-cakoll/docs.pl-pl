---
title: Rodzaje RPC - gRPC dla programistów WCF
description: Przegląd rodzajów zdalnych połączeń procedur obsługiwanych przez WCF i ich odpowiedników w gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 40c0779dc015904e9dabbb448075e3c5aa5dc49a
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111091"
---
# <a name="types-of-rpc"></a>Typy zdalnych wywołań procedur

Jako programista Windows Communication Foundation (WCF) prawdopodobnie jesteś przyzwyczajony do radzenia sobie z następującymi typami zdalnego wywołania procedury (RPC):

- Wniosek/odpowiedź
- Dupleksu:
  - Jednokierunkowy dupleks z sesją
  - Pełny dupleks z sesją
- Jednokierunkowe

Możliwe jest mapowanie tych typów RPC dość naturalnie na istniejące koncepcje gRPC. W tym rozdziale przyjrzymy się z kolei każdemu z tych obszarów. [Rozdział 5](migrate-wcf-to-grpc.md) będzie dogłębnie badał podobne przykłady.

| WCF | grpc |
| --- | ---- |
| Regularne żądanie/odpowiedź | Jednoargumentowy |
| Usługa dupleksu z sesją przy użyciu interfejsu wywołania zwrotnego klienta | Przesyłanie strumieniowe serwera |
| Pełna usługa dupleksu z sesją | Dwukierunkowe przesyłanie strumieniowe |
| Operacje jednokierunkowe | Przesyłanie strumieniowe klienta |

## <a name="requestreply"></a>Wniosek/odpowiedź

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

Jak widać, implementowanie metody usługi GRPC unary RPC jest podobne do implementowania operacji WCF. Różnica polega na tym, że w gRPC można zastąpić metodę klasy podstawowej zamiast implementowania interfejsu. Na serwerze metody podstawowe gRPC zawsze zwracają <xref:System.Threading.Tasks.Task%601>, chociaż klient udostępnia zarówno metody asynchronii, jak i blokowania, aby wywołać usługę.

## <a name="wcf-duplex-one-way-to-client"></a>WCF duplex, jeden sposób na klienta

Aplikacje WCF (z określonymi powiązaniami) można utworzyć trwałe połączenie między klientem a serwerem. Serwer może asynchronicznie wysyłać dane do klienta, dopóki połączenie nie zostanie zamknięte, za pomocą *interfejsu wywołania zwrotnego* <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> określonego we właściwości.

Usługi gRPC zapewniają podobną funkcjonalność ze strumieniami komunikatów. Strumienie nie mapują *dokładnie* usług dupleksu WCF pod względem implementacji, ale można osiągnąć takie same wyniki.

### <a name="grpc-streaming"></a>Strumieniowanie gRPC

GRPC obsługuje tworzenie trwałych strumieni z klienta na serwer oraz z serwera do klienta. Oba typy strumienia mogą być aktywne jednocześnie. Ta możliwość jest nazywana dwukierunkowym strumieniowaniem.

Można użyć strumieni dla dowolnego, asynchroniiowe wiadomości w czasie. Można ich użyć do przekazywania dużych zestawów danych, które są zbyt duże, aby wygenerować i wysłać w jednym żądaniu lub odpowiedzi.

W poniższym przykładzie przedstawiono rpc przesyłania strumieniowego serwera.

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

Ten strumień serwera może być zużywany z aplikacji klienckiej, jak pokazano w poniższym kodzie:

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
> Kontrolery RPC przesyłane strumieniowo serwera są przydatne w przypadku usług w stylu subskrypcji. Są one również przydatne do wysyłania dużych zestawów danych, gdy byłoby nieefektywne lub niemożliwe do utworzenia całego zestawu danych w pamięci. Jednak przesyłanie strumieniowe odpowiedzi nie `repeated` jest tak szybkie, jak wysyłanie pól w jednej wiadomości. Z reguły przesyłanie strumieniowe nie powinno być używane dla małych zestawów danych.

### <a name="differences-from-wcf"></a>Różnice w stosunku do WCF

Usługa dupleksu WCF używa interfejsu wywołania zwrotnego klienta, który może mieć wiele metod. Usługa przesyłania strumieniowego serwera gRPC może wysyłać wiadomości tylko za pomocą jednego strumienia. Jeśli potrzebujesz wielu metod, użyj typu wiadomości z [polem Any lub jednym z pól,](protobuf-any-oneof.md) aby wysyłać różne wiadomości i napisz kod w kliencie, aby je obsłużyć.

W WCF [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) klasy z sesji jest utrzymywana przy życiu, dopóki połączenie jest zamknięty. Wiele metod można wywołać w ramach sesji. W gRPC, `Task` że metoda implementacji zwraca nie należy zakończyć, dopóki połączenie zostanie zamknięte.

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a>Operacje w trybie jednokierunkowym WCF i przesyłanie strumieniowe klientów gRPC

WCF zapewnia operacje jednokierunkowe `[OperationContract(IsOneWay = true)]`(oznaczone ), które zwracają potwierdzenie specyficzne dla transportu. Metody usługi gRPC zawsze zwracają odpowiedź, nawet jeśli jest pusta. Klient powinien zawsze czekać na tę odpowiedź. Dla "fire-and-forget" styl wiadomości w gRPC, można utworzyć usługę przesyłania strumieniowego klienta.

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

Można użyć kontrolerów RPC przesyłania strumieniowego klienta do obsługi wiadomości typu fire-and-forget, jak pokazano w poprzednim przykładzie. Można ich również używać do wysyłania bardzo dużych zestawów danych na serwer. To samo ostrzeżenie o wydajności ma zastosowanie: `repeated` w przypadku mniejszych zestawów danych należy używać pól w zwykłych komunikatach.

## <a name="wcf-full-duplex-services"></a>Usługi WCF w trybie pełnego dupleksu

Powiązanie dupleksu WCF obsługuje wiele operacji jednokierunkowych zarówno w interfejsie usługi, jak i interfejsie wywołania zwrotnego klienta. Ta obsługa umożliwia prowadzenie konwersacji między klientem a serwerem. gRPC obsługuje coś podobnego z dwukierunkowymi strumieniowaniem RPC, gdzie oba parametry są oznaczone modyfikatorem. `stream`

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

W poprzednim przykładzie widać, że metoda implementacji odbiera`IAsyncStreamReader<MessageRequest>`zarówno strumień żądań ( ) i strumień odpowiedzi (`IServerStreamWriter<MessageResponse>`). Metoda może odczytywać i zapisywać wiadomości, dopóki połączenie nie zostanie zamknięte.

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
