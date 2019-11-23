---
title: Protobuf typy zagnieżdżone — gRPC dla deweloperów WCF
description: Dowiedz się więcej o zagnieżdżonych typach komunikatów w protobuf i gRPC i sposobach ich generowania C#.
ms.date: 09/09/2019
ms.openlocfilehash: bbc7ed41516d29f867bbc9da5b258f6a3c9ff261
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967389"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="8adcd-103">Typy zagnieżdżone Protobuf</span><span class="sxs-lookup"><span data-stu-id="8adcd-103">Protobuf nested types</span></span>

<span data-ttu-id="8adcd-104">Podobnie jak C# w przypadku programu można zadeklarować klasy wewnątrz innych klas, protobuf umożliwia zagnieżdżanie definicji komunikatów w innych wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="8adcd-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="8adcd-105">Poniższy przykład przedstawia sposób tworzenia zagnieżdżonych typów komunikatów:</span><span class="sxs-lookup"><span data-stu-id="8adcd-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="8adcd-106">W wygenerowanym C# kodzie typ `Inner` zostanie zadeklarowany w zagnieżdżonej klasie `Types` statycznej w klasie `HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="8adcd-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="8adcd-107">[Poprzedni](protobuf-data-types.md)
>[Następny](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="8adcd-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
