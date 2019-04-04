---
title: Przestrzenie nazw — C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 3e05e18225b198e9e34b4b96717cc813dab836c7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971276"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="35a7c-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="35a7c-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="35a7c-103">Przestrzenie nazw są intensywnie używane w języku C# programming na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="35a7c-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="35a7c-104">Po pierwsze .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="35a7c-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="35a7c-105">`System` jest to obszar nazw i `Console` jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="35a7c-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="35a7c-106">`using` — Słowo kluczowe może służyć tak, aby pełna nazwa nie jest wymagane, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="35a7c-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="35a7c-107">Aby uzyskać więcej informacji, zobacz [użycie dyrektywy](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="35a7c-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="35a7c-108">Po drugie deklarowania własne przestrzenie nazw mogą pomóc Ci kontrolować zakres nazwy klasy i metody w dużych projektach programowania.</span><span class="sxs-lookup"><span data-stu-id="35a7c-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="35a7c-109">Użyj [przestrzeni nazw](../../language-reference/keywords/namespace.md) — słowo kluczowe do deklarowania, przestrzeń nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="35a7c-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="35a7c-110">Nazwa przestrzeni nazw musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="35a7c-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="35a7c-111">Przegląd przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="35a7c-111">Namespaces Overview</span></span>  

<span data-ttu-id="35a7c-112">Przestrzenie nazw mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="35a7c-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="35a7c-113">Ich organizowanie kodu dużych projektów.</span><span class="sxs-lookup"><span data-stu-id="35a7c-113">They organize large code projects.</span></span>  
- <span data-ttu-id="35a7c-114">Są rozdzielane przy użyciu `.` operatora.</span><span class="sxs-lookup"><span data-stu-id="35a7c-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="35a7c-115">`using` Dyrektywy eliminuje konieczność określenia nazwy obszaru nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="35a7c-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="35a7c-116">`global` Przestrzeń nazw jest przestrzeń nazw "root": `global::System` zawsze będzie odnosił się do platformy .NET <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="35a7c-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="35a7c-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="35a7c-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35a7c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35a7c-118">See also</span></span>

- [<span data-ttu-id="35a7c-119">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="35a7c-119">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="35a7c-120">Instrukcje: Użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="35a7c-120">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="35a7c-121">Instrukcje: Użyj mojej Namespace</span><span class="sxs-lookup"><span data-stu-id="35a7c-121">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="35a7c-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="35a7c-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="35a7c-123">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="35a7c-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="35a7c-124">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="35a7c-124">Namespace Keywords</span></span>](../../language-reference/keywords/namespace-keywords.md)
- [<span data-ttu-id="35a7c-125">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="35a7c-125">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="35a7c-126">:: operator</span><span class="sxs-lookup"><span data-stu-id="35a7c-126">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)
- [<span data-ttu-id="35a7c-127">. operator</span><span class="sxs-lookup"><span data-stu-id="35a7c-127">. Operator</span></span>](../../language-reference/operators/member-access-operator.md)
