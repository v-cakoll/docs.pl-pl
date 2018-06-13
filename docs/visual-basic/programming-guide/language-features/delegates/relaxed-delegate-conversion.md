---
title: Swobodna konwersja delegatów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: c4a41bf74716a6ea7d3c1139651834acccf27657
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650832"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="f83ae-102">Swobodna konwersja delegatów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f83ae-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="f83ae-103">Swobodna konwersja delegatów umożliwia przypisanie subskrypcji i funkcji do delegatów lub obsługi, nawet wtedy, gdy ich podpisów nie są identyczne.</span><span class="sxs-lookup"><span data-stu-id="f83ae-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="f83ae-104">W związku z tym powiązanie do obiektów delegowanych staje się spójne z powiązaniem już dozwolone dla wywołań metod.</span><span class="sxs-lookup"><span data-stu-id="f83ae-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="f83ae-105">Parametry oraz zwracany typ</span><span class="sxs-lookup"><span data-stu-id="f83ae-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="f83ae-106">Zamiast podpisu dokładnego dopasowania, swobodna konwersja wymaga spełnienia następujących warunków podczas `Option Strict` ma ustawioną wartość `On`:</span><span class="sxs-lookup"><span data-stu-id="f83ae-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="f83ae-107">Konwersję rozszerzającą musi istnieć od każdego parametru delegowanego typu danych na typ danych odpowiadającego mu parametru funkcji przypisanej lub `Sub`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="f83ae-108">W poniższym przykładzie, delegat `Del1` ma jeden parametr `Integer`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="f83ae-109">Parametr `m` w przypisanej lambda wyrażenia musi mieć typ danych, dla którego jest konwersję rozszerzającą z `Integer`, takich jak `Long` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     <span data-ttu-id="f83ae-110">Konwersji zawężającej są dozwolone tylko wtedy, gdy `Option Strict` ma ustawioną wartość `Off`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   <span data-ttu-id="f83ae-111">Konwersję rozszerzającą musi istnieć w przeciwnym kierunku z zwracany typ funkcji przypisanej lub `Sub` na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="f83ae-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="f83ae-112">W poniższych przykładach treści każde wyrażenie lambda przypisanej musi być typem danych rozszerzająca do `Integer` ponieważ zwracany typ funkcji `del1` jest `Integer`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 <span data-ttu-id="f83ae-113">Jeśli `Option Strict` ma ustawioną wartość `Off`, rozszerzanie ograniczenie zostało usunięte w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="f83ae-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="f83ae-114">Pominięcie specyfikacji parametru</span><span class="sxs-lookup"><span data-stu-id="f83ae-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="f83ae-115">Swobodna delegatów pozwalają również całkowicie pominąć specyfikacje parametru w metodzie przypisanej:</span><span class="sxs-lookup"><span data-stu-id="f83ae-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 <span data-ttu-id="f83ae-116">Należy pamiętać, nie można określić niektóre parametry i Pomiń innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f83ae-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 <span data-ttu-id="f83ae-117">Pomiń parametry jest przydatne w sytuacji, takie jak Definiowanie obsługi zdarzeń, w którym są związane z kilku parametrów złożonych.</span><span class="sxs-lookup"><span data-stu-id="f83ae-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="f83ae-118">Argumenty do niektórych programów obsługi zdarzeń nie są używane.</span><span class="sxs-lookup"><span data-stu-id="f83ae-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="f83ae-119">Zamiast tego program obsługi bezpośredni dostęp do stanu formantu, na którym zdarzenie jest zarejestrowany i ignoruje argumentów.</span><span class="sxs-lookup"><span data-stu-id="f83ae-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="f83ae-120">Swobodna delegatów umożliwiają Pomiń argumentów oświadczenia, jeśli żadnego wyniku niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="f83ae-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="f83ae-121">W poniższym przykładzie pełni określonej metody `OnClick` można przepisany `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="f83ae-122">Przykłady AddressOf</span><span class="sxs-lookup"><span data-stu-id="f83ae-122">AddressOf Examples</span></span>  
 <span data-ttu-id="f83ae-123">Wyrażenia lambda są używane w poprzednich przykładach ułatwia Zobacz relacje typu.</span><span class="sxs-lookup"><span data-stu-id="f83ae-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="f83ae-124">Jednak sam złagodzenie są dozwolone dla przypisania delegata, które używają `AddressOf`, `Handles`, lub `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="f83ae-125">W poniższym przykładzie funkcje `f1`, `f2`, `f3`, i `f4` wszystkie można przypisać do `Del1`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 <span data-ttu-id="f83ae-126">Poniższy przykład jest prawidłowe tylko w przypadku `Option Strict` ma ustawioną wartość `Off`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="f83ae-127">Porzucanie zwraca — funkcja</span><span class="sxs-lookup"><span data-stu-id="f83ae-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="f83ae-128">Swobodna konwersja delegatów umożliwia przypisanie funkcji, aby `Sub` delegata, efektywnie ignorowanie zwracana wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="f83ae-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="f83ae-129">Jednak nie można przypisać `Sub` do delegata funkcji.</span><span class="sxs-lookup"><span data-stu-id="f83ae-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="f83ae-130">W poniższym przykładzie adresu funkcji `doubler` jest przypisany do `Sub` delegować `Del3`.</span><span class="sxs-lookup"><span data-stu-id="f83ae-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f83ae-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f83ae-131">See Also</span></span>  
 [<span data-ttu-id="f83ae-132">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="f83ae-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="f83ae-133">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="f83ae-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="f83ae-134">Delegaci</span><span class="sxs-lookup"><span data-stu-id="f83ae-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="f83ae-135">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f83ae-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="f83ae-136">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="f83ae-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="f83ae-137">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f83ae-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
