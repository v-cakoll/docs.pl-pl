---
title: 'Instrukcje: Wymuszanie argumentu być przekazywany przez wartość (Visual Basic)'
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
ms.openlocfilehash: 497ae11b858b7d164ba3b5607ff2109254a154de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863626"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="556c1-102">Instrukcje: Wymuszanie argumentu być przekazywany przez wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="556c1-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="556c1-103">Deklaracja procedury określa mechanizm przekazywania.</span><span class="sxs-lookup"><span data-stu-id="556c1-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="556c1-104">Jeśli parametr jest zadeklarowana [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic oczekuje przekazywania odpowiadający argument odwołania.</span><span class="sxs-lookup"><span data-stu-id="556c1-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="556c1-105">Dzięki temu procedurę, aby zmienić wartość elementu programistycznego, bazowy argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="556c1-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="556c1-106">Jeśli chcesz chronić element podstawowy względem takie zmiany, można zastąpić `ByRef` wywołać mechanizm przekazywania w procedurze, umieszczając nazwę argumentu w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="556c1-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="556c1-107">Te nawiasy w niniejszym dokumencie stanowią nawiasów otaczający listę argumentów w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="556c1-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="556c1-108">Nie można przesłonić, kod wywołujący [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanizm.</span><span class="sxs-lookup"><span data-stu-id="556c1-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="556c1-109">Aby wymusić argument jest przekazywany przez wartość</span><span class="sxs-lookup"><span data-stu-id="556c1-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="556c1-110">Jeżeli zadeklarowano odpowiadającego mu parametru `ByVal` w procedurze jest konieczne wykonanie żadnych dodatkowych czynności.</span><span class="sxs-lookup"><span data-stu-id="556c1-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="556c1-111">Visual Basic już oczekuje do przekazywania argumentu przez wartość.</span><span class="sxs-lookup"><span data-stu-id="556c1-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="556c1-112">Jeżeli zadeklarowano odpowiadającego mu parametru `ByRef` w procedurze, należy ująć argument w nawiasach w wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="556c1-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="556c1-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="556c1-113">Example</span></span>  
 <span data-ttu-id="556c1-114">Poniższy przykład zastępuje `ByRef` deklaracji parametru.</span><span class="sxs-lookup"><span data-stu-id="556c1-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="556c1-115">W wywołaniu, która wymusza `ByVal`, należy pamiętać, dwa poziomy nawiasów.</span><span class="sxs-lookup"><span data-stu-id="556c1-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="556c1-116">Gdy `str` jest ujęty w nawiasy dodatkowe w liście argumentów `setNewString` procedury nie można zmienić jego wartość w wywoływanym kodzie i `MsgBox` Wyświetla, "nie można zastąpić, jeśli przekazany ByVal".</span><span class="sxs-lookup"><span data-stu-id="556c1-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="556c1-117">Gdy `str` nie jest ujęty w nawiasy dodatkowe procedury można go zmienić, i `MsgBox` Wyświetla "Jest nową wartość dla argumentu inString".</span><span class="sxs-lookup"><span data-stu-id="556c1-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="556c1-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="556c1-118">Compiling the Code</span></span>  
 <span data-ttu-id="556c1-119">Jeśli zmienna jest przekazywane przez odwołanie, musisz użyć `ByRef` — słowo kluczowe, aby określić, ten mechanizm.</span><span class="sxs-lookup"><span data-stu-id="556c1-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="556c1-120">Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości.</span><span class="sxs-lookup"><span data-stu-id="556c1-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="556c1-121">Jednak dobrą praktyką, aby uwzględnić albo programowania jest [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr.</span><span class="sxs-lookup"><span data-stu-id="556c1-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="556c1-122">Dzięki temu można łatwiej odczytać kodu.</span><span class="sxs-lookup"><span data-stu-id="556c1-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="556c1-123">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="556c1-123">Robust Programming</span></span>  
 <span data-ttu-id="556c1-124">Jeśli procedura deklaruje parametr [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), poprawna wykonania kodu może zależeć od możliwości zmienić element podstawowy w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="556c1-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="556c1-125">Jeśli kod wywołujący zastępuje ten mechanizm wywołania, umieszczając argument w nawiasach lub przekazuje argument niemodyfikowalnymi, procedury nie można zmienić elementu bazowego.</span><span class="sxs-lookup"><span data-stu-id="556c1-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="556c1-126">Może to dawać nieoczekiwane wyniki w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="556c1-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="556c1-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="556c1-127">.NET Framework Security</span></span>  
 <span data-ttu-id="556c1-128">Z zezwoleniem na procedury zmienić wartość argumentu w wywoływanym kodzie bazowego zawsze to potencjalne zagrożenie.</span><span class="sxs-lookup"><span data-stu-id="556c1-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="556c1-129">Upewnij się, że oczekiwane tę wartość można zmienić i przygotowywane do sprawdzania poprawności, przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="556c1-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556c1-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="556c1-130">See also</span></span>

- [<span data-ttu-id="556c1-131">Procedury</span><span class="sxs-lookup"><span data-stu-id="556c1-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="556c1-132">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="556c1-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="556c1-133">Instrukcje: Przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="556c1-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="556c1-134">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="556c1-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="556c1-135">Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="556c1-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="556c1-136">Różnice między przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="556c1-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="556c1-137">Instrukcje: Zmień wartość argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="556c1-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="556c1-138">Instrukcje: Chronienie argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="556c1-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="556c1-139">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="556c1-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="556c1-140">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="556c1-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
