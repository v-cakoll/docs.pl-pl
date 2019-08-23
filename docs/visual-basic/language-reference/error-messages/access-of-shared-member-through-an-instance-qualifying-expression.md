---
title: Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 3174d463744303e8c90ed0b2e1a4d86ed08fbcfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947697"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
Zmienna wystąpienia klasy lub struktury jest używana w celu uzyskania dostępu `Shared` do zmiennej, właściwości, procedury lub zdarzenia zdefiniowanego w tej klasie lub strukturze. To ostrzeżenie może również wystąpić, jeśli zmienna wystąpienia jest używana w celu uzyskania dostępu do niejawnie udostępnionej składowej klasy lub struktury, takiej jak stała lub Wyliczenie lub zagnieżdżona Klasa lub struktura.  
  
 Celem udostępniania elementu członkowskiego jest utworzenie tylko jednej kopii tego elementu członkowskiego i udostępnienie tej pojedynczej kopii każdemu wystąpieniu klasy lub struktury, w której jest zadeklarowana. Jest to zgodne z tym celem w celu uzyskania `Shared` dostępu do członka za pomocą nazwy jego klasy lub struktury, a nie za pomocą zmiennej, która przechowuje pojedyncze wystąpienie tej klasy lub struktury.  
  
 Uzyskiwanie dostępu do `Shared` elementuczłonkowskiegozapomocązmiennejwystąpieniamożeutrudnićzrozumieniekoduprzezzaciemnieniefaktu,żeelementczłonkowskijest.`Shared` Ponadto, jeśli taki dostęp jest częścią wyrażenia, które wykonuje inne czynności, takie jak `Function` procedura zwracająca wystąpienie udostępnionego elementu członkowskiego, Visual Basic pomija wyrażenie i wszelkie inne akcje, które w przeciwnym razie byłyby wykonywane.  
  
 Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj nazwy klasy lub struktury, która definiuje `Shared` element członkowski, aby uzyskać do niego dostęp, jak pokazano w poniższym przykładzie.  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
> Alert dotyczący efektów zakresu, gdy dwa elementy programistyczne mają taką samą nazwę. W poprzednim przykładzie, Jeśli zadeklarujesz wystąpienie przy użyciu `Dim testClass as testClass = Nothing`, kompilator traktuje `testClass.sayHello()` wywołanie jako dostęp metody za pomocą nazwy klasy i nie występuje ostrzeżenie.  
  
## <a name="see-also"></a>Zobacz także

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Zakres w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
