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
ms.openlocfilehash: 40e93b718241c9819e3c0fd84595e76eb0c86472
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343814"
---
# <a name="ifthenelse-directives"></a><span data-ttu-id="9ef26-102">#If...Then...#Else — Dyrektywy</span><span class="sxs-lookup"><span data-stu-id="9ef26-102">#If...Then...#Else Directives</span></span>

<span data-ttu-id="9ef26-103">Warunkowo kompiluje wybrane bloki kodu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ef26-103">Conditionally compiles selected blocks of Visual Basic code.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ef26-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ef26-104">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="9ef26-105">Części</span><span class="sxs-lookup"><span data-stu-id="9ef26-105">Parts</span></span>

`expression`  
<span data-ttu-id="9ef26-106">Wymagane dla `#If` i `#ElseIf` instrukcji opcjonalnych w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="9ef26-106">Required for `#If` and `#ElseIf` statements, optional elsewhere.</span></span> <span data-ttu-id="9ef26-107">Każde wyrażenie składające się wyłącznie z jednej lub więcej warunkowych stałych kompilatora, literałów i operatorów, które są obliczane w `True` lub `False`.</span><span class="sxs-lookup"><span data-stu-id="9ef26-107">Any expression, consisting exclusively of one or more conditional compiler constants, literals, and operators, that evaluates to `True` or `False`.</span></span>

`statements`  
<span data-ttu-id="9ef26-108">Wymagane dla bloku instrukcji `#If`, opcjonalnie w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="9ef26-108">Required for `#If` statement block, optional elsewhere.</span></span> <span data-ttu-id="9ef26-109">Visual Basic linie programów lub dyrektywy kompilatora, które są kompilowane, jeśli skojarzone wyrażenie szacuje się na `True`.</span><span class="sxs-lookup"><span data-stu-id="9ef26-109">Visual Basic program lines or compiler directives that are compiled if the associated expression evaluates to `True`.</span></span>

`#End If`  
<span data-ttu-id="9ef26-110">Kończy blok instrukcji `#If`.</span><span class="sxs-lookup"><span data-stu-id="9ef26-110">Terminates the `#If` statement block.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ef26-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ef26-111">Remarks</span></span>

<span data-ttu-id="9ef26-112">Na powierzchni zachowanie dyrektyw `#If...Then...#Else` pojawia się tak samo, jak w przypadku instrukcji `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="9ef26-112">On the surface, the behavior of the `#If...Then...#Else` directives appears the same as that of the `If...Then...Else` statements.</span></span> <span data-ttu-id="9ef26-113">Jednakże `#If...Then...#Else` dyrektywy szacują, co jest kompilowane przez kompilator, podczas gdy instrukcje `If...Then...Else` obliczają warunki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9ef26-113">However, the `#If...Then...#Else` directives evaluate what is compiled by the compiler, whereas the `If...Then...Else` statements evaluate conditions at run time.</span></span>

<span data-ttu-id="9ef26-114">Kompilacja warunkowa jest zwykle używana do kompilowania tego samego programu dla różnych platform.</span><span class="sxs-lookup"><span data-stu-id="9ef26-114">Conditional compilation is typically used to compile the same program for different platforms.</span></span> <span data-ttu-id="9ef26-115">Służy również do zapobiegania wyświetlaniu kodu debugowania w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="9ef26-115">It is also used to prevent debugging code from appearing in an executable file.</span></span> <span data-ttu-id="9ef26-116">Kod wykluczony podczas kompilacji warunkowej jest całkowicie pomijany z końcowego pliku wykonywalnego, więc nie ma wpływu na rozmiar ani wydajność.</span><span class="sxs-lookup"><span data-stu-id="9ef26-116">Code excluded during conditional compilation is completely omitted from the final executable file, so it has no effect on size or performance.</span></span>

<span data-ttu-id="9ef26-117">Bez względu na wynik każdej oceny wszystkie wyrażenia są oceniane przy użyciu `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="9ef26-117">Regardless of the outcome of any evaluation, all expressions are evaluated using `Option Compare Binary`.</span></span> <span data-ttu-id="9ef26-118">Instrukcja `Option Compare` nie ma wpływu na wyrażenia w instrukcjach `#If` i `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="9ef26-118">The `Option Compare` statement does not affect expressions in `#If` and `#ElseIf` statements.</span></span>

> [!NOTE]
> <span data-ttu-id="9ef26-119">Nie istnieje jednowierszowa forma `#If`, `#Else`, `#ElseIf`i `#End If`.</span><span class="sxs-lookup"><span data-stu-id="9ef26-119">No single-line form of the `#If`, `#Else`, `#ElseIf`, and `#End If` directives exists.</span></span> <span data-ttu-id="9ef26-120">Żaden inny kod nie może pojawiać się w tym samym wierszu co którakolwiek z dyrektyw.</span><span class="sxs-lookup"><span data-stu-id="9ef26-120">No other code can appear on the same line as any of the directives.</span></span>

<span data-ttu-id="9ef26-121">Instrukcje w bloku kompilacji warunkowej muszą być kompletnymi instrukcjami logicznymi.</span><span class="sxs-lookup"><span data-stu-id="9ef26-121">The statements within a conditional compilation block must be complete logical statements.</span></span> <span data-ttu-id="9ef26-122">Na przykład nie można warunkowo kompilować tylko atrybutów funkcji, ale można warunkowo zadeklarować funkcję wraz z jej atrybutami:</span><span class="sxs-lookup"><span data-stu-id="9ef26-122">For example, you cannot conditionally compile only the attributes of a function, but you can conditionally declare the function along with its attributes:</span></span>

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a><span data-ttu-id="9ef26-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ef26-123">Example</span></span>

<span data-ttu-id="9ef26-124">W tym przykładzie używa konstrukcji `#If...Then...#Else`, aby określić, czy kompilować pewne instrukcje.</span><span class="sxs-lookup"><span data-stu-id="9ef26-124">This example uses the `#If...Then...#Else` construct to determine whether to compile certain statements.</span></span>

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9ef26-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ef26-125">See also</span></span>

- [<span data-ttu-id="9ef26-126">#Const, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="9ef26-126">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="9ef26-127">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9ef26-127">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="9ef26-128">Kompilacja warunkowa</span><span class="sxs-lookup"><span data-stu-id="9ef26-128">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
