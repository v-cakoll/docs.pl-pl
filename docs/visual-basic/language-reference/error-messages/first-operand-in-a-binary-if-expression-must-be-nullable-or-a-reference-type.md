---
title: Typem pierwszego operandu w binarnym wyrażeniu „If” musi być typ zerowalny lub typ referencyjny
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: a73a66313e7ca540711838c4d147d6bd163ec8d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625568"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="f5807-102">Typem pierwszego operandu w binarnym wyrażeniu „If” musi być typ zerowalny lub typ referencyjny</span><span class="sxs-lookup"><span data-stu-id="f5807-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="f5807-103">`If` Wyrażenie może przyjmować dwa lub trzy argumenty.</span><span class="sxs-lookup"><span data-stu-id="f5807-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="f5807-104">Podczas wysyłania tylko dwóch argumentów pierwszy argument musi być typem referencyjnym lub typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="f5807-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="f5807-105">Jeśli pierwszy argument daje w wyniku nic innego niż `Nothing`, zwracana jest jego wartość.</span><span class="sxs-lookup"><span data-stu-id="f5807-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="f5807-106">Jeśli pierwszy argument daje w wyniku `Nothing`, drugi argument funkcji jest obliczany i zwracany.</span><span class="sxs-lookup"><span data-stu-id="f5807-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="f5807-107">Na przykład, poniższy kod zawiera dwa `If` wyrażeń: jeden z trzech argumentów i jeden z dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="f5807-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="f5807-108">Wyrażenia obliczyć i zwrócić tę samą wartość.</span><span class="sxs-lookup"><span data-stu-id="f5807-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="f5807-109">Następujących wyrażeń przyczyny wystąpienia tego błędu:</span><span class="sxs-lookup"><span data-stu-id="f5807-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="f5807-110">**Identyfikator błędu:** BC33107</span><span class="sxs-lookup"><span data-stu-id="f5807-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5807-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f5807-111">To correct this error</span></span>  
  
- <span data-ttu-id="f5807-112">Jeśli nie możesz zmienić kod, tak aby pierwszy argument jest typu dopuszczającego wartość null lub typ referencyjny, należy wziąć pod uwagę konwersji argumentowi trzech `If` wyrażenie lub `If...Then...Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f5807-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5807-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5807-113">See also</span></span>

- [<span data-ttu-id="f5807-114">If, operator</span><span class="sxs-lookup"><span data-stu-id="f5807-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="f5807-115">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="f5807-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="f5807-116">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="f5807-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
