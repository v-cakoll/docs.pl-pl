---
title: Typy danych protobuf skalarnych - gRPC dla programistów WCF
description: Dowiedz się więcej o podstawowych i dobrze znanych typach danych obsługiwanych przez Protobuf i gRPC w .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: ea3b53426ecf6f50f3bae22a537e227b07248508
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249438"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="b30b4-103">Typy danych skalarnych Protobuf</span><span class="sxs-lookup"><span data-stu-id="b30b4-103">Protobuf scalar data types</span></span>

<span data-ttu-id="b30b4-104">Bufor protokołu (Protobuf) obsługuje szereg natywnych typów wartości skalarnych.</span><span class="sxs-lookup"><span data-stu-id="b30b4-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="b30b4-105">W poniższej tabeli wymieniono je wszystkie z ich równoważnym typem Języka C#:</span><span class="sxs-lookup"><span data-stu-id="b30b4-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="b30b4-106">Typ protobuf</span><span class="sxs-lookup"><span data-stu-id="b30b4-106">Protobuf type</span></span> | <span data-ttu-id="b30b4-107">Typ C#</span><span class="sxs-lookup"><span data-stu-id="b30b4-107">C# type</span></span>      | <span data-ttu-id="b30b4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b30b4-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="b30b4-109">1</span><span class="sxs-lookup"><span data-stu-id="b30b4-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="b30b4-110">1</span><span class="sxs-lookup"><span data-stu-id="b30b4-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="b30b4-111">1</span><span class="sxs-lookup"><span data-stu-id="b30b4-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="b30b4-112">1</span><span class="sxs-lookup"><span data-stu-id="b30b4-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="b30b4-113">2</span><span class="sxs-lookup"><span data-stu-id="b30b4-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="b30b4-114">2</span><span class="sxs-lookup"><span data-stu-id="b30b4-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="b30b4-115">2</span><span class="sxs-lookup"><span data-stu-id="b30b4-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="b30b4-116">2</span><span class="sxs-lookup"><span data-stu-id="b30b4-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="b30b4-117">3</span><span class="sxs-lookup"><span data-stu-id="b30b4-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="b30b4-118">4</span><span class="sxs-lookup"><span data-stu-id="b30b4-118">4</span></span>     |

<span data-ttu-id="b30b4-119">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="b30b4-119">Notes:</span></span>

1. <span data-ttu-id="b30b4-120">Standardowe kodowanie `int32` i `int64` jest nieefektywne podczas pracy z podpisanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="b30b4-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="b30b4-121">Jeśli pole może zawierać liczby ujemne, użyj `sint32` go lub `sint64` zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b30b4-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="b30b4-122">Te typy mapują `int` `long` odpowiednio do języka C# i typów.</span><span class="sxs-lookup"><span data-stu-id="b30b4-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="b30b4-123">Pola `fixed` zawsze używają tej samej liczby bajtów bez względu na wartość.</span><span class="sxs-lookup"><span data-stu-id="b30b4-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="b30b4-124">To zachowanie sprawia, że serializacji i deserializacji szybciej dla większych wartości.</span><span class="sxs-lookup"><span data-stu-id="b30b4-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="b30b4-125">Ciągi protobuf są utf-8 (lub 7-bit ASCII) zakodowane.</span><span class="sxs-lookup"><span data-stu-id="b30b4-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="b30b4-126">Zakodowana długość nie może być większa niż 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="b30b4-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="b30b4-127">Środowisko uruchomieniowe Protobuf zapewnia `ByteString` typ, który `byte[]` łatwo mapuje do i z tablic C#.</span><span class="sxs-lookup"><span data-stu-id="b30b4-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="b30b4-128">Inne typy pierwotne .NET</span><span class="sxs-lookup"><span data-stu-id="b30b4-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="b30b4-129">Daty i godziny</span><span class="sxs-lookup"><span data-stu-id="b30b4-129">Dates and times</span></span>

