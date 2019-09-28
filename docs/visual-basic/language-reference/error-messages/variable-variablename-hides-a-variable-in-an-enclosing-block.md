---
title: Zmienna „<variablename>” ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592064"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="054db-102">Zmienna "\<variablename >" ukrywa zmienną w otaczającym bloku</span><span class="sxs-lookup"><span data-stu-id="054db-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="054db-103">Zmienna ujęta w bloku ma taką samą nazwę jak inna zmienna lokalna.</span><span class="sxs-lookup"><span data-stu-id="054db-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="054db-104">**Identyfikator błędu:** BC30616</span><span class="sxs-lookup"><span data-stu-id="054db-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="054db-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="054db-105">To correct this error</span></span>  
  
- <span data-ttu-id="054db-106">Zmień nazwę zmiennej w załączonym bloku, tak aby nie była taka sama jak jakakolwiek inna zmienna lokalna.</span><span class="sxs-lookup"><span data-stu-id="054db-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="054db-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="054db-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="054db-108">Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="054db-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="054db-109">W takim przypadku należy nazwać zmienną bloku `Catch` `ex`, a nie `e`.</span><span class="sxs-lookup"><span data-stu-id="054db-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="054db-110">Innym wspólnym źródłem tego błędu jest próba uzyskania dostępu do zmiennej lokalnej zadeklarowanej w bloku `Try` w osobnym bloku `Catch`.</span><span class="sxs-lookup"><span data-stu-id="054db-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="054db-111">Aby rozwiązać ten krok, należy zadeklarować zmienną poza strukturą `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="054db-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054db-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="054db-112">See also</span></span>

- [<span data-ttu-id="054db-113">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="054db-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="054db-114">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="054db-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
