---
title: "Porady: bezpieczne rzutowanie bool? na bool (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a>Porady: bezpieczne rzutowanie bool? na bool (Przewodnik programowania w języku C#)
`bool?` Typ dopuszczający wartość null, mogą zawierać trzy różne wartości: `true`, `false`, i `null`. W związku z tym `bool?` typu nie można używać w warunków, takich jak z `if`, `for`, lub `while`. Na przykład następujący kod powoduje błąd kompilatora.  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 To jest niedozwolona, ponieważ nie jest jasne co `null` oznacza, że w kontekście warunkowego. Umożliwia `bool?` w instrukcji warunkowej, sprawdź najpierw jego <xref:System.Nullable%601.HasValue%2A> właściwości, aby upewnić się, że jego wartość nie jest `null`, a następnie rzutować go na `bool`. Aby uzyskać więcej informacji, zobacz [bool](../../../csharp/language-reference/keywords/bool.md). Jeśli wykonać Rzutowanie na `bool?` o wartości `null`, <xref:System.InvalidOperationException> zostanie zgłoszony w test warunkowy. Poniższy przykład przedstawia sposób bezpieczne rzutowanie z `bool?` do `bool`:  
  
## <a name="example"></a>Przykład  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe literału](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [Typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md)  
 [?? Operator](../../../csharp/language-reference/operators/null-conditional-operator.md)
