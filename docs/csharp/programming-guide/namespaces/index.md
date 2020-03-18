---
title: Przestrzenie nazw — przewodnik programowania C#
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 21452e259596c9ab10b3d653ec1d8fb90fad131d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937616"
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="63aaf-102">Przestrzenie nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="63aaf-102">Namespaces (C# Programming Guide)</span></span>

<span data-ttu-id="63aaf-103">Przestrzenie nazw są intensywnie używane w programowaniu języka C# na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="63aaf-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="63aaf-104">Po pierwsze. .NET używa przestrzeni nazw do organizowania wielu klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="63aaf-104">First, .NET uses namespaces to organize its many classes, as follows:</span></span>  

[!code-csharp[csProgGuide#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#22)]

<span data-ttu-id="63aaf-105"><xref:System>jest obszarem <xref:System.Console> nazw i jest klasą w tym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="63aaf-105"><xref:System> is a namespace and <xref:System.Console> is a class in that namespace.</span></span> <span data-ttu-id="63aaf-106">Słowa `using` kluczowego można użyć, aby pełna nazwa nie była wymagana, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="63aaf-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#25)]

<span data-ttu-id="63aaf-107">Aby uzyskać więcej informacji, zobacz [dyrektywę stosującą](../../language-reference/keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="63aaf-107">For more information, see the [using Directive](../../language-reference/keywords/using-directive.md).</span></span>

<span data-ttu-id="63aaf-108">Po drugie deklarowanie własnych przestrzeni nazw może pomóc kontrolować zakres nazw klas i metod w większych projektach programowania.</span><span class="sxs-lookup"><span data-stu-id="63aaf-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="63aaf-109">Użyj słowa kluczowego [obszaru nazw,](../../language-reference/keywords/namespace.md) aby zadeklarować obszar nazw, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="63aaf-109">Use the [namespace](../../language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>

[!code-csharp[csProgGuideNamespaces#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#6)]

<span data-ttu-id="63aaf-110">Nazwa obszaru nazw musi być prawidłową [nazwą identyfikatora C#.](../inside-a-program/identifier-names.md)</span><span class="sxs-lookup"><span data-stu-id="63aaf-110">The name of the namespace must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span>

## <a name="namespaces-overview"></a><span data-ttu-id="63aaf-111">Omówienie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="63aaf-111">Namespaces overview</span></span>

<span data-ttu-id="63aaf-112">Przestrzenie nazw mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="63aaf-112">Namespaces have the following properties:</span></span>

- <span data-ttu-id="63aaf-113">Organizują duże projekty kodu.</span><span class="sxs-lookup"><span data-stu-id="63aaf-113">They organize large code projects.</span></span>
- <span data-ttu-id="63aaf-114">Są one rozdzielane `.` za pomocą operatora.</span><span class="sxs-lookup"><span data-stu-id="63aaf-114">They are delimited by using the `.` operator.</span></span>
- <span data-ttu-id="63aaf-115">Dyrektywa `using` zażegna wymóg, aby określić nazwę obszaru nazw dla każdej klasy.</span><span class="sxs-lookup"><span data-stu-id="63aaf-115">The `using` directive obviates the requirement to specify the name of the namespace for every class.</span></span>
- <span data-ttu-id="63aaf-116">Obszar `global` nazw jest "root" obszar `global::System` nazw: zawsze odnoszą <xref:System> się do obszaru nazw .NET.</span><span class="sxs-lookup"><span data-stu-id="63aaf-116">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET <xref:System> namespace.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="63aaf-117">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="63aaf-117">C# language specification</span></span>

<span data-ttu-id="63aaf-118">Aby uzyskać więcej informacji, zobacz [sekcję Przestrzenie nazw](~/_csharplang/spec/namespaces.md) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="63aaf-118">For more information, see the [Namespaces](~/_csharplang/spec/namespaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63aaf-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63aaf-119">See also</span></span>

- [<span data-ttu-id="63aaf-120">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="63aaf-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="63aaf-121">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="63aaf-121">Using Namespaces</span></span>](using-namespaces.md)
- [<span data-ttu-id="63aaf-122">Korzystanie z przestrzeni nazw typu My</span><span class="sxs-lookup"><span data-stu-id="63aaf-122">How to use the My namespace</span></span>](how-to-use-the-my-namespace.md)
- [<span data-ttu-id="63aaf-123">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="63aaf-123">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="63aaf-124">using, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="63aaf-124">using Directive</span></span>](../../language-reference/keywords/using-directive.md)
- [<span data-ttu-id="63aaf-125">:: Operator</span><span class="sxs-lookup"><span data-stu-id="63aaf-125">:: Operator</span></span>](../../language-reference/operators/namespace-alias-qualifier.md)
