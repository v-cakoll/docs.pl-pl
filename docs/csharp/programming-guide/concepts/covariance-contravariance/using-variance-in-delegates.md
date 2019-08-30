---
title: Korzystanie z wariancji wC#delegatach ()
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 980caf8d5e4699115d203a89fab7994d18cc1707
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168361"
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

W tym przykładzie pokazano, jak obiekty delegowane mogą być używane z metodami, które mają parametry, których typy są typami podstawowymi typu parametru podpisu delegata. Za pomocą kontrawariancja można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi. W poniższym przykładzie użyto dwóch delegatów:

- Delegat definiujący podpis zdarzenia [Button. KeyDown.](xref:System.Windows.Forms.Control.KeyDown) <xref:System.Windows.Forms.KeyEventHandler> Podpis jest:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- Delegat definiujący sygnaturę zdarzenia [Button. MouseClick.](xref:System.Windows.Forms.Control.MouseDown) <xref:System.Windows.Forms.MouseEventHandler> Podpis jest:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

W przykładzie zdefiniowano procedurę obsługi zdarzeń z <xref:System.EventArgs> parametrem i używa jej do obsługi `Button.KeyDown` zarówno zdarzenia `Button.MouseClick` , jak i. Można to zrobić, ponieważ <xref:System.EventArgs> jest typem podstawowym obu <xref:System.Windows.Forms.KeyEventArgs> i <xref:System.Windows.Forms.MouseEventArgs>. 
  
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
