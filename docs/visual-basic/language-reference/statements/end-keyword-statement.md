---
title: End <keyword>, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.EndDefinition
helpviewer_keywords:
- End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
ms.openlocfilehash: 87f4724cc036e6e0bdf0b558854a4034f45b9ab5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343735"
---
# <a name="end-keyword-statement-visual-basic"></a><span data-ttu-id="a004a-102">End \<słowo kluczowe > instrukcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a004a-102">End \<keyword> Statement (Visual Basic)</span></span>

<span data-ttu-id="a004a-103">Gdy następuje po nim dodatkowe słowo kluczowe, kończy definicję bloku instrukcji wynikającą z tego słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="a004a-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>

## <a name="syntax"></a><span data-ttu-id="a004a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a004a-104">Syntax</span></span>

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
  
## <a name="parts"></a><span data-ttu-id="a004a-105">Części</span><span class="sxs-lookup"><span data-stu-id="a004a-105">Parts</span></span>

|<span data-ttu-id="a004a-106">Części</span><span class="sxs-lookup"><span data-stu-id="a004a-106">Part</span></span>|<span data-ttu-id="a004a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a004a-107">Description</span></span>|
|---|---|
|`End`|<span data-ttu-id="a004a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a004a-108">Required.</span></span> <span data-ttu-id="a004a-109">Kończy definicję elementu programowania.</span><span class="sxs-lookup"><span data-stu-id="a004a-109">Terminates the definition of the programming element.</span></span>|
|`AddHandler`|<span data-ttu-id="a004a-110">Wymagany do zakończenia metody dostępu `AddHandler` rozpoczętej przez zgodną instrukcję `AddHandler` w niestandardowej [instrukcji zdarzenia](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-110">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Class`|<span data-ttu-id="a004a-111">Wymagane, aby zakończyć definicję klasy rozpoczętą przez zgodną [instrukcję klasy](class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-111">Required to terminate a class definition begun by a matching [Class Statement](class-statement.md).</span></span>|
|`Enum`|<span data-ttu-id="a004a-112">Wymagane, aby zakończyć definicję wyliczenia rozpoczętą przez zgodną [instrukcję enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-112">Required to terminate an enumeration definition begun by a matching [Enum Statement](enum-statement.md).</span></span>|
|`Event`|<span data-ttu-id="a004a-113">Wymagane, aby zakończyć `Custom` definicję zdarzenia rozpoczętą przez zgodną [instrukcję zdarzenia](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-113">Required to terminate a `Custom` event definition begun by a matching [Event Statement](event-statement.md).</span></span>|  
|`Function`|<span data-ttu-id="a004a-114">Wymagane, aby zakończyć `Function` definicję procedury rozpoczętą przez zgodną [instrukcję Function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-114">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](function-statement.md).</span></span> <span data-ttu-id="a004a-115">Jeśli wykonanie napotka instrukcję `End Function`, sterowanie powraca do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a004a-115">If execution encounters an `End Function` statement, control returns to the calling code.</span></span>|
|`Get`|<span data-ttu-id="a004a-116">Wymagane, aby zakończyć `Property` definicję procedury rozpoczętą przez zgodną [instrukcję Get](get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-116">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](get-statement.md).</span></span> <span data-ttu-id="a004a-117">Jeśli wykonanie napotka instrukcję `End Get`, sterowanie powraca do instrukcji żądającej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="a004a-117">If execution encounters an `End Get` statement, control returns to the statement requesting the property's value.</span></span>|
|`If`|<span data-ttu-id="a004a-118">Wymagany do zakończenia `If`...`Then`...`Else` definicji bloku rozpoczętej przez zgodną instrukcję `If`.</span><span class="sxs-lookup"><span data-stu-id="a004a-118">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="a004a-119">Sprawdź, [czy... Następnie... Else — instrukcja](if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-119">See [If...Then...Else Statement](if-then-else-statement.md).</span></span>|
|`Interface`|<span data-ttu-id="a004a-120">Wymagane, aby zakończyć definicję interfejsu rozpoczętą przez zgodną [instrukcję interfejsu](interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-120">Required to terminate an interface definition begun by a matching [Interface Statement](interface-statement.md).</span></span>|
|`Module`|<span data-ttu-id="a004a-121">Wymagane, aby zakończyć definicję modułu rozpoczętą przez zgodną [instrukcję modułu](module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-121">Required to terminate a module definition begun by a matching [Module Statement](module-statement.md).</span></span>|
|`Namespace`|<span data-ttu-id="a004a-122">Wymagane, aby zakończyć definicję przestrzeni nazw rozpoczętą przez zgodną [instrukcję Namespace](namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-122">Required to terminate a namespace definition begun by a matching [Namespace Statement](namespace-statement.md).</span></span>|
|`Operator`|<span data-ttu-id="a004a-123">Wymagane, aby zakończyć definicję operatora rozpoczętą przez zgodną [instrukcję operatora](operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-123">Required to terminate an operator definition begun by a matching [Operator Statement](operator-statement.md).</span></span>|
|`Property`|<span data-ttu-id="a004a-124">Wymagane do zakończenia definicji właściwości rozpoczętej przez zgodną [instrukcję właściwości](property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-124">Required to terminate a property definition begun by a matching [Property Statement](property-statement.md).</span></span>|
|`RaiseEvent`|<span data-ttu-id="a004a-125">Wymagany do zakończenia metody dostępu `RaiseEvent` rozpoczętej przez zgodną instrukcję `RaiseEvent` w niestandardowej [instrukcji zdarzenia](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-125">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`RemoveHandler`|<span data-ttu-id="a004a-126">Wymagany do zakończenia metody dostępu `RemoveHandler` rozpoczętej przez zgodną instrukcję `RemoveHandler` w niestandardowej [instrukcji zdarzenia](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-126">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](event-statement.md).</span></span>|
|`Select`|<span data-ttu-id="a004a-127">Wymagany do zakończenia `Select`...`Case` definicji bloku rozpoczętej przez zgodną instrukcję `Select`.</span><span class="sxs-lookup"><span data-stu-id="a004a-127">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="a004a-128">Zobacz [Wybierz... Case — instrukcja](select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-128">See [Select...Case Statement](select-case-statement.md).</span></span>  
|`Set`|<span data-ttu-id="a004a-129">Wymagane, aby zakończyć `Property` definicję procedury rozpoczętą przez zgodną [instrukcję SET](set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-129">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](set-statement.md).</span></span> <span data-ttu-id="a004a-130">Jeśli wykonanie napotka instrukcję `End Set`, sterowanie powraca do instrukcji ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="a004a-130">If execution encounters an `End Set` statement, control returns to the statement setting the property's value.</span></span>  
|`Structure`|<span data-ttu-id="a004a-131">Wymagane, aby zakończyć definicję struktury rozpoczętą przez zgodną [instrukcję struktury](structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-131">Required to terminate a structure definition begun by a matching [Structure Statement](structure-statement.md).</span></span>  
|`Sub`|<span data-ttu-id="a004a-132">Wymagane, aby zakończyć `Sub` definicję procedury rozpoczętą przez pasującą [instrukcję sub](sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-132">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](sub-statement.md).</span></span> <span data-ttu-id="a004a-133">Jeśli wykonanie napotka instrukcję `End Sub`, sterowanie powraca do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a004a-133">If execution encounters an `End Sub` statement, control returns to the calling code.</span></span>  
|`SyncLock`|<span data-ttu-id="a004a-134">Wymagany do zakończenia definicji bloku `SyncLock` rozpoczętej przez zgodną instrukcję `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="a004a-134">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="a004a-135">Zobacz [SyncLock instrukcji](synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-135">See [SyncLock Statement](synclock-statement.md).</span></span>  
|`Try`|<span data-ttu-id="a004a-136">Wymagany do zakończenia `Try`...`Catch`...`Finally` definicji bloku rozpoczętej przez zgodną instrukcję `Try`.</span><span class="sxs-lookup"><span data-stu-id="a004a-136">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="a004a-137">Zobacz [try... Catch... Finally — instrukcja](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-137">See [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
|`While`|<span data-ttu-id="a004a-138">Wymagany do zakończenia `While`j definicji pętli uruchomionej przez pasującą instrukcję `While`.</span><span class="sxs-lookup"><span data-stu-id="a004a-138">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="a004a-139">Zobacz [while... Instrukcja End while](while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-139">See [While...End While Statement](while-end-while-statement.md).</span></span>  
|`With`| <span data-ttu-id="a004a-140">Wymagany do zakończenia definicji bloku `With` rozpoczętej przez zgodną instrukcję `With`.</span><span class="sxs-lookup"><span data-stu-id="a004a-140">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="a004a-141">Zobacz [z... End With — instrukcja](with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-141">See [With...End With Statement](with-end-with-statement.md).</span></span>  
|||
  
## <a name="directives"></a><span data-ttu-id="a004a-142">Dyrektyw</span><span class="sxs-lookup"><span data-stu-id="a004a-142">Directives</span></span>

<span data-ttu-id="a004a-143">Gdy jest poprzedzona znakiem numeru (`#`), słowo kluczowe `End` kończy blok przetwarzania wstępnego wprowadzony przez odpowiednią dyrektywę.</span><span class="sxs-lookup"><span data-stu-id="a004a-143">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  

```vb
#End ExternalSource
#End If
#End Region
```

|<span data-ttu-id="a004a-144">Części</span><span class="sxs-lookup"><span data-stu-id="a004a-144">Part</span></span>|<span data-ttu-id="a004a-145">Opis</span><span class="sxs-lookup"><span data-stu-id="a004a-145">Description</span></span>|
|---|---|
|`#End`|<span data-ttu-id="a004a-146">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a004a-146">Required.</span></span> <span data-ttu-id="a004a-147">Kończy definicję bloku przetwarzania wstępnego.</span><span class="sxs-lookup"><span data-stu-id="a004a-147">Terminates the definition of the preprocessing block.</span></span>|
|`ExternalSource`|<span data-ttu-id="a004a-148">Wymagane, aby zakończyć zewnętrzny blok źródłowy rozpoczęty przez zgodną [#ExternalSource dyrektywą](../directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-148">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../directives/externalsource-directive.md).</span></span>|
|`If`|<span data-ttu-id="a004a-149">Wymagane, aby zakończyć blok kompilacji warunkowej rozpoczęty przez zgodną `#If` dyrektywę.</span><span class="sxs-lookup"><span data-stu-id="a004a-149">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="a004a-150">Zobacz [#If... Następnie... #Else dyrektywy](../directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-150">See [#If...Then...#Else Directives](../directives/if-then-else-directives.md).</span></span>|
|`Region`|<span data-ttu-id="a004a-151">Wymagane, aby zakończyć blok regionu źródłowego rozpoczęty przez zgodną [#Region dyrektywę](../directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="a004a-151">Required to terminate a source region block begun by a matching [#Region Directive](../directives/region-directive.md).</span></span>|
|||

## <a name="remarks"></a><span data-ttu-id="a004a-152">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a004a-152">Remarks</span></span>

<span data-ttu-id="a004a-153">[End](end-statement.md), bez dodatkowego słowa kluczowego, kończy wykonywanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="a004a-153">The [End Statement](end-statement.md), without an additional keyword, terminates execution immediately.</span></span>

## <a name="smart-device-developer-notes"></a><span data-ttu-id="a004a-154">Uwagi dla deweloperów urządzeń inteligentnych</span><span class="sxs-lookup"><span data-stu-id="a004a-154">Smart Device Developer Notes</span></span>  

<span data-ttu-id="a004a-155">Instrukcja `End` bez słowa kluczowego New nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="a004a-155">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a004a-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a004a-156">See also</span></span>

- [<span data-ttu-id="a004a-157">End, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a004a-157">End Statement</span></span>](end-statement.md)
