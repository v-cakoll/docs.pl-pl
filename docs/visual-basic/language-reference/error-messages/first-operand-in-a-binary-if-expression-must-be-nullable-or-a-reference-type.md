---
title: Typem pierwszego operandu w binarnym wyrażeniu „If” musi być typ zerowalny lub typ referencyjny
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 32ff0adca9d35e6b5439ae06be85414924dac2e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838628"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>Typem pierwszego operandu w binarnym wyrażeniu „If” musi być typ zerowalny lub typ referencyjny
`If` Wyrażenie może przyjmować dwa lub trzy argumenty. Podczas wysyłania tylko dwóch argumentów pierwszy argument musi być typem referencyjnym lub typ dopuszczający wartość null. Jeśli pierwszy argument daje w wyniku nic innego niż `Nothing`, zwracana jest jego wartość. Jeśli pierwszy argument daje w wyniku `Nothing`, drugi argument funkcji jest obliczany i zwracany.  
  
 Na przykład, poniższy kod zawiera dwa `If` wyrażeń: jeden z trzech argumentów i jeden z dwóch argumentów. Wyrażenia obliczyć i zwrócić tę samą wartość.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Następujących wyrażeń przyczyny wystąpienia tego błędu:  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **Identyfikator błędu:** BC33107  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli nie możesz zmienić kod, tak aby pierwszy argument jest typu dopuszczającego wartość null lub typ referencyjny, należy wziąć pod uwagę konwersji argumentowi trzech `If` wyrażenie lub `If...Then...Else` instrukcji.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Zobacz także

- [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
