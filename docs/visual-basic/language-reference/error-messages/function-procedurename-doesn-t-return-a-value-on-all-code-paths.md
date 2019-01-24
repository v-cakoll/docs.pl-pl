---
title: Funkcja &#39; &lt;nazwaprocedury&gt; &#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: b6cc5143aafb6c2554b183a1fc5fb3b1331ec5d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552193"
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="58ccf-102">Funkcja &#39; &lt;nazwaprocedury&gt; &#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu</span><span class="sxs-lookup"><span data-stu-id="58ccf-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="58ccf-103">Funkcja "\<nazwaprocedury >' nie zwraca wartości we wszystkich ścieżkach kodu.</span><span class="sxs-lookup"><span data-stu-id="58ccf-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="58ccf-104">Czy nie brakuje instrukcji "Return"?</span><span class="sxs-lookup"><span data-stu-id="58ccf-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="58ccf-105">A `Function` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kodu, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="58ccf-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="58ccf-106">Może zwracać wartość z zakresu od `Function` procedury w dowolnym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="58ccf-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="58ccf-107">Zawiera wartości w [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="58ccf-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="58ccf-108">Przypisz wartość do `Function` procedury nazwę, a następnie wykonaj `Exit Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="58ccf-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="58ccf-109">Przypisz wartość do `Function` procedury nazwę, a następnie wykonaj `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="58ccf-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="58ccf-110">Jeśli kontrola przechodzi do `Exit Function` lub `End Function` i nie przypisano żadnej wartości do nazwy procedury, procedura zwraca wartość domyślną typu danych zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="58ccf-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="58ccf-111">Aby uzyskać więcej informacji, zobacz "Zachowanie" w [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="58ccf-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="58ccf-112">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="58ccf-112">By default, this message is a warning.</span></span> <span data-ttu-id="58ccf-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="58ccf-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="58ccf-114">**Identyfikator błędu:** BC42105</span><span class="sxs-lookup"><span data-stu-id="58ccf-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58ccf-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="58ccf-115">To correct this error</span></span>  
  
-   <span data-ttu-id="58ccf-116">Sprawdź logikę przepływu sterowania i upewnij się, że przypisanie wartości przed każdej instrukcji, który powoduje, że wynik.</span><span class="sxs-lookup"><span data-stu-id="58ccf-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="58ccf-117">Ułatwia to zagwarantować, każdy zwracany z procedury zwraca wartość, jeśli zawsze używasz `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="58ccf-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="58ccf-118">Jeśli to zrobisz, ostatnią instrukcję przed `End Function` powinien być `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="58ccf-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ccf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58ccf-119">See also</span></span>
- [<span data-ttu-id="58ccf-120">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="58ccf-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="58ccf-121">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="58ccf-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="58ccf-122">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58ccf-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
