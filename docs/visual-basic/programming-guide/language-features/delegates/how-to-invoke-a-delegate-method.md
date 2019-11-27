---
title: 'Porady: wywoływanie metody delegata'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 520bacfbe6103490e0459cd5af149c1d55a8fce4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345263"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Porady: wywoływanie metody delegata (Visual Basic)

Ten przykład pokazuje, jak skojarzyć metodę z delegatem, a następnie wywołać tę metodę za pomocą delegata.

### <a name="create-the-delegate-and-matching-procedures"></a>Tworzenie procedur delegat i Matching

1. Utwórz delegat o nazwie `MySubDelegate`.

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

3. Zdefiniuj metodę, która tworzy wystąpienie delegata i wywołuje metodę skojarzoną z delegatem, wywołując wbudowaną metodę `Invoke`.

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
- [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Aplikacje wielowątkowe](../../../../standard/threading/using-threads-and-threading.md)
