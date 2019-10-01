---
title: Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 95a67a552efacf9e77dc3ebc3e0187817a6d82e2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698580"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”
Jedynym sposobem rozszerzania typu danych w Visual Basic jest zdefiniowanie metody rozszerzającej wewnątrz modułu standardowego. Metoda rozszerzenia może być procedurą `Sub` lub `Function`. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>. Opcjonalnie moduł, który zawiera metodę rozszerzenia, może być oznaczony w taki sam sposób. Żadne inne użycie atrybutu Extension nie jest prawidłowe.  
  
 **Identyfikator błędu:** BC36550  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń atrybut rozszerzenia.  
  
- Przeprojektowanie rozszerzenia jako metody zdefiniowanej w otaczającym module.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano metodę `Print` dla typu danych `String`.  
  
```vb  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
