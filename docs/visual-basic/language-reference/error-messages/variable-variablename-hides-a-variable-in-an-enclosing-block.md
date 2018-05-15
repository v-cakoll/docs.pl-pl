---
title: Zmienna &#39; &lt;nazwa_zmiennej&gt; &#39; ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="70b5e-102">Zmienna &#39; &lt;nazwa_zmiennej&gt; &#39; ukrywa zmienną w otaczającym bloku</span><span class="sxs-lookup"><span data-stu-id="70b5e-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="70b5e-103">Zmienna ujęte w blok ma taką samą nazwę jak inny zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="70b5e-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="70b5e-104">**Identyfikator błędu:** BC30616</span><span class="sxs-lookup"><span data-stu-id="70b5e-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70b5e-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="70b5e-105">To correct this error</span></span>  
  
-   <span data-ttu-id="70b5e-106">Zmień nazwę zmiennej w bloku objętego tak, aby nie jest taka sama jak innych zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="70b5e-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="70b5e-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="70b5e-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="70b5e-108">Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="70b5e-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="70b5e-109">Jeśli jest to możliwe, nazwę `Catch` zmienna bloku `ex` zamiast `e`.</span><span class="sxs-lookup"><span data-stu-id="70b5e-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="70b5e-110">Inne typowe źródło tego błędu jest próba dostępu zmienna lokalna zadeklarowana wewnątrz `Try` blok w oddzielnej `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="70b5e-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="70b5e-111">Aby rozwiązać ten problem, należy zadeklarować zmienną poza `Try...Catch...Finally` struktury.</span><span class="sxs-lookup"><span data-stu-id="70b5e-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b5e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70b5e-112">See Also</span></span>  
 [<span data-ttu-id="70b5e-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="70b5e-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="70b5e-114">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="70b5e-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
