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
ms.openlocfilehash: a701ae02adebfa2dda8fb65053dbf2ebbe83328b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924693"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="4c2ad-102">extern alias (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4c2ad-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="4c2ad-103">Może zajść konieczność odwołująca się do dwóch wersji zestawów, które mają te same nazwy typów w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="4c2ad-104">Na przykład może być konieczne użycie co najmniej dwóch wersji zestawu w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="4c2ad-105">Korzystając z zewnętrznego aliasu zestawu, przestrzenie nazw z każdego zestawu mogą być opakowane w przestrzenie nazw poziomu głównego o nazwie alias, co umożliwia ich użycie w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c2ad-106">Słowo kluczowe [extern](./extern.md) jest również używane jako modyfikator metody, deklarując metodę zapisaną w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="4c2ad-107">Aby odwoływać się do dwóch zestawów z tymi samymi w pełni kwalifikowanymi nazwami typu, alias musi być określony w wierszu polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4c2ad-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="4c2ad-108">Spowoduje to utworzenie aliasów `GridV1` zewnętrznych `GridV2`i.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="4c2ad-109">Aby użyć tych aliasów z poziomu programu, odwołując się do `extern` nich za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="4c2ad-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4c2ad-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="4c2ad-111">Każda deklaracja aliasu zewnętrznego wprowadza dodatkową przestrzeń nazw na poziomie głównym, która jest równoległa (ale nie znajduje się w obrębie) globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="4c2ad-112">Z tego względu typy z każdego zestawu mogą być określane bez niejednoznaczności przy użyciu ich w pełni kwalifikowanej nazwy, w której znajduje się odpowiedni alias przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="4c2ad-113">W poprzednim przykładzie `GridV1::Grid` jest to formant siatki z `grid.dll`, `GridV2::Grid` który będzie formantem siatki z `grid20.dll`.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4c2ad-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4c2ad-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4c2ad-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c2ad-115">See also</span></span>

- [<span data-ttu-id="4c2ad-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4c2ad-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4c2ad-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4c2ad-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4c2ad-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4c2ad-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="4c2ad-119">:: operator</span><span class="sxs-lookup"><span data-stu-id="4c2ad-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="4c2ad-120">/Reference (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="4c2ad-120">/reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
