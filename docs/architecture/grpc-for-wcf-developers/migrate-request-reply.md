---
title: Migrowanie usługi żądania WCF-odpowiedź do gRPC-gRPC dla deweloperów WCF
description: Dowiedz się, jak migrować prostą usługę żądanie-odpowiedź z programu WCF do gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184310"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Migrowanie usługi żądania WCF-odpowiedź do gRPC jednoargumentowego wywołania procedury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

W tej sekcji opisano sposób migrowania podstawowej usługi żądania-odpowiedzi w programie WCF do jednoargumentowej usługi RPC w ASP.NET Core gRPC. Te usługi są najprostszymi typami usług w obu Windows Communication Foundation (WCF) i gRPC, więc jest to doskonałe miejsce do uruchomienia. Po przeprowadzeniu migracji usługi dowiesz się, jak wygenerować bibliotekę kliencką z tego `.proto` samego pliku, aby korzystać z usługi z aplikacji klienckiej platformy .NET.

## <a name="the-wcf-solution"></a>Rozwiązanie WCF

[Rozwiązanie PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) obejmuje prostą usługę portfolio żądanie-odpowiedź do pobrania pojedynczego portfolio lub wszystkich portfolio dla danego podmiotu gospodarczego. Usługa jest zdefiniowana w interfejsie `IPortfolioService` `ServiceContract` z atrybutem:

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

Model to prosta C# Klasa oznaczona przy użyciu [schematu DataContract](xref:System.Runtime.Serialization.DataContractAttribute), w tym lista `PortfolioItem` obiektów. `Portfolio` Modele te są zdefiniowane w `TraderSys.PortfolioData` projekcie wraz z klasą repozytorium reprezentującą abstrakcję dostępu do danych.

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

Implementacja używa klasy repozytorium dostarczonej za pośrednictwem iniekcji zależności, która zwraca `DataContract` wystąpienia typów. `ServiceContract`

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

Jeśli wykonano instrukcje podane w poprzedniej sekcji, powinien istnieć projekt gRPC z `portfolios.proto` plikiem, który wygląda następująco.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

Pierwszym krokiem jest Migrowanie `DataContract` klas do ich odpowiedników protobuf.

## <a name="convert-the-datacontracts-to-grpc-messages"></a>Konwertuj kontrakty DataContracts na komunikaty gRPC

Klasa zostanie najpierw przekonwertowana na komunikat protobuf, `Portfolio` ponieważ zależy od niej Klasa. `PortfolioItem` Klasa jest bardzo prosta i trzy właściwości są mapowane bezpośrednio do typów danych gRPC. Właściwość reprezentująca cenę płatną za udział w zakupie, `decimal` jest polem `double` i gRPC obsługuje `float` tylko wartości liczbowe, które nie są odpowiednie dla waluty. `Cost` Ze względu na to, że ceny udziałów są różne dla co najmniej jednego centa, `int32` koszt może być wyrażony jako procent.

> [!NOTE]
> Pamiętaj o używaniu `camelCase` nazw pól `.proto` w pliku; Generator C# kodu przekonwertuje je na `PascalCase` użytkownika, a użytkownicy innych języków poinformują Cię o poszanowaniu różnych standardów kodowania.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

`Portfolio` Klasa jest nieco bardziej skomplikowana. W kodzie WCF deweloper użył `Guid` `TraderId` dla `List<PortfolioItem>`właściwości i zawiera. W protobuf, który nie ma typu pierwszej klasy `UUID` , należy `string` użyć dla `traderId` pola i przeanalizować go w własnym kodzie. Aby uzyskać listę elementów, użyj `repeated` słowa kluczowego w polu.

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

Teraz mamy Twoje komunikaty dotyczące danych, możemy zadeklarować punkty końcowe usługi RPC.

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>Konwertuj kontrakt ServiceContract na usługę gRPC

