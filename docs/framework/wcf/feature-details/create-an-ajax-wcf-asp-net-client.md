---
title: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET w programie Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: a6d6e87de6200a5cb9bba566d595066673cdf9cf
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834786"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="45148-102">Instrukcje: Tworzenie usługi WCF z włączoną obsługą technologii AJAX i klienta ASP.NET korzystającego z tej usługi</span><span class="sxs-lookup"><span data-stu-id="45148-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="45148-103">W tym temacie przedstawiono sposób użycia programu Visual Studio do utworzenia usługi Windows Communication Foundation (WCF) z włączoną obsługą technologii AJAX i klienta ASP.NET, który uzyskuje dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="45148-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="45148-104">Tworzenie aplikacji sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45148-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="45148-105">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45148-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="45148-106">Z menu **plik** wybierz pozycję **Nowy** > **projekt**</span><span class="sxs-lookup"><span data-stu-id="45148-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="45148-107">W oknie dialogowym **Nowy projekt** rozwiń kategorię **zainstalowaną**@no__t-**2 C#Visual**  >  dla**sieci Web** , a następnie wybierz pozycję **aplikacja sieci Web ASP.NET (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="45148-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="45148-108">Nadaj projektowi nazwę **SandwichServices** i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45148-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="45148-109">W oknie dialogowym **Nowa aplikacja sieci Web ASP.NET** wybierz opcję **pusty** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="45148-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Okno dialogowe typu aplikacji sieci Web ASP.NET w programie Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="45148-111">Dodawanie formularza sieci Web</span><span class="sxs-lookup"><span data-stu-id="45148-111">Add a web form</span></span>

1. <span data-ttu-id="45148-112">Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="45148-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="45148-113">W oknie dialogowym **Dodaj nowy element** rozwiń kategorię **zainstalowaną**@no__t-**2 C#Visual**  >  dla**sieci Web** , a następnie wybierz szablon **formularza sieci Web** .</span><span class="sxs-lookup"><span data-stu-id="45148-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="45148-114">Zaakceptuj nazwę domyślną (**WebForm1**), a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="45148-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="45148-115">W widoku **źródła** zostanie otwarty *formularz WebForm1. aspx* .</span><span class="sxs-lookup"><span data-stu-id="45148-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="45148-116">Dodaj następujący znacznik wewnątrz tagów **@no__t 1body >** :</span><span class="sxs-lookup"><span data-stu-id="45148-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="45148-117">Tworzenie usługi WCF z włączoną obsługą technologii AJAX</span><span class="sxs-lookup"><span data-stu-id="45148-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="45148-118">Kliknij prawym przyciskiem myszy projekt SandwichServices w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **nowy element**.</span><span class="sxs-lookup"><span data-stu-id="45148-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="45148-119">W oknie dialogowym **Dodaj nowy element** rozwiń kategorię **zainstalowaną**@no__t-**2 C#Visual**  >  dla**sieci Web** , a następnie wybierz szablon **usługi WCF (z włączoną obsługą technologii AJAX)** .</span><span class="sxs-lookup"><span data-stu-id="45148-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Szablon elementu usługi WCF (z obsługą technologii AJAX) w programie Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="45148-121">Nazwij usługę **CostService** , a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="45148-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="45148-122">*CostService.svc.cs* zostanie otwarty w edytorze.</span><span class="sxs-lookup"><span data-stu-id="45148-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="45148-123">Implementowanie operacji w usłudze.</span><span class="sxs-lookup"><span data-stu-id="45148-123">Implement the operation in the service.</span></span> <span data-ttu-id="45148-124">Dodaj następującą metodę do klasy CostService, aby obliczyć koszt ilości Sandwiches:</span><span class="sxs-lookup"><span data-stu-id="45148-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="45148-125">Konfigurowanie klienta do uzyskiwania dostępu do usługi</span><span class="sxs-lookup"><span data-stu-id="45148-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="45148-126">Otwórz plik *WebForm1. aspx* i wybierz widok **projekt** .</span><span class="sxs-lookup"><span data-stu-id="45148-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="45148-127">Z menu **Widok** wybierz pozycję **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="45148-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="45148-128">Rozwiń węzeł **rozszerzenia AJAX** i przeciągnij i upuść element **ScriptManager** do formularza.</span><span class="sxs-lookup"><span data-stu-id="45148-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="45148-129">W widoku **źródła** Dodaj następujący kod między tagami **\<ScriptManager >** , aby określić ścieżkę do usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="45148-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="45148-130">Dodaj kod dla funkcji JavaScript `Calculate()`.</span><span class="sxs-lookup"><span data-stu-id="45148-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="45148-131">Umieść poniższy kod w sekcji **nagłówka** formularza sieci Web:</span><span class="sxs-lookup"><span data-stu-id="45148-131">Place the following code in the **head** section of the web form:</span></span>

    ```html
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

   <span data-ttu-id="45148-132">Ten kod wywołuje metodę CostService w celu obliczenia ceny dla trzech Sandwiches, a następnie wyświetla wynik w zakresie o nazwie **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="45148-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="45148-133">Uruchom program</span><span class="sxs-lookup"><span data-stu-id="45148-133">Run the program</span></span>

<span data-ttu-id="45148-134">Upewnij się, że *WebForm1. aspx* ma fokus, a następnie naciśnij przycisk **Start** , aby uruchomić klienta sieci Web.</span><span class="sxs-lookup"><span data-stu-id="45148-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="45148-135">Przycisk ma zielony trójkąt i przypomina **IIS Express (Microsoft Edge)** .</span><span class="sxs-lookup"><span data-stu-id="45148-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="45148-136">Możesz też nacisnąć klawisz <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="45148-136">Or, you can press <kbd>F5</kbd>.</span></span> <span data-ttu-id="45148-137">Kliknij przycisk **Cena 3 Sandwiches** , aby wygenerować oczekiwane dane wyjściowe "3,75".</span><span class="sxs-lookup"><span data-stu-id="45148-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example"></a><span data-ttu-id="45148-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="45148-138">Example</span></span>

<span data-ttu-id="45148-139">Poniżej znajduje się pełny kod w pliku *CostService.svc.cs* :</span><span class="sxs-lookup"><span data-stu-id="45148-139">The following is the full code in the *CostService.svc.cs* file:</span></span>

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

<span data-ttu-id="45148-140">Poniżej znajduje się pełna zawartość strony *WebForm1. aspx* :</span><span class="sxs-lookup"><span data-stu-id="45148-140">The following is the full contents of the *WebForm1.aspx* page:</span></span>

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
