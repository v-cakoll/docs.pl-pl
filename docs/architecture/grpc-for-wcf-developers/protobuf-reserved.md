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
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="ebe71-103">Pola zastrzeżone Protobuf</span><span class="sxs-lookup"><span data-stu-id="ebe71-103">Protobuf reserved fields</span></span>

<span data-ttu-id="ebe71-104">Gwarancje zgodności z powrotem w buforze protokołu (Protobuf) opierają się na numerach pól zawsze reprezentujących ten sam element danych.</span><span class="sxs-lookup"><span data-stu-id="ebe71-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="ebe71-105">Jeśli pole zostanie usunięte z wiadomości w nowej wersji usługi, numer tego pola nigdy nie powinien być ponownie odtwarzany.</span><span class="sxs-lookup"><span data-stu-id="ebe71-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="ebe71-106">Możesz to wymusić `reserved` za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="ebe71-106">You can enforce this by using the `reserved` keyword.</span></span>

<span data-ttu-id="ebe71-107">Jeśli `displayName` pola `marketId` i zostały `Stock` usunięte z wiadomości zdefiniowanej wcześniej, ich numery pól powinny być zarezerwowane jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ebe71-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="ebe71-108">Słowa kluczowego `reserved` można również użyć jako symbolu zastępczego dla pól, które mogą zostać dodane w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ebe71-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="ebe71-109">Przy użyciu `to` słowa kluczowego można wyrazić ciągłe liczby pól jako zakres.</span><span class="sxs-lookup"><span data-stu-id="ebe71-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="ebe71-110">[Poprzedni](protobuf-repeated.md)
>[następny](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="ebe71-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
