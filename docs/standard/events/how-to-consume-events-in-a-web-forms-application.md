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
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="f4010-102">Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="f4010-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="f4010-103">Typowym scenariuszem w ASP.NET aplikacjach formularzy sieci Web jest wypełnienie strony sieci Web formantami, a następnie wykonanie określonej akcji na podstawie tego, które użytkownik klika.</span><span class="sxs-lookup"><span data-stu-id="f4010-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="f4010-104">Na przykład <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> formant wywołuje zdarzenie, gdy użytkownik kliknie go na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f4010-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="f4010-105">Obsługując zdarzenie, aplikacja może wykonać odpowiednią logikę aplikacji dla tego kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="f4010-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="f4010-106">Aby obsługiwać przycisk Kliknij zdarzenie na stronie sieci Web</span><span class="sxs-lookup"><span data-stu-id="f4010-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="f4010-107">Utwórz ASP.NET stronę formularzy sieci Web <xref:System.Web.UI.WebControls.Button> (strony `OnClick` sieci Web), która ma kontrolkę z wartością ustawioną na nazwę metody, którą zdefiniujesz w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="f4010-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="f4010-108">Zdefiniuj program <xref:System.Web.UI.WebControls.Button.Click> obsługi zdarzeń, który pasuje do podpisu delegata zdarzenia i który ma nazwę zdefiniowaną `OnClick` dla wartości.</span><span class="sxs-lookup"><span data-stu-id="f4010-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="f4010-109">Zdarzenie <xref:System.Web.UI.WebControls.Button.Click> używa <xref:System.EventHandler> klasy dla typu delegata <xref:System.EventArgs> i klasy dla danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f4010-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="f4010-110">Struktura ASP.NET strony automatycznie generuje kod, który <xref:System.EventHandler> tworzy wystąpienie i dodaje <xref:System.Web.UI.WebControls.Button.Click> to <xref:System.Web.UI.WebControls.Button> wystąpienie delegata do zdarzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f4010-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="f4010-111">W metodzie obsługi zdarzeń zdefiniowanej w kroku 2 dodaj kod, aby wykonać wszystkie akcje, które są wymagane w przypadku wystąpienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f4010-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4010-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4010-112">See also</span></span>

- [<span data-ttu-id="f4010-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f4010-113">Events</span></span>](../../../docs/standard/events/index.md)
