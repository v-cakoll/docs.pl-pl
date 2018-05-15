---
title: Using — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 725eeb42dc5462022ac1a021c537d701929398ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="66ce4-102">Using — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66ce4-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="66ce4-103">Deklaruje początku `Using` blokować i opcjonalnie uzyskuje zasobów systemowych, które kontroluje bloku.</span><span class="sxs-lookup"><span data-stu-id="66ce4-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66ce4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66ce4-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="66ce4-105">Części</span><span class="sxs-lookup"><span data-stu-id="66ce4-105">Parts</span></span>  
  
|<span data-ttu-id="66ce4-106">Termin</span><span class="sxs-lookup"><span data-stu-id="66ce4-106">Term</span></span>|<span data-ttu-id="66ce4-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="66ce4-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="66ce4-108">Wymagane, jeśli nie podasz `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="66ce4-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="66ce4-109">Lista zasobów systemowych, co najmniej jeden tego `Using` blokowania formantów, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="66ce4-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="66ce4-110">Wymagane, jeśli nie podasz `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="66ce4-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="66ce4-111">Odwołanie do zmiennej lub wyrażenie odwołuje się do zasobu systemu kontrolowany przez to `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="66ce4-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="66ce4-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="66ce4-112">Optional.</span></span> <span data-ttu-id="66ce4-113">Blok instrukcji który `Using` blokowanie działa.</span><span class="sxs-lookup"><span data-stu-id="66ce4-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="66ce4-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="66ce4-114">Required.</span></span> <span data-ttu-id="66ce4-115">Kończy definicję `Using` bloku i usuwa wszystkie zasoby, które kontroluje.</span><span class="sxs-lookup"><span data-stu-id="66ce4-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="66ce4-116">Każdy zasób w `resourcelist` części ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="66ce4-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="66ce4-117">—lub—</span><span class="sxs-lookup"><span data-stu-id="66ce4-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="66ce4-118">Części resourcelist</span><span class="sxs-lookup"><span data-stu-id="66ce4-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="66ce4-119">Termin</span><span class="sxs-lookup"><span data-stu-id="66ce4-119">Term</span></span>|<span data-ttu-id="66ce4-120">Definicja</span><span class="sxs-lookup"><span data-stu-id="66ce4-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="66ce4-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="66ce4-121">Required.</span></span> <span data-ttu-id="66ce4-122">Odwołanie do zmiennej, która odwołuje się do zasobu systemu który `Using` blokowania formantów.</span><span class="sxs-lookup"><span data-stu-id="66ce4-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="66ce4-123">Jeśli wymagane `Using` instrukcji uzyskuje zasobu.</span><span class="sxs-lookup"><span data-stu-id="66ce4-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="66ce4-124">Jeśli już zostały nabyte zasobu, należy użyć drugiej alternatywnej składni.</span><span class="sxs-lookup"><span data-stu-id="66ce4-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="66ce4-125">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="66ce4-125">Required.</span></span> <span data-ttu-id="66ce4-126">Klasa zasobu.</span><span class="sxs-lookup"><span data-stu-id="66ce4-126">The class of the resource.</span></span> <span data-ttu-id="66ce4-127">Klasa musi implementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="66ce4-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="66ce4-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="66ce4-128">Optional.</span></span> <span data-ttu-id="66ce4-129">Lista argumentów jest przekazywany do konstruktora w celu utworzenia wystąpienia `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="66ce4-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="66ce4-130">Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="66ce4-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="66ce4-131">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="66ce4-131">Required.</span></span> <span data-ttu-id="66ce4-132">Zmiennej lub wyrażenie odwołujących się do zasobu systemu spełniających wymagania `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="66ce4-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="66ce4-133">Użycie drugiej alternatywnej składni, należy uzyskać zasobu przed przekazaniem kontroli do `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="66ce4-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66ce4-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66ce4-134">Remarks</span></span>  
 <span data-ttu-id="66ce4-135">Czasami kodu wymaga zasób niezarządzany, np. dojście do pliku, otoki COM lub połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="66ce4-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="66ce4-136">A `Using` bloku gwarantuje usuwania jeden lub więcej takich zasobów, po zakończeniu kodu z nimi.</span><span class="sxs-lookup"><span data-stu-id="66ce4-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="66ce4-137">Udostępnia je dla innych kodu do użycia.</span><span class="sxs-lookup"><span data-stu-id="66ce4-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="66ce4-138">Zarządzane zasoby są usuwane przez moduł zbierający elementy bezużyteczne .NET Framework (GC) bez żadnych dodatkowych kodowania ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="66ce4-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="66ce4-139">Nie trzeba `Using` blok dla zarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="66ce4-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="66ce4-140">Jednakże, nadal można `Using` bloku, aby wymusić usuwania zarządzanych zasobów, zamiast czekać na moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="66ce4-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="66ce4-141">A `Using` bloku ma trzy części: nabycie, użycia i usuwania.</span><span class="sxs-lookup"><span data-stu-id="66ce4-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
