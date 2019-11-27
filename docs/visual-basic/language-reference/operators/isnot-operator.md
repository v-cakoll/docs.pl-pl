---
title: Operator IsNot
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336075"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="39401-102">IsNot — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39401-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="39401-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="39401-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="39401-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39401-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="39401-105">Części</span><span class="sxs-lookup"><span data-stu-id="39401-105">Parts</span></span>
 <span data-ttu-id="39401-106">Wymagane `result`.</span><span class="sxs-lookup"><span data-stu-id="39401-106">`result` Required.</span></span> <span data-ttu-id="39401-107">Wartość `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="39401-107">A `Boolean` value.</span></span>

 <span data-ttu-id="39401-108">Wymagane `object1`.</span><span class="sxs-lookup"><span data-stu-id="39401-108">`object1` Required.</span></span> <span data-ttu-id="39401-109">Dowolna `Object` zmienna lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="39401-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="39401-110">Wymagane `object2`.</span><span class="sxs-lookup"><span data-stu-id="39401-110">`object2` Required.</span></span> <span data-ttu-id="39401-111">Dowolna `Object` zmienna lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="39401-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="39401-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39401-112">Remarks</span></span>
 <span data-ttu-id="39401-113">Operator `IsNot` określa, czy dwa odwołania do obiektów odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="39401-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="39401-114">Jednak nie wykonuje porównania wartości.</span><span class="sxs-lookup"><span data-stu-id="39401-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="39401-115">Jeśli `object1` i `object2` oba odnoszą się do tego samego wystąpienia obiektu, `result` jest `False`; Jeśli tak nie jest, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="39401-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="39401-116">`IsNot` jest przeciwieństwem operatora `Is`.</span><span class="sxs-lookup"><span data-stu-id="39401-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="39401-117">Zaletą `IsNot` jest możliwość uniknięcia składni niewygodna z `Not` i `Is`, co może być trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="39401-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="39401-118">Można użyć operatorów `Is` i `IsNot` do testowania zarówno obiektów wczesnych, jak i z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="39401-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="39401-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="39401-119">Example</span></span>
 <span data-ttu-id="39401-120">Poniższy przykład kodu używa operatora `Is` i operatora `IsNot` do wykonania tego samego porównania.</span><span class="sxs-lookup"><span data-stu-id="39401-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="39401-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39401-121">See also</span></span>

- [<span data-ttu-id="39401-122">Is, operator</span><span class="sxs-lookup"><span data-stu-id="39401-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="39401-123">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="39401-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="39401-124">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39401-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="39401-125">Instrukcje: testowanie, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="39401-125">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
