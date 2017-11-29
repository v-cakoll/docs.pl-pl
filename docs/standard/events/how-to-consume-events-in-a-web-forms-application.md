---
title: "Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bdb0a6be309f27348ba13bf93fd5aedd3c66a792
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web
Typowy scenariusz w aplikacji formularzy sieci Web programu ASP.NET jest wypełnienie strony sieci Web z formantami, a następnie wykonywać konkretną akcję, w oparciu o który kontroli, użytkownik klika polecenie. Na przykład <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> kontroli wywołuje zdarzenie po kliknięciu przez użytkownika na stronie sieci Web. Dzięki obsłudze zdarzenia, aplikacja może wykonywać logiki aplikacji dla tego kliknij przycisk.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Aby obsługiwać przycisk Kliknij zdarzenie na stronie sieci Web  
  
1.  Tworzenie strony formularzy sieci Web ASP.NET (strona sieci Web), który ma <xref:System.Web.UI.WebControls.Button> sterować za pomocą `OnClick` wartość ustawiona na nazwę metody, który będzie definiował w następnym kroku.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  Definiowanie procedury obsługi zdarzeń, odpowiadający <xref:System.Web.UI.WebControls.Button.Click> podpisu delegata zdarzenia i że ma nazwę zdefiniowane dla `OnClick` wartość.  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <xref:System.Web.UI.WebControls.Button.Click> Używa zdarzeń <xref:System.EventHandler> klasy dla typu delegata i <xref:System.EventArgs> klasy danych zdarzenia. Architekturę stron ASP.NET jest automatycznie generuje kod, który tworzy wystąpienie <xref:System.EventHandler> i dodanie tego wystąpienia obiektu delegowanego <xref:System.Web.UI.WebControls.Button.Click> zdarzenie <xref:System.Web.UI.WebControls.Button> wystąpienia.  
  
3.  W przypadku metoda obsługi, który został zdefiniowany w kroku 2, Dodaj kod, aby wykonać wszystkie akcje, które są wymagane w przypadku wystąpienia zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../docs/standard/events/index.md)
