---
title: Migrowanie usług programu WCF Duplex do gRPC-gRPC dla deweloperów programu WCF
description: Dowiedz się, jak migrować różne formy usługi programu WCF Duplex do usługi gRPC Streaming Services.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1702c9f7659f056af9009e81847f28c6e65b277c
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846602"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a>Migrowanie usług dwukierunkowych WCF do usługi gRPC

Teraz, gdy podstawowe koncepcje są stosowane, ta sekcja będzie wyglądać na bardziej skomplikowane usługi *przesyłania strumieniowego* gRPC.

Istnieje wiele sposobów używania usług dupleksowych w Windows Communication Foundation (WCF). Niektóre usługi są inicjowane przez klienta, a następnie przesyłają strumieniowo dane z serwera. Inne usługi o pełnym dupleksie mogą pociągnąć za sobą więcej trwających dwukierunkowej komunikacji, takich jak klasyczny przykład "Kalkulator" z dokumentacji programu WCF. Ten rozdział zajmie się dwoma możliwymi implementacjami "cykl giełdowy" platformy WCF i migruje je do gRPC: jeden przy użyciu protokołu RPC przesyłania strumieniowego serwera, a drugi przy użyciu dwukierunkowego wywołania RPC przesyłania strumieniowego.

## <a name="server-streaming-rpc"></a>Serwer RPC przesyłania strumieniowego

W [przykładowym rozwiązaniu SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker) *SimpleStockPriceTicker*, dostępna jest usługa dupleksowa, w której klient uruchamia połączenie z listą symboli magazynowych, a serwer używa *interfejsu wywołania zwrotnego* do wysyłania aktualizacji staną się dostępne. Klient implementuje ten interfejs, aby odpowiedzieć na wywołania z serwera.

### <a name="the-wcf-solution"></a>Rozwiązanie WCF

Rozwiązanie WCF jest zaimplementowane jako samodzielny serwer NetTCP w aplikacji konsolowej programu .NET Framework 4. x.

#### <a name="the-servicecontract"></a>ServiceContract

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

Usługa ma pojedynczą metodę bez zwracanego typu, ponieważ będzie używać interfejsu wywołania zwrotnego `ISimpleStockTickerCallback` do wysyłania danych do klienta w czasie rzeczywistym.

#### <a name="the-callback-interface"></a>Interfejs wywołania zwrotnego

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

Implementacje tych interfejsów można znaleźć w rozwiązaniu wraz z niektórymi zewnętrznymi zależnościami w celu zapewnienia danych testowych.

### <a name="grpc-streaming"></a>gRPC Streaming

GRPC sposób obsługi danych w czasie rzeczywistym jest różny. Wywołanie z klienta do serwera może utworzyć trwały strumień, który może być monitorowany w przypadku komunikatów przychodzących asynchronicznie. Pomimo różnic między strumieniami może być bardziej intuicyjny sposób postępowania z danymi i są one bardziej istotne w nowoczesnych programowaniu, z naciskiem na LINQ, reaktywne strumienie, programowanie funkcjonalne i tak dalej.

Definicja usługi wymaga dwóch komunikatów: jeden dla żądania oraz jeden dla strumienia. Usługa zwraca strumień komunikatu `StockTickerUpdate` za pomocą słowa kluczowego `stream` w swojej deklaracji `return`. Zaleca się dodanie `Timestamp` do aktualizacji w celu pokazywania dokładnego czasu zmiany ceny.

#### <a name="simple_stock_tickerproto"></a>simple_stock_ticker. proto

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-the-simplestockticker"></a>Implementowanie SimpleStockTicker

Ponownie Użyj fałszywej `StockPriceSubscriber` z projektu WCF, kopiując trzy klasy z biblioteki klas `TraderSys.StockMarket` do nowej biblioteki klas .NET Standard w rozwiązaniu docelowym. Aby lepiej stosować najlepsze rozwiązania, Dodaj `Factory` typ, aby utworzyć wystąpienia go i zarejestrować `IStockPriceSubscriberFactory` za pomocą usług iniekcji zależności ASP.NET Core.

#### <a name="the-factory-implementation"></a>Implementacja fabryki

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="registering-the-factory"></a>Rejestrowanie fabryki

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

Teraz można użyć tej klasy do zaimplementowania usługi gRPC StockTicker.

#### <a name="stocktickerservicecs"></a>StockTickerService.cs

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors due to broken connection etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

Jak widać, chociaż deklaracja w pliku `.proto` informuje o metodzie "zwraca" strumień komunikatów `StockTickerUpdate`, w rzeczywistości zwraca `Task` Wanili. Zadanie tworzenia strumienia jest obsługiwane przez wygenerowany kod i biblioteki środowiska uruchomieniowego gRPC, które zapewniają strumień odpowiedzi `IServerStreamWriter<StockTickerUpdate>`, gotowy do użycia.

