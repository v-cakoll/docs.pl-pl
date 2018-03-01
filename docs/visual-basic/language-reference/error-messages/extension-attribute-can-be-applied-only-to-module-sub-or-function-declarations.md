---
title: "&#39; Rozszerzenie &#39; Atrybut można stosować tylko do &#39; Moduł &#39; &#39; Sub &#39; lub &#39; Funkcja &#39; deklaracje"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d77933c52484eb934501107d1ddad15f0eca826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39; Rozszerzenie &#39; Atrybut można stosować tylko do &#39; Moduł &#39; &#39; Sub &#39; lub &#39; Funkcja &#39; deklaracje
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
 [Metody rozszerzenia](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
