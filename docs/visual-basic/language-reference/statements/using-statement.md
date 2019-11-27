---
title: Using — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352757"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="04ca2-102">Using — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04ca2-102">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="04ca2-103">Deklaruje początek bloku `Using` i opcjonalnie uzyskuje zasoby systemowe, które są kontrolkami bloku.</span><span class="sxs-lookup"><span data-stu-id="04ca2-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="04ca2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04ca2-104">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="04ca2-105">Części</span><span class="sxs-lookup"><span data-stu-id="04ca2-105">Parts</span></span>

|<span data-ttu-id="04ca2-106">Termin</span><span class="sxs-lookup"><span data-stu-id="04ca2-106">Term</span></span>|<span data-ttu-id="04ca2-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="04ca2-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="04ca2-108">Wymagane, jeśli nie podasz `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="04ca2-109">Lista co najmniej jednego zasobu systemowego, który `Using` formantów bloku, rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="04ca2-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="04ca2-110">Wymagane, jeśli nie podasz `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="04ca2-111">Odwołanie do zmiennej lub wyrażenia odwołującego się do zasobu systemowego, który ma być kontrolowany przez ten blok `Using`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="04ca2-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="04ca2-112">Optional.</span></span> <span data-ttu-id="04ca2-113">Blok instrukcji, które są uruchamiane przez blok `Using`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="04ca2-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="04ca2-114">Required.</span></span> <span data-ttu-id="04ca2-115">Kończy definicję bloku `Using` i usuwa wszystkie zasoby, które kontroluje.</span><span class="sxs-lookup"><span data-stu-id="04ca2-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="04ca2-116">Każdy zasób w części `resourcelist` ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="04ca2-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="04ca2-117">—lub—</span><span class="sxs-lookup"><span data-stu-id="04ca2-117">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="04ca2-118">resourceList części</span><span class="sxs-lookup"><span data-stu-id="04ca2-118">resourcelist Parts</span></span>

