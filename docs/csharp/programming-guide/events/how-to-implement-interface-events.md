---
title: Jak zaimplementować zdarzenia interfejsu - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 8c0d221ef1272a43e2682ef2af3fa37d2d12d35e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167483"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Jak zaimplementować zdarzenia interfejsu (Przewodnik programowania C#)
[Interfejs](../../language-reference/keywords/interface.md) może zadeklarować [zdarzenie](../../language-reference/keywords/event.md). W poniższym przykładzie pokazano, jak zaimplementować zdarzenia interfejsu w klasie. Zasadniczo reguły są takie same, jak podczas implementowania dowolnej metody interfejsu lub właściwości.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Aby zaimplementować zdarzenia interfejsu w klasie  
  
Zadeklarować zdarzenie w klasie, a następnie wywołać go w odpowiednich obszarach.  
  
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
W poniższym przykładzie pokazano, jak obsługiwać mniej typowej sytuacji, w której klasa dziedziczy z dwóch lub więcej interfejsów i każdy interfejs ma zdarzenie o tej samej nazwie. W tej sytuacji należy podać implementację interfejsu jawnego dla co najmniej jednego zdarzenia. Podczas pisania implementacji interfejsu jawnego dla zdarzenia, `add` `remove` należy również napisać akcesorów i zdarzeń. Zwykle są one dostarczane przez kompilator, ale w tym przypadku kompilator nie może ich podać.  
  
Udostępniając własne akcesory, można określić, czy dwa zdarzenia są reprezentowane przez to samo zdarzenie w klasie lub przez różne zdarzenia. Na przykład jeśli zdarzenia powinny być wywoływane w różnym czasie zgodnie ze specyfikacjami interfejsu, można skojarzyć każde zdarzenie z oddzielną implementacją w klasie. W poniższym przykładzie subskrybenci określają, które `OnDraw` zdarzenie `IShape` otrzymają, `IDrawingObject`rzutując odwołanie do kształtu do pliku .  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zdarzenia](./index.md)
- [Delegaty](../delegates/index.md)
- [Implementacja interfejsu jawnego](../interfaces/explicit-interface-implementation.md)
- [Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych](./how-to-raise-base-class-events-in-derived-classes.md)
