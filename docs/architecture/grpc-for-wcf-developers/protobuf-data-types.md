---
title: Protobuf typy danych skalarnych — gRPC dla deweloperów WCF
description: Dowiedz się więcej o podstawowych i dobrze znanych typach danych obsługiwanych przez protobuf i gRPC w programie .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: ae7f5f48099000dff0eefb36e23cb9b9f2ac517c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971553"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="ed6ea-103">Typy danych skalarnych Protobuf</span><span class="sxs-lookup"><span data-stu-id="ed6ea-103">Protobuf scalar data types</span></span>

<span data-ttu-id="ed6ea-104">Protobuf obsługuje zakres natywnych typów wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-104">Protobuf supports a range of native scalar value types.</span></span> <span data-ttu-id="ed6ea-105">W poniższej tabeli wymieniono wszystkie ich typy równoważne C# :</span><span class="sxs-lookup"><span data-stu-id="ed6ea-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="ed6ea-106">Typ protobuf</span><span class="sxs-lookup"><span data-stu-id="ed6ea-106">Protobuf type</span></span> | <span data-ttu-id="ed6ea-107">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="ed6ea-107">C# type</span></span>      | <span data-ttu-id="ed6ea-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed6ea-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="ed6ea-109">1</span><span class="sxs-lookup"><span data-stu-id="ed6ea-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="ed6ea-110">1</span><span class="sxs-lookup"><span data-stu-id="ed6ea-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="ed6ea-111">1</span><span class="sxs-lookup"><span data-stu-id="ed6ea-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="ed6ea-112">1</span><span class="sxs-lookup"><span data-stu-id="ed6ea-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="ed6ea-113">2</span><span class="sxs-lookup"><span data-stu-id="ed6ea-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="ed6ea-114">2</span><span class="sxs-lookup"><span data-stu-id="ed6ea-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="ed6ea-115">2</span><span class="sxs-lookup"><span data-stu-id="ed6ea-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="ed6ea-116">2</span><span class="sxs-lookup"><span data-stu-id="ed6ea-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="ed6ea-117">3</span><span class="sxs-lookup"><span data-stu-id="ed6ea-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="ed6ea-118">4</span><span class="sxs-lookup"><span data-stu-id="ed6ea-118">4</span></span>     |

## <a name="notes"></a><span data-ttu-id="ed6ea-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed6ea-119">Notes</span></span>

1. <span data-ttu-id="ed6ea-120">Standardowe kodowanie dla `int32` i `int64` jest niewydajne podczas pracy z podpisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-120">The standard encoding for `int32` and `int64` is inefficient when working with signed values.</span></span> <span data-ttu-id="ed6ea-121">Jeśli pole może zawierać liczby ujemne, zamiast tego użyj `sint32` lub `sint64`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="ed6ea-122">Oba typy są C# mapowane odpowiednio do `int` i `long`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-122">Both types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="ed6ea-123">Pola `fixed` zawsze używają tej samej liczby bajtów niezależnie od tego, co jest wartością.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="ed6ea-124">Takie zachowanie powoduje szybsze wykonywanie serializacji i deserializacji w przypadku większych wartości.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="ed6ea-125">Ciągi protobuf są kodowane w UTF-8 (lub 7-bitowym formacie ASCII), a zakodowana długość nie może być większa niż 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded, and the encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="ed6ea-126">Środowisko uruchomieniowe protobuf udostępnia typ `ByteString`, który umożliwia łatwe mapowanie do C# i z `byte[]` tablic.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-126">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="ed6ea-127">Inne typy pierwotne platformy .NET</span><span class="sxs-lookup"><span data-stu-id="ed6ea-127">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="ed6ea-128">Daty i godziny</span><span class="sxs-lookup"><span data-stu-id="ed6ea-128">Dates and times</span></span>

