---
title: extern alias (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 66210bc1a84e2c3239dcac72cdc194b14dcccf30
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999992"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="76fe8-102">extern alias (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="76fe8-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="76fe8-103">Może być konieczne dwie wersje zestawów, które mają takie same nazwy w pełni kwalifikowanego typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="76fe8-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="76fe8-104">Na przykład trzeba użyć dwóch lub więcej wersji zestawu w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="76fe8-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="76fe8-105">Za pomocą alias zestawu zewnętrznego, przestrzenie nazw z każdego zestawu, może zostać zawinięty wewnątrz przestrzeni nazw poziomie głównym o nazwie określonej przez alias, który umożliwia im ma być używany w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="76fe8-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76fe8-106">[Extern](../../../csharp/language-reference/keywords/extern.md) — słowo kluczowe jest również używane jako modyfikator metody, deklarowania metody zapisaną w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="76fe8-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="76fe8-107">Aby odwołać się dwa zestawy za pomocą tych samych nazw w pełni kwalifikowanego typu, alias musi być określona w wierszu polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="76fe8-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="76fe8-108">Spowoduje to utworzenie aliasów zewnętrznych `GridV1` i `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="76fe8-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="76fe8-109">Aby użyć te aliasy z poziomu używanego programu, odwoływać się do nich za pomocą `extern` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="76fe8-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="76fe8-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="76fe8-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="76fe8-111">Każdy extern Deklaracja aliasu wprowadza dodatkowe obszar nazw w katalogu głównego, który równoleżnikami (ale nie leży w obrębie) globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="76fe8-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="76fe8-112">Ten sposób typów z każdego zestawu może odnosić się bez niejednoznaczności przy użyciu w pełni kwalifikowaną nazwę, osadzonego w odpowiednich alias przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="76fe8-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="76fe8-113">W poprzednim przykładzie `GridV1::Grid` będzie formant siatki z `grid.dll`, i `GridV2::Grid` będzie formant siatki z `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="76fe8-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="76fe8-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="76fe8-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="76fe8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76fe8-115">See Also</span></span>

- [<span data-ttu-id="76fe8-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="76fe8-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="76fe8-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="76fe8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="76fe8-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="76fe8-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="76fe8-119">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="76fe8-119">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
- [<span data-ttu-id="76fe8-120">::, operator</span><span class="sxs-lookup"><span data-stu-id="76fe8-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="76fe8-121">/ Reference (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="76fe8-121">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
