---
title: Implementacja interfejsu jawnego - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 67ade9ae41e90d8320e1b798ccfcd89cef8055a3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966427"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="450bc-102">Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="450bc-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="450bc-103">Jeśli [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy, które zawierają element członkowski o tym samym podpisie, a następnie wykonywania tego elementu członkowskiego w klasie spowoduje, że oba interfejsy do użycia tego elementu członkowskiego jako ich implementacji.</span><span class="sxs-lookup"><span data-stu-id="450bc-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="450bc-104">W poniższym przykładzie, wszystkie wywołania do `Paint` wywołania tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="450bc-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 <span data-ttu-id="450bc-105">Jeśli dwa [interfejsu](../../../csharp/language-reference/keywords/interface.md) elementy członkowskie nie wykonuj tę samą funkcję, jednak może to spowodować niepoprawne implementację jeden lub oba interfejsy.</span><span class="sxs-lookup"><span data-stu-id="450bc-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="450bc-106">Można jawnie implementować składowej interfejsu — tworzenie składowej klasy, która jest wywoływana tylko za pośrednictwem interfejsu i specyficzne dla tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="450bc-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="450bc-107">Jest to realizowane za pomocą nazw składowej klasy o nazwie interfejsu i kropką.</span><span class="sxs-lookup"><span data-stu-id="450bc-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="450bc-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="450bc-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 <span data-ttu-id="450bc-109">Składowa klasy `IControl.Paint` jest dostępna tylko `IControl` interfejsu, a `ISurface.Paint` jest dostępna tylko `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="450bc-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="450bc-110">Zarówno implementacje metod są niezależne i nie będzie dostępny bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="450bc-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="450bc-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="450bc-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 <span data-ttu-id="450bc-112">Jawna implementacja jest również używany do rozpoznawania przypadki, w której dwa interfejsy zadeklarować inne elementy członkowskie o takiej samej nazwie, takie jak właściwości i metody:</span><span class="sxs-lookup"><span data-stu-id="450bc-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 <span data-ttu-id="450bc-113">Aby zaimplementować obu interfejsów, klasa ma używać jawnych implementacji P właściwości lub metody P i / lub, aby uniknąć błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="450bc-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="450bc-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="450bc-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a><span data-ttu-id="450bc-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="450bc-115">See also</span></span>

- [<span data-ttu-id="450bc-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="450bc-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="450bc-117">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="450bc-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="450bc-118">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="450bc-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="450bc-119">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="450bc-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
