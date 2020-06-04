---
title: 'Porady: przekazywanie argumentów do procedury'
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
ms.openlocfilehash: 903e05facccd1f2afdf4bb51b200531feb64aa79
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387780"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="c703e-102">Porady: przekazywanie argumentów do procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c703e-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="c703e-103">Po wywołaniu procedury należy użyć nazwy procedury z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="c703e-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="c703e-104">Należy podać argument odpowiadający każdemu wymaganemu parametrowi zdefiniowanej przez procedurę i opcjonalnie dostarczyć argumentów do `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="c703e-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="c703e-105">Jeśli nie podasz `Optional` parametru w wywołaniu, musisz dołączyć przecinek, aby oznaczyć jego miejsce na liście argumentów, jeśli podasz kolejne argumenty.</span><span class="sxs-lookup"><span data-stu-id="c703e-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="c703e-106">Jeśli zamierzasz przekazać argument typu danych innego niż odpowiadający mu parametr, na przykład `Byte` do `String` , można ustawić przełącznik kontroli typu ([Option Strict](../../../language-reference/statements/option-strict-statement.md)) na `Off` .</span><span class="sxs-lookup"><span data-stu-id="c703e-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="c703e-107">Jeśli `Option Strict` jest `On` , musisz użyć rozszerzonych słów kluczowych lub konwersji.</span><span class="sxs-lookup"><span data-stu-id="c703e-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="c703e-108">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md) oraz [funkcji konwersji typów](../../../language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c703e-108">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="c703e-109">Aby uzyskać więcej informacji, zobacz [parametry procedury i argumenty](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="c703e-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="c703e-110">Aby przekazać jeden lub więcej argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="c703e-110">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="c703e-111">W instrukcji wywołującej postępuj według nazwy procedury z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="c703e-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="c703e-112">Umieść listę argumentów wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="c703e-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="c703e-113">Należy dołączyć argument dla każdego wymaganego parametru, który definiuje procedura, i oddzielić argumenty przecinkami.</span><span class="sxs-lookup"><span data-stu-id="c703e-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="c703e-114">Upewnij się, że każdy argument jest prawidłowym wyrażeniem, które oblicza typ danych do przekonwertowania na typ, który procedura definiuje dla odpowiadającego parametru.</span><span class="sxs-lookup"><span data-stu-id="c703e-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="c703e-115">Jeśli parametr jest zdefiniowany jako [opcjonalny](../../../language-reference/modifiers/optional.md), można go umieścić na liście argumentów lub pominąć.</span><span class="sxs-lookup"><span data-stu-id="c703e-115">If a parameter is defined as [Optional](../../../language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="c703e-116">Jeśli zostanie pominięty, procedura używa wartości domyślnej zdefiniowanej dla tego parametru.</span><span class="sxs-lookup"><span data-stu-id="c703e-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="c703e-117">W przypadku pominięcia argumentu dla `Optional` parametru, gdy na liście parametrów istnieje inny parametr, można oznaczyć pominięty argument przez dodatkowy przecinek na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="c703e-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="c703e-118">Poniższy przykład wywołuje <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcję Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c703e-118">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="c703e-119">Powyższy przykład zawiera wymagany pierwszy argument, który jest ciągiem komunikatów do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="c703e-119">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="c703e-120">Pomija argument dla opcjonalnego drugiego parametru, który określa przyciski, które mają być wyświetlane w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c703e-120">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="c703e-121">Ponieważ wywołanie nie dostarcza wartości, `MsgBox` używa wartości domyślnej, `MsgBoxStyle.OKOnly` która wyświetla tylko przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="c703e-121">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="c703e-122">Drugi przecinek na liście argumentów oznacza miejsce pominiętego drugiego argumentu, a ostatni ciąg jest przenoszona do opcjonalnego trzeciego parametru `MsgBox` , który jest tekstem, który ma być wyświetlany na pasku tytułu.</span><span class="sxs-lookup"><span data-stu-id="c703e-122">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c703e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c703e-123">See also</span></span>

- [<span data-ttu-id="c703e-124">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="c703e-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="c703e-125">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="c703e-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="c703e-126">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="c703e-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="c703e-127">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="c703e-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c703e-128">Instrukcje: definiowanie parametru dla procedury</span><span class="sxs-lookup"><span data-stu-id="c703e-128">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="c703e-129">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="c703e-129">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c703e-130">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="c703e-130">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="c703e-131">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="c703e-131">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="c703e-132">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="c703e-132">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="c703e-133">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c703e-133">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
