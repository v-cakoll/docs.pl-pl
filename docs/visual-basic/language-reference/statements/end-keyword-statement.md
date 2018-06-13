---
title: End &lt;słowo kluczowe&gt; — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605267"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="df19c-102">End &lt;słowo kluczowe&gt; — instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df19c-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>
<span data-ttu-id="df19c-103">Gdy następuje dodatkowe słowo kluczowe, kończy definicję bloku instrukcji wynikające z tego słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="df19c-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df19c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df19c-104">Syntax</span></span>  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="df19c-105">Części</span><span class="sxs-lookup"><span data-stu-id="df19c-105">Parts</span></span>  
 `End`  
 <span data-ttu-id="df19c-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="df19c-106">Required.</span></span> <span data-ttu-id="df19c-107">Kończy definicję elementu programowania.</span><span class="sxs-lookup"><span data-stu-id="df19c-107">Terminates the definition of the programming element.</span></span>  
  
 `AddHandler`  
 <span data-ttu-id="df19c-108">Wymagane do zakończenia `AddHandler` akcesor rozpoczyna się od odpowiadającego mu `AddHandler` instrukcji w niestandardowej [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-108">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Class`  
 <span data-ttu-id="df19c-109">Wymagane do zakończenia definicję klasy rozpoczyna się od odpowiadającego mu [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-109">Required to terminate a class definition begun by a matching [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
 `Enum`  
 <span data-ttu-id="df19c-110">Wymagane do zakończenia definicja wyliczenia rozpoczyna się od odpowiadającego mu [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-110">Required to terminate an enumeration definition begun by a matching [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 `Event`  
 <span data-ttu-id="df19c-111">Wymagane do zakończenia `Custom` definicji zdarzenia uruchomione przez odpowiadającą jej instrukcją [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-111">Required to terminate a `Custom` event definition begun by a matching [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Function`  
 <span data-ttu-id="df19c-112">Wymagane do zakończenia `Function` Definicja procedury rozpoczyna się od odpowiadającego mu [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-112">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="df19c-113">Jeśli wykonanie napotkał `End``Function` instrukcji sterowania zwraca do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="df19c-113">If execution encounters an `End``Function` statement, control returns to the calling code.</span></span>  
  
 `Get`  
 <span data-ttu-id="df19c-114">Wymagane do zakończenia `Property` Definicja procedury rozpoczyna się od odpowiadającego mu [instrukcja Get](../../../visual-basic/language-reference/statements/get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-114">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md).</span></span> <span data-ttu-id="df19c-115">Jeśli wykonanie napotkał `End``Get` instrukcji sterowania zwraca do instrukcji żąda wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="df19c-115">If execution encounters an `End``Get` statement, control returns to the statement requesting the property's value.</span></span>  
  
 `If`  
 <span data-ttu-id="df19c-116">Wymagane do zakończenia `If`... `Then`... `Else` zablokować definicji rozpoczyna się od odpowiadającego mu `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df19c-116">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="df19c-117">Zobacz [Jeśli... Następnie... Else — instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-117">See [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span>  
  
 `Interface`  
 <span data-ttu-id="df19c-118">Wymagane do zakończenia definicji interfejsu rozpoczętej przez odpowiadającą jej instrukcją [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-118">Required to terminate an interface definition begun by a matching [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md).</span></span>  
  
 `Module`  
 <span data-ttu-id="df19c-119">Wymagane do zakończenia definicji modułu rozpoczyna się od odpowiadającego mu [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-119">Required to terminate a module definition begun by a matching [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
 `Namespace`  
 <span data-ttu-id="df19c-120">Wymagane do zakończenia definicję przestrzeni nazw, rozpoczyna się od odpowiadającego mu [instrukcji Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-120">Required to terminate a namespace definition begun by a matching [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span>  
  
 `Operator`  
 <span data-ttu-id="df19c-121">Wymagane do zakończenia definicja operatora rozpoczętej przez odpowiadającą jej instrukcją [operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-121">Required to terminate an operator definition begun by a matching [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 `Property`  
 <span data-ttu-id="df19c-122">Wymagane do zakończenia definicji właściwości rozpoczyna się od odpowiadającego mu [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-122">Required to terminate a property definition begun by a matching [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
 `RaiseEvent`  
 <span data-ttu-id="df19c-123">Wymagane do zakończenia `RaiseEvent` akcesor rozpoczyna się od odpowiadającego mu `RaiseEvent` instrukcji w niestandardowej [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-123">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `RemoveHandler`  
 <span data-ttu-id="df19c-124">Wymagane do zakończenia `RemoveHandler` akcesor rozpoczyna się od odpowiadającego mu `RemoveHandler` instrukcji w niestandardowej [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-124">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Select`  
 <span data-ttu-id="df19c-125">Wymagane do zakończenia `Select`... `Case` zablokować definicji rozpoczyna się od odpowiadającego mu `Select` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df19c-125">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="df19c-126">Zobacz [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-126">See [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
 `Set`  
 <span data-ttu-id="df19c-127">Wymagane do zakończenia `Property` Definicja procedury rozpoczyna się od odpowiadającego mu [Instrukcja Set](../../../visual-basic/language-reference/statements/set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-127">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md).</span></span> <span data-ttu-id="df19c-128">Jeśli wykonanie napotkał `End``Set` instrukcji sterowania zwraca do instrukcji ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="df19c-128">If execution encounters an `End``Set` statement, control returns to the statement setting the property's value.</span></span>  
  
 `Structure`  
 <span data-ttu-id="df19c-129">Wymagane do zakończenia definicji struktury rozpoczyna się od odpowiadającego mu [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-129">Required to terminate a structure definition begun by a matching [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
 `Sub`  
 <span data-ttu-id="df19c-130">Wymagane do zakończenia `Sub` Definicja procedury rozpoczyna się od odpowiadającego mu [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-130">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span> <span data-ttu-id="df19c-131">Jeśli wykonanie napotkał `End``Sub` instrukcji sterowania zwraca do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="df19c-131">If execution encounters an `End``Sub` statement, control returns to the calling code.</span></span>  
  
 `SyncLock`  
 <span data-ttu-id="df19c-132">Wymagane do zakończenia `SyncLock` zablokować definicji rozpoczyna się od odpowiadającego mu `SyncLock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df19c-132">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="df19c-133">Zobacz [SyncLock — instrukcja](../../../visual-basic/language-reference/statements/synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-133">See [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).</span></span>  
  
 `Try`  
 <span data-ttu-id="df19c-134">Wymagane do zakończenia `Try`... `Catch`... `Finally` zablokować definicji rozpoczyna się od odpowiadającego mu `Try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df19c-134">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="df19c-135">Zobacz [spróbuj... CATCH... Instrukcji finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-135">See [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 `While`  
 <span data-ttu-id="df19c-136">Wymagane do zakończenia `While` pętli definicji rozpoczyna się od odpowiadającego mu `While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df19c-136">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="df19c-137">Zobacz [podczas... End While — instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-137">See [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
 `With`  
 <span data-ttu-id="df19c-138">Wymagane do zakończenia `With` zablokować definicji rozpoczyna się od odpowiadającego mu `With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df19c-138">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="df19c-139">Zobacz [z... End With — instrukcja](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-139">See [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df19c-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df19c-140">Remarks</span></span>  
 <span data-ttu-id="df19c-141">[Instrukcji End](../../../visual-basic/language-reference/statements/end-statement.md), bez dodatkowych słowa kluczowego kończy wykonywanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="df19c-141">The [End Statement](../../../visual-basic/language-reference/statements/end-statement.md), without an additional keyword, terminates execution immediately.</span></span>  
  
 <span data-ttu-id="df19c-142">Gdy poprzedzone znakiem numeru (`#`), `End` — słowo kluczowe kończy wprowadzone przez odpowiednie dyrektywy przetwarzania wstępnego bloku.</span><span class="sxs-lookup"><span data-stu-id="df19c-142">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  
  
 `#End`  
 <span data-ttu-id="df19c-143">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="df19c-143">Required.</span></span> <span data-ttu-id="df19c-144">Kończy definicję bloku przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="df19c-144">Terminates the definition of the preprocessing block.</span></span>  
  
 `#ExternalSource`  
 <span data-ttu-id="df19c-145">Wymagane do zakończenia bloku źródła zewnętrznego rozpoczyna się od odpowiadającego mu [#ExternalSource — dyrektywa](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-145">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span></span>  
  
 `#If`  
 <span data-ttu-id="df19c-146">Wymagane do zakończenia bloku kompilacja warunkowa rozpoczyna się od odpowiadającego mu `#If` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="df19c-146">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="df19c-147">Zobacz [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-147">See [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span></span>  
  
 `#Region`  
 <span data-ttu-id="df19c-148">Wymagane do zakończenia bloku region źródłowego rozpoczyna się od odpowiadającego mu [#Region — dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="df19c-148">Required to terminate a source region block begun by a matching [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md).</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="df19c-149">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="df19c-149">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="df19c-150">`End` Instrukcja bez dodatkowych — słowo kluczowe nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="df19c-150">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df19c-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df19c-151">See Also</span></span>  
 [<span data-ttu-id="df19c-152">End Statement</span><span class="sxs-lookup"><span data-stu-id="df19c-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
