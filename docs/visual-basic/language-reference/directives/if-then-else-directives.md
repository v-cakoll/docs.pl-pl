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
ms.openlocfilehash: 8930e0e5c6bf9bd713b5601c91e6d1a5cbfd7a51
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568234"
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
 Wymagane dla `#If` i `#ElseIf` instrukcji opcjonalne gdzie indziej. Dowolne wyrażenie, składające się wyłącznie z co najmniej jeden warunkowe stałe kompilatora, literałów i operatory, które daje w wyniku `True` lub `False`.  
  
 `statements`  
 Wymagane dla `#If` instrukcji zablokować, opcjonalny gdzie indziej. Linie programu Visual Basic lub dyrektywy kompilatora, które są kompilowane, jeśli skojarzone wyrażenie daje w wyniku `True`.  
  
 `#End If`  
 Kończy `#If` blok instrukcji.  
  
## <a name="remarks"></a>Uwagi  
 Na powierzchni zachowanie `#If...Then...#Else` dyrektywy wygląda tak samo jak w przypadku `If...Then...Else` instrukcji. Jednak `#If...Then...#Else` dyrektywy ocenić, co jest kompilowany przez kompilator, natomiast `If...Then...Else` instrukcji oceny warunków w czasie wykonywania.  
  
 Kompilacja warunkowa jest zazwyczaj używana do kompilowania tego samego programu dla różnych platform. Służy również uniemożliwić debugowanie kodu pojawianiu się w pliku wykonywalnym. Kod wykluczone w czasie kompilacji warunkowej jest całkowicie pominięte ostateczny plik wykonywalny, dlatego nie ma ona wpływu na rozmiar lub wydajności.  
  
 Niezależnie od tego, w wyniku dowolnej wersji ewaluacyjnej, wszystkie wyrażenia są obliczane przy użyciu `Option Compare Binary`. `Option Compare` Instrukcji nie ma wpływu na wyrażeń w `#If` i `#ElseIf` instrukcji.  
  
> [!NOTE]
>  Żadna z form jednowierszowego `#If`, `#Else`, `#ElseIf`, i `#End If` istnieje dyrektywy. Nie inny kod może znajdować się w tym samym wierszu jako dyrektywy. 

Instrukcje w bloku kompilacji warunkowej należy pełne instrukcje logiczne. Na przykład nie warunkowo skompilować tylko te atrybuty, funkcji, ale warunkowo można zadeklarować funkcji wraz z jego atrybuty:

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
 W tym przykładzie użyto `#If...Then...#Else` konstrukcji, aby określić, czy można skompilować określone instrukcje.  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [#Const, dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>


