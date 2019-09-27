---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 7e1ac1004e671f592c03bd44ee7ec2e8cc572933
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331627"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="78887-102">IsNot — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78887-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="78887-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="78887-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="78887-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78887-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="78887-105">Części</span><span class="sxs-lookup"><span data-stu-id="78887-105">Parts</span></span>
 <span data-ttu-id="78887-106">`result` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="78887-106">`result` Required.</span></span> <span data-ttu-id="78887-107">Wartość `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="78887-107">A `Boolean` value.</span></span>

 <span data-ttu-id="78887-108">`object1` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="78887-108">`object1` Required.</span></span> <span data-ttu-id="78887-109">Dowolna zmienna lub wyrażenie `Object`.</span><span class="sxs-lookup"><span data-stu-id="78887-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="78887-110">`object2` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="78887-110">`object2` Required.</span></span> <span data-ttu-id="78887-111">Dowolna zmienna lub wyrażenie `Object`.</span><span class="sxs-lookup"><span data-stu-id="78887-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="78887-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78887-112">Remarks</span></span>
 <span data-ttu-id="78887-113">Operator `IsNot` Określa, czy dwa odwołania do obiektów odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="78887-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="78887-114">Jednak nie wykonuje porównania wartości.</span><span class="sxs-lookup"><span data-stu-id="78887-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="78887-115">Jeśli `object1` i `object2` odwołują się do dokładnie tego samego wystąpienia obiektu, `result` jest `False`; Jeśli tak nie jest, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="78887-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="78887-116">`IsNot` jest przeciwieństwem operatora `Is`.</span><span class="sxs-lookup"><span data-stu-id="78887-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="78887-117">Zaletą `IsNot` jest możliwość uniknięcia składni niewygodna z `Not` i `Is`, co może być trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="78887-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="78887-118">Można użyć operatorów `Is` i `IsNot` do testowania zarówno obiektów wczesnych, jak i z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="78887-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="78887-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="78887-119">Example</span></span>
 <span data-ttu-id="78887-120">Poniższy przykład kodu używa operatora `Is` i operatora `IsNot` do wykonania tego samego porównania.</span><span class="sxs-lookup"><span data-stu-id="78887-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="78887-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78887-121">See also</span></span>

- [<span data-ttu-id="78887-122">Is, operator</span><span class="sxs-lookup"><span data-stu-id="78887-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="78887-123">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="78887-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="78887-124">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78887-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- <span data-ttu-id="78887-125">[Instrukcje: Sprawdź, czy dwa obiekty są takie same, @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="78887-125">[How to: Test Whether Two Objects Are the Same](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)</span></span>
