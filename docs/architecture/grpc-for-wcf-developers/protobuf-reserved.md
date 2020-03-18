---
title: Pola zarezerwowane Protobuf - gRPC dla programistów WCF
description: Dowiedz się więcej o polach zarezerwowanych dla zgodności z wersjami krzyżowymi.
ms.date: 09/09/2019
ms.openlocfilehash: bde658c671e970b7ec841d71d5b4284eb91195f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147948"
---
# <a name="protobuf-reserved-fields"></a>Pola zastrzeżone Protobuf

Gwarancje zgodności z poprzednimi wersjami w buforze protokołu (Protobuf) opierają się na numerach pól zawsze reprezentujących ten sam element danych. Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany. Można to wyposażać za pomocą słowa kluczowego. `reserved`

Jeśli `displayName` pola `marketId` i pola `Stock` zostały usunięte z wiadomości zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane, jak w poniższym przykładzie.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Słowo `reserved` kluczowe można również użyć jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości. Za pomocą słowa kluczowego `to` można wyrazić ciągłe liczby pól jako zakres.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Poprzedni](protobuf-repeated.md)
>[następny](protobuf-any-oneof.md)
