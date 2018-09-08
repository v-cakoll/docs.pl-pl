---
title: 'Porady: wywoływanie metody delegata (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c50a32d300aaf52efe0c55cef69d5793a98305ac
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129219"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="d33ad-102">Porady: wywoływanie metody delegata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d33ad-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="d33ad-103">Ten przykład pokazuje, jak skojarzyć metodę z delegata, a następnie wywołać tę metodę przez delegat.</span><span class="sxs-lookup"><span data-stu-id="d33ad-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="d33ad-104">Utwórz delegata i procedur dopasowania</span><span class="sxs-lookup"><span data-stu-id="d33ad-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="d33ad-105">Utwórz delegata, o nazwie `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="d33ad-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="d33ad-106">Zadeklaruj klasę, która zawiera metody z taką samą sygnaturę jak delegat.</span><span class="sxs-lookup"><span data-stu-id="d33ad-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="d33ad-107">Zdefiniuj metodę, która tworzy wystąpienie obiektu delegowanego i wywołuje metodę skojarzoną z obiektem delegowanym przez wywołanie metody wbudowanej `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="d33ad-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d33ad-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d33ad-108">See also</span></span>

- [<span data-ttu-id="d33ad-109">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d33ad-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
- [<span data-ttu-id="d33ad-110">Delegaci</span><span class="sxs-lookup"><span data-stu-id="d33ad-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
- [<span data-ttu-id="d33ad-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d33ad-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
- [<span data-ttu-id="d33ad-112">Aplikacje wielowątkowe</span><span class="sxs-lookup"><span data-stu-id="d33ad-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
