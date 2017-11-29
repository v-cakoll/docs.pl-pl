---
title: "Funkcja &#39; &lt;nazwaprocedury&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords: BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="c9801-102">Funkcja &#39; &lt;nazwaprocedury&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu</span><span class="sxs-lookup"><span data-stu-id="c9801-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="c9801-103">Funkcja "\<nazwaprocedury >' nie zwraca wartości we wszystkich ścieżkach kodu.</span><span class="sxs-lookup"><span data-stu-id="c9801-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="c9801-104">Czy nie brakuje instrukcji "Return"?</span><span class="sxs-lookup"><span data-stu-id="c9801-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="c9801-105">A `Function` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod, który nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="c9801-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="c9801-106">Zostanie zwrócona wartość `Function` procedury w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="c9801-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="c9801-107">Włącz wartość w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c9801-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="c9801-108">Przypisuje wartość do `Function` procedury nazwę, a następnie wykonać `Exit Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c9801-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="c9801-109">Przypisuje wartość do `Function` procedury nazwę, a następnie wykonać `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c9801-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="c9801-110">Jeśli formant przekazuje do `Exit Function` lub `End Function` i nie przypisano żadnej wartości na nazwę procedury, procedura zwraca wartość domyślna typu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="c9801-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="c9801-111">Aby uzyskać więcej informacji, zobacz "Zachowanie" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c9801-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="c9801-112">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c9801-112">By default, this message is a warning.</span></span> <span data-ttu-id="c9801-113">Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c9801-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c9801-114">**Identyfikator błędu:** BC42105</span><span class="sxs-lookup"><span data-stu-id="c9801-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9801-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c9801-115">To correct this error</span></span>  
  
-   <span data-ttu-id="c9801-116">Sprawdź logika przepływu sterowania i upewnij się, że można przypisać wartości przed każdym instrukcji, która powoduje, że typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="c9801-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="c9801-117">Ułatwia zagwarantować co zwrotu z procedury zwraca wartość, jeśli używasz zawsze `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c9801-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="c9801-118">Jeśli to zrobisz, ostatniej instrukcji przed `End Function` powinien być `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c9801-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9801-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9801-119">See Also</span></span>  
 [<span data-ttu-id="c9801-120">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="c9801-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="c9801-121">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="c9801-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="c9801-122">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9801-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
