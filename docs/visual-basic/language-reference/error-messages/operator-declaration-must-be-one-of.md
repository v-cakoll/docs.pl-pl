---
title: 'Deklaracja operatora musi mieć jeden z: +,-, *,-, -, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt; , &gt;=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: f32935dd4aaccd3040655b418badc13c1988c1b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622276"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="4c21a-102">Deklaracja operatora musi mieć jeden z: +,-, \*,\,/, ^, &amp;, Like, Mod i, Or, Xor, nie &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="4c21a-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="4c21a-103">Można zadeklarować tylko kwalifikuje się do przeciążania operatora.</span><span class="sxs-lookup"><span data-stu-id="4c21a-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="4c21a-104">W poniższej tabeli wymieniono operatory, których można zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="4c21a-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="4c21a-105">Typ</span><span class="sxs-lookup"><span data-stu-id="4c21a-105">Type</span></span>|<span data-ttu-id="4c21a-106">Operatory</span><span class="sxs-lookup"><span data-stu-id="4c21a-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="4c21a-107">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="4c21a-107">Unary</span></span>|<span data-ttu-id="4c21a-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="4c21a-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="4c21a-109">plików binarnych</span><span class="sxs-lookup"><span data-stu-id="4c21a-109">Binary</span></span>|<span data-ttu-id="4c21a-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="4c21a-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="4c21a-111">Konwersja (jednoargumentowy)</span><span class="sxs-lookup"><span data-stu-id="4c21a-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="4c21a-112">Należy pamiętać, że `=` operator binarny listy jest operator porównania nie operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="4c21a-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="4c21a-113">**Identyfikator błędu:** BC33000</span><span class="sxs-lookup"><span data-stu-id="4c21a-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c21a-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4c21a-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="4c21a-115">Wybierz operatora z zestawu operatory z możliwością przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="4c21a-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="4c21a-116">Przeciążanie operatora, który nie może zostać bezpośrednio przeciążenia funkcji, należy utworzyć `Function` procedury, która przyjmuje odpowiednie parametry i zwraca odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="4c21a-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c21a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c21a-117">See also</span></span>
- [<span data-ttu-id="4c21a-118">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4c21a-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="4c21a-119">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="4c21a-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="4c21a-120">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="4c21a-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="4c21a-121">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="4c21a-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="4c21a-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4c21a-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
