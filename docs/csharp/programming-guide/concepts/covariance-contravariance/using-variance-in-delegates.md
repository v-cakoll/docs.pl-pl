---
title: Korzystanie z wariancji w Delegatach (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb8512945fa7aefa9afce4f4f1f8e0200dc3e2b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-c"></a>Korzystanie z wariancji w Delegatach (C#)
Po przypisaniu metodę z delegatem, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dopasowanie typem obiektu delegowanego przy użyciu podpisu metody. Kowariancja pozwala metoda ma typ zwracany jest bardziej pochodny niż zdefiniowana w elemencie delegowanym. Kontrawariancja zezwala na metodę, która zawiera typy parametrów, które są mniej pochodnego od tych w typie delegata.  
  
## <a name="example-1-covariance"></a>Przykład 1: Kowariancja  
  
### <a name="description"></a>Opis  
 W tym przykładzie pokazano, delegatów możliwości korzystania z metody, które mają zwracanych typów pochodzących z zwracany typ w sygnaturze delegata. Typ danych zwracanych przez `DogsHandler` jest typu `Dogs`, która jest pochodną `Mammals` typu, który jest zdefiniowany w elemencie delegowanym.  
  
### <a name="code"></a>Kod  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
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
 W przykładzie pokazano, jak delegatów można użyć z metod, które ma parametry typu, które typy podstawowe typu parametru podpisu delegata. Z kontrawariancji można użyć jednej procedury obsługi zdarzeń, zamiast oddzielnych programów obsługi. Na przykład można utworzyć program obsługi zdarzeń, który akceptuje `EventArgs` parametr wejściowy i używać go z `Button.MouseClick` zdarzeń, która wysyła `MouseEventArgs` typu jako parametru, a także z `TextBox.KeyDown` zdarzeń, która wysyła `KeyEventArgs` parametru.  
  
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
 [Wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
