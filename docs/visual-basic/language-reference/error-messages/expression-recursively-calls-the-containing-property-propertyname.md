---
title: Wyrażenie cyklicznie wywołuje zawierającą właściwość „<propertyname>”
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 93d02618ff19f431b3602e74478337f6918df289
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665165"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>Wyrażenie cyklicznie wywołuje zawierającą właściwość "\<propertyname >"
Instrukcja w `Set` procedury definicji właściwości przechowuje wartość do nazwy właściwości.  
  
 Zalecane podejście do przechowywania wartości właściwości jest zdefiniowanie `Private` zmiennej w kontenerze właściwości i używać go w obu `Get` i `Set` procedur. `Set` Procedury należy następnie przechowywać wartość przychodzącego w tym `Private` zmiennej.  
  
 `Get` Procedury zachowuje się jak `Function` procedury, dzięki czemu można przypisać wartości do danej nazwy właściwości i przywrócenie kontroli przez napotkania `End Get` instrukcji. Zalecanym podejściem jest jednak obejmują `Private` zmiennej jako wartości w [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Set` Procedury zachowuje się jak `Sub` procedury, która nie zwraca wartości. W związku z tym, nazwa procedura lub właściwość nie ma specjalnego znaczenia w ramach `Set` procedury, a nie można zapisać wartości do niego.  
  
 Poniższy przykład przedstawia podejście, które może być przyczyną tego błędu, a następnie zalecane podejście.  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42026  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Należy zmodyfikować definicję właściwości do użycia zalecane podejście, jak pokazano w powyższym przykładzie.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