W przeciwieństwie do usługi WCF Duplex, w której wystąpienie klasy usługi jest utrzymywane, gdy połączenie jest otwarte, usługa gRPC używa zwracanego zadania, aby zachować aktywność usługi. Zadanie nie powinno zostać ukończone do momentu zamknięcia połączenia.

Usługa może określić, kiedy klient zamknął połączenie przy użyciu `CancellationToken` z `ServerCallContext`. Prosta metoda statyczna `AwaitCancellation` jest używana do tworzenia zadania, które kończy się po anulowaniu tokenu.

W metodzie `Subscribe` należy uzyskać `StockPriceSubscriber` i dodać program obsługi zdarzeń, który zapisuje dane w strumieniu odpowiedzi. Następnie poczekaj na zamknięcie połączenia przed natychmiastowe usunięciem `subscriber`, aby zapobiec próbie zapisu danych do zamkniętego strumienia.

Metoda `WriteUpdateAsync` ma `try` / `catch` bloku, aby obsłużyć wszelkie błędy, które mogą wystąpić podczas zapisywania komunikatu w strumieniu. Jest to ważne zagadnienie w przypadku trwałych połączeń za pośrednictwem sieci, które mogą być uszkodzone w dowolnym milisekundach, niezależnie od tego, czy wystąpił błąd w dowolnym miejscu.

### <a name="using-the-stocktickerservice-from-a-client-application"></a>Korzystanie z StockTickerService z aplikacji klienckiej

Wykonaj te same czynności w poprzedniej sekcji, aby utworzyć bibliotekę klas klienta możliwej do udostępnienia z pliku `.proto`. W przykładzie znajduje się Aplikacja konsolowa programu .NET Core 3,0, która pokazuje, jak korzystać z klienta programu.

#### <a name="example-programcs"></a>Przykład Program.cs

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

W takim przypadku Metoda `Subscribe` wygenerowanego klienta nie jest asynchroniczna. Strumień jest tworzony i można go używać od razu, ponieważ jego Metoda `MoveNext` jest asynchroniczna i po raz pierwszy jest wywoływana, dopóki połączenie nie będzie aktywne.

Strumień jest przesyłany do asynchronicznej metody `DisplayAsync`; aplikacja czeka, aż użytkownik naciśnie klawisz, a następnie anuluje metodę `DisplayAsync` i czeka na ukończenie zadania przed wyjściem.

> [!NOTE]
> Ten kod używa składni New C# 8 "Using deklaracji", aby usunąć strumień i kanał, gdy metoda `Main` zostanie zakończona. Jest to mała zmiana, ale całkiem taka, która zmniejsza wcięcia i puste wiersze.

#### <a name="consume-the-stream"></a>Korzystanie z strumienia

Funkcja WCF użyła interfejsów wywołania zwrotnego, aby umożliwić serwerowi wywoływanie metod bezpośrednio na kliencie. strumienie gRPC działają inaczej. Klient wykonuje iterację na zwracanym strumieniu i przetwarza komunikaty, tak jakby były zwracane z metody lokalnej zwracającej `IEnumerable`.

