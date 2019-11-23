---
title: Protobuf wszystkie pola i oneof dla typów wariantów — gRPC dla deweloperów WCF
description: Dowiedz się, jak używać dowolnego typu i słowa kluczowego oneof do reprezentowania typów obiektów Variant w komunikatach.
ms.date: 09/09/2019
ms.openlocfilehash: af3ba22c238aa80a8c6119f62d5d8914770cad68
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971616"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf wszystkie pola i oneof dla typów wariantów

Obsługa typów właściwości dynamicznych (czyli właściwości typu `object`) w programie WCF jest skomplikowana. Należy określić serializatory, należy podać atrybuty [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) i tak dalej.

Protobuf udostępnia dwie prostsze opcje do pracy z wartościami, które mogą mieć więcej niż jeden typ. Typ `Any` może reprezentować dowolny znany typ komunikatu protobuf, podczas gdy słowo kluczowe `oneof` pozwala określić, że tylko jeden z zakresów pól można ustawić w danym komunikacie.

## <a name="any"></a>Dowolne

`Any` to jeden z "dobrze znanych typów protobuf": Kolekcja przydatnych typów wiadomości wielokrotnego użytku z implementacjami we wszystkich obsługiwanych językach. Aby użyć typu `Any`, należy zaimportować definicję `google/protobuf/any.proto`.

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

W C# kodzie Klasa `Any` dostarcza metody służące do ustawiania pola, wyodrębniania komunikatu i sprawdzania typu.

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

Pole statyczne `Descriptor` w każdym wygenerowanym typie jest używane przez wewnętrzny kod odbicia protobuf w celu rozpoznania `Any` typów pól. Istnieje również Metoda `TryUnpack<T>`, ale która tworzy niezainicjowane wystąpienie `T` nawet wtedy, gdy nie powiedzie się, dlatego lepiej jest użyć metody `Is`, jak pokazano powyżej.

## <a name="oneof"></a>Oneof

Pola oneof są funkcją języka: słowo kluczowe `oneof` jest obsługiwane przez kompilator podczas generowania klasy komunikatów. Użycie `oneof` do określenia `ChangeNotification` komunikat może wyglądać następująco:

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

Pola w ramach zestawu `oneof` muszą mieć unikatowe numery pól w całej deklaracji komunikatu.

Gdy używasz `oneof`, wygenerowany C# kod zawiera wyliczenie, które określa, które z pól zostały ustawione. Możesz przetestować Wyliczenie, aby znaleźć pole, które zostało ustawione. Pola, które nie ustawiają zwracanych `null` lub wartości domyślnej, zamiast zgłaszać wyjątek.

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

Ustawienie dowolnego pola, które jest częścią zestawu `oneof`, spowoduje automatyczne wyczyszczenie innych pól w zestawie. Nie można użyć `repeated` z `oneof`. Zamiast tego można utworzyć zagnieżdżony komunikat z powtarzającym się polem lub `oneof` ustawionym na obejście tego ograniczenia.

>[!div class="step-by-step"]
>[Poprzedni](protobuf-reserved.md)
>[Następny](protobuf-enums.md)
