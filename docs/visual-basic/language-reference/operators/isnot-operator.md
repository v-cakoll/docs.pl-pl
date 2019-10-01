---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 32e8f9532244679d2994b0e3d98279d75f7e77b4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701038"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="d7f17-102">IsNot — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7f17-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="d7f17-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="d7f17-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7f17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7f17-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="d7f17-105">Części</span><span class="sxs-lookup"><span data-stu-id="d7f17-105">Parts</span></span>
 <span data-ttu-id="d7f17-106">`result` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d7f17-106">`result` Required.</span></span> <span data-ttu-id="d7f17-107">Wartość `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d7f17-107">A `Boolean` value.</span></span>

 <span data-ttu-id="d7f17-108">`object1` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d7f17-108">`object1` Required.</span></span> <span data-ttu-id="d7f17-109">Dowolna zmienna lub wyrażenie `Object`.</span><span class="sxs-lookup"><span data-stu-id="d7f17-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="d7f17-110">`object2` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d7f17-110">`object2` Required.</span></span> <span data-ttu-id="d7f17-111">Dowolna zmienna lub wyrażenie `Object`.</span><span class="sxs-lookup"><span data-stu-id="d7f17-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7f17-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7f17-112">Remarks</span></span>
 <span data-ttu-id="d7f17-113">Operator `IsNot` Określa, czy dwa odwołania do obiektów odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d7f17-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="d7f17-114">Jednak nie wykonuje porównania wartości.</span><span class="sxs-lookup"><span data-stu-id="d7f17-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="d7f17-115">Jeśli `object1` i `object2` odwołują się do dokładnie tego samego wystąpienia obiektu, `result` jest `False`; Jeśli tak nie jest, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="d7f17-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="d7f17-116">`IsNot` jest przeciwieństwem operatora `Is`.</span><span class="sxs-lookup"><span data-stu-id="d7f17-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="d7f17-117">Zaletą `IsNot` jest możliwość uniknięcia składni niewygodna z `Not` i `Is`, co może być trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="d7f17-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="d7f17-118">Można użyć operatorów `Is` i `IsNot` do testowania zarówno obiektów wczesnych, jak i z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="d7f17-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="d7f17-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7f17-119">Example</span></span>
 <span data-ttu-id="d7f17-120">Poniższy przykład kodu używa operatora `Is` i operatora `IsNot` do wykonania tego samego porównania.</span><span class="sxs-lookup"><span data-stu-id="d7f17-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="d7f17-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7f17-121">See also</span></span>

- [<span data-ttu-id="d7f17-122">Is, operator</span><span class="sxs-lookup"><span data-stu-id="d7f17-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="d7f17-123">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="d7f17-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="d7f17-124">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d7f17-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="d7f17-125">Instrukcje: testowanie, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="d7f17-125">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
