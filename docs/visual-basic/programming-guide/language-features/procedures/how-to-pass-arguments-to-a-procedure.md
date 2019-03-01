---
title: 'Instrukcje: Przekazywanie argumentów do procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: 0bc7c9d09922b7fbef534e6b58389ca343cc1e13
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974396"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="20a0d-102">Instrukcje: Przekazywanie argumentów do procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20a0d-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="20a0d-103">Po wywołaniu procedury, należy wykonać Nazwa procedury z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="20a0d-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="20a0d-104">Należy podać argument odpowiadający każdego wymaganego parametru definiuje procedurę i opcjonalnie można podać argumenty do `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="20a0d-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="20a0d-105">Jeśli nie podasz `Optional` parametr w wywołaniu musi zawierać przecinek, aby oznaczyć jego miejsce na liście argumentów, jeśli są podawania wszystkie pozostałe argumenty.</span><span class="sxs-lookup"><span data-stu-id="20a0d-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="20a0d-106">Jeśli zamierzasz przekazać argumentu o typie danych innym niż odpowiadającego mu parametru takich jak `Byte` do `String`, można ustawić przełącznik kontrola typów ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) do `Off`.</span><span class="sxs-lookup"><span data-stu-id="20a0d-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="20a0d-107">Jeśli `Option Strict` jest `On`, należy użyć poszerzenia konwersje lub słowa kluczowe konwersji jawnej.</span><span class="sxs-lookup"><span data-stu-id="20a0d-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="20a0d-108">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i [funkcje konwersji typu](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="20a0d-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="20a0d-109">Aby uzyskać więcej informacji, zobacz [parametry i argumenty procedur](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="20a0d-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="20a0d-110">Aby przekazać jeden lub więcej argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="20a0d-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="20a0d-111">W instrukcji wywołujące postępuj zgodnie z nazwy procedury za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="20a0d-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="20a0d-112">Wewnątrz nawiasów umieść listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="20a0d-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="20a0d-113">Obejmują argument dla każdego wymaganego parametru definiuje procedurę i należy je oddzielić przecinkami.</span><span class="sxs-lookup"><span data-stu-id="20a0d-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="20a0d-114">Upewnij się, że każdy argument jest prawidłowe wyrażenie obliczane do typu danych można przekonwertować na typ procedury definiuje odpowiadającego mu parametru.</span><span class="sxs-lookup"><span data-stu-id="20a0d-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="20a0d-115">Jeśli parametr jest zdefiniowany jako [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md), możesz włączyć ją na liście argumentów lub Pomiń ją.</span><span class="sxs-lookup"><span data-stu-id="20a0d-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="20a0d-116">Jeśli ten parametr zostanie pominięty, w procedurze użyto wartości domyślnej zdefiniowanej dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="20a0d-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="20a0d-117">Jeżeli pominięto argument `Optional` parametru i ma inny parametr po liście parametrów, można oznaczyć miejsce pominięty argument przez dodatkowy przecinek na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="20a0d-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="20a0d-118">Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.</span><span class="sxs-lookup"><span data-stu-id="20a0d-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="20a0d-119">Poprzedni przykład dostarcza wymagane pierwszego argumentu, czyli ciąg komunikatu, które mają być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="20a0d-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="20a0d-120">Pomija argument opcjonalny drugi parametr, który określa przyciski, które mają być wyświetlane w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="20a0d-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="20a0d-121">Ponieważ to wywołanie nie dostarcza wartość `MsgBox` użyje wartości domyślnej `MsgBoxStyle.OKOnly`, powoduje wyświetlenie tylko **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="20a0d-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="20a0d-122">Drugi przecinek w liście argumentów oznacza miejsce pominięty drugi argument, a ostatni ciąg jest przekazywany do opcjonalny trzeci parametr `MsgBox`, który jest tekst, który ma być wyświetlany na pasku tytułu.</span><span class="sxs-lookup"><span data-stu-id="20a0d-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a0d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20a0d-123">See also</span></span>

- [<span data-ttu-id="20a0d-124">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="20a0d-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="20a0d-125">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="20a0d-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="20a0d-126">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="20a0d-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="20a0d-127">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="20a0d-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="20a0d-128">Instrukcje: Definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="20a0d-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="20a0d-129">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="20a0d-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="20a0d-130">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="20a0d-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="20a0d-131">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="20a0d-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="20a0d-132">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="20a0d-132">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="20a0d-133">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20a0d-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
