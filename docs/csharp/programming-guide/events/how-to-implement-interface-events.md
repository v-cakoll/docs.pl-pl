---
title: 'Porady: zdarzenia implementowania interfejsu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 3620a3e11553bdd6878126388b612113b5722e89
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802761"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Porady: zdarzenia implementowania interfejsu (Przewodnik programowania w języku C#)
[Interfejsu](../../../csharp/language-reference/keywords/interface.md) można zadeklarować [zdarzeń](../../../csharp/language-reference/keywords/event.md). Poniższy przykład pokazuje, jak zdarzenia implementowania interfejsu w klasie. Zasadniczo reguły są takie same, jak podczas implementowania metody interfejsu dowolnej właściwości.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Aby zaimplementować interfejs zdarzenia w klasie  
  
Zadeklarować zdarzenia w klasie, a następnie wywołaj je w odpowiednich obszarów.  
  
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
  
## <a name="example"></a>Przykład  
Poniższy przykład pokazuje, jak obsługiwać mniej znane sytuacji, w którym klasa dziedziczy z dwóch lub więcej interfejsów, a każdy interfejs posiada zdarzenie o takiej samej nazwie. W takiej sytuacji należy podać jawnej implementacji interfejsu dla co najmniej jednego zdarzenia. Podczas pisania jawnej implementacji interfejsu zdarzenia musi także napisać `add` i `remove` metod dostępu zdarzeń. Zwykle są one udostępniane przez kompilator, ale w tym przypadku kompilator nie może dostarczyć je.  
  
Podając własne metody dostępu, można określić, czy dwa zdarzenia są reprezentowane przez te same zdarzenia w klasie lub różnych zdarzeń. Na przykład jeśli zdarzenia powinien być wywoływany w różnym czasie zgodnie ze specyfikacją interfejsu, można skojarzyć każde zdarzenie z oddzielnych implementacją w klasie. W poniższym przykładzie subskrybentów określenie `OnDraw` otrzymają przez rzutowanie odwołanie kształtu do każdego zdarzenia `IShape` lub `IDrawingObject`.  
  
 [!code-csharp[WrapTwoInterfaceEvents](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs#everything)]
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
- [Implementacja interfejsu jawnego](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
- [Instrukcje: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