Metoda WCF `Get` przyjmuje dwa parametry: `Guid traderId` i `int portfolioId`. metody usługi gRPC mogą przyjmować tylko jeden parametr, dlatego należy utworzyć komunikat, aby przechowywać dwie wartości. Typowym sposobem jest nazywanie tych obiektów żądania o takiej samej nazwie jak metoda i sufiks `Request`. Ponownie jest używany `traderId` dla pola zamiast `Guid`. `string`

Usługa może po prostu zwrócić `Portfolio` komunikat bezpośrednio, ale może to mieć wpływ na zgodność z poprzednimi wersjami w przyszłości. Dobrym sposobem `Request` jest zdefiniowanie oddzielnych i `Response` komunikatów dla każdej metody w usłudze, nawet jeśli wiele z nich jest `GetResponse` teraz tego samego typu, więc Zadeklaruj komunikat przy użyciu pojedynczego `Portfolio` pola.

Poniższy przykład przedstawia deklarację metody usługi gRPC przy użyciu `GetRequest` komunikatu:

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

Metoda WCF `GetAll` przyjmuje tylko jeden parametr, `traderId`dlatego może wydawać się, że jeden z nich może być `string` określony jako typ parametru, ale gRPC wymaga zdefiniowanego typu komunikatu. To wymaganie umożliwia wymuszenie użycia niestandardowych komunikatów dla wszystkich danych wejściowych i wyjściowych w celu zachowania zgodności z poprzednimi wersjami.

Metoda WCF zwróciła również element `List<Portfolio>`, ale z tego samego powodu nie zezwala na proste typy parametrów, gRPC nie będzie `repeated Portfolio` zezwalać jako zwracany typ. Zamiast tego Utwórz `GetAllResponse` typ, aby otoczyć listę.

> [!WARNING]
> Użytkownik może być skłonny do tworzenia `PortfolioList` komunikatów lub podobnych i używania ich w wielu metodach usług, ale należy go odpornać na Temptation. Nie jest możliwe, aby wiedzieć, w jaki sposób różne metody w usłudze mogą się rozwijać w przyszłości, dlatego należy zapewnić, że ich wiadomości są charakterystyczne i czyste oddzielone.

```protobuf
message GetAllRequest {
    string traderId = 1;
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

`Services/GreeterService.cs` Otwórz klasę i Usuń przykładowy kod. Teraz możesz dodać implementację usługi portfolio. Wygenerowana Klasa bazowa będzie w `Protos` przestrzeni nazw i jest generowana jako Klasa zagnieżdżona. gRPC tworzy klasę statyczną o tej samej nazwie co usługa w `.proto` pliku, a następnie klasę bazową z sufiksem `Base` wewnątrz tej klasy statycznej, więc pełny identyfikator dla typu podstawowego to `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

Klasa bazowa deklaruje `virtual` metody dla `Get` i `GetAll` , które mogą zostać zastąpione w celu zaimplementowania usługi. `virtual` Metody są `Unimplemented` `NotImplementedException` C# zamiast tego, jeśli nie zostaną zaimplementowane, usługa może zwrócić jawny kod stanu gRPC, podobnie jak w przypadku zwykłego kodu. `abstract`

Sygnatura wszystkich jednoargumentowych metod usługi gRPC w ASP.NET Core jest spójna. Istnieją dwa parametry: pierwszy to typ komunikatu zadeklarowany w `.proto` pliku, a drugi `ServerCallContext` to `HttpContext` , który działa podobnie do ASP.NET Core od. W rzeczywistości istnieje metoda rozszerzająca wywołana `GetHttpContext` `ServerCallContext` na klasie, która może być używana do uzyskiwania bazowego `HttpContext`elementu, chociaż nie trzeba go często używać. Zapoznajemy się w dalszej części tego rozdziału, a także w rozdziale zawierającym Opis uwierzytelniania. `ServerCallContext`

Zwracany typ metody to `Task<T>` gdzie `T` jest typem komunikatu odpowiedzi. Wszystkie metody usługi gRPC są asynchroniczne.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Migrowanie biblioteki PortfolioData do platformy .NET Core

