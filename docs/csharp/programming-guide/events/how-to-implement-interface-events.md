---
title: 'Instrukcje: Zdarzenia implementowania interfejsu - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: dfd0602ef92f9b0f84a8e1434ef834a328d60f03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710904"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Instrukcje: Zdarzenia implementowania interfejsu (C# Programming Guide)
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
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)
- [Implementacja interfejsu jawnego](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)
- [Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
