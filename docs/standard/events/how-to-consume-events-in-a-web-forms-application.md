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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b8af7b3894c010d5a7a4c712efe2458a6bb2a50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571077"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="e646c-102">Porady: korzystanie ze zdarzeń w aplikacjach formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="e646c-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="e646c-103">Typowy scenariusz w aplikacji formularzy sieci Web programu ASP.NET jest wypełnienie strony sieci Web z formantami, a następnie wykonywać konkretną akcję, w oparciu o który kontroli, użytkownik klika polecenie.</span><span class="sxs-lookup"><span data-stu-id="e646c-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="e646c-104">Na przykład <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> kontroli wywołuje zdarzenie po kliknięciu przez użytkownika na stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e646c-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="e646c-105">Dzięki obsłudze zdarzenia, aplikacja może wykonywać logiki aplikacji dla tego kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="e646c-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="e646c-106">Aby obsługiwać przycisk Kliknij zdarzenie na stronie sieci Web</span><span class="sxs-lookup"><span data-stu-id="e646c-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="e646c-107">Tworzenie strony formularzy sieci Web ASP.NET (strona sieci Web), który ma <xref:System.Web.UI.WebControls.Button> sterować za pomocą `OnClick` wartość ustawiona na nazwę metody, który będzie definiował w następnym kroku.</span><span class="sxs-lookup"><span data-stu-id="e646c-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="e646c-108">Definiowanie procedury obsługi zdarzeń, odpowiadający <xref:System.Web.UI.WebControls.Button.Click> podpisu delegata zdarzenia i że ma nazwę zdefiniowane dla `OnClick` wartość.</span><span class="sxs-lookup"><span data-stu-id="e646c-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="e646c-109"><xref:System.Web.UI.WebControls.Button.Click> Używa zdarzeń <xref:System.EventHandler> klasy dla typu delegata i <xref:System.EventArgs> klasy danych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e646c-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="e646c-110">Architekturę stron ASP.NET jest automatycznie generuje kod, który tworzy wystąpienie <xref:System.EventHandler> i dodanie tego wystąpienia obiektu delegowanego <xref:System.Web.UI.WebControls.Button.Click> zdarzenie <xref:System.Web.UI.WebControls.Button> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e646c-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="e646c-111">W przypadku metoda obsługi, który został zdefiniowany w kroku 2, Dodaj kod, aby wykonać wszystkie akcje, które są wymagane w przypadku wystąpienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e646c-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e646c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e646c-112">See Also</span></span>  
 [<span data-ttu-id="e646c-113">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e646c-113">Events</span></span>](../../../docs/standard/events/index.md)
