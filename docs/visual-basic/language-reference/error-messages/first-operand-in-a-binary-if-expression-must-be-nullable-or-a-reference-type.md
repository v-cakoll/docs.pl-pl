---
title: Typem pierwszego operandu w binarnym &#39;Jeśli&#39; wyrażenie musi być typ zerowalny lub typ odwołania
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 76078d315b2c32a2a29aa652a65b463622afec36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590832"
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>Typem pierwszego operandu w binarnym &#39;Jeśli&#39; wyrażenie musi być typ zerowalny lub typ odwołania
`If` Wyrażenie może zająć dwie lub trzy argumenty. Po wysłaniu tylko dwa argumenty pierwszy argument musi być parametrem typu odwołanie lub typ dopuszczający wartość null. Jeśli pierwszy argument daje w wyniku cokolwiek innego niż `Nothing`, zwracana jest jego wartość. Jeśli pierwszy argument ma wartość `Nothing`, drugi argument jest obliczany i zwracany.  
  
 Na przykład poniższy kod zawiera dwa `If` wyrażenia, jeden z trzech argumentów i jeden z dwóch argumentów. Wyrażenia obliczenia i zwracają taką samą wartość.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Następujących wyrażeń być przyczyną tego błędu:  
  
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
  
-   Jeśli nie możesz zmienić kod, aby pierwszy argument jest typu dopuszczającego wartość null lub typ referencyjny, należy wziąć pod uwagę konwertowania na trzech argumentów `If` wyrażenia, lub do `If...Then...Else` instrukcji.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Zobacz też  
 [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)  
 [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
