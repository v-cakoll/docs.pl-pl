---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334353"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="c0a43-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c0a43-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="c0a43-103">Przestrzenie nazw silnie są używane w na dwa sposoby programowania w języku C#.</span><span class="sxs-lookup"><span data-stu-id="c0a43-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="c0a43-104">Najpierw .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c0a43-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="c0a43-105">`System` jest przestrzenią nazw i `Console` jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c0a43-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="c0a43-106">`using` Można można użyć słowa kluczowego, dzięki czemu Pełna nazwa nie jest wymagane, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c0a43-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="c0a43-107">Aby uzyskać więcej informacji, zobacz [dyrektywa using](../../../csharp/language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="c0a43-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="c0a43-108">Po drugie deklarowanie własnych przestrzeni nazw ułatwia kontrolowanie zakresu nazw klasy i metody w większych projektów programowania.</span><span class="sxs-lookup"><span data-stu-id="c0a43-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="c0a43-109">Użyj [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) słowo kluczowe, aby zadeklarować przestrzeni nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c0a43-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="c0a43-110">Omówienie przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="c0a43-110">Namespaces Overview</span></span>  
 <span data-ttu-id="c0a43-111">Przestrzenie nazw ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c0a43-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="c0a43-112">Ich organizowanie kodu dużych projektów.</span><span class="sxs-lookup"><span data-stu-id="c0a43-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="c0a43-113">Są rozdzielane przy użyciu `.` operatora.</span><span class="sxs-lookup"><span data-stu-id="c0a43-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="c0a43-114">`using directive` Eliminuje konieczność Określ nazwę obszaru nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="c0a43-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="c0a43-115">`global` Przestrzeni nazw jest przestrzenią nazw "root": `global::System` zawsze odwołuje się do przestrzeni nazw .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="c0a43-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0a43-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c0a43-116">Related Sections</span></span>  
 <span data-ttu-id="c0a43-117">Zobacz następujące tematy, aby uzyskać więcej informacji o przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="c0a43-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="c0a43-118">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="c0a43-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="c0a43-119">Instrukcje: użycie globalnych aliasów przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="c0a43-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="c0a43-120">Instrukcje: użycie przestrzeni nazw typu My</span><span class="sxs-lookup"><span data-stu-id="c0a43-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="c0a43-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c0a43-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c0a43-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0a43-122">See Also</span></span>  
 [<span data-ttu-id="c0a43-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c0a43-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c0a43-124">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="c0a43-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="c0a43-125">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="c0a43-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="c0a43-126">::, operator</span><span class="sxs-lookup"><span data-stu-id="c0a43-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="c0a43-127">. operator</span><span class="sxs-lookup"><span data-stu-id="c0a43-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
