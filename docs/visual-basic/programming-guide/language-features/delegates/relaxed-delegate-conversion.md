---
title: Swobodna konwersja delegatów
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345217"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="2544c-102">Swobodna konwersja delegatów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2544c-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="2544c-103">Swobodna konwersja delegatów umożliwia przypisanie funkcji do delegatów lub programów obsługi nawet wtedy, gdy ich podpisy nie są identyczne.</span><span class="sxs-lookup"><span data-stu-id="2544c-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="2544c-104">W związku z tym powiązanie z delegatami jest spójne z powiązaniem, które jest już dozwolone dla wywołań metod.</span><span class="sxs-lookup"><span data-stu-id="2544c-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="2544c-105">Parametry i zwracany typ</span><span class="sxs-lookup"><span data-stu-id="2544c-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="2544c-106">W przypadku dokładnego dopasowania podpisu przeprowadzona konwersja wymaga spełnienia następujących warunków, gdy `Option Strict` jest ustawiona na `On`:</span><span class="sxs-lookup"><span data-stu-id="2544c-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="2544c-107">Konwersja rozszerzająca musi istnieć z typu danych każdego parametru delegata na typ danych odpowiadającego mu parametru przypisanej funkcji lub `Sub`.</span><span class="sxs-lookup"><span data-stu-id="2544c-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="2544c-108">W poniższym przykładzie delegat `Del1` ma jeden parametr, `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2544c-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="2544c-109">Parametr `m` w przypisanych wyrażeniach lambda musi mieć typ danych, dla którego istnieje konwersja rozszerzająca z `Integer`, taka jak `Long` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="2544c-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="2544c-110">Konwersje zawężające są dozwolone tylko wtedy, gdy `Option Strict` jest ustawiona na `Off`.</span><span class="sxs-lookup"><span data-stu-id="2544c-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="2544c-111">Konwersja rozszerzająca musi istnieć w odwrotnym kierunku od typu zwracanego przypisanej funkcji lub `Sub` do zwracanego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="2544c-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="2544c-112">W poniższych przykładach treść każdego przypisanego wyrażenia lambda musi być Szacowana do typu danych, który poszerza do `Integer`, ponieważ typ zwracany `del1` jest `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2544c-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="2544c-113">Jeśli `Option Strict` jest ustawiona na `Off`, ograniczenie rozszerzania zostanie usunięte w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="2544c-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="2544c-114">Pomijanie specyfikacji parametrów</span><span class="sxs-lookup"><span data-stu-id="2544c-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="2544c-115">W przypadku delegatów swobodnych można również całkowicie pominąć specyfikacje parametrów w przypisanej metodzie:</span><span class="sxs-lookup"><span data-stu-id="2544c-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="2544c-116">Należy pamiętać, że nie można określić niektórych parametrów i pominąć innych.</span><span class="sxs-lookup"><span data-stu-id="2544c-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="2544c-117">Możliwość pominięcia parametrów jest przydatna w sytuacji, takiej jak Definiowanie procedury obsługi zdarzeń, w której występuje kilka złożonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2544c-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="2544c-118">Argumenty niektórych programów obsługi zdarzeń nie są używane.</span><span class="sxs-lookup"><span data-stu-id="2544c-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="2544c-119">Zamiast tego program obsługi bezpośrednio uzyskuje dostęp do stanu kontrolki, w której zdarzenie jest zarejestrowane, i ignoruje argumenty.</span><span class="sxs-lookup"><span data-stu-id="2544c-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="2544c-120">W przypadku delegatów swobodnych można pominąć argumenty w takich deklaracjach, gdy nie niejasności wyników.</span><span class="sxs-lookup"><span data-stu-id="2544c-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="2544c-121">W poniższym przykładzie w pełni określoną metodę `OnClick` można zapisać jako `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="2544c-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="2544c-122">Przykłady AddressOf</span><span class="sxs-lookup"><span data-stu-id="2544c-122">AddressOf Examples</span></span>  
 <span data-ttu-id="2544c-123">Wyrażenia lambda są używane w poprzednich przykładach, aby można było łatwo zobaczyć relacje typu.</span><span class="sxs-lookup"><span data-stu-id="2544c-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="2544c-124">Jednak te same złagodzenia są dozwolone dla przypisań delegatów korzystających `AddressOf`, `Handles`lub `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="2544c-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="2544c-125">W poniższym przykładzie funkcje `f1`, `f2`, `f3`i `f4` można przypisać do `Del1`.</span><span class="sxs-lookup"><span data-stu-id="2544c-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="2544c-126">Poniższy przykład jest prawidłowy tylko wtedy, gdy `Option Strict` jest ustawiona na `Off`.</span><span class="sxs-lookup"><span data-stu-id="2544c-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="2544c-127">Funkcja upuszczania zwraca</span><span class="sxs-lookup"><span data-stu-id="2544c-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="2544c-128">Swobodna konwersja delegatów umożliwia przypisanie funkcji do `Sub` delegata, co w efekcie ignorowanie wartości zwracanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="2544c-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="2544c-129">Nie można jednak przypisać `Sub` do delegata funkcji.</span><span class="sxs-lookup"><span data-stu-id="2544c-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="2544c-130">W poniższym przykładzie adres funkcji `doubler` jest przypisany do `Sub` delegata `Del3`.</span><span class="sxs-lookup"><span data-stu-id="2544c-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="2544c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2544c-131">See also</span></span>

- [<span data-ttu-id="2544c-132">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2544c-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="2544c-133">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="2544c-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="2544c-134">Delegaci</span><span class="sxs-lookup"><span data-stu-id="2544c-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="2544c-135">Instrukcje: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2544c-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="2544c-136">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="2544c-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="2544c-137">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2544c-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
