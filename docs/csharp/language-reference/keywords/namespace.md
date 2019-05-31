---
title: słowo kluczowe przestrzeni nazw - C# odwołania
ms.custom: seoapril2019
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: df921ecc670bf12411dc8b0d828d6c19bb0a1aec
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422747"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="19af0-102">namespace (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="19af0-102">namespace (C# Reference)</span></span>

<span data-ttu-id="19af0-103">`namespace` — Słowo kluczowe jest używane do deklarowania zakresu, który zawiera zestaw powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="19af0-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="19af0-104">Przestrzeń nazw można użyć do organizowania elementów kodu oraz tworzenie globalnie unikatowy typów.</span><span class="sxs-lookup"><span data-stu-id="19af0-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="19af0-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19af0-105">Remarks</span></span>

<span data-ttu-id="19af0-106">W przestrzeni nazw można zadeklarować zero lub więcej z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="19af0-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="19af0-107">innej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="19af0-107">another namespace</span></span>

- [<span data-ttu-id="19af0-108">class</span><span class="sxs-lookup"><span data-stu-id="19af0-108">class</span></span>](class.md)

- [<span data-ttu-id="19af0-109">interface</span><span class="sxs-lookup"><span data-stu-id="19af0-109">interface</span></span>](interface.md)

- [<span data-ttu-id="19af0-110">struct</span><span class="sxs-lookup"><span data-stu-id="19af0-110">struct</span></span>](struct.md)

- [<span data-ttu-id="19af0-111">enum</span><span class="sxs-lookup"><span data-stu-id="19af0-111">enum</span></span>](enum.md)

- [<span data-ttu-id="19af0-112">delegate</span><span class="sxs-lookup"><span data-stu-id="19af0-112">delegate</span></span>](delegate.md)

<span data-ttu-id="19af0-113">Czy jawnie deklarować przestrzeń nazw w pliku źródłowym języka C#, kompilator dodający domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="19af0-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="19af0-114">Tej nazwy przestrzeni nazw, czasami określane jako globalnej przestrzeni nazw jest obecny w każdym pliku.</span><span class="sxs-lookup"><span data-stu-id="19af0-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="19af0-115">Każdego identyfikatora w globalnej przestrzeni nazw jest dostępna do użytku w przestrzeni nazw o nazwie.</span><span class="sxs-lookup"><span data-stu-id="19af0-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="19af0-116">Przestrzenie nazw mają domyślnie dostęp publiczny i to nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="19af0-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="19af0-117">Omówienie modyfikatory dostępu, można przypisać do elementów w przestrzeni nazw, zobacz [modyfikatory dostępu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="19af0-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="19af0-118">Istnieje możliwość definiowania przestrzeni nazw w dwóch lub więcej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="19af0-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="19af0-119">Na przykład w poniższym przykładzie zdefiniowano dwie klasy jako część `MyCompany` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="19af0-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="19af0-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="19af0-120">Example</span></span>

<span data-ttu-id="19af0-121">Poniższy przykład pokazuje sposób wywołania metody statycznej w zagnieżdżonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="19af0-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a><span data-ttu-id="19af0-122">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="19af0-122">Related resources</span></span>

<span data-ttu-id="19af0-123">Aby uzyskać więcej informacji o korzystaniu z przestrzeni nazw zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="19af0-123">For more information about using namespaces, see the following topics:</span></span>

- [<span data-ttu-id="19af0-124">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="19af0-124">Namespaces</span></span>](../../programming-guide/namespaces/index.md)

- [<span data-ttu-id="19af0-125">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="19af0-125">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)

- [<span data-ttu-id="19af0-126">Instrukcje: Użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="19af0-126">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="19af0-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="19af0-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="19af0-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19af0-128">See also</span></span>

- [<span data-ttu-id="19af0-129">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="19af0-129">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="19af0-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="19af0-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="19af0-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="19af0-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="19af0-132">using</span><span class="sxs-lookup"><span data-stu-id="19af0-132">using</span></span>](using-directive.md)
- [<span data-ttu-id="19af0-133">Przy użyciu statycznej</span><span class="sxs-lookup"><span data-stu-id="19af0-133">using static</span></span>](using-static.md)
