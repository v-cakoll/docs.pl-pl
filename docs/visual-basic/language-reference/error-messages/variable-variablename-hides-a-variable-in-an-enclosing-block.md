---
title: Zmienna „<variablename>” ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 68ec1aac7ee8d292e2a433e0fb35039d4fb317b4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278502"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="4fe14-102">Zmienna "\<nazwa_zmiennej >" ukrywa zmienną w otaczającym bloku</span><span class="sxs-lookup"><span data-stu-id="4fe14-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="4fe14-103">Zmienna ujęte w blok ma taką samą nazwę jak inny zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="4fe14-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="4fe14-104">**Identyfikator błędu:** BC30616</span><span class="sxs-lookup"><span data-stu-id="4fe14-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4fe14-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4fe14-105">To correct this error</span></span>  
  
-   <span data-ttu-id="4fe14-106">Zmień nazwę zmiennej w bloku ujęty, tak aby nie była taka sama jak inne zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="4fe14-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="4fe14-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4fe14-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="4fe14-108">Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4fe14-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="4fe14-109">Jeśli jest to możliwe, nadaj nazwę `Catch` zmienna bloku `ex` zamiast `e`.</span><span class="sxs-lookup"><span data-stu-id="4fe14-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="4fe14-110">Wspólne źródło innego wystąpienia tego błędu jest próba dostępu zmienna lokalna zadeklarowana wewnątrz `Try` blok w osobnym `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="4fe14-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="4fe14-111">Aby rozwiązać ten problem, należy zadeklarować zmiennej poza `Try...Catch...Finally` struktury.</span><span class="sxs-lookup"><span data-stu-id="4fe14-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe14-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4fe14-112">See also</span></span>
- [<span data-ttu-id="4fe14-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4fe14-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="4fe14-114">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="4fe14-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
