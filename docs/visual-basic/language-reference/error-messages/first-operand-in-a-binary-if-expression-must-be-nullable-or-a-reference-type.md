---
title: "Typem pierwszego operandu w binarnym &#39; Jeśli &#39; Wyrażenie musi być typ zerowalny lub typ odwołania"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f66b110c02076120c55a3bff28c3d7614bf8be26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="76c88-102">Typem pierwszego operandu w binarnym &#39; Jeśli &#39; Wyrażenie musi być typ zerowalny lub typ odwołania</span><span class="sxs-lookup"><span data-stu-id="76c88-102">First operand in a binary &#39;If&#39; expression must be nullable or a reference type</span></span>
<span data-ttu-id="76c88-103">`If` Wyrażenie może zająć dwie lub trzy argumenty.</span><span class="sxs-lookup"><span data-stu-id="76c88-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="76c88-104">Po wysłaniu tylko dwa argumenty pierwszy argument musi być parametrem typu odwołanie lub typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="76c88-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="76c88-105">Jeśli pierwszy argument daje w wyniku cokolwiek innego niż `Nothing`, zwracana jest jego wartość.</span><span class="sxs-lookup"><span data-stu-id="76c88-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="76c88-106">Jeśli pierwszy argument ma wartość `Nothing`, drugi argument jest obliczany i zwracany.</span><span class="sxs-lookup"><span data-stu-id="76c88-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="76c88-107">Na przykład poniższy kod zawiera dwa `If` wyrażenia, jeden z trzech argumentów i jeden z dwóch argumentów.</span><span class="sxs-lookup"><span data-stu-id="76c88-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="76c88-108">Wyrażenia obliczenia i zwracają taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="76c88-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="76c88-109">Następujących wyrażeń być przyczyną tego błędu:</span><span class="sxs-lookup"><span data-stu-id="76c88-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="76c88-110">**Identyfikator błędu:** BC33107</span><span class="sxs-lookup"><span data-stu-id="76c88-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="76c88-111">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="76c88-111">To correct this error</span></span>  
  
-   <span data-ttu-id="76c88-112">Jeśli nie możesz zmienić kod, aby pierwszy argument jest typu dopuszczającego wartość null lub typ referencyjny, należy wziąć pod uwagę konwertowania na trzech argumentów `If` wyrażenia, lub do `If...Then...Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="76c88-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="76c88-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76c88-113">See Also</span></span>  
 [<span data-ttu-id="76c88-114">Jeśli — Operator</span><span class="sxs-lookup"><span data-stu-id="76c88-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="76c88-115">IF... Następnie... Else — instrukcja</span><span class="sxs-lookup"><span data-stu-id="76c88-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="76c88-116">Typy dopuszczające wartości zerowe wartości</span><span class="sxs-lookup"><span data-stu-id="76c88-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
