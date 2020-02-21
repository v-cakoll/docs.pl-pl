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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="173b4-103">Pola zastrzeżone Protobuf</span><span class="sxs-lookup"><span data-stu-id="173b4-103">Protobuf reserved fields</span></span>

<span data-ttu-id="173b4-104">Gwarancje zgodności z poprzednimi wersjami w buforze protokołu (protobuf) polegają na numerach pól zawsze reprezentujących ten sam element danych.</span><span class="sxs-lookup"><span data-stu-id="173b4-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="173b4-105">Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany.</span><span class="sxs-lookup"><span data-stu-id="173b4-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="173b4-106">Można to enfore za pomocą słowa kluczowego `reserved`.</span><span class="sxs-lookup"><span data-stu-id="173b4-106">You can enfore this by using the `reserved` keyword.</span></span> 

<span data-ttu-id="173b4-107">Jeśli pola `displayName` i `marketId` zostały usunięte z wiadomości `Stock` zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="173b4-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="173b4-108">Możesz również użyć słowa kluczowego `reserved` jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="173b4-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="173b4-109">Można wyznaczać ciągłe numery pól jako zakres za pomocą słowa kluczowego `to`.</span><span class="sxs-lookup"><span data-stu-id="173b4-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="173b4-110">[Poprzednie](protobuf-repeated.md)
>[dalej](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="173b4-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
