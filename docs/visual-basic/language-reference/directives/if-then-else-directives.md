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
# <a name="ifthenelse-directives"></a>#If...Then...#Else — Dyrektywy
Kompiluje warunkowo wybrane bloki kodu języka Visual Basic.  
  
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
 Wymagany dla `#If` i `#ElseIf` instrukcje opcjonalne w innym miejscu. Dowolne wyrażenie składające się wyłącznie z co najmniej jeden warunkowe stałe kompilatora, literałów i operatory, które daje w wyniku `True` lub `False`.  
  
 `statements`  
 Wymagany dla `#If` instrukcji zablokować, opcjonalny w innym miejscu. Linie programu Visual Basic lub dyrektywy kompilatora, które są kompilowane, jeśli skojarzone wyrażenie daje w wyniku `True`.  
  
 `#End If`  
 Kończy `#If` blok instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Na pierwszy rzut oka zachowanie `#If...Then...#Else` dyrektywy wygląda tak samo jak `If...Then...Else` instrukcje. Jednak `#If...Then...#Else` dyrektywy ocenić, co jest kompilowany przez kompilator, podczas gdy `If...Then...Else` instrukcje oceny warunków w czasie wykonywania.  
  
 Kompilacja warunkowa jest zwykle używana do kompilowania ten sam program dla różnych platform. Również jest używany do chronienia debugowanie kodu z znajdujących się w pliku wykonywalnym. Kod wyłączone podczas kompilacji warunkowej całkowicie został pominięty końcowego pliku wykonywalnego, aby go nie ma wpływu na rozmiar lub wydajności.  
  
 Niezależnie od wyników oceny dowolnego wszystkie wyrażenia są obliczane przy użyciu `Option Compare Binary`. `Option Compare` Instrukcji nie ma wpływu na wyrażenia w `#If` i `#ElseIf` instrukcje.  
  
> [!NOTE]
>  Nie jednowierszowego formę `#If`, `#Else`, `#ElseIf`, i `#End If` istnieje dyrektywy. Żadnego innego kodu może występować w tym samym wierszu co dyrektywy. 

Instrukcje w bloku kompilacja warunkowa musi być kompletne instrukcje logiczne. Na przykład warunkowo nie można skompilować tylko atrybuty funkcji, ale warunkowo mogą zadeklarować funkcji wraz z jego atrybuty:

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
 W tym przykładzie użyto `#If...Then...#Else` konstrukcji, aby określić, czy do skompilowania niektórych instrukcje.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
[#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)  
[If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
[Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