<span data-ttu-id="ed6ea-129">Natywne typy skalarne nie zapewniają wartości daty i godziny, równoważne C#<xref:System.DateTimeOffset>, <xref:System.DateTime>i <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-129">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="ed6ea-130">Te typy można określić przy użyciu niektórych rozszerzeń "dobrze znane typy" firmy Google, które zapewniają obsługę generowania kodu i środowiska uruchomieniowego dla bardziej złożonych typów pól na obsługiwanych platformach.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-130">These types can be specified using some of Google's "Well Known Types" extensions, which provide code generation and runtime support for more complex field types across the supported platforms.</span></span> <span data-ttu-id="ed6ea-131">W poniższej tabeli przedstawiono typy daty i godziny:</span><span class="sxs-lookup"><span data-stu-id="ed6ea-131">The following table shows the date and time types:</span></span>

| <span data-ttu-id="ed6ea-132">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="ed6ea-132">C# type</span></span> | <span data-ttu-id="ed6ea-133">Nieznany typ protobuf</span><span class="sxs-lookup"><span data-stu-id="ed6ea-133">Protobuf well-known type</span></span> |
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

<span data-ttu-id="ed6ea-134">Wygenerowane właściwości w C# klasie nie są typami dat i godzin platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-134">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="ed6ea-135">Właściwości używają klas `Timestamp` i `Duration` w przestrzeni nazw `Google.Protobuf.WellKnownTypes`, które zapewniają metody konwersji do i z `DateTimeOffset`, `DateTime`i `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-135">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace, which provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="ed6ea-136">Typ `Timestamp` działa z czasem UTC; wartości `DateTimeOffset` zawsze mają przesunięcie zero, a właściwość `DateTime.Kind` będzie zawsze `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-136">The `Timestamp` type works with UTC times; `DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property will always be `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="ed6ea-137">System.Guid</span><span class="sxs-lookup"><span data-stu-id="ed6ea-137">System.Guid</span></span>

<span data-ttu-id="ed6ea-138">Typ <xref:System.Guid>, znany jako `UUID` na innych platformach, nie jest bezpośrednio obsługiwany przez protobuf i nie ma dobrze znanego typu.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-138">The <xref:System.Guid> type, known as `UUID` on other platforms, isn't directly supported by Protobuf and there's no well-known type for it.</span></span> <span data-ttu-id="ed6ea-139">Najlepszym podejściem jest obsłużenie `Guid` wartości jako pola `string` przy użyciu standardowego `8-4-4-4-12` formacie szesnastkowym (na przykład `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), który może być analizowany przez wszystkie języki i platformy.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-139">The best approach is to handle `Guid` values as `string` field, using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), which can be parsed by all languages and platforms.</span></span> <span data-ttu-id="ed6ea-140">Nie używaj `bytes` pola do `Guid` wartości, ponieważ problemy z przypisaniami mogą spowodować błędne zachowanie podczas współpracy z innymi platformami, takimi jak Java.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-140">Don't use a `bytes` field for `Guid` values, as problems with endianness can result in erratic behavior when interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="ed6ea-141">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="ed6ea-141">Nullable types</span></span>

<span data-ttu-id="ed6ea-142">Generowanie kodu protobuf dla programu C# używa typów natywnych, takich jak `int` `int32`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-142">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="ed6ea-143">Oznacza to, że wartości są zawsze uwzględniane i nie mogą mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-143">This means that the values are always included and can't be null.</span></span> <span data-ttu-id="ed6ea-144">Dla wartości, które wymagają jawnej wartości null, takich jak używanie C# `int?` w kodzie, protobuf "dobrze znane typy" obejmują otoki, które są kompilowane C# na typy dopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-144">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="ed6ea-145">Aby ich użyć, zaimportuj `wrappers.proto` do pliku `.proto`, tak jak to:</span><span class="sxs-lookup"><span data-stu-id="ed6ea-145">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="ed6ea-146">Protobuf będzie używać prostej `T?` (na przykład `int?`) dla wygenerowanej właściwości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-146">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="ed6ea-147">W poniższej tabeli przedstawiono pełną listę typów otoki o równoważnym C# typie:</span><span class="sxs-lookup"><span data-stu-id="ed6ea-147">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="ed6ea-148">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="ed6ea-148">C# type</span></span>   | <span data-ttu-id="ed6ea-149">Otoka dobrze znanego typu</span><span class="sxs-lookup"><span data-stu-id="ed6ea-149">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="ed6ea-150">Dobrze znane typy `Timestamp` i `Duration` są reprezentowane w programie .NET jako klasy, więc nie ma potrzeby stosowania wersji dopuszczających wartości null, ale ważne jest, aby sprawdzić, czy właściwości tych typów są puste w przypadku konwertowania na `DateTimeOffset` lub `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-150">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version, but it's important to check for null on properties of those types when converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="ed6ea-151">miejsca dziesiętne</span><span class="sxs-lookup"><span data-stu-id="ed6ea-151">Decimals</span></span>

