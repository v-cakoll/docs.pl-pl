---
title: Użycie dyrektywy - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 3e8daf24929339e31cda81a726ec11fdcffc687a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660388"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="54929-102">Using — Dyrektywa (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="54929-102">using directive (C# Reference)</span></span>

<span data-ttu-id="54929-103">`using` Dyrektywy ma trzy zastosowań:</span><span class="sxs-lookup"><span data-stu-id="54929-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="54929-104">Aby zezwolić na używanie typów w przestrzeni nazw, tak, aby nie trzeba Zakwalifikuj użycie typu w tej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="54929-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="54929-105">Aby umożliwić dostęp do statycznych elementów członkowskich i typy zagnieżdżone typu bez konieczności kwalifikuj dostęp do nazwą typu.</span><span class="sxs-lookup"><span data-stu-id="54929-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="54929-106">Aby uzyskać więcej informacji, zobacz [using static, dyrektywa](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="54929-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="54929-107">Aby utworzyć alias dla przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="54929-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="54929-108">Jest to nazywane *użycie dyrektywy alias*.</span><span class="sxs-lookup"><span data-stu-id="54929-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="54929-109">`using` Słowo kluczowe jest również używane do tworzenia *za pomocą instrukcji*, co pomóc, upewnij się, że <xref:System.IDisposable> obiektów, takich jak pliki i czcionki są obsługiwane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="54929-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="54929-110">Zobacz [za pomocą instrukcji](using-statement.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="54929-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="54929-111">Za pomocą typu statycznego</span><span class="sxs-lookup"><span data-stu-id="54929-111">Using static type</span></span>

<span data-ttu-id="54929-112">Statyczne elementy członkowskie typu dostęp bez konieczności kwalifikuj dostęp do nazwą typu:</span><span class="sxs-lookup"><span data-stu-id="54929-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="54929-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54929-113">Remarks</span></span>

<span data-ttu-id="54929-114">Zakres `using` dyrektywa jest ograniczona do pliku, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="54929-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="54929-115">`using` Dyrektywy może się pojawić:</span><span class="sxs-lookup"><span data-stu-id="54929-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="54929-116">Na początku pliku kodu źródłowego, przed żadnych definicji przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="54929-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="54929-117">W dowolnym obszarze nazw, ale przed każdą przestrzeń nazw lub typów zadeklarowane w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="54929-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="54929-118">W przeciwnym razie, błąd kompilatora [CS1529](../../misc/cs1529.md) jest generowany.</span><span class="sxs-lookup"><span data-stu-id="54929-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="54929-119">Utwórz `using` alias — dyrektywa, aby ułatwić kwalifikują się do przestrzeni nazw lub typ identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="54929-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="54929-120">W dowolnym `using` dyrektywy, w pełni kwalifikowaną przestrzeń nazw lub typ należy użyć niezależnie od wartości `using` dyrektyw, które pochodzą przed nią.</span><span class="sxs-lookup"><span data-stu-id="54929-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="54929-121">Nie `using` alias mogą być używane w deklaracji `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="54929-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="54929-122">Na przykład poniższa generuje błąd kompilatora:</span><span class="sxs-lookup"><span data-stu-id="54929-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="54929-123">Utwórz `using` dyrektywy na używanie typów w przestrzeni nazw bez konieczności określania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="54929-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="54929-124">A `using` dyrektywy nie umożliwiają dostęp do wszelkich przestrzenie nazw, które są zagnieżdżone w przestrzeni nazw, należy określić.</span><span class="sxs-lookup"><span data-stu-id="54929-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="54929-125">Przestrzenie nazw są dostępne w dwóch kategorii: zdefiniowane przez użytkownika i zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="54929-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="54929-126">Zdefiniowane przez użytkownika przestrzenie nazw są przestrzenie nazw zdefiniowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="54929-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="54929-127">Aby uzyskać listę nazw zdefiniowaną przez system, zobacz [przeglądarka interfejsu API .NET](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="54929-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

<span data-ttu-id="54929-128">Przykłady dotyczące odwoływania się do metody w innych zestawach, zobacz [tworzenie i użyj zestawów przy użyciu wiersza polecenia](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="54929-128">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="54929-129">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="54929-129">Example 1</span></span>

<span data-ttu-id="54929-130">Poniższy przykład pokazuje, jak zdefiniować i zastosować `using` alias dla przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="54929-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="54929-131">Using — dyrektywa alias nie może mieć to otwarty typ ogólny po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="54929-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="54929-132">Na przykład nie można utworzyć za pomocą aliasu dla `List<T>`, ale można utworzyć dla `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="54929-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="54929-133">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="54929-133">Example 2</span></span>

<span data-ttu-id="54929-134">Poniższy przykład pokazuje jak zdefiniować `using` dyrektywy i `using` alias dla klasy:</span><span class="sxs-lookup"><span data-stu-id="54929-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="54929-135">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="54929-135">C# language specification</span></span>

<span data-ttu-id="54929-136">Aby uzyskać więcej informacji, zobacz [dyrektywy Using](~/_csharplang/spec/namespaces.md#using-directives) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="54929-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="54929-137">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="54929-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="54929-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54929-138">See also</span></span>

- [<span data-ttu-id="54929-139">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="54929-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="54929-140">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="54929-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="54929-141">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="54929-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="54929-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="54929-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="54929-143">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="54929-143">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="54929-144">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="54929-144">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="54929-145">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="54929-145">using Statement</span></span>](using-statement.md)
