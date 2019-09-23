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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="ac49d-103">Protobuf wszystkie pola i oneof dla typów wariantów</span><span class="sxs-lookup"><span data-stu-id="ac49d-103">Protobuf Any and Oneof fields for variant types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ac49d-104">Obsługa typów właściwości dynamicznych (czyli właściwości typu `object`) w programie WCF jest skomplikowana.</span><span class="sxs-lookup"><span data-stu-id="ac49d-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="ac49d-105">Należy określić serializatory, należy podać atrybuty [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ac49d-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="ac49d-106">Protobuf udostępnia dwie prostsze opcje do pracy z wartościami, które mogą mieć więcej niż jeden typ.</span><span class="sxs-lookup"><span data-stu-id="ac49d-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="ac49d-107">Typ może reprezentować dowolny znany typ komunikatu protobuf, `oneof` podczas gdy słowo kluczowe pozwala określić, że tylko jeden z zakresów pól może być ustawiony w danym komunikacie. `Any`</span><span class="sxs-lookup"><span data-stu-id="ac49d-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="ac49d-108">Any</span><span class="sxs-lookup"><span data-stu-id="ac49d-108">Any</span></span>

<span data-ttu-id="ac49d-109">`Any`jest jednym z "dobrze znanych typów protobuf": Kolekcja przydatnych typów wiadomości wielokrotnego użytku z implementacjami we wszystkich obsługiwanych językach.</span><span class="sxs-lookup"><span data-stu-id="ac49d-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="ac49d-110">Aby użyć tego `Any` typu, należy `google/protobuf/any.proto` zaimportować definicję.</span><span class="sxs-lookup"><span data-stu-id="ac49d-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="ac49d-111">W C# kodzie `Any` Klasa zawiera metody służące do ustawiania pola, wyodrębniania komunikatu i sprawdzania typu.</span><span class="sxs-lookup"><span data-stu-id="ac49d-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="ac49d-112">Pole statyczne w każdym wygenerowanym typie jest używane przez wewnętrzny kod odbicia protobuf w `Any` celu rozpoznania typów pól. `Descriptor`</span><span class="sxs-lookup"><span data-stu-id="ac49d-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="ac49d-113">Istnieje również `TryUnpack<T>` Metoda, ale która tworzy niezainicjowane `T` wystąpienie nawet wtedy, gdy nie powiedzie się, więc lepiej jest użyć `Is` metody, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="ac49d-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="ac49d-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="ac49d-114">Oneof</span></span>

<span data-ttu-id="ac49d-115">Pola oneof są funkcją języka: `oneof` słowo kluczowe jest obsługiwane przez kompilator podczas generowania klasy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ac49d-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="ac49d-116">Użycie `oneof` do`ChangeNotification` określenia komunikatu może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ac49d-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="ac49d-117">Pola w `oneof` zestawie muszą mieć unikatowe numery pól w całej deklaracji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="ac49d-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="ac49d-118">Gdy używasz `oneof`, wygenerowany C# kod zawiera wyliczenie, które określa, które z pól zostały ustawione.</span><span class="sxs-lookup"><span data-stu-id="ac49d-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="ac49d-119">Możesz przetestować Wyliczenie, aby znaleźć pole, które zostało ustawione.</span><span class="sxs-lookup"><span data-stu-id="ac49d-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="ac49d-120">Pola, które nie ustawiają `null` wartości zwracanej lub domyślnej, zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ac49d-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="ac49d-121">Ustawienie dowolnego pola, które jest częścią `oneof` zestawu, spowoduje automatyczne wyczyszczenie innych pól w zestawie.</span><span class="sxs-lookup"><span data-stu-id="ac49d-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="ac49d-122">Nie można używać `repeated` z `oneof`.</span><span class="sxs-lookup"><span data-stu-id="ac49d-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="ac49d-123">Zamiast tego można utworzyć zagnieżdżony komunikat z powtarzającym się polem lub `oneof` zestawem, aby obejść to ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="ac49d-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ac49d-124">[Poprzedni](protobuf-reserved.md)
>[Następny](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="ac49d-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