<span data-ttu-id="ed6ea-152">Protobuf nie obsługuje natywnie typu `decimal` .NET, po prostu `double` i `float`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-152">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="ed6ea-153">W projekcie protobuf istnieje trwająca dyskusja dotycząca możliwości dodawania standardowego typu `Decimal` do dobrze znanych typów, z obsługą platformy dla języków i struktur, które go obsługują, ale nic nie zostało jeszcze zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-153">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it, but nothing has been implemented yet.</span></span>

<span data-ttu-id="ed6ea-154">Istnieje możliwość utworzenia definicji komunikatu reprezentującej typ `decimal`, który będzie działał do bezpiecznej serializacji między klientami i serwerami platformy .NET, ale deweloperzy na innych platformach będą musieli zrozumieć używany format i wdrożyć ich własny sposób obsługi.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-154">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers, but developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="ed6ea-155">Tworzenie niestandardowego typu dziesiętnego dla protobuf</span><span class="sxs-lookup"><span data-stu-id="ed6ea-155">Creating a custom Decimal type for Protobuf</span></span>

<span data-ttu-id="ed6ea-156">Bardzo prosta implementacja może być podobna do niestandardowym typem `Money` używanym przez niektóre interfejsy API usługi Google, bez pola `currency`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-156">A very simple implementation could be similar to the non-standard `Money` type used by some Google APIs, without the `currency` field.</span></span>

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

<span data-ttu-id="ed6ea-157">Pole `nanos` reprezentuje wartości z `0.999_999_999` do `-0.999_999_999`.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-157">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="ed6ea-158">Na przykład `decimal` wartość `1.5m` byłaby reprezentowana jako `{ units = 1, nanos = 500_000_000 }` (dlatego w polu `nanos` w tym przykładzie jest używany typ `sfixed32`, który koduje bardziej wydajny niż `int32` dla większych wartości).</span><span class="sxs-lookup"><span data-stu-id="ed6ea-158">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }` (this is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values).</span></span> <span data-ttu-id="ed6ea-159">Jeśli pole `units` ma wartość ujemną, pole `nanos` powinno również być ujemne.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-159">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="ed6ea-160">Istnieje wiele innych algorytmów kodowania `decimal` wartości jako ciągi bajtów, ale ten komunikat jest znacznie łatwiejszy do zrozumienia, a wartości nie *[wpływają na różne](https://en.wikipedia.org/wiki/Endianness)* platformy.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-160">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is much easier to understand than any of them, and the values are not affected by *[endianness](https://en.wikipedia.org/wiki/Endianness)* on different platforms.</span></span>

<span data-ttu-id="ed6ea-161">Konwersję między tym typem i typem `decimal` BCL można zaimplementować w C# taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-161">Conversion between this type and the BCL `decimal` type could be implemented in C# like this.</span></span>

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
> <span data-ttu-id="ed6ea-162">Za każdym razem, gdy korzystasz z niestandardowych typów komunikatów narzędzi takich jak to, **musisz udokumentować** je za pomocą komentarzy w `.proto`, tak aby inni deweloperzy mogli zaimplementować konwersję do i z odpowiedniego typu w własnym języku lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="ed6ea-162">Whenever you use custom utility message types like this, you **must** document them with comments in the `.proto` so that other developers can implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ed6ea-163">[Poprzedni](protobuf-messages.md)
>[Następny](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="ed6ea-163">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
