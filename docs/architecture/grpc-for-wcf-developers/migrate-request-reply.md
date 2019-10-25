---
title: Migrowanie usługi żądania WCF-odpowiedź do gRPC-gRPC dla deweloperów WCF
description: Dowiedz się, jak migrować prostą usługę żądanie-odpowiedź z programu WCF do gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 12e042e8e7e3683cc4da1fedce2482e7199b04a7
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846611"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="08daf-103">Migrowanie usługi żądania WCF-odpowiedź do gRPC jednoargumentowego wywołania procedury</span><span class="sxs-lookup"><span data-stu-id="08daf-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="08daf-104">W tej sekcji opisano sposób migrowania podstawowej usługi żądania-odpowiedzi w programie WCF do jednoargumentowej usługi RPC w ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="08daf-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="08daf-105">Te usługi są najprostszymi typami usług w obu Windows Communication Foundation (WCF) i gRPC, więc jest to doskonałe miejsce do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="08daf-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="08daf-106">Po przeprowadzeniu migracji usługi dowiesz się, jak wygenerować bibliotekę kliencką z tego samego pliku `.proto`, aby korzystać z usługi z aplikacji klienckiej platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="08daf-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="08daf-107">Rozwiązanie WCF</span><span class="sxs-lookup"><span data-stu-id="08daf-107">The WCF solution</span></span>

<span data-ttu-id="08daf-108">[Rozwiązanie PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) obejmuje prostą usługę portfolio żądanie-odpowiedź do pobrania pojedynczego portfolio lub wszystkich portfolio dla danego podmiotu gospodarczego.</span><span class="sxs-lookup"><span data-stu-id="08daf-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple Request-Reply Portfolio service to download a single portfolio, or all portfolios for a given Trader.</span></span> <span data-ttu-id="08daf-109">Usługa jest definiowana w interfejsie `IPortfolioService` z atrybutem `ServiceContract`:</span><span class="sxs-lookup"><span data-stu-id="08daf-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="08daf-110">Model `Portfolio` to prosta C# Klasa oznaczona przy użyciu [schematu DataContract](xref:System.Runtime.Serialization.DataContractAttribute), w tym lista obiektów `PortfolioItem`.</span><span class="sxs-lookup"><span data-stu-id="08daf-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="08daf-111">Modele te są zdefiniowane w projekcie `TraderSys.PortfolioData` wraz z klasą repozytorium reprezentującą abstrakcję dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="08daf-111">These models are defined in the `TraderSys.PortfolioData` project, along with a repository class representing a data access abstraction.</span></span>

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

<span data-ttu-id="08daf-112">Implementacja `ServiceContract` używa klasy repozytorium dostarczonej przez iniekcję zależności, która zwraca wystąpienia typów `DataContract`.</span><span class="sxs-lookup"><span data-stu-id="08daf-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types.</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="08daf-113">Plik portfolio. proto</span><span class="sxs-lookup"><span data-stu-id="08daf-113">The portfolios.proto file</span></span>

<span data-ttu-id="08daf-114">Jeśli wykonano instrukcje w poprzedniej sekcji, powinien istnieć projekt gRPC z plikiem `portfolios.proto`, który wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="08daf-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="08daf-115">Pierwszym krokiem jest Migrowanie klas `DataContract` do ich odpowiedników protobuf.</span><span class="sxs-lookup"><span data-stu-id="08daf-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontracts-to-grpc-messages"></a><span data-ttu-id="08daf-116">Konwertuj kontrakty DataContracts na komunikaty gRPC</span><span class="sxs-lookup"><span data-stu-id="08daf-116">Convert the DataContracts to gRPC messages</span></span>

