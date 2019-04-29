---
title: Using static, dyrektywa - C# odwołania
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29610a77eadf587162731b5bddbcc4bbe7fa0714
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660336"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="8eb88-102">Using static, dyrektywa (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="8eb88-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="8eb88-103">`using static` Dyrektywy wyznacza typ, którego statycznych elementów członkowskich i typy zagnieżdżone, możesz uzyskać dostęp bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8eb88-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="8eb88-104">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="8eb88-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="8eb88-105">gdzie *w pełni kwalifikowana nazwa--typ* jest nazwa typu, którego statycznych elementów członkowskich i typy zagnieżdżone może znajdować się bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8eb88-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="8eb88-106">Jeśli nie podasz w pełni kwalifikowana nazwa typu (pełna nazwa przestrzeni nazw wraz z nazwą typu), C# generuje błąd kompilatora [CS0246](../compiler-messages/cs0246.md): "Nie można odnaleźć nazwy typu lub przestrzeni nazw"/ przestrzeń nazw typu"(Brak przy użyciu dyrektywy lub odwołania do zestawu?)".</span><span class="sxs-lookup"><span data-stu-id="8eb88-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="8eb88-107">`using static` Dyrektywa odnosi się do dowolnego typu, który ma statyczne elementy członkowskie (lub zagnieżdżone typy), nawet wtedy, gdy w nim również elementy członkowskie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8eb88-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="8eb88-108">Jednak składowych wystąpienia może być wywoływany przez wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="8eb88-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="8eb88-109">`using static` Dyrektywa została wprowadzona w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="8eb88-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="8eb88-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8eb88-110">Remarks</span></span>

<span data-ttu-id="8eb88-111">Zwykle po wywołaniu statycznego elementu członkowskiego, podaj nazwę typu, wraz z nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8eb88-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="8eb88-112">Wielokrotnego wprowadzania tej samej nazwie typu, aby wywołać elementy członkowskie tego typu może spowodować pełne zasłoniętej kodu.</span><span class="sxs-lookup"><span data-stu-id="8eb88-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="8eb88-113">Na przykład poniższą definicję `Circle` klasy odwołuje się do liczby elementów członkowskich <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="8eb88-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="8eb88-114">Dzięki wyeliminowaniu konieczności, aby jawnie odwołać <xref:System.Math> klasy zawsze odwołuje się do elementu członkowskiego, `using static` — dyrektywa generuje znacznie bardziej przejrzysty kod:</span><span class="sxs-lookup"><span data-stu-id="8eb88-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="8eb88-115">`using static` Importuje tylko dostępne statyczne elementy członkowskie i zagnieżdżone typy zadeklarowane w określonym typie.</span><span class="sxs-lookup"><span data-stu-id="8eb88-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="8eb88-116">Dziedziczone elementy członkowskie nie są importowane.</span><span class="sxs-lookup"><span data-stu-id="8eb88-116">Inherited members are not imported.</span></span>  <span data-ttu-id="8eb88-117">Można importować z dowolnego typu o nazwie z za pomocą dyrektywy statyczne, w tym moduły języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8eb88-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="8eb88-118">Jeśli F# funkcji najwyższego poziomu są wyświetlane w metadanych jako statyczne elementy członkowskie typu nazwanego, którego nazwa jest prawidłowym C# identyfikator, a następnie F# funkcje mogą być importowane.</span><span class="sxs-lookup"><span data-stu-id="8eb88-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="8eb88-119">`using static` sprawia, że metody rozszerzenia zadeklarowana w określonego typu dostępne do przeszukiwania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8eb88-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="8eb88-120">Nazwy metody rozszerzenia nie są importowane w zakresie niekwalifikowanej odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8eb88-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="8eb88-121">Metody o tej samej nazwie, zaimportowane z różnych typów przez różne `using static` dyrektywy w tej samej jednostce kompilacyjnej lub nazw tworzą grupy metod.</span><span class="sxs-lookup"><span data-stu-id="8eb88-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="8eb88-122">Rozpoznanie przeciążenia w tych grupach metoda regułom normalnego języka C#.</span><span class="sxs-lookup"><span data-stu-id="8eb88-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="8eb88-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="8eb88-123">Example</span></span>

<span data-ttu-id="8eb88-124">W poniższym przykładzie użyto `using static` dyrektywy, aby statyczne elementy członkowskie <xref:System.Console>, <xref:System.Math>, i <xref:System.String> klasy dostępne bez konieczności określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8eb88-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="8eb88-125">W tym przykładzie `using static` dyrektywy może również zostały zastosowane do <xref:System.Double> typu.</span><span class="sxs-lookup"><span data-stu-id="8eb88-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="8eb88-126">To spowoduje umożliwiły wywołać <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8eb88-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="8eb88-127">Jednak powoduje to utworzenie mniej czytelny kod, ponieważ staje się to konieczne sprawdzić `using static` instrukcje, aby ustalić, jakiego typu liczbowego `TryParse` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8eb88-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="8eb88-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eb88-128">See also</span></span>

- [<span data-ttu-id="8eb88-129">Using — Dyrektywa</span><span class="sxs-lookup"><span data-stu-id="8eb88-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="8eb88-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8eb88-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8eb88-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8eb88-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8eb88-132">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8eb88-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="8eb88-133">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8eb88-133">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="8eb88-134">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="8eb88-134">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
