---
title: "Wyrażenie cyklicznie wywołuje zawierającą je właściwość &#39; &lt;propertyname&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords: BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47de3c2d25336962168f01a4c8717274de7c9aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>Wyrażenie cyklicznie wywołuje zawierającą je właściwość &#39; &lt;propertyname&gt;&#39;
Instrukcja w `Set` procedury definicji właściwości przechowuje wartość w nazwie właściwości.  
  
 Zalecane podejście do przechowywania wartości właściwości jest określenie `Private` zmiennej w kontenerze właściwości i używać go zarówno `Get` i `Set` procedur. `Set` Procedury należy następnie przechowywać wartość przychodzącego w tym `Private` zmiennej.  
  
 `Get` Procedury zachowuje się jak `Function` procedury, można przypisać wartości do nazwy właściwości i zwrócić kontrolkę przez napotkania `End Get` instrukcji. Zalecane podejście jest jednak zawierać `Private` zmiennej jako wartości w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Set` Procedury zachowuje się jak `Sub` procedury, która nie zwraca wartości. W związku z tym nazwa procedura lub właściwość nie ma specjalnego znaczenia w `Set` procedura i nie można zapisać wartości do niego.  
  
 Poniższy przykład przedstawia podejście, które mogą być przyczyną tego błędu, następuje zalecane podejście.  
  
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
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42026  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Należy zmodyfikować definicję właściwości do użycia zalecane podejście, jak pokazano w poprzednim przykładzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury własności](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Set — instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
