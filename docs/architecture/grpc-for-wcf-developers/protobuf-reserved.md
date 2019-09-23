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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="5ac95-103">Pola zastrzeżone protobuf</span><span class="sxs-lookup"><span data-stu-id="5ac95-103">Protobuf reserved fields</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="5ac95-104">Gwarancje zgodności wstecznej protobuf polegają na numerach pól zawsze reprezentujących ten sam element danych.</span><span class="sxs-lookup"><span data-stu-id="5ac95-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="5ac95-105">Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, ten numer pola nigdy nie powinien być ponownie używany.</span><span class="sxs-lookup"><span data-stu-id="5ac95-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="5ac95-106">Można to zrobić za pomocą `reserved` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="5ac95-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="5ac95-107">Jeśli pola i `marketId` zostały usunięte z komunikatuzdefiniowanegowcześniej,ichnumerypólpowinnybyćzarezerwowanejakwponiższymprzykładzie.`Stock` `displayName`</span><span class="sxs-lookup"><span data-stu-id="5ac95-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="5ac95-108">`reserved` Słowo kluczowe może być również używane jako symbol zastępczy dla pól, które mogą zostać dodane w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="5ac95-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="5ac95-109">Ciągłe numery pól można wyrazić jako zakres przy użyciu `to` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="5ac95-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="5ac95-110">[Poprzedni](protobuf-repeated.md)
>[Następny](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="5ac95-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
