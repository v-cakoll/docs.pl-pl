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
# <a name="protobuf-scalar-data-types"></a>Typy danych skalarnych Protobuf

Bufor protokołu (Protobuf) obsługuje szereg natywnych typów wartości skalarnych. W poniższej tabeli wymieniono je wszystkie z ich równoważnym typem Języka C#:

| Typ protobuf | Typ C#      | Uwagi |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | 1     |
| `int64`       | `long`       | 1     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | 1     |
| `sint64`      | `long`       | 1     |
| `fixed32`     | `uint`       | 2     |
| `fixed64`     | `ulong`      | 2     |
| `sfixed32`    | `int`        | 2     |
| `sfixed64`    | `long`       | 2     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

Uwagi:

1. Standardowe kodowanie `int32` i `int64` jest nieefektywne podczas pracy z podpisanymi wartościami. Jeśli pole może zawierać liczby ujemne, użyj `sint32` go lub `sint64` zamiast tego. Te typy mapują `int` `long` odpowiednio do języka C# i typów.
2. Pola `fixed` zawsze używają tej samej liczby bajtów bez względu na wartość. To zachowanie sprawia, że serializacji i deserializacji szybciej dla większych wartości.
3. Ciągi protobuf są utf-8 (lub 7-bit ASCII) zakodowane. Zakodowana długość nie może być większa niż 2<sup>32</sup>.
4. Środowisko uruchomieniowe Protobuf zapewnia `ByteString` typ, który `byte[]` łatwo mapuje do i z tablic C#.

## <a name="other-net-primitive-types"></a>Inne typy pierwotne .NET

### <a name="dates-and-times"></a>Daty i godziny

Natywne typy skalarne nie zawierają wartości daty <xref:System.DateTimeOffset>i <xref:System.DateTime>godziny, równoważne wartościom C#, i <xref:System.TimeSpan>. Możesz określić te typy, korzystając z niektórych rozszerzeń Google "Dobrze znane typy". Rozszerzenia te zapewniają obsługę generowania kodu i środowiska uruchomieniowego dla złożonych typów pól na obsługiwanych platformach.

W poniższej tabeli przedstawiono typy dat i godzin:

| Typ C# | Protobuf dobrze znany typ |
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

Wygenerowane właściwości w klasie C# nie są typami daty i godziny .NET. Właściwości używają `Timestamp` i `Duration` klas w `Google.Protobuf.WellKnownTypes` obszarze nazw. Klasy te zapewniają metody konwersji `DateTimeOffset` `DateTime`do `TimeSpan`i z , i .

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
> Typ `Timestamp` działa z czasem UTC. `DateTimeOffset`wartości zawsze mają przesunięcie zero, `DateTime.Kind` a `DateTimeKind.Utc`właściwość jest zawsze .

### <a name="systemguid"></a>System.guid

Protobuf nie obsługuje bezpośrednio <xref:System.Guid> typu, znanego `UUID` jako na innych platformach. Nie ma dobrze znanego typu.

Najlepszym rozwiązaniem jest `Guid` obsługa wartości `string` jako pola, `8-4-4-4-12` przy użyciu standardowego formatu `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`szesnastkowego (na przykład ). Wszystkie języki i platformy mogą przeanalizować ten format.

Nie używaj `bytes` pola `Guid` dla wartości. Problemy z *endianness* [(definicja Wikipedii)](https://en.wikipedia.org/wiki/Endianness)może spowodować niekonsekwentne zachowanie, gdy Protobuf wchodzi w interakcje z innymi platformami, takimi jak Java.

### <a name="nullable-types"></a>Typy dopuszczające wartości null

Generowanie kodu Protobuf dla języka C# używa `int` `int32`typów natywnych, takich jak dla . Dlatego wartości są zawsze uwzględniane i nie mogą być null.

Dla wartości, które wymagają jawne null, takich jak przy użyciu `int?` w kodzie języka C#, Protobuf 's "Dobrze znane typy" obejmują otoki, które są kompilowane do nullable typów C#. Aby ich użyć, `wrappers.proto` `.proto` zaimportuj do pliku, w tym stylu:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf użyje `T?` prostego (na `int?`przykład) dla właściwości wygenerowanej wiadomości.

W poniższej tabeli przedstawiono pełną listę typów otoki z ich równoważnym typem języka C#:

| Typ C#   | Dobrze znana otoka typu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Dobrze znane `Timestamp` typy `Duration` i są reprezentowane w .NET jako klasy. W języku C# 8 i poza nią można użyć typów odwołań nullable. Ale ważne jest, aby sprawdzić wartość null na właściwości tych typów `DateTimeOffset` `TimeSpan`podczas konwersji do lub .

## <a name="decimals"></a>Miejsca dziesiętne

Protobuf nie obsługuje natywnie `decimal` typu `double` .NET, tylko i `float`. W projekcie Protobuf toczy się dyskusja na temat możliwości `Decimal` dodania standardowego typu do znanych typów, z obsługą platformy dla języków i struktur, które go obsługują. Nic nie zostało jeszcze wdrożone.

Istnieje możliwość utworzenia definicji wiadomości `decimal` do reprezentowania typu, który będzie działać dla bezpiecznej serializacji między klientami platformy .NET i serwerów. Ale deweloperzy na innych platformach musieliby zrozumieć używany format i wdrożyć dla niego własną obsługę.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Tworzenie niestandardowego typu dziesiętnego dla Protobuf

Prosta implementacja może być podobna `Money` do niestandardowego typu używanego `currency` przez niektóre interfejsy API Google bez tego pola.

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

Pole `nanos` reprezentuje wartości `0.999_999_999` `-0.999_999_999`od do . Na przykład `decimal` wartość `1.5m` będzie reprezentowana `{ units = 1, nanos = 500_000_000 }`jako . Dlatego `nanos` pole w tym przykładzie `sfixed32` używa typu, który koduje `int32` bardziej efektywnie niż w przypadku większych wartości. Jeśli `units` pole jest ujemne, `nanos` pole powinno być również ujemne.

> [!NOTE]
> Istnieje wiele innych algorytmów `decimal` kodowania wartości jako ciągi bajtów, ale ten komunikat jest łatwiejsze do zrozumienia niż którykolwiek z nich. Na wartości nie ma wpływu endianness na różnych platformach.

Konwersja między tym typem a typem listy BCL `decimal` może być zaimplementowana w języku C# w ten sposób:

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
> Za każdym razem, gdy używasz niestandardowych typów `.proto`wiadomości, takich jak ten, *należy udokumentować* je za pomocą komentarzy w pliku . Inni deweloperzy mogą następnie zaimplementować konwersji do i z równoważnego typu w ich własnym języku lub ramach.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-messages.md)
>[następny](protobuf-nested-types.md)
