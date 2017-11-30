---
title: "Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="bb842-102">Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bb842-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="bb842-103">Ponieważ obiekt jest polimorficzny, istnieje możliwość zmiennej typu klasy podstawowej typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="bb842-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="bb842-104">Aby uzyskać dostęp do metody typu pochodnego, należy rzutować wartości do typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="bb842-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="bb842-105">Próba prostą rzutowanie w tych przypadkach tworzy jednak ryzyko zgłaszanie <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="bb842-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="bb842-106">Oznacza to dlaczego C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="bb842-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="bb842-107">Aby sprawdzić, czy rzutowanie powiedzie się, nie powodując wyjątek zostanie wygenerowany, można użyć tych operatorów.</span><span class="sxs-lookup"><span data-stu-id="bb842-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="bb842-108">Ogólnie rzecz biorąc `as` operator jest bardziej wydajne, ponieważ zwraca ono wartość rzeczywistą wartość rzutowania Jeśli rzutowanie może się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bb842-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="bb842-109">`is` Operator zwraca tylko wartość typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="bb842-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="bb842-110">W związku z tym można używać podczas po prostu chcesz określić typu obiektu, ale nie trzeba rzeczywistą rzutować go.</span><span class="sxs-lookup"><span data-stu-id="bb842-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb842-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb842-111">Example</span></span>  
 <span data-ttu-id="bb842-112">W poniższych przykładach pokazano, jak używać `is` i `as` operatory rzutowania z jednego odwołania do typu na inny bez ryzyka Zgłaszanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="bb842-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="bb842-113">W przykładzie przedstawiono również sposób użycia `as` operatora z typów wartości null.</span><span class="sxs-lookup"><span data-stu-id="bb842-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bb842-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb842-114">See Also</span></span>  
 [<span data-ttu-id="bb842-115">Typy</span><span class="sxs-lookup"><span data-stu-id="bb842-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="bb842-116">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="bb842-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="bb842-117">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="bb842-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
