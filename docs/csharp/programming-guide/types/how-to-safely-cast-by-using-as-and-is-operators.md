---
title: 'Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: de59fb49ca5dbe1282cd828f7d6995dda449d31b
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257304"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="986c7-102">Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="986c7-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="986c7-103">Ponieważ obiekty są polimorficznych, jest możliwe dla zmiennej do przechowywania Typ pochodny typ klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="986c7-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="986c7-104">Aby uzyskać dostęp do metod wystąpienia typu pochodnego, jest niezbędne Rzutowanie wartości do typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="986c7-104">To access the derived type's instance methods, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="986c7-105">Próby prostego rzutowanie w tych przypadkach tworzy jednak ryzyko zgłaszanie <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="986c7-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="986c7-106">Oznacza to dlaczego C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatorów.</span><span class="sxs-lookup"><span data-stu-id="986c7-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="986c7-107">Te operatory służy do sprawdzenia, czy rzutowania powiedzie się bez powodowania zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="986c7-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="986c7-108">Ogólnie rzecz biorąc `as` operator jest bardziej wydajne, ponieważ faktycznie program zwraca wartość rzutowania w przypadku rzutowania może się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="986c7-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="986c7-109">`is` Operator zwraca tylko wartość typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="986c7-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="986c7-110">Można w związku z tym używane, gdy po prostu chcesz określić typu obiektu, ale nie trzeba go rzutować faktycznie.</span><span class="sxs-lookup"><span data-stu-id="986c7-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="986c7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="986c7-111">Example</span></span>  
 <span data-ttu-id="986c7-112">W poniższych przykładach pokazano sposób użycia `is` i `as` operatorów rzutowania z jedno odwołanie do typu na inny bez ryzyka zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="986c7-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="986c7-113">W przykładzie pokazano również sposób użycia `as` operatora z typami wartości null.</span><span class="sxs-lookup"><span data-stu-id="986c7-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="986c7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="986c7-114">See Also</span></span>  
 [<span data-ttu-id="986c7-115">Typy</span><span class="sxs-lookup"><span data-stu-id="986c7-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="986c7-116">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="986c7-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="986c7-117">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="986c7-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
