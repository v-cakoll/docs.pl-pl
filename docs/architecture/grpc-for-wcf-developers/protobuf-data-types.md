---
title: Protobuf typy danych skalarnych — gRPC dla deweloperów WCF
description: Dowiedz się więcej o podstawowych i dobrze znanych typach danych obsługiwanych przez protobuf i gRPC w programie .NET Core.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 8c8db795e927a44e9f75ec828336630ec9978eb6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184268"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="76150-103">Protobuf typy danych skalarnych</span><span class="sxs-lookup"><span data-stu-id="76150-103">Protobuf scalar data types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="76150-104">Protobuf obsługuje zakres natywnych typów wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="76150-104">Protobuf supports a range of native scalar value types.</span></span> <span data-ttu-id="76150-105">W poniższej tabeli wymieniono wszystkie ich typy równoważne C# :</span><span class="sxs-lookup"><span data-stu-id="76150-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="76150-106">Typ protobuf</span><span class="sxs-lookup"><span data-stu-id="76150-106">Protobuf type</span></span> | <span data-ttu-id="76150-107">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="76150-107">C# type</span></span>      | <span data-ttu-id="76150-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76150-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="76150-109">1</span><span class="sxs-lookup"><span data-stu-id="76150-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="76150-110">1</span><span class="sxs-lookup"><span data-stu-id="76150-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="76150-111">1</span><span class="sxs-lookup"><span data-stu-id="76150-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="76150-112">1</span><span class="sxs-lookup"><span data-stu-id="76150-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="76150-113">2</span><span class="sxs-lookup"><span data-stu-id="76150-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="76150-114">2</span><span class="sxs-lookup"><span data-stu-id="76150-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="76150-115">2</span><span class="sxs-lookup"><span data-stu-id="76150-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="76150-116">2</span><span class="sxs-lookup"><span data-stu-id="76150-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="76150-117">3</span><span class="sxs-lookup"><span data-stu-id="76150-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="76150-118">4</span><span class="sxs-lookup"><span data-stu-id="76150-118">4</span></span>     |

## <a name="notes"></a><span data-ttu-id="76150-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76150-119">Notes</span></span>

1. <span data-ttu-id="76150-120">Standardowe kodowanie dla `int32` i `int64` jest niewydajne podczas pracy z podpisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="76150-120">The standard encoding for `int32` and `int64` is inefficient when working with signed values.</span></span> <span data-ttu-id="76150-121">Jeśli pole może zawierać liczby ujemne, użyj `sint32` lub `sint64` zamiast.</span><span class="sxs-lookup"><span data-stu-id="76150-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="76150-122">Oba typy są C# `int` mapowane na typy `long` i, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="76150-122">Both types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="76150-123">`fixed` Pola zawsze używają tej samej liczby bajtów niezależnie od tego, co jest wartością.</span><span class="sxs-lookup"><span data-stu-id="76150-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="76150-124">Takie zachowanie powoduje szybsze wykonywanie serializacji i deserializacji w przypadku większych wartości.</span><span class="sxs-lookup"><span data-stu-id="76150-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="76150-125">Ciągi protobuf są kodowane w UTF-8 (lub 7-bitowym formacie ASCII), a zakodowana długość nie może być większa niż 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="76150-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded, and the encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="76150-126">Środowisko uruchomieniowe protobuf zapewnia `ByteString` typ, który umożliwia łatwe mapowanie do C# `byte[]` i z tablic.</span><span class="sxs-lookup"><span data-stu-id="76150-126">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="76150-127">Inne typy pierwotne platformy .NET</span><span class="sxs-lookup"><span data-stu-id="76150-127">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="76150-128">Daty i godziny</span><span class="sxs-lookup"><span data-stu-id="76150-128">Dates and times</span></span>

<span data-ttu-id="76150-129">Natywne typy skalarne nie zapewniają wartości daty i godziny, równoważne z C# <xref:System.DateTimeOffset>, <xref:System.DateTime>i <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="76150-129">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="76150-130">Te typy można określić przy użyciu niektórych rozszerzeń "dobrze znane typy" firmy Google, które zapewniają obsługę generowania kodu i środowiska uruchomieniowego dla bardziej złożonych typów pól na obsługiwanych platformach.</span><span class="sxs-lookup"><span data-stu-id="76150-130">These types can be specified using some of Google's "Well Known Types" extensions, which provide code generation and runtime support for more complex field types across the supported platforms.</span></span> <span data-ttu-id="76150-131">W poniższej tabeli przedstawiono typy daty i godziny:</span><span class="sxs-lookup"><span data-stu-id="76150-131">The following table shows the date and time types:</span></span>

