---
title: alias zewnętrzny — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: cfb662203216aa6ca208ceec20d55164c65163dc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626646"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="cba9c-102">extern alias (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cba9c-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="cba9c-103">Może zajść konieczność odwołująca się do dwóch wersji zestawów, które mają te same nazwy typów w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="cba9c-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="cba9c-104">Na przykład może być konieczne użycie co najmniej dwóch wersji zestawu w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cba9c-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="cba9c-105">Korzystając z zewnętrznego aliasu zestawu, przestrzenie nazw z każdego zestawu mogą być opakowane w przestrzenie nazw poziomu głównego o nazwie alias, co umożliwia ich użycie w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="cba9c-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cba9c-106">Słowo kluczowe [extern](../../../csharp/language-reference/keywords/extern.md) jest również używane jako modyfikator metody, deklarując metodę zapisaną w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="cba9c-106">The [extern](../../../csharp/language-reference/keywords/extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="cba9c-107">Aby odwoływać się do dwóch zestawów z tymi samymi w pełni kwalifikowanymi nazwami typu, alias musi być określony w wierszu polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cba9c-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="cba9c-108">Spowoduje to utworzenie aliasów `GridV1` zewnętrznych `GridV2`i.</span><span class="sxs-lookup"><span data-stu-id="cba9c-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="cba9c-109">Aby użyć tych aliasów z poziomu programu, odwołując się do `extern` nich za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cba9c-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="cba9c-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="cba9c-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="cba9c-111">Każda deklaracja aliasu zewnętrznego wprowadza dodatkową przestrzeń nazw na poziomie głównym, która jest równoległa (ale nie znajduje się w obrębie) globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cba9c-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="cba9c-112">Z tego względu typy z każdego zestawu mogą być określane bez niejednoznaczności przy użyciu ich w pełni kwalifikowanej nazwy, w której znajduje się odpowiedni alias przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cba9c-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="cba9c-113">W poprzednim przykładzie `GridV1::Grid` jest to formant siatki z `grid.dll`, `GridV2::Grid` który będzie formantem siatki z `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="cba9c-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cba9c-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cba9c-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cba9c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cba9c-115">See also</span></span>

- [<span data-ttu-id="cba9c-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cba9c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cba9c-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cba9c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cba9c-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cba9c-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="cba9c-119">:: operator</span><span class="sxs-lookup"><span data-stu-id="cba9c-119">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="cba9c-120">/Reference (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="cba9c-120">/reference (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