Typ `IAsyncStreamReader<T>` działa podobnie do `IEnumerator<T>`: istnieje metoda `MoveNext`, która zwróci wartość PRAWDA, o ile istnieje więcej danych, a właściwość `Current`, która zwraca najnowszą wartość. Jedyną różnicą jest to, że metoda `MoveNext` zwraca `Task<bool>` zamiast tylko `bool`. Metoda rozszerzenia `ReadAllAsync` otacza strumień w standardowym C# 8 `IAsyncEnumerable`, który może być używany z nową składnią `await foreach`.

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> Sekcja [biblioteki klienckie](client-libraries.md#iobservable) na końcu tego rozdziału przedstawia sposób dodawania metody rozszerzenia i klas do zawijania `IAsyncStreamReader<T>` w `IObservable<T>` dla deweloperów korzystających z reaktywnych wzorców programistycznych.

Ponownie należy zachować ostrożność, aby przechwytywać wyjątki w tym miejscu ze względu na możliwość awarii sieci, a także <xref:System.OperationCanceledException>, które będą nieuniknione, ponieważ kod używa <xref:System.Threading.CancellationToken> do przerwania pętli. Typ `RpcException` zawiera wiele przydatnych informacji o błędach środowiska uruchomieniowego gRPC, w tym `StatusCode`. Aby uzyskać więcej informacji, zobacz [ *Obsługa błędów* w rozdziale 4](error-handling.md).

## <a name="bidirectional-streaming"></a>Przesyłanie strumieniowe dwukierunkowe

Usługa WCF Full-Duplex umożliwia asynchroniczne wysyłanie komunikatów w czasie rzeczywistym w obu kierunkach. W przykładzie przesyłania strumieniowego serwera klient uruchamia żądanie, a następnie odbiera strumień aktualizacji. Lepsza wersja tej usługi pozwala klientowi dodawać i usuwać zasoby z listy bez konieczności zatrzymywania i tworzenia nowej subskrypcji. Ta funkcja została zaimplementowana w [przykładowym rozwiązaniu FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).

Interfejs `IFullStockTickerService` udostępnia trzy metody:

- `Subscribe` uruchamia połączenie.
- `AddSymbol` dodaje symbol giełdowy do obserwowania.
- `RemoveSymbol` usuwa symbol z listy obserwowanych.

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

Interfejs wywołania zwrotnego pozostaje taki sam.

Implementacja tego wzorca w gRPC jest mniej prosta, ponieważ istnieją teraz dwa strumienie danych z przekazywaniem komunikatów: jeden z klienta do serwera, a drugi z serwera do klienta. Nie jest możliwe użycie wielu metod w celu zaimplementowania operacji dodawania i usuwania, ale więcej niż jeden typ komunikatu może być przekazano do pojedynczego strumienia przy użyciu typu `Any` lub słowa kluczowego `oneof`, które zostały omówione w [rozdziale 3](protobuf-any-oneof.md).

W przypadku gdy istnieje konkretny zestaw typów, które są akceptowalne, `oneof` jest lepszym rozwiązaniem. Użyj `ActionMessage`, która może zawierać `AddSymbolRequest` lub `RemoveSymbolRequest`.

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

Zadeklaruj dwukierunkową usługę przesyłania strumieniowego, która pobiera strumień komunikatów `ActionMessage`.

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

Implementacja tej usługi jest podobna do powyższego przykładu, z wyjątkiem pierwszego parametru metody `Subscribe` jest teraz `IAsyncStreamReader<ActionMessage>`, która może służyć do obsługi żądań `Add` i `Remove`.

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors due to broken connection etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

Klasa `ActionMessage`, która gRPC wygenerowała gwarancje dla Stanów Zjednoczonych, że można ustawić tylko jedną z właściwości `Add` i `Remove` oraz znaleźć, która z nich nie `null` jest prawidłowym sposobem wyszukiwania, który typ komunikatu jest używany , ale istnieje lepszy sposób. Generowanie kodu spowodowało również utworzenie `enum ActionOneOfCase` w klasie `ActionMessage`, która wygląda następująco:

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

Właściwość `ActionCase` w obiekcie `ActionMessage` może być używana z instrukcją `switch`, aby określić, które pole jest ustawione.

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> W instrukcji `switch` występuje `default` przypadek, który rejestruje ostrzeżenie w przypadku napotkania nieznanej wartości `ActionOneOfCase`. Może to być przydatne w przypadku, gdy klient korzysta z nowszej wersji pliku `.proto`, który dodał więcej akcji. Jest to jeden z powodów, dla których użycie `switch` jest lepszym rozwiązaniem niż testowanie `null` w znanych polach.

### <a name="use-the-fullstocktickerservice-from-a-client-application"></a>Korzystanie z FullStockTickerService z aplikacji klienckiej

Istnieje prosta aplikacja WPF platformy .NET Core 3,0, która przedstawia użycie tego bardziej złożonego klienta. Pełną aplikację można znaleźć [w witrynie GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).

Klient jest używany w klasie `MainWindowViewModel`, która pobiera wystąpienie typu `FullStockTicker.FullStockTickerClient` z iniekcji zależności.

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

Obiekt zwrócony przez metodę `client.Subscribe()` jest teraz wystąpieniem typu biblioteki gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>`, który udostępnia `RequestStream` do wysyłania żądań do serwera i `ResponseStream` do obsługi odpowiedzi.

Strumień żądania jest używany z niektórych metod `ICommand` WPF do dodawania i usuwania symboli. Dla każdej operacji Ustaw odpowiednie pole na `ActionMessage` obiekcie:

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> Ustawienie wartości pola `oneof` w komunikacie automatycznie czyści wszystkie pola, które zostały wcześniej ustawione.

Strumień odpowiedzi jest obsługiwany w metodzie `async`, a `Task` zwracana jest zatrzymywana do usunięcia, gdy okno zostanie zamknięte.

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-clean-up"></a>Czyszczenie klienta

Po zamknięciu okna i usunięciu `MainWindowViewModel` (ze zdarzenia `Closed` `MainWindow`) zaleca się poprawne usuwanie obiektu `AsyncDuplexStreamingCall`. W szczególności Metoda `CompleteAsync` na `RequestStream` powinna zostać wywołana, aby bezpiecznie zamknąć strumień na serwerze. Poniższy przykład przedstawia metodę `DisposeAsync` z widoku przykład-model:

```csharp
public ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

Zamykające strumienie żądań umożliwia serwerowi usuwanie własnych zasobów w odpowiednim czasie. Poprawia to wydajność i skalowalność usług i zapobiega wyjątkom.

>[!div class="step-by-step"]
>[Poprzedni](migrate-request-reply.md)
>[Następny](streaming-versus-repeated.md)
