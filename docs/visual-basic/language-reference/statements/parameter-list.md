---
title: Lista parametrów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 651f08812032aa1c5aacc04fdb3d7f491f12b607
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836288"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="a8001-102">Lista parametrów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8001-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="a8001-103">Określa parametry, których oczekuje procedury, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a8001-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="a8001-104">Wiele parametrów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a8001-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="a8001-105">Poniżej przedstawiono składnię jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="a8001-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8001-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8001-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="a8001-107">Części</span><span class="sxs-lookup"><span data-stu-id="a8001-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="a8001-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a8001-108">Optional.</span></span> <span data-ttu-id="a8001-109">Lista atrybutów, które są stosowane do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="a8001-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="a8001-110">Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").</span><span class="sxs-lookup"><span data-stu-id="a8001-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="a8001-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a8001-111">Optional.</span></span> <span data-ttu-id="a8001-112">Określa, że ten parametr nie jest wymagany, gdy procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a8001-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="a8001-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a8001-113">Optional.</span></span> <span data-ttu-id="a8001-114">Określa, że procedura nie można zastąpić, lub ponowne przypisanie zmiennej elementu bazowego odnośnego argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a8001-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="a8001-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a8001-115">Optional.</span></span> <span data-ttu-id="a8001-116">Określa, czy procedurę można zmodyfikować element podstawowy zmiennej w wywoływanym kodzie taki sam sposób, który sam kod wywołujący może.</span><span class="sxs-lookup"><span data-stu-id="a8001-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="a8001-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a8001-117">Optional.</span></span> <span data-ttu-id="a8001-118">Określa, że ostatnim parametrem na liście parametrów jest opcjonalną tablicę elementów określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="a8001-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="a8001-119">Dzięki temu kod wywołujący przekazać dowolną liczbę argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="a8001-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="a8001-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a8001-120">Required.</span></span> <span data-ttu-id="a8001-121">Nazwa zmiennej lokalnej, reprezentujący parametr.</span><span class="sxs-lookup"><span data-stu-id="a8001-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="a8001-122">Jeśli wymagane `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="a8001-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="a8001-123">Typ danych zmiennej lokalnej, reprezentujący parametr.</span><span class="sxs-lookup"><span data-stu-id="a8001-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="a8001-124">Wymagane dla `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="a8001-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="a8001-125">Dowolne wyrażenie stałe lub stałą, którego wynikiem jest typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="a8001-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="a8001-126">Jeśli typ jest `Object`, lub klasy, interfejsu, tablicy lub struktury, wartość domyślna może składać się `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a8001-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8001-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a8001-127">Remarks</span></span>  
 <span data-ttu-id="a8001-128">Parametry są ujęte w nawiasy i rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a8001-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="a8001-129">Parametr może być zadeklarowana z dowolnego typu danych.</span><span class="sxs-lookup"><span data-stu-id="a8001-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="a8001-130">Jeśli nie określisz `parametertype`, jego wartość domyślna to `Object`.</span><span class="sxs-lookup"><span data-stu-id="a8001-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="a8001-131">Gdy kod wywołujący wywołuje procedurę, przekazuje on *argument* do wszystkich wymaganych parametrów.</span><span class="sxs-lookup"><span data-stu-id="a8001-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="a8001-132">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy parametrami i argumentami](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="a8001-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="a8001-133">Argument, którego kod wywołujący przekazuje do każdego z parametrów jest wskaźnik do podstawowego elementu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a8001-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="a8001-134">Jeśli ten element jest *nonvariable* (stałą, literał, wyliczenie lub wyrażenia), nie jest możliwe dla jakiegokolwiek kodu ją zmienić.</span><span class="sxs-lookup"><span data-stu-id="a8001-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="a8001-135">Jeśli jest *zmiennej* — element (zadeklarowanej zmiennej, pola, właściwości, elementu tablicy lub element struktury), kod wywołujący można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="a8001-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="a8001-136">Aby uzyskać więcej informacji, zobacz [różnice między modyfikowalnymi i niemodyfikowalnymi argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="a8001-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="a8001-137">Jeśli element zmienna jest przekazywana `ByRef`, procedury można go także zmienić.</span><span class="sxs-lookup"><span data-stu-id="a8001-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="a8001-138">Aby uzyskać więcej informacji, zobacz [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="a8001-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a8001-139">reguły</span><span class="sxs-lookup"><span data-stu-id="a8001-139">Rules</span></span>  
  
-   <span data-ttu-id="a8001-140">**Nawiasy.**</span><span class="sxs-lookup"><span data-stu-id="a8001-140">**Parentheses.**</span></span> <span data-ttu-id="a8001-141">Jeśli określisz listę parametrów, należy ująć go w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="a8001-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="a8001-142">Jeśli nie ma żadnych parametrów, ale nadal używać nawiasów obejmujących pustej listy.</span><span class="sxs-lookup"><span data-stu-id="a8001-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="a8001-143">Zwiększa to czytelność kodu przez wyjaśnienie, że element jest procedurą.</span><span class="sxs-lookup"><span data-stu-id="a8001-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="a8001-144">**Parametry opcjonalne.**</span><span class="sxs-lookup"><span data-stu-id="a8001-144">**Optional Parameters.**</span></span> <span data-ttu-id="a8001-145">Jeśli używasz `Optional` modyfikator parametru, wszystkie kolejne parametry na liście musi być również opcjonalne i można zadeklarować za pomocą `Optional` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="a8001-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="a8001-146">Należy podać co deklaracja parametru opcjonalnego `defaultvalue` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a8001-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="a8001-147">Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a8001-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="a8001-148">**Tablice parametrów.**</span><span class="sxs-lookup"><span data-stu-id="a8001-148">**Parameter Arrays.**</span></span> <span data-ttu-id="a8001-149">Należy określić `ByVal` dla `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="a8001-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="a8001-150">Nie można używać obu `Optional` i `ParamArray` liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="a8001-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="a8001-151">Aby uzyskać więcej informacji, zobacz [Parameter — tablice](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="a8001-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="a8001-152">**Mechanizm przekazywania.**</span><span class="sxs-lookup"><span data-stu-id="a8001-152">**Passing Mechanism.**</span></span> <span data-ttu-id="a8001-153">Domyślny mechanizm dla każdego argumentu jest `ByVal`, co oznacza procedury nie można zmienić podstawowego elementu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a8001-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="a8001-154">Jednak jeśli element jest typem referencyjnym, procedury można zmodyfikować zawartość lub elementy członkowskie obiektu bazowego, mimo że nie można zastąpić, lub ponownie przypisać samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8001-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="a8001-155">**Nazwy parametrów.**</span><span class="sxs-lookup"><span data-stu-id="a8001-155">**Parameter Names.**</span></span> <span data-ttu-id="a8001-156">Jeśli typ danych parametru jest tablicą, postępuj zgodnie z `parametername` bezpośrednio przez nawiasy.</span><span class="sxs-lookup"><span data-stu-id="a8001-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="a8001-157">Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="a8001-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8001-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8001-158">Example</span></span>  
 <span data-ttu-id="a8001-159">W poniższym przykładzie przedstawiono `Function` procedury, która definiuje dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="a8001-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a8001-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8001-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="a8001-161">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a8001-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="a8001-162">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a8001-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a8001-163">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a8001-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="a8001-164">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a8001-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a8001-165">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a8001-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="a8001-166">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="a8001-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="a8001-167">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="a8001-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
