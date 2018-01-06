---
title: "Porady: zdarzenia implementowania interfejsu (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a53c6ba29837ad8827d97ea745be0462451eb145
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="d5a54-102">Porady: zdarzenia implementowania interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d5a54-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="d5a54-103">[Interfejsu](../../../csharp/language-reference/keywords/interface.md) mogą zadeklarować [zdarzeń](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="d5a54-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="d5a54-104">Poniższy przykład pokazuje, jak można zaimplementować interfejsu zdarzenia w klasie.</span><span class="sxs-lookup"><span data-stu-id="d5a54-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="d5a54-105">Zasadniczo zasad są takie same jak podczas implementowania interfejsu metody ani właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5a54-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
### <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="d5a54-106">Aby zaimplementować interfejsu zdarzenia w klasie</span><span class="sxs-lookup"><span data-stu-id="d5a54-106">To implement interface events in a class</span></span>  
  
-   <span data-ttu-id="d5a54-107">Deklarowanie zdarzenia w klasie i wywołać go w odpowiednich obszarach.</span><span class="sxs-lookup"><span data-stu-id="d5a54-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="d5a54-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5a54-108">Example</span></span>  
 <span data-ttu-id="d5a54-109">Poniższy przykład przedstawia sposób obsługi mniej typowe sytuacji, w którym klasa dziedziczy z dwóch lub więcej interfejsów i każdy interfejs ma zdarzenia o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d5a54-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="d5a54-110">W takiej sytuacji należy dostarczyć jawnej implementacji interfejsu dla co najmniej jednego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5a54-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="d5a54-111">Podczas pisania jawnej implementacji interfejsu zdarzenia musi także zapisywać `add` i `remove` metod dostępu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5a54-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="d5a54-112">Zwykle te są dostarczane przez kompilator, ale w takim przypadku kompilator nie można udostępnić je.</span><span class="sxs-lookup"><span data-stu-id="d5a54-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
 <span data-ttu-id="d5a54-113">Podając własne metody dostępu, można określić, czy dwa zdarzenia są reprezentowane przez tego samego zdarzenia w klasie lub różnych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5a54-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="d5a54-114">Na przykład jeśli zdarzenia powinien być wywoływany w różnych momentach zgodnie ze specyfikacją określoną interfejsu, można skojarzyć każdego zdarzenia z implementacją oddzielne w klasie.</span><span class="sxs-lookup"><span data-stu-id="d5a54-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="d5a54-115">W poniższym przykładzie subskrybentów określenie `OnDraw` zdarzeń otrzymywanych przez rzutowanie odwołanie kształtu do albo `IShape` lub `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="d5a54-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d5a54-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5a54-116">See Also</span></span>  
 [<span data-ttu-id="d5a54-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d5a54-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d5a54-118">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d5a54-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="d5a54-119">Delegaci</span><span class="sxs-lookup"><span data-stu-id="d5a54-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="d5a54-120">Implementacja interfejsu jawnego</span><span class="sxs-lookup"><span data-stu-id="d5a54-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [<span data-ttu-id="d5a54-121">Instrukcje: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="d5a54-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
