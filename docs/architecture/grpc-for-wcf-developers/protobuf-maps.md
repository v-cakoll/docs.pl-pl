---
title: Mapy protobuf dla słowników — gRPC dla deweloperów WCF
description: Dowiedz się, jak reprezentować za pomocą map protobuf. Typy słowników netto.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6a71fb7940145571a94eaf5c8bae9dfc91a30db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184212"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="216ec-103">Mapy protobuf dla słowników</span><span class="sxs-lookup"><span data-stu-id="216ec-103">Protobuf maps for dictionaries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="216ec-104">Ważne jest, aby reprezentować dowolne kolekcje nazwanych wartości w komunikatach.</span><span class="sxs-lookup"><span data-stu-id="216ec-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="216ec-105">W programie .NET jest to często obsługiwane przy użyciu typów słowników.</span><span class="sxs-lookup"><span data-stu-id="216ec-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="216ec-106">Odpowiednikiem protobuf typu .NET <xref:System.Collections.Generic.IDictionary%602> `map<key_type, value_type>` jest typ.</span><span class="sxs-lookup"><span data-stu-id="216ec-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="216ec-107">W tej sekcji pokazano, jak zadeklarować element `map` w protobuf i jak używać wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="216ec-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="216ec-108">W wygenerowanym kodzie `map` pola `Google.Protobuf.Collections.MapField<TKey, TValue>` używają klasy, która implementuje standardowe interfejsy kolekcji .NET, w tym <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="216ec-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="216ec-109">Pola mapy nie mogą być bezpośrednio powtórzone w definicji komunikatu, ale można utworzyć zagnieżdżony komunikat zawierający mapę i użyć `repeated` jej w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="216ec-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="216ec-110">Używanie właściwości MapField w kodzie</span><span class="sxs-lookup"><span data-stu-id="216ec-110">Using MapField properties in code</span></span>

<span data-ttu-id="216ec-111">Właściwości generowane na podstawie `map` pól są tylko do odczytu i nigdy nie `null`będą. `MapField`</span><span class="sxs-lookup"><span data-stu-id="216ec-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="216ec-112">Aby ustawić właściwość mapy, użyj `Add(IDictionary<TKey,TValue> values)` metody na pustej `MapField` właściwości, aby skopiować wartości z dowolnego słownika platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="216ec-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="216ec-113">Dalsze odczytywanie</span><span class="sxs-lookup"><span data-stu-id="216ec-113">Further reading</span></span>

<span data-ttu-id="216ec-114">Aby uzyskać więcej informacji na temat protobuf, zobacz oficjalną [dokumentację protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="216ec-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="216ec-115">[Poprzedni](protobuf-enums.md)
>[Następny](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="216ec-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
