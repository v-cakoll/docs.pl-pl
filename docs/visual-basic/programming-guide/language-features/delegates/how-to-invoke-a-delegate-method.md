---
title: 'Porady: wywoływanie metody delegata (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: aca87dd9fa1990d44c99aab7753f2fd7d508adc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646955"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="1b01e-102">Porady: wywoływanie metody delegata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b01e-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="1b01e-103">W tym przykładzie pokazano, jak można skojarzyć metodę z delegata, a następnie wywołać tej metody za pomocą obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="1b01e-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="1b01e-104">Utwórz delegata i procedur dopasowania</span><span class="sxs-lookup"><span data-stu-id="1b01e-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="1b01e-105">Utworzenia delegata o nazwie `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="1b01e-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="1b01e-106">Deklarowanie klasy, która zawiera metodę o takiej samej sygnatury jak obiekt delegowany.</span><span class="sxs-lookup"><span data-stu-id="1b01e-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="1b01e-107">Zdefiniuj metodę, która tworzy wystąpienie obiektu delegowanego i wywołuje metodę skojarzoną z obiektem delegowanym wywołując wbudowane `Invoke` metody.</span><span class="sxs-lookup"><span data-stu-id="1b01e-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1b01e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b01e-108">See Also</span></span>  
 [<span data-ttu-id="1b01e-109">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b01e-109">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="1b01e-110">Delegaci</span><span class="sxs-lookup"><span data-stu-id="1b01e-110">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="1b01e-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1b01e-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="1b01e-112">Aplikacje wielowątkowe</span><span class="sxs-lookup"><span data-stu-id="1b01e-112">Multithreaded Applications</span></span>](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
