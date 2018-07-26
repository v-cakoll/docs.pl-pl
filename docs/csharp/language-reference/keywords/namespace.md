---
title: namespace (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
ms.openlocfilehash: 343cce85dd235532fbe3fc90af0a785f48518db7
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245618"
---
# <a name="namespace-c-reference"></a><span data-ttu-id="db7fe-102">namespace (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="db7fe-102">namespace (C# Reference)</span></span>
<span data-ttu-id="db7fe-103">`namespace` — Słowo kluczowe jest używane do deklarowania zakresu, który zawiera zestaw powiązanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="db7fe-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="db7fe-104">Przestrzeń nazw można użyć do organizowania elementów kodu oraz tworzenie globalnie unikatowy typów.</span><span class="sxs-lookup"><span data-stu-id="db7fe-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="db7fe-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db7fe-105">Remarks</span></span>  
 <span data-ttu-id="db7fe-106">W przestrzeni nazw można zadeklarować co najmniej jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="db7fe-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="db7fe-107">innej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="db7fe-107">another namespace</span></span>  
  
-   [<span data-ttu-id="db7fe-108">class</span><span class="sxs-lookup"><span data-stu-id="db7fe-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="db7fe-109">interface</span><span class="sxs-lookup"><span data-stu-id="db7fe-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="db7fe-110">struct</span><span class="sxs-lookup"><span data-stu-id="db7fe-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="db7fe-111">enum</span><span class="sxs-lookup"><span data-stu-id="db7fe-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="db7fe-112">delegate</span><span class="sxs-lookup"><span data-stu-id="db7fe-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="db7fe-113">Czy jawnie deklarować przestrzeń nazw w pliku źródłowym języka C#, kompilator dodający domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="db7fe-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="db7fe-114">Tej nazwy przestrzeni nazw, czasami określane jako globalnej przestrzeni nazw jest obecny w każdym pliku.</span><span class="sxs-lookup"><span data-stu-id="db7fe-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="db7fe-115">Każdego identyfikatora w globalnej przestrzeni nazw jest dostępna do użytku w przestrzeni nazw o nazwie.</span><span class="sxs-lookup"><span data-stu-id="db7fe-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="db7fe-116">Przestrzenie nazw mają domyślnie dostęp publiczny i to nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="db7fe-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="db7fe-117">Omówienie modyfikatory dostępu, można przypisać do elementów w przestrzeni nazw, zobacz [modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="db7fe-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="db7fe-118">Istnieje możliwość definiowania przestrzeni nazw w dwóch lub więcej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="db7fe-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="db7fe-119">Na przykład w poniższym przykładzie zdefiniowano dwie klasy jako część `MyCompany` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="db7fe-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="db7fe-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="db7fe-120">Example</span></span>  
 <span data-ttu-id="db7fe-121">Poniższy przykład pokazuje sposób wywołania metody statycznej w zagnieżdżonej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="db7fe-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="db7fe-122">Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="db7fe-122">For More Information</span></span>  
 <span data-ttu-id="db7fe-123">Aby uzyskać więcej informacji o korzystaniu z przestrzeni nazw zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="db7fe-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="db7fe-124">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="db7fe-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="db7fe-125">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="db7fe-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="db7fe-126">Instrukcje: użycie globalnych aliasów przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="db7fe-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="db7fe-127">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="db7fe-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="db7fe-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db7fe-128">See Also</span></span>  
 [<span data-ttu-id="db7fe-129">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="db7fe-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="db7fe-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="db7fe-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="db7fe-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="db7fe-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="db7fe-132">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="db7fe-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="db7fe-133">using</span><span class="sxs-lookup"><span data-stu-id="db7fe-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
