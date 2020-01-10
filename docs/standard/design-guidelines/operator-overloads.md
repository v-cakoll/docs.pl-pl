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
ms.openlocfilehash: 4cea3c17de40a873d977223f36b6dcef4f2c2d78
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709143"
---
# <a name="operator-overloads"></a><span data-ttu-id="7ff50-102">Przeciążenia operatorów</span><span class="sxs-lookup"><span data-stu-id="7ff50-102">Operator Overloads</span></span>
<span data-ttu-id="7ff50-103">Przeciążenia operatorów pozwalają na wyświetlanie typów struktur, tak jakby były wbudowane jako elementy pierwotne języka.</span><span class="sxs-lookup"><span data-stu-id="7ff50-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="7ff50-104">Chociaż dozwolone i przydatne w niektórych sytuacjach, przeciążenia operatorów powinny być stosowane ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="7ff50-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="7ff50-105">Istnieje wiele przypadków, w których przeciążanie operatora zostało nadmiarowe, na przykład gdy projektanci struktury zaczynali używać operatorów dla operacji, które powinny być prostymi metodami.</span><span class="sxs-lookup"><span data-stu-id="7ff50-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="7ff50-106">Poniższe wskazówki powinny pomóc określić, kiedy i jak należy używać przeciążania operatora.</span><span class="sxs-lookup"><span data-stu-id="7ff50-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="7ff50-107">**X AVOID** Definiowanie przeciążenia operatora w typów, które powinny uznać, takich jak typy pierwotne (wbudowane).</span><span class="sxs-lookup"><span data-stu-id="7ff50-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="7ff50-108">**✓ CONSIDER** Definiowanie przeciążenia operatora w typie, który powinien uznać, takie jak typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="7ff50-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="7ff50-109">Na przykład <xref:System.String?displayProperty=nameWithType> ma zdefiniowane `operator==` i `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="7ff50-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="7ff50-110">**✓ DO** definiować przeciążeń operatora w strukturach, które reprezentują numery (takie jak <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="7ff50-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="7ff50-111">**X DO NOT** można cute podczas definiowania przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="7ff50-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="7ff50-112">Przeciążanie operatora jest przydatne w przypadkach, w których jest od razu oczywisty, co jest wynikiem operacji.</span><span class="sxs-lookup"><span data-stu-id="7ff50-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="7ff50-113">Na przykład warto mieć możliwość odejmowania jednego <xref:System.DateTime> od innego `DateTime` i uzyskania <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="7ff50-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="7ff50-114">Nie jest jednak konieczne użycie operatora Union Logical do złożenia dwóch zapytań bazy danych lub użycie operatora przesunięcia do zapisu w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="7ff50-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="7ff50-115">**X DO NOT** Podaj operator overloads, chyba że jest co najmniej jeden z argumentów typu Definiowanie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="7ff50-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="7ff50-116">**✓ DO** przeciążać operatory w sposób symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="7ff50-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="7ff50-117">Na przykład w przypadku przeciążenia `operator==`należy również przeciążyć `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="7ff50-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="7ff50-118">Podobnie w przypadku przeciążenia `operator<`należy również przeciążać `operator>`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7ff50-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="7ff50-119">**✓ CONSIDER** zapewniając metod przyjaznych nazw, które odpowiadają do każdego przeciążonego operatora.</span><span class="sxs-lookup"><span data-stu-id="7ff50-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="7ff50-120">Wiele języków nie obsługuje przeciążania operatora.</span><span class="sxs-lookup"><span data-stu-id="7ff50-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="7ff50-121">Z tego powodu zaleca się, aby typy, które zawierają operatory przeciążeń, uwzględniają dodatkową metodę z odpowiednią nazwą domeny, która zapewnia równorzędną funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="7ff50-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="7ff50-122">Poniższa tabela zawiera listę operatorów i odpowiednich przyjaznych nazw metod.</span><span class="sxs-lookup"><span data-stu-id="7ff50-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="7ff50-123">C#Symbol operatora</span><span class="sxs-lookup"><span data-stu-id="7ff50-123">C# Operator Symbol</span></span>|<span data-ttu-id="7ff50-124">Nazwa metadanych</span><span class="sxs-lookup"><span data-stu-id="7ff50-124">Metadata Name</span></span>|<span data-ttu-id="7ff50-125">Przyjazna nazwa</span><span class="sxs-lookup"><span data-stu-id="7ff50-125">Friendly Name</span></span>|  
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
  
### <a name="overloading-operator-"></a><span data-ttu-id="7ff50-126">Przeciążanie operatora = =</span><span class="sxs-lookup"><span data-stu-id="7ff50-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="7ff50-127">Przeciążenie `operator ==` jest dość skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="7ff50-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="7ff50-128">Semantyka operatora musi być zgodna z kilkoma innymi elementami członkowskimi, takimi jak <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7ff50-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="7ff50-129">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="7ff50-129">Conversion Operators</span></span>  
 <span data-ttu-id="7ff50-130">Operatory konwersji to operatory jednoargumentowe, które umożliwiają konwersję z jednego typu na drugi.</span><span class="sxs-lookup"><span data-stu-id="7ff50-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="7ff50-131">Operatory muszą być zdefiniowane jako statyczne elementy członkowskie dla operandu lub typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="7ff50-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="7ff50-132">Istnieją dwa typy operatorów konwersji: niejawne i jawne.</span><span class="sxs-lookup"><span data-stu-id="7ff50-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="7ff50-133">**X DO NOT** Podaj operatora konwersji, jeśli takie konwersja nie jest wyraźnie oczekiwany przez użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="7ff50-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="7ff50-134">**X DO NOT** definiować operatory konwersji poza domeny typu.</span><span class="sxs-lookup"><span data-stu-id="7ff50-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="7ff50-135">Na przykład <xref:System.Int32>, <xref:System.Double>i <xref:System.Decimal> to wszystkie typy liczbowe, natomiast <xref:System.DateTime> nie jest.</span><span class="sxs-lookup"><span data-stu-id="7ff50-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="7ff50-136">W związku z tym nie powinien istnieć operator konwersji do konwersji `Double(long)` na `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="7ff50-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="7ff50-137">Konstruktor jest preferowany w takich przypadkach.</span><span class="sxs-lookup"><span data-stu-id="7ff50-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="7ff50-138">**X DO NOT** Podaj operator niejawnej konwersji, jeśli konwersja jest potencjalnie stratnej.</span><span class="sxs-lookup"><span data-stu-id="7ff50-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="7ff50-139">Na przykład nie powinna być niejawna konwersja z `Double` na `Int32`, ponieważ `Double` ma szerszy zakres niż `Int32`.</span><span class="sxs-lookup"><span data-stu-id="7ff50-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="7ff50-140">Jawny Operator konwersji można podać, nawet jeśli konwersja jest potencjalnie stratna.</span><span class="sxs-lookup"><span data-stu-id="7ff50-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="7ff50-141">**X DO NOT** zgłaszanie wyjątków z niejawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="7ff50-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="7ff50-142">Bardzo trudne jest, aby użytkownicy końcowi wiedzieli, co się dzieje, ponieważ mogą nie wiedzieć, że odbywa się konwersja.</span><span class="sxs-lookup"><span data-stu-id="7ff50-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="7ff50-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> jeśli powoduje wywołanie operatora rzutowania stratnej konwersji i kontrakt operator nie zezwala stratnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="7ff50-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="7ff50-144">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="7ff50-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7ff50-145">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="7ff50-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff50-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ff50-146">See also</span></span>

- [<span data-ttu-id="7ff50-147">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="7ff50-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="7ff50-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="7ff50-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
