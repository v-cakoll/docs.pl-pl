---
title: Wyrażenie cyklicznie wywołuje zawierającą właściwość „<propertyname>”
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: e3a9f4cf2f4105d2c449813bf0c593860df7d1f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409533"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>Wyrażenie cyklicznie wywołuje zawierającą właściwość „\<propertyname>”
Instrukcja w `Set` procedurze definicji właściwości przechowuje wartość w nazwie właściwości.  
  
 Zalecanym podejściem do przechowywania wartości właściwości jest definiowanie `Private` zmiennej w kontenerze właściwości i użycie jej w `Get` `Set` procedurach i. `Set`Procedura powinna następnie przechowywać wartość przychodzącą w tej `Private` zmiennej.  
  
 `Get`Procedura zachowuje się jak `Function` procedura, dlatego może przypisywać wartości do nazwy właściwości i kontroli powrotu przez napotkanie `End Get` instrukcji. Zalecanym podejściem jest jednak uwzględnienie `Private` zmiennej jako wartości w [instrukcji return](../statements/return-statement.md).  
  
 `Set`Procedura zachowuje się jak `Sub` procedura, która nie zwraca wartości. W związku z tym, procedura lub nazwa właściwości nie ma specjalnego znaczenia w ramach `Set` procedury i nie można zapisać w niej wartości.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Procedury własności](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property — Instrukcja](../statements/property-statement.md)
- [Set — Instrukcja](../statements/set-statement.md)
