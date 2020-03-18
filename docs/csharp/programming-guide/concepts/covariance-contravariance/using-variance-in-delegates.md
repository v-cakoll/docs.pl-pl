---
title: Używanie wariancji w delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 83e86e760edb17f6d9ae61864c154062d41416e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169769"
---
# <a name="using-variance-in-delegates-c"></a>Używanie wariancji w delegatach (C#)
Po przypisaniu metody do delegata, *kowariancja* i *contravariance* zapewniają elastyczność dopasowania typu delegata z podpisem metody. Kowariancja pozwala metody mieć zwracany typ, który jest bardziej pochodną niż zdefiniowane w delegata. Contravariance zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż w typie delegata.  
  
## <a name="example-1-covariance"></a>Przykład 1: Kowariancja  
  
### <a name="description"></a>Opis  
 W tym przykładzie pokazano, jak delegatów mogą być używane z metod, które mają typy zwracane, które są uzyskiwane z typu zwracanego w podpisie delegata. Typ danych zwracany `DogsHandler` przez `Dogs`jest typu , `Mammals` który pochodzi od typu, który jest zdefiniowany w pełnomocnika.  
  
### <a name="code"></a>Code  
  
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
  
## <a name="example-2-contravariance"></a>Przykład 2: Contravariance  
  
### <a name="description"></a>Opis

W tym przykładzie pokazano, jak delegatów mogą być używane z metod, które mają parametry, których typy są typy podstawowe typu typu parametru podpisu delegata. Z contravariance, można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi. W poniższym przykładzie korzysta z dwóch delegatów:

- Pełnomocnik, <xref:System.Windows.Forms.KeyEventHandler> który definiuje podpis [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) zdarzenia. Jego podpis jest:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- Pełnomocnik <xref:System.Windows.Forms.MouseEventHandler> definiujący podpis zdarzenia [Button.MouseClick.](xref:System.Windows.Forms.Control.MouseDown) Jego podpis jest:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

W przykładzie definiuje program obsługi <xref:System.EventArgs> zdarzeń z parametrem `Button.KeyDown` `Button.MouseClick` i używa go do obsługi zarówno i zdarzenia. Można to zrobić, ponieważ <xref:System.EventArgs> jest <xref:System.Windows.Forms.KeyEventArgs> typem bazowym obu i <xref:System.Windows.Forms.MouseEventArgs>.
  
### <a name="code"></a>Code  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Wariancja w delegatach (C#)](./variance-in-delegates.md)
- [Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)](./using-variance-for-func-and-action-generic-delegates.md)
