---
title: Typy danych skalarnych Protobuf - gRPC dla programistów WCF
description: Dowiedz się więcej o podstawowych i dobrze znanych typach danych obsługiwanych przez protobuf i gRPC w .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: a40f51fa32ddb97ba417ec01f31e1f0187f0d544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148130"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="4bca3-103">Typy danych skalarnych Protobuf</span><span class="sxs-lookup"><span data-stu-id="4bca3-103">Protobuf scalar data types</span></span>

<span data-ttu-id="4bca3-104">Bufor protokołu (Protobuf) obsługuje szereg typów wartości skalarnych natywnych.</span><span class="sxs-lookup"><span data-stu-id="4bca3-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="4bca3-105">W poniższej tabeli wymieniono wszystkie z ich równoważnym typem Języka C#:</span><span class="sxs-lookup"><span data-stu-id="4bca3-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="4bca3-106">Typ Protobuf</span><span class="sxs-lookup"><span data-stu-id="4bca3-106">Protobuf type</span></span> | <span data-ttu-id="4bca3-107">Typ języka C#</span><span class="sxs-lookup"><span data-stu-id="4bca3-107">C# type</span></span>      | <span data-ttu-id="4bca3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bca3-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="4bca3-109">1</span><span class="sxs-lookup"><span data-stu-id="4bca3-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="4bca3-110">1</span><span class="sxs-lookup"><span data-stu-id="4bca3-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="4bca3-111">1</span><span class="sxs-lookup"><span data-stu-id="4bca3-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="4bca3-112">1</span><span class="sxs-lookup"><span data-stu-id="4bca3-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="4bca3-113">2</span><span class="sxs-lookup"><span data-stu-id="4bca3-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="4bca3-114">2</span><span class="sxs-lookup"><span data-stu-id="4bca3-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="4bca3-115">2</span><span class="sxs-lookup"><span data-stu-id="4bca3-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="4bca3-116">2</span><span class="sxs-lookup"><span data-stu-id="4bca3-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="4bca3-117">3</span><span class="sxs-lookup"><span data-stu-id="4bca3-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="4bca3-118">4</span><span class="sxs-lookup"><span data-stu-id="4bca3-118">4</span></span>     |

<span data-ttu-id="4bca3-119">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="4bca3-119">Notes:</span></span>

1. <span data-ttu-id="4bca3-120">Standardowe kodowanie `int32` dla `int64` i jest nieefektywne podczas pracy z podpisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="4bca3-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="4bca3-121">Jeśli pole może zawierać liczby ujemne, użyj `sint32` lub `sint64` zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="4bca3-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="4bca3-122">Te typy map do `int` `long` C# i typów, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4bca3-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="4bca3-123">Pola `fixed` zawsze używają tej samej liczby bajtów bez względu na wartość.</span><span class="sxs-lookup"><span data-stu-id="4bca3-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="4bca3-124">To zachowanie sprawia, że serializacja i deserializacja szybciej dla większych wartości.</span><span class="sxs-lookup"><span data-stu-id="4bca3-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="4bca3-125">Ciągi Protobuf są zakodowane uTF-8 (lub 7-bitowy ASCII).</span><span class="sxs-lookup"><span data-stu-id="4bca3-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="4bca3-126">Zakodowana długość nie może być większa niż 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="4bca3-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="4bca3-127">Protobuf runtime zapewnia `ByteString` typ, który mapuje `byte[]` łatwo do iz tablic C#.</span><span class="sxs-lookup"><span data-stu-id="4bca3-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="4bca3-128">Inne typy pierwotne .NET</span><span class="sxs-lookup"><span data-stu-id="4bca3-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="4bca3-129">Daty i godziny</span><span class="sxs-lookup"><span data-stu-id="4bca3-129">Dates and times</span></span>

