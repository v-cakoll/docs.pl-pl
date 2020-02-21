---
title: Protobuf typy zagnieżdżone — gRPC dla deweloperów WCF
description: Dowiedz się więcej o zagnieżdżonych typach komunikatów w protobuf i gRPC i sposobach ich generowania C#.
ms.date: 09/09/2019
ms.openlocfilehash: 7b9a331336ebe1ca7bc75fdd164b7b88ae4f9db2
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542849"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="3312a-103">Typy zagnieżdżone Protobuf</span><span class="sxs-lookup"><span data-stu-id="3312a-103">Protobuf nested types</span></span>

<span data-ttu-id="3312a-104">Podobnie jak C# w przypadku, gdy można zadeklarować klasy wewnątrz innych klas, bufor protokołu (protobuf) pozwala zagnieżdżać definicje komunikatów w innych wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="3312a-104">Just as C# allows you to declare classes inside other classes, Protocol Buffer (Protobuf) allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="3312a-105">Poniższy przykład przedstawia sposób tworzenia zagnieżdżonych typów komunikatów:</span><span class="sxs-lookup"><span data-stu-id="3312a-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="3312a-106">W wygenerowanym C# kodzie typ `Inner` zostanie zadeklarowany w zagnieżdżonej klasie `Types` statycznej w klasie `HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="3312a-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="3312a-107">[Poprzednie](protobuf-data-types.md)
>[dalej](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="3312a-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
