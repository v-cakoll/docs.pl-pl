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
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="dfb49-102">Typem pierwszego operandu w binarnym &#39;Jeśli&#39; wyrażenie musi być typ zerowalny lub typ odwołania</span><span class="sxs-lookup"><span data-stu-id="dfb49-102">First operand in a binary &#39;If&#39; expression must be nullable or a reference type</span></span>
<span data-ttu-id="dfb49-103">`If` Wyrażenie może zająć dwie lub trzy argumenty.</span><span class="sxs-lookup"><span data-stu-id="dfb49-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="dfb49-104">Po wysłaniu tylko dwa argumenty pierwszy argument musi być parametrem typu odwołanie lub typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="dfb49-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="dfb49-105">Jeśli pierwszy argument daje w wyniku cokolwiek innego niż `Nothing`, zwracana jest jego wartość.</span><span class="sxs-lookup"><span data-stu-id="dfb49-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="dfb49-106">Jeśli pierwszy argument ma wartość `Nothing`, drugi argument jest obliczany i zwracany.</span><span class="sxs-lookup"><span data-stu-id="dfb49-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="dfb49-107">Na przykład poniższy kod zawiera dwa `If` wyrażenia, jeden z trzech argumentów i jeden z dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="dfb49-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="dfb49-108">Wyrażenia obliczenia i zwracają taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="dfb49-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="dfb49-109">Następujących wyrażeń być przyczyną tego błędu:</span><span class="sxs-lookup"><span data-stu-id="dfb49-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="dfb49-110">**Identyfikator błędu:** BC33107</span><span class="sxs-lookup"><span data-stu-id="dfb49-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dfb49-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="dfb49-111">To correct this error</span></span>  
  
-   <span data-ttu-id="dfb49-112">Jeśli nie możesz zmienić kod, aby pierwszy argument jest typu dopuszczającego wartość null lub typ referencyjny, należy wziąć pod uwagę konwertowania na trzech argumentów `If` wyrażenia, lub do `If...Then...Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="dfb49-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfb49-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfb49-113">See Also</span></span>  
 [<span data-ttu-id="dfb49-114">If, operator</span><span class="sxs-lookup"><span data-stu-id="dfb49-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="dfb49-115">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dfb49-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="dfb49-116">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="dfb49-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
