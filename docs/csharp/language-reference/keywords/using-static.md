---
title: Używanie dyrektywy static- C# Reference
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 1a0e26d8b0a14e0c77b724fc492588e08762e47f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099998"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="fe6a8-102">Używanie statycznej dyrektywyC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="fe6a8-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="fe6a8-103">Dyrektywa `using static` wyznacza typ, którego statyczne składowe i zagnieżdżone typy można uzyskać dostęp bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="fe6a8-104">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="fe6a8-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="fe6a8-105">gdzie w *pełni kwalifikowana nazwa* typu jest nazwą typu, którego statyczne składowe i zagnieżdżone typy mogą być wywoływane bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="fe6a8-106">Jeśli nie podasz w pełni kwalifikowanej nazwy typu (pełna nazwa przestrzeni nazw wraz z nazwą typu), C# generuje błąd kompilatora [CS0246](../compiler-messages/cs0246.md): "nie można znaleźć nazwy typu lub przestrzeni nazw" typu/przestrzeni nazw "(czy nie brakuje dyrektywy using lub zestawu odwołanie?) ".</span><span class="sxs-lookup"><span data-stu-id="fe6a8-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="fe6a8-107">Dyrektywa `using static` ma zastosowanie do dowolnego typu, który ma statyczne elementy członkowskie (lub typy zagnieżdżone), nawet jeśli ma również elementy członkowskie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="fe6a8-108">Jednak elementy członkowskie wystąpienia mogą być wywoływane tylko za pomocą wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="fe6a8-109">Dyrektywa `using static` została wprowadzona w C# 6.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe6a8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe6a8-110">Remarks</span></span>

<span data-ttu-id="fe6a8-111">Zwykle podczas wywoływania statycznej składowej należy podać nazwę typu wraz z nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="fe6a8-112">Wielokrotne wprowadzenie tej samej nazwy typu w celu wywołania elementów członkowskich typu może spowodować pełne, zaciemnienie kodu.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="fe6a8-113">Na przykład następująca definicja klasy `Circle` odwołuje się do wielu elementów członkowskich klasy <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="fe6a8-114">Eliminując konieczność jawnego odwoływania się do klasy <xref:System.Math> za każdym razem, gdy następuje odwołanie do elementu członkowskiego, dyrektywa `using static` tworzy wiele bardziej estetycznych kodu:</span><span class="sxs-lookup"><span data-stu-id="fe6a8-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="fe6a8-115">`using static` importuje tylko dostępne statyczne elementy członkowskie i zagnieżdżone typy zadeklarowane w określonym typie.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="fe6a8-116">Dziedziczone elementy członkowskie nie są importowane.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-116">Inherited members are not imported.</span></span>  <span data-ttu-id="fe6a8-117">Można importować z dowolnego typu nazwanego za pomocą dyrektywy static with, w tym modułów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="fe6a8-118">Jeśli F# funkcje najwyższego poziomu są wyświetlane w metadanych jako statyczne elementy członkowskie nazwanego typu, którego nazwa C# jest prawidłowym identyfikatorem, można zaimportować te F# funkcje.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="fe6a8-119">`using static` sprawia, że metody rozszerzające zadeklarowane w określonym typie są dostępne dla wyszukiwania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="fe6a8-120">Jednak nazwy metod rozszerzenia nie są importowane do zakresu dla niekwalifikowanego odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="fe6a8-121">Metody o tej samej nazwie zaimportowanej z różnych typów przez różne dyrektywy `using static` w tej samej jednostce kompilacji lub przestrzeni nazw tworzą grupę metod.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="fe6a8-122">W ramach tych grup metod Rozpoznanie przeciążenia C# jest zgodne z normalnymi regułami.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="fe6a8-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe6a8-123">Example</span></span>

<span data-ttu-id="fe6a8-124">W poniższym przykładzie zastosowano dyrektywę `using static` w celu udostępnienia statycznych elementów członkowskich <xref:System.Console>, <xref:System.Math>i <xref:System.String>, bez konieczności określania ich nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="fe6a8-125">W przykładzie można także zastosować dyrektywę `using static` do typu <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="fe6a8-126">Mogłoby to spowodować wywołanie metody <xref:System.Double.TryParse(System.String,System.Double@)> bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="fe6a8-127">Jednak tworzy to mniej czytelny kod, ponieważ jest on niezbędny do sprawdzenia instrukcji `using static`, aby określić, który typ metody `TryParse` jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="fe6a8-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe6a8-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe6a8-128">See also</span></span>

- [<span data-ttu-id="fe6a8-129">Using — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="fe6a8-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="fe6a8-130">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="fe6a8-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fe6a8-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="fe6a8-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fe6a8-132">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="fe6a8-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="fe6a8-133">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="fe6a8-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
