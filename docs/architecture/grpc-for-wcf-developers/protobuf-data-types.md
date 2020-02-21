---
title: Protobuf typy danych skalarnych — gRPC dla deweloperów WCF
description: Dowiedz się więcej o podstawowych i dobrze znanych typach danych, które obsługują protobuf i gRPC w programie .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: f5215550a6a2d54dfe2e859c574a34f641fdb68d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543160"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="74710-103">Typy danych skalarnych Protobuf</span><span class="sxs-lookup"><span data-stu-id="74710-103">Protobuf scalar data types</span></span>

<span data-ttu-id="74710-104">Bufor protokołu (protobuf) obsługuje zakres natywnych typów wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="74710-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="74710-105">W poniższej tabeli wymieniono wszystkie ich typy równoważne C# :</span><span class="sxs-lookup"><span data-stu-id="74710-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="74710-106">Typ protobuf</span><span class="sxs-lookup"><span data-stu-id="74710-106">Protobuf type</span></span> | <span data-ttu-id="74710-107">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="74710-107">C# type</span></span>      | <span data-ttu-id="74710-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74710-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="74710-109">1</span><span class="sxs-lookup"><span data-stu-id="74710-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="74710-110">1</span><span class="sxs-lookup"><span data-stu-id="74710-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="74710-111">1</span><span class="sxs-lookup"><span data-stu-id="74710-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="74710-112">1</span><span class="sxs-lookup"><span data-stu-id="74710-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="74710-113">2</span><span class="sxs-lookup"><span data-stu-id="74710-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="74710-114">2</span><span class="sxs-lookup"><span data-stu-id="74710-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="74710-115">2</span><span class="sxs-lookup"><span data-stu-id="74710-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="74710-116">2</span><span class="sxs-lookup"><span data-stu-id="74710-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="74710-117">3</span><span class="sxs-lookup"><span data-stu-id="74710-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="74710-118">4</span><span class="sxs-lookup"><span data-stu-id="74710-118">4</span></span>     |

<span data-ttu-id="74710-119">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="74710-119">Notes:</span></span>

1. <span data-ttu-id="74710-120">Standardowe kodowanie dla `int32` i `int64` jest nieefektywne podczas pracy z podpisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="74710-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="74710-121">Jeśli pole może zawierać liczby ujemne, zamiast tego użyj `sint32` lub `sint64`.</span><span class="sxs-lookup"><span data-stu-id="74710-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="74710-122">Te typy są mapowane odpowiednio C# do typów `int` i `long`.</span><span class="sxs-lookup"><span data-stu-id="74710-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="74710-123">Pola `fixed` zawsze używają tej samej liczby bajtów niezależnie od tego, co jest wartością.</span><span class="sxs-lookup"><span data-stu-id="74710-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="74710-124">Takie zachowanie powoduje szybsze wykonywanie serializacji i deserializacji w przypadku większych wartości.</span><span class="sxs-lookup"><span data-stu-id="74710-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="74710-125">Ciągi protobuf są kodowane w formacie UTF-8 (lub 7-bitowym ASCII).</span><span class="sxs-lookup"><span data-stu-id="74710-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="74710-126">Zakodowana długość nie może być większa niż 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="74710-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="74710-127">Środowisko uruchomieniowe protobuf udostępnia typ `ByteString`, który umożliwia łatwe mapowanie do C# i z `byte[]` tablic.</span><span class="sxs-lookup"><span data-stu-id="74710-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="74710-128">Inne typy pierwotne platformy .NET</span><span class="sxs-lookup"><span data-stu-id="74710-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="74710-129">Daty i godziny</span><span class="sxs-lookup"><span data-stu-id="74710-129">Dates and times</span></span>

