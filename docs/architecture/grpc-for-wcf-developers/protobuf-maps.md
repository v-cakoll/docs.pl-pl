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
# <a name="protobuf-maps-for-dictionaries"></a>Mapy Protobuf dla słowników

Ważne jest, aby reprezentować dowolne kolekcje nazwanych wartości w komunikatach. W programie .NET jest to często obsługiwane przez typy słowników. Odpowiednikiem typu <xref:System.Collections.Generic.IDictionary%602> .NET w buforze protokołu (protobuf) jest typ `map<key_type, value_type>`. W tej sekcji pokazano, jak zadeklarować typ `map` w protobuf i jak używać wygenerowanego kodu.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

W wygenerowanym kodzie `map` pola używają klasy `Google.Protobuf.Collections.MapField<TKey, TValue>`. Ta klasa implementuje standardowe interfejsy kolekcji .NET, w tym <xref:System.Collections.Generic.IDictionary%602>.

Nie można bezpośrednio powtarzać pól mapy w definicji komunikatu. Można jednak utworzyć zagnieżdżony komunikat zawierający mapę i użyć `repeated` w przypadku typu komunikatu, jak w poniższym przykładzie:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Używanie właściwości MapField w kodzie

`MapField` właściwości generowane na podstawie `map` pól są tylko do odczytu i nie będą `null`. Aby ustawić właściwość mapy, użyj metody `Add(IDictionary<TKey,TValue> values)` na pustej właściwości `MapField`, aby skopiować wartości z dowolnego słownika platformy .NET.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Dalsze informacje

Aby uzyskać więcej informacji na temat protobuf, zobacz oficjalną [dokumentację protobuf](https://developers.google.com/protocol-buffers/docs/overview).

>[!div class="step-by-step"]
>[Poprzednie](protobuf-enums.md)
>[dalej](wcf-services-to-grpc-comparison.md)
