---
title: 'Porady: wymuszanie przekazywania argumentu przez wartość'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 047738a2cbadc6b7d72f41aade22bbeff16d1bac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347593"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="4bc42-102">Porady: wymuszanie przekazywania argumentu przez wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4bc42-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="4bc42-103">Deklaracja procedury określa mechanizm przekazywania.</span><span class="sxs-lookup"><span data-stu-id="4bc42-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="4bc42-104">Jeśli parametr jest zadeklarowany jako [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic oczekuje na przekazanie odpowiadającego argumentu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="4bc42-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="4bc42-105">Pozwala to na zmianę wartości elementu programowania bazowego argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4bc42-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="4bc42-106">Jeśli chcesz chronić podstawowy element przed takimi zmianami, możesz zastąpić mechanizm `ByRef` przekazywaniem w wywołaniu procedury, umieszczając nazwę argumentu w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="4bc42-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="4bc42-107">Nawiasy te są uzupełnieniem nawiasu otaczającego listę argumentów w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="4bc42-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="4bc42-108">Kod wywołujący nie może przesłonić mechanizmu [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) .</span><span class="sxs-lookup"><span data-stu-id="4bc42-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="4bc42-109">Aby wymusić przekazywanie argumentu przez wartość</span><span class="sxs-lookup"><span data-stu-id="4bc42-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="4bc42-110">Jeśli odpowiedni parametr jest zadeklarowany `ByVal` w procedurze, nie trzeba podejmować żadnych dodatkowych kroków.</span><span class="sxs-lookup"><span data-stu-id="4bc42-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="4bc42-111">Visual Basic już oczekuje na przekazanie argumentu przez wartość.</span><span class="sxs-lookup"><span data-stu-id="4bc42-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="4bc42-112">Jeśli odpowiedni parametr jest zadeklarowany `ByRef` w procedurze, należy ująć argument w nawiasy w wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="4bc42-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bc42-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bc42-113">Example</span></span>  
 <span data-ttu-id="4bc42-114">Poniższy przykład zastępuje deklarację parametru `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="4bc42-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="4bc42-115">W wywołaniu, które wymusza `ByVal`, należy pamiętać o dwóch poziomach nawiasów.</span><span class="sxs-lookup"><span data-stu-id="4bc42-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="4bc42-116">Gdy `str` jest ujęta w dodatkowe nawiasy na liście argumentów, procedura `setNewString` nie może zmienić jej wartości w kodzie wywołującym, a `MsgBox` wyświetla "nie można zastąpić w przypadku pomyślnego ByVal".</span><span class="sxs-lookup"><span data-stu-id="4bc42-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="4bc42-117">Gdy `str` nie jest ujęta w dodatkowe nawiasy, procedura może go zmienić, a `MsgBox` wyświetla "jest to nowa wartość argumentu unstring".</span><span class="sxs-lookup"><span data-stu-id="4bc42-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="4bc42-118">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="4bc42-118">Compile the code</span></span>  
 <span data-ttu-id="4bc42-119">Gdy przekazujesz zmienną według odwołania, musisz użyć słowa kluczowego `ByRef`, aby określić ten mechanizm.</span><span class="sxs-lookup"><span data-stu-id="4bc42-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="4bc42-120">Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości.</span><span class="sxs-lookup"><span data-stu-id="4bc42-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="4bc42-121">Jednak dobrym sposobem programowania jest dołączenie albo słowa kluczowego [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) z każdym zadeklarowanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="4bc42-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="4bc42-122">Ułatwia to odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="4bc42-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4bc42-123">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="4bc42-123">Robust Programming</span></span>  
 <span data-ttu-id="4bc42-124">Jeśli procedura deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), poprawne wykonanie kodu może zależeć od możliwości zmiany podstawowego elementu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="4bc42-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="4bc42-125">Jeśli wywoływany kod zastępuje ten mechanizm wywołujący przez załączanie argumentu w nawiasach lub jeśli przeszedł niemodyfikowalny argument, procedura nie może zmienić elementu bazowego.</span><span class="sxs-lookup"><span data-stu-id="4bc42-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="4bc42-126">Może to spowodować nieoczekiwane wyniki w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4bc42-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4bc42-127">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4bc42-127">.NET Framework Security</span></span>  
 <span data-ttu-id="4bc42-128">Zawsze istnieje potencjalne ryzyko w umożliwieniu procedury zmiany wartości bazowej argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4bc42-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="4bc42-129">Upewnij się, że ta wartość jest zmieniana, i przygotuj się do sprawdzenia jej pod kątem poprawności przed jej użyciem.</span><span class="sxs-lookup"><span data-stu-id="4bc42-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc42-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bc42-130">See also</span></span>

- [<span data-ttu-id="4bc42-131">Procedury</span><span class="sxs-lookup"><span data-stu-id="4bc42-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="4bc42-132">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="4bc42-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="4bc42-133">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="4bc42-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="4bc42-134">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="4bc42-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="4bc42-135">Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="4bc42-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="4bc42-136">Różnice między przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="4bc42-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="4bc42-137">Instrukcje: zmiana wartości argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="4bc42-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="4bc42-138">Instrukcje: ochrona argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="4bc42-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="4bc42-139">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="4bc42-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="4bc42-140">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="4bc42-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
