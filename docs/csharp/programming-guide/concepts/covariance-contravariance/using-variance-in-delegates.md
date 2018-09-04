---
title: Korzystanie z wariancji w Delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 5be4f786d2e1b8a0ead3fd58fe056e188faa916a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501727"
---
# <a name="using-variance-in-delegates-c"></a>Korzystanie z wariancji w Delegatach (C#)
Po przypisaniu metody z delegatem, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dopasowanie typu delegata z podpis metody. Kowariancja zezwala na metodę, aby zwracany typ, który jest bardziej pochodnego niż zdefiniowanymi dla delegata. Kontrawariancja umożliwia metody, która ma typy parametrów, które są mniej pochodnego niż typ delegata.  
  
## <a name="example-1-covariance"></a>Przykład 1: Kowariancja  
  
### <a name="description"></a>Opis  
 W tym przykładzie pokazano, jak można używać delegatów za pomocą metod, które mają zwracane typy, które są uzyskiwane ze zwracanego typu w podpisie delegata. Typ danych zwracanych przez `DogsHandler` typu `Dogs`, która pochodzi od klasy `Mammals` typu, który jest zdefiniowany w delegacie.  
  
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
 W tym przykładzie pokazano, jak można używać delegatów za pomocą metody, które mają parametry typu, które typy podstawowe typu parametru podpis delegata. Za pomocą kontrawariancja możesz użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi. Na przykład można utworzyć program obsługi zdarzeń, który akceptuje `EventArgs` parametr wejściowy i korzystać z niego przy użyciu `Button.MouseClick` zdarzenia, które wysyła `MouseEventArgs` typu jako parametru, a także z `TextBox.KeyDown` zdarzenia, które wysyła `KeyEventArgs` parametru.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
- [Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