<span data-ttu-id="b30b4-130">Natywne typy skalarne nie zawierają wartości daty <xref:System.DateTimeOffset>i <xref:System.DateTime>godziny, równoważne wartościom C#, i <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="b30b4-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="b30b4-131">Możesz określić te typy, korzystając z niektórych rozszerzeń Google "Dobrze znane typy".</span><span class="sxs-lookup"><span data-stu-id="b30b4-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="b30b4-132">Rozszerzenia te zapewniają obsługę generowania kodu i środowiska uruchomieniowego dla złożonych typów pól na obsługiwanych platformach.</span><span class="sxs-lookup"><span data-stu-id="b30b4-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="b30b4-133">W poniższej tabeli przedstawiono typy dat i godzin:</span><span class="sxs-lookup"><span data-stu-id="b30b4-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="b30b4-134">Typ C#</span><span class="sxs-lookup"><span data-stu-id="b30b4-134">C# type</span></span> | <span data-ttu-id="b30b4-135">Protobuf dobrze znany typ</span><span class="sxs-lookup"><span data-stu-id="b30b4-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="b30b4-136">Wygenerowane właściwości w klasie C# nie są typami daty i godziny .NET.</span><span class="sxs-lookup"><span data-stu-id="b30b4-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="b30b4-137">Właściwości używają `Timestamp` i `Duration` klas w `Google.Protobuf.WellKnownTypes` obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="b30b4-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="b30b4-138">Klasy te zapewniają metody konwersji `DateTimeOffset` `DateTime`do `TimeSpan`i z , i .</span><span class="sxs-lookup"><span data-stu-id="b30b4-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="b30b4-139">Typ `Timestamp` działa z czasem UTC.</span><span class="sxs-lookup"><span data-stu-id="b30b4-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="b30b4-140">`DateTimeOffset`wartości zawsze mają przesunięcie zero, `DateTime.Kind` a `DateTimeKind.Utc`właściwość jest zawsze .</span><span class="sxs-lookup"><span data-stu-id="b30b4-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="b30b4-141">System.guid</span><span class="sxs-lookup"><span data-stu-id="b30b4-141">System.Guid</span></span>

<span data-ttu-id="b30b4-142">Protobuf nie obsługuje bezpośrednio <xref:System.Guid> typu, znanego `UUID` jako na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="b30b4-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="b30b4-143">Nie ma dobrze znanego typu.</span><span class="sxs-lookup"><span data-stu-id="b30b4-143">There's no well-known type for it.</span></span>

<span data-ttu-id="b30b4-144">Najlepszym rozwiązaniem jest `Guid` obsługa wartości `string` jako pola, `8-4-4-4-12` przy użyciu standardowego formatu `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`szesnastkowego (na przykład ).</span><span class="sxs-lookup"><span data-stu-id="b30b4-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="b30b4-145">Wszystkie języki i platformy mogą przeanalizować ten format.</span><span class="sxs-lookup"><span data-stu-id="b30b4-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="b30b4-146">Nie używaj `bytes` pola `Guid` dla wartości.</span><span class="sxs-lookup"><span data-stu-id="b30b4-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="b30b4-147">Problemy z *endianness* [(definicja Wikipedii)](https://en.wikipedia.org/wiki/Endianness)może spowodować niekonsekwentne zachowanie, gdy Protobuf wchodzi w interakcje z innymi platformami, takimi jak Java.</span><span class="sxs-lookup"><span data-stu-id="b30b4-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="b30b4-148">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="b30b4-148">Nullable types</span></span>

<span data-ttu-id="b30b4-149">Generowanie kodu Protobuf dla języka C# używa `int` `int32`typów natywnych, takich jak dla .</span><span class="sxs-lookup"><span data-stu-id="b30b4-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="b30b4-150">Dlatego wartości są zawsze uwzględniane i nie mogą być null.</span><span class="sxs-lookup"><span data-stu-id="b30b4-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="b30b4-151">Dla wartości, które wymagają jawne null, takich jak przy użyciu `int?` w kodzie języka C#, Protobuf 's "Dobrze znane typy" obejmują otoki, które są kompilowane do nullable typów C#.</span><span class="sxs-lookup"><span data-stu-id="b30b4-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="b30b4-152">Aby ich użyć, `wrappers.proto` `.proto` zaimportuj do pliku, w tym stylu:</span><span class="sxs-lookup"><span data-stu-id="b30b4-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="b30b4-153">Protobuf użyje `T?` prostego (na `int?`przykład) dla właściwości wygenerowanej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b30b4-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="b30b4-154">W poniższej tabeli przedstawiono pełną listę typów otoki z ich równoważnym typem języka C#:</span><span class="sxs-lookup"><span data-stu-id="b30b4-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="b30b4-155">Typ C#</span><span class="sxs-lookup"><span data-stu-id="b30b4-155">C# type</span></span>   | <span data-ttu-id="b30b4-156">Dobrze znana otoka typu</span><span class="sxs-lookup"><span data-stu-id="b30b4-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="b30b4-157">Dobrze znane `Timestamp` typy `Duration` i są reprezentowane w .NET jako klasy.</span><span class="sxs-lookup"><span data-stu-id="b30b4-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="b30b4-158">W języku C# 8 i poza nią można użyć typów odwołań nullable.</span><span class="sxs-lookup"><span data-stu-id="b30b4-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="b30b4-159">Ale ważne jest, aby sprawdzić wartość null na właściwości tych typów `DateTimeOffset` `TimeSpan`podczas konwersji do lub .</span><span class="sxs-lookup"><span data-stu-id="b30b4-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="b30b4-160">Miejsca dziesiętne</span><span class="sxs-lookup"><span data-stu-id="b30b4-160">Decimals</span></span>

