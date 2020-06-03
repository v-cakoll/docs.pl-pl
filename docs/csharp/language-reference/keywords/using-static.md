---
title: Używanie dyrektywy statycznej — odwołanie w C#
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: bffbc026e8f7937db91d42b7a06a5b7bba3bc2f8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396150"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="6a396-102">Using static — dyrektywa (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6a396-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="6a396-103">`using static`Dyrektywa określa typ, którego statyczne składowe i zagnieżdżone typy, do których można uzyskać dostęp bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="6a396-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="6a396-104">Jego składnia to:</span><span class="sxs-lookup"><span data-stu-id="6a396-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="6a396-105">gdzie w *pełni kwalifikowana nazwa* typu jest nazwą typu, którego statyczne składowe i zagnieżdżone typy mogą być wywoływane bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="6a396-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="6a396-106">Jeśli nie podasz w pełni kwalifikowanej nazwy typu (pełna nazwa przestrzeni nazw wraz z nazwą typu), C# generuje błąd kompilatora [CS0246](../compiler-messages/cs0246.md): "nie można znaleźć nazwy typu lub przestrzeni nazw" typu/przestrzeni nazw "(czy nie brakuje dyrektywy using lub odwołania do zestawu?)".</span><span class="sxs-lookup"><span data-stu-id="6a396-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="6a396-107">`using static`Dyrektywa ma zastosowanie do dowolnego typu, który ma statyczne elementy członkowskie (lub typy zagnieżdżone), nawet jeśli ma również elementy członkowskie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6a396-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="6a396-108">Jednak elementy członkowskie wystąpienia mogą być wywoływane tylko za pomocą wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="6a396-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="6a396-109">`using static`Dyrektywa została wprowadzona w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="6a396-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a396-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a396-110">Remarks</span></span>

<span data-ttu-id="6a396-111">Zwykle podczas wywoływania statycznej składowej należy podać nazwę typu wraz z nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="6a396-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="6a396-112">Wielokrotne wprowadzenie tej samej nazwy typu w celu wywołania elementów członkowskich typu może spowodować pełne, zaciemnienie kodu.</span><span class="sxs-lookup"><span data-stu-id="6a396-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="6a396-113">Na przykład następująca definicja `Circle` klasy odwołuje się do wielu elementów członkowskich <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="6a396-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="6a396-114">Eliminując konieczność jawnego odwoływania się do <xref:System.Math> klasy za każdym razem, gdy następuje odwołanie do elementu członkowskiego, `using static` dyrektywa generuje dużo kod czyszczący:</span><span class="sxs-lookup"><span data-stu-id="6a396-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="6a396-115">`using static`Importuje tylko dostępne statyczne elementy członkowskie i zagnieżdżone typy zadeklarowane w określonym typie.</span><span class="sxs-lookup"><span data-stu-id="6a396-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="6a396-116">Dziedziczone elementy członkowskie nie są importowane.</span><span class="sxs-lookup"><span data-stu-id="6a396-116">Inherited members are not imported.</span></span>  <span data-ttu-id="6a396-117">Można importować z dowolnego typu nazwanego za pomocą dyrektywy static with, w tym modułów Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6a396-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="6a396-118">Jeśli funkcje najwyższego poziomu języka F # są wyświetlane w metadanych jako statyczne elementy członkowskie nazwanego typu, którego nazwa jest prawidłowym identyfikatorem języka C#, można zaimportować funkcje języka F #.</span><span class="sxs-lookup"><span data-stu-id="6a396-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="6a396-119">`using static`sprawia, że metody rozszerzające zadeklarowane w określonym typie są dostępne dla wyszukiwania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="6a396-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="6a396-120">Jednak nazwy metod rozszerzenia nie są importowane do zakresu dla niekwalifikowanego odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6a396-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="6a396-121">Metody o tej samej nazwie zaimportowanej z różnych typów przez różne `using static` dyrektywy w tej samej jednostce kompilacji lub przestrzeni nazw tworzą grupę metod.</span><span class="sxs-lookup"><span data-stu-id="6a396-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="6a396-122">W ramach tych grup metod Rozpoznanie przeciążenia odbywa się zgodnie z normalnymi regułami języka C#.</span><span class="sxs-lookup"><span data-stu-id="6a396-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="6a396-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a396-123">Example</span></span>

<span data-ttu-id="6a396-124">W poniższym przykładzie zastosowano `using static` dyrektywę, aby zapewnić statyczny element członkowski <xref:System.Console> <xref:System.Math> klas, i <xref:System.String> dostępnych bez konieczności określania ich nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="6a396-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="6a396-125">W przykładzie `using static` można również zastosować dyrektywę do <xref:System.Double> typu.</span><span class="sxs-lookup"><span data-stu-id="6a396-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="6a396-126">Mogłoby to umożliwić wywołanie <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="6a396-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="6a396-127">Jednak tworzy to mniej czytelny kod, ponieważ jest konieczny do sprawdzenia `using static` dyrektywy w celu ustalenia, która metoda typu liczbowego `TryParse` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6a396-127">However, this creates less readable code, since it becomes necessary to check the `using static` directives to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a396-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a396-128">See also</span></span>

- [<span data-ttu-id="6a396-129">Using — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="6a396-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="6a396-130">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6a396-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6a396-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6a396-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6a396-132">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="6a396-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="6a396-133">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="6a396-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
