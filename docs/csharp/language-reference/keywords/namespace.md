---
title: słowo kluczowe przestrzeni C# nazw — odwołanie
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: b35f0a2a5cc0b2895b491d4ee24f89955f4b8fed
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625803"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="cb4d9-102">namespace (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cb4d9-102">namespace (C# Reference)</span></span>

<span data-ttu-id="cb4d9-103">Słowo kluczowe `namespace` jest używane do deklarowania zakresu, który zawiera zestaw powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="cb4d9-104">Można użyć przestrzeni nazw do organizowania elementów kodu i tworzenia unikatowych typów globalnie.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>

[!code-csharp[csrefKeywordsNamespace#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#1)]

## <a name="remarks"></a><span data-ttu-id="cb4d9-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb4d9-105">Remarks</span></span>

<span data-ttu-id="cb4d9-106">W przestrzeni nazw można zadeklarować zero lub więcej następujących typów:</span><span class="sxs-lookup"><span data-stu-id="cb4d9-106">Within a namespace, you can declare zero or more of the following types:</span></span>

- <span data-ttu-id="cb4d9-107">inna przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="cb4d9-107">another namespace</span></span>

- [<span data-ttu-id="cb4d9-108">class</span><span class="sxs-lookup"><span data-stu-id="cb4d9-108">class</span></span>](class.md)

- [<span data-ttu-id="cb4d9-109">interface</span><span class="sxs-lookup"><span data-stu-id="cb4d9-109">interface</span></span>](interface.md)

- [<span data-ttu-id="cb4d9-110">struct</span><span class="sxs-lookup"><span data-stu-id="cb4d9-110">struct</span></span>](../builtin-types/struct.md)

- [<span data-ttu-id="cb4d9-111">enum</span><span class="sxs-lookup"><span data-stu-id="cb4d9-111">enum</span></span>](../builtin-types/enum.md)

- [<span data-ttu-id="cb4d9-112">delegate</span><span class="sxs-lookup"><span data-stu-id="cb4d9-112">delegate</span></span>](../builtin-types/reference-types.md#the-delegate-type)

<span data-ttu-id="cb4d9-113">Niezależnie od tego, czy jawnie deklarujesz przestrzeń nazw C# w pliku źródłowym, kompilator dodaje domyślną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="cb4d9-114">NIENAZWANA przestrzeń nazw, czasami określana jako globalna przestrzeń nazw, jest obecna w każdym pliku.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="cb4d9-115">Wszystkie identyfikatory w globalnej przestrzeni nazw są dostępne do użycia w nazwanym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>

<span data-ttu-id="cb4d9-116">Przestrzenie nazw niejawnie mają dostęp publiczny i nie są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="cb4d9-117">Aby uzyskać Omówienie modyfikatorów dostępu, które można przypisać do elementów w przestrzeni nazw, zobacz [Modyfikatory dostępu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="cb4d9-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](access-modifiers.md).</span></span>

<span data-ttu-id="cb4d9-118">Istnieje możliwość zdefiniowania przestrzeni nazw w dwóch lub większej liczbie deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="cb4d9-119">Na przykład poniższy przykład definiuje dwie klasy jako część przestrzeni nazw `MyCompany`:</span><span class="sxs-lookup"><span data-stu-id="cb4d9-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#2)]

## <a name="example"></a><span data-ttu-id="cb4d9-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb4d9-120">Example</span></span>

<span data-ttu-id="cb4d9-121">Poniższy przykład pokazuje, jak wywołać metodę statyczną w zagnieżdżonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cb4d9-121">The following example shows how to call a static method in a nested namespace.</span></span>

[!code-csharp[csrefKeywordsNamespace#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="cb4d9-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb4d9-122">C# language specification</span></span>

<span data-ttu-id="cb4d9-123">Aby uzyskać więcej informacji, zobacz sekcję [przestrzenie nazw](~/_csharplang/spec/namespaces.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cb4d9-123">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb4d9-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb4d9-124">See also</span></span>

- [<span data-ttu-id="cb4d9-125">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="cb4d9-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cb4d9-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cb4d9-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="cb4d9-127">using</span><span class="sxs-lookup"><span data-stu-id="cb4d9-127">using</span></span>](using-directive.md)
- [<span data-ttu-id="cb4d9-128">Używanie static</span><span class="sxs-lookup"><span data-stu-id="cb4d9-128">using static</span></span>](using-static.md)
- [<span data-ttu-id="cb4d9-129">`::` kwalifikator aliasu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="cb4d9-129">Namespace alias qualifier `::`</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="cb4d9-130">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="cb4d9-130">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
