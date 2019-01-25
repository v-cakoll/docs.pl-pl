---
title: Użycie zmiennej iteracyjnej w wyrażeniu lambda może spowodować nieoczekiwane wyniki
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 358c7a988ae95c2326a26bc048f5436e11acb340
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641593"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="bfb2e-102">Użycie zmiennej iteracyjnej w wyrażeniu lambda może spowodować nieoczekiwane wyniki</span><span class="sxs-lookup"><span data-stu-id="bfb2e-102">Using the iteration variable in a lambda expression may have unexpected results</span></span>
<span data-ttu-id="bfb2e-103">Użycie zmiennej iteracyjnej w wyrażeniu lambda może spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-103">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="bfb2e-104">Zamiast tego należy utworzyć zmienną lokalną, w ramach pętli i przypisać jej wartość zmiennej iteracji.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-104">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>  
  
 <span data-ttu-id="bfb2e-105">To ostrzeżenie jest wyświetlane, gdy używasz Zmienna iteracji pętli w wyrażeniu lambda, która jest zadeklarowana wewnątrz pętli.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-105">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="bfb2e-106">Na przykład poniższy przykład powoduje, że ostrzeżenia są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-106">For example, the following example causes the warning to appear.</span></span>  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 <span data-ttu-id="bfb2e-107">Poniższy przykład pokazuje nieoczekiwane wyniki, które mogą wystąpić.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-107">The following example shows the unexpected results that might occur.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="bfb2e-108">`For` Pętli tworzy tablicę wyrażeń lambda, z których każda zwraca wartość zmiennej iteracji pętli `i`.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-108">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="bfb2e-109">Gdy wyrażenia lambda są obliczane w `For Each` pętli, można by oczekiwać zobaczyć, 0, 1, 2, 3 i 4 wyświetlane, kolejnych wartości `i` w `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-109">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="bfb2e-110">Zamiast tego zobacz końcowa wartość `i` wyświetlane pięć razy:</span><span class="sxs-lookup"><span data-stu-id="bfb2e-110">Instead, you see the final value of `i` displayed five times:</span></span>  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 <span data-ttu-id="bfb2e-111">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-111">By default, this message is a warning.</span></span> <span data-ttu-id="bfb2e-112">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bfb2e-112">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bfb2e-113">**Identyfikator błędu:** BC42324</span><span class="sxs-lookup"><span data-stu-id="bfb2e-113">**Error ID:** BC42324</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bfb2e-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bfb2e-114">To correct this error</span></span>  
  
-   <span data-ttu-id="bfb2e-115">Przypisz wartość zmiennej iteracyjnej do zmiennej lokalnej, a następnie użyć zmiennej lokalnej w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="bfb2e-115">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfb2e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfb2e-116">See also</span></span>
- [<span data-ttu-id="bfb2e-117">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="bfb2e-117">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
