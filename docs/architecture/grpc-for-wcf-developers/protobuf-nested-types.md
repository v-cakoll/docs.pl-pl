---
title: Protobuf typy zagnieżdżone — gRPC dla deweloperów WCF
description: Dowiedz się więcej o zagnieżdżonych typach komunikatów w protobuf i gRPC i sposobach ich generowania C#.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 39bc52b37cc9e57cfe0ed5a5118c348de5f014d8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184191"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="eb244-103">Protobuf typy zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="eb244-103">Protobuf nested types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="eb244-104">Podobnie jak C# w przypadku programu można zadeklarować klasy wewnątrz innych klas, protobuf umożliwia zagnieżdżanie definicji komunikatów w innych wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="eb244-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="eb244-105">Poniższy przykład przedstawia sposób tworzenia zagnieżdżonych typów komunikatów:</span><span class="sxs-lookup"><span data-stu-id="eb244-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="eb244-106">C# W wygenerowanym kodzie, `Inner` typ zostanie zadeklarowany w zagnieżdżonej klasie `Types` `HelloRequest` statycznej w klasie:</span><span class="sxs-lookup"><span data-stu-id="eb244-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="eb244-107">[Poprzedni](protobuf-data-types.md)
>[Następny](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="eb244-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
