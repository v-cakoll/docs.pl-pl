---
title: Przestrzenie C# nazw — Przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 79b7057b1f6a9cdba2215124160b28efb9a1c0be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629523"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="5085f-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5085f-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="5085f-103">Przestrzenie nazw są intensywnie używane w C# programowaniu na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="5085f-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="5085f-104">Najpierw .NET Framework używa przestrzeni nazw do organizowania jej wielu klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5085f-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]  
  
<span data-ttu-id="5085f-105">`System`jest przestrzenią nazw `Console` i jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5085f-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="5085f-106">Można `using` użyć słowa kluczowego, tak aby pełna nazwa nie była wymagana, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5085f-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]  
  
<span data-ttu-id="5085f-107">Aby uzyskać więcej informacji, zobacz [dyrektywa using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="5085f-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>  
  
<span data-ttu-id="5085f-108">Po drugie, zadeklarowanie własnych przestrzeni nazw może pomóc w kontroli zakresu nazw klas i metod w większych projektach programistycznych.</span><span class="sxs-lookup"><span data-stu-id="5085f-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="5085f-109">Użyj słowa kluczowego [Namespace](../../language-reference/keywords/namespace.md) , aby zadeklarować przestrzeń nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5085f-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="5085f-110">Nazwa przestrzeni nazw musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="5085f-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="5085f-111">Przegląd przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="5085f-111">Namespaces Overview</span></span>  

<span data-ttu-id="5085f-112">Przestrzenie nazw mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5085f-112">Namespaces have the following properties:</span></span>  
  
- <span data-ttu-id="5085f-113">Organizują one duże projekty kodu.</span><span class="sxs-lookup"><span data-stu-id="5085f-113">They organize large code projects.</span></span>  
- <span data-ttu-id="5085f-114">Są one rozdzielane za pomocą `.` operatora.</span><span class="sxs-lookup"><span data-stu-id="5085f-114">They are delimited by using the `.` operator.</span></span>  
- <span data-ttu-id="5085f-115">`using` Dyrektywa eliminuje konieczność określenia nazwy przestrzeni nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="5085f-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>  
- <span data-ttu-id="5085f-116">Przestrzeń nazw jest przestrzenią nazw "root" `global::System` : zawsze odwołuje się do przestrzeni nazw platformy .NET <xref:System>. `global`</span><span class="sxs-lookup"><span data-stu-id="5085f-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="5085f-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5085f-117">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5085f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5085f-118">See also</span></span>

- [<span data-ttu-id="5085f-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5085f-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5085f-120">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="5085f-120">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="5085f-121">Instrukcje: Użyj globalnego aliasu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="5085f-121">How to: Use the Global Namespace Alias</span></span>](how-to-use-the-global-namespace-alias.md)
- [<span data-ttu-id="5085f-122">Instrukcje: Korzystanie z przestrzeni nazw my</span><span class="sxs-lookup"><span data-stu-id="5085f-122">How to: Use the My Namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="5085f-123">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="5085f-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="5085f-124">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="5085f-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="5085f-125">:: operator</span><span class="sxs-lookup"><span data-stu-id="5085f-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
