---
title: Swobodna konwersja delegatów
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: a581ffae77c496908d2e4e38df53491a54ae2ab8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410673"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="7b9d3-102">Swobodna konwersja delegatów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b9d3-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="7b9d3-103">Swobodna konwersja delegatów umożliwia przypisanie funkcji do delegatów lub programów obsługi nawet wtedy, gdy ich podpisy nie są identyczne.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="7b9d3-104">W związku z tym powiązanie z delegatami jest spójne z powiązaniem, które jest już dozwolone dla wywołań metod.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="7b9d3-105">Parametry i zwracany typ</span><span class="sxs-lookup"><span data-stu-id="7b9d3-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="7b9d3-106">W przypadku dokładnego dopasowania podpisu, Przekształcenie swobodne wymaga spełnienia następujących warunków, gdy `Option Strict` jest ustawiony na `On` :</span><span class="sxs-lookup"><span data-stu-id="7b9d3-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="7b9d3-107">Konwersja rozszerzająca musi istnieć z typu danych każdego parametru delegata na typ danych odpowiadającego mu parametru przypisanej funkcji lub `Sub` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="7b9d3-108">W poniższym przykładzie delegat `Del1` ma jeden parametr, a `Integer` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="7b9d3-109">Parametr `m` w przypisanych wyrażeniach lambda musi mieć typ danych, dla którego istnieje konwersja rozszerzająca z `Integer` , taka jak `Long` lub `Double` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="7b9d3-110">Konwersje zawężające są dozwolone tylko wtedy `Option Strict` , gdy jest ustawiony na `Off` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="7b9d3-111">Konwersja rozszerzająca musi istnieć w odwrotnym kierunku od typu zwraca przypisanej funkcji lub `Sub` do zwracanego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="7b9d3-112">W poniższych przykładach treść każdego przypisanego wyrażenia lambda musi być wynikiem obliczenia na typ danych, który jest poszerzany do, `Integer` ponieważ zwracany typ `del1` to `Integer` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="7b9d3-113">Jeśli `Option Strict` jest ustawiona na `Off` , ograniczenie rozszerzające zostanie usunięte w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="7b9d3-114">Pomijanie specyfikacji parametrów</span><span class="sxs-lookup"><span data-stu-id="7b9d3-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="7b9d3-115">W przypadku delegatów swobodnych można również całkowicie pominąć specyfikacje parametrów w przypisanej metodzie:</span><span class="sxs-lookup"><span data-stu-id="7b9d3-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="7b9d3-116">Należy pamiętać, że nie można określić niektórych parametrów i pominąć innych.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="7b9d3-117">Możliwość pominięcia parametrów jest przydatna w sytuacji, takiej jak Definiowanie procedury obsługi zdarzeń, w której występuje kilka złożonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="7b9d3-118">Argumenty niektórych programów obsługi zdarzeń nie są używane.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="7b9d3-119">Zamiast tego program obsługi bezpośrednio uzyskuje dostęp do stanu kontrolki, w której zdarzenie jest zarejestrowane, i ignoruje argumenty.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="7b9d3-120">W przypadku delegatów swobodnych można pominąć argumenty w takich deklaracjach, gdy nie niejasności wyników.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="7b9d3-121">W poniższym przykładzie, w pełni określona metoda `OnClick` można napisać ponownie jako `RelaxedOnClick` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="7b9d3-122">Przykłady AddressOf</span><span class="sxs-lookup"><span data-stu-id="7b9d3-122">AddressOf Examples</span></span>  
 <span data-ttu-id="7b9d3-123">Wyrażenia lambda są używane w poprzednich przykładach, aby można było łatwo zobaczyć relacje typu.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="7b9d3-124">Jednak te same złagodzenia są dozwolone dla przypisań delegatów korzystających z `AddressOf` , `Handles` lub `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="7b9d3-125">W poniższym przykładzie funkcje `f1` , `f2` , `f3` i `f4` mogą być przypisane do `Del1` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="7b9d3-126">Poniższy przykład jest prawidłowy tylko wtedy, gdy `Option Strict` jest ustawiony na `Off` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="7b9d3-127">Funkcja upuszczania zwraca</span><span class="sxs-lookup"><span data-stu-id="7b9d3-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="7b9d3-128">Swobodna konwersja delegatów umożliwia przypisanie funkcji do `Sub` delegata, co w efekcie ignorowanie wartości zwracanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="7b9d3-129">Nie można jednak przypisać `Sub` do delegata funkcji.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="7b9d3-130">W poniższym przykładzie adres funkcji `doubler` jest przypisany do `Sub` obiektu delegowanego `Del3` .</span><span class="sxs-lookup"><span data-stu-id="7b9d3-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="7b9d3-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b9d3-131">See also</span></span>

- [<span data-ttu-id="7b9d3-132">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="7b9d3-132">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="7b9d3-133">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="7b9d3-133">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="7b9d3-134">Delegaci</span><span class="sxs-lookup"><span data-stu-id="7b9d3-134">Delegates</span></span>](index.md)
- [<span data-ttu-id="7b9d3-135">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b9d3-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="7b9d3-136">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="7b9d3-136">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="7b9d3-137">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="7b9d3-137">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