W tym momencie projekt wymaga repozytorium portfolio i modeli zawartych w `TraderSys.PortfolioData` bibliotece klas w rozwiązaniu WCF. Najprostszym sposobem na ich przełączenie jest utworzenie nowej biblioteki klas przy użyciu okna dialogowego **Nowy projekt** programu Visual Studio z szablonem *biblioteka klas (.NET standard)* lub z wiersza polecenia przy użyciu interfejs wiersza polecenia platformy .NET Core, uruchamiając następujące polecenia z katalogu zawierającego `TraderSys.sln` plik.

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Gdy biblioteka została utworzona i dodana do rozwiązania, Usuń wygenerowany `Class1.cs` plik i skopiuj pliki z biblioteki rozwiązania WCF do folderu nowej biblioteki klas, utrzymując strukturę folderów.

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

Nowoczesne pliki projektu .NET są automatycznie dołączane do wszystkich `.cs` plików w folderze lub w ich własnym katalogu, dlatego nie trzeba jawnie dodawać ich do projektu. Jedyne pozostała czynność polega na `DataContract` usunięciu atrybutów i `Portfolio` `DataMember` z `PortfolioItem` klas i, tak aby były C# one zwykłymi klasami.

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

Teraz można dodać odwołanie do tej biblioteki do projektu aplikacji gRPC i użyć `PortfolioRepository` klasy przy użyciu iniekcji zależności w implementacji usługi gRPC. W aplikacji WCF funkcja wstrzykiwania zależności została dostarczona przez kontener Autofac IoC. ASP.NET Core ma rozszerzania iniekcji zależności w; repozytorium można zarejestrować w `ConfigureServices` metodzie `Startup` w klasie.

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

Implementację można teraz określić jako parametr konstruktora `PortfolioService` w klasie w następujący sposób: `IPortfolioRepository`

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

Po zadeklarowaniu komunikatów i usługi w `portfolios.proto` pliku należy zaimplementować metody usługi `PortfolioService` w klasie, która dziedziczy z klasy generowanej `Portfolios.PortfoliosBase` przez gRPC. Metody są zadeklarowane jako `virtual` w klasie bazowej. Jeśli ich nie zastąpisz, domyślnie zwróci kod stanu gRPC "nie zaimplementowana".

Zacznij od wprowadzenia `Get` metody. Domyślne przesłonięcie wygląda tak, jak w poniższym przykładzie:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

Pierwszy problem to `request.TraderId` ciąg, a usługa `Guid`wymaga. Mimo że oczekiwany format ciągu to a `UUID`, kod musi zajmować się możliwością, że obiekt wywołujący wysłał nieprawidłową wartość i odpowiada odpowiednio. Usługa może odpowiedzieć z błędami przez wyrzucanie `RpcException`i użycie standardowego `InvalidArgument` kodu stanu do wyznaczania problemu.

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

Gdy istnieje odpowiednia `Guid` `traderId`wartość, można użyć repozytorium do pobrania portfolio i zwrócić go do klienta programu.

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Mapowanie wewnętrznych modeli na komunikaty gRPC

