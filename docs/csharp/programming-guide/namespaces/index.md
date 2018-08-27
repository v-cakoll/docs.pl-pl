---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934876"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="a4701-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a4701-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="a4701-103">Przestrzenie nazw są intensywnie używane w języku C# programming na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="a4701-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="a4701-104">Po pierwsze .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a4701-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="a4701-105">`System` jest to obszar nazw i `Console` jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a4701-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="a4701-106">`using` — Słowo kluczowe może służyć tak, aby pełna nazwa nie jest wymagane, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a4701-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="a4701-107">Aby uzyskać więcej informacji, zobacz [użycie dyrektywy](../../../csharp/language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="a4701-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="a4701-108">Po drugie deklarowania własne przestrzenie nazw mogą pomóc Ci kontrolować zakres nazwy klasy i metody w dużych projektach programowania.</span><span class="sxs-lookup"><span data-stu-id="a4701-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="a4701-109">Użyj [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) — słowo kluczowe do deklarowania, przestrzeń nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a4701-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="a4701-110">Przegląd przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a4701-110">Namespaces Overview</span></span>  
 <span data-ttu-id="a4701-111">Przestrzenie nazw mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a4701-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="a4701-112">Ich organizowanie kodu dużych projektów.</span><span class="sxs-lookup"><span data-stu-id="a4701-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="a4701-113">Są rozdzielane przy użyciu `.` operatora.</span><span class="sxs-lookup"><span data-stu-id="a4701-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="a4701-114">`using directive` Eliminuje konieczność określenia nazwy obszaru nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="a4701-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="a4701-115">`global` Przestrzeń nazw jest przestrzeń nazw "root": `global::System` zawsze będzie odnosił się do przestrzeni nazw .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="a4701-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a4701-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a4701-116">Related Sections</span></span>  
 <span data-ttu-id="a4701-117">Zobacz następujące tematy, aby uzyskać więcej informacji na temat przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="a4701-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="a4701-118">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a4701-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="a4701-119">Instrukcje: użycie globalnych aliasów przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a4701-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="a4701-120">Instrukcje: użycie przestrzeni nazw typu My</span><span class="sxs-lookup"><span data-stu-id="a4701-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a4701-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a4701-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a4701-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4701-122">See Also</span></span>  
 [<span data-ttu-id="a4701-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a4701-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a4701-124">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a4701-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="a4701-125">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="a4701-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="a4701-126">::, operator</span><span class="sxs-lookup"><span data-stu-id="a4701-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="a4701-127">. operator</span><span class="sxs-lookup"><span data-stu-id="a4701-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
