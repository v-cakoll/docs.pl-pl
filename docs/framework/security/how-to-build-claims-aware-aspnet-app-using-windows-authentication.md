---
title: "Porady: Tworzenie aplikacji ASP.NET obsługujący oświadczenia za pomocą uwierzytelniania systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 676a03678cbdf6fe08e628806df2a1853fb71718
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="fce6d-102">Porady: Tworzenie aplikacji ASP.NET obsługujący oświadczenia za pomocą uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fce6d-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="fce6d-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="fce6d-103">Applies To</span></span>  
  
-   <span data-ttu-id="fce6d-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="fce6d-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="fce6d-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="fce6d-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="fce6d-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="fce6d-106">Summary</span></span>  
 <span data-ttu-id="fce6d-107">Porada ten zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostego obsługujący oświadczenia aplikacji formularzy sieci Web ASP.NET, która używa uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fce6d-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="fce6d-108">Umożliwia także instrukcje dotyczące testowania aplikacji, aby zweryfikować, że oświadczenia są dostarczane, gdy użytkownik loguje się przy użyciu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fce6d-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="fce6d-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="fce6d-109">Contents</span></span>  
  
-   <span data-ttu-id="fce6d-110">Cele</span><span class="sxs-lookup"><span data-stu-id="fce6d-110">Objectives</span></span>  
  
-   <span data-ttu-id="fce6d-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="fce6d-111">Overview</span></span>  
  
-   <span data-ttu-id="fce6d-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="fce6d-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="fce6d-113">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="fce6d-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="fce6d-114">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fce6d-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="fce6d-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fce6d-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="fce6d-116">Cele</span><span class="sxs-lookup"><span data-stu-id="fce6d-116">Objectives</span></span>  
  
-   <span data-ttu-id="fce6d-117">Skonfigurować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fce6d-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="fce6d-118">Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa poprawnie</span><span class="sxs-lookup"><span data-stu-id="fce6d-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="fce6d-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="fce6d-119">Overview</span></span>  
 <span data-ttu-id="fce6d-120">W programie .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach struktury.</span><span class="sxs-lookup"><span data-stu-id="fce6d-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="fce6d-121">Wcześniej, jeśli chce oświadczenia przez użytkownika ASP.NET, możesz były wymagane do zainstalowania programu WIF, a następnie rzutowania interfejsy do podmiotu zabezpieczeń obiekty takie jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="fce6d-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="fce6d-122">Teraz oświadczenia są obsługiwane automatycznie przez głównych tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="fce6d-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="fce6d-123">Uwierzytelnianie systemu Windows uzyskał WIF jego włączenia w programie .NET 4.5, ponieważ wszyscy użytkownicy, uwierzytelniane przez poświadczenia systemu Windows automatycznie mają oświadczeń skojarzonych z nimi.</span><span class="sxs-lookup"><span data-stu-id="fce6d-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="fce6d-124">Aby rozpocząć, przy użyciu tych oświadczeń bezpośrednio w aplikacji ASP.NET, która używa uwierzytelniania systemu Windows, jak pokazano to instrukcje.</span><span class="sxs-lookup"><span data-stu-id="fce6d-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="fce6d-125">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="fce6d-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="fce6d-126">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="fce6d-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="fce6d-127">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fce6d-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="fce6d-128">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fce6d-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="fce6d-129">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="fce6d-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="fce6d-130">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="fce6d-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="fce6d-131">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fce6d-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="fce6d-132">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="fce6d-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="fce6d-133">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="fce6d-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="fce6d-134">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="fce6d-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="fce6d-135">Po **TestApp** projekt został utworzony, kliknij go w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fce6d-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="fce6d-136">Właściwości projektu będą wyświetlane w **właściwości** poniżej okienku **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fce6d-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="fce6d-137">Ustaw **uwierzytelniania systemu Windows** właściwości **włączone**.</span><span class="sxs-lookup"><span data-stu-id="fce6d-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="fce6d-138">Uwierzytelnianie systemu Windows jest domyślnie wyłączona w nowej aplikacji ASP.NET, dlatego należy ręcznie włączyć ją.</span><span class="sxs-lookup"><span data-stu-id="fce6d-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="fce6d-139">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fce6d-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="fce6d-140">W tym kroku spowoduje dodanie pozycji konfiguracji, aby *Web.config* konfiguracji plik i zmodyfikuj *Default.aspx* plik, aby wyświetlić oświadczeń informacji o koncie.</span><span class="sxs-lookup"><span data-stu-id="fce6d-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="fce6d-141">Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fce6d-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="fce6d-142">W **TestApp** projektu *Default.aspx* pliku, Zastąp istniejące znaczników następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="fce6d-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
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
  
     <span data-ttu-id="fce6d-143">Ten krok powoduje dodanie kontrolce GridView do Twojej *Default.aspx* strona, która zostanie wypełniona oświadczenia jest pobierana z uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fce6d-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2.  <span data-ttu-id="fce6d-144">Zapisz *Default.aspx* pliku, a następnie otwórz jego plik CodeBehind o nazwie *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="fce6d-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="fce6d-145">Zastąp istniejący kod poniżej:</span><span class="sxs-lookup"><span data-stu-id="fce6d-145">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="fce6d-146">Powyższy kod zostaną wyświetlone oświadczenia dotyczące uwierzytelnionego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fce6d-146">The above code will display claims about an authenticated user.</span></span>  
  
3.  <span data-ttu-id="fce6d-147">Aby zmienić typ uwierzytelniania aplikacji, należy zmodyfikować  **\<uwierzytelniania >** blok w  **\<system.web >** sekcji głównego projektu  *Plik Web.config* pliku co zawierają one tylko następujący wpis konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="fce6d-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  <span data-ttu-id="fce6d-148">Na koniec zmodyfikuj  **\<autoryzacji >** blok w  **\<system.web >** sekcji tego samego *Web.config* pliku, aby wymusić uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="fce6d-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="fce6d-149">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="fce6d-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="fce6d-150">W tym kroku zostanie testowania aplikacji formularzy sieci Web ASP.NET i sprawdź, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fce6d-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="fce6d-151">Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fce6d-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="fce6d-152">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fce6d-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="fce6d-153">Powinna pojawić się *Default.aspx*, a nazwa konta systemu Windows (łącznie z nazwą domeny) już powinny się wyświetlać jako użytkownik uwierzytelniony w górnym rogu strony.</span><span class="sxs-lookup"><span data-stu-id="fce6d-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="fce6d-154">Zawartość strony ma powinna zawierać tabelę wypełnione oświadczeń pobierane z konta systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fce6d-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
