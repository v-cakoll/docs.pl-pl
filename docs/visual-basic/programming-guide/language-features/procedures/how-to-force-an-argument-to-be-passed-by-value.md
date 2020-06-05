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
ms.openlocfilehash: 48f7d7afebd76916cba11459532d89d71871c79b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387988"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="ad345-102">Porady: wymuszanie przekazywania argumentu przez wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad345-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="ad345-103">Deklaracja procedury określa mechanizm przekazywania.</span><span class="sxs-lookup"><span data-stu-id="ad345-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="ad345-104">Jeśli parametr jest zadeklarowany jako [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic oczekuje na przekazanie odpowiadającego argumentu przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="ad345-104">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="ad345-105">Pozwala to na zmianę wartości elementu programowania bazowego argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad345-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="ad345-106">Jeśli chcesz chronić podstawowy element przed takimi zmianami, możesz przesłonić `ByRef` mechanizm przekazywania w wywołaniu procedury, umieszczając nazwę argumentu w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="ad345-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="ad345-107">Nawiasy te są uzupełnieniem nawiasu otaczającego listę argumentów w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="ad345-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="ad345-108">Kod wywołujący nie może przesłonić mechanizmu [ByVal](../../../language-reference/modifiers/byval.md) .</span><span class="sxs-lookup"><span data-stu-id="ad345-108">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="ad345-109">Aby wymusić przekazywanie argumentu przez wartość</span><span class="sxs-lookup"><span data-stu-id="ad345-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="ad345-110">Jeśli odpowiedni parametr jest zadeklarowany `ByVal` w procedurze, nie trzeba wykonywać żadnych dodatkowych czynności.</span><span class="sxs-lookup"><span data-stu-id="ad345-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="ad345-111">Visual Basic już oczekuje na przekazanie argumentu przez wartość.</span><span class="sxs-lookup"><span data-stu-id="ad345-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="ad345-112">Jeśli odpowiedni parametr jest zadeklarowany `ByRef` w procedurze, należy ująć argument w nawiasy w wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="ad345-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad345-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad345-113">Example</span></span>  
 <span data-ttu-id="ad345-114">Poniższy przykład zastępuje `ByRef` deklarację parametru.</span><span class="sxs-lookup"><span data-stu-id="ad345-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="ad345-115">W wywołaniu, które wymuszają `ByVal` , należy pamiętać o dwóch poziomach nawiasów.</span><span class="sxs-lookup"><span data-stu-id="ad345-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="ad345-116">Gdy `str` jest ujęta w dodatkowe nawiasy na liście argumentów, `setNewString` procedura nie może zmienić jej wartości w kodzie wywołującym i nie `MsgBox` może zostać zastąpiona, jeśli został zakończony.</span><span class="sxs-lookup"><span data-stu-id="ad345-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="ad345-117">Gdy `str` nie jest ujęty w dodatkowe nawiasy, procedura może je zmienić i `MsgBox` wyświetla "jest to nowa wartość argumentu unstring".</span><span class="sxs-lookup"><span data-stu-id="ad345-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="ad345-118">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="ad345-118">Compile the code</span></span>  
 <span data-ttu-id="ad345-119">Gdy przekazujesz zmienną według odwołania, musisz użyć `ByRef` słowa kluczowego, aby określić ten mechanizm.</span><span class="sxs-lookup"><span data-stu-id="ad345-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="ad345-120">Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości.</span><span class="sxs-lookup"><span data-stu-id="ad345-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="ad345-121">Jednak dobrym sposobem programowania jest dołączenie albo słowa kluczowego [ByVal](../../../language-reference/modifiers/byval.md) lub [ByRef](../../../language-reference/modifiers/byref.md) z każdym zadeklarowanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="ad345-121">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="ad345-122">Ułatwia to odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="ad345-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ad345-123">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ad345-123">Robust Programming</span></span>  
 <span data-ttu-id="ad345-124">Jeśli procedura deklaruje parametr [ByRef](../../../language-reference/modifiers/byref.md), poprawne wykonanie kodu może zależeć od możliwości zmiany podstawowego elementu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="ad345-124">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="ad345-125">Jeśli wywoływany kod zastępuje ten mechanizm wywołujący przez załączanie argumentu w nawiasach lub jeśli przeszedł niemodyfikowalny argument, procedura nie może zmienić elementu bazowego.</span><span class="sxs-lookup"><span data-stu-id="ad345-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="ad345-126">Może to spowodować nieoczekiwane wyniki w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad345-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ad345-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad345-127">.NET Framework Security</span></span>  
 <span data-ttu-id="ad345-128">Zawsze istnieje potencjalne ryzyko w umożliwieniu procedury zmiany wartości bazowej argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad345-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="ad345-129">Upewnij się, że ta wartość jest zmieniana, i przygotuj się do sprawdzenia jej pod kątem poprawności przed jej użyciem.</span><span class="sxs-lookup"><span data-stu-id="ad345-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad345-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad345-130">See also</span></span>

- [<span data-ttu-id="ad345-131">Procedury</span><span class="sxs-lookup"><span data-stu-id="ad345-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ad345-132">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="ad345-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ad345-133">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="ad345-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="ad345-134">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="ad345-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="ad345-135">Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="ad345-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="ad345-136">Różnice między przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="ad345-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="ad345-137">Instrukcje: zmiana wartości argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="ad345-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="ad345-138">Instrukcje: ochrona argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="ad345-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="ad345-139">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="ad345-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="ad345-140">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="ad345-140">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
