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
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="38b9b-102">Typem pierwszego operandu w binarnym wyrażeniu „If” musi być typ zerowalny lub typ referencyjny</span><span class="sxs-lookup"><span data-stu-id="38b9b-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="38b9b-103">Wyrażenie `If` może mieć dwa lub trzy argumenty.</span><span class="sxs-lookup"><span data-stu-id="38b9b-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="38b9b-104">Podczas wysyłania tylko dwa argumenty, pierwszy argument musi być typu odwołania lub typu wartości nullable.</span><span class="sxs-lookup"><span data-stu-id="38b9b-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="38b9b-105">Jeśli pierwszy argument ma wartość `Nothing`inną niż zwracana jest jego wartość.</span><span class="sxs-lookup"><span data-stu-id="38b9b-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="38b9b-106">Jeśli pierwszy argument ma `Nothing`wartość , drugi argument jest oceniany i zwracany.</span><span class="sxs-lookup"><span data-stu-id="38b9b-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="38b9b-107">Na przykład poniższy kod `If` zawiera dwa wyrażenia, jeden z trzema argumentami i jeden z dwoma argumentami.</span><span class="sxs-lookup"><span data-stu-id="38b9b-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="38b9b-108">Wyrażenia obliczają i zwracają tę samą wartość.</span><span class="sxs-lookup"><span data-stu-id="38b9b-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="38b9b-109">Następujące wyrażenia powodują ten błąd:</span><span class="sxs-lookup"><span data-stu-id="38b9b-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="38b9b-110">**Identyfikator błędu:** Bc33107</span><span class="sxs-lookup"><span data-stu-id="38b9b-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38b9b-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="38b9b-111">To correct this error</span></span>  
  
- <span data-ttu-id="38b9b-112">Jeśli nie można zmienić kodu tak, aby pierwszy argument był typem wartości nullable `If` lub typu `If...Then...Else` odwołania, należy rozważyć konwersję na wyrażenie trzech argumentów lub na instrukcję.</span><span class="sxs-lookup"><span data-stu-id="38b9b-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="38b9b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38b9b-113">See also</span></span>

- [<span data-ttu-id="38b9b-114">If, operator</span><span class="sxs-lookup"><span data-stu-id="38b9b-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="38b9b-115">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="38b9b-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="38b9b-116">Typy o wartości zerowalnej</span><span class="sxs-lookup"><span data-stu-id="38b9b-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
