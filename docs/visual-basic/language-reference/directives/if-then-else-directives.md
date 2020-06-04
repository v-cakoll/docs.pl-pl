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
# <a name="ifthenelse-directives"></a>#If...Then...#Else — Dyrektywy

Warunkowo kompiluje wybrane bloki kodu Visual Basic.

## <a name="syntax"></a>Składnia

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

## <a name="parts"></a>Części

`expression`  
Wymagane przez `#If` `#ElseIf` instrukcje i, opcjonalnie, w innym miejscu. Każde wyrażenie składające się wyłącznie z jednej lub więcej warunkowych stałych kompilatora, literałów i operatorów, które są obliczane do `True` lub `False` .

`statements`  
Wymagane dla `#If` bloku instrukcji, opcjonalnie w innym miejscu. Visual Basic linie programów lub dyrektywy kompilatora, które są kompilowane w przypadku, gdy skojarzone wyrażenie zwróci wartość `True` .

`#End If`  
Kończy `#If` blok instrukcji.

## <a name="remarks"></a>Uwagi

Na powierzchni zachowanie `#If...Then...#Else` dyrektyw pojawia się tak samo, jak w przypadku `If...Then...Else` instrukcji. Jednakże `#If...Then...#Else` dyrektywy szacują, co jest kompilowane przez kompilator, podczas gdy `If...Then...Else` instrukcje obliczają warunki w czasie wykonywania.

Kompilacja warunkowa jest zwykle używana do kompilowania tego samego programu dla różnych platform. Służy również do zapobiegania wyświetlaniu kodu debugowania w pliku wykonywalnym. Kod wykluczony podczas kompilacji warunkowej jest całkowicie pomijany z końcowego pliku wykonywalnego, więc nie ma wpływu na rozmiar ani wydajność.

Niezależnie od wyniku każdej oceny, wszystkie wyrażenia są oceniane przy użyciu `Option Compare Binary` . `Option Compare`Instrukcja nie ma wpływu na wyrażenia w `#If` `#ElseIf` instrukcjach i.

> [!NOTE]
> Nie istnieje jednowierszowa forma `#If` dyrektywy, `#Else` , `#ElseIf` i `#End If` . Żaden inny kod nie może pojawiać się w tym samym wierszu co którakolwiek z dyrektyw.

Instrukcje w bloku kompilacji warunkowej muszą być kompletnymi instrukcjami logicznymi. Na przykład nie można warunkowo kompilować tylko atrybutów funkcji, ale można warunkowo zadeklarować funkcję wraz z jej atrybutami:

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a>Przykład

Ten przykład używa `#If...Then...#Else` konstrukcji, aby określić, czy kompilować pewne instrukcje.

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>Zobacz też

- [#Const — dyrektywa](const-directive.md)
- [If...Then...Else, instrukcja](../statements/if-then-else-statement.md)
- [Kompilacja warunkowa](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
