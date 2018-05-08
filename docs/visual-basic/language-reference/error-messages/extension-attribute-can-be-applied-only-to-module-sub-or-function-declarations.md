---
title: '&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji
Jedynym sposobem rozszerzenia typu danych w języku Visual Basic jest określenie metody rozszerzenia wewnątrz standardowy moduł. Metoda rozszerzenia może być `Sub` procedury lub `Function` procedury. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw. Opcjonalnie moduł, który zawiera metody rozszerzenia mogą być oznaczone w taki sam sposób. Nie użycie atrybutu rozszerzenia jest prawidłowy.  
  
 **Identyfikator błędu:** BC36550  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń atrybut rozszerzenia.  
  
-   Zmodyfikowanie rozszerzenie metodą zdefiniowanego w module otaczającej.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `Print` metodę `String` typu danych.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty — omówienie](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