<span data-ttu-id="4bca3-130">Typy natywnych skalarnych nie zapewniają wartości daty i <xref:System.DateTimeOffset>godziny, równoważne c#' , <xref:System.DateTime>i <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="4bca3-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="4bca3-131">Możesz określić te typy, korzystając z niektórych rozszerzeń Google "Dobrze znane typy".</span><span class="sxs-lookup"><span data-stu-id="4bca3-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="4bca3-132">Te rozszerzenia zapewniają generowanie kodu i obsługę w czasie wykonywania dla złożonych typów pól na obsługiwanych platformach.</span><span class="sxs-lookup"><span data-stu-id="4bca3-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="4bca3-133">W poniższej tabeli przedstawiono typy daty i godziny:</span><span class="sxs-lookup"><span data-stu-id="4bca3-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="4bca3-134">Typ języka C#</span><span class="sxs-lookup"><span data-stu-id="4bca3-134">C# type</span></span> | <span data-ttu-id="4bca3-135">Protobuf dobrze znany typ</span><span class="sxs-lookup"><span data-stu-id="4bca3-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="4bca3-136">Wygenerowane właściwości w klasie C# nie są typami daty i godziny .NET.</span><span class="sxs-lookup"><span data-stu-id="4bca3-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="4bca3-137">Właściwości używają `Timestamp` i `Duration` klas w `Google.Protobuf.WellKnownTypes` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4bca3-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="4bca3-138">Klasy te zapewniają metody konwersji do `DateTimeOffset` `DateTime`iz `TimeSpan`, i .</span><span class="sxs-lookup"><span data-stu-id="4bca3-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="4bca3-139">Typ `Timestamp` działa z czasem UTC.</span><span class="sxs-lookup"><span data-stu-id="4bca3-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="4bca3-140">`DateTimeOffset`wartości zawsze mają przesunięcie zero, `DateTime.Kind` a `DateTimeKind.Utc`właściwość jest zawsze .</span><span class="sxs-lookup"><span data-stu-id="4bca3-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="4bca3-141">System.guid</span><span class="sxs-lookup"><span data-stu-id="4bca3-141">System.Guid</span></span>

<span data-ttu-id="4bca3-142">Protobuf nie obsługuje bezpośrednio <xref:System.Guid> tego typu, znanego jako `UUID` na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="4bca3-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="4bca3-143">Nie ma dla niego znanego typu.</span><span class="sxs-lookup"><span data-stu-id="4bca3-143">There's no well-known type for it.</span></span>

<span data-ttu-id="4bca3-144">Najlepszym rozwiązaniem jest `Guid` obsługa wartości `string` jako pola przy `8-4-4-4-12` użyciu standardowego formatu szesnastkowego (na `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`przykład).</span><span class="sxs-lookup"><span data-stu-id="4bca3-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="4bca3-145">Wszystkie języki i platformy mogą analizować ten format.</span><span class="sxs-lookup"><span data-stu-id="4bca3-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="4bca3-146">Nie używaj `bytes` pola `Guid` dla wartości.</span><span class="sxs-lookup"><span data-stu-id="4bca3-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="4bca3-147">Problemy z *endianness* [(definicja Wikipedii](https://en.wikipedia.org/wiki/Endianness)) może spowodować niekonsekwentne zachowanie, gdy Protobuf wchodzi w interakcje z innymi platformami, takimi jak Java.</span><span class="sxs-lookup"><span data-stu-id="4bca3-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="4bca3-148">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="4bca3-148">Nullable types</span></span>

<span data-ttu-id="4bca3-149">Generowanie kodu Protobuf dla języka C# `int` używa `int32`typów natywnych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="4bca3-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="4bca3-150">Tak więc wartości są zawsze uwzględniane i nie mogą być null.</span><span class="sxs-lookup"><span data-stu-id="4bca3-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="4bca3-151">Dla wartości, które wymagają jawnego wartości null, takich jak przy użyciu `int?` w kodzie C# Protobuf "Dobrze znane typy" obejmują otoki, które są kompilowane do typów c# null.</span><span class="sxs-lookup"><span data-stu-id="4bca3-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="4bca3-152">Aby z nich `wrappers.proto` korzystać, zaimportuj do pliku `.proto` w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="4bca3-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="4bca3-153">Protobuf użyje `T?` prostego (na `int?`przykład) dla wygenerowanej właściwości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4bca3-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="4bca3-154">W poniższej tabeli przedstawiono pełną listę typów otoki z ich odpowiednikiem typu C#:</span><span class="sxs-lookup"><span data-stu-id="4bca3-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="4bca3-155">Typ języka C#</span><span class="sxs-lookup"><span data-stu-id="4bca3-155">C# type</span></span>   | <span data-ttu-id="4bca3-156">Otoka dobrze znanego typu</span><span class="sxs-lookup"><span data-stu-id="4bca3-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="4bca3-157">Dobrze znane typy `Timestamp` `Duration` i są reprezentowane w .NET jako klasy, więc nie ma potrzeby wersji nullable.</span><span class="sxs-lookup"><span data-stu-id="4bca3-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="4bca3-158">Ale ważne jest, aby sprawdzić wartość null na właściwości tych typów `DateTimeOffset` `TimeSpan`podczas konwersji do lub .</span><span class="sxs-lookup"><span data-stu-id="4bca3-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="4bca3-159">Miejsca dziesiętne</span><span class="sxs-lookup"><span data-stu-id="4bca3-159">Decimals</span></span>

