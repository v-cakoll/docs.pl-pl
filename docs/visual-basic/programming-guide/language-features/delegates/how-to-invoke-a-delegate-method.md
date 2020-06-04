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
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="20fcc-102">Porady: wywoływanie metody delegata (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20fcc-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>

<span data-ttu-id="20fcc-103">Ten przykład pokazuje, jak skojarzyć metodę z delegatem, a następnie wywołać tę metodę za pomocą delegata.</span><span class="sxs-lookup"><span data-stu-id="20fcc-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>

### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="20fcc-104">Tworzenie procedur delegat i Matching</span><span class="sxs-lookup"><span data-stu-id="20fcc-104">Create the delegate and matching procedures</span></span>

1. <span data-ttu-id="20fcc-105">Utwórz delegata o nazwie `MySubDelegate` .</span><span class="sxs-lookup"><span data-stu-id="20fcc-105">Create a delegate named `MySubDelegate`.</span></span>

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. <span data-ttu-id="20fcc-106">Zadeklaruj klasę, która zawiera metodę o tym samym podpisie co delegat.</span><span class="sxs-lookup"><span data-stu-id="20fcc-106">Declare a class that contains a method with the same signature as the delegate.</span></span>

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. <span data-ttu-id="20fcc-107">Zdefiniuj metodę, która tworzy wystąpienie delegata i wywołuje metodę skojarzoną z delegatem przez wywołanie metody wbudowanej `Invoke` .</span><span class="sxs-lookup"><span data-stu-id="20fcc-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>

    ```vb
    Protected Sub DelegateTest()
        Dim c1 As New class1
        ' Create an instance of the delegate.
        Dim msd As MySubDelegate = AddressOf c1.Sub1
        ' Call the method.
        msd.Invoke(10)
    End Sub
    ```

## <a name="see-also"></a><span data-ttu-id="20fcc-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20fcc-108">See also</span></span>

- [<span data-ttu-id="20fcc-109">Delegate — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="20fcc-109">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="20fcc-110">Delegaci</span><span class="sxs-lookup"><span data-stu-id="20fcc-110">Delegates</span></span>](index.md)
- [<span data-ttu-id="20fcc-111">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="20fcc-111">Events</span></span>](../events/index.md)
- [<span data-ttu-id="20fcc-112">Aplikacje wielowątkowe</span><span class="sxs-lookup"><span data-stu-id="20fcc-112">Multithreaded Applications</span></span>](../../../../standard/threading/using-threads-and-threading.md)
