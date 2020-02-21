---
title: Protobuf wszystkie pola i oneof dla typów wariantów — gRPC dla deweloperów WCF
description: Dowiedz się, jak używać dowolnego typu i słowa kluczowego oneof do reprezentowania typów obiektów Variant w komunikatach.
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543199"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf wszystkie pola i oneof dla typów wariantów

Obsługa typów właściwości dynamicznych (czyli właściwości typu `object`) w Windows Communication Foundation (WCF) jest skomplikowana. Na przykład należy określić serializatory i podać atrybuty [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .

Bufor protokołu (protobuf) oferuje dwie prostsze opcje do pracy z wartościami, które mogą mieć więcej niż jeden typ. Typ `Any` może reprezentować dowolny znany typ komunikatu protobuf. Można też użyć słowa kluczowego `oneof`, aby określić, że tylko jeden z zakresów pól może być ustawiony w dowolnym komunikacie.

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

Wewnętrzny kod odbicia protobuf używa pola statycznego `Descriptor` w każdym wygenerowanym typie, aby rozwiązać `Any` typy pól. Istnieje również Metoda `TryUnpack<T>`, która tworzy niezainicjowane wystąpienie `T` nawet wtedy, gdy nie powiedzie się. Lepiej jest użyć metody `Is`, jak pokazano wcześniej.

## <a name="oneof"></a>Oneof

Pola oneof są funkcją języka: kompilator obsługuje słowo kluczowe `oneof` podczas generowania klasy komunikatów. Użycie `oneof` do określenia `ChangeNotification` komunikat może wyglądać następująco:

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

Pola w zestawie `oneof` muszą mieć unikatowe numery pól w ogólnej deklaracji komunikatu.

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
>[Poprzednie](protobuf-reserved.md)
>[dalej](protobuf-enums.md)
