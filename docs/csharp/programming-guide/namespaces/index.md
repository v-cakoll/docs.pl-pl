---
title: Przestrzenie nazw (Przewodnik programowania w języku C#)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: c4011092a6c605137053b544d4b9f14cce2fdb4c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211999"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="73a70-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="73a70-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="73a70-103">Przestrzenie nazw są intensywnie używane w języku C# programming na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="73a70-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="73a70-104">Po pierwsze .NET Framework używa przestrzeni nazw do organizowania jego wiele klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="73a70-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
[!code-csharp[csProgGuide#22](../inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
<span data-ttu-id="73a70-105">`System` jest to obszar nazw i `Console` jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="73a70-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="73a70-106">`using` — Słowo kluczowe może służyć tak, aby pełna nazwa nie jest wymagane, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="73a70-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
[!code-csharp[csProgGuide#1](../inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
[!code-csharp[csProgGuide#25](../inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
<span data-ttu-id="73a70-107">Aby uzyskać więcej informacji, zobacz [użycie dyrektywy](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="73a70-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="73a70-108">Po drugie deklarowania własne przestrzenie nazw mogą pomóc Ci kontrolować zakres nazwy klasy i metody w dużych projektach programowania.</span><span class="sxs-lookup"><span data-stu-id="73a70-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="73a70-109">Użyj [przestrzeni nazw](../../language-reference/keywords/namespace.md) — słowo kluczowe do deklarowania, przestrzeń nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="73a70-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
[!code-csharp[csProgGuideNamespaces#6](codesnippet/CSharp/index_4.cs)]

<span data-ttu-id="73a70-110">Nazwa przestrzeni nazw musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="73a70-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="73a70-111">Przegląd przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="73a70-111">Namespaces Overview</span></span>  

<span data-ttu-id="73a70-112">Przestrzenie nazw mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="73a70-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="73a70-113">Ich organizowanie kodu dużych projektów.</span><span class="sxs-lookup"><span data-stu-id="73a70-113">They organize large code projects.</span></span>  
- <span data-ttu-id="73a70-114">Są rozdzielane przy użyciu `.` operatora.</span><span class="sxs-lookup"><span data-stu-id="73a70-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="73a70-115">`using directive` Eliminuje konieczność określenia nazwy obszaru nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="73a70-115">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="73a70-116">`global` Przestrzeń nazw jest przestrzeń nazw "root": `global::System` zawsze będzie odnosił się do przestrzeni nazw .NET Framework `System`.</span><span class="sxs-lookup"><span data-stu-id="73a70-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="73a70-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="73a70-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73a70-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73a70-118">See Also</span></span>

- [<span data-ttu-id="73a70-119">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="73a70-119">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="73a70-120">Instrukcje: użycie globalnych aliasów przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="73a70-120">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="73a70-121">Instrukcje: użycie przestrzeni nazw typu My</span><span class="sxs-lookup"><span data-stu-id="73a70-121">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="73a70-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="73a70-122">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="73a70-123">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="73a70-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="73a70-124">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="73a70-124">Namespace Keywords</span></span>](../../language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="73a70-125">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="73a70-125">using Directive</span></span>](../../language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="73a70-126">::, operator</span><span class="sxs-lookup"><span data-stu-id="73a70-126">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="73a70-127">. operator</span><span class="sxs-lookup"><span data-stu-id="73a70-127">. Operator</span></span>](../../language-reference/operators/member-access-operator.md)
>>>>>>> <span data-ttu-id="73a70-128">Dodaj identyfikator reguły nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="73a70-128">add identifier naming rules</span></span>
