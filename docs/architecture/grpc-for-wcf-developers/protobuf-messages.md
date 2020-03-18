---
title: Wiadomości Protobuf - gRPC dla programistów WCF
description: Dowiedz się, jak wiadomości Protobuf są zdefiniowane w IDL i generowane w języku C#.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147987"
---
# <a name="protobuf-messages"></a><span data-ttu-id="8fc9f-103">Komunikaty Protobuf</span><span class="sxs-lookup"><span data-stu-id="8fc9f-103">Protobuf messages</span></span>

<span data-ttu-id="8fc9f-104">W tej sekcji opisano sposób deklarowania komunikatów `.proto` buforu protokołu (Protobuf) w plikach.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="8fc9f-105">Wyjaśnia podstawowe pojęcia numerów pól i typów i patrzy na kod `protoc` C#, który generuje kompilator.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="8fc9f-106">Reszta rozdziału będzie bardziej szczegółowo patrzeć na to, jak różne rodzaje danych są reprezentowane w Protobuf.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="8fc9f-107">Deklarowanie wiadomości</span><span class="sxs-lookup"><span data-stu-id="8fc9f-107">Declaring a message</span></span>

<span data-ttu-id="8fc9f-108">W programie Windows Communication Foundation `Stock` (WCF) klasa dla aplikacji obrotu giełdowego może być zdefiniowana w następujący sposób w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8fc9f-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="8fc9f-109">Aby zaimplementować równoważną klasę w Protobuf, należy zadeklarować ją w `.proto` pliku.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="8fc9f-110">Kompilator `protoc` wygeneruje klasę .NET jako część procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="8fc9f-111">Pierwszy wiersz deklaruje używaną wersję składni.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="8fc9f-112">Wersja 3 języka została wydana w 2016 roku.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="8fc9f-113">Jest to wersja, którą polecamy dla usług gRPC.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="8fc9f-114">Wiersz `option csharp_namespace` określa obszar nazw, który ma być używany dla wygenerowanych typów C#.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="8fc9f-115">Ta opcja zostanie zignorowana, `.proto` gdy plik zostanie skompilowany dla innych języków.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="8fc9f-116">Pliki Protobuf często zawierają opcje specyficzne dla języka dla kilku języków.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="8fc9f-117">Definicja `Stock` wiadomości określa cztery pola.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="8fc9f-118">Każdy z nich ma typ, nazwę i numer pola.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="8fc9f-119">Numery pól</span><span class="sxs-lookup"><span data-stu-id="8fc9f-119">Field numbers</span></span>

<span data-ttu-id="8fc9f-120">Numery pól są ważną częścią Protobuf.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="8fc9f-121">Są one używane do identyfikowania pól w binarnych zakodowanych danych, co oznacza, że nie można zmienić z wersji na wersję usługi.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="8fc9f-122">Zaletą jest to, że zgodność z poprzednimi wersjami i kompatybilność do przodu są możliwe.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="8fc9f-123">Klienci i usługi po prostu zignorują numery pól, o których nie wiedzą, o ile jest obsługiwana możliwość brakujących wartości.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="8fc9f-124">W formacie binarnym numer pola jest łączony z identyfikatorem typu.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="8fc9f-125">Numery pól od 1 do 15 mogą być kodowane z ich typem jako pojedynczy bajt.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="8fc9f-126">Liczby od 16 do 2047 wziąć 2 bajty.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="8fc9f-127">Możesz iść wyżej, jeśli potrzebujesz więcej niż 2047 pól w wiadomości z jakiegokolwiek powodu.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="8fc9f-128">Identyfikatory pojedynczego bajtu dla numerów pól od 1 do 15 oferują lepszą wydajność, dlatego należy ich używać w najbardziej podstawowych, często używanych polach.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="8fc9f-129">Typy</span><span class="sxs-lookup"><span data-stu-id="8fc9f-129">Types</span></span>

<span data-ttu-id="8fc9f-130">Deklaracje typów są przy użyciu natywnych typów danych skalarnych Protobuf, które zostały omówione bardziej szczegółowo w [następnej sekcji](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="8fc9f-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="8fc9f-131">Pozostała część tego rozdziału obejmie wbudowane typy Protobuf i pokaże, jak odnoszą się one do typowych typów .NET.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="8fc9f-132">Protobuf nie obsługuje natywnie `decimal` `double` typu, więc jest używany zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="8fc9f-133">W przypadku aplikacji, które wymagają pełnej dokładności dziesiętnej, należy zapoznać się z [sekcją dotyczącą miejsc dziesiętnych](protobuf-data-types.md#decimals) w następnej części tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="8fc9f-134">Wygenerowany kod</span><span class="sxs-lookup"><span data-stu-id="8fc9f-134">The generated code</span></span>

<span data-ttu-id="8fc9f-135">Podczas tworzenia aplikacji Protobuf tworzy klasy dla każdego z komunikatów, mapowanie jego typów natywnych do typów C#.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="8fc9f-136">Wygenerowany `Stock` typ będzie miał następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="8fc9f-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="8fc9f-137">Rzeczywisty kod, który jest generowany jest znacznie bardziej skomplikowane niż to.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="8fc9f-138">Powodem jest to, że każda klasa zawiera cały kod niezbędny do serializacji i deserializacji się do formatu przewodu binarnego.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="8fc9f-139">Nazwy właściwości</span><span class="sxs-lookup"><span data-stu-id="8fc9f-139">Property names</span></span>

<span data-ttu-id="8fc9f-140">Należy zauważyć, że kompilator `PascalCase` Protobuf stosowane `snake_case` do `.proto` nazw właściwości, mimo że były one w pliku.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="8fc9f-141">[Protobuf styl przewodnik](https://developers.google.com/protocol-buffers/docs/style) zaleca `snake_case` użycie w definicjach wiadomości, tak aby generowanie kodu dla innych platform produkuje oczekiwane go dla ich konwencji.</span><span class="sxs-lookup"><span data-stu-id="8fc9f-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8fc9f-142">[Poprzedni](protocol-buffers.md)
>[następny](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="8fc9f-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
