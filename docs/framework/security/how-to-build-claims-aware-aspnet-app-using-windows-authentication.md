---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows'
ms.date: 03/30/2017
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
author: BrucePerlerMS
ms.openlocfilehash: 34d6c7916b3035e9896b1dd9d7c7d8b3e7b0fcfc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040994"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="6744f-102">Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6744f-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>

## <a name="applies-to"></a><span data-ttu-id="6744f-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="6744f-103">Applies To</span></span>

- <span data-ttu-id="6744f-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="6744f-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="6744f-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="6744f-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="6744f-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="6744f-106">Summary</span></span>

<span data-ttu-id="6744f-107">Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms, która używa uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6744f-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="6744f-108">Zawiera również instrukcje dotyczące testowania aplikacji w celu sprawdzenia, czy oświadczenia są prezentowane, gdy użytkownik loguje się przy użyciu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6744f-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>

## <a name="contents"></a><span data-ttu-id="6744f-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="6744f-109">Contents</span></span>

- <span data-ttu-id="6744f-110">Cele</span><span class="sxs-lookup"><span data-stu-id="6744f-110">Objectives</span></span>

- <span data-ttu-id="6744f-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="6744f-111">Overview</span></span>

- <span data-ttu-id="6744f-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="6744f-112">Summary of Steps</span></span>

- <span data-ttu-id="6744f-113">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="6744f-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="6744f-114">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6744f-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

- <span data-ttu-id="6744f-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6744f-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="6744f-116">Cele</span><span class="sxs-lookup"><span data-stu-id="6744f-116">Objectives</span></span>

- <span data-ttu-id="6744f-117">Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6744f-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>

- <span data-ttu-id="6744f-118">Przetestuj aplikację ASP.NET Web Forms, aby sprawdzić, czy działa prawidłowo</span><span class="sxs-lookup"><span data-stu-id="6744f-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="6744f-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="6744f-119">Overview</span></span>

<span data-ttu-id="6744f-120">W programie .NET 4,5, WIF i Autoryzacja oparta na oświadczeniach została uwzględniona jako integralna część struktury.</span><span class="sxs-lookup"><span data-stu-id="6744f-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="6744f-121">Wcześniej, jeśli chcesz uzyskać oświadczenia od użytkownika ASP.NET, musisz zainstalować WIF, a następnie rzutować interfejsy na obiekty Principal, takie jak `Thread.CurrentPrincipal` lub. `HttpContext.Current.User`</span><span class="sxs-lookup"><span data-stu-id="6744f-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="6744f-122">Teraz oświadczenia są automatycznie obsługiwane przez te obiekty główne.</span><span class="sxs-lookup"><span data-stu-id="6744f-122">Now, claims are served automatically by these Principal objects.</span></span>

<span data-ttu-id="6744f-123">Uwierzytelnianie systemu Windows skorzystało z WIF w programie .NET 4,5, ponieważ wszyscy użytkownicy uwierzytelnieni przez poświadczenia systemu Windows automatycznie mają skojarzone z nimi oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="6744f-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="6744f-124">Możesz zacząć korzystać z tych oświadczeń natychmiast w aplikacji ASP.NET, która używa uwierzytelniania systemu Windows, jak pokazano na tej liście.</span><span class="sxs-lookup"><span data-stu-id="6744f-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="6744f-125">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="6744f-125">Summary of Steps</span></span>

- <span data-ttu-id="6744f-126">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="6744f-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="6744f-127">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6744f-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

- <span data-ttu-id="6744f-128">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6744f-128">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="6744f-129">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="6744f-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="6744f-130">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="6744f-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="6744f-131">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6744f-131">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="6744f-132">Uruchom program Visual Studio, a następnie kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.</span><span class="sxs-lookup"><span data-stu-id="6744f-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="6744f-133">W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="6744f-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="6744f-134">W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6744f-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

