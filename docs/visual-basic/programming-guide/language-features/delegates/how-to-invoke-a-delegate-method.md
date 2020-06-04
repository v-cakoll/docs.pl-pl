---
title: 'Porady: wywoływanie metody delegata'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: f319727c007b93c7b334af0598f1b9f7c034144d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410724"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Porady: wywoływanie metody delegata (Visual Basic)

Ten przykład pokazuje, jak skojarzyć metodę z delegatem, a następnie wywołać tę metodę za pomocą delegata.

### <a name="create-the-delegate-and-matching-procedures"></a>Tworzenie procedur delegat i Matching

1. Utwórz delegata o nazwie `MySubDelegate` .

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

3. Zdefiniuj metodę, która tworzy wystąpienie delegata i wywołuje metodę skojarzoną z delegatem przez wywołanie metody wbudowanej `Invoke` .

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a>Zobacz też

- [Delegate — Instrukcja](../../../language-reference/statements/delegate-statement.md)
- [Delegaci](index.md)
- [Zdarzenia](../events/index.md)
- [Aplikacje wielowątkowe](../../../../standard/threading/using-threads-and-threading.md)
