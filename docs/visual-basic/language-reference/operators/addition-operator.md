---
title: + Operator
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 6ae3feae6ecb63b82426f2aa69359625bbffcec8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372119"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="5883e-102">+ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5883e-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="5883e-103">Dodaje dwie liczby lub zwraca wartość dodatnią wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="5883e-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="5883e-104">Można również użyć do łączenia dwóch wyrażeń ciągu.</span><span class="sxs-lookup"><span data-stu-id="5883e-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5883e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5883e-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="5883e-106">lub</span><span class="sxs-lookup"><span data-stu-id="5883e-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="5883e-107">Części</span><span class="sxs-lookup"><span data-stu-id="5883e-107">Parts</span></span>  
  
|<span data-ttu-id="5883e-108">Termin</span><span class="sxs-lookup"><span data-stu-id="5883e-108">Term</span></span>|<span data-ttu-id="5883e-109">Definicja</span><span class="sxs-lookup"><span data-stu-id="5883e-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="5883e-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5883e-110">Required.</span></span> <span data-ttu-id="5883e-111">Dowolne wyrażenie liczbowe lub ciąg.</span><span class="sxs-lookup"><span data-stu-id="5883e-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="5883e-112">Wymagane, chyba że `+` operator oblicza wartość ujemną.</span><span class="sxs-lookup"><span data-stu-id="5883e-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="5883e-113">Dowolne wyrażenie liczbowe lub ciąg.</span><span class="sxs-lookup"><span data-stu-id="5883e-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="5883e-114">Wynik</span><span class="sxs-lookup"><span data-stu-id="5883e-114">Result</span></span>  
 <span data-ttu-id="5883e-115">Jeśli `expression1` i `expression2` są wartościami liczbowymi, wynik jest ich sumą arytmetyczną.</span><span class="sxs-lookup"><span data-stu-id="5883e-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="5883e-116">Jeśli `expression2` jest nieobecny, `+` operator jest *jednoargumentowym* operatorem tożsamości dla niezmienionej wartości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5883e-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="5883e-117">W tym sensie operacja składa się z zachowania znaku `expression1` , dlatego wynik jest ujemny, jeśli `expression1` jest ujemny.</span><span class="sxs-lookup"><span data-stu-id="5883e-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="5883e-118">Jeśli `expression1` i `expression2` są oba ciągi, wynikiem jest łączenie ich wartości.</span><span class="sxs-lookup"><span data-stu-id="5883e-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="5883e-119">Jeśli `expression1` i `expression2` są typu mieszanego, podejmowana akcja zależy od ich typów, zawartości i ustawienia [Option Strict instrukcji](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5883e-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="5883e-120">Aby uzyskać więcej informacji, Zobacz tabele w "uwagi".</span><span class="sxs-lookup"><span data-stu-id="5883e-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="5883e-121">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="5883e-121">Supported Types</span></span>  
 <span data-ttu-id="5883e-122">Wszystkie typy liczbowe, w tym typy niepodpisane i zmiennoprzecinkowe oraz `Decimal` , i `String` .</span><span class="sxs-lookup"><span data-stu-id="5883e-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5883e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5883e-123">Remarks</span></span>  
 <span data-ttu-id="5883e-124">Ogólnie rzecz biorąc, program `+` wykonuje operacje arytmetyczne, jeśli jest to możliwe, i łączy się tylko wtedy, gdy oba wyrażenia są ciągami.</span><span class="sxs-lookup"><span data-stu-id="5883e-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="5883e-125">Jeśli żadne wyrażenie nie jest `Object` , Visual Basic wykonuje następujące akcje.</span><span class="sxs-lookup"><span data-stu-id="5883e-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="5883e-126">Typy danych wyrażeń</span><span class="sxs-lookup"><span data-stu-id="5883e-126">Data types of expressions</span></span>|<span data-ttu-id="5883e-127">Akcja według kompilatora</span><span class="sxs-lookup"><span data-stu-id="5883e-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="5883e-128">Oba wyrażenia są typami danych liczbowych (,,,,,,,,, `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` `Decimal` `Single` , lub `Double` )</span><span class="sxs-lookup"><span data-stu-id="5883e-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="5883e-129">Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="5883e-129">Add.</span></span> <span data-ttu-id="5883e-130">Typ danych wyniku jest typem liczbowym odpowiednim dla typów danych `expression1` i `expression2` .</span><span class="sxs-lookup"><span data-stu-id="5883e-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="5883e-131">Zobacz tabele "arytmetyczne liczby całkowite" w [typach danych wyników operatora](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="5883e-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="5883e-132">Oba wyrażenia są typu`String`</span><span class="sxs-lookup"><span data-stu-id="5883e-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="5883e-133">Łączenie.</span><span class="sxs-lookup"><span data-stu-id="5883e-133">Concatenate.</span></span>|  
