---
title: Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 311f4c025072162e0cfb6b87587f8602d33fcd19
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646867"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
Zmienna wystąpienia klasy lub struktury jest używana, aby uzyskać dostęp do `Shared` zmiennej, właściwość, procedura lub zdarzenia, zdefiniowany w tej klasy lub struktury. To ostrzeżenie może również wystąpić, jeśli zmienną instance umożliwia dostęp do niejawnie udostępnionego elementu członkowskiego klasy lub struktury, takiej jak stała wyliczenia, lub zagnieżdżona klasa lub Struktura.  
  
 Udostępnianie członka ma na celu tworzenie tylko jednej kopii tego elementu członkowskiego i udostępnić pojedynczej kopii każdego wystąpienia klasy lub struktury, w którym jest zdeklarowana. Jest ona zgodna z dostępu do tego celu `Shared` elementu członkowskiego za pośrednictwem nazwy klasy lub struktury, a nie za pomocą zmienna, która zawiera poszczególne wystąpienia tej klasy lub struktury.  
  
 Uzyskiwanie dostępu do `Shared` elementu członkowskiego przez zmienną instance, może uczynić kod trudniejszy do zrozumienia przez fakt, że składowa jest przesłaniania `Shared`. Ponadto, jeśli taki dostęp jest częścią wyrażenia wykonująca innych działań, takich jak `Function` procedury, która zwraca wystąpienie do udostępnionej składowej, Visual Basic pomija wyrażenie i innych akcji, w przeciwnym razie wykona.  
  
 Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj nazwy klasy lub struktury, która definiuje `Shared` członka do niego dostęp, jak pokazano w poniższym przykładzie.  
  
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
>  Być alert dotyczący skutków zakresu, jeśli dwa elementy programowania mają taką samą nazwę. W poprzednim przykładzie, jeśli zadeklarować wystąpienia przy użyciu `Dim testClass as testClass = Nothing`, kompilator traktuje wywołanie `testClass.sayHello()` po wystąpieniu dostępu metody przy użyciu nazwy klasy i bez ostrzeżenia.  
  
## <a name="see-also"></a>Zobacz także

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Zakres w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
