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
ms.openlocfilehash: c5357dca24b03ddd03779866019baf14175be992
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698547"
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
 Wymagane dla `#If` i `#ElseIf` instrukcji opcjonalnych w innym miejscu. Każde wyrażenie, składające się wyłącznie z jednej lub więcej warunkowych stałych kompilatora, literałów i operatorów, których wynikiem jest `True` lub `False`.  
  
 `statements`  
 Wymagane dla bloku instrukcji `#If`, opcjonalnie w innym miejscu. Visual Basic linie programów lub dyrektywy kompilatora, które są kompilowane, jeśli skojarzone wyrażenie ma wartość `True`.  
  
 `#End If`  
 Kończy blok instrukcji `#If`.  
  
## <a name="remarks"></a>Uwagi  
 Na powierzchni zachowanie dyrektyw `#If...Then...#Else` jest takie samo jak w przypadku instrukcji `If...Then...Else`. Jednakże dyrektywy `#If...Then...#Else` szacują, co jest kompilowane przez kompilator, natomiast instrukcje `If...Then...Else` obliczają warunki w czasie wykonywania.  
  
 Kompilacja warunkowa jest zwykle używana do kompilowania tego samego programu dla różnych platform. Służy również do zapobiegania wyświetlaniu kodu debugowania w pliku wykonywalnym. Kod wykluczony podczas kompilacji warunkowej jest całkowicie pomijany z końcowego pliku wykonywalnego, więc nie ma wpływu na rozmiar ani wydajność.  
  
 Bez względu na wynik każdej oceny wszystkie wyrażenia są oceniane przy użyciu `Option Compare Binary`. Instrukcja `Option Compare` nie ma wpływu na wyrażenia w instrukcjach `#If` i `#ElseIf`.  
  
> [!NOTE]
> Nie istnieje jednowierszowa forma `#If`, `#Else`, `#ElseIf` i `#End If` dyrektyw. Żaden inny kod nie może pojawiać się w tym samym wierszu co którakolwiek z dyrektyw. 

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
 W tym przykładzie używa konstrukcji `#If...Then...#Else`, aby określić, czy kompilować pewne instrukcje.  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
