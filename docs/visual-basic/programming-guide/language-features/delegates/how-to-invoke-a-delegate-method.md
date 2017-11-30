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
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="3e2e7-102">Porady: wywoływanie metody delegata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e2e7-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="3e2e7-103">W tym przykładzie pokazano, jak można skojarzyć metodę z delegata, a następnie wywołać tej metody za pomocą obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="3e2e7-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="3e2e7-104">Utwórz delegata i procedur dopasowania</span><span class="sxs-lookup"><span data-stu-id="3e2e7-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="3e2e7-105">Utworzenia delegata o nazwie `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="3e2e7-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="3e2e7-106">Deklarowanie klasy, która zawiera metodę o takiej samej sygnatury jak obiekt delegowany.</span><span class="sxs-lookup"><span data-stu-id="3e2e7-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="3e2e7-107">Zdefiniuj metodę, która tworzy wystąpienie obiektu delegowanego i wywołuje metodę skojarzoną z obiektem delegowanym wywołując wbudowane `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="3e2e7-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3e2e7-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e2e7-108">See Also</span></span>  
 [<span data-ttu-id="3e2e7-109">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3e2e7-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="3e2e7-110">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="3e2e7-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="3e2e7-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3e2e7-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="3e2e7-112">Aplikacje wielowątkowe</span><span class="sxs-lookup"><span data-stu-id="3e2e7-112">Multithreaded Applications</span></span>](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
