---
title: "Lista parametrów (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c7190b618aa98c91b826ca7c065660d3b19c31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="5c09c-102">Lista parametrów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c09c-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="5c09c-103">Określa parametry, które oczekuje procedury, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="5c09c-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="5c09c-104">Wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5c09c-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="5c09c-105">Poniżej przedstawiono składnię jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="5c09c-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c09c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c09c-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="5c09c-107">Części</span><span class="sxs-lookup"><span data-stu-id="5c09c-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="5c09c-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5c09c-108">Optional.</span></span> <span data-ttu-id="5c09c-109">Lista atrybutów, które są stosowane do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="5c09c-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="5c09c-110">Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").</span><span class="sxs-lookup"><span data-stu-id="5c09c-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="5c09c-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5c09c-111">Optional.</span></span> <span data-ttu-id="5c09c-112">Określa, że ten parametr nie jest wymagany, gdy procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="5c09c-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="5c09c-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5c09c-113">Optional.</span></span> <span data-ttu-id="5c09c-114">Określa, że procedura nie można zastąpić lub ponownie przypisać zmiennej element bazowy odpowiadającego mu argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5c09c-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="5c09c-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5c09c-115">Optional.</span></span> <span data-ttu-id="5c09c-116">Określa, czy procedurę można zmodyfikować odpowiedniego elementu zmiennej w wywoływanym kodzie w taki sam sposób można kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5c09c-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="5c09c-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5c09c-117">Optional.</span></span> <span data-ttu-id="5c09c-118">Określa, że ostatnim parametrem na liście parametrów opcjonalną tablicę elementów określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="5c09c-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="5c09c-119">Dzięki temu kod wywołujący przekazać dowolnej liczby argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="5c09c-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="5c09c-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5c09c-120">Required.</span></span> <span data-ttu-id="5c09c-121">Nazwa zmiennej lokalnej reprezentujące parametr.</span><span class="sxs-lookup"><span data-stu-id="5c09c-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="5c09c-122">Jeśli wymagane `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="5c09c-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="5c09c-123">Typ danych zmiennej lokalnej reprezentujące parametr.</span><span class="sxs-lookup"><span data-stu-id="5c09c-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="5c09c-124">Wymagany dla `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="5c09c-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="5c09c-125">Dowolne wyrażenie stałej lub stała, którego wynikiem jest typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="5c09c-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="5c09c-126">Jeśli typ jest `Object`, lub klasy, interfejsu, tablicy lub struktury, wartością domyślną można tylko `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="5c09c-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c09c-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c09c-127">Remarks</span></span>  
 <span data-ttu-id="5c09c-128">Parametry są ujęte w nawiasy i oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="5c09c-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="5c09c-129">Parametr mogą być deklarowane w przypadku każdego typu danych.</span><span class="sxs-lookup"><span data-stu-id="5c09c-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="5c09c-130">Jeśli nie określisz `parametertype`, domyślne `Object`.</span><span class="sxs-lookup"><span data-stu-id="5c09c-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="5c09c-131">Gdy kod wywołujący wywołuje procedurę, przekazuje *argument* do wszystkich wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5c09c-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="5c09c-132">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="5c09c-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="5c09c-133">Argument kod wywołujący przekazuje do każdego parametru jest wskaźnik do odpowiedniego elementu kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5c09c-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="5c09c-134">Jeśli ten element jest *nonvariable* (stała, literal, wyliczenie lub wyrażenie), nie jest możliwe w dla żadnego kodu go zmienić.</span><span class="sxs-lookup"><span data-stu-id="5c09c-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="5c09c-135">Jeśli jest *zmiennej* elementu (zadeklarowana zmienna, pola, właściwości, element tablicy lub element struktury), można go zmienić kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="5c09c-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="5c09c-136">Aby uzyskać więcej informacji, zobacz [różnice między modyfikowalnymi i niemodyfikowalnymi argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="5c09c-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="5c09c-137">Jeśli element zmienna jest przekazywana `ByRef`, procedury można go także zmienić.</span><span class="sxs-lookup"><span data-stu-id="5c09c-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="5c09c-138">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="5c09c-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5c09c-139">Reguły</span><span class="sxs-lookup"><span data-stu-id="5c09c-139">Rules</span></span>  
  
-   <span data-ttu-id="5c09c-140">**Nawiasy.**</span><span class="sxs-lookup"><span data-stu-id="5c09c-140">**Parentheses.**</span></span> <span data-ttu-id="5c09c-141">Jeśli określisz listę parametrów, należy ująć go w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5c09c-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="5c09c-142">Jeśli nie ma żadnych parametrów, możesz nadal używać nawiasów pustej listy otaczającej.</span><span class="sxs-lookup"><span data-stu-id="5c09c-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="5c09c-143">Zwiększa to czytelność kodu przez wyjaśnienia, że element jest procedurą.</span><span class="sxs-lookup"><span data-stu-id="5c09c-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="5c09c-144">**Parametry opcjonalne.**</span><span class="sxs-lookup"><span data-stu-id="5c09c-144">**Optional Parameters.**</span></span> <span data-ttu-id="5c09c-145">Jeśli używasz `Optional` modyfikator w parametrze, wszystkie kolejne parametry na liście muszą być opcjonalne i można zadeklarować przy użyciu `Optional` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="5c09c-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="5c09c-146">Należy podać co deklaracja opcjonalny parametr `defaultvalue` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5c09c-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="5c09c-147">Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5c09c-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="5c09c-148">**Tablice parametrów.**</span><span class="sxs-lookup"><span data-stu-id="5c09c-148">**Parameter Arrays.**</span></span> <span data-ttu-id="5c09c-149">Należy określić `ByVal` dla `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="5c09c-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="5c09c-150">Nie można używać obu `Optional` i `ParamArray` w tej samej listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="5c09c-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="5c09c-151">Aby uzyskać więcej informacji, zobacz [tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="5c09c-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="5c09c-152">**Mechanizm przekazywania.**</span><span class="sxs-lookup"><span data-stu-id="5c09c-152">**Passing Mechanism.**</span></span> <span data-ttu-id="5c09c-153">Domyślny mechanizm dla każdego argumentu jest `ByVal`, co oznacza procedury nie można zmienić odpowiedniego elementu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5c09c-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="5c09c-154">Jednak jeśli element jest typem referencyjnym, procedury można zmodyfikować zawartość lub elementy członkowskie obiektu podstawowego, nawet jeśli nie można zastąpić, lub ponownie przypisać samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5c09c-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="5c09c-155">**Nazwy parametrów.**</span><span class="sxs-lookup"><span data-stu-id="5c09c-155">**Parameter Names.**</span></span> <span data-ttu-id="5c09c-156">Typ danych parametru jest tablicą, należy wykonać `parametername` natychmiast w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5c09c-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="5c09c-157">Aby uzyskać więcej informacji na nazwy parametrów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5c09c-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c09c-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c09c-158">Example</span></span>  
 <span data-ttu-id="5c09c-159">W poniższym przykładzie przedstawiono `Function` procedury, który definiuje dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="5c09c-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5c09c-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c09c-160">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="5c09c-161">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c09c-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5c09c-162">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c09c-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="5c09c-163">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c09c-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="5c09c-164">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c09c-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="5c09c-165">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c09c-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="5c09c-166">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="5c09c-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="5c09c-167">Porady: przerywanie i łączenie instrukcji w Code</span><span class="sxs-lookup"><span data-stu-id="5c09c-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
