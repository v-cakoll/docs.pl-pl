---
title: słowo kluczowe obszaru nazw — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625803"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="ad2fb-102">namespace (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ad2fb-102">namespace (C# Reference)</span></span>

<span data-ttu-id="ad2fb-103">Słowo `namespace` kluczowe służy do deklarowania zakresu, który zawiera zestaw powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="ad2fb-104">Za pomocą obszaru nazw można organizować elementy kodu i tworzyć typy unikatowe globalnie.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="ad2fb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad2fb-105">Remarks</span></span>

<span data-ttu-id="ad2fb-106">W obszarze nazw można zadeklarować zero lub więcej z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ad2fb-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="ad2fb-107">inny obszar nazw</span><span class="sxs-lookup"><span data-stu-id="ad2fb-107">another namespace</span></span>

- [<span data-ttu-id="ad2fb-108">Klasa</span><span class="sxs-lookup"><span data-stu-id="ad2fb-108">class</span></span>](class.md)

- [<span data-ttu-id="ad2fb-109">Interfejs</span><span class="sxs-lookup"><span data-stu-id="ad2fb-109">interface</span></span>](interface.md)

- [<span data-ttu-id="ad2fb-110">Struct</span><span class="sxs-lookup"><span data-stu-id="ad2fb-110">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="ad2fb-111">Enum</span><span class="sxs-lookup"><span data-stu-id="ad2fb-111">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="ad2fb-112">delegate</span><span class="sxs-lookup"><span data-stu-id="ad2fb-112">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="ad2fb-113">Niezależnie od tego, czy jawnie zadeklarować obszar nazw w pliku źródłowym Języka C#, kompilator dodaje domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="ad2fb-114">Ta nienazwana przestrzeń nazw, czasami nazywana globalną przestrzenią nazw, jest obecna w każdym pliku.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="ad2fb-115">Dowolny identyfikator w globalnej przestrzeni nazw jest dostępny do użycia w nazwanym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="ad2fb-116">Przestrzenie nazw niejawnie mają dostęp publiczny i nie można tego modyfikować.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="ad2fb-117">Aby uzyskać omówienie modyfikatorów dostępu, które można przypisać do elementów w obszarze nazw, zobacz [Modyfikatory programu Access](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ad2fb-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="ad2fb-118">Istnieje możliwość zdefiniowania obszaru nazw w dwóch lub więcej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="ad2fb-119">Na przykład w poniższym przykładzie definiuje dwie `MyCompany` klasy jako część obszaru nazw:</span><span class="sxs-lookup"><span data-stu-id="ad2fb-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="ad2fb-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad2fb-120">Example</span></span>

<span data-ttu-id="ad2fb-121">W poniższym przykładzie pokazano, jak wywołać metodę statyczną w zagnieżdżonym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="ad2fb-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="ad2fb-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ad2fb-122">C# language specification</span></span>

<span data-ttu-id="ad2fb-123">Aby uzyskać więcej informacji, zobacz [sekcję Przestrzenie nazw](~/_csharplang/spec/namespaces.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="ad2fb-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad2fb-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad2fb-124">See also</span></span>

- [<span data-ttu-id="ad2fb-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ad2fb-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ad2fb-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ad2fb-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="ad2fb-127">Za pomocą</span><span class="sxs-lookup"><span data-stu-id="ad2fb-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="ad2fb-128">za pomocą statycznego</span><span class="sxs-lookup"><span data-stu-id="ad2fb-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="ad2fb-129">Kwalifikator aliasu obszaru nazw`::`</span><span class="sxs-lookup"><span data-stu-id="ad2fb-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="ad2fb-130">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="ad2fb-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
