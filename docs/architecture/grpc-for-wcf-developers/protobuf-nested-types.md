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
# <a name="protobuf-nested-types"></a>Protobuf typy zagnieżdżone

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Podobnie jak C# w przypadku programu można zadeklarować klasy wewnątrz innych klas, protobuf umożliwia zagnieżdżanie definicji komunikatów w innych wiadomościach. Poniższy przykład przedstawia sposób tworzenia zagnieżdżonych typów komunikatów:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

C# W wygenerowanym kodzie, `Inner` typ zostanie zadeklarowany w zagnieżdżonej klasie `Types` `HelloRequest` statycznej w klasie:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Poprzedni](protobuf-data-types.md)
>[Następny](protobuf-repeated.md)
