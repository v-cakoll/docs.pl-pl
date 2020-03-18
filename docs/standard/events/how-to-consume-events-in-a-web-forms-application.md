---
title: 'Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 1f95fd0dcc12f2d4e47ee07e1e6bb15d91000f0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124786"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web
Typowym scenariuszem w ASP.NET aplikacjach formularzy sieci Web jest wypełnienie strony sieci Web formantami, a następnie wykonanie określonej akcji na podstawie tego, które użytkownik klika. Na przykład <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> formant wywołuje zdarzenie, gdy użytkownik kliknie go na stronie sieci Web. Obsługując zdarzenie, aplikacja może wykonać odpowiednią logikę aplikacji dla tego kliknięcia przycisku.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Aby obsługiwać przycisk Kliknij zdarzenie na stronie sieci Web  
  
1. Utwórz ASP.NET stronę formularzy sieci Web <xref:System.Web.UI.WebControls.Button> (strony `OnClick` sieci Web), która ma kontrolkę z wartością ustawioną na nazwę metody, którą zdefiniujesz w następnym kroku.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. Zdefiniuj program <xref:System.Web.UI.WebControls.Button.Click> obsługi zdarzeń, który pasuje do podpisu delegata zdarzenia i który ma nazwę zdefiniowaną `OnClick` dla wartości.  
  
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
  
     Zdarzenie <xref:System.Web.UI.WebControls.Button.Click> używa <xref:System.EventHandler> klasy dla typu delegata <xref:System.EventArgs> i klasy dla danych zdarzenia. Struktura ASP.NET strony automatycznie generuje kod, który <xref:System.EventHandler> tworzy wystąpienie i dodaje <xref:System.Web.UI.WebControls.Button.Click> to <xref:System.Web.UI.WebControls.Button> wystąpienie delegata do zdarzenia wystąpienia.  
  
3. W metodzie obsługi zdarzeń zdefiniowanej w kroku 2 dodaj kod, aby wykonać wszystkie akcje, które są wymagane w przypadku wystąpienia zdarzenia.  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../../docs/standard/events/index.md)
