---
title: Migrowanie usługi żądania WCF-odpowiedź do gRPC-gRPC dla deweloperów WCF
description: Dowiedz się, jak migrować prostą usługę żądanie-odpowiedź z programu WCF do gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 018aa94a15cdcb1e0f559afb7b3a88cd4f915398
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628556"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Migrowanie usługi żądania WCF-odpowiedź do gRPC jednoargumentowego wywołania procedury

W tej sekcji opisano sposób migrowania podstawowej usługi żądania-odpowiedzi w programie WCF do jednoargumentowej usługi RPC w ASP.NET Core gRPC. Te usługi są najprostszymi typami usług w obu Windows Communication Foundation (WCF) i gRPC, więc jest to doskonałe miejsce do uruchomienia. Po przeprowadzeniu migracji usługi dowiesz się, jak wygenerować bibliotekę kliencką z tego samego pliku `.proto`, aby korzystać z usługi z aplikacji klienckiej platformy .NET.

## <a name="the-wcf-solution"></a>Rozwiązanie WCF

[Rozwiązanie PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) obejmuje prostą usługę portfolio żądanie-odpowiedź do pobrania pojedynczego portfolio lub wszystkich portfolio dla danego podmiotu gospodarczego. Usługa jest definiowana w interfejsie `IPortfolioService` z atrybutem `ServiceContract`:

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

Model `Portfolio` to prosta C# Klasa oznaczona przy użyciu [schematu DataContract](xref:System.Runtime.Serialization.DataContractAttribute) , która obejmuje listę obiektów `PortfolioItem`. Modele te są zdefiniowane w projekcie `TraderSys.PortfolioData` wraz z klasą repozytorium, która reprezentuje abstrakcję dostępu do danych.

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

Implementacja `ServiceContract` używa klasy repozytorium dostarczonej przez iniekcję zależności, która zwraca wystąpienia typów `DataContract`:

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>Plik portfolio. proto

Jeśli wykonano instrukcje w poprzedniej sekcji, powinien istnieć projekt gRPC z plikiem `portfolios.proto`, który wygląda następująco:

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

Pierwszym krokiem jest Migrowanie klas `DataContract` do ich odpowiedników protobuf.

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a>Konwertowanie klas DataContract na komunikaty gRPC

Klasa `PortfolioItem` zostanie najpierw przekonwertowana na komunikat protobuf, ponieważ zależy od niej Klasa `Portfolio`. Klasa jest prosta i trzy właściwości są mapowane bezpośrednio do typów danych gRPC. Właściwość `Cost`, która przedstawia cenę płatną za udział w zakupie, jest polem `decimal`. gRPC obsługuje tylko `float` lub `double` dla liczb rzeczywistych, które nie są odpowiednie dla waluty. Ze względu na to, że ceny udziałów są różne dla co najmniej jednego centa, koszt może być wyrażony jako `int32` centów.

> [!NOTE]
> Pamiętaj, aby używać camelCase nazw pól w pliku `.proto`. Generator C# kodu wykona konwersję na PascalCase dla Ciebie, a użytkownicy innych języków poinformują Cię o poszanowaniu różnych standardów kodowania.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

Klasa `Portfolio` jest nieco bardziej skomplikowana. W kodzie WCF deweloper użył `Guid` dla właściwości `TraderId` i zawiera `List<PortfolioItem>`. W protobuf, który nie ma typu `UUID` pierwszej klasy, należy użyć `string` dla pola `traderId` i przeanalizować go w własnym kodzie. Dla listy elementów należy użyć słowa kluczowego `repeated` w polu.

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

Teraz, gdy masz komunikaty dotyczące danych, możesz zadeklarować punkty końcowe usługi RPC.

## <a name="convert-servicecontract-to-a-grpc-service"></a>Konwertuj kontrakt ServiceContract na usługę gRPC

Metoda `Get` WCF przyjmuje dwa parametry: `Guid traderId` i `int portfolioId`. metody usługi gRPC mogą przyjmować tylko jeden parametr, dlatego należy utworzyć komunikat, aby przechowywać dwie wartości. Typowym podejściem jest nazwa tych obiektów żądania o tej samej nazwie co metoda, po której następuje sufiks `Request`. Ponownie `string` jest używany dla pola `traderId` zamiast `Guid`.

