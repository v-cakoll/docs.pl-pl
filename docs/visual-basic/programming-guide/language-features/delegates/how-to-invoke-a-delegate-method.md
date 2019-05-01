---
title: 'Instrukcje: Wywoływanie metody delegata (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: ac3e32010e7c20ba76e39915d694b11ab3a65d40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973332"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Instrukcje: Wywoływanie metody delegata (Visual Basic)
Ten przykład pokazuje, jak skojarzyć metodę z delegata, a następnie wywołać tę metodę przez delegat.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Utwórz delegata i procedur dopasowania  
  
1. Utwórz delegata, o nazwie `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2. Zadeklaruj klasę, która zawiera metody z taką samą sygnaturę jak delegat.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3. Zdefiniuj metodę, która tworzy wystąpienie obiektu delegowanego i wywołuje metodę skojarzoną z obiektem delegowanym przez wywołanie metody wbudowanej `Invoke` metody.  
  
    ```  
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
