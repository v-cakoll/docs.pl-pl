---
title: "Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; ukrywa zmienną w otaczającym bloku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="304bd-102">Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; ukrywa zmienną w otaczającym bloku</span><span class="sxs-lookup"><span data-stu-id="304bd-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="304bd-103">Zmienna ujęte w blok ma taką samą nazwę jak inny zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="304bd-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="304bd-104">**Identyfikator błędu:** BC30616</span><span class="sxs-lookup"><span data-stu-id="304bd-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="304bd-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="304bd-105">To correct this error</span></span>  
  
-   <span data-ttu-id="304bd-106">Zmień nazwę zmiennej w bloku objętego tak, aby nie jest taka sama jak innych zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="304bd-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="304bd-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="304bd-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="304bd-108">Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="304bd-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="304bd-109">Jeśli jest to możliwe, nazwę `Catch` zmienna bloku `ex` zamiast `e`.</span><span class="sxs-lookup"><span data-stu-id="304bd-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="304bd-110">Inne typowe źródło tego błędu jest próba dostępu zmienna lokalna zadeklarowana wewnątrz `Try` blok w oddzielnej `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="304bd-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="304bd-111">Aby rozwiązać ten problem, należy zadeklarować zmienną poza `Try...Catch...Finally` struktury.</span><span class="sxs-lookup"><span data-stu-id="304bd-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="304bd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="304bd-112">See Also</span></span>  
 [<span data-ttu-id="304bd-113">Try... CATCH... Finally — instrukcja</span><span class="sxs-lookup"><span data-stu-id="304bd-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="304bd-114">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="304bd-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
