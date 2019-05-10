---
title: Swobodna konwersja delegatów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ac1246764d26d694d10b817b9195b13169d6d9be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651272"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="4b39f-102">Swobodna konwersja delegatów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b39f-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="4b39f-103">Swobodna konwersja delegatów umożliwia przypisywanie subskrypcji i funkcji do delegatów lub programów obsługi, nawet wtedy, gdy ich podpisy nie są identyczne.</span><span class="sxs-lookup"><span data-stu-id="4b39f-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="4b39f-104">W związku z tym powiązania do obiektów delegowanych staje się spójne z powiązaniem już dozwolone w przypadku wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="4b39f-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="4b39f-105">Parametry oraz zwracany typ</span><span class="sxs-lookup"><span data-stu-id="4b39f-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="4b39f-106">Zamiast podpisu dokładne dopasowanie, swobodna konwersja wymaga spełnienia następujących warunków podczas `Option Strict` ustawiono `On`:</span><span class="sxs-lookup"><span data-stu-id="4b39f-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="4b39f-107">Konwersję rozszerzającą musi istnieć typ danych każdego parametru na typ danych w odpowiadającym jej parametrze w funkcji przypisane lub `Sub`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="4b39f-108">W poniższym przykładzie, delegat `Del1` ma jeden parametr `Integer`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="4b39f-109">Parametr `m` w przypisanych lambda wyrażenia muszą mieć typ danych, dla którego jest konwersją rozszerzającą z `Integer`, takich jak `Long` lub `Double`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="4b39f-110">Konwersje zawężające są dozwolone tylko wtedy, gdy `Option Strict` ustawiono `Off`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="4b39f-111">Konwersję rozszerzającą musi istnieć w odwrotnym kierunku ze zwracanego typu funkcji przypisane lub `Sub` zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="4b39f-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="4b39f-112">W poniższych przykładach treści każde wyrażenie lambda przypisane musi być typu danych, która rozszerza się na `Integer` ponieważ zwracany typ metody `del1` jest `Integer`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="4b39f-113">Jeśli `Option Strict` ustawiono `Off`, rozszerzanie ograniczeń zostanie usunięta w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="4b39f-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="4b39f-114">Pominięcie specyfikacji parametru</span><span class="sxs-lookup"><span data-stu-id="4b39f-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="4b39f-115">Obniżone delegaty umożliwiają również całkowicie pominąć parametr specyfikacji w przypisanej metodzie:</span><span class="sxs-lookup"><span data-stu-id="4b39f-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="4b39f-116">Należy pamiętać, nie można określić niektóre parametry i pominąć innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4b39f-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="4b39f-117">Zdolność do pominięcia parametrów jest przydatne w sytuacji, takich jak definiowanie program obsługi zdarzeń, w której kilka parametrów złożone są zaangażowane.</span><span class="sxs-lookup"><span data-stu-id="4b39f-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="4b39f-118">Argumenty, które mają niektóre procedury obsługi zdarzeń nie są używane.</span><span class="sxs-lookup"><span data-stu-id="4b39f-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="4b39f-119">Zamiast tego program obsługi bezpośrednio uzyskuje dostęp do stanu kontrolki, w którym zdarzenie jest zarejestrowany i ignoruje argumenty.</span><span class="sxs-lookup"><span data-stu-id="4b39f-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="4b39f-120">Obniżone delegaty umożliwiają pominięcie argumentów w takich deklaracji, gdy brak wyniku niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="4b39f-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="4b39f-121">W poniższym przykładzie w pełni określonej metody `OnClick` może być napisany `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="4b39f-122">Przykłady AddressOf</span><span class="sxs-lookup"><span data-stu-id="4b39f-122">AddressOf Examples</span></span>  
 <span data-ttu-id="4b39f-123">Wyrażenia lambda są używane w poprzednich przykładach ułatwia Zobacz relacje typów.</span><span class="sxs-lookup"><span data-stu-id="4b39f-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="4b39f-124">Jednak sam złagodzenie są dozwolone dla przypisania delegata, które używają `AddressOf`, `Handles`, lub `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="4b39f-125">W poniższym przykładzie funkcje `f1`, `f2`, `f3`, i `f4` wszystkie można przypisać do `Del1`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="4b39f-126">Poniższy przykład jest prawidłowy tylko wtedy, gdy `Option Strict` ustawiono `Off`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="4b39f-127">Upuszczanie zwraca — funkcja</span><span class="sxs-lookup"><span data-stu-id="4b39f-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="4b39f-128">Swobodna konwersja delegatów umożliwia przypisanie funkcja `Sub` delegata, efektywnie ignorowanie wartości zwracanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b39f-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="4b39f-129">Jednak nie można przypisać `Sub` delegata funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b39f-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="4b39f-130">W poniższym przykładzie adresu funkcji `doubler` jest przypisany do `Sub` delegować `Del3`.</span><span class="sxs-lookup"><span data-stu-id="4b39f-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="4b39f-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b39f-131">See also</span></span>

- [<span data-ttu-id="4b39f-132">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="4b39f-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="4b39f-133">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="4b39f-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="4b39f-134">Delegaty</span><span class="sxs-lookup"><span data-stu-id="4b39f-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="4b39f-135">Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b39f-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="4b39f-136">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="4b39f-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="4b39f-137">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4b39f-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
