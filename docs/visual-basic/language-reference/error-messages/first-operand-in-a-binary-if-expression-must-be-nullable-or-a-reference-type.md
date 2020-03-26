---
title: Typem pierwszego operandu w binarnym wyrażeniu „If” musi być typ zerowalny lub typ referencyjny
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249529"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>Typem pierwszego operandu w binarnym wyrażeniu „If” musi być typ zerowalny lub typ referencyjny
Wyrażenie `If` może mieć dwa lub trzy argumenty. Podczas wysyłania tylko dwa argumenty, pierwszy argument musi być typu odwołania lub typu wartości nullable. Jeśli pierwszy argument ma wartość `Nothing`inną niż zwracana jest jego wartość. Jeśli pierwszy argument ma `Nothing`wartość , drugi argument jest oceniany i zwracany.  
  
 Na przykład poniższy kod `If` zawiera dwa wyrażenia, jeden z trzema argumentami i jeden z dwoma argumentami. Wyrażenia obliczają i zwracają tę samą wartość.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Następujące wyrażenia powodują ten błąd:  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **Identyfikator błędu:** Bc33107  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli nie można zmienić kodu tak, aby pierwszy argument był typem wartości nullable `If` lub typu `If...Then...Else` odwołania, należy rozważyć konwersję na wyrażenie trzech argumentów lub na instrukcję.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Zobacz też

- [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)
- [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Typy o wartości zerowalnej](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
