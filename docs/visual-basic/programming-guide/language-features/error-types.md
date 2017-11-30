---
title: "Error — Typy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e01ed588d284a475a537a5fcf5ca506d25ca69f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="dc328-102">Error — Typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc328-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="dc328-103">W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], błędy (nazywane również *wyjątki*) dzielą się na trzy kategorie: błędy składni, błędy środowiska wykonawczego i błędy logiczne.</span><span class="sxs-lookup"><span data-stu-id="dc328-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="dc328-104">Błędy składniowe</span><span class="sxs-lookup"><span data-stu-id="dc328-104">Syntax Errors</span></span>  
 <span data-ttu-id="dc328-105">*Błędy składniowe* są wyświetlane podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="dc328-105">*Syntax errors* are those that appear while you write code.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="dc328-106">sprawdza kod w trakcie pisania **edytora kodu** okna i powiadamia w przypadku popełnienia błędu, takie jak błędy wyraz lub nieprawidłowo przy użyciu elementu języka.</span><span class="sxs-lookup"><span data-stu-id="dc328-106"> checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="dc328-107">Błędy składniowe są najczęściej spotykane błędy.</span><span class="sxs-lookup"><span data-stu-id="dc328-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="dc328-108">Możesz rozwiązać je łatwo w środowisku programowania natychmiast po ich występowania.</span><span class="sxs-lookup"><span data-stu-id="dc328-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc328-109">`Option Explicit` Instrukcja jest jednym ze sposobów unikanie błędy składniowe.</span><span class="sxs-lookup"><span data-stu-id="dc328-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="dc328-110">Wymusza zadeklarować z wyprzedzeniem wszystkie zmienne, które mają być używane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc328-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="dc328-111">Dlatego w przypadku używania tych zmiennych w kodzie błędy związane z typografią są przechwytywane natychmiast i można naprawić.</span><span class="sxs-lookup"><span data-stu-id="dc328-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="dc328-112">Błędy środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="dc328-112">Run-Time Errors</span></span>  
 <span data-ttu-id="dc328-113">*Błędy środowiska wykonawczego* to takie, które są wyświetlane tylko po skompilować i uruchomić kod.</span><span class="sxs-lookup"><span data-stu-id="dc328-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="dc328-114">Obejmują one kod, który może wydają się być poprawne, w tym zawiera ma błędów składni, ale nie zostanie wykonany.</span><span class="sxs-lookup"><span data-stu-id="dc328-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="dc328-115">Na przykład może poprawnie zapisać wiersza kodu w celu otwarcia pliku.</span><span class="sxs-lookup"><span data-stu-id="dc328-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="dc328-116">Ale jeśli plik jest uszkodzony, nie można wykonać aplikacji `Open` funkcji i jej przestanie działać.</span><span class="sxs-lookup"><span data-stu-id="dc328-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="dc328-117">Większość błędów czasu wykonywania można rozwiązać przez ponowne zapisywanie nieprawidłowy kod, a następnie ponowną kompilację i uruchomienie go.</span><span class="sxs-lookup"><span data-stu-id="dc328-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="dc328-118">Błędy logiczne</span><span class="sxs-lookup"><span data-stu-id="dc328-118">Logic Errors</span></span>  
 <span data-ttu-id="dc328-119">*Błędy logiczne* są wyświetlane, gdy aplikacja jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="dc328-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="dc328-120">Są one większość często niepożądanych lub nieoczekiwane wyniki w odpowiedzi na działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dc328-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="dc328-121">Na przykład podczas przepisywania klucz lub innych poza wpływ może spowodować aplikacja przestanie działać w ramach oczekiwanych parametrów lub zupełnie.</span><span class="sxs-lookup"><span data-stu-id="dc328-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="dc328-122">Błędy logiczne są zwykle najtrudniejsze typu, aby rozwiązać problem, ponieważ nie jest zawsze jasne, których pochodzą.</span><span class="sxs-lookup"><span data-stu-id="dc328-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc328-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc328-123">See Also</span></span>  
 [<span data-ttu-id="dc328-124">Try... CATCH... Finally — instrukcja</span><span class="sxs-lookup"><span data-stu-id="dc328-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="dc328-125">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="dc328-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
