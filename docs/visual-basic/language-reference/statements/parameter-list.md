---
title: Lista parametrów
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
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404320"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="fc68a-102">Lista parametrów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc68a-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="fc68a-103">Określa parametry, których oczekuje procedura, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="fc68a-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="fc68a-104">Wiele parametrów jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fc68a-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="fc68a-105">Poniżej znajduje się składnia jednego parametru.</span><span class="sxs-lookup"><span data-stu-id="fc68a-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc68a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc68a-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="fc68a-107">Części</span><span class="sxs-lookup"><span data-stu-id="fc68a-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="fc68a-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc68a-108">Optional.</span></span> <span data-ttu-id="fc68a-109">Lista atrybutów, które są stosowane do tego parametru.</span><span class="sxs-lookup"><span data-stu-id="fc68a-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="fc68a-110">Należy ująć [listę atrybutów](attribute-list.md) w nawiasy kątowe (" `<` " i " `>` ").</span><span class="sxs-lookup"><span data-stu-id="fc68a-110">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="fc68a-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc68a-111">Optional.</span></span> <span data-ttu-id="fc68a-112">Określa, że ten parametr nie jest wymagany, gdy procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="fc68a-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="fc68a-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc68a-113">Optional.</span></span> <span data-ttu-id="fc68a-114">Określa, że procedura nie może zastąpić ani ponownie przypisać elementu zmiennej odpowiadającego mu argumentu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="fc68a-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="fc68a-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc68a-115">Optional.</span></span> <span data-ttu-id="fc68a-116">Określa, że procedura może zmodyfikować bazowy element zmiennej w kodzie wywołującym tak samo jak kod wywołujący może.</span><span class="sxs-lookup"><span data-stu-id="fc68a-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="fc68a-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc68a-117">Optional.</span></span> <span data-ttu-id="fc68a-118">Określa, że ostatnim parametrem na liście parametrów jest opcjonalna Tablica elementów określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="fc68a-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="fc68a-119">Dzięki temu kod wywołujący przekazuje dowolną liczbę argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="fc68a-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="fc68a-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fc68a-120">Required.</span></span> <span data-ttu-id="fc68a-121">Nazwa zmiennej lokalnej reprezentującej parametr.</span><span class="sxs-lookup"><span data-stu-id="fc68a-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="fc68a-122">Wymagane, jeśli `Option Strict` jest `On` .</span><span class="sxs-lookup"><span data-stu-id="fc68a-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="fc68a-123">Typ danych zmiennej lokalnej reprezentującej parametr.</span><span class="sxs-lookup"><span data-stu-id="fc68a-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="fc68a-124">Wymagany dla `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="fc68a-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="fc68a-125">Każde stałe lub stałe wyrażenie, którego wynikiem jest typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="fc68a-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="fc68a-126">Jeśli typem jest `Object` lub Klasa, interfejs, tablica lub struktura, wartość domyślna to `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="fc68a-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc68a-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc68a-127">Remarks</span></span>

