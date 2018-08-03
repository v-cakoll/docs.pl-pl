---
title: End &lt;słowo kluczowe&gt; — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 8137434bfd8c26144d78b1761b784cdba4894eaf
ms.sourcegitcommit: 7fe772c6c05a982153655d618c826e9839d39cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "33605267"
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="3d0fe-102">End &lt;słowo kluczowe&gt; — instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d0fe-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>

<span data-ttu-id="3d0fe-103">Gdy następuje po nim dodatkowe słowo kluczowe, kończy definicję bloku instrukcji wynikającą z tego słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="3d0fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d0fe-104">Syntax</span></span>

```vb
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
  
## <a name="parts"></a><span data-ttu-id="3d0fe-105">Części</span><span class="sxs-lookup"><span data-stu-id="3d0fe-105">Parts</span></span>

|<span data-ttu-id="3d0fe-106">Część</span><span class="sxs-lookup"><span data-stu-id="3d0fe-106">Part</span></span>|<span data-ttu-id="3d0fe-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3d0fe-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="3d0fe-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-108">Required.</span></span> <span data-ttu-id="3d0fe-109">Kończy definicję elementu programistycznego.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="3d0fe-110">Wymagane do zakończenia `AddHandler` uruchomione za pasujący obiekt typu metody dostępu `AddHandler` instrukcji w niestandardowym [Event — instrukcja](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="3d0fe-111">Wymagane do zakończenia definicję klasy uruchomione za pasujący obiekt typu [Class — instrukcja](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="3d0fe-112">Wymagane do zakończenia definicja wyliczenia uruchomione za pasujący obiekt typu [Enum — instrukcja](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="3d0fe-113">Wymagane do zakończenia `Custom` definicji zdarzenia uruchomione za pasujący obiekt typu [Event — instrukcja](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="3d0fe-114">Wymagane do zakończenia `Function` definicji procedury uruchomione za pasujący obiekt typu [Function — instrukcja](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="3d0fe-115">Jeśli wykonanie napotka `End Function` instrukcji, sterowanie powraca do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="3d0fe-116">Wymagane do zakończenia `Property` definicji procedury uruchomione za pasujący obiekt typu [instrukcja Get](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="3d0fe-117">Jeśli wykonanie napotka `End Get` instrukcji, sterowanie powraca do instrukcji żąda wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="3d0fe-118">Wymagane do zakończenia `If`... `Then`... `Else` block definicji uruchomione za pasujący obiekt typu `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="3d0fe-119">Zobacz [Jeśli... Następnie... Else — instrukcja](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="3d0fe-120">Wymagane do zakończenia definicji interfejsu uruchomione za pasujący obiekt typu [Interface — instrukcja](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="3d0fe-121">Wymagane do zakończenia definicji modułu, uruchomione za pasujący obiekt typu [Module — instrukcja](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="3d0fe-122">Wymagane do zakończenia definicję przestrzeni nazw, uruchomione za pasujący obiekt typu [Namespace, instrukcja](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="3d0fe-123">Wymagane do zakończenia definicję operatora, uruchomione za pasujący obiekt typu [operator — instrukcja](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="3d0fe-124">Wymagane do zakończenia definicji właściwości uruchomione za pasujący obiekt typu [Property — instrukcja](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="3d0fe-125">Wymagane do zakończenia `RaiseEvent` uruchomione za pasujący obiekt typu metody dostępu `RaiseEvent` instrukcji w niestandardowym [Event — instrukcja](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="3d0fe-126">Wymagane do zakończenia `RemoveHandler` uruchomione za pasujący obiekt typu metody dostępu `RemoveHandler` instrukcji w niestandardowym [Event — instrukcja](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="3d0fe-127">Wymagane do zakończenia `Select`... `Case` block definicji uruchomione za pasujący obiekt typu `Select` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="3d0fe-128">Zobacz [wybierz... Case — instrukcja](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="3d0fe-129">Wymagane do zakończenia `Property` definicji procedury uruchomione za pasujący obiekt typu [instrukcji Set](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="3d0fe-130">Jeśli wykonanie napotka `End Set` instrukcji, sterowanie powraca do instrukcji, ustawiając wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="3d0fe-131">Wymagane do zakończenia definicji struktury uruchomione za pasujący obiekt typu [Structure — instrukcja](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="3d0fe-132">Wymagane do zakończenia `Sub` definicji procedury uruchomione za pasujący obiekt typu [Sub — instrukcja](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="3d0fe-133">Jeśli wykonanie napotka `End Sub` instrukcji, sterowanie powraca do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="3d0fe-134">Wymagane do zakończenia `SyncLock` block definicji uruchomione za pasujący obiekt typu `SyncLock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="3d0fe-135">Zobacz [SyncLock — instrukcja](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="3d0fe-136">Wymagane do zakończenia `Try`... `Catch`... `Finally` block definicji uruchomione za pasujący obiekt typu `Try` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="3d0fe-137">Zobacz [spróbuj... CATCH... Na koniec instrukcji](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="3d0fe-138">Wymagane do zakończenia `While` pętli definicji uruchomione za pasujący obiekt typu `While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="3d0fe-139">Zobacz [podczas... Kończy While, instrukcja](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="3d0fe-140">Wymagane do zakończenia `With` block definicji uruchomione za pasujący obiekt typu `With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="3d0fe-141">Zobacz [za pomocą... End With — instrukcja](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="3d0fe-142">Dyrektyw</span><span class="sxs-lookup"><span data-stu-id="3d0fe-142">Directives</span></span>

<span data-ttu-id="3d0fe-143">Jeśli są poprzedzone znakiem numeru (`#`), `End` — słowo kluczowe kończy blok preprocesora wprowadzone przez odpowiednie dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="3d0fe-144">Część</span><span class="sxs-lookup"><span data-stu-id="3d0fe-144">Part</span></span>|<span data-ttu-id="3d0fe-145">Opis</span><span class="sxs-lookup"><span data-stu-id="3d0fe-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="3d0fe-146">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-146">Required.</span></span> <span data-ttu-id="3d0fe-147">Kończy definicję bloku przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="3d0fe-148">Wymagane do zakończenia blokiem zewnętrznego źródła, uruchomione za pasujący obiekt typu [#ExternalSource — dyrektywa](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="3d0fe-149">Wymagane do zakończenia bloku kompilacji warunkowej, uruchomione za pasujący obiekt typu `#If` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="3d0fe-150">Zobacz [#If... Then... #Else — dyrektywy](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="3d0fe-151">Wymagane do zakończenia bloku regionu źródłowego uruchomione za pasujący obiekt typu [#Region — dyrektywa](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="3d0fe-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="3d0fe-152">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d0fe-152">Remarks</span></span>

<span data-ttu-id="3d0fe-153">[Instrukcja End](end-statement.md) bez dodatkowego słowa kluczowego kończy wykonywanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="3d0fe-154">Uwagi dla deweloperów urządzeń inteligentnych</span><span class="sxs-lookup"><span data-stu-id="3d0fe-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="3d0fe-155">Instrukcja `End` bez dodatkowego słowa kluczowego nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="3d0fe-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d0fe-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d0fe-156">See also</span></span>

[<span data-ttu-id="3d0fe-157">End, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3d0fe-157">End Statement</span></span>](end-statement.md)
