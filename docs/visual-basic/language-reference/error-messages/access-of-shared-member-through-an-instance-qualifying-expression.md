---
title: Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 035882b60c90d9a6141ad0d34b4c40682e0c32a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588986"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Dostęp członka udostępnionego, przez wystąpienie; wyrażenie kwalifikujące nie zostanie oszacowane
Zmienna wystąpienia klasy lub struktury jest używana do dostępu `Shared` zmienną, właściwością, procedura lub zdarzeń zdefiniowanych w tej klasy lub struktury. To ostrzeżenie może również wystąpić, jeśli zmienna wystąpienia są używane do uzyskania dostępu niejawnie udostępnionego elementu członkowskiego klasy lub struktury, takich jak stałą lub wyliczenia, lub zagnieżdżone klasy lub struktury.  
  
 Udostępnianie element członkowski ma na celu tworzenie tylko jednej kopii tego członka i udostępnić tym pojedynczej kopii każdego wystąpienia klasy lub struktury, w którym jest zadeklarowany. Jest ona zgodna z dostępu do tego celu `Shared` elementu członkowskiego za pomocą nazwy klasy lub struktury, a nie za pośrednictwem zmiennej, która przechowuje poszczególne wystąpienia tej klasy lub struktury.  
  
 Uzyskiwanie dostępu do `Shared` użytkownika za pomocą zmienna wystąpienia może utrudnić kodu bardziej zrozumiałe przesłaniania fakt, że element członkowski jest `Shared`. Ponadto, jeśli taki dostęp jest częścią wyrażenia wykonująca inne akcje, takie jak `Function` procedury, która zwraca wystąpienie klasy udostępnionego elementu członkowskiego, Visual Basic pomija wyrażenie i inne akcje, w przeciwnym razie będzie wykonywać.  
  
 Aby uzyskać więcej informacji i przykład zobacz [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj nazwy klasy lub struktury, który definiuje `Shared` elementu członkowskiego dostępu do niego, jak pokazano w poniższym przykładzie.  
  
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
>  Być alert dotyczący skutków zakresu, jeśli dwa elementy programowania mają taką samą nazwę. W poprzednim przykładzie, jeśli Zadeklaruj wystąpienie za pomocą `Dim testClass as testClass = Nothing`, kompilator traktuje wywołanie `testClass.sayHello()` jako dostępu metody za pomocą nazwy klasy i ostrzeżenie nie występuje.  
  
## <a name="see-also"></a>Zobacz też  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Zakres w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
