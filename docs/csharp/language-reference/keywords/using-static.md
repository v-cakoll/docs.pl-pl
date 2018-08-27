---
title: Using static, dyrektywa (odwołanie w C#)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e7368a6b6a4453f2dd07c7afdc0bffa7473ed1
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929681"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="8e834-102">Using static, dyrektywa (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8e834-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="8e834-103">`using static` Dyrektywy wyznacza typ, którego statycznych elementów członkowskich i typy zagnieżdżone, możesz uzyskać dostęp bez określenia nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8e834-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="8e834-104">Jego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="8e834-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="8e834-105">gdzie *w pełni kwalifikowana nazwa--typ* jest nazwa typu, którego statycznych elementów członkowskich i typy zagnieżdżone może znajdować się bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8e834-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="8e834-106">Jeśli nie podasz w pełni kwalifikowana nazwa typu (nazwa przestrzeni nazw pełnej wraz z nazwą typu), C# generuje błąd kompilatora [CS0246](../compiler-messages/cs0246.md): "nie można odnaleźć nazwy typu lub przestrzeni nazw"/ przestrzeń nazw typu"(Brak using — dyrektywa lub odwołanie do zestawu?) ".</span><span class="sxs-lookup"><span data-stu-id="8e834-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="8e834-107">`using static` Dyrektywa odnosi się do dowolnego typu, który ma statyczne elementy członkowskie (lub zagnieżdżone typy), nawet wtedy, gdy w nim również elementy członkowskie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8e834-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="8e834-108">Jednak składowych wystąpienia może być wywoływany przez wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="8e834-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="8e834-109">`using static` Dyrektywa została wprowadzona w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="8e834-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e834-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e834-110">Remarks</span></span>
 
<span data-ttu-id="8e834-111">Zwykle po wywołaniu statycznego elementu członkowskiego, podaj nazwę typu, wraz z nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="8e834-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="8e834-112">Wielokrotnego wprowadzania tej samej nazwie typu, aby wywołać elementy członkowskie tego typu może spowodować pełne zasłoniętej kodu.</span><span class="sxs-lookup"><span data-stu-id="8e834-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="8e834-113">Na przykład poniższą definicję `Circle` klasy odwołuje się do liczby elementów członkowskich <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="8e834-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="8e834-114">Dzięki wyeliminowaniu konieczności, aby jawnie odwołać <xref:System.Math> klasy zawsze odwołuje się do elementu członkowskiego, `using static` — dyrektywa generuje znacznie bardziej przejrzysty kod:</span><span class="sxs-lookup"><span data-stu-id="8e834-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="8e834-115">`using static` Importuje tylko dostępne statyczne elementy członkowskie i zagnieżdżone typy zadeklarowane w określonym typie.</span><span class="sxs-lookup"><span data-stu-id="8e834-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="8e834-116">Dziedziczone elementy członkowskie nie są importowane.</span><span class="sxs-lookup"><span data-stu-id="8e834-116">Inherited members are not imported.</span></span>  <span data-ttu-id="8e834-117">Można importować z dowolnego typu o nazwie z za pomocą dyrektywy statyczne, w tym moduły języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8e834-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="8e834-118">Jeśli funkcji najwyższego poziomu F # są wyświetlane w metadanych jako statyczne elementy członkowskie typu nazwanego, którego nazwa jest prawidłowym identyfikatorem języka C#, F # funkcje mogą zostać zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="8e834-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="8e834-119">`using static` sprawia, że metody rozszerzenia zadeklarowana w określonego typu dostępne do przeszukiwania metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8e834-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="8e834-120">Nazwy metody rozszerzenia nie są importowane w zakresie niekwalifikowanej odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8e834-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="8e834-121">Metody o tej samej nazwie, zaimportowane z różnych typów przez różne `using static` dyrektywy w tej samej jednostce kompilacyjnej lub nazw tworzą grupy metod.</span><span class="sxs-lookup"><span data-stu-id="8e834-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="8e834-122">Rozpoznanie przeciążenia w tych grupach metoda regułom normalnego języka C#.</span><span class="sxs-lookup"><span data-stu-id="8e834-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e834-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e834-123">Example</span></span>

<span data-ttu-id="8e834-124">W poniższym przykładzie użyto `using static` dyrektywy, aby statyczne elementy członkowskie <xref:System.Console>, <xref:System.Math>, i <xref:System.String> klasy dostępne bez konieczności określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8e834-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="8e834-125">W tym przykładzie `using static` dyrektywy może również zostały zastosowane do <xref:System.Double> typu.</span><span class="sxs-lookup"><span data-stu-id="8e834-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="8e834-126">To spowoduje umożliwiły wywołać <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8e834-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="8e834-127">Jednak powoduje to utworzenie mniej czytelny kod, ponieważ staje się to konieczne sprawdzić `using static` instrukcje, aby ustalić, jakiego typu liczbowego `TryParse` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8e834-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e834-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e834-128">See also</span></span>

- [<span data-ttu-id="8e834-129">Using — Dyrektywa</span><span class="sxs-lookup"><span data-stu-id="8e834-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="8e834-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8e834-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="8e834-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8e834-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="8e834-132">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8e834-132">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="8e834-133">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8e834-133">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [<span data-ttu-id="8e834-134">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="8e834-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
