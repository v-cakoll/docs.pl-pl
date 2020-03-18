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
# <a name="protobuf-scalar-data-types"></a>Typy danych skalarnych Protobuf

Bufor protokołu (Protobuf) obsługuje szereg typów wartości skalarnych natywnych. W poniższej tabeli wymieniono wszystkie z ich równoważnym typem Języka C#:

| Typ Protobuf | Typ języka C#      | Uwagi |
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

1. Standardowe kodowanie `int32` dla `int64` i jest nieefektywne podczas pracy z podpisanymi wartościami. Jeśli pole może zawierać liczby ujemne, użyj `sint32` lub `sint64` zamiast tego. Te typy map do `int` `long` C# i typów, odpowiednio.
2. Pola `fixed` zawsze używają tej samej liczby bajtów bez względu na wartość. To zachowanie sprawia, że serializacja i deserializacja szybciej dla większych wartości.
3. Ciągi Protobuf są zakodowane uTF-8 (lub 7-bitowy ASCII). Zakodowana długość nie może być większa niż 2<sup>32</sup>.
4. Protobuf runtime zapewnia `ByteString` typ, który mapuje `byte[]` łatwo do iz tablic C#.

## <a name="other-net-primitive-types"></a>Inne typy pierwotne .NET

### <a name="dates-and-times"></a>Daty i godziny

Typy natywnych skalarnych nie zapewniają wartości daty i <xref:System.DateTimeOffset>godziny, równoważne c#' , <xref:System.DateTime>i <xref:System.TimeSpan>. Możesz określić te typy, korzystając z niektórych rozszerzeń Google "Dobrze znane typy". Te rozszerzenia zapewniają generowanie kodu i obsługę w czasie wykonywania dla złożonych typów pól na obsługiwanych platformach.

W poniższej tabeli przedstawiono typy daty i godziny:

| Typ języka C# | Protobuf dobrze znany typ |
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

Wygenerowane właściwości w klasie C# nie są typami daty i godziny .NET. Właściwości używają `Timestamp` i `Duration` klas w `Google.Protobuf.WellKnownTypes` przestrzeni nazw. Klasy te zapewniają metody konwersji do `DateTimeOffset` `DateTime`iz `TimeSpan`, i .

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

Protobuf nie obsługuje bezpośrednio <xref:System.Guid> tego typu, znanego jako `UUID` na innych platformach. Nie ma dla niego znanego typu.

Najlepszym rozwiązaniem jest `Guid` obsługa wartości `string` jako pola przy `8-4-4-4-12` użyciu standardowego formatu szesnastkowego (na `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`przykład). Wszystkie języki i platformy mogą analizować ten format.

Nie używaj `bytes` pola `Guid` dla wartości. Problemy z *endianness* [(definicja Wikipedii](https://en.wikipedia.org/wiki/Endianness)) może spowodować niekonsekwentne zachowanie, gdy Protobuf wchodzi w interakcje z innymi platformami, takimi jak Java.

### <a name="nullable-types"></a>Typy dopuszczające wartości null

Generowanie kodu Protobuf dla języka C# `int` używa `int32`typów natywnych, takich jak . Tak więc wartości są zawsze uwzględniane i nie mogą być null.

Dla wartości, które wymagają jawnego wartości null, takich jak przy użyciu `int?` w kodzie C# Protobuf "Dobrze znane typy" obejmują otoki, które są kompilowane do typów c# null. Aby z nich `wrappers.proto` korzystać, zaimportuj do pliku `.proto` w ten sposób:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf użyje `T?` prostego (na `int?`przykład) dla wygenerowanej właściwości wiadomości.

W poniższej tabeli przedstawiono pełną listę typów otoki z ich odpowiednikiem typu C#:

| Typ języka C#   | Otoka dobrze znanego typu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Dobrze znane typy `Timestamp` `Duration` i są reprezentowane w .NET jako klasy, więc nie ma potrzeby wersji nullable. Ale ważne jest, aby sprawdzić wartość null na właściwości tych typów `DateTimeOffset` `TimeSpan`podczas konwersji do lub .

## <a name="decimals"></a>Miejsca dziesiętne

Protobuf nie obsługuje natywnie `decimal` typu `double` .NET, tylko i `float`. W projekcie Protobuf toczy się dyskusja na temat `Decimal` możliwości dodania standardowego typu do znanych typów, z obsługą platform y dla języków i struktur, które go obsługują. Nic nie zostało jeszcze wdrożone.

Możliwe jest utworzenie definicji wiadomości reprezentującej `decimal` typ, który będzie działał dla bezpiecznej serializacji między klientami .NET a serwerami. Ale deweloperzy na innych platformach musieliby zrozumieć format używany i zaimplementować własną obsługę dla niego.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Tworzenie niestandardowego typu dziesiętnego dla protobufu

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

To `nanos` pole reprezentuje `0.999_999_999` wartości `-0.999_999_999`od . Na przykład `decimal` wartość `1.5m` będzie reprezentowana `{ units = 1, nanos = 500_000_000 }`jako . Dlatego pole `nanos` w tym przykładzie `sfixed32` używa typu, który koduje `int32` bardziej efektywnie niż dla większych wartości. Jeśli `units` pole jest ujemne, `nanos` pole powinno być również ujemne.

> [!NOTE]
> Istnieje wiele innych algorytmów `decimal` kodowania wartości jako ciągi bajtów, ale ten komunikat jest łatwiejsze do zrozumienia niż którykolwiek z nich. Wartości nie mają wpływu endianness na różnych platformach.

Konwersja między tym typem a typem BCL `decimal` może być zaimplementowana w języku C# w ten sposób:

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
> Za każdym razem, gdy używasz niestandardowych typów wiadomości, takich jak ten, *należy udokumentować* je z komentarzami w `.proto`. Inni deweloperzy mogą następnie zaimplementować konwersję do i z równoważnego typu w ich własnym języku lub ramach.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-messages.md)
>[następny](protobuf-nested-types.md)
