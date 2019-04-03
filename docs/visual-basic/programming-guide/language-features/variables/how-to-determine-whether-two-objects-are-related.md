---
title: 'Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: c4ff7c8e616c9126eae11a23e001c219dcbc0907
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819206"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)
Możesz porównać dwa obiekty przeznaczone do określenia relacji między klasami, z których są tworzone. <xref:System.Type.IsInstanceOfType%2A> Metody <xref:System.Type?displayProperty=nameWithType> klasy zwraca `True` czy określona klasa dziedziczy z klasy, czy bieżący typ jest interfejsem obsługiwanych przez określonej klasy.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Aby określić, jeśli jeden obiekt dziedziczy z klasy lub interfejsu innego obiektu.  
  
1.  W obiekcie Twoim zdaniem może być typu podstawowego, wywoływanie <xref:System.Object.GetType%2A> metody.  
  
2.  Na <xref:System.Type?displayProperty=nameWithType> obiektu zwróconego przez <xref:System.Object.GetType%2A>, wywołaj <xref:System.Type.IsInstanceOfType%2A> metody.  
  
3.  Na liście argumentów dla <xref:System.Type.IsInstanceOfType%2A>, określ obiekt Twoim zdaniem mogą być typu pochodnego.  
  
     <xref:System.Type.IsInstanceOfType%2A> Zwraca `True` jeśli jego typ argumentu dziedziczy z <xref:System.Type?displayProperty=nameWithType> typ obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa, czy jeden obiekt reprezentuje klasy pochodzącej od klasy innego obiektu.  
  
```  
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
  
 Należy pamiętać, nieoczekiwany umieszczania zmiennych dwóch obiektów w wywołaniu <xref:System.Type.IsInstanceOfType%2A>. Umożliwia generowanie tymczasowego obiektu typu podstawowego <xref:System.Type?displayProperty=nameWithType> klasy i tymczasowego obiektu typu pochodnego jest przekazywany jako argument do <xref:System.Type.IsInstanceOfType%2A> metody.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: Określanie, czy dwa obiekty są jednakowe](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