<span data-ttu-id="08daf-117">Klasa `PortfolioItem` zostanie najpierw przekonwertowana na komunikat protobuf, ponieważ zależy od niej Klasa `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="08daf-117">The `PortfolioItem` class will be converted to a Protobuf message first, as the `Portfolio` class depends on it.</span></span> <span data-ttu-id="08daf-118">Klasa jest bardzo prosta i trzy właściwości są mapowane bezpośrednio do typów danych gRPC.</span><span class="sxs-lookup"><span data-stu-id="08daf-118">The class is very simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="08daf-119">Właściwość `Cost`, reprezentująca cenę płatną za udział w zakupie, jest polem `decimal`, a gRPC obsługuje tylko `float` lub `double` dla liczb rzeczywistych, które nie są odpowiednie dla waluty.</span><span class="sxs-lookup"><span data-stu-id="08daf-119">The `Cost` property, representing the price paid for the shares at purchase, is a `decimal` field, and gRPC only supports `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="08daf-120">Ze względu na to, że ceny udziałów są różne dla co najmniej jednego centa, koszt może być wyrażony jako `int32` centów.</span><span class="sxs-lookup"><span data-stu-id="08daf-120">Since share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="08daf-121">Pamiętaj, aby użyć `camelCase` nazw pól w pliku `.proto`; Generator C# kodu przekonwertuje je na `PascalCase` dla Ciebie, a użytkownicy innych języków poinformują Cię o poszanowaniu różnych standardów kodowania.</span><span class="sxs-lookup"><span data-stu-id="08daf-121">Remember to use `camelCase` for field names in your `.proto` file; the C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="08daf-122">Klasa `Portfolio` jest nieco bardziej skomplikowana.</span><span class="sxs-lookup"><span data-stu-id="08daf-122">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="08daf-123">W kodzie WCF deweloper użył `Guid` dla właściwości `TraderId` i zawiera `List<PortfolioItem>`.</span><span class="sxs-lookup"><span data-stu-id="08daf-123">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="08daf-124">W protobuf, który nie ma typu `UUID` pierwszej klasy, należy użyć `string` dla pola `traderId` i przeanalizować go w własnym kodzie.</span><span class="sxs-lookup"><span data-stu-id="08daf-124">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="08daf-125">Dla listy elementów należy użyć słowa kluczowego `repeated` w polu.</span><span class="sxs-lookup"><span data-stu-id="08daf-125">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="08daf-126">Teraz mamy Twoje komunikaty dotyczące danych, możemy zadeklarować punkty końcowe usługi RPC.</span><span class="sxs-lookup"><span data-stu-id="08daf-126">Now we have our data messages, we can declare the service RPC endpoints.</span></span>

## <a name="convert-the-servicecontract-to-a-grpc-service"></a><span data-ttu-id="08daf-127">Konwertuj kontrakt ServiceContract na usługę gRPC</span><span class="sxs-lookup"><span data-stu-id="08daf-127">Convert the ServiceContract to a gRPC service</span></span>

<span data-ttu-id="08daf-128">Metoda `Get` WCF przyjmuje dwa parametry: `Guid traderId` i `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="08daf-128">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="08daf-129">metody usługi gRPC mogą przyjmować tylko jeden parametr, dlatego należy utworzyć komunikat, aby przechowywać dwie wartości.</span><span class="sxs-lookup"><span data-stu-id="08daf-129">gRPC service methods can only take a single parameter, so a message must be created to hold the two values.</span></span> <span data-ttu-id="08daf-130">Typowym sposobem jest nazywanie tych obiektów żądania o takiej samej nazwie jak metoda i sufiks `Request`.</span><span class="sxs-lookup"><span data-stu-id="08daf-130">It's common practice to name these request objects with the same name as the method and the suffix `Request`.</span></span> <span data-ttu-id="08daf-131">Ponownie `string` jest używany dla pola `traderId` zamiast `Guid`.</span><span class="sxs-lookup"><span data-stu-id="08daf-131">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="08daf-132">Usługa może po prostu zwrócić komunikat `Portfolio` bezpośrednio, ale może to mieć wpływ na zgodność z poprzednimi wersjami w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="08daf-132">The service could just return a `Portfolio` message directly, but again, this could impact backward compatibility in the future.</span></span> <span data-ttu-id="08daf-133">Dobrym sposobem jest zdefiniowanie oddzielnych `Request` i `Response` komunikatów dla każdej metody w usłudze, nawet jeśli wiele z nich jest teraz tego samego, więc Zadeklaruj komunikat `GetResponse` z pojedynczym polem `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="08daf-133">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now, so declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="08daf-134">Poniższy przykład przedstawia deklarację metody usługi gRPC przy użyciu komunikatu `GetRequest`:</span><span class="sxs-lookup"><span data-stu-id="08daf-134">The following example shows the declaration of the gRPC service method using the `GetRequest` message:</span></span>

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

