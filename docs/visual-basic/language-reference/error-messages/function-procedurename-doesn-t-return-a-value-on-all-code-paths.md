---
title: Funkcja „<procedurename>" nie zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: badcfea4f24ba3858071e02ba47b8f77ab557f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802381"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="161fa-102">Funkcja "\<nazwaprocedury >' nie zwraca wartości we wszystkich ścieżkach kodu</span><span class="sxs-lookup"><span data-stu-id="161fa-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="161fa-103">Funkcja "\<nazwaprocedury >' nie zwraca wartości we wszystkich ścieżkach kodu.</span><span class="sxs-lookup"><span data-stu-id="161fa-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="161fa-104">Czy nie brakuje instrukcji "Return"?</span><span class="sxs-lookup"><span data-stu-id="161fa-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="161fa-105">A `Function` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kodu, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="161fa-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="161fa-106">Może zwracać wartość z zakresu od `Function` procedury w dowolnym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="161fa-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="161fa-107">Zawiera wartości w [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="161fa-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="161fa-108">Przypisz wartość do `Function` procedury nazwę, a następnie wykonaj `Exit Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="161fa-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="161fa-109">Przypisz wartość do `Function` procedury nazwę, a następnie wykonaj `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="161fa-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="161fa-110">Jeśli kontrola przechodzi do `Exit Function` lub `End Function` i nie przypisano żadnej wartości do nazwy procedury, procedura zwraca wartość domyślną typu danych zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="161fa-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="161fa-111">Aby uzyskać więcej informacji, zobacz 'Zachowanie' w [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="161fa-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="161fa-112">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="161fa-112">By default, this message is a warning.</span></span> <span data-ttu-id="161fa-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="161fa-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="161fa-114">**Identyfikator błędu:** BC42105</span><span class="sxs-lookup"><span data-stu-id="161fa-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="161fa-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="161fa-115">To correct this error</span></span>  
  
- <span data-ttu-id="161fa-116">Sprawdź logikę przepływu sterowania i upewnij się, że przypisanie wartości przed każdej instrukcji, który powoduje, że wynik.</span><span class="sxs-lookup"><span data-stu-id="161fa-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="161fa-117">Ułatwia to zagwarantować, każdy zwracany z procedury zwraca wartość, jeśli zawsze używasz `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="161fa-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="161fa-118">Jeśli to zrobisz, ostatnią instrukcję przed `End Function` powinien być `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="161fa-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161fa-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="161fa-119">See also</span></span>

- [<span data-ttu-id="161fa-120">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="161fa-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="161fa-121">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="161fa-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="161fa-122">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="161fa-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
