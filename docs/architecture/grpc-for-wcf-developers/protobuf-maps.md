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
# <a name="protobuf-maps-for-dictionaries"></a>Mapy protobuf dla słowników

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Ważne jest, aby reprezentować dowolne kolekcje nazwanych wartości w komunikatach. W programie .NET jest to często obsługiwane przy użyciu typów słowników. Odpowiednikiem protobuf typu .NET <xref:System.Collections.Generic.IDictionary%602> `map<key_type, value_type>` jest typ. W tej sekcji pokazano, jak zadeklarować element `map` w protobuf i jak używać wygenerowanego kodu.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

W wygenerowanym kodzie `map` pola `Google.Protobuf.Collections.MapField<TKey, TValue>` używają klasy, która implementuje standardowe interfejsy kolekcji .NET, w tym <xref:System.Collections.Generic.IDictionary%602>.

Pola mapy nie mogą być bezpośrednio powtórzone w definicji komunikatu, ale można utworzyć zagnieżdżony komunikat zawierający mapę i użyć `repeated` jej w następującym przykładzie:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Używanie właściwości MapField w kodzie

Właściwości generowane na podstawie `map` pól są tylko do odczytu i nigdy nie `null`będą. `MapField` Aby ustawić właściwość mapy, użyj `Add(IDictionary<TKey,TValue> values)` metody na pustej `MapField` właściwości, aby skopiować wartości z dowolnego słownika platformy .NET.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Dalsze odczytywanie

Aby uzyskać więcej informacji na temat protobuf, zobacz oficjalną [dokumentację protobuf](https://developers.google.com/protocol-buffers/docs/overview).

>[!div class="step-by-step"]
>[Poprzedni](protobuf-enums.md)
>[Następny](wcf-services-to-grpc-comparison.md)
