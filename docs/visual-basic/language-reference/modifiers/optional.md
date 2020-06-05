---
title: Opcjonalne
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: c46d06dba61158d7362d736731161be306af3f10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392148"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="a9b06-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9b06-102">Optional (Visual Basic)</span></span>

<span data-ttu-id="a9b06-103">Określa, że argument procedury może zostać pominięty, gdy procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a9b06-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9b06-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9b06-104">Remarks</span></span>

<span data-ttu-id="a9b06-105">Dla każdego opcjonalnego parametru należy określić wyrażenie stałe jako wartość domyślną tego parametru.</span><span class="sxs-lookup"><span data-stu-id="a9b06-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="a9b06-106">Jeśli wyrażenie zwróci wartość [Nothing](../nothing.md), wartością domyślną parametru typ danych jest jako wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="a9b06-106">If the expression evaluates to [Nothing](../nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="a9b06-107">Jeśli lista parametrów zawiera opcjonalny parametr, każdy parametr, który następuje po nim musi być również opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="a9b06-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="a9b06-108">`Optional`Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="a9b06-108">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="a9b06-109">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9b06-109">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="a9b06-110">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9b06-110">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="a9b06-111">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9b06-111">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="a9b06-112">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9b06-112">Sub Statement</span></span>](../statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="a9b06-113">Podczas wywoływania procedury z parametrami opcjonalnymi lub bez nich można przekazać argumenty według pozycji lub według nazwy.</span><span class="sxs-lookup"><span data-stu-id="a9b06-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="a9b06-114">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="a9b06-114">For more information, see [Passing Arguments by Position and by Name](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a9b06-115">Można także zdefiniować procedurę z opcjonalnymi parametrami przy użyciu przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="a9b06-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="a9b06-116">Jeśli masz jeden opcjonalny parametr, możesz zdefiniować dwie przeciążone wersje procedury, jedną, która akceptuje parametr i jeden, który nie jest.</span><span class="sxs-lookup"><span data-stu-id="a9b06-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="a9b06-117">Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](../../programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="a9b06-117">For more information, see [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="a9b06-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9b06-118">Example</span></span>

<span data-ttu-id="a9b06-119">W poniższym przykładzie zdefiniowano procedurę, która ma opcjonalny parametr.</span><span class="sxs-lookup"><span data-stu-id="a9b06-119">The following example defines a procedure that has an optional parameter.</span></span>

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a><span data-ttu-id="a9b06-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9b06-120">Example</span></span>

<span data-ttu-id="a9b06-121">W poniższym przykładzie pokazano, jak wywołać procedurę z argumentami przekazaną przez pozycję i z argumentami przekazaną przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="a9b06-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="a9b06-122">Procedura ma dwa parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a9b06-122">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="a9b06-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9b06-123">See also</span></span>

- [<span data-ttu-id="a9b06-124">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="a9b06-124">Parameter List</span></span>](../statements/parameter-list.md)
- [<span data-ttu-id="a9b06-125">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="a9b06-125">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="a9b06-126">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="a9b06-126">Keywords</span></span>](../keywords/index.md)
