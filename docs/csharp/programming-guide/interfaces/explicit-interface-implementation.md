---
title: Implementacja interfejsu jawnego C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 498c45ff1c5837f5dcb0d4a80d0e3bb249abd694
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589216"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="080a9-102">Implementacja interfejsu jawnego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="080a9-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="080a9-103">Jeśli [Klasa](../../language-reference/keywords/class.md) implementuje dwa interfejsy, które zawierają element członkowski o tym samym podpisie, a następnie wdrożenie tego elementu członkowskiego w klasie spowoduje, że oba interfejsy używają tego elementu członkowskiego jako ich implementacji.</span><span class="sxs-lookup"><span data-stu-id="080a9-103">If a [class](../../language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="080a9-104">W poniższym przykładzie wszystkie wywołania do `Paint` wywołania tej samej metody.</span><span class="sxs-lookup"><span data-stu-id="080a9-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 <span data-ttu-id="080a9-105">Jeśli dwa elementy członkowskie [interfejsu](../../language-reference/keywords/interface.md) nie wykonują tej samej funkcji, może to jednak prowadzić do niepoprawnej implementacji jednego lub obu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="080a9-105">If the two [interface](../../language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="080a9-106">Istnieje możliwość jawnej implementacji elementu członkowskiego interfejsu — tworzenie składowej klasy, która jest wywoływana tylko przez interfejs i jest specyficzna dla tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="080a9-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="080a9-107">Jest to realizowane przez nazywanie składowej klasy nazwą interfejsu i kropką.</span><span class="sxs-lookup"><span data-stu-id="080a9-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="080a9-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="080a9-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 <span data-ttu-id="080a9-109">Element członkowski `IControl.Paint` klasy jest dostępny tylko `IControl` za pomocą interfejsu i `ISurface.Paint` jest dostępny tylko za pomocą `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="080a9-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="080a9-110">Obie implementacje metod są oddzielone, a żaden z nich nie jest dostępny bezpośrednio w klasie.</span><span class="sxs-lookup"><span data-stu-id="080a9-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="080a9-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="080a9-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 <span data-ttu-id="080a9-112">Jawna implementacja służy również do rozwiązywania przypadków, gdy dwa interfejsy deklarują różne elementy członkowskie o tej samej nazwie, takie jak właściwość i Metoda:</span><span class="sxs-lookup"><span data-stu-id="080a9-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 <span data-ttu-id="080a9-113">Aby zaimplementować oba interfejsy, Klasa musi używać jawnej implementacji dla właściwości P, lub metody P lub obu, aby uniknąć błędu kompilatora.</span><span class="sxs-lookup"><span data-stu-id="080a9-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="080a9-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="080a9-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a><span data-ttu-id="080a9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="080a9-115">See also</span></span>

- [<span data-ttu-id="080a9-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="080a9-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="080a9-117">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="080a9-117">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="080a9-118">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="080a9-118">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="080a9-119">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="080a9-119">Inheritance</span></span>](../classes-and-structs/inheritance.md)
