---
title: Stała i typy literałów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 1d030f8058cd497212c20bca8f064f2bedc99fce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507820"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="03eac-102">Stała i typy literałów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03eac-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="03eac-103">Literał jest wartość, która jest wyrażona w swoim imieniu, a nie jako wartość zmiennej lub wyniku wyrażenia, takie jak numer 3 lub ciąg "Hello".</span><span class="sxs-lookup"><span data-stu-id="03eac-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="03eac-104">Stałe są znaczącą nazwę, która zajmuje miejsce literału i zachowuje ta sama wartość w całym programie, w przeciwieństwie do zmiennej, którego wartość może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="03eac-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="03eac-105">Gdy [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off` i [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, należy jawnie zadeklarować wszystkich stałych o typie danych.</span><span class="sxs-lookup"><span data-stu-id="03eac-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="03eac-106">W poniższym przykładzie typ danych `MyByte` jest jawnie zadeklarowana jako typ danych `Byte`:</span><span class="sxs-lookup"><span data-stu-id="03eac-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 <span data-ttu-id="03eac-107">Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, stałej można zadeklarować bez określania typu danych za pomocą `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="03eac-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="03eac-108">Kompilator Określa typ stałej z typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="03eac-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="03eac-109">Liczbowe literał liczby całkowitej jest rzutowany domyślnie `Integer` typu danych.</span><span class="sxs-lookup"><span data-stu-id="03eac-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="03eac-110">Domyślny typ danych liczb zmiennoprzecinkowych jest `Double`i słowa kluczowe `True` i `False` określ `Boolean` stałej.</span><span class="sxs-lookup"><span data-stu-id="03eac-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="03eac-111">Literały i wymuszenia typu</span><span class="sxs-lookup"><span data-stu-id="03eac-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="03eac-112">W niektórych przypadkach możesz chcieć wymusić literału do określonego typu danych; na przykład podczas przypisywania szczególnie dużą wartość całkowitą literału do zmiennej typu `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="03eac-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="03eac-113">Poniższy przykład generuje błąd:</span><span class="sxs-lookup"><span data-stu-id="03eac-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="03eac-114">Ten błąd wynika z reprezentacji literału.</span><span class="sxs-lookup"><span data-stu-id="03eac-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="03eac-115">`Decimal` Typu danych można zawierającą wartość parametru tak dużej, ale literał niejawnie jest reprezentowany jako `Long`, które nie mogą.</span><span class="sxs-lookup"><span data-stu-id="03eac-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="03eac-116">Można wymusić literału do określonego typu danych na dwa sposoby: przez dodanie znaku typu do niego lub przez umieszczenie ich w ramach otaczającej znaków.</span><span class="sxs-lookup"><span data-stu-id="03eac-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="03eac-117">Znak typu lub Załączanie znaków musi bezpośrednio poprzedzać i/lub wykonaj literału, bez pośredniczące miejsca lub znaków jakiegokolwiek rodzaju.</span><span class="sxs-lookup"><span data-stu-id="03eac-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="03eac-118">Aby w poprzednim przykładzie działają, można dołączyć `D` wpisz znak literału, który powoduje, że może być reprezentowana jako `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="03eac-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 <span data-ttu-id="03eac-119">Poniższy przykład pokazuje poprawne użycie typu znaki i znaki otaczającej:</span><span class="sxs-lookup"><span data-stu-id="03eac-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 <span data-ttu-id="03eac-120">Pokazano w poniższej tabeli otaczającego znaki i znaki typu, które są dostępne w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03eac-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="03eac-121">Typ danych</span><span class="sxs-lookup"><span data-stu-id="03eac-121">Data type</span></span>|<span data-ttu-id="03eac-122">Otaczający znaków</span><span class="sxs-lookup"><span data-stu-id="03eac-122">Enclosing character</span></span>|<span data-ttu-id="03eac-123">Znak typu dołączonych</span><span class="sxs-lookup"><span data-stu-id="03eac-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="03eac-124">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-124">(none)</span></span>|<span data-ttu-id="03eac-125">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="03eac-126">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-126">(none)</span></span>|<span data-ttu-id="03eac-127">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="03eac-128">"</span><span class="sxs-lookup"><span data-stu-id="03eac-128">"</span></span>|<span data-ttu-id="03eac-129">C</span><span class="sxs-lookup"><span data-stu-id="03eac-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="03eac-130">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="03eac-131">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-131">(none)</span></span>|<span data-ttu-id="03eac-132">D lub @</span><span class="sxs-lookup"><span data-stu-id="03eac-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="03eac-133">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-133">(none)</span></span>|<span data-ttu-id="03eac-134">R lub #</span><span class="sxs-lookup"><span data-stu-id="03eac-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="03eac-135">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-135">(none)</span></span>|<span data-ttu-id="03eac-136">Lub %</span><span class="sxs-lookup"><span data-stu-id="03eac-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="03eac-137">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-137">(none)</span></span>|<span data-ttu-id="03eac-138">L lub &</span><span class="sxs-lookup"><span data-stu-id="03eac-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="03eac-139">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-139">(none)</span></span>|<span data-ttu-id="03eac-140">S</span><span class="sxs-lookup"><span data-stu-id="03eac-140">S</span></span>|  
|`Single`|<span data-ttu-id="03eac-141">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-141">(none)</span></span>|<span data-ttu-id="03eac-142">F lub!</span><span class="sxs-lookup"><span data-stu-id="03eac-142">F or !</span></span>|  
|`String`|<span data-ttu-id="03eac-143">"</span><span class="sxs-lookup"><span data-stu-id="03eac-143">"</span></span>|<span data-ttu-id="03eac-144">(Brak)</span><span class="sxs-lookup"><span data-stu-id="03eac-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03eac-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03eac-145">See Also</span></span>  
 [<span data-ttu-id="03eac-146">Stałe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="03eac-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="03eac-147">Instrukcje: deklarowanie stałej</span><span class="sxs-lookup"><span data-stu-id="03eac-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="03eac-148">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="03eac-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="03eac-149">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="03eac-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="03eac-150">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="03eac-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="03eac-151">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="03eac-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="03eac-152">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="03eac-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="03eac-153">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="03eac-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="03eac-154">Typy danych</span><span class="sxs-lookup"><span data-stu-id="03eac-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="03eac-155">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="03eac-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