<span data-ttu-id="08daf-135">Metoda `GetAll` WCF przyjmuje tylko jeden parametr, `traderId`, dlatego może wydawać się, że jeden może określić `string` jako typ parametru, ale gRPC wymaga zdefiniowanego typu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="08daf-135">The WCF `GetAll` method only takes a single parameter, `traderId`, so it might seem that one could specify `string` as the parameter type, but gRPC requires a defined message type.</span></span> <span data-ttu-id="08daf-136">To wymaganie umożliwia wymuszenie użycia niestandardowych komunikatów dla wszystkich danych wejściowych i wyjściowych w celu zachowania zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="08daf-136">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="08daf-137">Metoda WCF zwróciła również `List<Portfolio>`, ale z tego samego powodu nie zezwala na proste typy parametrów, gRPC nie zezwoli `repeated Portfolio` jako zwracany typ.</span><span class="sxs-lookup"><span data-stu-id="08daf-137">The WCF method also returned a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="08daf-138">Zamiast tego Utwórz `GetAllResponse` typ, aby otoczyć listę.</span><span class="sxs-lookup"><span data-stu-id="08daf-138">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="08daf-139">Użytkownik może być skłonny do tworzenia komunikatów `PortfolioList` lub podobnych i używania ich w wielu metodach usług, ale należy go odpornować na Temptation.</span><span class="sxs-lookup"><span data-stu-id="08daf-139">You may be tempted to create a `PortfolioList` message or similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="08daf-140">Nie jest możliwe, aby wiedzieć, w jaki sposób różne metody w usłudze mogą się rozwijać w przyszłości, dlatego należy zapewnić, że ich wiadomości są charakterystyczne i czyste oddzielone.</span><span class="sxs-lookup"><span data-stu-id="08daf-140">It's impossible to know how the various methods on a service may evolve in the future, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="08daf-141">Jeśli zapiszesz projekt z tymi zmianami, obiekt docelowy kompilacji gRPC zostanie uruchomiony w tle i wygeneruje wszystkie typy komunikatów protobuf i klasę bazową, którą można odziedziczyć w celu zaimplementowania usługi.</span><span class="sxs-lookup"><span data-stu-id="08daf-141">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class you can inherit to implement the service.</span></span>

