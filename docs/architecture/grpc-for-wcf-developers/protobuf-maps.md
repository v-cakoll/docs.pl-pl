---
title: Mapy protobuf dla słowników — gRPC dla deweloperów WCF
description: Zapoznaj się z tematem jak używać map protobuf do reprezentowania typów słowników w programie .NET.
ms.date: 09/09/2019
ms.openlocfilehash: bf848bbc7e3618f6d78e280fcd85d5eb88d5cfae
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543134"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="225d6-103">Mapy Protobuf dla słowników</span><span class="sxs-lookup"><span data-stu-id="225d6-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="225d6-104">Ważne jest, aby reprezentować dowolne kolekcje nazwanych wartości w komunikatach.</span><span class="sxs-lookup"><span data-stu-id="225d6-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="225d6-105">W programie .NET jest to często obsługiwane przez typy słowników.</span><span class="sxs-lookup"><span data-stu-id="225d6-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="225d6-106">Odpowiednikiem typu <xref:System.Collections.Generic.IDictionary%602> .NET w buforze protokołu (protobuf) jest typ `map<key_type, value_type>`.</span><span class="sxs-lookup"><span data-stu-id="225d6-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="225d6-107">W tej sekcji pokazano, jak zadeklarować typ `map` w protobuf i jak używać wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="225d6-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="225d6-108">W wygenerowanym kodzie `map` pola używają klasy `Google.Protobuf.Collections.MapField<TKey, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="225d6-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class.</span></span> <span data-ttu-id="225d6-109">Ta klasa implementuje standardowe interfejsy kolekcji .NET, w tym <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="225d6-109">This class implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="225d6-110">Nie można bezpośrednio powtarzać pól mapy w definicji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="225d6-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="225d6-111">Można jednak utworzyć zagnieżdżony komunikat zawierający mapę i użyć `repeated` w przypadku typu komunikatu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="225d6-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="225d6-112">Używanie właściwości MapField w kodzie</span><span class="sxs-lookup"><span data-stu-id="225d6-112">Using MapField properties in code</span></span>

<span data-ttu-id="225d6-113">`MapField` właściwości generowane na podstawie `map` pól są tylko do odczytu i nie będą `null`.</span><span class="sxs-lookup"><span data-stu-id="225d6-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="225d6-114">Aby ustawić właściwość mapy, użyj metody `Add(IDictionary<TKey,TValue> values)` na pustej właściwości `MapField`, aby skopiować wartości z dowolnego słownika platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="225d6-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="225d6-115">Dalsze informacje</span><span class="sxs-lookup"><span data-stu-id="225d6-115">Further reading</span></span>

<span data-ttu-id="225d6-116">Aby uzyskać więcej informacji na temat protobuf, zobacz oficjalną [dokumentację protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="225d6-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="225d6-117">[Poprzednie](protobuf-enums.md)
>[dalej](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="225d6-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
