---
title: Protobuf zastrzeżone pola — gRPC dla deweloperów WCF
description: Dowiedz się więcej na temat zarezerwowanych pól w celu zapewnienia zgodności między wersjami.
ms.date: 09/09/2019
ms.openlocfilehash: 50082a1aab2e7707a1839b9d56455124a9e4a6a1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542979"
---
# <a name="protobuf-reserved-fields"></a>Pola zastrzeżone Protobuf

Gwarancje zgodności z poprzednimi wersjami w buforze protokołu (protobuf) polegają na numerach pól zawsze reprezentujących ten sam element danych. Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany. Można to enfore za pomocą słowa kluczowego `reserved`. 

Jeśli pola `displayName` i `marketId` zostały usunięte z wiadomości `Stock` zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane jak w poniższym przykładzie.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Możesz również użyć słowa kluczowego `reserved` jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości. Można wyznaczać ciągłe numery pól jako zakres za pomocą słowa kluczowego `to`.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Poprzednie](protobuf-repeated.md)
>[dalej](protobuf-any-oneof.md)