<span data-ttu-id="74710-130">Natywne typy skalarne nie zapewniają wartości daty i godziny, równoważne C#<xref:System.DateTimeOffset>, <xref:System.DateTime>i <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="74710-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="74710-131">Te typy można określić za pomocą niektórych rozszerzeń "dobrze znane typy" firmy Google.</span><span class="sxs-lookup"><span data-stu-id="74710-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="74710-132">Rozszerzenia te zapewniają obsługę generowania kodu i środowiska uruchomieniowego dla złożonych typów pól na obsługiwanych platformach.</span><span class="sxs-lookup"><span data-stu-id="74710-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span> 

<span data-ttu-id="74710-133">W poniższej tabeli przedstawiono typy daty i godziny:</span><span class="sxs-lookup"><span data-stu-id="74710-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="74710-134">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="74710-134">C# type</span></span> | <span data-ttu-id="74710-135">Nieznany typ protobuf</span><span class="sxs-lookup"><span data-stu-id="74710-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="74710-136">Wygenerowane właściwości w C# klasie nie są typami dat i godzin platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="74710-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="74710-137">Właściwości używają klas `Timestamp` i `Duration` w przestrzeni nazw `Google.Protobuf.WellKnownTypes`.</span><span class="sxs-lookup"><span data-stu-id="74710-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="74710-138">Klasy te zapewniają metody konwersji do i z `DateTimeOffset`, `DateTime`i `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="74710-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="74710-139">Typ `Timestamp` działa z czasem UTC.</span><span class="sxs-lookup"><span data-stu-id="74710-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="74710-140">wartości `DateTimeOffset` zawsze mają przesunięcie zero, a właściwość `DateTime.Kind` jest zawsze `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="74710-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="74710-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="74710-141">System.Guid</span></span>

<span data-ttu-id="74710-142">Protobuf nie obsługuje bezpośrednio typu <xref:System.Guid>, znanego jako `UUID` na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="74710-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="74710-143">Nie ma dobrze znanego typu.</span><span class="sxs-lookup"><span data-stu-id="74710-143">There's no well-known type for it.</span></span> 

