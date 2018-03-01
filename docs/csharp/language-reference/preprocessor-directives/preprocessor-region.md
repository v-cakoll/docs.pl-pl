---
title: "#region (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a>#region (odwołanie w C#)
`#region`Pozwala określić blok kodu, który można rozwinąć lub zwinąć przy użyciu [zwijania](/visualstudio/ide/outlining) funkcji edytora kodu programu Visual Studio. W plikach kodu dłużej jest wygodne można zwinąć lub ukrywanie jednego lub więcej regionów, dzięki czemu można skupić się w tej części pliku, który pracuje obecnie. Poniższy przykład przedstawia sposób definiowania regionu:  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>Uwagi  
 A `#region` muszą kończyć bloku [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) dyrektywy.  
  
 A `#region` bloku nie mogą nakładać się na [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloku. Jednak `#region` bloku może być zagnieżdżona w `#if` bloku, a `#if` bloku może być zagnieżdżona w `#region` bloku.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
