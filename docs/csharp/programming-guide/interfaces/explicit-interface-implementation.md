---
title: Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 7494f7d6a3897d56419f9d3aa96668fd9dab5f35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331594"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="c690c-102">Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c690c-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="c690c-103">Jeśli [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy zawierające element członkowski o tej samej sygnaturze, a następnie wykonania ten element członkowski klasy spowoduje, że oba interfejsy do użycia tego elementu członkowskiego jako ich wdrażania.</span><span class="sxs-lookup"><span data-stu-id="c690c-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="c690c-104">W poniższym przykładzie wszystkie wywołania do `Paint` wywołanie tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="c690c-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 <span data-ttu-id="c690c-105">Jeśli dwa [interfejsu](../../../csharp/language-reference/keywords/interface.md) elementów członkowskich nie wykonuj tę samą funkcję, jednak może to prowadzić do niepoprawna implementacja jednej lub obu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="c690c-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="c690c-106">Istnieje możliwość jawnie implementować elementu członkowskiego interfejsu — Tworzenie elementu członkowskiego klasy, która jest wywoływana tylko za pośrednictwem interfejsu i specyficzne dla interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c690c-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="c690c-107">Odbywa się za pomocą nazw elementu członkowskiego klasy o nazwie interfejs i okres.</span><span class="sxs-lookup"><span data-stu-id="c690c-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="c690c-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c690c-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 <span data-ttu-id="c690c-109">Element członkowski klasy `IControl.Paint` są dostępne tylko w `IControl` interfejsu i `ISurface.Paint` są dostępne tylko w `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="c690c-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="c690c-110">Zarówno implementacje metod są oddzielone i nie będzie dostępny bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="c690c-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="c690c-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c690c-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 <span data-ttu-id="c690c-112">Jawna implementacja jest również używany do rozpoznawania przypadków, gdy dwa interfejsy zadeklarować inne elementy członkowskie o tej samej nazwie, takie jak właściwości i metody:</span><span class="sxs-lookup"><span data-stu-id="c690c-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 <span data-ttu-id="c690c-113">Aby zaimplementować dotyczą obu interfejsów, klasa ma Użyj jawnej implementacji dla właściwości P lub metody P i/lub aby uniknąć błędów kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c690c-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="c690c-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c690c-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c690c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c690c-115">See Also</span></span>  
 [<span data-ttu-id="c690c-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c690c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c690c-117">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="c690c-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="c690c-118">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c690c-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="c690c-119">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="c690c-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
