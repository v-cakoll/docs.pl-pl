---
title: Nazwy identyfikatorów
description: Poznaj reguły dotyczące prawidłowych nazw identyfikatorów w języku C# programowania.
ms.date: 08/21/2018
ms.openlocfilehash: f8a27ddae0437ed037b59f76d60dc7e420ddc2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589357"
---
# <a name="identifier-names"></a><span data-ttu-id="dcd59-103">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="dcd59-103">Identifier names</span></span>

<span data-ttu-id="dcd59-104">**Identyfikator** to nazwa przypisywana do typu (Klasa, interfejs, struktura, delegat lub enum), element członkowski, zmienna lub przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="dcd59-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="dcd59-105">Prawidłowe identyfikatory muszą być zgodne z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="dcd59-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="dcd59-106">Identyfikatory muszą zaczynać się literą lub `_`.</span><span class="sxs-lookup"><span data-stu-id="dcd59-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="dcd59-107">Identyfikatory mogą zawierać znaki Unicode, cyfry dziesiętne, znaki łączące kod Unicode, znaki łączące kod Unicode lub znaki formatowania Unicode.</span><span class="sxs-lookup"><span data-stu-id="dcd59-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="dcd59-108">Aby uzyskać więcej informacji na temat kategorii Unicode, zobacz [baza danych kategorii Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="dcd59-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="dcd59-109">Identyfikatory, które pasują C# do słów kluczowych, można `@` zadeklarować przy użyciu prefiksu identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="dcd59-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="dcd59-110">Nie `@` jest częścią nazwy identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="dcd59-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="dcd59-111">Na przykład `@if` deklaruje identyfikator o nazwie `if`.</span><span class="sxs-lookup"><span data-stu-id="dcd59-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="dcd59-112">Te [identyfikatory Verbatim](../../language-reference/tokens/verbatim.md) są głównie do współdziałania z identyfikatorami zadeklarowanymi w innych językach.</span><span class="sxs-lookup"><span data-stu-id="dcd59-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="dcd59-113">Aby uzyskać pełną definicję prawidłowych identyfikatorów, zobacz [temat identyfikatory w C# specyfikacji języka](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="dcd59-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="dcd59-114">Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="dcd59-114">Naming conventions</span></span>

<span data-ttu-id="dcd59-115">Oprócz reguł istnieje wiele [konwencji nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) identyfikatorów używanych w ramach interfejsów API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="dcd59-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="dcd59-116">Zgodnie z Konwencją C# programy `PascalCase` programu korzystają z nazw typów, przestrzeni nazw i wszystkich publicznych członków.</span><span class="sxs-lookup"><span data-stu-id="dcd59-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="dcd59-117">Ponadto są wspólne następujące konwencje:</span><span class="sxs-lookup"><span data-stu-id="dcd59-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="dcd59-118">Nazwy interfejsów zaczynają się od `I`wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="dcd59-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="dcd59-119">Typy atrybutów kończą się słowem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="dcd59-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="dcd59-120">Typy wyliczeniowe używają pojedynczej rzeczownika dla flag innych niż flagi i rzeczownika w liczbie mnogiej dla flag.</span><span class="sxs-lookup"><span data-stu-id="dcd59-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="dcd59-121">Identyfikatory nie powinny zawierać dwóch następujących `_` po sobie znaków.</span><span class="sxs-lookup"><span data-stu-id="dcd59-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="dcd59-122">Te nazwy są zarezerwowane dla identyfikatorów wygenerowanych przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="dcd59-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dcd59-123">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dcd59-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dcd59-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcd59-124">See also</span></span>

- [<span data-ttu-id="dcd59-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dcd59-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dcd59-126">Konstrukcja programu C#</span><span class="sxs-lookup"><span data-stu-id="dcd59-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="dcd59-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dcd59-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="dcd59-128">Klasy</span><span class="sxs-lookup"><span data-stu-id="dcd59-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="dcd59-129">Struktury</span><span class="sxs-lookup"><span data-stu-id="dcd59-129">Structs</span></span>](../classes-and-structs/structs.md)
- [<span data-ttu-id="dcd59-130">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="dcd59-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="dcd59-131">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="dcd59-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="dcd59-132">Delegaty</span><span class="sxs-lookup"><span data-stu-id="dcd59-132">Delegates</span></span>](../delegates/index.md)
