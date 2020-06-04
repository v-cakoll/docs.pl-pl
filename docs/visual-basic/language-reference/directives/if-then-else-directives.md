---
title: '#f...Then...#Else, dyrektywy'
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
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410013"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="4fd0d-102">#If...Then...#Else — Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="4fd0d-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="4fd0d-103">Warunkowo kompiluje wybrane bloki kodu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="4fd0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fd0d-104">Syntax</span></span>

```vb
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

## <a name="parts"></a><span data-ttu-id="4fd0d-105">Części</span><span class="sxs-lookup"><span data-stu-id="4fd0d-105">Parts</span></span>

`expression`  
<span data-ttu-id="4fd0d-106">Wymagane przez `#If` `#ElseIf` instrukcje i, opcjonalnie, w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="4fd0d-107">Każde wyrażenie składające się wyłącznie z jednej lub więcej warunkowych stałych kompilatora, literałów i operatorów, które są obliczane do `True` lub `False` .</span><span class="sxs-lookup"><span data-stu-id="4fd0d-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="4fd0d-108">Wymagane dla `#If` bloku instrukcji, opcjonalnie w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="4fd0d-109">Visual Basic linie programów lub dyrektywy kompilatora, które są kompilowane w przypadku, gdy skojarzone wyrażenie zwróci wartość `True` .</span><span class="sxs-lookup"><span data-stu-id="4fd0d-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="4fd0d-110">Kończy `#If` blok instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fd0d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4fd0d-111">Remarks</span></span>

<span data-ttu-id="4fd0d-112">Na powierzchni zachowanie `#If...Then...#Else` dyrektyw pojawia się tak samo, jak w przypadku `If...Then...Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="4fd0d-113">Jednakże `#If...Then...#Else` dyrektywy szacują, co jest kompilowane przez kompilator, podczas gdy `If...Then...Else` instrukcje obliczają warunki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="4fd0d-114">Kompilacja warunkowa jest zwykle używana do kompilowania tego samego programu dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="4fd0d-115">Służy również do zapobiegania wyświetlaniu kodu debugowania w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="4fd0d-116">Kod wykluczony podczas kompilacji warunkowej jest całkowicie pomijany z końcowego pliku wykonywalnego, więc nie ma wpływu na rozmiar ani wydajność.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="4fd0d-117">Niezależnie od wyniku każdej oceny, wszystkie wyrażenia są oceniane przy użyciu `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="4fd0d-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="4fd0d-118">`Option Compare`Instrukcja nie ma wpływu na wyrażenia w `#If` `#ElseIf` instrukcjach i.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="4fd0d-119">Nie istnieje jednowierszowa forma `#If` dyrektywy, `#Else` , `#ElseIf` i `#End If` .</span><span class="sxs-lookup"><span data-stu-id="4fd0d-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="4fd0d-120">Żaden inny kod nie może pojawiać się w tym samym wierszu co którakolwiek z dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="4fd0d-121">Instrukcje w bloku kompilacji warunkowej muszą być kompletnymi instrukcjami logicznymi.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="4fd0d-122">Na przykład nie można warunkowo kompilować tylko atrybutów funkcji, ale można warunkowo zadeklarować funkcję wraz z jej atrybutami:</span><span class="sxs-lookup"><span data-stu-id="4fd0d-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="4fd0d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="4fd0d-123">Example</span></span>

<span data-ttu-id="4fd0d-124">Ten przykład używa `#If...Then...#Else` konstrukcji, aby określić, czy kompilować pewne instrukcje.</span><span class="sxs-lookup"><span data-stu-id="4fd0d-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4fd0d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4fd0d-125">See also</span></span>

- [<span data-ttu-id="4fd0d-126">#Const — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="4fd0d-126">#Const Directive</span></span>](const-directive.md)
- [<span data-ttu-id="4fd0d-127">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4fd0d-127">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="4fd0d-128">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="4fd0d-128">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
