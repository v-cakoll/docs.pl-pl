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
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="b55e3-102">Instrukcje: Korzystanie ze zdarzeń w aplikacjach formularzy internetowych</span><span class="sxs-lookup"><span data-stu-id="b55e3-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="b55e3-103">Jest to częsty przypadek w aplikacji formularzy sieci Web programu ASP.NET do wypełniania strony sieci Web za pomocą kontrolek, a następnie wykonać określonej akcji, które kontrolują użytkownik klika polecenie w oparciu.</span><span class="sxs-lookup"><span data-stu-id="b55e3-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="b55e3-104">Na przykład <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> kontrolki wywołuje zdarzenie po kliknięciu przez użytkownika na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b55e3-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="b55e3-105">Dzięki obsłudze zdarzenia, aplikację można wykonać logiki aplikacji odpowiednie dla tego kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="b55e3-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="b55e3-106">Aby obsługiwać przycisk Kliknij zdarzenie na stronie sieci Web</span><span class="sxs-lookup"><span data-stu-id="b55e3-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="b55e3-107">Tworzenie strony formularzy sieci Web platformy ASP.NET (strona sieci Web), który ma <xref:System.Web.UI.WebControls.Button> kontrolką `OnClick` wartość ustawiona na nazwę metody definiującej w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="b55e3-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="b55e3-108">Definiowanie obsługi zdarzeń, który odpowiada <xref:System.Web.UI.WebControls.Button.Click> podpis delegata zdarzenia i który ma nazwę zdefiniowaną dla `OnClick` wartość.</span><span class="sxs-lookup"><span data-stu-id="b55e3-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="b55e3-109"><xref:System.Web.UI.WebControls.Button.Click> Zdarzeń używa <xref:System.EventHandler> klasy dla typu delegata i <xref:System.EventArgs> klasy danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b55e3-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="b55e3-110">Architektura strony ASP.NET automatycznie generuje kod, który tworzy wystąpienie <xref:System.EventHandler> i dodaje tego wystąpienia delegata <xref:System.Web.UI.WebControls.Button.Click> zdarzenia <xref:System.Web.UI.WebControls.Button> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b55e3-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="b55e3-111">W przypadku metody obsługi, który został zdefiniowany w kroku 2, Dodaj kod, aby wykonywać żadnych akcji, które są wymagane, gdy wystąpi zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b55e3-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55e3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b55e3-112">See also</span></span>

- [<span data-ttu-id="b55e3-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b55e3-113">Events</span></span>](../../../docs/standard/events/index.md)
