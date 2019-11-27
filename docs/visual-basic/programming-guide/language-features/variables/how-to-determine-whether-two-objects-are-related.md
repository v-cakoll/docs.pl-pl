---
title: 'Porady: określanie, czy dwa obiekty są powiązane'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: b3f5fc017166ba9cf28359db5de850c81b73bd69
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348631"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Porady: określanie, czy dwa obiekty są powiązane (Visual Basic)

Można porównać dwa obiekty, aby określić relację, jeśli istnieje, między klasami, z których zostały utworzone. Metoda <xref:System.Type.IsInstanceOfType%2A> klasy <xref:System.Type?displayProperty=nameWithType> zwraca `True`, jeśli określona klasa dziedziczy z bieżącej klasy lub jeśli bieżący typ jest interfejsem obsługiwanym przez określoną klasę.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Aby określić, czy jeden obiekt dziedziczy z klasy lub interfejsu innego obiektu

1. Na obiekcie, który sądzisz, może być typu podstawowego, wywołaj metodę <xref:System.Object.GetType%2A>.

2. Dla obiektu <xref:System.Type?displayProperty=nameWithType> zwróconego przez <xref:System.Object.GetType%2A>Wywołaj metodę <xref:System.Type.IsInstanceOfType%2A>.

3. Na liście argumentów dla <xref:System.Type.IsInstanceOfType%2A>Określ obiekt, który może być typem pochodnym.

    <xref:System.Type.IsInstanceOfType%2A> zwraca `True`, jeśli jego typ jest Dziedziczony z typu obiektu <xref:System.Type?displayProperty=nameWithType>.

## <a name="example"></a>Przykład
 Poniższy przykład określa, czy jeden obiekt reprezentuje klasę pochodzącą od klasy innego obiektu.

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

Zwróć uwagę na nieoczekiwane rozmieszczenie dwóch zmiennych obiektów w wywołaniu do <xref:System.Type.IsInstanceOfType%2A>. Przypuszczalny typ podstawowy jest używany do generowania klasy <xref:System.Type?displayProperty=nameWithType>, a typ pochodny jest przenoszona jako argument do metody <xref:System.Type.IsInstanceOfType%2A>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: określanie, czy dwa obiekty są jednakowe](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
