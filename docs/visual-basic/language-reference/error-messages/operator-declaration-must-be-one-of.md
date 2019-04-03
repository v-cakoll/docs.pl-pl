---
title: 'Deklaracja operatora musi mieć jeden z: +,-, *,-, -, ^, &amp;, Like, Mod i, Or, Xor, nie <<>>,, = <>, <, < =, >, > =, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: dac8613d79e3262e4d1fd6ad1599fd01182e329b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819375"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="6b799-102">Deklaracja operatora musi mieć jeden z: +,-, \*,\,/, ^, &amp;, Like, Mod i, Or, Xor, nie \< \<, >>...</span><span class="sxs-lookup"><span data-stu-id="6b799-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="6b799-103">Można zadeklarować tylko kwalifikuje się do przeciążania operatora.</span><span class="sxs-lookup"><span data-stu-id="6b799-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="6b799-104">W poniższej tabeli wymieniono operatory, których można zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="6b799-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="6b799-105">Typ</span><span class="sxs-lookup"><span data-stu-id="6b799-105">Type</span></span>|<span data-ttu-id="6b799-106">Operatory</span><span class="sxs-lookup"><span data-stu-id="6b799-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="6b799-107">Jednoargumentowy</span><span class="sxs-lookup"><span data-stu-id="6b799-107">Unary</span></span>|<span data-ttu-id="6b799-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="6b799-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="6b799-109">plików binarnych</span><span class="sxs-lookup"><span data-stu-id="6b799-109">Binary</span></span>|<span data-ttu-id="6b799-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="6b799-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="6b799-111">Konwersja (jednoargumentowy)</span><span class="sxs-lookup"><span data-stu-id="6b799-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="6b799-112">Należy pamiętać, że `=` operator binarny listy jest operator porównania nie operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="6b799-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="6b799-113">**Identyfikator błędu:** BC33000</span><span class="sxs-lookup"><span data-stu-id="6b799-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b799-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6b799-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="6b799-115">Wybierz operatora z zestawu operatory z możliwością przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="6b799-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="6b799-116">Przeciążanie operatora, który nie może zostać bezpośrednio przeciążenia funkcji, należy utworzyć `Function` procedury, która przyjmuje odpowiednie parametry i zwraca odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="6b799-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b799-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b799-117">See also</span></span>

- [<span data-ttu-id="6b799-118">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b799-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="6b799-119">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="6b799-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="6b799-120">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="6b799-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="6b799-121">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="6b799-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="6b799-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b799-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
