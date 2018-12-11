---
title: Przestrzenie nazw — C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 4abdf8a0008ce50a89eb5f3ad3512a9579dc832a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236755"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="a7b35-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a7b35-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="a7b35-103">Przestrzenie nazw są intensywnie używane w języku C# programming na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="a7b35-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="a7b35-104">Po pierwsze .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a7b35-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
<span data-ttu-id="a7b35-105">`System` jest to obszar nazw i `Console` jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a7b35-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="a7b35-106">`using` — Słowo kluczowe może służyć tak, aby pełna nazwa nie jest wymagane, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a7b35-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
<span data-ttu-id="a7b35-107">Aby uzyskać więcej informacji, zobacz [użycie dyrektywy](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="a7b35-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="a7b35-108">Po drugie deklarowania własne przestrzenie nazw mogą pomóc Ci kontrolować zakres nazwy klasy i metody w dużych projektach programowania.</span><span class="sxs-lookup"><span data-stu-id="a7b35-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="a7b35-109">Użyj [przestrzeni nazw](../../language-reference/keywords/namespace.md) — słowo kluczowe do deklarowania, przestrzeń nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a7b35-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

<span data-ttu-id="a7b35-110">Nazwa przestrzeni nazw musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="a7b35-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="a7b35-111">Przegląd przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a7b35-111">Namespaces Overview</span></span>  

<span data-ttu-id="a7b35-112">Przestrzenie nazw mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a7b35-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="a7b35-113">Ich organizowanie kodu dużych projektów.</span><span class="sxs-lookup"><span data-stu-id="a7b35-113">They organize large code projects.</span></span>  
- <span data-ttu-id="a7b35-114">Są rozdzielane przy użyciu `.` operatora.</span><span class="sxs-lookup"><span data-stu-id="a7b35-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="a7b35-115">`using` Dyrektywy eliminuje konieczność określenia nazwy obszaru nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="a7b35-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="a7b35-116">`global` Przestrzeń nazw jest przestrzeń nazw "root": `global::System` zawsze będzie odnosił się do platformy .NET <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a7b35-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="a7b35-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a7b35-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a7b35-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7b35-118">See Also</span></span>

- [<span data-ttu-id="a7b35-119">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a7b35-119">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="a7b35-120">Instrukcje: Użycie globalnych aliasów Namespace</span><span class="sxs-lookup"><span data-stu-id="a7b35-120">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="a7b35-121">Instrukcje: Użyj mojej Namespace</span><span class="sxs-lookup"><span data-stu-id="a7b35-121">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="a7b35-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a7b35-122">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="a7b35-123">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="a7b35-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="a7b35-124">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="a7b35-124">Namespace Keywords</span></span>](../../language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="a7b35-125">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="a7b35-125">using Directive</span></span>](../../language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="a7b35-126">:: operator</span><span class="sxs-lookup"><span data-stu-id="a7b35-126">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="a7b35-127">. operator</span><span class="sxs-lookup"><span data-stu-id="a7b35-127">. Operator</span></span>](../../language-reference/operators/member-access-operator.md)
