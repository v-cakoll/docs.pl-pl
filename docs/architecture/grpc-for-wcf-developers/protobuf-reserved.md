---
title: Pola zastrzeżone Protobuf - gRPC dla programistów WCF
description: Dowiedz się więcej o polach zarezerwowanych dla zgodności między wersjami.
ms.date: 09/09/2019
ms.openlocfilehash: f89513c4659a02cbc94e1c659baecb9e750acbdc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111039"
---
# <a name="protobuf-reserved-fields"></a>Pola zastrzeżone Protobuf

Gwarancje zgodności z powrotem w buforze protokołu (Protobuf) opierają się na numerach pól zawsze reprezentujących ten sam element danych. Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, numer tego pola nigdy nie powinien być ponownie odtwarzany. Możesz to wymusić `reserved` za pomocą słowa kluczowego.

Jeśli `displayName` pola `marketId` i zostały `Stock` usunięte z wiadomości zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane jak w poniższym przykładzie.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Słowa kluczowego `reserved` można również użyć jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości. Przy użyciu `to` słowa kluczowego można wyrazić ciągłe liczby pól jako zakres.

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
