---
title: "extern alias (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e995586c08659853538726a12679770cd1ada37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="cad48-102">extern alias (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cad48-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="cad48-103">Może być konieczne dwie wersje zestawy takich samych nazwach w pełni kwalifikowanego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="cad48-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="cad48-104">Może być konieczne na przykład użyć dwóch lub więcej wersji zestawu w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cad48-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="cad48-105">Za pomocą aliasu zewnętrznego zestawu, przestrzeni nazw z każdego zestawu można ich opakować wewnątrz przestrzeni nazw poziomu głównego o nazwie aliasu, co umożliwia ich do użycia w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="cad48-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cad48-106">[Extern](../../../csharp/language-reference/keywords/extern.md) — słowo kluczowe jest również używany jako modyfikator metody, deklarowanie metody zapisane za pomocą kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="cad48-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="cad48-107">Aby odwołać się do dwóch zestawów pod tą samą nazwą w pełni kwalifikowanego typu aliasu musi być określona w wierszu polecenia, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cad48-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="cad48-108">Spowoduje to utworzenie aliasów zewnętrznych `GridV1` i `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="cad48-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="cad48-109">Aby korzystać z tych aliasy w programie, odwoływać je za pomocą `extern` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="cad48-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="cad48-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="cad48-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="cad48-111">Każdy extern alias deklaracji wprowadzono dodatkowe nazw poziomu głównego, który równoleżnikami (ale nie znajduje się w obrębie) globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cad48-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="cad48-112">W związku z tym typów z każdego zestawu może być określone bez niejednoznaczności przy użyciu ich w pełni kwalifikowanej nazwy, umieszczone w odpowiednich alias przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cad48-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="cad48-113">W poprzednim przykładzie `GridV1::Grid` byłoby formantu siatki z `grid.dll`, i `GridV2::Grid` byłoby formantu siatki z `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="cad48-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cad48-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cad48-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cad48-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cad48-115">See Also</span></span>  
 [<span data-ttu-id="cad48-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="cad48-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cad48-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cad48-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cad48-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cad48-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="cad48-119">Słowa kluczowe Namespace</span><span class="sxs-lookup"><span data-stu-id="cad48-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="cad48-120">:: — Operator</span><span class="sxs-lookup"><span data-stu-id="cad48-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="cad48-121">/ Reference (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="cad48-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
