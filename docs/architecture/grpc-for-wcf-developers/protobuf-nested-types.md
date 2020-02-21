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
# <a name="protobuf-nested-types"></a>Typy zagnieżdżone Protobuf

Podobnie jak C# w przypadku, gdy można zadeklarować klasy wewnątrz innych klas, bufor protokołu (protobuf) pozwala zagnieżdżać definicje komunikatów w innych wiadomościach. Poniższy przykład przedstawia sposób tworzenia zagnieżdżonych typów komunikatów:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

W wygenerowanym C# kodzie typ `Inner` zostanie zadeklarowany w zagnieżdżonej klasie `Types` statycznej w klasie `HelloRequest`:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Poprzednie](protobuf-data-types.md)
>[dalej](protobuf-repeated.md)
