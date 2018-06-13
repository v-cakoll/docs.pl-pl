---
title: '#IF... Then... #Else — dyrektywy'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591084"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="ceace-102">#If...Then...#Else — Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="ceace-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="ceace-103">Kompiluje warunkowo wybrane bloki kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ceace-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceace-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ceace-104">Syntax</span></span>  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a><span data-ttu-id="ceace-105">Części</span><span class="sxs-lookup"><span data-stu-id="ceace-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="ceace-106">Wymagany dla `#If` i `#ElseIf` instrukcje opcjonalne w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="ceace-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="ceace-107">Dowolne wyrażenie składające się wyłącznie z co najmniej jeden warunkowe stałe kompilatora, literałów i operatory, które daje w wyniku `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="ceace-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="ceace-108">Wymagany dla `#If` instrukcji zablokować, opcjonalny w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="ceace-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="ceace-109">Linie programu Visual Basic lub dyrektywy kompilatora, które są kompilowane, jeśli skojarzone wyrażenie daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="ceace-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="ceace-110">Kończy `#If` blok instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ceace-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceace-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ceace-111">Remarks</span></span>  
 <span data-ttu-id="ceace-112">Na pierwszy rzut oka zachowanie `#If...Then...#Else` dyrektywy wygląda tak samo jak `If...Then...Else` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="ceace-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="ceace-113">Jednak `#If...Then...#Else` dyrektywy ocenić, co jest kompilowany przez kompilator, podczas gdy `If...Then...Else` instrukcje oceny warunków w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ceace-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="ceace-114">Kompilacja warunkowa jest zwykle używana do kompilowania ten sam program dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="ceace-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="ceace-115">Również jest używany do chronienia debugowanie kodu z znajdujących się w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="ceace-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="ceace-116">Kod wyłączone podczas kompilacji warunkowej całkowicie został pominięty końcowego pliku wykonywalnego, aby go nie ma wpływu na rozmiar lub wydajności.</span><span class="sxs-lookup"><span data-stu-id="ceace-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="ceace-117">Niezależnie od wyników oceny dowolnego wszystkie wyrażenia są obliczane przy użyciu `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="ceace-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="ceace-118">`Option Compare` Instrukcji nie ma wpływu na wyrażenia w `#If` i `#ElseIf` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="ceace-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceace-119">Nie jednowierszowego formę `#If`, `#Else`, `#ElseIf`, i `#End If` istnieje dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="ceace-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="ceace-120">Żadnego innego kodu może występować w tym samym wierszu co dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="ceace-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="ceace-121">Instrukcje w bloku kompilacja warunkowa musi być kompletne instrukcje logiczne.</span><span class="sxs-lookup"><span data-stu-id="ceace-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="ceace-122">Na przykład warunkowo nie można skompilować tylko atrybuty funkcji, ale warunkowo mogą zadeklarować funkcji wraz z jego atrybuty:</span><span class="sxs-lookup"><span data-stu-id="ceace-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="ceace-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="ceace-123">Example</span></span>
 <span data-ttu-id="ceace-124">W tym przykładzie użyto `#If...Then...#Else` konstrukcji, aby określić, czy do skompilowania niektórych instrukcje.</span><span class="sxs-lookup"><span data-stu-id="ceace-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ceace-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ceace-125">See Also</span></span>  
[<span data-ttu-id="ceace-126">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="ceace-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
[<span data-ttu-id="ceace-127">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ceace-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
<span data-ttu-id="ceace-128">[Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="ceace-128">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