<span data-ttu-id="08daf-142">Otwórz klasę `Services/GreeterService.cs` i Usuń przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="08daf-142">Open up the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="08daf-143">Teraz możesz dodać implementację usługi portfolio.</span><span class="sxs-lookup"><span data-stu-id="08daf-143">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="08daf-144">Wygenerowana Klasa bazowa będzie znajdować się w przestrzeni nazw `Protos` i jest generowana jako Klasa zagnieżdżona.</span><span class="sxs-lookup"><span data-stu-id="08daf-144">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="08daf-145">gRPC tworzy klasę statyczną o tej samej nazwie co usługa w pliku `.proto`, a następnie klasę bazową z sufiksem `Base` wewnątrz tej klasy statycznej, więc pełny identyfikator dla typu podstawowego to `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="08daf-145">gRPC creates a static class with the same name as the service in the `.proto` file, and then a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="08daf-146">Klasa bazowa deklaruje `virtual` metody `Get` i `GetAll`, które mogą zostać zastąpione w celu zaimplementowania usługi.</span><span class="sxs-lookup"><span data-stu-id="08daf-146">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="08daf-147">Metody są `virtual`, a nie `abstract`, dzięki czemu usługa może zwrócić jawny kod stanu `Unimplemented` gRPC, podobnie jak w przypadku, gdy użytkownik może zgłosić `NotImplementedException` w zwykłym C# kodzie.</span><span class="sxs-lookup"><span data-stu-id="08daf-147">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="08daf-148">Sygnatura wszystkich jednoargumentowych metod usługi gRPC w ASP.NET Core jest spójna.</span><span class="sxs-lookup"><span data-stu-id="08daf-148">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="08daf-149">Istnieją dwa parametry: pierwszy jest typem komunikatu zadeklarowanym w pliku `.proto`, a drugi to `ServerCallContext`, który działa podobnie do `HttpContext` z ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="08daf-149">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="08daf-150">W rzeczywistości istnieje metoda rozszerzająca o nazwie `GetHttpContext` w klasie `ServerCallContext`, której można użyć do uzyskania bazowego `HttpContext`, ale nie trzeba jej często używać.</span><span class="sxs-lookup"><span data-stu-id="08daf-150">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="08daf-151">Przyjrzyjmy się `ServerCallContext` dalszej części tego rozdziału, a także w rozdziale zawierającym Opis uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="08daf-151">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="08daf-152">Zwracany typ metody to `Task<T>`, gdzie `T` jest typem komunikatu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="08daf-152">The method's return type is a `Task<T>` where `T` is the response message type.</span></span> <span data-ttu-id="08daf-153">Wszystkie metody usługi gRPC są asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="08daf-153">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="08daf-154">Migrowanie biblioteki PortfolioData do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="08daf-154">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="08daf-155">W tym momencie projekt wymaga repozytorium portfolio i modeli zawartych w bibliotece klas `TraderSys.PortfolioData` w rozwiązaniu WCF.</span><span class="sxs-lookup"><span data-stu-id="08daf-155">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="08daf-156">Najprostszym sposobem na ich przełączenie jest utworzenie nowej biblioteki klas przy użyciu okna dialogowego **Nowy projekt** programu Visual Studio z szablonem *biblioteka klas (.NET standard)* lub z wiersza polecenia przy użyciu interfejs wiersza polecenia platformy .NET Core, uruchamiając następujące polecenia z katalogu zawierającego plik `TraderSys.sln`.</span><span class="sxs-lookup"><span data-stu-id="08daf-156">The easiest way to bring them across is to create a new class library using either the Visual Studio **New project** dialog with the *Class Library (.NET Standard)* template, or from the command line using the .NET Core CLI, running the following commands from the directory containing the `TraderSys.sln` file.</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="08daf-157">Gdy biblioteka została utworzona i dodana do rozwiązania, Usuń wygenerowany plik `Class1.cs` i skopiuj pliki z biblioteki rozwiązania WCF do folderu nowej biblioteki klas, utrzymując strukturę folderów.</span><span class="sxs-lookup"><span data-stu-id="08daf-157">Once the library has been created and added to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure.</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="08daf-158">Projekty platformy .NET w stylu zestawu SDK automatycznie zawierają wszystkie `.cs` pliki w lub w ich własnym katalogu, dlatego nie trzeba jawnie dodawać ich do projektu.</span><span class="sxs-lookup"><span data-stu-id="08daf-158">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so there's no need to explicitly add them to the project.</span></span> <span data-ttu-id="08daf-159">Jedyną pozostałą czynnością jest usunięcie `DataContract` i `DataMember` atrybutów z klas `Portfolio` i `PortfolioItem`, aby były to zwykłe stare C# klasy.</span><span class="sxs-lookup"><span data-stu-id="08daf-159">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes.</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="08daf-160">Użyj iniekcji zależności ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="08daf-160">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="08daf-161">Teraz można dodać odwołanie do tej biblioteki do projektu aplikacji gRPC i użyć klasy `PortfolioRepository` przy użyciu iniekcji zależności w implementacji usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="08daf-161">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="08daf-162">W aplikacji WCF funkcja wstrzykiwania zależności została dostarczona przez kontener Autofac IoC.</span><span class="sxs-lookup"><span data-stu-id="08daf-162">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="08daf-163">ASP.NET Core ma rozszerzania iniekcji zależności w; repozytorium można zarejestrować w metodzie `ConfigureServices` w klasie `Startup`.</span><span class="sxs-lookup"><span data-stu-id="08daf-163">ASP.NET Core has dependency injection baked in; the repository can be registered in the `ConfigureServices` method in the `Startup` class.</span></span>

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

<span data-ttu-id="08daf-164">Implementację `IPortfolioRepository` można teraz określić jako parametr konstruktora w klasie `PortfolioService` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="08daf-164">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="08daf-165">Implementowanie usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="08daf-165">Implement the gRPC service</span></span>

<span data-ttu-id="08daf-166">Po zadeklarowaniu komunikatów i usługi w pliku `portfolios.proto` musisz zaimplementować metody usługi w klasie `PortfolioService`, która dziedziczy z klasy `Portfolios.PortfoliosBase` generowanej przez gRPC.</span><span class="sxs-lookup"><span data-stu-id="08daf-166">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="08daf-167">Metody są zadeklarowane jako `virtual` w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="08daf-167">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="08daf-168">Jeśli ich nie zastąpisz, domyślnie zwróci kod stanu gRPC "nie zaimplementowana".</span><span class="sxs-lookup"><span data-stu-id="08daf-168">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="08daf-169">Zacznij od wprowadzenia metody `Get`.</span><span class="sxs-lookup"><span data-stu-id="08daf-169">Start by implementing the `Get` method.</span></span> <span data-ttu-id="08daf-170">Domyślne przesłonięcie wygląda tak, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="08daf-170">The default override looks like the following example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="08daf-171">Pierwszy problem polega na tym, że `request.TraderId` jest ciągiem, a usługa wymaga `Guid`.</span><span class="sxs-lookup"><span data-stu-id="08daf-171">The first issue is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="08daf-172">Mimo że oczekiwany format ciągu jest `UUID`, kod musi zajmować się możliwością, że obiekt wywołujący wysłał nieprawidłową wartość i odpowiednio odpowiada.</span><span class="sxs-lookup"><span data-stu-id="08daf-172">Even though the expected format for the string is a `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="08daf-173">Usługa może odpowiedzieć z błędami przez wyrzucanie `RpcException` i użycie standardowego kodu stanu `InvalidArgument` do wyznaczania problemu.</span><span class="sxs-lookup"><span data-stu-id="08daf-173">The service can respond with errors by throwing an `RpcException`, and use the standard `InvalidArgument` status code to express the problem.</span></span>

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

