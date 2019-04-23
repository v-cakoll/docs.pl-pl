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
ms.openlocfilehash: 4859c361b3321c1144204f63896152694f6ac5c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148762"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="ca165-102">namespace (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ca165-102">namespace (C# Reference)</span></span>

<span data-ttu-id="ca165-103">`namespace` — Słowo kluczowe jest używane do deklarowania zakresu, który zawiera zestaw powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ca165-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="ca165-104">Przestrzeń nazw można użyć do organizowania elementów kodu oraz tworzenie globalnie unikatowy typów.</span><span class="sxs-lookup"><span data-stu-id="ca165-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="ca165-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca165-105">Remarks</span></span>

<span data-ttu-id="ca165-106">W przestrzeni nazw można zadeklarować zero lub więcej z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ca165-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="ca165-107">innej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="ca165-107">another namespace</span></span>

- [<span data-ttu-id="ca165-108">class</span><span class="sxs-lookup"><span data-stu-id="ca165-108">class</span></span>](class.md)

- [<span data-ttu-id="ca165-109">interface</span><span class="sxs-lookup"><span data-stu-id="ca165-109">interface</span></span>](interface.md)

- [<span data-ttu-id="ca165-110">struct</span><span class="sxs-lookup"><span data-stu-id="ca165-110">struct</span></span>](struct.md)

- [<span data-ttu-id="ca165-111">enum</span><span class="sxs-lookup"><span data-stu-id="ca165-111">enum</span></span>](enum.md)

- [<span data-ttu-id="ca165-112">delegate</span><span class="sxs-lookup"><span data-stu-id="ca165-112">delegate</span></span>](delegate.md)

<span data-ttu-id="ca165-113">Czy jawnie deklarować przestrzeń nazw w pliku źródłowym języka C#, kompilator dodający domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="ca165-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="ca165-114">Tej nazwy przestrzeni nazw, czasami określane jako globalnej przestrzeni nazw jest obecny w każdym pliku.</span><span class="sxs-lookup"><span data-stu-id="ca165-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="ca165-115">Każdego identyfikatora w globalnej przestrzeni nazw jest dostępna do użytku w przestrzeni nazw o nazwie.</span><span class="sxs-lookup"><span data-stu-id="ca165-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="ca165-116">Przestrzenie nazw mają domyślnie dostęp publiczny i to nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="ca165-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="ca165-117">Omówienie modyfikatory dostępu, można przypisać do elementów w przestrzeni nazw, zobacz [modyfikatory dostępu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ca165-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="ca165-118">Istnieje możliwość definiowania przestrzeni nazw w dwóch lub więcej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ca165-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="ca165-119">Na przykład w poniższym przykładzie zdefiniowano dwie klasy jako część `MyCompany` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="ca165-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="ca165-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca165-120">Example</span></span>

<span data-ttu-id="ca165-121">Poniższy przykład pokazuje sposób wywołania metody statycznej w zagnieżdżonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ca165-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="related-resources"></a><span data-ttu-id="ca165-122">Powiązane zasoby</span><span class="sxs-lookup"><span data-stu-id="ca165-122">Related resources</span></span>

<span data-ttu-id="ca165-123">Aby uzyskać więcej informacji o korzystaniu z przestrzeni nazw zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="ca165-123">For more information about using namespaces, see the following topics:</span></span>

- [<span data-ttu-id="ca165-124">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="ca165-124">Namespaces</span></span>](../../programming-guide/namespaces/index.md)

- [<span data-ttu-id="ca165-125">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="ca165-125">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)

- [<span data-ttu-id="ca165-126">Instrukcje: Użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="ca165-126">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="ca165-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ca165-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ca165-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca165-128">See also</span></span>

- [<span data-ttu-id="ca165-129">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ca165-129">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="ca165-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ca165-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ca165-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ca165-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ca165-132">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="ca165-132">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="ca165-133">using</span><span class="sxs-lookup"><span data-stu-id="ca165-133">using</span></span>](using-directive.md)
- [<span data-ttu-id="ca165-134">Przy użyciu statycznej</span><span class="sxs-lookup"><span data-stu-id="ca165-134">using static</span></span>](using-static.md)