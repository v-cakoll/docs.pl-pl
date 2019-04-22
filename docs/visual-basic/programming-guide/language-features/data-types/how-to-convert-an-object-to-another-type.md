---
title: 'Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 1e515c0f4ce8e787754c61a9b53d247fa93c49f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814383"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic
Możesz przekonwertować `Object` zmiennej na inny typ danych przy użyciu słowa kluczowego konwersji, takich jak [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
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
  
 Jeśli wiesz, że zawartość `Object` zmiennych są typu danych, zaleca się przekonwertować zmiennej tego typu danych. Jeśli będziesz nadal używać `Object` zmiennej, wiąże się z jednej *pakowania* i *Rozpakowywanie* (w przypadku typu wartości) lub *późnym wiązaniu* (dla typu odwołania). Te operacje wszystkie zająć dodatkowy czas wykonywania i wprowadź wydajność wolniej.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie do <xref:System?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Object>
- [Konwersje typów w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Konwersje jawne i niejawne](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Konwertowanie między ciągami a innymi typami danych](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Konwersje tablic](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Typy danych](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