<span data-ttu-id="08daf-174">Gdy istnieje właściwa `Guid` wartość dla `traderId`, można użyć repozytorium do pobrania portfolio i zwrócić go do klienta programu.</span><span class="sxs-lookup"><span data-stu-id="08daf-174">Once there's a proper `Guid` value for `traderId`, the repository can be used to retrieve the Portfolio and return it to the client.</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="08daf-175">Mapowanie wewnętrznych modeli na komunikaty gRPC</span><span class="sxs-lookup"><span data-stu-id="08daf-175">Map internal models to gRPC messages</span></span>

<span data-ttu-id="08daf-176">Poprzedni kod nie działa, ponieważ repozytorium zwraca własny model POCO `Portfolio`, ale *gRPC potrzebuje własnego* `Portfolio` komunikatów protobuf.</span><span class="sxs-lookup"><span data-stu-id="08daf-176">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs *its* own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="08daf-177">Podobnie jak mapowanie typów Entity Framework do typów transferu danych, najlepszym rozwiązaniem jest zapewnienie konwersji między nimi.</span><span class="sxs-lookup"><span data-stu-id="08daf-177">Much like mapping Entity Framework types to data transfer types, the best solution is to provide conversion between the two.</span></span> <span data-ttu-id="08daf-178">Dobrym miejscem, aby umieścić kod dla tego elementu, znajduje się w klasie wygenerowanej przez protobuf, która jest zadeklarowana jako Klasa `partial`, więc można ją rozszerzyć.</span><span class="sxs-lookup"><span data-stu-id="08daf-178">A good place to put the code for this is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended.</span></span>

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
> <span data-ttu-id="08daf-179">Można użyć biblioteki, takiej jak [automapowania](https://automapper.org/) , do obsługi tej konwersji z klas wewnętrznych modelu do typów protobuf, o ile można skonfigurować konwersje typu niższego poziomu, takie jak `string` / `Guid` lub `decimal` / `double` i mapowanie listy.</span><span class="sxs-lookup"><span data-stu-id="08daf-179">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="08daf-180">Przy użyciu kodu konwersji w miejscu można wykonać implementację metody `Get`.</span><span class="sxs-lookup"><span data-stu-id="08daf-180">With the conversion code in place, the `Get` method implementation can be completed.</span></span>

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

<span data-ttu-id="08daf-181">Implementacja metody `GetAll` jest podobna.</span><span class="sxs-lookup"><span data-stu-id="08daf-181">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="08daf-182">Należy zauważyć, że pola `repeated` w komunikatach protobuf są generowane jako właściwości `readonly` typu `RepeatedField<T>`, dlatego należy dodać do nich elementy przy użyciu metody `AddRange`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="08daf-182">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them using the `AddRange` method, like in the following example:</span></span>

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

<span data-ttu-id="08daf-183">Pomyślnie przeprowadzono migrację usługi żądania WCF-odpowiedź do gRPC, przyjrzyjmy się tworzeniu klienta dla niego z pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="08daf-183">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="08daf-184">Generuj kod klienta</span><span class="sxs-lookup"><span data-stu-id="08daf-184">Generate client code</span></span>

<span data-ttu-id="08daf-185">Utwórz bibliotekę klas .NET Standard w tym samym rozwiązaniu, aby zawierała klienta.</span><span class="sxs-lookup"><span data-stu-id="08daf-185">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="08daf-186">Jest to przede wszystkim przykład tworzenia kodu klienta, ale można go spakować przy użyciu NuGet i rozpowszechniać w ramach wewnętrznego repozytorium dla innych zespołów .NET do użycia.</span><span class="sxs-lookup"><span data-stu-id="08daf-186">This is primarily an example of creating client code, but you could package such a library using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="08daf-187">Przejdź dalej i Dodaj nową bibliotekę klas .NET Standard o nazwie `TraderSys.Portfolios.Client` do rozwiązania i Usuń plik `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="08daf-187">Go ahead and add a new .NET Standard Class Library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="08daf-188">Pakiet NuGet [GRPC .NET. Client](https://www.nuget.org/packages/Grpc.Net.Client) wymaga platformy .net Core 3,0 (lub innego środowiska uruchomieniowego zgodnego z .NET Standard 2,1).</span><span class="sxs-lookup"><span data-stu-id="08daf-188">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="08daf-189">Starsze wersje .NET Framework i .NET Core są obsługiwane przez pakiet NuGet [GRPC. Core](https://www.nuget.org/packages/Grpc.Core) .</span><span class="sxs-lookup"><span data-stu-id="08daf-189">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="08daf-190">W programie Visual Studio 2019 można dodać odwołania do usług gRPC, podobnie jak w przypadku dodawania odwołań do usług do projektów WCF we wcześniejszych wersjach programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08daf-190">In Visual Studio 2019, you can add references to gRPC services similar to the way you'd add Service References to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="08daf-191">Odwołania do usług i połączone usługi są zarządzane w ramach tego samego interfejsu użytkownika teraz, do którego można uzyskać dostęp, klikając prawym przyciskiem myszy węzeł **zależności** w projekcie `TraderSys.Portfolios.Client` w Eksplorator rozwiązań i wybierając pozycję **Dodaj usługę połączoną**.</span><span class="sxs-lookup"><span data-stu-id="08daf-191">Service References and Connected Services are all managed under the same UI now, which you can access by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="08daf-192">W wyświetlonym oknie narzędzi wybierz sekcję odwołania do **usługi** , a następnie kliknij pozycję **Dodaj nowe odwołanie do usługi gRPC**.</span><span class="sxs-lookup"><span data-stu-id="08daf-192">In the tool window that appears, select the **Service References** section and click **Add new gRPC service reference**.</span></span>

![Interfejs użytkownika usług połączonych w programie Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="08daf-194">Przejdź do pliku `portfolios.proto` w projekcie `TraderSys.Portfolios`, pozostaw **Typ klasy do wygenerowania** jako **Klient**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="08daf-194">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave the **type of class to be generated** as **Client**, and click **OK**.</span></span>

![Okno dialogowe Dodawanie nowego odwołania do usługi gRPC w programie Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="08daf-196">Należy zauważyć, że to okno dialogowe zawiera również pole adresu URL.</span><span class="sxs-lookup"><span data-stu-id="08daf-196">Notice that this dialog also provides a URL field.</span></span> <span data-ttu-id="08daf-197">Jeśli Twoja organizacja utrzymuje katalog `.proto` plików dostępny dla sieci Web, można utworzyć klientów bezpośrednio przez ustawienie tego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="08daf-197">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="08daf-198">W przypadku korzystania z funkcji **dodawania usługi połączonej** programu Visual Studio plik `portfolios.proto` jest dodawany do projektu biblioteki klas jako *plik połączony*, a nie skopiowane, więc zmiany w pliku w projekcie usługi zostaną automatycznie zastosowane na kliencie projektu.</span><span class="sxs-lookup"><span data-stu-id="08daf-198">When using the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the Class Library project as a *linked file*, rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="08daf-199">Element `<Protobuf>` w pliku `csproj` wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="08daf-199">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="08daf-200">Jeśli nie używasz programu Visual Studio lub wolisz pracować z wiersza polecenia, możesz użyć narzędzia globalnego **dotnet-GRPC** do zarządzania odwołaniami protobuf w ramach projektu .NET GRPC.</span><span class="sxs-lookup"><span data-stu-id="08daf-200">If you are not using Visual Studio or prefer to work from the command line, you can use the **dotnet-grpc** global tool to manage Protobuf references within a .NET gRPC project.</span></span> <span data-ttu-id="08daf-201">[Aby uzyskać więcej informacji, zapoznaj się z dokumentacją programu **dotnet-GRPC** ](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span><span class="sxs-lookup"><span data-stu-id="08daf-201">[Refer to the **dotnet-grpc** documentation for more information](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="08daf-202">Korzystanie z usługi portfolio w aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="08daf-202">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="08daf-203">Poniższy kod stanowi krótki przykład użycia wygenerowanego klienta w aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="08daf-203">The following code is a brief example of using the generated client in a console application.</span></span> <span data-ttu-id="08daf-204">Bardziej szczegółowa Eksploracja kodu klienta gRPC znajduje się na końcu tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="08daf-204">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="08daf-205">Teraz przeprowadzono migrację podstawowej aplikacji WCF do ASP.NET Core usługi gRPC i utworzono klienta w celu korzystania z usługi z poziomu aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="08daf-205">Now, you've migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="08daf-206">Następna sekcja będzie obejmować więcej "dupleks" usług.</span><span class="sxs-lookup"><span data-stu-id="08daf-206">The next section will cover the more involved "duplex" services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="08daf-207">[Poprzedni](create-project.md)
>[Następny](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="08daf-207">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
