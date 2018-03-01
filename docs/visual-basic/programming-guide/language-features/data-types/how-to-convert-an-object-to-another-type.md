---
title: 'Porady: konwertowanie obiektu do innego typu w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Porady: konwertowanie obiektu do innego typu w Visual Basic
Możesz przekonwertować `Object` zmiennej na inny typ danych przy użyciu słowa kluczowego konwersji, takich jak [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konwertuje `Object` zmienną `Integer` i `String`.  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Jeśli wiesz, że zawartość `Object` są zmiennej typu danych, warto przekonwertować zmiennej typu danych. Jeśli będziesz nadal używać `Object` zmiennej, ponosisz albo *boxing* i *rozpakowującej* (dla typu wartości) lub *późne wiązanie* (dla typu odwołania). Te operacje wszystkie zająć dodatkowy czas wykonywania i upewnij wydajność wolniejszej.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object>  
 [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Konwertowanie pomiędzy ciągami a innymi typami](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
