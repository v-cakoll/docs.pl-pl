---
title: Przestrzenie C# nazw — Przewodnik programowania
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937616"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="7a814-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="7a814-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="7a814-103">Przestrzenie nazw są intensywnie używane w C# programowaniu na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="7a814-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="7a814-104">Najpierw platforma .NET używa przestrzeni nazw do organizowania jej wielu klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7a814-104">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="7a814-105"><xref:System> jest przestrzenią nazw, a <xref:System.Console> jest klasą w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7a814-105"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="7a814-106">Za pomocą słowa kluczowego `using` można użyć, aby pełna nazwa nie była wymagana, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7a814-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="7a814-107">Aby uzyskać więcej informacji, zobacz [dyrektywa using](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="7a814-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="7a814-108">Po drugie, zadeklarowanie własnych przestrzeni nazw może pomóc w kontroli zakresu nazw klas i metod w większych projektach programistycznych.</span><span class="sxs-lookup"><span data-stu-id="7a814-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="7a814-109">Użyj słowa kluczowego [Namespace](../../language-reference/keywords/namespace.md) , aby zadeklarować przestrzeń nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7a814-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="7a814-110">Nazwa przestrzeni nazw musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="7a814-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="7a814-111">Przegląd przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="7a814-111">Namespaces overview</span></span>

<span data-ttu-id="7a814-112">Przestrzenie nazw mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7a814-112">Namespaces have the following properties:</span></span>

- <span data-ttu-id="7a814-113">Organizują one duże projekty kodu.</span><span class="sxs-lookup"><span data-stu-id="7a814-113">They organize large code projects.</span></span>
- <span data-ttu-id="7a814-114">Są one rozdzielane za pomocą operatora `.`.</span><span class="sxs-lookup"><span data-stu-id="7a814-114">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="7a814-115">Dyrektywa `using` eliminuje konieczność określenia nazwy przestrzeni nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="7a814-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="7a814-116">Przestrzeń nazw `global` jest przestrzenią nazw "root": `global::System` zawsze będzie odwoływać się do przestrzeni nazw .NET <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="7a814-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7a814-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7a814-117">C# language specification</span></span>

<span data-ttu-id="7a814-118">Aby uzyskać więcej informacji, zobacz sekcję [przestrzenie nazw](~/_csharplang/spec/namespaces.md) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7a814-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a814-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a814-119">See also</span></span>

- [<span data-ttu-id="7a814-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7a814-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7a814-121">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="7a814-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="7a814-122">Jak używać przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="7a814-122">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="7a814-123">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="7a814-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="7a814-124">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="7a814-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="7a814-125">::, operator</span><span class="sxs-lookup"><span data-stu-id="7a814-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
