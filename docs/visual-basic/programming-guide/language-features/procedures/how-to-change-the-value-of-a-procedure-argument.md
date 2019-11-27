---
title: 'Porady: zmienianie wartości argumentu procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: e562c0f5ec01380c792b4dc064554171cfb007e7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339960"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="83fa9-102">Porady: zmienianie wartości argumentu procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83fa9-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="83fa9-103">Po wywołaniu procedury każdy pożądany argument odpowiada jednemu z parametrów zdefiniowanych w procedurze.</span><span class="sxs-lookup"><span data-stu-id="83fa9-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="83fa9-104">W niektórych przypadkach kod procedury może zmienić wartość odpowiadającą argumentowi w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="83fa9-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="83fa9-105">W innych przypadkach procedura może zmienić tylko jego lokalną kopię argumentu.</span><span class="sxs-lookup"><span data-stu-id="83fa9-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="83fa9-106">Po wywołaniu procedury Visual Basic wykonuje kopię lokalną każdego argumentu, który został przekazaną przez [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="83fa9-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="83fa9-107">Dla każdego argumentu, który przeszedł metodę [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic daje kod procedury bezpośrednio odwołanie do elementu programowania, który jest powiązany z argumentem w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="83fa9-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="83fa9-108">Jeśli element źródłowy w kodzie wywołującym jest elementem modyfikowalnym, a argument jest przenoszona `ByRef`, kod procedury może użyć odwołania bezpośredniego do zmiany wartości elementu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="83fa9-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="83fa9-109">Zmiana podstawowej wartości</span><span class="sxs-lookup"><span data-stu-id="83fa9-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="83fa9-110">Aby zmienić podstawową wartość argumentu procedury w kodzie wywołującym</span><span class="sxs-lookup"><span data-stu-id="83fa9-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="83fa9-111">W deklaracji procedury Określ wartość [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) dla parametru odpowiadającego argumentowi.</span><span class="sxs-lookup"><span data-stu-id="83fa9-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="83fa9-112">W kodzie wywołującym Przekaż modyfikowalny element programistyczny jako argument.</span><span class="sxs-lookup"><span data-stu-id="83fa9-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="83fa9-113">W kodzie wywołującym nie należy ujmować argumentu w nawiasach na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="83fa9-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="83fa9-114">W kodzie procedury Użyj nazwy parametru, aby przypisać wartość do podstawowego elementu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="83fa9-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="83fa9-115">Zapoznaj się z przykładem.</span><span class="sxs-lookup"><span data-stu-id="83fa9-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="83fa9-116">Zmienianie kopii lokalnych</span><span class="sxs-lookup"><span data-stu-id="83fa9-116">Changing Local Copies</span></span>  
 <span data-ttu-id="83fa9-117">Jeśli element źródłowy w kodzie wywołującym jest niemodyfikowalnym elementem lub jeśli argument jest przenoszona `ByVal`, procedura nie może zmienić jego wartości w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="83fa9-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="83fa9-118">Jednakże procedura może zmienić swoją lokalną kopię takiego argumentu.</span><span class="sxs-lookup"><span data-stu-id="83fa9-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="83fa9-119">Aby zmienić kopię argumentu procedury w kodzie procedury</span><span class="sxs-lookup"><span data-stu-id="83fa9-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="83fa9-120">W deklaracji procedury Określ [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dla parametru odpowiadającego argumentowi.</span><span class="sxs-lookup"><span data-stu-id="83fa9-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="83fa9-121">—lub—</span><span class="sxs-lookup"><span data-stu-id="83fa9-121">-or-</span></span>  
  
     <span data-ttu-id="83fa9-122">W kodzie wywołującym Umieść argument w nawiasach na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="83fa9-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="83fa9-123">Wymusza to Visual Basic przekazanie argumentu według wartości, nawet jeśli odpowiedni parametr określa `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="83fa9-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="83fa9-124">W kodzie procedury Użyj nazwy parametru, aby przypisać wartość do lokalnej kopii argumentu.</span><span class="sxs-lookup"><span data-stu-id="83fa9-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="83fa9-125">Wartość bazowa w wywołaniu kodu nie jest zmieniana.</span><span class="sxs-lookup"><span data-stu-id="83fa9-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83fa9-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="83fa9-126">Example</span></span>  
 <span data-ttu-id="83fa9-127">Poniższy przykład przedstawia dwie procedury, które pobierają zmienną tablicową i działają na jej elementach.</span><span class="sxs-lookup"><span data-stu-id="83fa9-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="83fa9-128">Procedura `increase` po prostu dodaje jeden do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="83fa9-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="83fa9-129">Procedura `replace` przypisuje nową tablicę do parametru `a()` a następnie dodaje ją do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="83fa9-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="83fa9-130">Pierwsze wywołanie `MsgBox` wyświetla "po zwiększeniu (n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="83fa9-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="83fa9-131">Ponieważ tablica `n` jest typem referencyjnym, `replace` może zmienić jego składowe, nawet gdy mechanizm przekazywania jest `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="83fa9-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="83fa9-132">Drugie wywołanie `MsgBox` wyświetla "po zastąpieniu (n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="83fa9-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="83fa9-133">Ponieważ `n` jest przenoszona `ByRef`, `replace` może zmodyfikować zmienną `n` w kodzie wywołującym i przypisać do niej nową tablicę.</span><span class="sxs-lookup"><span data-stu-id="83fa9-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="83fa9-134">Ponieważ `n` jest typem referencyjnym, `replace` może również zmienić jego składowe.</span><span class="sxs-lookup"><span data-stu-id="83fa9-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="83fa9-135">Można zapobiec modyfikowaniu przez procedurę samej zmiennej w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="83fa9-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="83fa9-136">Zobacz [jak: Ochrona argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="83fa9-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="83fa9-137">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="83fa9-137">Compiling the Code</span></span>  
 <span data-ttu-id="83fa9-138">Gdy przekazujesz zmienną według odwołania, musisz użyć słowa kluczowego `ByRef`, aby określić ten mechanizm.</span><span class="sxs-lookup"><span data-stu-id="83fa9-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="83fa9-139">Wartością domyślną w Visual Basic jest przekazanie argumentów według wartości.</span><span class="sxs-lookup"><span data-stu-id="83fa9-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="83fa9-140">Jednak dobrym sposobem programowania jest dołączenie albo słowa kluczowego [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) z każdym zadeklarowanym parametrem.</span><span class="sxs-lookup"><span data-stu-id="83fa9-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="83fa9-141">Ułatwia to odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="83fa9-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="83fa9-142">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="83fa9-142">.NET Framework Security</span></span>  
 <span data-ttu-id="83fa9-143">Zawsze istnieje potencjalne ryzyko w umożliwieniu procedury zmiany wartości bazowej argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="83fa9-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="83fa9-144">Upewnij się, że ta wartość jest zmieniana, i przygotuj się do sprawdzenia jej pod kątem poprawności przed jej użyciem.</span><span class="sxs-lookup"><span data-stu-id="83fa9-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83fa9-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83fa9-145">See also</span></span>

- [<span data-ttu-id="83fa9-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="83fa9-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="83fa9-147">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="83fa9-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="83fa9-148">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="83fa9-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="83fa9-149">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="83fa9-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="83fa9-150">Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="83fa9-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="83fa9-151">Różnice między przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="83fa9-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="83fa9-152">Instrukcje: ochrona argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="83fa9-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="83fa9-153">Instrukcje: wymuszanie przekazywania argumentu przez wartość</span><span class="sxs-lookup"><span data-stu-id="83fa9-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="83fa9-154">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="83fa9-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="83fa9-155">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="83fa9-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
