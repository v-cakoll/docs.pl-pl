---
title: 'Instrukcje: Wywołaj metodę delegata (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c2bdb65c9d060e854db3319e4aa5b2e93b9681af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629587"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Instrukcje: Wywołaj metodę delegata (Visual Basic)

Ten przykład pokazuje, jak skojarzyć metodę z delegatem, a następnie wywołać tę metodę za pomocą delegata.

### <a name="create-the-delegate-and-matching-procedures"></a>Tworzenie procedur delegat i Matching

1. Utwórz delegata o `MySubDelegate`nazwie.

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. Zadeklaruj klasę, która zawiera metodę o tym samym podpisie co delegat.

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. Zdefiniuj metodę, która tworzy wystąpienie delegata i wywołuje metodę skojarzoną z delegatem przez wywołanie `Invoke` metody wbudowanej.

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a>Zobacz także

- [Delegate, instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Aplikacje wielowątkowe](../../../../standard/threading/using-threads-and-threading.md)
