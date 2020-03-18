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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="d04e1-103">Pola zastrzeżone Protobuf</span><span class="sxs-lookup"><span data-stu-id="d04e1-103">Protobuf reserved fields</span></span>

<span data-ttu-id="d04e1-104">Gwarancje zgodności z poprzednimi wersjami w buforze protokołu (Protobuf) opierają się na numerach pól zawsze reprezentujących ten sam element danych.</span><span class="sxs-lookup"><span data-stu-id="d04e1-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="d04e1-105">Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany.</span><span class="sxs-lookup"><span data-stu-id="d04e1-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="d04e1-106">Można to wyposażać za pomocą słowa kluczowego. `reserved`</span><span class="sxs-lookup"><span data-stu-id="d04e1-106">You can enfore this by using the `reserved` keyword.</span></span>

<span data-ttu-id="d04e1-107">Jeśli `displayName` pola `marketId` i pola `Stock` zostały usunięte z wiadomości zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d04e1-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="d04e1-108">Słowo `reserved` kluczowe można również użyć jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="d04e1-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="d04e1-109">Za pomocą słowa kluczowego `to` można wyrazić ciągłe liczby pól jako zakres.</span><span class="sxs-lookup"><span data-stu-id="d04e1-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="d04e1-110">[Poprzedni](protobuf-repeated.md)
>[następny](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="d04e1-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
