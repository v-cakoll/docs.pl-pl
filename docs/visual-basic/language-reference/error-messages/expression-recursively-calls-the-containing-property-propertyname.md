---
title: Wyrażenie cyklicznie wywołuje zawierającą właściwość „<propertyname>”
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698564"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>Wyrażenie cyklicznie wywołuje zawierającą właściwość "\<propertyname >"
Instrukcja w procedurze `Set` definicji właściwości przechowuje wartość w nazwie właściwości.  
  
 Zalecanym podejściem do przechowywania wartości właściwości jest Definiowanie zmiennej `Private` w kontenerze właściwości i użycie jej w procedurach `Get` i `Set`. Procedura `Set` powinna następnie przechowywać wartość przychodzącą w tej zmiennej `Private`.  
  
 Procedura `Get` zachowuje się jak procedura `Function`, więc może przypisywać wartości do nazwy właściwości i kontroli powrotu przez napotkanie instrukcji `End Get`. Zalecanym podejściem jest jednak uwzględnienie zmiennej `Private` jako wartości w [instrukcji return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Procedura `Set` zachowuje się jak procedura `Sub`, która nie zwraca wartości. W związku z tym, nazwa procedury lub właściwości nie ma specjalnego znaczenia w ramach procedury `Set` i nie można zapisać w niej wartości.  
  
 Poniższy przykład ilustruje podejście, które może spowodować wystąpienie tego błędu, a następnie zalecane podejście.  
  
```vb  
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
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42026  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zapisz definicję właściwości, aby użyć zalecanego podejścia, jak pokazano w powyższym przykładzie.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury właściwości](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set, instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
