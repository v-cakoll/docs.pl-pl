---
title: '&amp;= — Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: db42f7be7225b866eacf5b73066754e91cd1a0f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371989"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="7bb25-102">&amp;= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bb25-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="7bb25-103">Łączy `String` wyrażenie ze `String` zmienną lub właściwością i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="7bb25-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bb25-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="7bb25-105">Części</span><span class="sxs-lookup"><span data-stu-id="7bb25-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="7bb25-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="7bb25-106">Required.</span></span> <span data-ttu-id="7bb25-107">Dowolna `String` zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="7bb25-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="7bb25-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="7bb25-108">Required.</span></span> <span data-ttu-id="7bb25-109">Dowolne `String` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="7bb25-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bb25-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bb25-110">Remarks</span></span>  
 <span data-ttu-id="7bb25-111">Element po lewej stronie `&=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="7bb25-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="7bb25-112">Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="7bb25-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="7bb25-113">`&=`Operator łączy `String` wyrażenie po prawej stronie ze `String` zmienną lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="7bb25-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7bb25-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="7bb25-114">Overloading</span></span>  
 <span data-ttu-id="7bb25-115">[Operator&](concatenation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="7bb25-115">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7bb25-116">Przeciążanie `&` operatora ma wpływ na zachowanie `&=` operatora.</span><span class="sxs-lookup"><span data-stu-id="7bb25-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="7bb25-117">Jeśli kod korzysta z `&=` klasy lub struktury, która przeciążania `&` , należy poznać jej ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="7bb25-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7bb25-118">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7bb25-118">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bb25-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="7bb25-119">Example</span></span>  
 <span data-ttu-id="7bb25-120">Poniższy przykład używa operatora, `&=` Aby połączyć dwie `String` zmienne i przypisać wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7bb25-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7bb25-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bb25-121">See also</span></span>

- [<span data-ttu-id="7bb25-122">Operator&</span><span class="sxs-lookup"><span data-stu-id="7bb25-122">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="7bb25-123">Operator + =</span><span class="sxs-lookup"><span data-stu-id="7bb25-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="7bb25-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="7bb25-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="7bb25-125">Concatenation — Operatory</span><span class="sxs-lookup"><span data-stu-id="7bb25-125">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="7bb25-126">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bb25-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="7bb25-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="7bb25-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="7bb25-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="7bb25-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
