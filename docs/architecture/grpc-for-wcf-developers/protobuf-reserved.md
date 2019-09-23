---
title: Protobuf zastrzeżone pola — gRPC dla deweloperów WCF
description: Dowiedz się więcej na temat zarezerwowanych pól w celu zapewnienia zgodności między wersjami.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d4d40ca12d41ec37e0baebf10de9d0690e4297cc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184177"
---
# <a name="protobuf-reserved-fields"></a>Pola zastrzeżone protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Gwarancje zgodności wstecznej protobuf polegają na numerach pól zawsze reprezentujących ten sam element danych. Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany. Można to zrobić za pomocą `reserved` słowa kluczowego. Jeśli pola i `marketId` zostały usunięte z komunikatuzdefiniowanegowcześniej,ichnumerypólpowinnybyćzarezerwowanejakwponiższymprzykładzie.`Stock` `displayName`

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved` Słowo kluczowe może być również używane jako symbol zastępczy dla pól, które mogą zostać dodane w przyszłości. Ciągłe numery pól można wyrazić jako zakres przy użyciu `to` słowa kluczowego.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Poprzedni](protobuf-repeated.md)
>[Następny](protobuf-any-oneof.md)