|<span data-ttu-id="5883e-134">Jedno wyrażenie jest typem danych liczbowych, a drugi jest ciągiem</span><span class="sxs-lookup"><span data-stu-id="5883e-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="5883e-135">Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5883e-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5883e-136">Jeśli `Option Strict` jest `Off` , następnie niejawnie przekonwertuj wartość `String` na `Double` i Dodaj.</span><span class="sxs-lookup"><span data-stu-id="5883e-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5883e-137">Jeśli `String` nie można przekonwertować na `Double` , a następnie zgłosić <xref:System.InvalidCastException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5883e-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="5883e-138">Jedno wyrażenie jest typu danych liczbowych, a drugi to [Nothing](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="5883e-138">One expression is a numeric data type, and the other is [Nothing](../nothing.md)</span></span>|<span data-ttu-id="5883e-139">Dodaj, przy `Nothing` wartości równej zero.</span><span class="sxs-lookup"><span data-stu-id="5883e-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="5883e-140">Jedno wyrażenie jest ciągiem, a drugi to`Nothing`</span><span class="sxs-lookup"><span data-stu-id="5883e-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="5883e-141">Połącz, używając `Nothing` wartości "".</span><span class="sxs-lookup"><span data-stu-id="5883e-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="5883e-142">Jeśli jedno wyrażenie jest `Object` wyrażeniem, Visual Basic wykonuje następujące akcje.</span><span class="sxs-lookup"><span data-stu-id="5883e-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="5883e-143">Typy danych wyrażeń</span><span class="sxs-lookup"><span data-stu-id="5883e-143">Data types of expressions</span></span>|<span data-ttu-id="5883e-144">Akcja według kompilatora</span><span class="sxs-lookup"><span data-stu-id="5883e-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="5883e-145">`Object`wyrażenie zawiera wartość liczbową, a druga jest typem danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="5883e-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="5883e-146">Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5883e-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5883e-147">Jeśli `Option Strict` jest `Off` , a następnie Dodaj.</span><span class="sxs-lookup"><span data-stu-id="5883e-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="5883e-148">`Object`wyrażenie zawiera wartość liczbową, a druga jest typu`String`</span><span class="sxs-lookup"><span data-stu-id="5883e-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="5883e-149">Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5883e-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5883e-150">Jeśli `Option Strict` jest `Off` , następnie niejawnie przekonwertuj wartość `String` na `Double` i Dodaj.</span><span class="sxs-lookup"><span data-stu-id="5883e-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5883e-151">Jeśli `String` nie można przekonwertować na `Double` , a następnie zgłosić <xref:System.InvalidCastException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5883e-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="5883e-152">`Object`wyrażenie zawiera ciąg, a drugi to typ danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="5883e-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="5883e-153">Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5883e-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5883e-154">Jeśli `Option Strict` tak `Off` , następnie niejawnie Przekonwertuj ciąg `Object` na `Double` i Dodaj.</span><span class="sxs-lookup"><span data-stu-id="5883e-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5883e-155">Jeśli `Object` nie można przekonwertować ciągu na `Double` , a następnie zgłosić <xref:System.InvalidCastException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5883e-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="5883e-156">`Object`wyrażenie zawiera ciąg, a drugi jest typu`String`</span><span class="sxs-lookup"><span data-stu-id="5883e-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="5883e-157">Jeśli `Option Strict` jest `On` , wygeneruj błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5883e-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5883e-158">Jeśli `Option Strict` jest `Off` , a następnie niejawnie Przekształć `Object` do `String` i Połącz.</span><span class="sxs-lookup"><span data-stu-id="5883e-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="5883e-159">Jeśli oba wyrażenia są `Object` wyrażeniami, Visual Basic wykonuje następujące akcje ( `Option Strict Off` tylko).</span><span class="sxs-lookup"><span data-stu-id="5883e-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="5883e-160">Typy danych wyrażeń</span><span class="sxs-lookup"><span data-stu-id="5883e-160">Data types of expressions</span></span>|<span data-ttu-id="5883e-161">Akcja według kompilatora</span><span class="sxs-lookup"><span data-stu-id="5883e-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="5883e-162">Oba `Object` wyrażenia przechowują wartości liczbowe</span><span class="sxs-lookup"><span data-stu-id="5883e-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="5883e-163">Dodawanie.</span><span class="sxs-lookup"><span data-stu-id="5883e-163">Add.</span></span>|  
|<span data-ttu-id="5883e-164">Oba `Object` wyrażenia są typu`String`</span><span class="sxs-lookup"><span data-stu-id="5883e-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="5883e-165">Łączenie.</span><span class="sxs-lookup"><span data-stu-id="5883e-165">Concatenate.</span></span>|  
|<span data-ttu-id="5883e-166">Jedno `Object` wyrażenie zawiera wartość liczbową, a druga przechowuje ciąg</span><span class="sxs-lookup"><span data-stu-id="5883e-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="5883e-167">Niejawnie Przekonwertuj ciąg `Object` na `Double` i Dodaj.</span><span class="sxs-lookup"><span data-stu-id="5883e-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5883e-168">Jeśli `Object` nie można przekonwertować ciągu na wartość liczbową, zgłoś <xref:System.InvalidCastException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5883e-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="5883e-169">Jeśli dowolne `Object` wyrażenie zwróci wartość [Nothing](../nothing.md) lub <xref:System.DBNull> , `+` operator traktuje go jako element `String` o wartości "".</span><span class="sxs-lookup"><span data-stu-id="5883e-169">If either `Object` expression evaluates to [Nothing](../nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5883e-170">Gdy używasz `+` operatora, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="5883e-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="5883e-171">Użyj `&` operatora do łączenia, aby wyeliminować niejednoznaczność i zapewnić kod służący do samodokumentowania.</span><span class="sxs-lookup"><span data-stu-id="5883e-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5883e-172">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="5883e-172">Overloading</span></span>  
 <span data-ttu-id="5883e-173">`+`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5883e-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5883e-174">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5883e-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5883e-175">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5883e-175">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5883e-176">Przykład</span><span class="sxs-lookup"><span data-stu-id="5883e-176">Example</span></span>  
 <span data-ttu-id="5883e-177">Poniższy przykład używa operatora, `+` Aby dodać liczby.</span><span class="sxs-lookup"><span data-stu-id="5883e-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="5883e-178">Jeśli operandy są liczbowe, Visual Basic oblicza wynik arytmetyczny.</span><span class="sxs-lookup"><span data-stu-id="5883e-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="5883e-179">Wynik arytmetyczny reprezentuje sumę dwóch operandów.</span><span class="sxs-lookup"><span data-stu-id="5883e-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="5883e-180">Można również użyć operatora, `+` Aby połączyć ciągi.</span><span class="sxs-lookup"><span data-stu-id="5883e-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="5883e-181">Jeśli operandy są obu ciągów, Visual Basic je łączyć.</span><span class="sxs-lookup"><span data-stu-id="5883e-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="5883e-182">Wynik łączenia reprezentuje pojedynczy ciąg składający się z zawartości dwóch operandów jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="5883e-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="5883e-183">Jeśli operandy są typu mieszanego, wynik zależy od ustawienia [Option Strict instrukcji](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5883e-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../statements/option-strict-statement.md).</span></span> <span data-ttu-id="5883e-184">Poniższy przykład ilustruje wynik `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="5883e-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="5883e-185">Poniższy przykład ilustruje wynik `Option Strict` `Off` .</span><span class="sxs-lookup"><span data-stu-id="5883e-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="5883e-186">Aby wyeliminować niejednoznaczności, należy użyć `&` operatora zamiast `+` łączenia.</span><span class="sxs-lookup"><span data-stu-id="5883e-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5883e-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5883e-187">See also</span></span>

- [<span data-ttu-id="5883e-188">Operator&</span><span class="sxs-lookup"><span data-stu-id="5883e-188">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="5883e-189">Concatenation — Operatory</span><span class="sxs-lookup"><span data-stu-id="5883e-189">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="5883e-190">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="5883e-190">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="5883e-191">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="5883e-191">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="5883e-192">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5883e-192">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5883e-193">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5883e-193">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="5883e-194">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5883e-194">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
