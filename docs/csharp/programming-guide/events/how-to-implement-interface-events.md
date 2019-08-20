---
title: 'Instrukcje: Implementowanie zdarzeń interfejsu C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 574ea9927a22c24c356d84652fd29692c519247b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590507"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Instrukcje: Implementuj zdarzenia interfejsu (C# Przewodnik programowania)
[Interfejs](../../language-reference/keywords/interface.md) może zadeklarować [zdarzenie](../../language-reference/keywords/event.md). Poniższy przykład pokazuje, jak zaimplementować zdarzenia interfejsu w klasie. Zasadniczo reguły są takie same, jak w przypadku implementowania dowolnej metody interfejsu lub właściwości.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Aby zaimplementować zdarzenia interfejsu w klasie  
  
Zadeklaruj zdarzenie w klasie, a następnie Wywołaj je w odpowiednich obszarach.  
  
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
Poniższy przykład pokazuje, jak obsłużyć mniej typowe sytuacje, w których Klasa dziedziczy z co najmniej dwóch interfejsów, a każdy interfejs ma zdarzenie o tej samej nazwie. W takiej sytuacji należy podać jawną implementację interfejsu dla co najmniej jednego zdarzenia. Podczas pisania jawnej implementacji interfejsu dla zdarzenia należy również napisać `add` metody dostępu do zdarzeń i. `remove` Zwykle są one dostarczane przez kompilator, ale w tym przypadku kompilator nie może ich udostępnić.  
  
Dostarczając własne metody dostępu, można określić, czy dwa zdarzenia są reprezentowane przez to samo zdarzenie w klasie, czy przez różne zdarzenia. Na przykład jeśli zdarzenia powinny być zgłaszane w różnych terminach zgodnie ze specyfikacją interfejsu, można skojarzyć każde zdarzenie z oddzielną implementacją w klasie. W poniższym przykładzie Subskrybenci określają, które `OnDraw` zdarzenie będzie odbierane przez wyrzucanie odwołania kształtu do `IShape` `IDrawingObject`albo.  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](./index.md)
- [Delegaty](../delegates/index.md)
- [Implementacja interfejsu jawnego](../interfaces/explicit-interface-implementation.md)
- [Instrukcje: Wywołaj zdarzenia klasy podstawowej w klasach pochodnych](./how-to-raise-base-class-events-in-derived-classes.md)
