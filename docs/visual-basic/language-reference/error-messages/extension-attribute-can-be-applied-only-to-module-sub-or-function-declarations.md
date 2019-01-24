---
title: '&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718237"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji
Jedynym sposobem, aby rozszerzyć typu danych w języku Visual Basic jest zdefiniować metodę rozszerzenia w ramach standardowego modułu. Metoda rozszerzenia może być `Sub` procedury lub `Function` procedury. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw. Opcjonalnie moduł, który zawiera metodę rozszerzającą może być oznaczony w taki sam sposób. Zakaz używania atrybutu rozszerzenia jest nieprawidłowy.  
  
 **Identyfikator błędu:** BC36550  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń atrybut rozszerzenia.  
  
-   Zmodyfikowanie Twojego rozszerzenia jako metoda, zdefiniowana w module otaczającej.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Omówienie atrybuty](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Metody rozszerzeń](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)