-   <span data-ttu-id="66ce4-142">*Nabycia* oznacza tworzenia zmiennej i inicjowania go do odwoływania się do zasobu systemowego.</span><span class="sxs-lookup"><span data-stu-id="66ce4-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="66ce4-143">`Using` Instrukcji można pobrać co najmniej jeden zasób, lub można uzyskać dokładnie jeden zasób przed wprowadzeniem bloku i dostarczenia go do `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="66ce4-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="66ce4-144">Jeśli podasz `resourceexpression`, należy uzyskać zasobu przed przekazaniem kontroli do `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="66ce4-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
-   <span data-ttu-id="66ce4-145">*Użycie* oznacza, że uzyskanie dostępu do zasobów i wykonywania związanych z nimi czynności.</span><span class="sxs-lookup"><span data-stu-id="66ce4-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="66ce4-146">Instrukcje między `Using` i `End Using` reprezentują użycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="66ce4-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
-   <span data-ttu-id="66ce4-147">*Usuwanie* sposób wywoływania <xref:System.IDisposable.Dispose%2A> metody dla obiekt w `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="66ce4-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="66ce4-148">Dzięki temu obiekt, aby prawidłowo zakończyć jego zasoby.</span><span class="sxs-lookup"><span data-stu-id="66ce4-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="66ce4-149">`End Using` Instrukcji usuwa zasobów w ramach `Using` bloku kontroli.</span><span class="sxs-lookup"><span data-stu-id="66ce4-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="66ce4-150">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="66ce4-150">Behavior</span></span>  
 <span data-ttu-id="66ce4-151">A `Using` bloku zachowuje się jak `Try`... `Finally` konstrukcji, w którym `Try` bloku używa zasobów i `Finally` bloku usuwa z nich.</span><span class="sxs-lookup"><span data-stu-id="66ce4-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="66ce4-152">W związku z tym `Using` bloku gwarantuje usuwania tych zasobów, niezależnie od tego, jak zakończyć bloku.</span><span class="sxs-lookup"><span data-stu-id="66ce4-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="66ce4-153">Dotyczy to nawet w przypadku nieobsługiwany wyjątek, z wyjątkiem <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="66ce4-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="66ce4-154">Zakres zmiennej zasobu, co uzyskaną przez `Using` instrukcji jest ograniczona do `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="66ce4-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="66ce4-155">Jeśli określono więcej niż jeden zasób systemowy w `Using` instrukcji, efekt jest taki sam, jakby użytkownik zagnieżdżone `Using` blokuje jedną w innym.</span><span class="sxs-lookup"><span data-stu-id="66ce4-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="66ce4-156">Jeśli `resourcename` jest `Nothing`, Brak wywołania <xref:System.IDisposable.Dispose%2A> następuje, i nie jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="66ce4-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="66ce4-157">Obsługa w bloku przy użyciu wyjątków strukturalnych</span><span class="sxs-lookup"><span data-stu-id="66ce4-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="66ce4-158">Jeśli należy do obsługi wyjątku, który może wystąpić w ramach `Using` bloku, możesz dodać pełnego `Try`... `Finally` konstrukcji do niego.</span><span class="sxs-lookup"><span data-stu-id="66ce4-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="66ce4-159">Jeśli wymagana jest obsługa w przypadku których `Using` instrukcji zakończy się niepowodzeniem podczas uzyskiwania zasobu, możesz przetestować, aby sprawdzić, czy `resourcename` jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="66ce4-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="66ce4-160">Obsługi zamiast za pomocą bloku wyjątków strukturalnych</span><span class="sxs-lookup"><span data-stu-id="66ce4-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="66ce4-161">Jeśli potrzebujesz bardziej precyzyjną kontrolę nad nabywania zasobów lub konieczne dodatkowy kod w `Finally` bloku, można ponownie napisać `Using` zablokować jako `Try`... `Finally` konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="66ce4-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="66ce4-162">W poniższym przykładzie przedstawiono szkielet `Try` i `Using` konstrukcje, które są równoważne nabycia i usuwania `resource`.</span><span class="sxs-lookup"><span data-stu-id="66ce4-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  <span data-ttu-id="66ce4-163">Kodu wewnątrz `Using` blok, nie należy przypisywać obiektu w `resourcename` do innej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="66ce4-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="66ce4-164">Po zakończeniu `Using` bloku, zasób zostanie usunięty i innej zmiennej nie może uzyskać dostęp do zasobu którą wskazuje.</span><span class="sxs-lookup"><span data-stu-id="66ce4-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66ce4-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="66ce4-165">Example</span></span>  
 <span data-ttu-id="66ce4-166">Poniższy przykład tworzy plik o nazwie log.txt i zapisuje dwóch wierszy tekstu do pliku.</span><span class="sxs-lookup"><span data-stu-id="66ce4-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="66ce4-167">W przykładzie również odczytuje tego samego pliku i wyświetla wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="66ce4-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="66ce4-168">Ponieważ <xref:System.IO.TextWriter> i <xref:System.IO.TextReader> implementacji klasy <xref:System.IDisposable> interfejsu, można użyć kodu `Using` instrukcje, aby upewnić się, że plik jest poprawnie zamknięte po wykonaniu operacji zapisu i operacje odczytu.</span><span class="sxs-lookup"><span data-stu-id="66ce4-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="66ce4-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66ce4-169">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="66ce4-170">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="66ce4-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="66ce4-171">Instrukcje: usuwanie zasobu systemu</span><span class="sxs-lookup"><span data-stu-id="66ce4-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
