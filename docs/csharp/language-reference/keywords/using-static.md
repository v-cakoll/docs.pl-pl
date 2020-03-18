---
title: przy użyciu dyrektywy statycznej - C# Reference
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712952"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="c4040-102">przy użyciu dyrektywy statycznej (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="c4040-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="c4040-103">Dyrektywa `using static` wyznacza typ, którego statyczne elementy członkowskie i typy zagnieżdżone można uzyskać dostęp bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="c4040-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="c4040-104">Jego składnia jest:</span><span class="sxs-lookup"><span data-stu-id="c4040-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="c4040-105">gdzie *w pełni kwalifikowana nazwa typu* jest nazwą typu, do którego można odwoływać się do statycznych elementów członkowskich i typów zagnieżdżonych bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="c4040-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="c4040-106">Jeśli nie podasz w pełni kwalifikowaną nazwę typu (pełna nazwa obszaru nazw wraz z nazwą typu), C# generuje błąd kompilatora [CS0246:](../compiler-messages/cs0246.md)"Nie można odnaleźć nazwy typu lub obszaru nazw "typ/obszar nazw" (brakuje ci using dyrektywy lub odwołania do zestawu?)".</span><span class="sxs-lookup"><span data-stu-id="c4040-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="c4040-107">Dyrektywa `using static` ma zastosowanie do dowolnego typu, który ma statycznych elementów członkowskich (lub typów zagnieżdżonych), nawet jeśli ma również elementy członkowskie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c4040-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="c4040-108">Jednak elementy członkowskie wystąpienia można wywołać tylko za pośrednictwem wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="c4040-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="c4040-109">Dyrektywa `using static` została wprowadzona w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="c4040-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4040-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4040-110">Remarks</span></span>

<span data-ttu-id="c4040-111">Zwykle podczas wywoływania statycznego elementu członkowskiego podajesz nazwę typu wraz z nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c4040-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="c4040-112">Wielokrotne wprowadzanie tej samej nazwy typu w celu wywołania elementów członkowskich typu może spowodować pełne, niejasne kodu.</span><span class="sxs-lookup"><span data-stu-id="c4040-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="c4040-113">Na przykład następująca definicja `Circle` klasy odwołuje się <xref:System.Math> do liczby członków klasy.</span><span class="sxs-lookup"><span data-stu-id="c4040-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="c4040-114">Poprzez wyeliminowanie konieczności jawnie <xref:System.Math> odwoływać się do klasy za `using static` każdym razem odwołuje się do elementu członkowskiego, dyrektywa tworzy znacznie czystszy kod:</span><span class="sxs-lookup"><span data-stu-id="c4040-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="c4040-115">`using static`importuje dostępne tylko elementy statyczny i typy zagnieżdżone zadeklarowane w określonym typie.</span><span class="sxs-lookup"><span data-stu-id="c4040-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="c4040-116">Dziedziczone elementy członkowskie nie są importowane.</span><span class="sxs-lookup"><span data-stu-id="c4040-116">Inherited members are not imported.</span></span>  <span data-ttu-id="c4040-117">Można zaimportować z dowolnego typu o nazwie za pomocą dyrektywy statycznej, w tym modułów języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c4040-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="c4040-118">Jeśli f# funkcje najwyższego poziomu pojawiają się w metadanych jako statyczne elementy członkowskie nazwanego typu, którego nazwa jest prawidłowy identyfikator C#, a następnie F# funkcje mogą być importowane.</span><span class="sxs-lookup"><span data-stu-id="c4040-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="c4040-119">`using static`sprawia, że metody rozszerzenia zadeklarowane w określonym typie są dostępne do wyszukiwania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c4040-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="c4040-120">Jednak nazwy metod rozszerzenia nie są importowane do zakresu dla niekwalifikowanego odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c4040-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="c4040-121">Metody o tej samej nazwie importowane `using static` z różnych typów przez różne dyrektywy w tej samej jednostce kompilacji lub przestrzeni nazw tworzą grupę metod.</span><span class="sxs-lookup"><span data-stu-id="c4040-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="c4040-122">Rozpoznawanie przeciążenia w ramach tych grup metod jest zgodne z normalnymi regułami Języka C#.</span><span class="sxs-lookup"><span data-stu-id="c4040-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="c4040-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4040-123">Example</span></span>

<span data-ttu-id="c4040-124">W `using static` poniższym przykładzie użyto dyrektywy, <xref:System.Console> <xref:System.Math>aby <xref:System.String> statyczne elementy członkowskie , i klasy dostępne bez konieczności określania ich nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="c4040-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="c4040-125">W tym przykładzie `using static` dyrektywy można również zastosować <xref:System.Double> do typu.</span><span class="sxs-lookup"><span data-stu-id="c4040-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="c4040-126">Umożliwiłoby to wywołanie <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="c4040-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="c4040-127">Jednak to tworzy mniej czytelny kod, ponieważ staje `using static` się konieczne, aby sprawdzić `TryParse` instrukcje, aby określić, która metoda typu liczbowego jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c4040-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4040-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4040-128">See also</span></span>

- [<span data-ttu-id="c4040-129">za pomocą dyrektywy</span><span class="sxs-lookup"><span data-stu-id="c4040-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="c4040-130">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c4040-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c4040-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c4040-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c4040-132">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="c4040-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="c4040-133">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="c4040-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
