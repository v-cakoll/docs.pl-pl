---
title: "#<a name=\"undef-c-reference\"></a>undef (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#undef'
helpviewer_keywords: '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a3c162c0ecb8bb39cc13a34dcd15fa3ce96ebb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="undef-c-reference"></a>#undef (odwołanie w C#)
`#undef`Umożliwia usuń symbol, taki sposób, że przy użyciu symbolu jako wyrażenie w [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy, wyrażenie, które będą oceniać do `false`.  
  
 Symbol może być zdefiniowany za pomocą [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy lub [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora. `#undef` Dyrektywa musi występować w pliku, aby korzystać z żadnych instrukcji, które nie są również dyrektywy.  
  
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
  
 **Nie zdefiniowano debugowania**  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
