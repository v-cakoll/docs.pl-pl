---
title: Użycie zmiennej iteracyjnej w wyrażeniu lambda może spowodować nieoczekiwane wyniki
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: aa3e1d6281af22b301a4697b265ed3fbf23e3de4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373917"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>Użycie zmiennej iteracyjnej w wyrażeniu lambda może spowodować nieoczekiwane wyniki
Użycie zmiennej iteracji w wyrażeniu lambda może mieć nieoczekiwane wyniki. Zamiast tego należy utworzyć zmienną lokalną wewnątrz pętli i przypisać ją do wartości zmiennej iteracji.  
  
 To ostrzeżenie jest wyświetlane, gdy w wyrażeniu lambda, który jest zadeklarowany wewnątrz pętli, jest używana zmienna iteracji pętli. Na przykład poniższy przykład powoduje wyświetlenie ostrzeżenia.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 Poniższy przykład pokazuje nieoczekiwane wyniki, które mogą wystąpić.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 `For`Pętla tworzy tablicę wyrażeń lambda, z których każdy zwraca wartość zmiennej iteracji pętli `i` . Gdy wyrażenia lambda są oceniane w `For Each` pętli, może się zdarzyć, że będą widoczne wartości 0, 1, 2, 3 i 4 `i` `For` . Zamiast tego zobaczysz końcową wartość `i` wyświetlaną pięć razy:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42324  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Przypisz wartość zmiennej iteracji do zmiennej lokalnej i Użyj zmiennej lokalnej w wyrażeniu lambda.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
