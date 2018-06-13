---
title: przy użyciu statycznych — dyrektywa (odwołanie w C#)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b7508c6e751f83fdc16a700ad68aa7de36e497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285138"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="7eb6d-102">przy użyciu statycznych — dyrektywa (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7eb6d-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="7eb6d-103">`using static` Dyrektywy wyznacza typ którego statyczne elementy członkowskie użytkownik ma dostęp bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="7eb6d-104">Składnia to:</span><span class="sxs-lookup"><span data-stu-id="7eb6d-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="7eb6d-105">gdzie *pełni kwalifikowana nazwa--typu* jest nazwa typu, w których statyczne elementy członkowskie można odwoływać się bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="7eb6d-106">Jeśli podasz typu w pełni kwalifikowaną nazwę (pełna przestrzeni nazw wraz z nazwą typu), C# generuje błąd kompilatora CS0246: "nie można odnaleźć nazwy typu lub przestrzeni nazw"< Nazwa typu >"."</span><span class="sxs-lookup"><span data-stu-id="7eb6d-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="7eb6d-107">`using static` Dyrektywę stosuje się do dowolnego typu, który ma elementy członkowskie static, nawet jeśli ma również elementów członkowskich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="7eb6d-108">Jednak elementów członkowskich wystąpienia można wywołać tylko za pomocą wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="7eb6d-109">`using static` Dyrektywy wprowadzono w języku C# 6.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="7eb6d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7eb6d-110">Remarks</span></span>
 
<span data-ttu-id="7eb6d-111">Zwykle po wywołaniu statyczny element członkowski, musisz podać nazwy typu oraz nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="7eb6d-112">Wielokrotnie wprowadzania tej samej nazwy typu do wywołania elementy członkowskie tego typu może spowodować pełne zasłoniętej kodu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="7eb6d-113">Na przykład następujące definicji `Circle` klasy odwołuje się do liczby elementów członkowskich <xref:System.Math> klasy.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="7eb6d-114">Dzięki wyeliminowaniu konieczności jawnie odwoływać się do <xref:System.Math> klasy zawsze odwołuje się element członkowski, `using static` dyrektywy tworzy dużo czyszczący kodu:</span><span class="sxs-lookup"><span data-stu-id="7eb6d-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="7eb6d-115">`using static` Importuje tylko dostępny statyczne elementy członkowskie i typy zagnieżdżone zadeklarowany w określonego typu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="7eb6d-116">Dziedziczone elementy członkowskie nie zostaną zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-116">Inherited members are not imported.</span></span>  <span data-ttu-id="7eb6d-117">Można importować z dowolnego typu o nazwie using dyrektywy statycznych, w tym moduły Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="7eb6d-118">Jeśli F # najwyższego poziomu funkcji są wyświetlane w metadanych jako statyczne elementy członkowskie typu nazwanego, którego nazwa jest prawidłowym identyfikatorem języka C#, F # funkcje mogą zostać zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="7eb6d-119">`using static` udostępnia metody rozszerzenia zadeklarowany w określonym typie dostępne do wyszukiwania — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="7eb6d-120">Jednak nazwy metody rozszerzenia nie są importowane do zakresu niekwalifikowane odwołania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="7eb6d-121">Metody o tej samej nazwie zaimportowane z różnych typów przez różne `using static` dyrektywy w tej samej jednostce kompilacyjnej lub przestrzeni nazw tworzą grupy metod.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="7eb6d-122">Rozpoznanie przeciążenia w tych grupach — metoda zgodna normalnych C# reguł.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7eb6d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="7eb6d-123">Example</span></span>

<span data-ttu-id="7eb6d-124">W poniższym przykładzie użyto `using static` dyrektywy Aby statyczne elementy członkowskie <xref:System.Console>, <xref:System.Math>, i <xref:System.String> klasy dostępne bez konieczności określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="7eb6d-125">W tym przykładzie `using static` dyrektywy można również zostały zastosowane do <xref:System.Double> typu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="7eb6d-126">To spowoduje umożliwiły do wywołania <xref:System.Double.TryParse(System.String,System.Double@)> metody bez określania nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="7eb6d-127">Jednak spowoduje to utworzenie kodu mniej do odczytu, ponieważ trzeba sprawdzić `using static` instrukcje, aby określić, którego typ liczbowy `TryParse` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="7eb6d-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="7eb6d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7eb6d-128">See also</span></span>

<span data-ttu-id="7eb6d-129">[Using — Dyrektywa](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="7eb6d-129">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="7eb6d-130">[Odwołanie w C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7eb6d-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="7eb6d-131">[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7eb6d-131">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="7eb6d-132">[Używanie usługi przestrzenie nazw](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="7eb6d-132">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="7eb6d-133">[Słowa kluczowe Namespace](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="7eb6d-133">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="7eb6d-134">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="7eb6d-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   