Poprzedni kod nie działa, ponieważ repozytorium zwraca własny model `Portfolio`poco, ale gRPC wymaga własnego komunikatu `Portfolio`protobuf. Podobnie jak mapowanie typów Entity Framework do typów transferu danych, najlepszym rozwiązaniem jest zapewnienie konwersji między nimi. Dobrym miejscem, aby umieścić kod dla tego elementu, znajduje się w klasie generowanej przez protobuf, która jest zadeklarowana jako `partial` Klasa, aby można ją było rozszerzyć.

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
> Możesz użyć biblioteki, takiej jak [automapowania](https://automapper.org/) , aby obsługiwać tę konwersję z wewnętrznych klas modelu do typów protobuf, o ile można skonfigurować konwersje typu niższego poziomu, `string` takie `decimal` / `Guid` jak lub /imapowanielisty. `double`

W przypadku kodu konwersji w miejscu `Get` można wykonać implementację metody.

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

Implementacja `GetAll` metody jest podobna. Należy zauważyć, `repeated` że pola w komunikatach protobuf są `readonly` generowane jako właściwości `RepeatedField<T>`typu, dlatego należy dodać do nich elementy przy użyciu `AddRange` metody, jak w poniższym przykładzie:

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

Pomyślnie przeprowadzono migrację usługi żądania WCF-odpowiedź do gRPC, przyjrzyjmy się tworzeniu klienta dla tego `.proto` pliku.

## <a name="generate-client-code"></a>Generuj kod klienta

Utwórz bibliotekę klas .NET Standard w tym samym rozwiązaniu, aby zawierała klienta. Jest to przede wszystkim przykład tworzenia kodu klienta, ale można go spakować przy użyciu NuGet i rozpowszechniać w ramach wewnętrznego repozytorium dla innych zespołów .NET do użycia. Przejdź dalej i Dodaj nową bibliotekę klas .NET Standard wywołana `TraderSys.Portfolios.Client` do rozwiązania i `Class1.cs` Usuń plik.

> [!CAUTION]
> Pakiet NuGet [GRPC .NET. Client](https://www.nuget.org/packages/Grpc.Net.Client) wymaga platformy .net Core 3,0 (lub innego środowiska uruchomieniowego zgodnego z .NET Standard 2,1). Starsze wersje .NET Framework i .NET Core są obsługiwane przez pakiet NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .

W programie Visual Studio 2019 można dodać odwołania do usług gRPC, podobnie jak w przypadku dodawania odwołań do usług do projektów WCF we wcześniejszych wersjach programu Visual Studio. Odwołania do usług i połączone usługi są zarządzane w ramach tego samego interfejsu użytkownika teraz, do którego można uzyskać dostęp, klikając prawym przyciskiem myszy `TraderSys.Portfolios.Client` węzeł zależności w projekcie w Eksplorator rozwiązań i wybierając pozycję **Dodaj usługę połączoną**. W wyświetlonym oknie narzędzi wybierz sekcję odwołania do **usługi** , a następnie kliknij pozycję **Dodaj nowe odwołanie do usługi gRPC**.

![Interfejs użytkownika usług połączonych w programie Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Przejdź do `portfolios.proto` pliku `TraderSys.Portfolios` w projekcie, pozostaw **Typ klasy do wygenerowania** jako **Klient**, a następnie kliknij przycisk **OK**.

![Okno dialogowe Dodawanie nowego odwołania do usługi gRPC w programie Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Należy zauważyć, że to okno dialogowe zawiera również pole adresu URL. Jeśli Twoja organizacja utrzymuje katalog `.proto` plików dostępny dla sieci Web, możesz utworzyć klientów bezpośrednio, ustawiając ten adres URL.

W przypadku korzystania z `portfolios.proto` funkcji **Dodaj podłączoną usługę** programu Visual Studio plik jest dodawany do projektu biblioteki klas jako *połączony plik*, a nie skopiowane, więc zmiany w pliku w projekcie usługi zostaną automatycznie zastosowane w projekt klienta. `<Protobuf>` Element`csproj` w pliku wygląda następująco:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

### <a name="use-the-portfolios-service-from-a-client-application"></a>Korzystanie z usługi portfolio w aplikacji klienckiej

Poniższy kod stanowi krótki przykład użycia wygenerowanego klienta w aplikacji konsolowej. Bardziej szczegółowa Eksploracja kodu klienta gRPC znajduje się na końcu tego rozdziału.

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

Teraz przeprowadzono migrację podstawowej aplikacji WCF do ASP.NET Core usługi gRPC i utworzono klienta w celu korzystania z usługi z poziomu aplikacji .NET. Następna sekcja będzie obejmować więcej "dupleks" usług.

>[!div class="step-by-step"]
>[Poprzedni](create-project.md)
>[Następny](migrate-duplex-services.md)
