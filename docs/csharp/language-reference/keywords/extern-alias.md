---
title: alias extern — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713544"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="0125e-102">extern alias (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0125e-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="0125e-103">Może być wymagane odwołanie się do dwóch wersji zestawów, które mają te same nazwy typów w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="0125e-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="0125e-104">Na przykład może być trzeba użyć dwóch lub więcej wersji zestawu w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0125e-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="0125e-105">Za pomocą aliasu zewnętrznego zestawu przestrzenie nazw z każdego zestawu mogą być opakowane wewnątrz obszarów nazw na poziomie głównym nazwanych aliasem, co umożliwia ich użycie w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="0125e-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0125e-106">[Extern](./extern.md) słowo kluczowe jest również używany jako modyfikator metody, deklarując metodę zapisaną w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0125e-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="0125e-107">Aby odwołać się do dwóch zestawów o tych samych w pełni kwalifikowanych nazwach typów, alias musi być określony w wierszu polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0125e-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="0125e-108">Spowoduje to utworzenie aliasów `GridV1` zewnętrznych i `GridV2`.</span><span class="sxs-lookup"><span data-stu-id="0125e-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="0125e-109">Aby używać tych aliasów z poziomu programu, `extern` należy odwoływać się do nich za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="0125e-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="0125e-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0125e-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="0125e-111">Każda deklaracja aliasu extern wprowadza dodatkową obszar nazw na poziomie głównym, który paralele (ale nie znajduje się w) globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0125e-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="0125e-112">W związku z tym typy z każdego zestawu można odwoływać się bez dwuznaczności przy użyciu ich w pełni kwalifikowanej nazwy, zakorzenione w odpowiednim aliasie obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="0125e-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="0125e-113">W poprzednim przykładzie `GridV1::Grid` będzie kontrola siatki `grid.dll` `GridV2::Grid` z , i `grid20.dll`będzie kontrola siatki z .</span><span class="sxs-lookup"><span data-stu-id="0125e-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0125e-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0125e-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0125e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0125e-115">See also</span></span>

- [<span data-ttu-id="0125e-116">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="0125e-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0125e-117">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="0125e-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0125e-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0125e-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="0125e-119">:: Operator</span><span class="sxs-lookup"><span data-stu-id="0125e-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="0125e-120">-reference (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="0125e-120">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
