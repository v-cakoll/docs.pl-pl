---
title: Nazwy identyfikatorów
description: Poznaj reguły dotyczące prawidłowych nazw identyfikatorów w języku programowania Języka C#.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673371"
---
# <a name="identifier-names"></a><span data-ttu-id="ee30d-103">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="ee30d-103">Identifier names</span></span>

<span data-ttu-id="ee30d-104">Identyfikator **identifier** to nazwa przypisana do typu (klasa, interfejs, struktura, delegat lub wyliczenie), element członkowski, zmienna lub obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="ee30d-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="ee30d-105">Prawidłowe identyfikatory muszą być zgodne z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="ee30d-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="ee30d-106">Identyfikatory muszą zaczynać się `_`od litery lub .</span><span class="sxs-lookup"><span data-stu-id="ee30d-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="ee30d-107">Identyfikatory mogą zawierać znaki literunicode, znaki cyfr dziesiętnych, znaki łączące Unicode, znaki unicode łączące znaki lub znaki formatowania Unicode.</span><span class="sxs-lookup"><span data-stu-id="ee30d-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="ee30d-108">Aby uzyskać więcej informacji na temat kategorii Unicode, zobacz [bazę danych kategorii Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="ee30d-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="ee30d-109">Można zadeklarować identyfikatory, które pasują do `@` słów kluczowych Języka C#, używając prefiksu na identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="ee30d-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="ee30d-110">Nie `@` jest częścią nazwy identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="ee30d-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="ee30d-111">Na przykład `@if` deklaruje identyfikator o `if`nazwie .</span><span class="sxs-lookup"><span data-stu-id="ee30d-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="ee30d-112">Te [dosłowne identyfikatory](../../language-reference/tokens/verbatim.md) są przede wszystkim dla interoperacyjności z identyfikatorami zadeklarowanymi w innych językach.</span><span class="sxs-lookup"><span data-stu-id="ee30d-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="ee30d-113">Aby uzyskać pełną definicję prawidłowych identyfikatorów, zobacz [temat Identyfikatory w specyfikacji języka języka Języka C#.](../../../../_csharplang/spec/lexical-structure.md#identifiers)</span><span class="sxs-lookup"><span data-stu-id="ee30d-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="ee30d-114">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="ee30d-114">Naming conventions</span></span>

<span data-ttu-id="ee30d-115">Oprócz reguł istnieje wiele [konwencji nazewnictwa identyfikatorużywanych](../../../standard/design-guidelines/naming-guidelines.md) w interfejsach API .NET.</span><span class="sxs-lookup"><span data-stu-id="ee30d-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="ee30d-116">Zgodnie z konwencją programy `PascalCase` Języka C# są używane dla nazw typów, przestrzeni nazw i wszystkich publicznych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ee30d-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="ee30d-117">Ponadto wspólne są następujące konwencje:</span><span class="sxs-lookup"><span data-stu-id="ee30d-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="ee30d-118">Nazwy interfejsów zaczynają `I`się od kapitału .</span><span class="sxs-lookup"><span data-stu-id="ee30d-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="ee30d-119">Typy atrybutów kończą `Attribute`się słowem .</span><span class="sxs-lookup"><span data-stu-id="ee30d-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="ee30d-120">Typy wyliczenia używają rzeczownika liczby pojedynczej dla innych niż flagi i rzeczownika liczby mnogiej dla flag.</span><span class="sxs-lookup"><span data-stu-id="ee30d-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="ee30d-121">Identyfikatory nie powinny `_` zawierać dwóch kolejnych znaków.</span><span class="sxs-lookup"><span data-stu-id="ee30d-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="ee30d-122">Nazwy te są zarezerwowane dla identyfikatorów generowanych przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="ee30d-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ee30d-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ee30d-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ee30d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee30d-124">See also</span></span>

- [<span data-ttu-id="ee30d-125">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ee30d-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ee30d-126">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="ee30d-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="ee30d-127">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="ee30d-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="ee30d-128">Klasy</span><span class="sxs-lookup"><span data-stu-id="ee30d-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="ee30d-129">Typy konstrukcji</span><span class="sxs-lookup"><span data-stu-id="ee30d-129">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="ee30d-130">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="ee30d-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="ee30d-131">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ee30d-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="ee30d-132">Delegaty</span><span class="sxs-lookup"><span data-stu-id="ee30d-132">Delegates</span></span>](../delegates/index.md)
