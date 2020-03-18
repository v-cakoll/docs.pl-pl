---
title: Przeciążenia operatorów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 0999e94c8d77396b237522e89c51206ce1226718
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400569"
---
# <a name="operator-overloads"></a><span data-ttu-id="3553e-102">Przeciążenia operatorów</span><span class="sxs-lookup"><span data-stu-id="3553e-102">Operator Overloads</span></span>
<span data-ttu-id="3553e-103">Przeciążenia operatorów umożliwiają typy struktury, które mają być wyświetlane tak, jakby były wbudowane prymitywy języka.</span><span class="sxs-lookup"><span data-stu-id="3553e-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="3553e-104">Mimo że dozwolone i przydatne w niektórych sytuacjach, przeciążenia operatora powinny być używane ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="3553e-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="3553e-105">Istnieje wiele przypadków, w których przeciążenie operatora zostało nadużywane, na przykład gdy projektanci struktury zaczęli używać operatorów do operacji, które powinny być prostymi metodami.</span><span class="sxs-lookup"><span data-stu-id="3553e-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="3553e-106">Poniższe wskazówki powinny pomóc w podjęciu decyzji, kiedy i jak używać przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="3553e-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="3553e-107">❌UNIKAJ definiowania przeciążeń operatora, z wyjątkiem typów, które powinny czuć się jak typy pierwotne (wbudowane).</span><span class="sxs-lookup"><span data-stu-id="3553e-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="3553e-108">✔️ ROZWAŻ definiowanie przeciążeń operatora w typie, który powinien czuć się jak typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="3553e-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="3553e-109">Na przykład <xref:System.String?displayProperty=nameWithType> `operator==` ma `operator!=` i zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="3553e-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="3553e-110">✔️ Zdefiniuj przeciążenia operatora w <xref:System.Decimal?displayProperty=nameWithType>strukturach reprezentujących liczby (takie jak ).</span><span class="sxs-lookup"><span data-stu-id="3553e-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="3553e-111">❌NIE bądź uroczy podczas definiowania przeciążeń operatora.</span><span class="sxs-lookup"><span data-stu-id="3553e-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="3553e-112">Przeciążenie operatora jest przydatne w przypadkach, w których od razu jest oczywiste, jaki będzie wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="3553e-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="3553e-113">Na przykład, to ma sens, aby <xref:System.DateTime> móc `DateTime` odjąć <xref:System.TimeSpan>jeden od drugiego i uzyskać .</span><span class="sxs-lookup"><span data-stu-id="3553e-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="3553e-114">Jednak nie jest właściwe użycie operatora unii logicznej do unii dwóch kwerend bazy danych lub użyć operatora shift do zapisu do strumienia.</span><span class="sxs-lookup"><span data-stu-id="3553e-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="3553e-115">❌NIE należy podawać przeciążenia operatora, chyba że co najmniej jeden z operandów jest typu definiującego przeciążenie.</span><span class="sxs-lookup"><span data-stu-id="3553e-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="3553e-116">✔️ DO operatorów przeciążenia w sposób symetryczny.</span><span class="sxs-lookup"><span data-stu-id="3553e-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="3553e-117">Na przykład, jeśli przeciążenie `operator==`, należy `operator!=`również przeciążyć .</span><span class="sxs-lookup"><span data-stu-id="3553e-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="3553e-118">Podobnie, jeśli przeciążysz `operator<`, należy również `operator>`przeciążyć , i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3553e-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="3553e-119">✔️ ROZWAŻ dostarczenie metod o przyjaznych nazwach, które odpowiadają każdemu przeciążonemu operatorowi.</span><span class="sxs-lookup"><span data-stu-id="3553e-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="3553e-120">Wiele języków nie obsługuje przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="3553e-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="3553e-121">Z tego powodu zaleca się, że typy, które przeciążenia operatory zawierają metodę pomocniczą o odpowiedniej nazwie specyficznej dla domeny, która zapewnia równoważne funkcje.</span><span class="sxs-lookup"><span data-stu-id="3553e-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="3553e-122">Poniższa tabela zawiera listę operatorów i odpowiadające im nazwy metod przyjaznych.</span><span class="sxs-lookup"><span data-stu-id="3553e-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="3553e-123">Symbol operatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="3553e-123">C# Operator Symbol</span></span>|<span data-ttu-id="3553e-124">Nazwa metadanych</span><span class="sxs-lookup"><span data-stu-id="3553e-124">Metadata Name</span></span>|<span data-ttu-id="3553e-125">Przyjazna nazwa</span><span class="sxs-lookup"><span data-stu-id="3553e-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="3553e-126">Operator przeciążenia ==</span><span class="sxs-lookup"><span data-stu-id="3553e-126">Overloading Operator ==</span></span>
 <span data-ttu-id="3553e-127">Przeciążenie `operator ==` jest dość skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="3553e-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="3553e-128">Semantyka operatora musi być zgodna z kilkoma innymi <xref:System.Object.Equals%2A?displayProperty=nameWithType>członkami, takimi jak .</span><span class="sxs-lookup"><span data-stu-id="3553e-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="3553e-129">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="3553e-129">Conversion Operators</span></span>
 <span data-ttu-id="3553e-130">Operatory konwersji są operatorami jednoargumentowymi, które umożliwiają konwersję z jednego typu na inny.</span><span class="sxs-lookup"><span data-stu-id="3553e-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="3553e-131">Operatory muszą być zdefiniowane jako statyczne elementy członkowskie na operand lub typu zwracane.</span><span class="sxs-lookup"><span data-stu-id="3553e-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="3553e-132">Istnieją dwa typy operatorów konwersji: niejawne i jawne.</span><span class="sxs-lookup"><span data-stu-id="3553e-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="3553e-133">❌NIE udostępniaj operatora konwersji, jeśli taka konwersja nie jest wyraźnie oczekiwana przez użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="3553e-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="3553e-134">❌NIE definiuj operatorów konwersji poza domeną typu.</span><span class="sxs-lookup"><span data-stu-id="3553e-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="3553e-135">Na przykład <xref:System.Int32> <xref:System.Double>, <xref:System.Decimal> , i są wszystkie <xref:System.DateTime> typy liczbowe, podczas gdy nie jest.</span><span class="sxs-lookup"><span data-stu-id="3553e-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="3553e-136">W związku z tym nie powinno `Double(long)` być `DateTime`operator konwersji do konwersji na .</span><span class="sxs-lookup"><span data-stu-id="3553e-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="3553e-137">Konstruktor jest preferowany w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="3553e-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="3553e-138">❌NIE udostępniaj niejawnego operatora konwersji, jeśli konwersja jest potencjalnie stratna.</span><span class="sxs-lookup"><span data-stu-id="3553e-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="3553e-139">Na przykład nie powinno być niejawna `Double` konwersja z `Int32` `Double` powodu `Int32` ma szerszy zakres niż .</span><span class="sxs-lookup"><span data-stu-id="3553e-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="3553e-140">Operator konwersji jawnej można podać, nawet jeśli konwersja jest potencjalnie stratna.</span><span class="sxs-lookup"><span data-stu-id="3553e-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="3553e-141">❌NIE zgłaszaj wyjątków od rzutów niejawnych.</span><span class="sxs-lookup"><span data-stu-id="3553e-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="3553e-142">Jest to bardzo trudne dla użytkowników końcowych, aby zrozumieć, co się dzieje, ponieważ mogą nie być świadomi, że konwersja ma miejsce.</span><span class="sxs-lookup"><span data-stu-id="3553e-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="3553e-143">✔️ czy <xref:System.InvalidCastException?displayProperty=nameWithType> rzucać, jeśli wywołanie odlewanego operatora powoduje stratną konwersję, a umowa operatora nie zezwala na straty konwersji.</span><span class="sxs-lookup"><span data-stu-id="3553e-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="3553e-144">*Części © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="3553e-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3553e-145">*Przedruk za zgodą Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms i Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) autorstwa Krzysztofa Cwaliny i Brada Abramsa, opublikowane 22 października 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="3553e-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3553e-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3553e-146">See also</span></span>

- [<span data-ttu-id="3553e-147">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="3553e-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="3553e-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="3553e-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