| <span data-ttu-id="76150-132">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="76150-132">C# type</span></span> | <span data-ttu-id="76150-133">Nieznany typ protobuf</span><span class="sxs-lookup"><span data-stu-id="76150-133">Protobuf well-known type</span></span> |
| ------- | ------------------------ |
| `DateTimeOffset` | `google.protobuf.Timestamp` |
| `DateTime` | `google.protobuf.Timestamp` |
| `TimeSpan` | `google.protobuf.Duration` |

```protobuf  
syntax = "proto3"

import "google/protobuf/duration.proto";  
import "google/protobuf/timestamp.proto";

message Meeting {

    string subject = 1;
    google.protobuf.Timestamp time = 2;
    google.protobuf.Duration duration = 3;

}  
```

<span data-ttu-id="76150-134">Wygenerowane właściwości w C# klasie nie są typami dat i godzin platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="76150-134">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="76150-135">Właściwości używają `Timestamp` klas i `DateTime` `DateTimeOffset` `TimeSpan`w przestrzeni nazw, które zapewniają metody konwersji do i z, i. `Google.Protobuf.WellKnownTypes` `Duration`</span><span class="sxs-lookup"><span data-stu-id="76150-135">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace, which provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

```csharp
// Create Timestamp and Duration from .NET DateTimeOffset and TimeSpan
var meeting = new Meeting
{
    Time = Timestamp.FromDateTimeOffset(meetingTime), // also FromDateTime()
    Duration = Duration.FromTimeSpan(meetingLength)
};

// Convert Timestamp and Duration to .NET DateTimeOffset and TimeSpan
DateTimeOffset time = meeting.Time.ToDateTimeOffset();
TimeSpan? duration = meeting.Duration?.ToTimeSpan();
```

> [!NOTE]
> <span data-ttu-id="76150-136">`Timestamp` Typ działa z czasem UTC; wartości zawsze mają przesunięcie zero, `DateTime.Kind` a właściwość zawsze `DateTimeKind.Utc`będzie. `DateTimeOffset`</span><span class="sxs-lookup"><span data-stu-id="76150-136">The `Timestamp` type works with UTC times; `DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property will always be `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="76150-137">System.Guid</span><span class="sxs-lookup"><span data-stu-id="76150-137">System.Guid</span></span>

