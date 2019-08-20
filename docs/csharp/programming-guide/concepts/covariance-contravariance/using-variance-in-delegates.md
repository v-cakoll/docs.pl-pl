---
title: Korzystanie z wariancji wC#delegatach ()
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 00e11d4ce755c8c75b73023fec14d95ebc96b4fe
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595261"
---
# <a name="using-variance-in-delegates-c"></a>Korzystanie z wariancji wC#delegatach ()
Podczas przypisywania metody do delegata, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dla dopasowania typu delegata z sygnaturą metody. Kowariancja zezwala metodzie na typ zwracany, który jest bardziej pochodny niż zdefiniowany w delegatze. Kontrawariancja zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż te w typie delegata.  
  
## <a name="example-1-covariance"></a>Przykład 1: Kowariancja  
  
### <a name="description"></a>Opis  
 Ten przykład pokazuje, jak obiekty delegowane mogą być używane z metodami, które mają typy zwracane, które pochodzą z typu zwracanego w sygnaturze delegata. Typ danych zwracanych przez `DogsHandler` element jest typu `Dogs` `Mammals` , który pochodzi od typu, który jest zdefiniowany w delegacie.  
  
### <a name="code"></a>Kod  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a>Przykład 2: Kontrawariancja  
  
### <a name="description"></a>Opis  
 W tym przykładzie pokazano, jak można używać delegatów z metodami, które mają parametry typu, które są typami podstawowymi typu parametru podpisu delegata. Za pomocą kontrawariancja można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi. Można na przykład utworzyć procedurę obsługi zdarzeń, `EventArgs` która akceptuje parametr wejściowy, i użyć go `Button.MouseClick` ze zdarzeniem, które wysyła `MouseEventArgs` typ `TextBox.KeyDown` jako parametr, `KeyEventArgs` a także ze zdarzeniem, które wysyła parametr.  
  
### <a name="code"></a>Kod  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wariancja w delegatach (C#)](./variance-in-delegates.md)
- [Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()](./using-variance-for-func-and-action-generic-delegates.md)
