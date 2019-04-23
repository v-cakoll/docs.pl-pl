---
title: 'Instrukcje: Korzystanie ze zdarzeń w aplikacjach formularzy internetowych'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc1dee9377200e4c9fd575b8dcd00982db45f249
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317821"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Instrukcje: Korzystanie ze zdarzeń w aplikacjach formularzy internetowych
Jest to częsty przypadek w aplikacji formularzy sieci Web programu ASP.NET do wypełniania strony sieci Web za pomocą kontrolek, a następnie wykonać określonej akcji, które kontrolują użytkownik klika polecenie w oparciu. Na przykład <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> kontrolki wywołuje zdarzenie po kliknięciu przez użytkownika na stronie sieci Web. Dzięki obsłudze zdarzenia, aplikację można wykonać logiki aplikacji odpowiednie dla tego kliknięcia przycisku.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Aby obsługiwać przycisk Kliknij zdarzenie na stronie sieci Web  
  
1. Tworzenie strony formularzy sieci Web platformy ASP.NET (strona sieci Web), który ma <xref:System.Web.UI.WebControls.Button> kontrolką `OnClick` wartość ustawiona na nazwę metody definiującej w następnym kroku.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. Definiowanie obsługi zdarzeń, który odpowiada <xref:System.Web.UI.WebControls.Button.Click> podpis delegata zdarzenia i który ma nazwę zdefiniowaną dla `OnClick` wartość.  
  
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
  
     <xref:System.Web.UI.WebControls.Button.Click> Zdarzeń używa <xref:System.EventHandler> klasy dla typu delegata i <xref:System.EventArgs> klasy danych zdarzenia. Architektura strony ASP.NET automatycznie generuje kod, który tworzy wystąpienie <xref:System.EventHandler> i dodaje tego wystąpienia delegata <xref:System.Web.UI.WebControls.Button.Click> zdarzenia <xref:System.Web.UI.WebControls.Button> wystąpienia.  
  
3. W przypadku metody obsługi, który został zdefiniowany w kroku 2, Dodaj kod, aby wykonywać żadnych akcji, które są wymagane, gdy wystąpi zdarzenie.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../../docs/standard/events/index.md)
