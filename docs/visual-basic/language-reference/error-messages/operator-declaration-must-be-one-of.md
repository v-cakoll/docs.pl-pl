---
title: 'Deklaracja operatora musi mieć jeden z: +,-, *,-, -, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: eb1e7e8088ec8661be2469aff043c0f1a96e4d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="a6f7d-102">Deklaracja operatora musi mieć jeden z: +,-, \*,\,/, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="a6f7d-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="a6f7d-103">Można zadeklarować tylko operatora, który jest uprawniona do przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="a6f7d-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="a6f7d-104">W poniższej tabeli wymieniono operatory, których można zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="a6f7d-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="a6f7d-105">Typ</span><span class="sxs-lookup"><span data-stu-id="a6f7d-105">Type</span></span>|<span data-ttu-id="a6f7d-106">Operatory</span><span class="sxs-lookup"><span data-stu-id="a6f7d-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="a6f7d-107">Jednoargumentowe</span><span class="sxs-lookup"><span data-stu-id="a6f7d-107">Unary</span></span>|<span data-ttu-id="a6f7d-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="a6f7d-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="a6f7d-109">plików binarnych</span><span class="sxs-lookup"><span data-stu-id="a6f7d-109">Binary</span></span>|<span data-ttu-id="a6f7d-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="a6f7d-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="a6f7d-111">Konwersja (jednoargumentowy)</span><span class="sxs-lookup"><span data-stu-id="a6f7d-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="a6f7d-112">Należy pamiętać, że `=` operator porównania nie operator przypisania jest operator binarny listy.</span><span class="sxs-lookup"><span data-stu-id="a6f7d-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="a6f7d-113">**Identyfikator błędu:** BC33000</span><span class="sxs-lookup"><span data-stu-id="a6f7d-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6f7d-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a6f7d-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="a6f7d-115">Wybierz operator z zestawu operatory z możliwością przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="a6f7d-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="a6f7d-116">Jeśli potrzebujesz funkcji przeciążenia operatora, który nie możesz przeciążyć bezpośrednio utworzyć `Function` procedury, która przyjmuje odpowiednie parametry i zwraca odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="a6f7d-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f7d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6f7d-117">See Also</span></span>  
 [<span data-ttu-id="a6f7d-118">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a6f7d-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="a6f7d-119">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="a6f7d-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="a6f7d-120">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="a6f7d-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="a6f7d-121">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="a6f7d-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="a6f7d-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a6f7d-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
