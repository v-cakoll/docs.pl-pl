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
ms.openlocfilehash: 4e5be295a52edc1a7f0a0a3aa98f55335ae3e31b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453003"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="56392-102">Wyrażenia Lambda w PLINQ i TPL</span><span class="sxs-lookup"><span data-stu-id="56392-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="56392-103">Biblioteka równoległa zadania (TPL) zawiera wiele <xref:System.Func%601?displayProperty=nameWithType> metod, które biorą jeden z lub <xref:System.Action?displayProperty=nameWithType> rodziny delegatów jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="56392-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="56392-104">Ci pełnomocnicy są używane do przekazywania w niestandardowej logiki programu do pętli równoległej, zadania lub kwerendy.</span><span class="sxs-lookup"><span data-stu-id="56392-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="56392-105">Przykłady kodu dla TPL, a także PLINQ używać wyrażeń lambda do tworzenia wystąpień tych delegatów jako bloki kodu liniowego.</span><span class="sxs-lookup"><span data-stu-id="56392-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="56392-106">W tym temacie przedstawiono krótkie wprowadzenie do Func i Action i pokazano, jak używać wyrażeń lambda w bibliotece równoległej zadania i PLINQ.</span><span class="sxs-lookup"><span data-stu-id="56392-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="56392-107">Aby uzyskać więcej informacji na temat delegatów w ogóle, zobacz [delegatów](../../csharp/programming-guide/delegates/index.md) i [delegatów](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="56392-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="56392-108">Aby uzyskać więcej informacji na temat wyrażeń lambda w językach C# i Visual Basic, zobacz [Wyrażenia Lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) i [wyrażenia Lambda](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="56392-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="56392-109">Delegat Func</span><span class="sxs-lookup"><span data-stu-id="56392-109">Func Delegate</span></span>

<span data-ttu-id="56392-110">Pełnomocnik `Func` hermetyzuje metodę, która zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="56392-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="56392-111">W `Func` podpisie ostatni lub prawy parametr typu zawsze określa typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="56392-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="56392-112">Jedną z typowych przyczyn błędów kompilatora jest <xref:System.Func%602?displayProperty=nameWithType>próba przekazania w dwóch parametrów wejściowych do ; w rzeczywistości ten typ przyjmuje tylko jeden parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="56392-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="56392-113">.NET definiuje 17 `Func`wersji <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Func%602?displayProperty=nameWithType>: <xref:System.Func%603?displayProperty=nameWithType>, , i <xref:System.Func%6017?displayProperty=nameWithType>tak dalej przez .</span><span class="sxs-lookup"><span data-stu-id="56392-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="56392-114">Pełnomocnik akcji</span><span class="sxs-lookup"><span data-stu-id="56392-114">Action Delegate</span></span>

<span data-ttu-id="56392-115">Delegat <xref:System.Action?displayProperty=nameWithType> hermetyzuje metodę (Sub w języku Visual Basic), która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="56392-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="56392-116">W `Action` podpisie typu parametry typu reprezentują tylko parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="56392-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="56392-117">Podobnie `Func`jak . . `Action`</span><span class="sxs-lookup"><span data-stu-id="56392-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="56392-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="56392-118">Example</span></span>

<span data-ttu-id="56392-119">Poniższy przykład dla <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metody pokazuje, jak wyrazić zarówno Func i Action delegatów przy użyciu wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="56392-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="56392-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56392-120">See also</span></span>

- [<span data-ttu-id="56392-121">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="56392-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
