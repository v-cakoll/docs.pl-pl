---
title: Protobuf zastrzeżone pola — gRPC dla deweloperów WCF
description: Dowiedz się więcej na temat zarezerwowanych pól w celu zapewnienia zgodności między wersjami.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 34697371299bdc5d9a58c0696c1ce7d19816ca87
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846327"
---
# <a name="protobuf-reserved-fields"></a>Pola zastrzeżone Protobuf

Gwarancje zgodności wstecznej protobuf polegają na numerach pól zawsze reprezentujących ten sam element danych. Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany. Można to zrobić za pomocą słowa kluczowego `reserved`. Jeśli pola `displayName` i `marketId` zostały usunięte z wiadomości `Stock` zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane jak w poniższym przykładzie.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Słowa kluczowego `reserved` można także użyć jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości. Ciągłe numery pól można wyrazić jako zakres przy użyciu słowa kluczowego `to`.

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
