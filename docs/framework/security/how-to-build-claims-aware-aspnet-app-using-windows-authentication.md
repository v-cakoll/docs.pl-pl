---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 48b1b4715e9e2613757a981ba692d84ad06a1ec6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767971"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="5186c-102">Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5186c-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="5186c-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="5186c-103">Applies To</span></span>  
  
-   <span data-ttu-id="5186c-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="5186c-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="5186c-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="5186c-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="5186c-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="5186c-106">Summary</span></span>  
 <span data-ttu-id="5186c-107">Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia korzystającej z uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5186c-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="5186c-108">On również instrukcje testowania aplikacji pozwalające sprawdzić, czy są prezentowane oświadczenia, gdy użytkownik loguje się przy użyciu uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5186c-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="5186c-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="5186c-109">Contents</span></span>  
  
-   <span data-ttu-id="5186c-110">Cele</span><span class="sxs-lookup"><span data-stu-id="5186c-110">Objectives</span></span>  
  
-   <span data-ttu-id="5186c-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="5186c-111">Overview</span></span>  
  
-   <span data-ttu-id="5186c-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="5186c-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="5186c-113">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="5186c-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="5186c-114">Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows</span><span class="sxs-lookup"><span data-stu-id="5186c-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="5186c-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5186c-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="5186c-116">Cele</span><span class="sxs-lookup"><span data-stu-id="5186c-116">Objectives</span></span>  
  
-   <span data-ttu-id="5186c-117">Skonfigurować aplikację ASP.NET Web Forms pod kątem oświadczeń przy użyciu uwierzytelniania Windows</span><span class="sxs-lookup"><span data-stu-id="5186c-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="5186c-118">Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa prawidłowo</span><span class="sxs-lookup"><span data-stu-id="5186c-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5186c-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="5186c-119">Overview</span></span>  
 <span data-ttu-id="5186c-120">W .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach Framework.</span><span class="sxs-lookup"><span data-stu-id="5186c-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="5186c-121">Wcześniej, jeśli chce oświadczeń użytkownika ASP.NET należało do zainstalowania programu WIF, i następnie rzutowania interfejsy z podmiotem zabezpieczeń obiektów takich jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="5186c-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="5186c-122">Obecnie oświadczeń są obsługiwane automatycznie przez te jednostki obiektów.</span><span class="sxs-lookup"><span data-stu-id="5186c-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="5186c-123">Uwierzytelnianie Windows skorzystał z włączenia programu WIF w .NET 4.5, ponieważ wszyscy użytkownicy uwierzytelnieni poświadczenia Windows automatycznie oświadczenia skojarzone z nimi.</span><span class="sxs-lookup"><span data-stu-id="5186c-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="5186c-124">Możesz rozpocząć korzystanie z tych oświadczeń bezpośrednio w aplikacji ASP.NET, która korzysta z uwierzytelniania Windows, tak jak pokazano w tym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="5186c-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="5186c-125">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="5186c-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="5186c-126">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="5186c-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="5186c-127">Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows</span><span class="sxs-lookup"><span data-stu-id="5186c-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="5186c-128">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5186c-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="5186c-129">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="5186c-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="5186c-130">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="5186c-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="5186c-131">Aby utworzyć prostą aplikację platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5186c-131">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="5186c-132">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="5186c-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="5186c-133">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="5186c-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="5186c-134">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="5186c-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="5186c-135">Po **TestApp** został utworzony projekt, kliknij go w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="5186c-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="5186c-136">Właściwości projektu, pojawi się w **właściwości** okienku poniżej **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="5186c-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="5186c-137">Ustaw **uwierzytelniania Windows** właściwości **włączone**.</span><span class="sxs-lookup"><span data-stu-id="5186c-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="5186c-138">Uwierzytelnianie Windows jest domyślnie wyłączona, w nowej aplikacji ASP.NET, więc musisz ręcznie włączyć ją.</span><span class="sxs-lookup"><span data-stu-id="5186c-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="5186c-139">Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows</span><span class="sxs-lookup"><span data-stu-id="5186c-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="5186c-140">W tym kroku dodasz wpis konfiguracyjny do *Web.config* konfiguracji plik i Modyfikuj *Default.aspx* plik, aby wyświetlić oświadczenia informacji o koncie.</span><span class="sxs-lookup"><span data-stu-id="5186c-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="5186c-141">Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania Windows</span><span class="sxs-lookup"><span data-stu-id="5186c-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1. <span data-ttu-id="5186c-142">W **TestApp** projektu *Default.aspx* pliku, Zastąp istniejący kod znaczników następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5186c-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     <span data-ttu-id="5186c-143">Ten krok powoduje dodanie kontrolki widoku siatki do Twojej *Default.aspx* strony, który zostanie wypełniony oświadczenia jest pobierana z uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5186c-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2. <span data-ttu-id="5186c-144">Zapisz *Default.aspx* pliku, a następnie otwórz jego pliku związanego z kodem o nazwie *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="5186c-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="5186c-145">Zastąp istniejący kod następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5186c-145">Replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="5186c-146">Powyższy kod wyświetli oświadczenia dotyczące uwierzytelnionego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5186c-146">The above code will display claims about an authenticated user.</span></span>  
  
3. <span data-ttu-id="5186c-147">Aby zmienić typ uwierzytelniania aplikacji, należy zmodyfikować  **\<uwierzytelniania >** bloku  **\<system.web >** sekcji katalog główny projektu  *Plik Web.config* plik zawiera tylko następujący wpis konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="5186c-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4. <span data-ttu-id="5186c-148">Na koniec zmodyfikuj  **\<autoryzacji >** bloku  **\<system.web >** sekcji tego samego *Web.config* plik, aby wymusić uwierzytelnianie:</span><span class="sxs-lookup"><span data-stu-id="5186c-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="5186c-149">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5186c-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="5186c-150">W tym kroku zostanie testowanie aplikacji ASP.NET Web Forms i sprawdź, czy są prezentowane oświadczenia, gdy użytkownik loguje się przy użyciu uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5186c-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="5186c-151">Aby przetestować aplikację ASP.NET Web Forms oświadczenia przy użyciu uwierzytelniania Windows</span><span class="sxs-lookup"><span data-stu-id="5186c-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1. <span data-ttu-id="5186c-152">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5186c-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="5186c-153">Powinna pojawić się *Default.aspx*, i nazwę konta Windows (łącznie z nazwą domeny) już powinna zostać wyświetlona jako użytkownik uwierzytelniony w prawym górnym rogu strony.</span><span class="sxs-lookup"><span data-stu-id="5186c-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="5186c-154">Zawartość strony powinna zawierać tabelę wypełnione oświadczeń pobierane z konta usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="5186c-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
