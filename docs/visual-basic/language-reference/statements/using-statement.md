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
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957542"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="21417-102">Using — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21417-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="21417-103">Deklaruje początek `Using` bloku i opcjonalnie uzyskuje zasoby systemowe, które są kontrolkami bloku.</span><span class="sxs-lookup"><span data-stu-id="21417-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21417-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21417-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="21417-105">Części</span><span class="sxs-lookup"><span data-stu-id="21417-105">Parts</span></span>  
  
|<span data-ttu-id="21417-106">Termin</span><span class="sxs-lookup"><span data-stu-id="21417-106">Term</span></span>|<span data-ttu-id="21417-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="21417-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="21417-108">Wymagane, jeśli nie podasz `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="21417-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="21417-109">Lista co najmniej jednego zasobu systemowego, który `Using` kontroluje ten blok, oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="21417-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="21417-110">Wymagane, jeśli nie podasz `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="21417-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="21417-111">Zmienna odniesienia lub wyrażenie odwołujące się do zasobu systemowego, który `Using` ma być kontrolowany przez ten blok.</span><span class="sxs-lookup"><span data-stu-id="21417-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="21417-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="21417-112">Optional.</span></span> <span data-ttu-id="21417-113">Blok instrukcji, które są `Using` uruchamiane przez blok.</span><span class="sxs-lookup"><span data-stu-id="21417-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="21417-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="21417-114">Required.</span></span> <span data-ttu-id="21417-115">Kończy definicję `Using` bloku i usuwa wszystkie zasoby, które on kontroluje.</span><span class="sxs-lookup"><span data-stu-id="21417-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="21417-116">Każdy zasób w `resourcelist` części ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="21417-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="21417-117">—lub—</span><span class="sxs-lookup"><span data-stu-id="21417-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="21417-118">resourceList części</span><span class="sxs-lookup"><span data-stu-id="21417-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="21417-119">Termin</span><span class="sxs-lookup"><span data-stu-id="21417-119">Term</span></span>|<span data-ttu-id="21417-120">Definicja</span><span class="sxs-lookup"><span data-stu-id="21417-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="21417-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="21417-121">Required.</span></span> <span data-ttu-id="21417-122">Zmienna odniesienia odwołująca się do zasobu systemowego `Using` , który kontroluje blok.</span><span class="sxs-lookup"><span data-stu-id="21417-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="21417-123">Wymagane, `Using` Jeśli instrukcja uzyskuje zasób.</span><span class="sxs-lookup"><span data-stu-id="21417-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="21417-124">Jeśli zasób został już pobrany, użyj drugiej alternatywy składni.</span><span class="sxs-lookup"><span data-stu-id="21417-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="21417-125">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="21417-125">Required.</span></span> <span data-ttu-id="21417-126">Klasa zasobu.</span><span class="sxs-lookup"><span data-stu-id="21417-126">The class of the resource.</span></span> <span data-ttu-id="21417-127">Klasa musi implementować <xref:System.IDisposable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="21417-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="21417-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="21417-128">Optional.</span></span> <span data-ttu-id="21417-129">Lista argumentów przekazywana do konstruktora, aby utworzyć wystąpienie `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="21417-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="21417-130">Zobacz [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="21417-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="21417-131">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="21417-131">Required.</span></span> <span data-ttu-id="21417-132">Zmienna lub wyrażenie odwołujące się do zasobu systemowego spełniającego `resourcetype`wymagania.</span><span class="sxs-lookup"><span data-stu-id="21417-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="21417-133">Jeśli używasz drugiej alternatywy składni, musisz uzyskać zasób przed przekazaniem kontroli do `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21417-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21417-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21417-134">Remarks</span></span>  
 <span data-ttu-id="21417-135">Czasami kod wymaga niezarządzanego zasobu, takiego jak dojście do pliku, otoka COM lub połączenie SQL.</span><span class="sxs-lookup"><span data-stu-id="21417-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="21417-136">`Using` Blok gwarantuje usunięcie jednego lub większej liczby takich zasobów, gdy kod zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="21417-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="21417-137">Sprawia to, że są one dostępne do użycia w innym kodzie.</span><span class="sxs-lookup"><span data-stu-id="21417-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="21417-138">Zarządzane zasoby są usuwane przez .NET Framework Moduł wyrzucania elementów bezużytecznych (GC) bez żadnego dodatkowego kodowania w części.</span><span class="sxs-lookup"><span data-stu-id="21417-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="21417-139">Nie jest potrzebny `Using` blok dla zarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="21417-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="21417-140">Można jednak nadal używać `Using` bloku, aby wymusić usunięcie zarządzanego zasobu, zamiast czekać na Moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="21417-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="21417-141">`Using` Blok ma trzy części: pozyskiwanie, użycie i usuwanie.</span><span class="sxs-lookup"><span data-stu-id="21417-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
