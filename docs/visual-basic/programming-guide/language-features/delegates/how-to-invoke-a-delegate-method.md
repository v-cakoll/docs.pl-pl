---
title: "Porady: wywoływanie metody delegata (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea94d4bb26e168667fd75c6928e52261f230c85e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Porady: wywoływanie metody delegata (Visual Basic)
W tym przykładzie pokazano, jak można skojarzyć metodę z delegata, a następnie wywołać tej metody za pomocą obiektu delegowanego.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Utwórz delegata i procedur dopasowania  
  
1.  Utworzenia delegata o nazwie `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  Deklarowanie klasy, która zawiera metodę o takiej samej sygnatury jak obiekt delegowany.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  Zdefiniuj metodę, która tworzy wystąpienie obiektu delegowanego i wywołuje metodę skojarzoną z obiektem delegowanym wywołując wbudowane `Invoke` metody.  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Delegate — instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Obiekty delegowane](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Aplikacje wielowątkowe](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
