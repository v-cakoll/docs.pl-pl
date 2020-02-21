---
title: Protobuf messages — gRPC dla deweloperów WCF
description: Dowiedz się, w jaki sposób komunikaty protobuf są zdefiniowane w C#IDL i generowane w.
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543043"
---
# <a name="protobuf-messages"></a><span data-ttu-id="7517e-103">Komunikaty Protobuf</span><span class="sxs-lookup"><span data-stu-id="7517e-103">Protobuf messages</span></span>

<span data-ttu-id="7517e-104">W tej sekcji opisano sposób deklarowania komunikatów buforu protokołu (protobuf) w plikach `.proto`.</span><span class="sxs-lookup"><span data-stu-id="7517e-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="7517e-105">Objaśniono podstawowe pojęcia dotyczące numerów pól i typów oraz sprawdza C# kod generowany przez kompilator `protoc`.</span><span class="sxs-lookup"><span data-stu-id="7517e-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span> 

<span data-ttu-id="7517e-106">Pozostała część rozdziału zawiera bardziej szczegółowe informacje na temat sposobu reprezentowania różnych typów danych w protobuf.</span><span class="sxs-lookup"><span data-stu-id="7517e-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="7517e-107">Deklarowanie komunikatu</span><span class="sxs-lookup"><span data-stu-id="7517e-107">Declaring a message</span></span>

<span data-ttu-id="7517e-108">W Windows Communication Foundation (WCF) Klasa `Stock` dla aplikacji handlowego rynku giełdowego może być zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7517e-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

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

<span data-ttu-id="7517e-109">Aby zaimplementować równoważną klasę w protobuf, należy zadeklarować ją w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="7517e-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="7517e-110">Kompilator `protoc` będzie następnie generować klasę .NET jako część procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7517e-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

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

<span data-ttu-id="7517e-111">Pierwszy wiersz deklaruje używaną wersję składni.</span><span class="sxs-lookup"><span data-stu-id="7517e-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="7517e-112">Wersja 3 języka została wydana w 2016.</span><span class="sxs-lookup"><span data-stu-id="7517e-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="7517e-113">Jest to wersja, którą zalecamy dla usług gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="7517e-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="7517e-114">Wiersz `option csharp_namespace` określa przestrzeń nazw, która ma być używana dla wygenerowanych C# typów.</span><span class="sxs-lookup"><span data-stu-id="7517e-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="7517e-115">Ta opcja zostanie zignorowana w przypadku skompilowania pliku `.proto` dla innych języków.</span><span class="sxs-lookup"><span data-stu-id="7517e-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="7517e-116">Pliki protobuf często zawierają opcje specyficzne dla języka dla kilku języków.</span><span class="sxs-lookup"><span data-stu-id="7517e-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="7517e-117">Definicja komunikatu `Stock` określa cztery pola.</span><span class="sxs-lookup"><span data-stu-id="7517e-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="7517e-118">Każdy z nich ma typ, nazwę i numer pola.</span><span class="sxs-lookup"><span data-stu-id="7517e-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="7517e-119">Numery pól</span><span class="sxs-lookup"><span data-stu-id="7517e-119">Field numbers</span></span>

<span data-ttu-id="7517e-120">Numery pól są ważną częścią protobuf.</span><span class="sxs-lookup"><span data-stu-id="7517e-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="7517e-121">Są one używane do identyfikowania pól w szyfrowanych danych binarnych, co oznacza, że nie mogą ulec zmianie z wersji na wersję usługi.</span><span class="sxs-lookup"><span data-stu-id="7517e-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="7517e-122">Zalety tej usługi to zgodność z poprzednimi wersjami i zgodność.</span><span class="sxs-lookup"><span data-stu-id="7517e-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="7517e-123">Klienci i usługi będą po prostu ignorować numery pól, o których nie znają, tak długo, jak można obsługiwać brakujące wartości.</span><span class="sxs-lookup"><span data-stu-id="7517e-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="7517e-124">W formacie binarnym numer pola jest połączony z identyfikatorem typu.</span><span class="sxs-lookup"><span data-stu-id="7517e-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="7517e-125">Numery pól od 1 do 15 można zakodować ich typem jako pojedynczy bajt.</span><span class="sxs-lookup"><span data-stu-id="7517e-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="7517e-126">Liczby z 16 do 2 047 mają 2 bajty.</span><span class="sxs-lookup"><span data-stu-id="7517e-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="7517e-127">Jeśli potrzebujesz więcej niż 2 047 pól w komunikacie z dowolnego powodu, możesz przejść do wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="7517e-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="7517e-128">Identyfikatory pojedynczych bajtów dla numerów pól od 1 do 15 oferują lepszą wydajność, dlatego należy używać ich w przypadku najbardziej podstawowych, często używanych pól.</span><span class="sxs-lookup"><span data-stu-id="7517e-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="7517e-129">Typy</span><span class="sxs-lookup"><span data-stu-id="7517e-129">Types</span></span>

<span data-ttu-id="7517e-130">Deklaracje typu korzystają z natywnych typów danych skalarnych protobuf, które zostały omówione bardziej szczegółowo w [następnej sekcji](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="7517e-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="7517e-131">Pozostała część tego rozdziału obejmuje wbudowane typy protobuf i pokazuje, w jaki sposób odnoszą się do wspólnych typów .NET.</span><span class="sxs-lookup"><span data-stu-id="7517e-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="7517e-132">Protobuf nie obsługuje natywnie typu `decimal`, więc zamiast tego użyto `double`.</span><span class="sxs-lookup"><span data-stu-id="7517e-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="7517e-133">W przypadku aplikacji wymagających pełnej precyzji dziesiętnej zapoznaj się z [sekcją miejsc dziesiętnych](protobuf-data-types.md#decimals) w następnej części tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="7517e-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="7517e-134">Wygenerowany kod</span><span class="sxs-lookup"><span data-stu-id="7517e-134">The generated code</span></span>

<span data-ttu-id="7517e-135">Podczas kompilowania aplikacji protobuf tworzy klasy dla poszczególnych komunikatów, mapując typy natywne na C# typy.</span><span class="sxs-lookup"><span data-stu-id="7517e-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="7517e-136">Wygenerowany typ `Stock` powinien mieć następującą sygnaturę:</span><span class="sxs-lookup"><span data-stu-id="7517e-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="7517e-137">Rzeczywisty wygenerowany kod jest znacznie bardziej skomplikowany niż ten.</span><span class="sxs-lookup"><span data-stu-id="7517e-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="7517e-138">Przyczyną jest to, że każda klasa zawiera cały kod, który jest niezbędny do serializacji i deserializacji samego formatu sieci binarnej.</span><span class="sxs-lookup"><span data-stu-id="7517e-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="7517e-139">Nazwy właściwości</span><span class="sxs-lookup"><span data-stu-id="7517e-139">Property names</span></span>

<span data-ttu-id="7517e-140">Należy zauważyć, że kompilator protobuf zastosował `PascalCase` do nazw właściwości, chociaż zostały one `snake_case` w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="7517e-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="7517e-141">[Przewodnik stylu protobuf](https://developers.google.com/protocol-buffers/docs/style) zaleca używanie `snake_case` w definicjach komunikatów, dzięki czemu generowanie kodu dla innych platform daje oczekiwany przypadek dla ich Konwencji.</span><span class="sxs-lookup"><span data-stu-id="7517e-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7517e-142">[Poprzednie](protocol-buffers.md)
>[dalej](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="7517e-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