<span data-ttu-id="76150-138">Typ, znany jako `UUID` na innych platformach, nie jest bezpośrednio obsługiwany przez protobuf i nie ma dobrze znanego typu. <xref:System.Guid></span><span class="sxs-lookup"><span data-stu-id="76150-138">The <xref:System.Guid> type, known as `UUID` on other platforms, isn't directly supported by Protobuf and there's no well-known type for it.</span></span> <span data-ttu-id="76150-139">`Guid` Najlepszym podejściem jest obsłużenie wartości jako `string` pola przy użyciu standardowego `8-4-4-4-12` formatu szesnastkowego (na przykład `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), który może być analizowany przez wszystkie języki i platformy.</span><span class="sxs-lookup"><span data-stu-id="76150-139">The best approach is to handle `Guid` values as `string` field, using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), which can be parsed by all languages and platforms.</span></span> <span data-ttu-id="76150-140">Nie używaj `bytes` `Guid` pola wartości, ponieważ problemy z przypisaniami mogą spowodować błędne zachowanie podczas pracy z innymi platformami, takimi jak Java.</span><span class="sxs-lookup"><span data-stu-id="76150-140">Don't use a `bytes` field for `Guid` values, as problems with endianness can result in erratic behavior when interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="76150-141">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="76150-141">Nullable types</span></span>

<span data-ttu-id="76150-142">Generowanie kodu protobuf dla programu C# używa typów natywnych, takich jak `int` for `int32`.</span><span class="sxs-lookup"><span data-stu-id="76150-142">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="76150-143">Oznacza to, że wartości są zawsze uwzględniane i nie mogą mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="76150-143">This means that the values are always included and can't be null.</span></span> <span data-ttu-id="76150-144">Dla wartości, które wymagają jawnej wartości null, `int?` takich jak C# użycie w kodzie, protobuf "dobrze znane typy" obejmuje otoki, które są kompilowane C# na typy dopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="76150-144">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="76150-145">Aby go użyć, `wrappers.proto` zaimportuj `.proto` do pliku, tak jak to:</span><span class="sxs-lookup"><span data-stu-id="76150-145">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="76150-146">Protobuf będzie używać prostego `T?` (na `int?`przykład) dla wygenerowanej właściwości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="76150-146">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="76150-147">W poniższej tabeli przedstawiono pełną listę typów otoki o równoważnym C# typie:</span><span class="sxs-lookup"><span data-stu-id="76150-147">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="76150-148">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="76150-148">C# type</span></span>   | <span data-ttu-id="76150-149">Otoka dobrze znanego typu</span><span class="sxs-lookup"><span data-stu-id="76150-149">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="76150-150">Dobrze znane typy `Timestamp` i `Duration` są reprezentowane w programie .NET jako klasy, więc nie ma potrzeby stosowania wersji dopuszczających wartość null, ale ważne jest, aby sprawdzić, czy właściwości tych typów są puste w przypadku konwertowania `DateTimeOffset` na `TimeSpan`lub.</span><span class="sxs-lookup"><span data-stu-id="76150-150">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version, but it's important to check for null on properties of those types when converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="76150-151">Miejsca dziesiętne</span><span class="sxs-lookup"><span data-stu-id="76150-151">Decimals</span></span>

<span data-ttu-id="76150-152">Protobuf nie obsługuje natywnie typu .NET `decimal` , tylko `double` i `float`.</span><span class="sxs-lookup"><span data-stu-id="76150-152">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="76150-153">W projekcie protobuf istnieje trwająca dyskusja dotycząca możliwości dodawania typu standardowego `Decimal` do dobrze znanych typów, z obsługą platformy dla języków i struktur, które go obsługują, ale nic nie zostało jeszcze zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="76150-153">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it, but nothing has been implemented yet.</span></span>

<span data-ttu-id="76150-154">Istnieje możliwość utworzenia definicji komunikatu reprezentującej `decimal` typ, który będzie działał do bezpiecznej serializacji między klientami i serwerami platformy .NET, ale deweloperzy na innych platformach będą musieli zrozumieć używany format i zaimplementować własny Obsługa dla tego programu.</span><span class="sxs-lookup"><span data-stu-id="76150-154">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers, but developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="76150-155">Tworzenie niestandardowego typu dziesiętnego dla protobuf</span><span class="sxs-lookup"><span data-stu-id="76150-155">Creating a custom Decimal type for Protobuf</span></span>

<span data-ttu-id="76150-156">Bardzo prosta implementacja może być podobna do niestandardowym `Money` typem używanym przez niektóre interfejsy API Google, bez tego `currency` pola.</span><span class="sxs-lookup"><span data-stu-id="76150-156">A very simple implementation could be similar to the non-standard `Money` type used by some Google APIs, without the `currency` field.</span></span>

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message Decimal {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

<span data-ttu-id="76150-157">Pole reprezentuje wartości z `0.999_999_999` do `-0.999_999_999`. `nanos`</span><span class="sxs-lookup"><span data-stu-id="76150-157">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="76150-158">Na przykład `decimal` wartość `1.5m` będzie reprezentowana jako `{ units = 1, nanos = 500_000_000 }` ( `nanos` dlategow`int32` polu w tym przykładzie jest używany Typ,którykodujebardziejwydajneniżwprzypadkuwiększychwartości).`sfixed32`</span><span class="sxs-lookup"><span data-stu-id="76150-158">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }` (this is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values).</span></span> <span data-ttu-id="76150-159">Jeśli pole jest ujemne, pole powinno również być ujemne. `nanos` `units`</span><span class="sxs-lookup"><span data-stu-id="76150-159">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="76150-160">Istnieje wiele innych algorytmów kodowania `decimal` wartości jako ciągi bajtowe, ale ten komunikat jest znacznie łatwiejszy do zrozumienia, a wartości nie wpływają na różne platformy. *[](https://en.wikipedia.org/wiki/Endianness)*</span><span class="sxs-lookup"><span data-stu-id="76150-160">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is much easier to understand than any of them, and the values are not affected by *[endianness](https://en.wikipedia.org/wiki/Endianness)* on different platforms.</span></span>

<span data-ttu-id="76150-161">Konwersję między tym typem a typem `decimal` BCL można zaimplementować w C# taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="76150-161">Conversion between this type and the BCL `decimal` type could be implemented in C# like this.</span></span>

```csharp
namespace CustomTypes
{
    public partial class GrpcDecimal
    {
        private const decimal NanoFactor = 1_000_000_000;
        public GrpcDecimal(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.Decimal grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.Decimal(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.Decimal(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="76150-162">Za każdym razem, gdy korzystasz z niestandardowych typów komunikatów narzędzi takich jak to, **musisz** udokumentować je przy użyciu komentarzy w `.proto` tak, aby inni deweloperzy mogli zaimplementować konwersję do i z równoważnego typu w własnym języku lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="76150-162">Whenever you use custom utility message types like this, you **must** document them with comments in the `.proto` so that other developers can implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="76150-163">[Poprzedni](protobuf-messages.md)
>[Następny](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="76150-163">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
