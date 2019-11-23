---
title: Protobuf zastrzeżone pola — gRPC dla deweloperów WCF
description: Dowiedz się więcej na temat zarezerwowanych pól w celu zapewnienia zgodności między wersjami.
ms.date: 09/09/2019
ms.openlocfilehash: e589cd38a712ce014fa2c4d847fbde359d538dd0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967310"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="38251-103">Pola zastrzeżone Protobuf</span><span class="sxs-lookup"><span data-stu-id="38251-103">Protobuf reserved fields</span></span>

<span data-ttu-id="38251-104">Gwarancje zgodności wstecznej protobuf polegają na numerach pól zawsze reprezentujących ten sam element danych.</span><span class="sxs-lookup"><span data-stu-id="38251-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="38251-105">Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany.</span><span class="sxs-lookup"><span data-stu-id="38251-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="38251-106">Można to zrobić za pomocą słowa kluczowego `reserved`.</span><span class="sxs-lookup"><span data-stu-id="38251-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="38251-107">Jeśli pola `displayName` i `marketId` zostały usunięte z wiadomości `Stock` zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="38251-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="38251-108">Słowa kluczowego `reserved` można także użyć jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="38251-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="38251-109">Ciągłe numery pól można wyrazić jako zakres przy użyciu słowa kluczowego `to`.</span><span class="sxs-lookup"><span data-stu-id="38251-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="38251-110">[Poprzedni](protobuf-repeated.md)
>[Następny](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="38251-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