<span data-ttu-id="b30b4-161">Protobuf nie obsługuje natywnie `decimal` typu `double` .NET, tylko i `float`.</span><span class="sxs-lookup"><span data-stu-id="b30b4-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="b30b4-162">W projekcie Protobuf toczy się dyskusja na temat możliwości `Decimal` dodania standardowego typu do znanych typów, z obsługą platformy dla języków i struktur, które go obsługują.</span><span class="sxs-lookup"><span data-stu-id="b30b4-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="b30b4-163">Nic nie zostało jeszcze wdrożone.</span><span class="sxs-lookup"><span data-stu-id="b30b4-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="b30b4-164">Istnieje możliwość utworzenia definicji wiadomości `decimal` do reprezentowania typu, który będzie działać dla bezpiecznej serializacji między klientami platformy .NET i serwerów.</span><span class="sxs-lookup"><span data-stu-id="b30b4-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="b30b4-165">Ale deweloperzy na innych platformach musieliby zrozumieć używany format i wdrożyć dla niego własną obsługę.</span><span class="sxs-lookup"><span data-stu-id="b30b4-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="b30b4-166">Tworzenie niestandardowego typu dziesiętnego dla Protobuf</span><span class="sxs-lookup"><span data-stu-id="b30b4-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="b30b4-167">Prosta implementacja może być podobna `Money` do niestandardowego typu używanego `currency` przez niektóre interfejsy API Google bez tego pola.</span><span class="sxs-lookup"><span data-stu-id="b30b4-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="b30b4-168">Pole `nanos` reprezentuje wartości `0.999_999_999` `-0.999_999_999`od do .</span><span class="sxs-lookup"><span data-stu-id="b30b4-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="b30b4-169">Na przykład `decimal` wartość `1.5m` będzie reprezentowana `{ units = 1, nanos = 500_000_000 }`jako .</span><span class="sxs-lookup"><span data-stu-id="b30b4-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="b30b4-170">Dlatego `nanos` pole w tym przykładzie `sfixed32` używa typu, który koduje `int32` bardziej efektywnie niż w przypadku większych wartości.</span><span class="sxs-lookup"><span data-stu-id="b30b4-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="b30b4-171">Jeśli `units` pole jest ujemne, `nanos` pole powinno być również ujemne.</span><span class="sxs-lookup"><span data-stu-id="b30b4-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="b30b4-172">Istnieje wiele innych algorytmów `decimal` kodowania wartości jako ciągi bajtów, ale ten komunikat jest łatwiejsze do zrozumienia niż którykolwiek z nich.</span><span class="sxs-lookup"><span data-stu-id="b30b4-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="b30b4-173">Na wartości nie ma wpływu endianness na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="b30b4-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="b30b4-174">Konwersja między tym typem a typem listy BCL `decimal` może być zaimplementowana w języku C# w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="b30b4-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="b30b4-175">Za każdym razem, gdy używasz niestandardowych typów `.proto`wiadomości, takich jak ten, *należy udokumentować* je za pomocą komentarzy w pliku .</span><span class="sxs-lookup"><span data-stu-id="b30b4-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="b30b4-176">Inni deweloperzy mogą następnie zaimplementować konwersji do i z równoważnego typu w ich własnym języku lub ramach.</span><span class="sxs-lookup"><span data-stu-id="b30b4-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b30b4-177">[Poprzedni](protobuf-messages.md)
>[następny](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="b30b4-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
