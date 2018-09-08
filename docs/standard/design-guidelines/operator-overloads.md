---
title: Przeciążenia operatorów
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ca42d25a5f3456c6a10eff76d7015656322abae
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192473"
---
# <a name="operator-overloads"></a><span data-ttu-id="3f6fa-102">Przeciążenia operatorów</span><span class="sxs-lookup"><span data-stu-id="3f6fa-102">Operator Overloads</span></span>
<span data-ttu-id="3f6fa-103">Przeciążenia operatorów zezwala na typy framework są wyświetlane tak, jakby były one elementów podstawowych języka wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="3f6fa-104">Mimo że dozwolonych i przydatne w niektórych sytuacjach przeciążenia operatorów powinny być używane ostrożnie.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="3f6fa-105">Istnieje wiele przypadków, w której operator przeciążenia ma zostały użyte, takie jak podczas uruchamiania projektantów framework można używać operatorów dla operacji, które powinny być proste metody.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="3f6fa-106">Poniższe wskazówki powinien pomóc zdecydować, kiedy i jak użycie przeładowania operatora.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="3f6fa-107">**X AVOID** Definiowanie przeciążenia operatora w typów, które powinny uznać, takich jak typy pierwotne (wbudowane).</span><span class="sxs-lookup"><span data-stu-id="3f6fa-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="3f6fa-108">**✓ CONSIDER** Definiowanie przeciążenia operatora w typie, który powinien uznać, takie jak typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="3f6fa-109">Na przykład <xref:System.String?displayProperty=nameWithType> ma `operator==` i `operator!=` zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="3f6fa-110">**✓ DO** definiować przeciążeń operatora w strukturach, które reprezentują numery (takie jak <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="3f6fa-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="3f6fa-111">**X DO NOT** można cute podczas definiowania przeciążenia operatora.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="3f6fa-112">Przeciążanie operatora jest przydatne w sytuacjach, w których jest od razu widoczne jaki będzie wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="3f6fa-113">Na przykład, dobrym pomysłem będzie mieć możliwość odjęcie jednego <xref:System.DateTime> z innego `DateTime` i Uzyskaj <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="3f6fa-114">Jednak nie jest odpowiedni do użycia logiczny operator union, union zapytań dwie bazy danych lub użyć operator przesunięcia bitowego do zapisywania do strumienia.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="3f6fa-115">**X DO NOT** Podaj operator overloads, chyba że jest co najmniej jeden z argumentów typu Definiowanie przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="3f6fa-116">**✓ DO** przeciążać operatory w sposób symetrycznego.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="3f6fa-117">Na przykład, jeśli przeładujesz `operator==`, powinien także przeciążać `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="3f6fa-118">Podobnie jeśli przeładujesz `operator<`, powinien także przeciążać `operator>`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="3f6fa-119">**✓ CONSIDER** zapewniając metod przyjaznych nazw, które odpowiadają do każdego przeciążonego operatora.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="3f6fa-120">Wiele języków nie obsługują przeciążanie operatora.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="3f6fa-121">Z tego powodu zaleca się, że typy, które przeciążają operatory obejmują metody pomocniczej z odpowiednią nazwę specyficznego dla domeny, która zapewnia podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="3f6fa-122">Poniższa tabela zawiera listę operatorów i odpowiadających im nazw przyjaznych metody.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="3f6fa-123">Symbol operatora w języku C#</span><span class="sxs-lookup"><span data-stu-id="3f6fa-123">C# Operator Symbol</span></span>|<span data-ttu-id="3f6fa-124">Nazwa metadanych</span><span class="sxs-lookup"><span data-stu-id="3f6fa-124">Metadata Name</span></span>|<span data-ttu-id="3f6fa-125">Przyjazna nazwa</span><span class="sxs-lookup"><span data-stu-id="3f6fa-125">Friendly Name</span></span>|  
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
  
### <a name="overloading-operator-"></a><span data-ttu-id="3f6fa-126">Przeciążanie operatora ==</span><span class="sxs-lookup"><span data-stu-id="3f6fa-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="3f6fa-127">Przeciążanie `operator ==` jest dość skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="3f6fa-128">Semantyki operatora muszą być zgodne z kilku innych członków, takich jak <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="3f6fa-129">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="3f6fa-129">Conversion Operators</span></span>  
 <span data-ttu-id="3f6fa-130">Operatory konwersji są operatory jednoargumentowe, które umożliwiają konwersja z jednego typu na inny.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="3f6fa-131">Operatory muszą być zdefiniowane jako elementy statyczne argument lub zwracany typ.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="3f6fa-132">Istnieją dwa typy operatory konwersji: jawne i niejawne.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="3f6fa-133">**X DO NOT** Podaj operatora konwersji, jeśli takie konwersja nie jest wyraźnie oczekiwany przez użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="3f6fa-134">**X DO NOT** definiować operatory konwersji poza domeny typu.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="3f6fa-135">Na przykład <xref:System.Int32>, <xref:System.Double>, i <xref:System.Decimal> są wszystkie typy liczbowe, podczas gdy <xref:System.DateTime> nie jest.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="3f6fa-136">Dlatego powinny być żaden operator konwersji, aby przekonwertować `Double(long)` do `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="3f6fa-137">W takim przypadku jest preferowane konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="3f6fa-138">**X DO NOT** Podaj operator niejawnej konwersji, jeśli konwersja jest potencjalnie stratnej.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="3f6fa-139">Na przykład, nie powinno być niejawna konwersja z `Double` do `Int32` ponieważ `Double` zapewnia szerszy zakres niż `Int32`.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="3f6fa-140">Operator jawnej konwersji można podać, nawet jeśli konwersja jest potencjalnie stratnej.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="3f6fa-141">**X DO NOT** zgłaszanie wyjątków z niejawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="3f6fa-142">Jest to bardzo trudne dla użytkowników końcowych zorientować się, ponieważ nie są świadomi, że konwersja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="3f6fa-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> jeśli powoduje wywołanie operatora rzutowania stratnej konwersji i kontrakt operator nie zezwala stratnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="3f6fa-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="3f6fa-144">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="3f6fa-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3f6fa-145">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="3f6fa-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6fa-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f6fa-146">See also</span></span>

- [<span data-ttu-id="3f6fa-147">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="3f6fa-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="3f6fa-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="3f6fa-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
