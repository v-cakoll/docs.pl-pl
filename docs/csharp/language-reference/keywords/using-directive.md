---
title: Używanie dyrektywy- C# Reference
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: a2028ccce47de54b59323194a0ffab3a643d878c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712978"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="6df2d-102">Using — dyrektywaC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="6df2d-102">using directive (C# Reference)</span></span>

<span data-ttu-id="6df2d-103">Dyrektywa `using` ma trzy zastosowania:</span><span class="sxs-lookup"><span data-stu-id="6df2d-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="6df2d-104">Aby zezwolić na używanie typów w przestrzeni nazw, aby nie trzeba było kwalifikować użycia typu w tej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="6df2d-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="6df2d-105">Aby umożliwić dostęp do statycznych elementów członkowskich i typów zagnieżdżonych typu bez konieczności kwalifikowania dostępu przy użyciu nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="6df2d-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="6df2d-106">Aby uzyskać więcej informacji, zobacz [Using static dyrektywą](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="6df2d-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="6df2d-107">Aby utworzyć alias dla przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="6df2d-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="6df2d-108">Ta nazwa jest nazywana *dyrektywą aliasu using*.</span><span class="sxs-lookup"><span data-stu-id="6df2d-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="6df2d-109">Słowo kluczowe `using` jest również używane do tworzenia *instrukcji using*, które ułatwiają zapewnienie, że <xref:System.IDisposable> obiektów, takich jak pliki i czcionki, są obsługiwane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="6df2d-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="6df2d-110">Aby uzyskać więcej informacji, zobacz [używanie instrukcji using](using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="6df2d-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="6df2d-111">Używanie typu statycznego</span><span class="sxs-lookup"><span data-stu-id="6df2d-111">Using static type</span></span>

<span data-ttu-id="6df2d-112">Można uzyskać dostęp do statycznych elementów członkowskich typu bez konieczności kwalifikowania dostępu przy użyciu nazwy typu:</span><span class="sxs-lookup"><span data-stu-id="6df2d-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="6df2d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6df2d-113">Remarks</span></span>

<span data-ttu-id="6df2d-114">Zakres dyrektywy `using` jest ograniczony do pliku, w którym występuje.</span><span class="sxs-lookup"><span data-stu-id="6df2d-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="6df2d-115">`using` można wyświetlić dyrektywy:</span><span class="sxs-lookup"><span data-stu-id="6df2d-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="6df2d-116">Na początku pliku kodu źródłowego przed dowolnymi obszarami nazw lub definicjami typów.</span><span class="sxs-lookup"><span data-stu-id="6df2d-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="6df2d-117">W dowolnej przestrzeni nazw, ale przed wszelkimi obszarami nazw lub typami zadeklarowanymi w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6df2d-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="6df2d-118">W przeciwnym razie zostanie wygenerowany błąd kompilatora [CS1529](../../misc/cs1529.md) .</span><span class="sxs-lookup"><span data-stu-id="6df2d-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="6df2d-119">Utwórz dyrektywę aliasu `using`, aby ułatwić kwalifikowanie identyfikatora do przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="6df2d-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="6df2d-120">W dowolnej dyrektywie `using` w pełni kwalifikowana przestrzeń nazw lub typ muszą być używane niezależnie od dyrektyw `using`, które przed nim pochodzą.</span><span class="sxs-lookup"><span data-stu-id="6df2d-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="6df2d-121">Nie można użyć aliasu `using` w deklaracji dyrektywy `using`.</span><span class="sxs-lookup"><span data-stu-id="6df2d-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="6df2d-122">Na przykład poniższy kod generuje błąd kompilatora:</span><span class="sxs-lookup"><span data-stu-id="6df2d-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="6df2d-123">Utwórz dyrektywę `using`, aby użyć typów w przestrzeni nazw bez konieczności określania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6df2d-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="6df2d-124">Dyrektywa `using` nie zapewnia dostępu do żadnych przestrzeni nazw, które są zagnieżdżone w określonym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="6df2d-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="6df2d-125">Przestrzenie nazw są dostępne w dwóch kategoriach: zdefiniowane przez użytkownika i zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="6df2d-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="6df2d-126">Przestrzenie nazw zdefiniowane przez użytkownika to przestrzenie nazw zdefiniowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6df2d-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="6df2d-127">Aby uzyskać listę przestrzeni nazw zdefiniowanych przez system, zobacz [.NET API Browser](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="6df2d-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="6df2d-128">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="6df2d-128">Example 1</span></span>

<span data-ttu-id="6df2d-129">Poniższy przykład pokazuje sposób definiowania i używania aliasu `using` dla przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="6df2d-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="6df2d-130">Dyrektywa using alias nie może mieć otwartego typu ogólnego po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="6df2d-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="6df2d-131">Nie można na przykład utworzyć aliasu using dla `List<T>`, ale można go utworzyć dla `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="6df2d-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="6df2d-132">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="6df2d-132">Example 2</span></span>

<span data-ttu-id="6df2d-133">Poniższy przykład pokazuje, jak zdefiniować dyrektywę `using` i alias `using` dla klasy:</span><span class="sxs-lookup"><span data-stu-id="6df2d-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="6df2d-134">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6df2d-134">C# language specification</span></span>

<span data-ttu-id="6df2d-135">Aby uzyskać więcej informacji, zobacz [Używanie dyrektyw](~/_csharplang/spec/namespaces.md#using-directives) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="6df2d-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="6df2d-136">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="6df2d-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="6df2d-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6df2d-137">See also</span></span>

- [<span data-ttu-id="6df2d-138">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6df2d-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6df2d-139">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6df2d-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6df2d-140">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="6df2d-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="6df2d-141">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6df2d-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6df2d-142">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="6df2d-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="6df2d-143">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6df2d-143">using Statement</span></span>](using-statement.md)
