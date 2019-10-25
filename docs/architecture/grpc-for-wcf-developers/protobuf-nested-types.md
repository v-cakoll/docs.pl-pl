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
# <a name="protobuf-nested-types"></a>Typy zagnieżdżone Protobuf

Podobnie jak C# w przypadku programu można zadeklarować klasy wewnątrz innych klas, protobuf umożliwia zagnieżdżanie definicji komunikatów w innych wiadomościach. Poniższy przykład przedstawia sposób tworzenia zagnieżdżonych typów komunikatów:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

W wygenerowanym C# kodzie typ`Inner`zostanie zadeklarowany w zagnieżdżonej klasie`Types`statycznej w klasie`HelloRequest`:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Poprzedni](protobuf-data-types.md)
>[Następny](protobuf-repeated.md)
