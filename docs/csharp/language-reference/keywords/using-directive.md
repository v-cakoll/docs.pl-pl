---
title: za pomocą dyrektywy - C# Odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 4f7ddad8c3dc12391ef6bf345a73ebb384400b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093152"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="38329-102">za pomocą dyrektywy (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="38329-102">using directive (C# Reference)</span></span>

<span data-ttu-id="38329-103">Dyrektywa `using` ma trzy zastosowania:</span><span class="sxs-lookup"><span data-stu-id="38329-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="38329-104">Aby zezwolić na używanie typów w obszarze nazw, dzięki czemu nie trzeba kwalifikować użycie typu w tym obszarze nazw:</span><span class="sxs-lookup"><span data-stu-id="38329-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="38329-105">Aby umożliwić dostęp do elementów statycznych i zagnieżdżonych typów typu bez konieczności kwalifikowania dostępu z nazwą typu.</span><span class="sxs-lookup"><span data-stu-id="38329-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="38329-106">Aby uzyskać więcej informacji, zobacz [using static dyrektywy](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="38329-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="38329-107">Aby utworzyć alias dla obszaru nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="38329-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="38329-108">Jest to tak zwana *dyrektywa używająca aliasu*.</span><span class="sxs-lookup"><span data-stu-id="38329-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="38329-109">Słowo `using` kluczowe jest również używane do tworzenia <xref:System.IDisposable> za pomocą *instrukcji*, które pomagają zapewnić, że obiekty, takie jak pliki i czcionki są obsługiwane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="38329-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="38329-110">Aby uzyskać więcej [informacji, zobacz korzystanie z instrukcji.](using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="38329-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="38329-111">Korzystanie z typu statycznego</span><span class="sxs-lookup"><span data-stu-id="38329-111">Using static type</span></span>

<span data-ttu-id="38329-112">Dostęp do statycznych elementów członkowskich typu można uzyskać bez konieczności kwalifikowania dostępu przy użyciu nazwy typu:</span><span class="sxs-lookup"><span data-stu-id="38329-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a><span data-ttu-id="38329-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38329-113">Remarks</span></span>

<span data-ttu-id="38329-114">Zakres `using` dyrektywy jest ograniczony do pliku, w którym się pojawia.</span><span class="sxs-lookup"><span data-stu-id="38329-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="38329-115">Dyrektywa `using` może pojawić się:</span><span class="sxs-lookup"><span data-stu-id="38329-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="38329-116">Na początku pliku kodu źródłowego, przed dowolnym obszarem nazw lub definicjami typów.</span><span class="sxs-lookup"><span data-stu-id="38329-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="38329-117">W dowolnym obszarze nazw, ale przed dowolnym obszarem nazw lub typami zadeklarowanym w tym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="38329-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="38329-118">W przeciwnym razie generowany jest błąd kompilatora [CS1529.](../../misc/cs1529.md)</span><span class="sxs-lookup"><span data-stu-id="38329-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="38329-119">Utwórz `using` dyrektywę aliasu, aby ułatwić kwalifikowanie identyfikatora do obszaru nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="38329-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="38329-120">W `using` każdej dyrektywie w pełni kwalifikowana przestrzeń nazw lub `using` typ muszą być używane niezależnie od dyrektyw, które są przed nim.</span><span class="sxs-lookup"><span data-stu-id="38329-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="38329-121">Nie `using` alias może być używany `using` w deklaracji dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="38329-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="38329-122">Na przykład następujące generuje błąd kompilatora:</span><span class="sxs-lookup"><span data-stu-id="38329-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="38329-123">Utwórz `using` dyrektywę, aby używać typów w obszarze nazw bez konieczności określania obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="38329-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="38329-124">Dyrektywa `using` nie daje dostępu do żadnych obszarów nazw, które są zagnieżdżone w określonym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="38329-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="38329-125">Przestrzenie nazw są dostępne w dwóch kategoriach: zdefiniowane przez użytkownika i zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="38329-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="38329-126">Przestrzenie nazw zdefiniowane przez użytkownika to obszary nazw zdefiniowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="38329-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="38329-127">Aby uzyskać listę obszarów nazw zdefiniowanych przez system, zobacz [Przeglądarka interfejsu API .NET](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="38329-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="38329-128">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="38329-128">Example 1</span></span>

<span data-ttu-id="38329-129">W poniższym przykładzie pokazano, `using` jak zdefiniować alias i używać go dla obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="38329-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="38329-130">A using alias dyrektywy nie może mieć otwarty typ ogólny po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="38329-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="38329-131">Na przykład nie można utworzyć aliasu używającego `List<T>`dla , `List<int>`ale można go utworzyć dla .</span><span class="sxs-lookup"><span data-stu-id="38329-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="38329-132">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="38329-132">Example 2</span></span>

<span data-ttu-id="38329-133">W poniższym przykładzie pokazano, jak zdefiniować dyrektywę `using` i `using` alias dla klasy:</span><span class="sxs-lookup"><span data-stu-id="38329-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="38329-134">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="38329-134">C# language specification</span></span>

<span data-ttu-id="38329-135">Aby uzyskać więcej informacji, zobacz [Korzystanie z dyrektyw](~/_csharplang/spec/namespaces.md#using-directives) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="38329-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="38329-136">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="38329-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="38329-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38329-137">See also</span></span>

- [<span data-ttu-id="38329-138">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="38329-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="38329-139">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="38329-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="38329-140">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="38329-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="38329-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="38329-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="38329-142">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="38329-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="38329-143">za pomocą instrukcji</span><span class="sxs-lookup"><span data-stu-id="38329-143">using Statement</span></span>](using-statement.md)
