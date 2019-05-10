---
title: Optional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 40605d4843bfccf9d2819b3ec6f2ef65f9e9cf9a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661329"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="8fea0-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fea0-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="8fea0-103">Określa, czy argumentu procedury, można pominąć, jeśli procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8fea0-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fea0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fea0-104">Remarks</span></span>  
 <span data-ttu-id="8fea0-105">Dla każdego opcjonalnego parametru należy określić wyrażenie stałe, wartością domyślną tego parametru.</span><span class="sxs-lookup"><span data-stu-id="8fea0-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="8fea0-106">Jeśli wyrażenie ma [nic](../../../visual-basic/language-reference/nothing.md), wartością domyślną typu danych wartość jest używana jako wartość domyślna parametru.</span><span class="sxs-lookup"><span data-stu-id="8fea0-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="8fea0-107">Jeśli lista parametrów zawiera parametr opcjonalny, każdy parametr, który po nim następuje również musi być opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8fea0-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="8fea0-108">`Optional` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="8fea0-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="8fea0-109">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8fea0-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="8fea0-110">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8fea0-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="8fea0-111">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="8fea0-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="8fea0-112">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8fea0-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="8fea0-113">Podczas wywoływania procedury z lub bez parametrów opcjonalnych, istnieje możliwość przekazywania argumentów według pozycji i według nazwy.</span><span class="sxs-lookup"><span data-stu-id="8fea0-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="8fea0-114">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="8fea0-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fea0-115">Aby zdefiniować procedury z opcjonalnymi parametrami, można również za pomocą przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="8fea0-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="8fea0-116">Jeśli masz jeden parametr opcjonalny, można zdefiniować dwie przeciążone wersje procedury, taki, który akceptuje parametr i jedną, która nie.</span><span class="sxs-lookup"><span data-stu-id="8fea0-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="8fea0-117">Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="8fea0-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fea0-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fea0-118">Example</span></span>  
 <span data-ttu-id="8fea0-119">W poniższym przykładzie zdefiniowano procedury, która ma parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8fea0-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="8fea0-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fea0-120">Example</span></span>  
 <span data-ttu-id="8fea0-121">Poniższy przykład pokazuje, jak wywołać procedurę z argumenty przekazywane według pozycji i argumenty przekazywane według nazwy.</span><span class="sxs-lookup"><span data-stu-id="8fea0-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="8fea0-122">Procedura nie zawiera dwa parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8fea0-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="8fea0-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fea0-123">See also</span></span>

- [<span data-ttu-id="8fea0-124">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="8fea0-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="8fea0-125">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="8fea0-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="8fea0-126">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8fea0-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
