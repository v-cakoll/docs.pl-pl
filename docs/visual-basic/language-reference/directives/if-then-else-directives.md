---
title: '#If... Then... #Else — dyrektywy (Visual Basic)'
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
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940760"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else — Dyrektywy
Warunkowo kompiluje wybrane bloki kodu Visual Basic.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="parts"></a>Części  
 `expression`  
 Wymagane przez `#If` instrukcje `#ElseIf` i, opcjonalnie, w innym miejscu. Każde wyrażenie składające się wyłącznie z jednej lub więcej warunkowych stałych kompilatora, literałów i operatorów, które są obliczane `True` do `False`lub.  
  
 `statements`  
 Wymagane dla `#If` bloku instrukcji, opcjonalnie w innym miejscu. Visual Basic linie programów lub dyrektywy kompilatora, które są kompilowane w `True`przypadku, gdy skojarzone wyrażenie zwróci wartość.  
  
 `#End If`  
 Kończy blok instrukcji `#If` .  
  
## <a name="remarks"></a>Uwagi  
 Na powierzchni zachowanie `#If...Then...#Else` dyrektyw pojawia się tak samo, jak `If...Then...Else` w przypadku instrukcji. Jednakże dyrektywy szacują, co jest kompilowane przez kompilator, `If...Then...Else` podczas gdy instrukcje obliczają warunki w czasie wykonywania. `#If...Then...#Else`  
  
 Kompilacja warunkowa jest zwykle używana do kompilowania tego samego programu dla różnych platform. Służy również do zapobiegania wyświetlaniu kodu debugowania w pliku wykonywalnym. Kod wykluczony podczas kompilacji warunkowej jest całkowicie pomijany z końcowego pliku wykonywalnego, więc nie ma wpływu na rozmiar ani wydajność.  
  
 Niezależnie od wyniku każdej oceny, wszystkie wyrażenia są oceniane przy użyciu `Option Compare Binary`. Instrukcja nie ma wpływu na wyrażenia w `#If` instrukcjach i `#ElseIf`. `Option Compare`  
  
> [!NOTE]
> `#If`Nie istnieje jednowierszowa forma dyrektywy `#ElseIf`, `#Else`, i `#End If` . Żaden inny kod nie może pojawiać się w tym samym wierszu co którakolwiek z dyrektyw. 

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
 Ten przykład używa konstrukcji `#If...Then...#Else` , aby określić, czy kompilować pewne instrukcje.  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
