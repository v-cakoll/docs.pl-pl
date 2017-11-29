---
title: "namespace (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76cc1adc21f6cfadc93da58250336705e43e333a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-c-reference"></a><span data-ttu-id="43269-102">namespace (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="43269-102">namespace (C# Reference)</span></span>
<span data-ttu-id="43269-103">`namespace` — Słowo kluczowe służy do deklarowania zakresu, który zawiera zestaw obiektów pokrewnych.</span><span class="sxs-lookup"><span data-stu-id="43269-103">The `namespace` keyword is used to declare a scope that contains a set of related objects.</span></span> <span data-ttu-id="43269-104">Przestrzeń nazw można użyć do organizowania elementów kodu i tworzenia unikatowych typów.</span><span class="sxs-lookup"><span data-stu-id="43269-104">You can use a namespace to organize code elements and to create globally unique types.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="43269-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43269-105">Remarks</span></span>  
 <span data-ttu-id="43269-106">W przypadku przestrzeni nazw można zadeklarować co najmniej jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="43269-106">Within a namespace, you can declare one or more of the following types:</span></span>  
  
-   <span data-ttu-id="43269-107">innej przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="43269-107">another namespace</span></span>  
  
-   [<span data-ttu-id="43269-108">klasy</span><span class="sxs-lookup"><span data-stu-id="43269-108">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="43269-109">Interfejs</span><span class="sxs-lookup"><span data-stu-id="43269-109">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
-   [<span data-ttu-id="43269-110">— Struktura</span><span class="sxs-lookup"><span data-stu-id="43269-110">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="43269-111">wyliczenia</span><span class="sxs-lookup"><span data-stu-id="43269-111">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
-   [<span data-ttu-id="43269-112">Delegowanie</span><span class="sxs-lookup"><span data-stu-id="43269-112">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
 <span data-ttu-id="43269-113">Czy jawnie zadeklarować przestrzeni nazw w pliku źródłowym C#, kompilator dodaje domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="43269-113">Whether or not you explicitly declare a namespace in a C# source file, the compiler adds a default namespace.</span></span> <span data-ttu-id="43269-114">Ta nienazwanej przestrzeni nazw, czasami określane jako globalnej przestrzeni nazw jest obecny w każdym pliku.</span><span class="sxs-lookup"><span data-stu-id="43269-114">This unnamed namespace, sometimes referred to as the global namespace, is present in every file.</span></span> <span data-ttu-id="43269-115">Wszelkie identyfikator w globalnej przestrzeni nazw jest dostępny do użytku w nazwanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="43269-115">Any identifier in the global namespace is available for use in a named namespace.</span></span>  
  
 <span data-ttu-id="43269-116">Przestrzenie nazw niejawnie mają dostęp publiczny i nie jest to można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="43269-116">Namespaces implicitly have public access and this is not modifiable.</span></span> <span data-ttu-id="43269-117">Omówienie modyfikatorów dostępu można przypisać do elementów w przestrzeni nazw, zobacz [modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="43269-117">For a discussion of the access modifiers you can assign to elements in a namespace, see [Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="43269-118">Jest możliwe określenie przestrzeni nazw w deklaracjach dwóch lub więcej.</span><span class="sxs-lookup"><span data-stu-id="43269-118">It is possible to define a namespace in two or more declarations.</span></span> <span data-ttu-id="43269-119">Na przykład w poniższym przykładzie zdefiniowano dwie klasy jako część `MyCompany` przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="43269-119">For example, the following example defines two classes as part of the `MyCompany` namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="43269-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="43269-120">Example</span></span>  
 <span data-ttu-id="43269-121">Poniższy przykład przedstawia sposób wywołania metody statycznej w zagnieżdżonych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="43269-121">The following example shows how to call a static method in a nested namespace.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a><span data-ttu-id="43269-122">Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="43269-122">For More Information</span></span>  
 <span data-ttu-id="43269-123">Aby uzyskać więcej informacji o korzystaniu z przestrzeni nazw zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="43269-123">For more information about using namespaces, see the following topics:</span></span>  
  
-   [<span data-ttu-id="43269-124">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="43269-124">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [<span data-ttu-id="43269-125">Używanie usługi przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="43269-125">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="43269-126">Porady: użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="43269-126">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="43269-127">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="43269-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43269-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43269-128">See Also</span></span>  
 [<span data-ttu-id="43269-129">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="43269-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="43269-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="43269-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="43269-131">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="43269-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="43269-132">Słowa kluczowe Namespace</span><span class="sxs-lookup"><span data-stu-id="43269-132">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="43269-133">za pomocą</span><span class="sxs-lookup"><span data-stu-id="43269-133">using</span></span>](../../../csharp/language-reference/keywords/using.md)
