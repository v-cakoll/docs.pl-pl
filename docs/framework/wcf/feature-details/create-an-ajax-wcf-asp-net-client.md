---
title: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET w programie Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454318"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="22283-102">Instrukcje: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET korzystającego z tej usługi</span><span class="sxs-lookup"><span data-stu-id="22283-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="22283-103">W tym temacie pokazano, jak używać programu Visual Studio do tworzenia usługi z włączoną obsługą technologii AJAX Windows Communication Foundation (WCF) i kliencie programu ASP.NET, który uzyskuje dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="22283-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="22283-104">Tworzenie aplikacji sieci web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="22283-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="22283-105">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22283-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="22283-106">Z **pliku** menu, wybierz opcję **New** > **projektu**</span><span class="sxs-lookup"><span data-stu-id="22283-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="22283-107">W **nowy projekt** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** > **Web** kategorii, a następnie Wybierz **aplikacji sieci Web platformy ASP.NET (.NET Framework)**.</span><span class="sxs-lookup"><span data-stu-id="22283-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="22283-108">Nadaj projektowi nazwę **SandwichServices** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="22283-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="22283-109">W **Nowa aplikacja internetowa ASP.NET** okno dialogowe, wybierz opcję **pusty** , a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="22283-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Okno dialogowe typu aplikacji sieci web platformy ASP.NET w programie Visual Studio](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="22283-111">Dodaj formularz sieci web</span><span class="sxs-lookup"><span data-stu-id="22283-111">Add a web form</span></span>

1. <span data-ttu-id="22283-112">Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="22283-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="22283-113">W **Dodaj nowy element** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** > **Web** kategorii, a następnie Wybierz **formularz sieci Web** szablonu.</span><span class="sxs-lookup"><span data-stu-id="22283-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="22283-114">Zaakceptuj nazwę domyślną (**WebForm1**), a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="22283-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="22283-115">*WebForm1.aspx* zostanie otwarty w **źródła** widoku.</span><span class="sxs-lookup"><span data-stu-id="22283-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="22283-116">Dodaj następujący kod wewnątrz  **\<treści >** tagi:</span><span class="sxs-lookup"><span data-stu-id="22283-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="22283-117">Tworzenie usługi WCF z włączoną obsługą technologii AJAX</span><span class="sxs-lookup"><span data-stu-id="22283-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="22283-118">Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="22283-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="22283-119">W **Dodaj nowy element** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** > **Web** kategorii, a następnie Wybierz **usługi WCF (włączoną obsługą technologii AJAX)** szablonu.</span><span class="sxs-lookup"><span data-stu-id="22283-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Szablon elementu (włączoną obsługą technologii AJAX) usługi WCF w programie Visual Studio](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="22283-121">Nazwij usługę **CostService** , a następnie wybierz **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="22283-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="22283-122">*CostService.svc.cs* zostanie otwarty w edytorze.</span><span class="sxs-lookup"><span data-stu-id="22283-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="22283-123">Implementowanie operacji w usłudze.</span><span class="sxs-lookup"><span data-stu-id="22283-123">Implement the operation in the service.</span></span> <span data-ttu-id="22283-124">Dodaj następującą metodę do klasy CostService, aby obliczyć koszt ilość kanapki:</span><span class="sxs-lookup"><span data-stu-id="22283-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="22283-125">Konfigurowanie klienta do uzyskania dostępu do usługi</span><span class="sxs-lookup"><span data-stu-id="22283-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="22283-126">Otwórz *WebForm1.aspx* plik i wybierz **projektowania** widoku.</span><span class="sxs-lookup"><span data-stu-id="22283-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="22283-127">Z **widoku** menu, wybierz opcję **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="22283-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="22283-128">Rozwiń **rozszerzenia AJAX** węzła i przeciągania i upuszczania **ScriptManager** na formularz.</span><span class="sxs-lookup"><span data-stu-id="22283-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="22283-129">Ponownie **źródła** wyświetlanie, Dodaj następujący kod między  **\<ScriptManager >** tagów, aby określić ścieżkę do usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="22283-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. <span data-ttu-id="22283-130">Dodaj kod dla funkcji języka Javascript `Calculate()`.</span><span class="sxs-lookup"><span data-stu-id="22283-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="22283-131">Umieść następujący kod w **head** części formularza sieci web:</span><span class="sxs-lookup"><span data-stu-id="22283-131">Place the following code in the **head** section of the web form:</span></span>

    ```javascript
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   <span data-ttu-id="22283-132">Ten kod wywołuje metodę CostService do obliczania ceny dla trzech kanapki, a następnie wyświetla wynik w zakresie o nazwie **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="22283-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="22283-133">Uruchom program</span><span class="sxs-lookup"><span data-stu-id="22283-133">Run the program</span></span>

<span data-ttu-id="22283-134">Upewnij się, że *WebForm1.aspx* ma fokus, a następnie naciśnij klawisz **Start** przycisk, aby uruchomić klienta sieci web.</span><span class="sxs-lookup"><span data-stu-id="22283-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="22283-135">Ten przycisk ma zielony trójkąt i jest wyświetlany komunikat podobny do **usług IIS Express (Microsoft Edge)**.</span><span class="sxs-lookup"><span data-stu-id="22283-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="22283-136">Lub możesz nacisnąć przycisk **F5**.</span><span class="sxs-lookup"><span data-stu-id="22283-136">Or, you can press **F5**.</span></span> <span data-ttu-id="22283-137">Kliknij przycisk **cena 3 kanapki** przycisk, aby wygenerować oczekiwane dane wyjściowe "3,75".</span><span class="sxs-lookup"><span data-stu-id="22283-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example-code"></a><span data-ttu-id="22283-138">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="22283-138">Example code</span></span>

<span data-ttu-id="22283-139">Oto pełny kod w *CostService.svc.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="22283-139">Following is the full code in the *CostService.svc.cs* file :</span></span>

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

<span data-ttu-id="22283-140">Poniżej znajduje się pełna zawartość *WebForm1.aspx* strony:</span><span class="sxs-lookup"><span data-stu-id="22283-140">Following is the full contents of the *WebForm1.aspx* page:</span></span>

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
