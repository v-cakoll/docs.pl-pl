---
title: Funkcja „<procedurename>" nie zwraca wartości we wszystkich ścieżkach kodu
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: edb2195f4e83c2315aa929936aff8af88ca8556c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374138"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="73b8c-102">Funkcja „\<procedurename>" nie zwraca wartości we wszystkich ścieżkach kodu</span><span class="sxs-lookup"><span data-stu-id="73b8c-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="73b8c-103">Funkcja " \<procedurename> " nie zwraca wartości we wszystkich ścieżkach kodu.</span><span class="sxs-lookup"><span data-stu-id="73b8c-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="73b8c-104">Czy brakuje instrukcji "return"?</span><span class="sxs-lookup"><span data-stu-id="73b8c-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="73b8c-105">`Function`Procedura zawiera co najmniej jedną możliwą ścieżkę za pomocą kodu, który nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="73b8c-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="73b8c-106">Można zwrócić wartość z `Function` procedury w dowolny z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="73b8c-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="73b8c-107">Dołącz wartość do [instrukcji return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="73b8c-107">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="73b8c-108">Przypisz wartość do `Function` nazwy procedury, a następnie wykonaj `Exit Function` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="73b8c-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="73b8c-109">Przypisz wartość do `Function` nazwy procedury, a następnie wykonaj `End Function` instrukcję.</span><span class="sxs-lookup"><span data-stu-id="73b8c-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="73b8c-110">Jeśli kontrola przechodzi do `Exit Function` lub `End Function` i nie przypisano żadnej wartości do nazwy procedury, procedura zwraca wartość domyślną zwracanego typu danych.</span><span class="sxs-lookup"><span data-stu-id="73b8c-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="73b8c-111">Aby uzyskać więcej informacji, zobacz "zachowanie" w [instrukcji funkcji](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="73b8c-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="73b8c-112">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="73b8c-112">By default, this message is a warning.</span></span> <span data-ttu-id="73b8c-113">Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="73b8c-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="73b8c-114">**Identyfikator błędu:** BC42105</span><span class="sxs-lookup"><span data-stu-id="73b8c-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73b8c-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="73b8c-115">To correct this error</span></span>  
  
- <span data-ttu-id="73b8c-116">Sprawdź logikę przepływu sterowania i upewnij się, że przypiszesz wartość przed każdą instrukcją, która powoduje zwrócenie.</span><span class="sxs-lookup"><span data-stu-id="73b8c-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="73b8c-117">Łatwiej jest zagwarantować, że każde zwrócenie z procedury zwraca wartość, jeśli zawsze używasz `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="73b8c-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="73b8c-118">Jeśli to zrobisz, ostatnią instrukcją przed `End Function` powinien być `Return` instrukcja.</span><span class="sxs-lookup"><span data-stu-id="73b8c-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b8c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73b8c-119">See also</span></span>

- [<span data-ttu-id="73b8c-120">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="73b8c-120">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="73b8c-121">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="73b8c-121">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="73b8c-122">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73b8c-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
