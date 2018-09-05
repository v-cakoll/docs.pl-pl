---
title: '#IF... Then... #Else — dyrektywy (Visual Basic)'
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
ms.openlocfilehash: 05aac9109e49897d1c4dbbad60d807eb3e47798d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555134"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="56d16-102">#If...Then...#Else — Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="56d16-102">#If...Then...#Else Directives</span></span>
<span data-ttu-id="56d16-103">Kompiluje warunkowo wybrane bloki kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="56d16-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56d16-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="56d16-105">Części</span><span class="sxs-lookup"><span data-stu-id="56d16-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="56d16-106">Wymagane dla `#If` i `#ElseIf` instrukcji opcjonalne gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="56d16-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="56d16-107">Dowolne wyrażenie, składające się wyłącznie z co najmniej jeden warunkowe stałe kompilatora, literałów i operatory, które daje w wyniku `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="56d16-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>  
  
 `statements`  
 <span data-ttu-id="56d16-108">Wymagane dla `#If` instrukcji zablokować, opcjonalny gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="56d16-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="56d16-109">Linie programu Visual Basic lub dyrektywy kompilatora, które są kompilowane, jeśli skojarzone wyrażenie daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="56d16-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>  
  
 `#End If`  
 <span data-ttu-id="56d16-110">Kończy `#If` blok instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56d16-110">Terminates the `#If` statement block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56d16-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56d16-111">Remarks</span></span>  
 <span data-ttu-id="56d16-112">Na powierzchni zachowanie `#If...Then...#Else` dyrektywy wygląda tak samo jak w przypadku `If...Then...Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56d16-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="56d16-113">Jednak `#If...Then...#Else` dyrektywy ocenić, co jest kompilowany przez kompilator, natomiast `If...Then...Else` instrukcji oceny warunków w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="56d16-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>  
  
 <span data-ttu-id="56d16-114">Kompilacja warunkowa jest zazwyczaj używana do kompilowania tego samego programu dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="56d16-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="56d16-115">Służy również uniemożliwić debugowanie kodu pojawianiu się w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="56d16-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="56d16-116">Kod wykluczone w czasie kompilacji warunkowej jest całkowicie pominięte ostateczny plik wykonywalny, dlatego nie ma ona wpływu na rozmiar lub wydajności.</span><span class="sxs-lookup"><span data-stu-id="56d16-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>  
  
 <span data-ttu-id="56d16-117">Niezależnie od tego, w wyniku dowolnej wersji ewaluacyjnej, wszystkie wyrażenia są obliczane przy użyciu `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="56d16-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="56d16-118">`Option Compare` Instrukcji nie ma wpływu na wyrażeń w `#If` i `#ElseIf` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56d16-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56d16-119">Żadna z form jednowierszowego `#If`, `#Else`, `#ElseIf`, i `#End If` istnieje dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="56d16-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="56d16-120">Nie inny kod może znajdować się w tym samym wierszu jako dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="56d16-120">No other code can appear on the same line as any of the directives.</span></span> 

<span data-ttu-id="56d16-121">Instrukcje w bloku kompilacji warunkowej należy pełne instrukcje logiczne.</span><span class="sxs-lookup"><span data-stu-id="56d16-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="56d16-122">Na przykład nie warunkowo skompilować tylko te atrybuty, funkcji, ale warunkowo można zadeklarować funkcji wraz z jego atrybuty:</span><span class="sxs-lookup"><span data-stu-id="56d16-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a><span data-ttu-id="56d16-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="56d16-123">Example</span></span>
 <span data-ttu-id="56d16-124">W tym przykładzie użyto `#If...Then...#Else` konstrukcji, aby określić, czy można skompilować określone instrukcje.</span><span class="sxs-lookup"><span data-stu-id="56d16-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="56d16-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56d16-125">See Also</span></span>  
[<span data-ttu-id="56d16-126">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="56d16-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
[<span data-ttu-id="56d16-127">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="56d16-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
<span data-ttu-id="56d16-128">[Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="56d16-128">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