4. <span data-ttu-id="6744f-135">Po utworzeniu projektu **TestApp** kliknij go w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="6744f-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="6744f-136">Właściwości projektu zostaną wyświetlone w okienku **Właściwości** poniżej **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="6744f-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="6744f-137">Ustaw właściwość **uwierzytelnianie systemu Windows** na **włączone**.</span><span class="sxs-lookup"><span data-stu-id="6744f-137">Set the **Windows Authentication** property to **Enabled**.</span></span>

    > [!WARNING]
    > <span data-ttu-id="6744f-138">Uwierzytelnianie systemu Windows jest domyślnie wyłączone w nowych aplikacjach ASP.NET, więc należy je włączyć ręcznie.</span><span class="sxs-lookup"><span data-stu-id="6744f-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="6744f-139">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6744f-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>

<span data-ttu-id="6744f-140">W tym kroku dodasz wpis konfiguracyjny do pliku konfiguracji *Web. config* i zmodyfikujesz domyślny plik *. aspx* , aby wyświetlić informacje dotyczące oświadczeń dla konta.</span><span class="sxs-lookup"><span data-stu-id="6744f-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>

### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="6744f-141">Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6744f-141">To configure ASP.NET application for claims using Windows authentication</span></span>

1. <span data-ttu-id="6744f-142">W pliku *default. aspx* projektu **TestApp** Zastąp istniejący znacznik następującym:</span><span class="sxs-lookup"><span data-stu-id="6744f-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>

    ```aspx-csharp
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

    <span data-ttu-id="6744f-143">Ten krok powoduje dodanie kontrolki GridView do *domyślnej strony. aspx* , która zostanie uzupełniona o oświadczenia pobrane z uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6744f-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>

2. <span data-ttu-id="6744f-144">Zapisz plik *default. aspx* , a następnie otwórz jego plik związany z kodem o nazwie *default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="6744f-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="6744f-145">Zastąp istniejący kod następującym:</span><span class="sxs-lookup"><span data-stu-id="6744f-145">Replace the existing code with the following:</span></span>

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

    <span data-ttu-id="6744f-146">Powyższy kod będzie wyświetlał oświadczenia dotyczące uwierzytelnionego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6744f-146">The above code will display claims about an authenticated user.</span></span>

3. <span data-ttu-id="6744f-147">Aby zmienić typ uwierzytelniania aplikacji, należy zmodyfikować  **\<blok > uwierzytelniania** w sekcji  **\<> System. Web** w głównym pliku *Web. config* projektu, tak aby zawierał tylko następujące elementy: wpis konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="6744f-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>

    ```xml
    <authentication mode="Windows" />
    ```

4. <span data-ttu-id="6744f-148">Na koniec zmodyfikuj  **\<blok > autoryzacji** w  **\<sekcji > System. Web** w tym samym pliku *Web. config* , aby wymusić uwierzytelnianie:</span><span class="sxs-lookup"><span data-stu-id="6744f-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>

    ```xml
    <authorization>
        <deny users="?" />
    </authorization>
    ```

## <a name="step-3--test-your-solution"></a><span data-ttu-id="6744f-149">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6744f-149">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="6744f-150">W tym kroku nastąpi przetestowanie aplikacji ASP.NET Web Forms i sprawdzenie, czy oświadczenia są wyświetlane, gdy użytkownik loguje się przy użyciu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6744f-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="6744f-151">Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6744f-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>

1. <span data-ttu-id="6744f-152">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="6744f-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="6744f-153">Powinna zostać wyświetlona *wartość default. aspx*, a nazwa konta systemu Windows (w tym nazwa domeny) powinna już być wyświetlana jako uwierzytelniony użytkownik w prawym górnym rogu strony.</span><span class="sxs-lookup"><span data-stu-id="6744f-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="6744f-154">Zawartość strony powinna zawierać tabelę wypełnioną przez oświadczenia pobrane z konta systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6744f-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
