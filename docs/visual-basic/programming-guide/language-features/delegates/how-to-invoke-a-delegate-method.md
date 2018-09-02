---
title: 'Porady: wywoływanie metody delegata (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 9fea3ddbc9fb553041671713a64e4b866ee38b50
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392441"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="77bcb-102">Porady: wywoływanie metody delegata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77bcb-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="77bcb-103">Ten przykład pokazuje, jak skojarzyć metodę z delegata, a następnie wywołać tę metodę przez delegat.</span><span class="sxs-lookup"><span data-stu-id="77bcb-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="77bcb-104">Utwórz delegata i procedur dopasowania</span><span class="sxs-lookup"><span data-stu-id="77bcb-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="77bcb-105">Utwórz delegata, o nazwie `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="77bcb-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="77bcb-106">Zadeklaruj klasę, która zawiera metody z taką samą sygnaturę jak delegat.</span><span class="sxs-lookup"><span data-stu-id="77bcb-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="77bcb-107">Zdefiniuj metodę, która tworzy wystąpienie obiektu delegowanego i wywołuje metodę skojarzoną z obiektem delegowanym przez wywołanie metody wbudowanej `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="77bcb-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77bcb-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77bcb-108">See Also</span></span>  
 [<span data-ttu-id="77bcb-109">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="77bcb-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="77bcb-110">Delegaci</span><span class="sxs-lookup"><span data-stu-id="77bcb-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="77bcb-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="77bcb-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="77bcb-112">Aplikacje wielowątkowe</span><span class="sxs-lookup"><span data-stu-id="77bcb-112">Multithreaded Applications</span></span>](https://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
