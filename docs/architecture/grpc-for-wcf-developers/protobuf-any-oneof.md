---
title: Protobuf wszystkie pola i oneof dla typów wariantów — gRPC dla deweloperów WCF
description: Dowiedz się, jak używać dowolnego typu i słowa kluczowego oneof do reprezentowania typów obiektów Variant w komunikatach.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184282"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf wszystkie pola i oneof dla typów wariantów

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Obsługa typów właściwości dynamicznych (czyli właściwości typu `object`) w programie WCF jest skomplikowana. Należy określić serializatory, należy podać atrybuty [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) i tak dalej.

Protobuf udostępnia dwie prostsze opcje do pracy z wartościami, które mogą mieć więcej niż jeden typ. Typ może reprezentować dowolny znany typ komunikatu protobuf, `oneof` podczas gdy słowo kluczowe pozwala określić, że tylko jeden z zakresów pól może być ustawiony w danym komunikacie. `Any`

## <a name="any"></a>Any

`Any`jest jednym z "dobrze znanych typów protobuf": Kolekcja przydatnych typów wiadomości wielokrotnego użytku z implementacjami we wszystkich obsługiwanych językach. Aby użyć tego `Any` typu, należy `google/protobuf/any.proto` zaimportować definicję.

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

W C# kodzie `Any` Klasa zawiera metody służące do ustawiania pola, wyodrębniania komunikatu i sprawdzania typu.

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

Pole statyczne w każdym wygenerowanym typie jest używane przez wewnętrzny kod odbicia protobuf w `Any` celu rozpoznania typów pól. `Descriptor` Istnieje również `TryUnpack<T>` Metoda, ale która tworzy niezainicjowane `T` wystąpienie nawet wtedy, gdy nie powiedzie się, więc lepiej jest użyć `Is` metody, jak pokazano powyżej.

## <a name="oneof"></a>Oneof

Pola oneof są funkcją języka: `oneof` słowo kluczowe jest obsługiwane przez kompilator podczas generowania klasy komunikatów. Użycie `oneof` do`ChangeNotification` określenia komunikatu może wyglądać następująco:

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

Pola w `oneof` zestawie muszą mieć unikatowe numery pól w całej deklaracji komunikatu.

Gdy używasz `oneof`, wygenerowany C# kod zawiera wyliczenie, które określa, które z pól zostały ustawione. Możesz przetestować Wyliczenie, aby znaleźć pole, które zostało ustawione. Pola, które nie ustawiają `null` wartości zwracanej lub domyślnej, zamiast zgłaszać wyjątek.

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

Ustawienie dowolnego pola, które jest częścią `oneof` zestawu, spowoduje automatyczne wyczyszczenie innych pól w zestawie. Nie można używać `repeated` z `oneof`. Zamiast tego można utworzyć zagnieżdżony komunikat z powtarzającym się polem lub `oneof` zestawem, aby obejść to ograniczenie.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-reserved.md)
>[Następny](protobuf-enums.md)