<span data-ttu-id="fc68a-128">Parametry są ujęte w nawiasy i oddzielane przecinkami.</span><span class="sxs-lookup"><span data-stu-id="fc68a-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="fc68a-129">Parametr można zadeklarować przy użyciu dowolnego typu danych.</span><span class="sxs-lookup"><span data-stu-id="fc68a-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="fc68a-130">Jeśli nie określisz `parametertype` wartości, wartość domyślna to `Object` .</span><span class="sxs-lookup"><span data-stu-id="fc68a-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="fc68a-131">Gdy wywoływany kod wywołuje procedurę, przekazuje *argument* do każdego wymaganego parametru.</span><span class="sxs-lookup"><span data-stu-id="fc68a-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="fc68a-132">Aby uzyskać więcej informacji, zobacz [różnice między parametrami i argumentami](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="fc68a-132">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="fc68a-133">Argument wywoływany przez kod przekazywany do każdego parametru jest wskaźnikiem do podstawowego elementu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="fc68a-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="fc68a-134">Jeśli ten element jest *niezmienny* (stała, literał, Wyliczenie lub wyrażenie), nie można go zmienić.</span><span class="sxs-lookup"><span data-stu-id="fc68a-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="fc68a-135">Jeśli jest to element *zmiennej* (zadeklarowana zmienna, pole, właściwość, element tablicy lub element struktury), kod wywołujący może go zmienić.</span><span class="sxs-lookup"><span data-stu-id="fc68a-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="fc68a-136">Aby uzyskać więcej informacji, zobacz [różnice między argumentami modyfikowalnymi i niemodyfikowalnymi](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="fc68a-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="fc68a-137">W przypadku przekazania elementu zmiennej `ByRef` procedura może również je zmienić.</span><span class="sxs-lookup"><span data-stu-id="fc68a-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="fc68a-138">Aby uzyskać więcej informacji, zobacz [różnice między przekazywaniem argumentu według wartości i przez odwołanie](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="fc68a-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="fc68a-139">Reguły</span><span class="sxs-lookup"><span data-stu-id="fc68a-139">Rules</span></span>

- <span data-ttu-id="fc68a-140">**Nawiasów.**</span><span class="sxs-lookup"><span data-stu-id="fc68a-140">**Parentheses.**</span></span> <span data-ttu-id="fc68a-141">W przypadku określenia listy parametrów należy ująć ją w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="fc68a-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="fc68a-142">Jeśli nie ma żadnych parametrów, można nadal używać nawiasów otaczających pustą listę.</span><span class="sxs-lookup"><span data-stu-id="fc68a-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="fc68a-143">Poprawia to czytelność kodu przez wyjaśnienie, że element jest procedurą.</span><span class="sxs-lookup"><span data-stu-id="fc68a-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="fc68a-144">**Parametry opcjonalne.**</span><span class="sxs-lookup"><span data-stu-id="fc68a-144">**Optional Parameters.**</span></span> <span data-ttu-id="fc68a-145">Jeśli używasz `Optional` modyfikatora w parametrze, wszystkie kolejne parametry na liście muszą być również opcjonalne i być zadeklarowane za pomocą `Optional` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="fc68a-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="fc68a-146">Każda deklaracja opcjonalnego parametru musi dostarczyć `defaultvalue` klauzulę.</span><span class="sxs-lookup"><span data-stu-id="fc68a-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="fc68a-147">Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne](../../programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="fc68a-147">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="fc68a-148">**Tablice parametrów.**</span><span class="sxs-lookup"><span data-stu-id="fc68a-148">**Parameter Arrays.**</span></span> <span data-ttu-id="fc68a-149">Należy określić `ByVal` dla `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="fc68a-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="fc68a-150">Nie można używać obu `Optional` i `ParamArray` na tej samej liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="fc68a-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="fc68a-151">Aby uzyskać więcej informacji, zobacz [tablice parametrów](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="fc68a-151">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="fc68a-152">**Mechanizm przekazywania.**</span><span class="sxs-lookup"><span data-stu-id="fc68a-152">**Passing Mechanism.**</span></span> <span data-ttu-id="fc68a-153">Domyślny mechanizm dla każdego argumentu to `ByVal` , co oznacza, że procedura nie może zmienić bazowego elementu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fc68a-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="fc68a-154">Jeśli jednak element jest typem referencyjnym, procedura może zmodyfikować zawartość lub elementy członkowskie obiektu bazowego, nawet jeśli nie można zastąpić ani ponownie przypisać samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fc68a-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="fc68a-155">**Nazwy parametrów.**</span><span class="sxs-lookup"><span data-stu-id="fc68a-155">**Parameter Names.**</span></span> <span data-ttu-id="fc68a-156">Jeśli typ danych parametru jest tablicą, obserwuj `parametername` bezpośrednio w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="fc68a-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="fc68a-157">Aby uzyskać więcej informacji na temat nazw parametrów, zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="fc68a-157">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="fc68a-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc68a-158">Example</span></span>

<span data-ttu-id="fc68a-159">Poniższy przykład pokazuje `Function` procedurę, która definiuje dwa parametry.</span><span class="sxs-lookup"><span data-stu-id="fc68a-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="fc68a-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc68a-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="fc68a-161">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fc68a-161">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="fc68a-162">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fc68a-162">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="fc68a-163">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="fc68a-163">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="fc68a-164">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="fc68a-164">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="fc68a-165">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="fc68a-165">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="fc68a-166">Przegląd atrybutów</span><span class="sxs-lookup"><span data-stu-id="fc68a-166">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="fc68a-167">Instrukcje: Przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="fc68a-167">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
