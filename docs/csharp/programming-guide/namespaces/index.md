---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="3a716-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3a716-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="3a716-103">Przestrzenie nazw silnie są używane w na dwa sposoby programowania w języku C#.</span><span class="sxs-lookup"><span data-stu-id="3a716-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="3a716-104">Najpierw .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3a716-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="3a716-105">`System`jest przestrzenią nazw i `Console` jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3a716-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="3a716-106">`using` Można można użyć słowa kluczowego, dzięki czemu Pełna nazwa nie jest wymagane, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a716-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="3a716-107">Aby uzyskać więcej informacji, zobacz [dyrektywa using](../../../csharp/language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="3a716-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="3a716-108">Po drugie deklarowanie własnych przestrzeni nazw ułatwia kontrolowanie zakresu nazw klasy i metody w większych projektów programowania.</span><span class="sxs-lookup"><span data-stu-id="3a716-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="3a716-109">Użyj [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) słowo kluczowe, aby zadeklarować przestrzeni nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a716-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="3a716-110">Omówienie przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="3a716-110">Namespaces Overview</span></span>  
 <span data-ttu-id="3a716-111">Przestrzenie nazw ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3a716-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="3a716-112">Ich organizowanie kodu dużych projektów.</span><span class="sxs-lookup"><span data-stu-id="3a716-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="3a716-113">Są rozdzielane przy użyciu `.` operatora.</span><span class="sxs-lookup"><span data-stu-id="3a716-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="3a716-114">`using directive` Eliminuje konieczność Określ nazwę obszaru nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="3a716-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="3a716-115">`global` Przestrzeni nazw jest przestrzenią nazw "root": `global::System` zawsze odwołuje się do przestrzeni nazw .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="3a716-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3a716-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3a716-116">Related Sections</span></span>  
 <span data-ttu-id="3a716-117">Zobacz następujące tematy, aby uzyskać więcej informacji o przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="3a716-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="3a716-118">Używanie usługi przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="3a716-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="3a716-119">Porady: użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="3a716-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="3a716-120">Porady: Użyj mojej Namespace</span><span class="sxs-lookup"><span data-stu-id="3a716-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3a716-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3a716-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3a716-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a716-122">See Also</span></span>  
 [<span data-ttu-id="3a716-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3a716-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3a716-124">Słowa kluczowe Namespace</span><span class="sxs-lookup"><span data-stu-id="3a716-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="3a716-125">Using — Dyrektywa</span><span class="sxs-lookup"><span data-stu-id="3a716-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="3a716-126">:: — Operator</span><span class="sxs-lookup"><span data-stu-id="3a716-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="3a716-127">. Operator</span><span class="sxs-lookup"><span data-stu-id="3a716-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
