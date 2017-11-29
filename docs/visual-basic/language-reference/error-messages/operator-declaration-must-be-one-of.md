---
title: "Deklaracja operatora musi mieć jeden z: +,-, *,-, -, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue, IsFalse"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords: BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="11f7b-102">Deklaracja operatora musi mieć jeden z: +,-, *,\,/, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="11f7b-102">Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="11f7b-103">Można zadeklarować tylko operatora, który jest uprawniona do przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="11f7b-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="11f7b-104">W poniższej tabeli wymieniono operatory, których można zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="11f7b-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="11f7b-105">Typ</span><span class="sxs-lookup"><span data-stu-id="11f7b-105">Type</span></span>|<span data-ttu-id="11f7b-106">Operatory</span><span class="sxs-lookup"><span data-stu-id="11f7b-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="11f7b-107">Jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="11f7b-107">Unary</span></span>|<span data-ttu-id="11f7b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="11f7b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="11f7b-109">plików binarnych</span><span class="sxs-lookup"><span data-stu-id="11f7b-109">Binary</span></span>|<span data-ttu-id="11f7b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="11f7b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="11f7b-111">Konwersja (jednoargumentowy)</span><span class="sxs-lookup"><span data-stu-id="11f7b-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="11f7b-112">Należy pamiętać, że `=` operator porównania nie operator przypisania jest operator binarny listy.</span><span class="sxs-lookup"><span data-stu-id="11f7b-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="11f7b-113">**Identyfikator błędu:** BC33000</span><span class="sxs-lookup"><span data-stu-id="11f7b-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11f7b-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="11f7b-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="11f7b-115">Wybierz operator z zestawu operatory z możliwością przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="11f7b-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="11f7b-116">Jeśli potrzebujesz funkcji przeciążenia operatora, który nie możesz przeciążyć bezpośrednio utworzyć `Function` procedury, która przyjmuje odpowiednie parametry i zwraca odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="11f7b-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f7b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11f7b-117">See Also</span></span>  
 [<span data-ttu-id="11f7b-118">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="11f7b-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="11f7b-119">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="11f7b-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="11f7b-120">Porady: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="11f7b-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="11f7b-121">Porady: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="11f7b-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="11f7b-122">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="11f7b-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
