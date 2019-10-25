---
title: Protobuf typy zagnieżdżone — gRPC dla deweloperów WCF
description: Dowiedz się więcej o zagnieżdżonych typach komunikatów w protobuf i gRPC i sposobach ich generowania C#.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ec9fc522619230c1201bfef1e8128f7356936212
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846314"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="9059c-103">Typy zagnieżdżone Protobuf</span><span class="sxs-lookup"><span data-stu-id="9059c-103">Protobuf nested types</span></span>

<span data-ttu-id="9059c-104">Podobnie jak C# w przypadku programu można zadeklarować klasy wewnątrz innych klas, protobuf umożliwia zagnieżdżanie definicji komunikatów w innych wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="9059c-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="9059c-105">Poniższy przykład przedstawia sposób tworzenia zagnieżdżonych typów komunikatów:</span><span class="sxs-lookup"><span data-stu-id="9059c-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="9059c-106">W wygenerowanym C# kodzie typ`Inner`zostanie zadeklarowany w zagnieżdżonej klasie`Types`statycznej w klasie`HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="9059c-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="9059c-107">[Poprzedni](protobuf-data-types.md)
>[Następny](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="9059c-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