|<span data-ttu-id="04ca2-119">Termin</span><span class="sxs-lookup"><span data-stu-id="04ca2-119">Term</span></span>|<span data-ttu-id="04ca2-120">Definicja</span><span class="sxs-lookup"><span data-stu-id="04ca2-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="04ca2-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="04ca2-121">Required.</span></span> <span data-ttu-id="04ca2-122">Zmienna odniesienia odwołująca się do zasobu systemowego, który kontroluje blok `Using`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="04ca2-123">Wymagane, jeśli instrukcja `Using` uzyskuje zasób.</span><span class="sxs-lookup"><span data-stu-id="04ca2-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="04ca2-124">Jeśli zasób został już pobrany, użyj drugiej alternatywy składni.</span><span class="sxs-lookup"><span data-stu-id="04ca2-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="04ca2-125">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="04ca2-125">Required.</span></span> <span data-ttu-id="04ca2-126">Klasa zasobu.</span><span class="sxs-lookup"><span data-stu-id="04ca2-126">The class of the resource.</span></span> <span data-ttu-id="04ca2-127">Klasa musi implementować interfejs <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="04ca2-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="04ca2-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="04ca2-128">Optional.</span></span> <span data-ttu-id="04ca2-129">Lista argumentów przekazywana do konstruktora, aby utworzyć wystąpienie `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="04ca2-130">Zobacz [listę parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="04ca2-130">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="04ca2-131">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="04ca2-131">Required.</span></span> <span data-ttu-id="04ca2-132">Zmienna lub wyrażenie odwołujące się do zasobu systemowego spełniającego wymagania `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="04ca2-133">Jeśli używasz drugiej alternatywy składni, musisz uzyskać zasób przed przekazaniem kontroli do instrukcji `Using`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04ca2-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04ca2-134">Remarks</span></span>

 <span data-ttu-id="04ca2-135">Czasami kod wymaga niezarządzanego zasobu, takiego jak dojście do pliku, otoka COM lub połączenie SQL.</span><span class="sxs-lookup"><span data-stu-id="04ca2-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="04ca2-136">Blok `Using` gwarantuje usunięcie jednego lub większej liczby takich zasobów, gdy kod zostanie ukończony z nimi.</span><span class="sxs-lookup"><span data-stu-id="04ca2-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="04ca2-137">Sprawia to, że są one dostępne do użycia w innym kodzie.</span><span class="sxs-lookup"><span data-stu-id="04ca2-137">This makes them available for other code to use.</span></span>

 <span data-ttu-id="04ca2-138">Zarządzane zasoby są usuwane przez .NET Framework Moduł wyrzucania elementów bezużytecznych (GC) bez żadnego dodatkowego kodowania w części.</span><span class="sxs-lookup"><span data-stu-id="04ca2-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="04ca2-139">Nie jest potrzebny blok `Using` dla zarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="04ca2-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="04ca2-140">Można jednak nadal używać bloku `Using`, aby wymusić usunięcie zarządzanego zasobu, zamiast czekać na Moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="04ca2-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="04ca2-141">Blok `Using` ma trzy części: pozyskiwanie, użycie i usuwanie.</span><span class="sxs-lookup"><span data-stu-id="04ca2-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="04ca2-142">*Pozyskiwanie* oznacza tworzenie zmiennej i Inicjowanie jej w celu odwoływania się do zasobu systemowego.</span><span class="sxs-lookup"><span data-stu-id="04ca2-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="04ca2-143">Instrukcja `Using` może uzyskać jeden lub więcej zasobów lub można uzyskać dokładnie jeden zasób przed wprowadzeniem bloku i przekazać go do instrukcji `Using`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="04ca2-144">W przypadku podania `resourceexpression`należy nabyć zasób przed przekazaniem kontroli do instrukcji `Using`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="04ca2-145">*Użycie* oznacza uzyskiwanie dostępu do zasobów i wykonywanie do nich działań.</span><span class="sxs-lookup"><span data-stu-id="04ca2-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="04ca2-146">Instrukcje między `Using` i `End Using` reprezentują użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="04ca2-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="04ca2-147">*Usuwanie* oznacza wywołanie metody <xref:System.IDisposable.Dispose%2A> na obiekcie w `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="04ca2-148">Dzięki temu obiekt może czyścić swoje zasoby.</span><span class="sxs-lookup"><span data-stu-id="04ca2-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="04ca2-149">Instrukcja `End Using` usuwa zasoby w kontrolce `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="04ca2-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="04ca2-150">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="04ca2-150">Behavior</span></span>

 <span data-ttu-id="04ca2-151">Blok `Using` zachowuje się jak `Try`...`Finally` konstrukcja, w której blok `Try` używa zasobów i bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="04ca2-152">W związku z tym blok `Using` gwarantuje usunięcie zasobów bez względu na sposób zamykania bloku.</span><span class="sxs-lookup"><span data-stu-id="04ca2-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="04ca2-153">Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku, z wyjątkiem <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="04ca2-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="04ca2-154">Zakres każdej zmiennej zasobów uzyskanej przez instrukcję `Using` jest ograniczony do bloku `Using`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="04ca2-155">W przypadku określenia więcej niż jednego zasobu systemowego w instrukcji `Using` efekt jest taki sam jak w przypadku zagnieżdżonych `Using` bloków w innym.</span><span class="sxs-lookup"><span data-stu-id="04ca2-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="04ca2-156">Jeśli `resourcename` jest `Nothing`, żadne wywołanie do <xref:System.IDisposable.Dispose%2A> nie zostanie wykonane i żaden wyjątek nie jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="04ca2-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="04ca2-157">Obsługa wyjątków strukturalnych w bloku using</span><span class="sxs-lookup"><span data-stu-id="04ca2-157">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="04ca2-158">Jeśli musisz obsłużyć wyjątek, który może wystąpić w bloku `Using`, możesz dodać do niego kompletny `Try`...`Finally`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="04ca2-159">Jeśli potrzebujesz obsłużyć przypadek, w którym instrukcja `Using` nie powiodła się podczas pobierania zasobu, możesz sprawdzić, czy `resourcename` jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="04ca2-160">Strukturalna obsługa wyjątków zamiast bloku using</span><span class="sxs-lookup"><span data-stu-id="04ca2-160">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="04ca2-161">Jeśli potrzebujesz bardziej precyzyjnej kontroli nad przejęciem zasobów lub potrzebujesz dodatkowego kodu w bloku `Finally`, możesz ponownie napisać blok `Using` jako `Try`...`Finally` konstrukcja.</span><span class="sxs-lookup"><span data-stu-id="04ca2-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="04ca2-162">W poniższym przykładzie przedstawiono szkielet `Try` i `Using` konstrukcjach, które są równoważne pozyskiwaniu i rozdysponowaniu `resource`.</span><span class="sxs-lookup"><span data-stu-id="04ca2-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

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
> <span data-ttu-id="04ca2-163">Kod wewnątrz bloku `Using` nie powinien przypisywać obiektu w `resourcename` do innej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="04ca2-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="04ca2-164">Po zamknięciu bloku `Using` zasób jest usuwany, a druga zmienna nie może uzyskać dostępu do zasobu, do którego wskazuje.</span><span class="sxs-lookup"><span data-stu-id="04ca2-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="04ca2-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="04ca2-165">Example</span></span>

 <span data-ttu-id="04ca2-166">Poniższy przykład tworzy plik o nazwie log. txt i zapisuje dwa wiersze tekstu do pliku.</span><span class="sxs-lookup"><span data-stu-id="04ca2-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="04ca2-167">Przykład odczytuje również ten sam plik i wyświetla wiersze tekstu:</span><span class="sxs-lookup"><span data-stu-id="04ca2-167">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="04ca2-168">Ponieważ klasy <xref:System.IO.TextWriter> i <xref:System.IO.TextReader> implementują interfejs <xref:System.IDisposable>, kod może użyć instrukcji `Using`, aby upewnić się, że plik jest prawidłowo zamknięty po operacji zapisu i odczytu.</span><span class="sxs-lookup"><span data-stu-id="04ca2-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="04ca2-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04ca2-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="04ca2-170">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="04ca2-170">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="04ca2-171">Instrukcje: usuwanie zasobu systemu</span><span class="sxs-lookup"><span data-stu-id="04ca2-171">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
