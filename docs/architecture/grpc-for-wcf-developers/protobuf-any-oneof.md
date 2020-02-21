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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="eae31-103">Protobuf wszystkie pola i oneof dla typów wariantów</span><span class="sxs-lookup"><span data-stu-id="eae31-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="eae31-104">Obsługa typów właściwości dynamicznych (czyli właściwości typu `object`) w Windows Communication Foundation (WCF) jest skomplikowana.</span><span class="sxs-lookup"><span data-stu-id="eae31-104">Handling dynamic property types (that is, properties of type `object`) in Windows Communication Foundation (WCF) is complicated.</span></span> <span data-ttu-id="eae31-105">Na przykład należy określić serializatory i podać atrybuty [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="eae31-105">For example, you must specify serializers and provide [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes.</span></span>

<span data-ttu-id="eae31-106">Bufor protokołu (protobuf) oferuje dwie prostsze opcje do pracy z wartościami, które mogą mieć więcej niż jeden typ.</span><span class="sxs-lookup"><span data-stu-id="eae31-106">Protocol Buffer (Protobuf) provides two simpler options for dealing with values that might be of more than one type.</span></span> <span data-ttu-id="eae31-107">Typ `Any` może reprezentować dowolny znany typ komunikatu protobuf.</span><span class="sxs-lookup"><span data-stu-id="eae31-107">The `Any` type can represent any known Protobuf message type.</span></span> <span data-ttu-id="eae31-108">Można też użyć słowa kluczowego `oneof`, aby określić, że tylko jeden z zakresów pól może być ustawiony w dowolnym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="eae31-108">And you can use the `oneof` keyword to specify that only one of a range of fields can be set in any message.</span></span>

## <a name="any"></a><span data-ttu-id="eae31-109">Dowolne</span><span class="sxs-lookup"><span data-stu-id="eae31-109">Any</span></span>

<span data-ttu-id="eae31-110">`Any` to jeden z "dobrze znanych typów protobuf": Kolekcja przydatnych typów wiadomości wielokrotnego użytku z implementacjami we wszystkich obsługiwanych językach.</span><span class="sxs-lookup"><span data-stu-id="eae31-110">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="eae31-111">Aby użyć typu `Any`, należy zaimportować definicję `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="eae31-111">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="eae31-112">W C# kodzie Klasa `Any` dostarcza metody służące do ustawiania pola, wyodrębniania komunikatu i sprawdzania typu.</span><span class="sxs-lookup"><span data-stu-id="eae31-112">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="eae31-113">Wewnętrzny kod odbicia protobuf używa pola statycznego `Descriptor` w każdym wygenerowanym typie, aby rozwiązać `Any` typy pól.</span><span class="sxs-lookup"><span data-stu-id="eae31-113">Protobuf's internal reflection code uses the `Descriptor` static field on each generated type to resolve `Any` field types.</span></span> <span data-ttu-id="eae31-114">Istnieje również Metoda `TryUnpack<T>`, która tworzy niezainicjowane wystąpienie `T` nawet wtedy, gdy nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="eae31-114">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails.</span></span> <span data-ttu-id="eae31-115">Lepiej jest użyć metody `Is`, jak pokazano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="eae31-115">It's better to use the `Is` method as shown earlier.</span></span>

## <a name="oneof"></a><span data-ttu-id="eae31-116">Oneof</span><span class="sxs-lookup"><span data-stu-id="eae31-116">Oneof</span></span>

<span data-ttu-id="eae31-117">Pola oneof są funkcją języka: kompilator obsługuje słowo kluczowe `oneof` podczas generowania klasy komunikatów.</span><span class="sxs-lookup"><span data-stu-id="eae31-117">Oneof fields are a language feature: the compiler handles the `oneof` keyword when it generates the message class.</span></span> <span data-ttu-id="eae31-118">Użycie `oneof` do określenia `ChangeNotification` komunikat może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="eae31-118">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="eae31-119">Pola w zestawie `oneof` muszą mieć unikatowe numery pól w ogólnej deklaracji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="eae31-119">Fields within the `oneof` set must have unique field numbers in the overall message declaration.</span></span>

<span data-ttu-id="eae31-120">Gdy używasz `oneof`, wygenerowany C# kod zawiera wyliczenie, które określa, które z pól zostały ustawione.</span><span class="sxs-lookup"><span data-stu-id="eae31-120">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="eae31-121">Możesz przetestować Wyliczenie, aby znaleźć pole, które zostało ustawione.</span><span class="sxs-lookup"><span data-stu-id="eae31-121">You can test the enum to find which field is set.</span></span> <span data-ttu-id="eae31-122">Pola, które nie ustawiają zwracanych `null` lub wartości domyślnej, zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="eae31-122">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="eae31-123">Ustawienie dowolnego pola, które jest częścią zestawu `oneof`, spowoduje automatyczne wyczyszczenie innych pól w zestawie.</span><span class="sxs-lookup"><span data-stu-id="eae31-123">Setting any field that's part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="eae31-124">Nie można użyć `repeated` z `oneof`.</span><span class="sxs-lookup"><span data-stu-id="eae31-124">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="eae31-125">Zamiast tego można utworzyć zagnieżdżony komunikat z powtarzającym się polem lub `oneof` ustawionym na obejście tego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="eae31-125">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="eae31-126">[Poprzednie](protobuf-reserved.md)
>[dalej](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="eae31-126">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