<span data-ttu-id="4bca3-160">Protobuf nie obsługuje natywnie `decimal` typu `double` .NET, tylko i `float`.</span><span class="sxs-lookup"><span data-stu-id="4bca3-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="4bca3-161">W projekcie Protobuf toczy się dyskusja na temat `Decimal` możliwości dodania standardowego typu do znanych typów, z obsługą platform y dla języków i struktur, które go obsługują.</span><span class="sxs-lookup"><span data-stu-id="4bca3-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="4bca3-162">Nic nie zostało jeszcze wdrożone.</span><span class="sxs-lookup"><span data-stu-id="4bca3-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="4bca3-163">Możliwe jest utworzenie definicji wiadomości reprezentującej `decimal` typ, który będzie działał dla bezpiecznej serializacji między klientami .NET a serwerami.</span><span class="sxs-lookup"><span data-stu-id="4bca3-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="4bca3-164">Ale deweloperzy na innych platformach musieliby zrozumieć format używany i zaimplementować własną obsługę dla niego.</span><span class="sxs-lookup"><span data-stu-id="4bca3-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="4bca3-165">Tworzenie niestandardowego typu dziesiętnego dla protobufu</span><span class="sxs-lookup"><span data-stu-id="4bca3-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="4bca3-166">Prosta implementacja może być podobna `Money` do niestandardowego typu używanego `currency` przez niektóre interfejsy API Google bez tego pola.</span><span class="sxs-lookup"><span data-stu-id="4bca3-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="4bca3-167">To `nanos` pole reprezentuje `0.999_999_999` wartości `-0.999_999_999`od .</span><span class="sxs-lookup"><span data-stu-id="4bca3-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="4bca3-168">Na przykład `decimal` wartość `1.5m` będzie reprezentowana `{ units = 1, nanos = 500_000_000 }`jako .</span><span class="sxs-lookup"><span data-stu-id="4bca3-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="4bca3-169">Dlatego pole `nanos` w tym przykładzie `sfixed32` używa typu, który koduje `int32` bardziej efektywnie niż dla większych wartości.</span><span class="sxs-lookup"><span data-stu-id="4bca3-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="4bca3-170">Jeśli `units` pole jest ujemne, `nanos` pole powinno być również ujemne.</span><span class="sxs-lookup"><span data-stu-id="4bca3-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="4bca3-171">Istnieje wiele innych algorytmów `decimal` kodowania wartości jako ciągi bajtów, ale ten komunikat jest łatwiejsze do zrozumienia niż którykolwiek z nich.</span><span class="sxs-lookup"><span data-stu-id="4bca3-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="4bca3-172">Wartości nie mają wpływu endianness na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="4bca3-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="4bca3-173">Konwersja między tym typem a typem BCL `decimal` może być zaimplementowana w języku C# w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="4bca3-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="4bca3-174">Za każdym razem, gdy używasz niestandardowych typów wiadomości, takich jak ten, *należy udokumentować* je z komentarzami w `.proto`.</span><span class="sxs-lookup"><span data-stu-id="4bca3-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="4bca3-175">Inni deweloperzy mogą następnie zaimplementować konwersję do i z równoważnego typu w ich własnym języku lub ramach.</span><span class="sxs-lookup"><span data-stu-id="4bca3-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4bca3-176">[Poprzedni](protobuf-messages.md)
>[następny](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="4bca3-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