- <span data-ttu-id="21417-142">*Pozyskiwanie* oznacza tworzenie zmiennej i Inicjowanie jej w celu odwoływania się do zasobu systemowego.</span><span class="sxs-lookup"><span data-stu-id="21417-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="21417-143">Instrukcja może uzyskać jeden lub więcej zasobów lub można uzyskać dokładnie jeden zasób przed wprowadzeniem bloku i przekazać go `Using` do instrukcji. `Using`</span><span class="sxs-lookup"><span data-stu-id="21417-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="21417-144">W przypadku podania `resourceexpression`należy nabyć zasób przed przekazaniem kontroli `Using` do instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21417-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
- <span data-ttu-id="21417-145">*Użycie* oznacza uzyskiwanie dostępu do zasobów i wykonywanie do nich działań.</span><span class="sxs-lookup"><span data-stu-id="21417-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="21417-146">Instrukcje między `Using` i `End Using` reprezentowania użycia zasobów.</span><span class="sxs-lookup"><span data-stu-id="21417-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
- <span data-ttu-id="21417-147">*Usuwanie* oznacza wywołanie <xref:System.IDisposable.Dispose%2A> metody dla obiektu w `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="21417-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="21417-148">Dzięki temu obiekt może czyścić swoje zasoby.</span><span class="sxs-lookup"><span data-stu-id="21417-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="21417-149">Instrukcja usuwa zasoby `Using` pod kontrolką bloku. `End Using`</span><span class="sxs-lookup"><span data-stu-id="21417-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="21417-150">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="21417-150">Behavior</span></span>  
 <span data-ttu-id="21417-151">Blok zachowuje się `Try`jak... `Using` konstrukcja, w `Try` której blok `Finally` używa zasobów i blokują elementy Dispose. `Finally`</span><span class="sxs-lookup"><span data-stu-id="21417-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="21417-152">W związku z tym `Using` blok gwarantuje usunięcie zasobów bez względu na sposób zamykania bloku.</span><span class="sxs-lookup"><span data-stu-id="21417-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="21417-153">Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku, z wyjątkiem <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="21417-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="21417-154">Zakres każdej zmiennej zasobu uzyskanej przez `Using` instrukcję jest ograniczony `Using` do bloku.</span><span class="sxs-lookup"><span data-stu-id="21417-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="21417-155">Jeśli w `Using` instrukcji określono więcej niż jeden zasób systemowy, efekt jest taki sam, jak w przypadku zagnieżdżonych `Using` bloków w innym.</span><span class="sxs-lookup"><span data-stu-id="21417-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="21417-156">Jeśli `resourcename` <xref:System.IDisposable.Dispose%2A> jest `Nothing`, żadne wywołanie nie jest wykonywane i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="21417-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="21417-157">Obsługa wyjątków strukturalnych w bloku using</span><span class="sxs-lookup"><span data-stu-id="21417-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="21417-158">Jeśli musisz obsłużyć wyjątek, który może wystąpić w `Using` bloku, możesz dodać kompletną `Try`... `Finally` do niego konstrukcja.</span><span class="sxs-lookup"><span data-stu-id="21417-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="21417-159">Jeśli potrzebujesz obsłużyć przypadek, w którym `Using` instrukcja nie powiodła się podczas pobierania zasobu, możesz sprawdzić, czy `resourcename` jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="21417-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="21417-160">Strukturalna obsługa wyjątków zamiast bloku using</span><span class="sxs-lookup"><span data-stu-id="21417-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="21417-161">Jeśli potrzebujesz bardziej precyzyjnej kontroli nad przejęciem zasobów lub potrzebujesz dodatkowego kodu w `Finally` bloku, możesz `Using` ponownie napisać blok jako `Try`... `Finally` konstrukcja.</span><span class="sxs-lookup"><span data-stu-id="21417-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="21417-162">W poniższym przykładzie przedstawiono szkielet `Try` i `Using` konstrukcje, które są równoważne podczas pozyskiwania i usuwania `resource`.</span><span class="sxs-lookup"><span data-stu-id="21417-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
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
> <span data-ttu-id="21417-163">Kod wewnątrz `Using` bloku nie powinien przypisywać `resourcename` obiektu do innej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="21417-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="21417-164">Po zamknięciu `Using` bloku zasób jest usuwany, a druga zmienna nie może uzyskać dostępu do zasobu, do którego wskazuje.</span><span class="sxs-lookup"><span data-stu-id="21417-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21417-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="21417-165">Example</span></span>  
 <span data-ttu-id="21417-166">Poniższy przykład tworzy plik o nazwie log. txt i zapisuje dwa wiersze tekstu do pliku.</span><span class="sxs-lookup"><span data-stu-id="21417-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="21417-167">Przykład odczytuje również ten sam plik i wyświetla wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="21417-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="21417-168">Ponieważ klasy <xref:System.IO.TextReader> <xref:System.IDisposable> i implementują interfejs, kod może używać `Using` instrukcji, aby upewnić się, że plik jest prawidłowo zamknięty po operacji zapisu i odczytu. <xref:System.IO.TextWriter></span><span class="sxs-lookup"><span data-stu-id="21417-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a><span data-ttu-id="21417-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21417-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="21417-170">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="21417-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="21417-171">Instrukcje: Usuwanie zasobu systemowego</span><span class="sxs-lookup"><span data-stu-id="21417-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
