---
title: 'Instrukcje: Zdarzenia implementowania interfejsu - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: dfd0602ef92f9b0f84a8e1434ef834a328d60f03
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200276"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="abe83-102">Instrukcje: Zdarzenia implementowania interfejsu (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="abe83-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="abe83-103">[Interfejsu](../../../csharp/language-reference/keywords/interface.md) można zadeklarować [zdarzeń](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="abe83-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="abe83-104">Poniższy przykład pokazuje, jak zdarzenia implementowania interfejsu w klasie.</span><span class="sxs-lookup"><span data-stu-id="abe83-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="abe83-105">Zasadniczo reguły są takie same, jak podczas implementowania metody interfejsu dowolnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="abe83-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="abe83-106">Aby zaimplementować interfejs zdarzenia w klasie</span><span class="sxs-lookup"><span data-stu-id="abe83-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="abe83-107">Zadeklarować zdarzenia w klasie, a następnie wywołaj je w odpowiednich obszarów.</span><span class="sxs-lookup"><span data-stu-id="abe83-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs   
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.   
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a><span data-ttu-id="abe83-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="abe83-108">Example</span></span>  
<span data-ttu-id="abe83-109">Poniższy przykład pokazuje, jak obsługiwać mniej znane sytuacji, w którym klasa dziedziczy z dwóch lub więcej interfejsów, a każdy interfejs posiada zdarzenie o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="abe83-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="abe83-110">W takiej sytuacji należy podać jawnej implementacji interfejsu dla co najmniej jednego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="abe83-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="abe83-111">Podczas pisania jawnej implementacji interfejsu zdarzenia musi także napisać `add` i `remove` metod dostępu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="abe83-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="abe83-112">Zwykle są one udostępniane przez kompilator, ale w tym przypadku kompilator nie może dostarczyć je.</span><span class="sxs-lookup"><span data-stu-id="abe83-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="abe83-113">Podając własne metody dostępu, można określić, czy dwa zdarzenia są reprezentowane przez te same zdarzenia w klasie lub różnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="abe83-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="abe83-114">Na przykład jeśli zdarzenia powinien być wywoływany w różnym czasie zgodnie ze specyfikacją interfejsu, można skojarzyć każde zdarzenie z oddzielnych implementacją w klasie.</span><span class="sxs-lookup"><span data-stu-id="abe83-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="abe83-115">W poniższym przykładzie subskrybentów określenie `OnDraw` otrzymają przez rzutowanie odwołanie kształtu do każdego zdarzenia `IShape` lub `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="abe83-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="abe83-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abe83-116">See also</span></span>

- [<span data-ttu-id="abe83-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="abe83-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="abe83-118">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="abe83-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="abe83-119">Delegaty</span><span class="sxs-lookup"><span data-stu-id="abe83-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="abe83-120">Implementacja interfejsu jawnego</span><span class="sxs-lookup"><span data-stu-id="abe83-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="abe83-121">Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="abe83-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
