---
title: Stała i typy literałów
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 8ebecddfab0724023c269e92c1fc5534f096bf1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333727"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="2b749-102">Stała i typy literałów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b749-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="2b749-103">Literał jest wartością, która jest wyrażona jako sama wartość zmiennej lub wynik wyrażenia, takie jak liczba 3 lub ciąg "Hello".</span><span class="sxs-lookup"><span data-stu-id="2b749-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="2b749-104">Stała jest zrozumiałą nazwą, która przyjmuje miejsce literału i zachowuje tę samą wartość w całym programie, w przeciwieństwie do zmiennej, której wartość może zmienić.</span><span class="sxs-lookup"><span data-stu-id="2b749-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="2b749-105">Gdy [opcja wnioskowanie](../../../../visual-basic/language-reference/statements/option-infer-statement.md) jest `Off`, a [opcja Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) jest `On`, należy zadeklarować wszystkie stałe jawnie z typem danych.</span><span class="sxs-lookup"><span data-stu-id="2b749-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="2b749-106">W poniższym przykładzie typ danych `MyByte` jest zadeklarowany jako typ danych `Byte`:</span><span class="sxs-lookup"><span data-stu-id="2b749-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2b749-107">Gdy `Option Infer` jest `On` lub `Option Strict` jest `Off`, można zadeklarować stałą bez określania typu danych z klauzulą `As`.</span><span class="sxs-lookup"><span data-stu-id="2b749-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="2b749-108">Kompilator określa typ stałej z typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2b749-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="2b749-109">Literał liczbowy liczb całkowitych jest domyślnie rzutowany na typ danych `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2b749-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="2b749-110">Domyślny typ danych dla liczb zmiennoprzecinkowych to `Double`, a słowa kluczowe `True` i `False` określają stałą `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="2b749-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="2b749-111">Literały i przekształcenia typów</span><span class="sxs-lookup"><span data-stu-id="2b749-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="2b749-112">W niektórych przypadkach może zajść potrzeba wymuszenia literału dla określonego typu danych; na przykład podczas przypisywania szczególnie dużej wartości literału całkowitego do zmiennej typu `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="2b749-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="2b749-113">Poniższy przykład generuje błąd:</span><span class="sxs-lookup"><span data-stu-id="2b749-113">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="2b749-114">Błąd wynika z reprezentacji literału.</span><span class="sxs-lookup"><span data-stu-id="2b749-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="2b749-115">Typ danych `Decimal` może przechowywać wartość, która jest duża, ale literał jest niejawnie reprezentowany jako `Long`, co nie może.</span><span class="sxs-lookup"><span data-stu-id="2b749-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="2b749-116">Można przekształcić literał na określony typ danych na dwa sposoby: przez dołączenie do niego znaku typu lub umieszczenie go w obrębie otaczających znaków.</span><span class="sxs-lookup"><span data-stu-id="2b749-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="2b749-117">Znak typu lub otaczające znaki muszą bezpośrednio poprzedzać i/lub stosować literał, bez spacji lub znaków w żadnym rodzaju.</span><span class="sxs-lookup"><span data-stu-id="2b749-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="2b749-118">Aby wykonać poprzedni przykład pracy, można dołączyć do literału znak typu `D`, który powoduje, że jest on reprezentowany jako `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="2b749-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2b749-119">Poniższy przykład ilustruje poprawne użycie znaków typu i otaczające znaki:</span><span class="sxs-lookup"><span data-stu-id="2b749-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="2b749-120">W poniższej tabeli przedstawiono znaki otaczające i znaki typu dostępne w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2b749-120">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="2b749-121">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2b749-121">Data type</span></span>|<span data-ttu-id="2b749-122">Znak otaczający</span><span class="sxs-lookup"><span data-stu-id="2b749-122">Enclosing character</span></span>|<span data-ttu-id="2b749-123">Znak typu dołączanego</span><span class="sxs-lookup"><span data-stu-id="2b749-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="2b749-124">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-124">(none)</span></span>|<span data-ttu-id="2b749-125">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="2b749-126">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-126">(none)</span></span>|<span data-ttu-id="2b749-127">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="2b749-128">"</span><span class="sxs-lookup"><span data-stu-id="2b749-128">"</span></span>|<span data-ttu-id="2b749-129">C</span><span class="sxs-lookup"><span data-stu-id="2b749-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="2b749-130">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="2b749-131">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-131">(none)</span></span>|<span data-ttu-id="2b749-132">D lub @</span><span class="sxs-lookup"><span data-stu-id="2b749-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="2b749-133">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-133">(none)</span></span>|<span data-ttu-id="2b749-134">R lub #</span><span class="sxs-lookup"><span data-stu-id="2b749-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="2b749-135">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-135">(none)</span></span>|<span data-ttu-id="2b749-136">I lub%</span><span class="sxs-lookup"><span data-stu-id="2b749-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="2b749-137">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-137">(none)</span></span>|<span data-ttu-id="2b749-138">L lub &</span><span class="sxs-lookup"><span data-stu-id="2b749-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="2b749-139">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-139">(none)</span></span>|<span data-ttu-id="2b749-140">S</span><span class="sxs-lookup"><span data-stu-id="2b749-140">S</span></span>|  
|`Single`|<span data-ttu-id="2b749-141">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-141">(none)</span></span>|<span data-ttu-id="2b749-142">F lub!</span><span class="sxs-lookup"><span data-stu-id="2b749-142">F or !</span></span>|  
|`String`|<span data-ttu-id="2b749-143">"</span><span class="sxs-lookup"><span data-stu-id="2b749-143">"</span></span>|<span data-ttu-id="2b749-144">dawaj</span><span class="sxs-lookup"><span data-stu-id="2b749-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b749-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b749-145">See also</span></span>

- [<span data-ttu-id="2b749-146">Stałe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="2b749-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [<span data-ttu-id="2b749-147">Instrukcje: deklarowanie stałej</span><span class="sxs-lookup"><span data-stu-id="2b749-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [<span data-ttu-id="2b749-148">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="2b749-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="2b749-149">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2b749-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="2b749-150">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2b749-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="2b749-151">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="2b749-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="2b749-152">Instrukcje: deklarowanie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2b749-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="2b749-153">Wyliczenia i kwalifikacja nazw</span><span class="sxs-lookup"><span data-stu-id="2b749-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="2b749-154">Typy danych</span><span class="sxs-lookup"><span data-stu-id="2b749-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="2b749-155">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2b749-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
