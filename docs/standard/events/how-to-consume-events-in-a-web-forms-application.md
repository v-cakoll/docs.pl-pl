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
ms.openlocfilehash: 3490b6fb89bfe6d7ac778078f58381bb5172e2fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288488"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="ec479-102">Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="ec479-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="ec479-103">Typowy scenariusz w aplikacjach formularzy sieci Web ASP.NET to wypełnienie strony sieci Web z kontrolkami, a następnie wykonanie konkretnej akcji na podstawie tego, która kontrolka klika użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ec479-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="ec479-104">Na przykład <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> kontrolka wywołuje zdarzenie, gdy użytkownik kliknie go na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ec479-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="ec479-105">Dzięki obsłudze zdarzenia, aplikacja może wykonać odpowiednią logikę aplikacji dla tego przycisku.</span><span class="sxs-lookup"><span data-stu-id="ec479-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="ec479-106">Aby obsługiwać przycisk Kliknij zdarzenie na stronie sieci Web</span><span class="sxs-lookup"><span data-stu-id="ec479-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="ec479-107">Utwórz stronę formularzy sieci Web ASP.NET (Web), która ma <xref:System.Web.UI.WebControls.Button> kontrolkę z `OnClick` wartością ustawioną na nazwę metody, która zostanie zdefiniowana w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="ec479-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="ec479-108">Zdefiniuj procedurę obsługi zdarzeń, która pasuje do <xref:System.Web.UI.WebControls.Button.Click> sygnatury delegata zdarzenia i ma nazwę zdefiniowaną dla tej `OnClick` wartości.</span><span class="sxs-lookup"><span data-stu-id="ec479-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="ec479-109"><xref:System.Web.UI.WebControls.Button.Click>Zdarzenie używa <xref:System.EventHandler> klasy dla typu delegata i <xref:System.EventArgs> klasy dla danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ec479-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="ec479-110">Struktura strony ASP.NET automatycznie generuje kod, który tworzy wystąpienie klasy <xref:System.EventHandler> i dodaje to wystąpienie delegata do <xref:System.Web.UI.WebControls.Button.Click> zdarzenia <xref:System.Web.UI.WebControls.Button> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ec479-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="ec479-111">W metodzie obsługi zdarzeń zdefiniowanej w kroku 2 Dodaj kod, aby wykonać wszelkie akcje, które są wymagane w przypadku wystąpienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ec479-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec479-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec479-112">See also</span></span>

- [<span data-ttu-id="ec479-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ec479-113">Events</span></span>](index.md)
