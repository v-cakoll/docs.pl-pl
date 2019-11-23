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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="91a0b-103">Protobuf wszystkie pola i oneof dla typów wariantów</span><span class="sxs-lookup"><span data-stu-id="91a0b-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="91a0b-104">Obsługa typów właściwości dynamicznych (czyli właściwości typu `object`) w programie WCF jest skomplikowana.</span><span class="sxs-lookup"><span data-stu-id="91a0b-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="91a0b-105">Należy określić serializatory, należy podać atrybuty [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="91a0b-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="91a0b-106">Protobuf udostępnia dwie prostsze opcje do pracy z wartościami, które mogą mieć więcej niż jeden typ.</span><span class="sxs-lookup"><span data-stu-id="91a0b-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="91a0b-107">Typ `Any` może reprezentować dowolny znany typ komunikatu protobuf, podczas gdy słowo kluczowe `oneof` pozwala określić, że tylko jeden z zakresów pól można ustawić w danym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="91a0b-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="91a0b-108">Dowolne</span><span class="sxs-lookup"><span data-stu-id="91a0b-108">Any</span></span>

<span data-ttu-id="91a0b-109">`Any` to jeden z "dobrze znanych typów protobuf": Kolekcja przydatnych typów wiadomości wielokrotnego użytku z implementacjami we wszystkich obsługiwanych językach.</span><span class="sxs-lookup"><span data-stu-id="91a0b-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="91a0b-110">Aby użyć typu `Any`, należy zaimportować definicję `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="91a0b-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="91a0b-111">W C# kodzie Klasa `Any` dostarcza metody służące do ustawiania pola, wyodrębniania komunikatu i sprawdzania typu.</span><span class="sxs-lookup"><span data-stu-id="91a0b-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="91a0b-112">Pole statyczne `Descriptor` w każdym wygenerowanym typie jest używane przez wewnętrzny kod odbicia protobuf w celu rozpoznania `Any` typów pól.</span><span class="sxs-lookup"><span data-stu-id="91a0b-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="91a0b-113">Istnieje również Metoda `TryUnpack<T>`, ale która tworzy niezainicjowane wystąpienie `T` nawet wtedy, gdy nie powiedzie się, dlatego lepiej jest użyć metody `Is`, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="91a0b-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="91a0b-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="91a0b-114">Oneof</span></span>

<span data-ttu-id="91a0b-115">Pola oneof są funkcją języka: słowo kluczowe `oneof` jest obsługiwane przez kompilator podczas generowania klasy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="91a0b-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="91a0b-116">Użycie `oneof` do określenia `ChangeNotification` komunikat może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="91a0b-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="91a0b-117">Pola w ramach zestawu `oneof` muszą mieć unikatowe numery pól w całej deklaracji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="91a0b-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="91a0b-118">Gdy używasz `oneof`, wygenerowany C# kod zawiera wyliczenie, które określa, które z pól zostały ustawione.</span><span class="sxs-lookup"><span data-stu-id="91a0b-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="91a0b-119">Możesz przetestować Wyliczenie, aby znaleźć pole, które zostało ustawione.</span><span class="sxs-lookup"><span data-stu-id="91a0b-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="91a0b-120">Pola, które nie ustawiają zwracanych `null` lub wartości domyślnej, zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="91a0b-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="91a0b-121">Ustawienie dowolnego pola, które jest częścią zestawu `oneof`, spowoduje automatyczne wyczyszczenie innych pól w zestawie.</span><span class="sxs-lookup"><span data-stu-id="91a0b-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="91a0b-122">Nie można użyć `repeated` z `oneof`.</span><span class="sxs-lookup"><span data-stu-id="91a0b-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="91a0b-123">Zamiast tego można utworzyć zagnieżdżony komunikat z powtarzającym się polem lub `oneof` ustawionym na obejście tego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="91a0b-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="91a0b-124">[Poprzedni](protobuf-reserved.md)
>[Następny](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="91a0b-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
