---
title: 'Porady: określanie, czy dwa obiekty są powiązane (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2041f89ffd954e479046eb85c6dd82de1f8793ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649828"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a>Porady: określanie, czy dwa obiekty są powiązane (Visual Basic)
Możesz porównać dwa obiekty określenia relacji między klasami, z których są tworzone. <xref:System.Type.IsInstanceOfType%2A> Metody <xref:System.Type?displayProperty=nameWithType> klasy zwraca `True` czy określonej klasy dziedziczy z klasy, czy bieżący typ jest interfejsem obsługiwane przez określonej klasy.  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a>Aby określić, jeśli jeden obiekt dziedziczy z klasy lub interfejsu innego obiektu.  
  
1.  W obiekcie uważasz, że może być typu podstawowego, wywołaj <xref:System.Object.GetType%2A> metody.  
  
2.  Na <xref:System.Type?displayProperty=nameWithType> obiektu zwróconego przez <xref:System.Object.GetType%2A>, wywołaj <xref:System.Type.IsInstanceOfType%2A> metody.  
  
3.  Na liście argumentów dla <xref:System.Type.IsInstanceOfType%2A>, określ uważasz, że obiekt może być typu pochodnego.  
  
     <xref:System.Type.IsInstanceOfType%2A> Zwraca `True` jeśli jego typ argumentu dziedziczy <xref:System.Type?displayProperty=nameWithType> typu obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa, czy jeden obiekt reprezentuje klasę pochodzącą od klasy innego obiektu.  
  
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
  
 Należy pamiętać, nieoczekiwany umieszczania zmiennych dwóch obiektów w wywołaniu <xref:System.Type.IsInstanceOfType%2A>. Domniemana typ podstawowy jest używany do generowania <xref:System.Type?displayProperty=nameWithType> klasy i właściwego typu pochodnego jest przekazywany jako argument <xref:System.Type.IsInstanceOfType%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Instrukcje: określanie, czy dwa obiekty są jednakowe](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
