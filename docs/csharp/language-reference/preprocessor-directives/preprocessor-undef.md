---
title: '#undef - C# odwołania'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 0dedd1480dae15d2c04b47cee132ab3227098f56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688569"
---
# <a name="undef-c-reference"></a>#undef (odwołanie w C#)
Dyrektywa `#undef` umożliwia anulowanie definicji symbolu w taki sposób, że w przypadku użycia symbolu jako wyrażenia w dyrektywie [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) zostanie zwrócona wartość `false`.  
  
 Symbol może być zdefiniowana za pomocą [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy lub [— Zdefiniuj](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora. Dyrektywa `#undef` musi znajdować się w pliku przed użyciem jakichkolwiek instrukcji, które nie są również dyrektywami.  
  
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

**DEBUGOWANIE nie jest zdefiniowany.**

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