Usługa może po prostu zwrócić komunikat `Portfolio` bezpośrednio, ale może to mieć wpływ na zgodność z poprzednimi wersjami w przyszłości. Dobrym sposobem jest zdefiniowanie oddzielnych `Request` i `Response` komunikatów dla każdej metody w usłudze, nawet jeśli wiele z nich jest teraz tego samego. W związku z tym deklaruj `GetResponse` komunikat z pojedynczym polem `Portfolio`.

Ten przykład przedstawia deklarację metody usługi gRPC z komunikatem `GetRequest`:

```protobuf
message GetRequest {
    string trader_id = 1;
    int32 portfolio_id = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

Metoda `GetAll` WCF przyjmuje tylko jeden parametr `traderId`, dlatego może wydawać się, że można określić `string` jako typ parametru. Ale gRPC wymaga zdefiniowanego typu wiadomości. To wymaganie umożliwia wymuszenie użycia niestandardowych komunikatów dla wszystkich danych wejściowych i wyjściowych w celu zachowania zgodności z poprzednimi wersjami.

Metoda WCF zwraca również `List<Portfolio>`, ale z tego samego powodu nie zezwala na proste typy parametrów, gRPC nie zezwoli `repeated Portfolio` jako zwracany typ. Zamiast tego Utwórz `GetAllResponse` typ, aby otoczyć listę.

> [!WARNING]
> Być może chcesz utworzyć komunikat `PortfolioList` lub coś podobnego i używać go w wielu metodach usługi, ale należy go odpornować na Temptation. Nie jest możliwe, aby wiedzieć, w jaki sposób różne metody w usłudze zostaną rozłączone, dlatego należy zapewnić ich obsługę i czyszczenie ich komunikatów.

```protobuf
message GetAllRequest {
    string trader_id = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

Jeśli zapiszesz projekt z tymi zmianami, obiekt docelowy kompilacji gRPC zostanie uruchomiony w tle i wygeneruje wszystkie typy komunikatów protobuf i klasę bazową, którą można odziedziczyć w celu zaimplementowania usługi.

Otwórz klasę `Services/GreeterService.cs` i Usuń przykładowy kod. Teraz możesz dodać implementację usługi portfolio. Wygenerowana Klasa bazowa będzie znajdować się w przestrzeni nazw `Protos` i jest generowana jako Klasa zagnieżdżona. gRPC tworzy klasę statyczną o tej samej nazwie co usługa w pliku `.proto` i klasie bazowej z sufiksem `Base` wewnątrz tej klasy statycznej, więc pełny identyfikator dla typu podstawowego to `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

Klasa bazowa deklaruje `virtual` metody `Get` i `GetAll`, które mogą zostać zastąpione w celu zaimplementowania usługi. Metody są `virtual`, a nie `abstract`, dzięki czemu usługa może zwrócić jawny kod stanu `Unimplemented` gRPC, podobnie jak w przypadku, gdy użytkownik może zgłosić `NotImplementedException` w zwykłym C# kodzie.

Sygnatura wszystkich jednoargumentowych metod usługi gRPC w ASP.NET Core jest spójna. Istnieją dwa parametry: pierwszy jest typem komunikatu zadeklarowanym w pliku `.proto`, a drugi to `ServerCallContext`, który działa podobnie do `HttpContext` z ASP.NET Core. W rzeczywistości istnieje metoda rozszerzająca o nazwie `GetHttpContext` w klasie `ServerCallContext`, której można użyć do uzyskania bazowego `HttpContext`, ale nie trzeba jej często używać. Przyjrzyjmy się `ServerCallContext` dalszej części tego rozdziału, a także w rozdziale zawierającym Opis uwierzytelniania.

Zwracany typ metody to `Task<T>`, gdzie `T` jest typem komunikatu odpowiedzi. Wszystkie metody usługi gRPC są asynchroniczne.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Migrowanie biblioteki PortfolioData do platformy .NET Core

W tym momencie projekt wymaga repozytorium portfolio i modeli zawartych w bibliotece klas `TraderSys.PortfolioData` w rozwiązaniu WCF. Najprostszym sposobem na ich przełączenie jest utworzenie nowej biblioteki klas przy użyciu okna dialogowego **Nowy projekt** programu Visual Studio z szablonem Biblioteka klas (.NET standard) lub z wiersza polecenia przy użyciu interfejs wiersza polecenia platformy .NET Core, uruchomienie tych poleceń z katalogu zawierającego plik `TraderSys.sln`:

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Po utworzeniu biblioteki i dodaniu jej do rozwiązania Usuń wygenerowany plik `Class1.cs` i skopiuj pliki z biblioteki rozwiązania WCF do folderu nowej biblioteki klas, utrzymując strukturę folderu:

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

Projekty platformy .NET w stylu zestawu SDK automatycznie zawierają wszystkie `.cs` pliki w lub w ich własnym katalogu, dlatego nie trzeba jawnie dodawać ich do projektu. Jedyna pozostała czynność polega na usunięciu `DataContract` i `DataMember` atrybutów z klas `Portfolio` i `PortfolioItem`, aby były to C# zwykłe stare klasy:

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>Użyj iniekcji zależności ASP.NET Core

Teraz można dodać odwołanie do tej biblioteki do projektu aplikacji gRPC i użyć klasy `PortfolioRepository` przy użyciu iniekcji zależności w implementacji usługi gRPC. W aplikacji WCF funkcja wstrzykiwania zależności została dostarczona przez kontener Autofac IoC. ASP.NET Core ma iniekcję zależności rozszerzania w. Repozytorium można zarejestrować w metodzie `ConfigureServices` w klasie `Startup`:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

Implementację `IPortfolioRepository` można teraz określić jako parametr konstruktora w klasie `PortfolioService` w następujący sposób:

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>Implementowanie usługi gRPC

Po zadeklarowaniu komunikatów i usługi w pliku `portfolios.proto` musisz zaimplementować metody usługi w klasie `PortfolioService`, która dziedziczy z klasy `Portfolios.PortfoliosBase` generowanej przez gRPC. Metody są zadeklarowane jako `virtual` w klasie bazowej. Jeśli ich nie zastąpisz, domyślnie zwróci kod stanu gRPC "nie zaimplementowana".

Zacznij od wprowadzenia metody `Get`. Domyślne przesłonięcie wygląda następująco:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

Pierwszy problem polega na tym, że `request.TraderId` jest ciągiem, a usługa wymaga `Guid`. Mimo że oczekiwany format ciągu jest `UUID`, kod musi zajmować się możliwością, że obiekt wywołujący wysłał nieprawidłową wartość i odpowiada odpowiednio. Usługa może odpowiedzieć z błędami przez wyrzucanie `RpcException` i użycie standardowego kodu stanu `InvalidArgument` do wyznaczania problemu:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

Po poprawnym `Guid` wartości dla `traderId`, można użyć repozytorium, aby pobrać portfolio i zwrócić go do klienta:

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Mapowanie wewnętrznych modeli na komunikaty gRPC

Poprzedni kod nie działa, ponieważ repozytorium zwraca własny model POCO `Portfolio`, ale gRPC potrzebuje własnego `Portfolio`komunikatów protobuf. Podobnie jak podczas mapowania typów Entity Framework na typy transferu danych najlepszym rozwiązaniem jest zapewnienie konwersji między nimi. Dobrym miejscem do umieszczenia kodu dla tej konwersji jest Klasa wygenerowana protobuf, która jest zadeklarowana jako Klasa `partial`, więc można ją rozszerzyć:

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> Można użyć biblioteki, takiej jak [automapowania](https://automapper.org/) , do obsługi tej konwersji z klas wewnętrznych modelu do typów protobuf, o ile można skonfigurować konwersje typu niższego poziomu, takie jak `string`/`Guid` lub `decimal`/`double` i mapowanie listy.

Teraz, gdy masz kod konwersji na miejscu, możesz wykonać implementację metody `Get`:

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

Implementacja metody `GetAll` jest podobna. Należy zauważyć, że pola `repeated` w komunikatach protobuf są generowane jako właściwości `readonly` typu `RepeatedField<T>`, dlatego należy dodać do nich elementy przy użyciu metody `AddRange`, jak w poniższym przykładzie:

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

Pomyślnie przeprowadzono migrację usługi żądania WCF-odpowiedź do gRPC, przyjrzyjmy się tworzeniu klienta dla niego z pliku `.proto`.

## <a name="generate-client-code"></a>Generuj kod klienta

Utwórz bibliotekę klas .NET Standard w tym samym rozwiązaniu, aby zawierała klienta. Jest to przede wszystkim przykład tworzenia kodu klienta, ale można go spakować przy użyciu NuGet i rozpowszechniać w ramach wewnętrznego repozytorium dla innych zespołów .NET do użycia. Przejdź dalej i Dodaj nową bibliotekę klas .NET Standard o nazwie `TraderSys.Portfolios.Client` do rozwiązania i Usuń plik `Class1.cs`.

> [!CAUTION]
> Pakiet NuGet [GRPC .NET. Client](https://www.nuget.org/packages/Grpc.Net.Client) wymaga platformy .net Core 3,0 (lub innego środowiska uruchomieniowego zgodnego z .NET Standard 2,1). Starsze wersje .NET Framework i .NET Core są obsługiwane przez pakiet NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .

W programie Visual Studio 2019 można dodać odwołania do usług gRPC w sposób podobny do sposobu dodawania odwołań do usług do projektów WCF we wcześniejszych wersjach programu Visual Studio. Odwołania do usług i połączone usługi są teraz zarządzane w tym samym interfejsie użytkownika. Aby uzyskać dostęp do interfejsu użytkownika, kliknij prawym przyciskiem myszy węzeł **zależności** w projekcie `TraderSys.Portfolios.Client` w Eksplorator rozwiązań i wybierz polecenie **Dodaj podłączoną usługę**. W wyświetlonym oknie narzędzi wybierz sekcję odwołania do **usługi** , a następnie wybierz pozycję **Dodaj nowe odwołanie do usługi gRPC**:

![Interfejs użytkownika usług połączonych w programie Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Przejdź do pliku `portfolios.proto` w projekcie `TraderSys.Portfolios`, pozostaw **Klient** w obszarze **Wybierz typ klasy do wygenerowania**, a następnie wybierz przycisk **OK**:

![Okno dialogowe Dodawanie nowego odwołania do usługi gRPC w programie Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Zwróć uwagę, że to okno dialogowe zawiera również pole adresu URL. Jeśli Twoja organizacja utrzymuje katalog `.proto` plików dostępny dla sieci Web, można utworzyć klientów bezpośrednio przez ustawienie tego adresu URL.

W przypadku korzystania z funkcji **Dodaj usługę połączoną** programu Visual Studio plik `portfolios.proto` jest dodawany do projektu biblioteki klas jako *plik połączony* , a nie skopiowane, więc zmiany w pliku w projekcie usługi zostaną automatycznie zastosowane w projekcie klienta. Element `<Protobuf>` w pliku `csproj` wygląda następująco:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> Jeśli nie używasz programu Visual Studio lub wolisz pracować z wiersza polecenia, możesz użyć narzędzia globalnego `dotnet-grpc` do zarządzania odwołaniami protobuf w projekcie .NET gRPC. Aby uzyskać więcej informacji, zobacz [dokumentację`dotnet-grpc`](/aspnet/core/grpc/dotnet-grpc).

### <a name="use-the-portfolios-service-from-a-client-application"></a>Korzystanie z usługi portfolio w aplikacji klienckiej

Poniższy kod stanowi krótki przykład korzystania z wygenerowanego klienta w aplikacji konsolowej. Bardziej szczegółowa Eksploracja kodu klienta gRPC znajduje się na końcu tego rozdziału.

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

Przeprowadzono migrację podstawowej aplikacji WCF do ASP.NET Core usługi gRPC i utworzono klienta w celu korzystania z usługi z poziomu aplikacji .NET. Następna sekcja będzie obejmować więcej procesów usług dupleksowych.

>[!div class="step-by-step"]
>[Poprzednie](create-project.md)
>[dalej](migrate-duplex-services.md)
