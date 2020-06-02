---
title: Wyrażenia Lambda w PLINQ i TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 3d985a003fe613699c89e38583f84be9e21b383d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290671"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="4d3e7-102">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="4d3e7-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="4d3e7-103">Biblioteka zadań równoległych (TPL) zawiera wiele metod, które mają jedną z <xref:System.Func%601?displayProperty=nameWithType> lub <xref:System.Action?displayProperty=nameWithType> rodzinę delegatów jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="4d3e7-104">Te Delegaty służą do przekazywania niestandardowej logiki programu do pętli równoległej, zadania lub zapytania.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="4d3e7-105">Przykłady kodu dla TPL oraz PLINQ używają wyrażeń lambda do tworzenia wystąpień tych delegatów jako wbudowanych bloków kodu.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="4d3e7-106">Ten temat zawiera krótkie wprowadzenie do funkcji Func i Action oraz pokazuje, jak używać wyrażeń lambda w bibliotece zadań równoległych i PLINQ.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="4d3e7-107">Aby uzyskać więcej informacji na temat ogólnie delegowanych delegatów, zobacz [delegats](../../csharp/programming-guide/delegates/index.md) and [delegats](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="4d3e7-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="4d3e7-108">Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C# i Visual Basic, zobacz [wyrażenia lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) i [wyrażenia lambda](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4d3e7-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="4d3e7-109">Obiekt delegowany Func</span><span class="sxs-lookup"><span data-stu-id="4d3e7-109">Func Delegate</span></span>

<span data-ttu-id="4d3e7-110">`Func`Delegat hermetyzuje metodę, która zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="4d3e7-111">W `Func` podpisie, ostatni lub po prawej stronie, parametr typu zawsze określa typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="4d3e7-112">Jedną z typowych przyczyn błędów kompilatora jest próba przekazania dwóch parametrów wejściowych do <xref:System.Func%602?displayProperty=nameWithType> ; w rzeczywistości ten typ przyjmuje tylko jeden parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="4d3e7-113">Platforma .NET definiuje 17 wersji systemów `Func` : <xref:System.Func%601?displayProperty=nameWithType> , <xref:System.Func%602?displayProperty=nameWithType> , <xref:System.Func%603?displayProperty=nameWithType> i tak dalej <xref:System.Func%6017?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4d3e7-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="4d3e7-114">Delegat akcji</span><span class="sxs-lookup"><span data-stu-id="4d3e7-114">Action Delegate</span></span>

<span data-ttu-id="4d3e7-115"><xref:System.Action?displayProperty=nameWithType>Delegat hermetyzuje metodę (sub in Visual Basic), która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="4d3e7-116">W `Action` sygnaturze typu parametry typu reprezentują tylko parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="4d3e7-117">Podobnie jak `Func` platforma .NET definiuje 17 wersji programu `Action` , z wersji, która nie ma parametrów typu w górę za pośrednictwem wersji zawierającej 16 parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="4d3e7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d3e7-118">Example</span></span>

<span data-ttu-id="4d3e7-119">Poniższy przykład dla <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metody pokazuje, jak przedstawić delegatów funkcji Func i Action przy użyciu wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="4d3e7-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="4d3e7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d3e7-120">See also</span></span>

- [<span data-ttu-id="4d3e7-121">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="4d3e7-121">Parallel Programming</span></span>](index.md)
