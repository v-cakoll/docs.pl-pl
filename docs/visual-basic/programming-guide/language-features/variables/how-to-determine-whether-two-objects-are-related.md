---
title: 'Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626556"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)

Można porównać dwa obiekty, aby określić relację, jeśli istnieje, między klasami, z których zostały utworzone. <xref:System.Type.IsInstanceOfType%2A> Metoda klasy<xref:System.Type?displayProperty=nameWithType> zwraca ,jeśliokreślonaklasadziedziczyzbieżącejklasylubjeślibieżącytypjest`True` interfejsem obsługiwanym przez określoną klasę.

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Aby określić, czy jeden obiekt dziedziczy z klasy lub interfejsu innego obiektu

1. Na obiekcie, który sądzisz, może być typu podstawowego, wywołaj <xref:System.Object.GetType%2A> metodę.

2. Dla obiektu zwróconego przez <xref:System.Object.GetType%2A>, wywołaj <xref:System.Type.IsInstanceOfType%2A> metodę. <xref:System.Type?displayProperty=nameWithType>

3. Na liście argumentów dla <xref:System.Type.IsInstanceOfType%2A>Określ obiekt, który może być typem pochodnym.

    <xref:System.Type.IsInstanceOfType%2A>zwraca `True` wartość, jeśli jej typ argumentu dziedziczy <xref:System.Type?displayProperty=nameWithType> z typu obiektu.

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

Zwróć uwagę na nieoczekiwane rozmieszczenie dwóch zmiennych obiektów w wywołaniu <xref:System.Type.IsInstanceOfType%2A>. Przypuszczalny typ podstawowy jest używany do generowania <xref:System.Type?displayProperty=nameWithType> klasy, a typ pochodny jest przenoszona jako argument <xref:System.Type.IsInstanceOfType%2A> do metody.

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: Określanie, czy dwa obiekty są identyczne](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
