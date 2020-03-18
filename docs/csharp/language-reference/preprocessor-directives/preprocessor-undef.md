---
title: '#undef — odwołanie do języka C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712445"
---
# <a name="undef-c-reference"></a>#undef (odwołanie w C#)
`#undef`umożliwia oddefiniowanie symbolu, tak aby za pomocą symbolu jako wyrażenia w `false` [#if](./preprocessor-if.md) dyrektywy wyrażenie będzie obliczać .  
  
 Symbol można zdefiniować za pomocą [#define](./preprocessor-define.md) dyrektywy lub [opcji -define](../compiler-options/define-compiler-option.md) kompilatora. Dyrektywa `#undef` musi pojawić się w pliku przed użyciem żadnych instrukcji, które nie są również dyrektywy.  
  
## <a name="example"></a>Przykład  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

**DEBUG nie jest zdefiniowany**

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
