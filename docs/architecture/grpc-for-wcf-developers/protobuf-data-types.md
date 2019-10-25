---
title: Protobuf typy danych skalarnych — gRPC dla deweloperów WCF
description: Dowiedz się więcej o podstawowych i dobrze znanych typach danych obsługiwanych przez protobuf i gRPC w programie .NET Core.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: cae9cc483ffb791a9b53e6a2d9d7c0924d725a67
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846351"
---
# <a name="protobuf-scalar-data-types"></a>Typy danych skalarnych Protobuf

Protobuf obsługuje zakres natywnych typów wartości skalarnych. W poniższej tabeli wymieniono wszystkie ich typy równoważne C# :

| Typ protobuf | C#Wprowadź      | Uwagi |
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

## <a name="notes"></a>Uwagi

1. Standardowe kodowanie dla `int32` i `int64` jest niewydajne podczas pracy z podpisanymi wartościami. Jeśli pole może zawierać liczby ujemne, zamiast tego użyj `sint32` lub `sint64`. Oba typy są C# mapowane odpowiednio do`int`i`long`.
2. Pola `fixed` zawsze używają tej samej liczby bajtów niezależnie od tego, co jest wartością. Takie zachowanie powoduje szybsze wykonywanie serializacji i deserializacji w przypadku większych wartości.
3. Ciągi protobuf są kodowane w UTF-8 (lub 7-bitowym formacie ASCII), a zakodowana długość nie może być większa niż 2<sup>32</sup>.
4. Środowisko uruchomieniowe protobuf udostępnia typ `ByteString`, który umożliwia łatwe mapowanie do C# i z`byte[]`tablic.

## <a name="other-net-primitive-types"></a>Inne typy pierwotne platformy .NET

### <a name="dates-and-times"></a>Daty i godziny

Natywne typy skalarne nie zapewniają wartości daty i godziny, równoważne C#<xref:System.DateTimeOffset>,<xref:System.DateTime>i<xref:System.TimeSpan>. Te typy można określić przy użyciu niektórych rozszerzeń "dobrze znane typy" firmy Google, które zapewniają obsługę generowania kodu i środowiska uruchomieniowego dla bardziej złożonych typów pól na obsługiwanych platformach. W poniższej tabeli przedstawiono typy daty i godziny:

| C#Wprowadź | Nieznany typ protobuf |
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

Wygenerowane właściwości w C# klasie nie są typami dat i godzin platformy .NET. Właściwości używają klas `Timestamp` i `Duration` w przestrzeni nazw `Google.Protobuf.WellKnownTypes`, które zapewniają metody konwersji do i z `DateTimeOffset`, `DateTime`i `TimeSpan`.

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
> Typ `Timestamp` działa z czasem UTC; wartości `DateTimeOffset` zawsze mają przesunięcie zero, a właściwość `DateTime.Kind` będzie zawsze `DateTimeKind.Utc`.

### <a name="systemguid"></a>System. GUID

Typ <xref:System.Guid>, znany jako `UUID` na innych platformach, nie jest bezpośrednio obsługiwany przez protobuf i nie ma dobrze znanego typu. Najlepszym podejściem jest obsłużenie `Guid` wartości jako pola `string` przy użyciu standardowego `8-4-4-4-12` formacie szesnastkowym (na przykład `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), który może być analizowany przez wszystkie języki i platformy. Nie używaj `bytes` pola do `Guid` wartości, ponieważ problemy z przypisaniami mogą spowodować błędne zachowanie podczas współpracy z innymi platformami, takimi jak Java.

### <a name="nullable-types"></a>Typy dopuszczające wartości null

Generowanie kodu protobuf dla programu C# używa typów natywnych, takich jak`int``int32`. Oznacza to, że wartości są zawsze uwzględniane i nie mogą mieć wartości null. Dla wartości, które wymagają jawnej wartości null, takich jak używanie C# `int?` w kodzie, protobuf "dobrze znane typy" obejmują otoki, które są kompilowane C# na typy dopuszczające wartości null. Aby ich użyć, zaimportuj `wrappers.proto` do pliku `.proto`, tak jak to:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf będzie używać prostej `T?` (na przykład `int?`) dla wygenerowanej właściwości wiadomości.

W poniższej tabeli przedstawiono pełną listę typów otoki o równoważnym C# typie:

| C#Wprowadź   | Otoka dobrze znanego typu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Dobrze znane typy `Timestamp` i `Duration` są reprezentowane w programie .NET jako klasy, więc nie ma potrzeby stosowania wersji dopuszczających wartości null, ale ważne jest, aby sprawdzić, czy właściwości tych typów są puste w przypadku konwertowania na `DateTimeOffset` lub `TimeSpan`.

## <a name="decimals"></a>miejsca dziesiętne

Protobuf nie obsługuje natywnie typu `decimal` .NET, po prostu `double` i `float`. W projekcie protobuf istnieje trwająca dyskusja dotycząca możliwości dodawania standardowego typu `Decimal` do dobrze znanych typów, z obsługą platformy dla języków i struktur, które go obsługują, ale nic nie zostało jeszcze zaimplementowane.

Istnieje możliwość utworzenia definicji komunikatu reprezentującej typ `decimal`, który będzie działał do bezpiecznej serializacji między klientami i serwerami platformy .NET, ale deweloperzy na innych platformach będą musieli zrozumieć używany format i wdrożyć własną obsługę dla niego.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Tworzenie niestandardowego typu dziesiętnego dla protobuf

Bardzo prosta implementacja może być podobna do niestandardowym typem `Money` używanym przez niektóre interfejsy API usługi Google, bez pola `currency`.

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

Pole `nanos` reprezentuje wartości z `0.999_999_999` do `-0.999_999_999`. Na przykład `decimal` wartość `1.5m` byłaby reprezentowana jako `{ units = 1, nanos = 500_000_000 }` (dlatego w polu `nanos` w tym przykładzie jest używany typ `sfixed32`, który koduje bardziej wydajny niż `int32` dla większych wartości). Jeśli pole `units` ma wartość ujemną, pole `nanos` powinno również być ujemne.

> [!NOTE]
> Istnieje wiele innych algorytmów kodowania `decimal` wartości jako ciągi bajtów, ale ten komunikat jest znacznie łatwiejszy do zrozumienia, a wartości nie *[wpływają na różne](https://en.wikipedia.org/wiki/Endianness)* platformy.

Konwersję między tym typem i typem `decimal` BCL można zaimplementować w C# taki sam sposób.

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
> Za każdym razem, gdy korzystasz z niestandardowych typów komunikatów narzędzi takich jak to, **musisz udokumentować** je za pomocą komentarzy w `.proto`, tak aby inni deweloperzy mogli zaimplementować konwersję do i z odpowiedniego typu w własnym języku lub strukturze.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-messages.md)
>[Następny](protobuf-nested-types.md)