<span data-ttu-id="74710-144">Najlepszym podejściem jest obsłużenie `Guid` wartości jako pola `string`, przy użyciu standardowego `8-4-4-4-12` formatu szesnastkowego (na przykład `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span><span class="sxs-lookup"><span data-stu-id="74710-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="74710-145">Wszystkie języki i platformy mogą przeanalizować ten format.</span><span class="sxs-lookup"><span data-stu-id="74710-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="74710-146">Nie używaj pola `bytes` do `Guid` wartości.</span><span class="sxs-lookup"><span data-stu-id="74710-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="74710-147">Problemy z *przydziałami* ([Definicja witryny Wikipedia](https://en.wikipedia.org/wiki/Endianness)) mogą spowodować błędne zachowanie, gdy protobuf się z innymi platformami, takimi jak Java.</span><span class="sxs-lookup"><span data-stu-id="74710-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="74710-148">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="74710-148">Nullable types</span></span>

<span data-ttu-id="74710-149">Generowanie kodu protobuf dla programu C# używa typów natywnych, takich jak `int` `int32`.</span><span class="sxs-lookup"><span data-stu-id="74710-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="74710-150">Dlatego wartości są zawsze uwzględniane i nie mogą mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="74710-150">So the values are always included and can't be null.</span></span> 

<span data-ttu-id="74710-151">Dla wartości, które wymagają jawnej wartości null, takich jak używanie C# `int?` w kodzie, protobuf "dobrze znane typy" obejmują otoki, które są kompilowane C# na typy dopuszczające wartości null.</span><span class="sxs-lookup"><span data-stu-id="74710-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="74710-152">Aby ich użyć, zaimportuj `wrappers.proto` do pliku `.proto`, tak jak to:</span><span class="sxs-lookup"><span data-stu-id="74710-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="74710-153">Protobuf będzie używać prostej `T?` (na przykład `int?`) dla wygenerowanej właściwości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="74710-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="74710-154">W poniższej tabeli przedstawiono pełną listę typów otoki o równoważnym C# typie:</span><span class="sxs-lookup"><span data-stu-id="74710-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="74710-155">C#Wprowadź</span><span class="sxs-lookup"><span data-stu-id="74710-155">C# type</span></span>   | <span data-ttu-id="74710-156">Otoka dobrze znanego typu</span><span class="sxs-lookup"><span data-stu-id="74710-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="74710-157">Dobrze znane typy `Timestamp` i `Duration` są reprezentowane w programie .NET jako klasy, więc nie ma potrzeby stosowania wersji dopuszczających wartość null.</span><span class="sxs-lookup"><span data-stu-id="74710-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="74710-158">Należy jednak pamiętać o wartości null we właściwościach tych typów podczas konwertowania na `DateTimeOffset` lub `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="74710-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="74710-159">Miejsca dziesiętne</span><span class="sxs-lookup"><span data-stu-id="74710-159">Decimals</span></span>

<span data-ttu-id="74710-160">Protobuf nie obsługuje natywnie typu `decimal` .NET, po prostu `double` i `float`.</span><span class="sxs-lookup"><span data-stu-id="74710-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="74710-161">W projekcie protobuf istnieje trwająca dyskusja dotycząca możliwości dodawania standardowego typu `Decimal` do dobrze znanych typów, z obsługą platformy dla języków i struktur, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="74710-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="74710-162">Nic nie zostało jeszcze zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="74710-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="74710-163">Można utworzyć definicję komunikatu reprezentującą typ `decimal`, który będzie działał do bezpiecznej serializacji między klientami i serwerami platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="74710-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="74710-164">Jednak deweloperzy na innych platformach będą musieli zrozumieć używany format i zaimplementować ich własny sposób obsługi.</span><span class="sxs-lookup"><span data-stu-id="74710-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="74710-165">Tworzenie niestandardowego typu dziesiętnego dla protobuf</span><span class="sxs-lookup"><span data-stu-id="74710-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="74710-166">Prosta implementacja może być podobna do niestandardowego typu `Money`, który jest używany przez niektóre interfejsy API usługi Google, bez pola `currency`.</span><span class="sxs-lookup"><span data-stu-id="74710-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="74710-167">Pole `nanos` reprezentuje wartości z `0.999_999_999` do `-0.999_999_999`.</span><span class="sxs-lookup"><span data-stu-id="74710-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="74710-168">Na przykład `decimal` wartość `1.5m` byłaby reprezentowana jako `{ units = 1, nanos = 500_000_000 }`.</span><span class="sxs-lookup"><span data-stu-id="74710-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="74710-169">To dlatego, że pole `nanos` w tym przykładzie używa typu `sfixed32`, który koduje bardziej wydajne niż `int32` dla większych wartości.</span><span class="sxs-lookup"><span data-stu-id="74710-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="74710-170">Jeśli pole `units` ma wartość ujemną, pole `nanos` powinno również być ujemne.</span><span class="sxs-lookup"><span data-stu-id="74710-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="74710-171">Istnieje wiele innych algorytmów kodowania `decimal` wartości jako ciągi bajtowe, ale ten komunikat jest łatwiejszy do zrozumienia niż którekolwiek z nich.</span><span class="sxs-lookup"><span data-stu-id="74710-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="74710-172">Nie ma to wpływ na wartości endian na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="74710-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="74710-173">Konwersję między tym typem i typem `decimal` BCL można zaimplementować w C# następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="74710-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="74710-174">Za każdym razem, gdy używasz niestandardowych typów komunikatów, takich jak ta, *musisz* udokumentować je za pomocą komentarzy w `.proto`.</span><span class="sxs-lookup"><span data-stu-id="74710-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="74710-175">Inni deweloperzy mogą następnie zaimplementować konwersję do i z równoważnego typu w własnym języku lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="74710-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="74710-176">[Poprzednie](protobuf-messages.md)
>[dalej](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="74710-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
