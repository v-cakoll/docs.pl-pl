---
title: Nazwy identyfikatorów
description: Dowiedz się, zasady dotyczące nazw prawidłowym identyfikatorem języka programowania C#.
ms.date: 08/21/2018
ms.openlocfilehash: 2147b3846d4ba6d5471b81448489c6d716e3cd61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680496"
---
# <a name="identifier-names"></a><span data-ttu-id="15926-103">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="15926-103">Identifier names</span></span>

<span data-ttu-id="15926-104">**Identyfikator** nazywa się przypisać do elementu członkowskiego (klasy, interfejsu, struktury, delegata lub typu wyliczeniowego), typ, zmienna lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="15926-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="15926-105">Ważne identyfikatory muszą wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="15926-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="15926-106">Identyfikatory musi rozpoczynać się od litery, lub `_`.</span><span class="sxs-lookup"><span data-stu-id="15926-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="15926-107">Identyfikatory mogą zawierać znaki Unicode, znaki cyfr dziesiętnych, łączenie znaków Unicode, łączenie znaków Unicode lub formatowanie znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="15926-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="15926-108">Aby uzyskać więcej informacji na temat kategorii Unicode, zobacz [baza danych kategorii Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="15926-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="15926-109">Można zadeklarować identyfikatory, które odpowiadają słowa kluczowe języka C# za pomocą `@` prefiks identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="15926-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="15926-110">`@` Nie jest częścią nazwy identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="15926-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="15926-111">Na przykład `@if` deklaruje identyfikatora o nazwie `if`.</span><span class="sxs-lookup"><span data-stu-id="15926-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="15926-112">Te [verbatim identyfikatory](../../language-reference/tokens/verbatim.md) są głównie do współdziałania z identyfikatorów zdeklarowanych w innych językach.</span><span class="sxs-lookup"><span data-stu-id="15926-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="15926-113">Aby uzyskać pełną definicję prawidłowych identyfikatorów, zobacz [temat identyfikatory w specyfikacji języka C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="15926-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="15926-114">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="15926-114">Naming conventions</span></span>

<span data-ttu-id="15926-115">Oprócz reguł, istnieje kilka identyfikatora [konwencje nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) używane w całym interfejsów API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="15926-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="15926-116">Zgodnie z Konwencją, C# programy użyj `PascalCase` dla nazwy typu, przestrzeni nazw i wszystkie publiczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="15926-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="15926-117">Ponadto następujące konwencje są wspólne:</span><span class="sxs-lookup"><span data-stu-id="15926-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="15926-118">Interfejs nazw rozpoczyna się od wielkiej litery `I`.</span><span class="sxs-lookup"><span data-stu-id="15926-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="15926-119">Atrybut typy kończących się wyrazem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="15926-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="15926-120">Typach wyliczeniowych na użytek pojedynczej rzeczownik bez flag i liczba mnoga rzeczownik flag.</span><span class="sxs-lookup"><span data-stu-id="15926-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="15926-121">Identyfikatory nie powinny zawierać dwóch kolejnych `_` znaków.</span><span class="sxs-lookup"><span data-stu-id="15926-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="15926-122">Te nazwy są zarezerwowane dla identyfikatorów wygenerowanego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="15926-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="15926-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15926-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="15926-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15926-124">See also</span></span>

- [<span data-ttu-id="15926-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="15926-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="15926-126">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="15926-126">Inside a C# Program</span></span>](../inside-a-program/index.md)
- [<span data-ttu-id="15926-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15926-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="15926-128">Klasy</span><span class="sxs-lookup"><span data-stu-id="15926-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="15926-129">Struktury</span><span class="sxs-lookup"><span data-stu-id="15926-129">Structs</span></span>](../classes-and-structs/structs.md)
- [<span data-ttu-id="15926-130">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="15926-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="15926-131">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="15926-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="15926-132">Delegaty</span><span class="sxs-lookup"><span data-stu-id="15926-132">Delegates</span></span>](../delegates/index.md)
