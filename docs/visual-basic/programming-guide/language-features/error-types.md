---
title: Error — Typy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831569"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="b3fcb-102">Error — Typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3fcb-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="b3fcb-103">W języku Visual Basic, błędy (nazywane również *wyjątki*) można podzielić na trzy kategorie: błędy składniowe, błędy czasu wykonywania i błędy logiczne.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-103">In Visual Basic, errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="b3fcb-104">Błędy składniowe</span><span class="sxs-lookup"><span data-stu-id="b3fcb-104">Syntax Errors</span></span>  
 <span data-ttu-id="b3fcb-105">*Błędy składniowe* są te, które pojawiają się podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-105">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="b3fcb-106">Visual Basic umożliwia sprawdzenie kodu podczas wpisywania w **Edytor kodu** okna i generuje alert w przypadku popełnienia błędu, takie jak błąd pisowni wyrazu lub nieprawidłowo za pomocą elementu języka.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-106">Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="b3fcb-107">Błędy składniowe są najczęściej spotykanym typem błędy.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="b3fcb-108">Można je naprawić łatwo w środowisku programowania zaraz po ich wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3fcb-109">`Option Explicit` Instrukcja jest jednym ze sposobów uniknięcia błędów składniowych.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="b3fcb-110">Wymusza zadeklarować z wyprzedzeniem, wszystkie zmienne, które ma być używany w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="b3fcb-111">Dlatego stosowania tych zmiennych w kodzie błędy związane z typografią są przechwytywane natychmiast i można naprawić.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="b3fcb-112">Błędy czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="b3fcb-112">Run-Time Errors</span></span>  
 <span data-ttu-id="b3fcb-113">*Błędy środowiska wykonawczego* te, które są wyświetlane tylko po kompilacji i uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="b3fcb-114">Obejmują one kod, który może wydawać się być poprawne, ponieważ jej nie ma żadnych błędów składni, ale nie zostanie wykonany.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="b3fcb-115">Na przykład może być poprawnie napisać wiersza kodu, aby otworzyć plik.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="b3fcb-116">Ale jeśli plik jest uszkodzony, aplikacja nie może przeprowadzić `Open` funkcji i jej przestanie działać.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="b3fcb-117">Większość błędów czasu wykonywania można naprawić poprzez ponowne napisanie nieprawidłowy kod, a następnie ponownego kompilowania i ponowne jej uruchomienie.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="b3fcb-118">Błędy logiczne</span><span class="sxs-lookup"><span data-stu-id="b3fcb-118">Logic Errors</span></span>  
 <span data-ttu-id="b3fcb-119">*Błędy logiczne* te, które są wyświetlane, gdy aplikacja jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="b3fcb-120">Są one większość często niepożądane i nieoczekiwane wyniki, w odpowiedzi na działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="b3fcb-121">Na przykład, błędnie wpisane klucza lub innych zewnętrznych wpływ może spowodować, że aplikacja przestanie działać w ramach oczekiwanych parametrów lub całkowicie.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="b3fcb-122">Błędy logiczne są zwykle najtrudniejsze typu, aby rozwiązać problem, ponieważ nie zawsze jest jasne których pochodzą.</span><span class="sxs-lookup"><span data-stu-id="b3fcb-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3fcb-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3fcb-123">See also</span></span>

- [<span data-ttu-id="b3fcb-124">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3fcb-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b3fcb-125">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="b3fcb-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
