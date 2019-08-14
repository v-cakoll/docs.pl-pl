---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania opartego na formularzach'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 75db96a621d7863ef445efb24814111b34da6960
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971835"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="de9e6-102">Instrukcje: Tworzenie obsługującej oświadczenia aplikacji ASP.NET przy użyciu uwierzytelniania opartego na formularzach</span><span class="sxs-lookup"><span data-stu-id="de9e6-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>

## <a name="applies-to"></a><span data-ttu-id="de9e6-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="de9e6-103">Applies To</span></span>

- <span data-ttu-id="de9e6-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="de9e6-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="de9e6-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="de9e6-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="de9e6-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="de9e6-106">Summary</span></span>

<span data-ttu-id="de9e6-107">Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms, która korzysta z uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="de9e6-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="de9e6-108">Zawiera również instrukcje dotyczące testowania aplikacji w celu sprawdzenia, czy oświadczenia są prezentowane, gdy użytkownik loguje się przy użyciu uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="de9e6-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>

## <a name="contents"></a><span data-ttu-id="de9e6-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="de9e6-109">Contents</span></span>

- <span data-ttu-id="de9e6-110">Cele</span><span class="sxs-lookup"><span data-stu-id="de9e6-110">Objectives</span></span>

- <span data-ttu-id="de9e6-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="de9e6-111">Overview</span></span>

- <span data-ttu-id="de9e6-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="de9e6-112">Summary of Steps</span></span>

- <span data-ttu-id="de9e6-113">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="de9e6-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="de9e6-114">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="de9e6-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

- <span data-ttu-id="de9e6-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="de9e6-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="de9e6-116">Cele</span><span class="sxs-lookup"><span data-stu-id="de9e6-116">Objectives</span></span>

- <span data-ttu-id="de9e6-117">Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="de9e6-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>

- <span data-ttu-id="de9e6-118">Przetestuj aplikację ASP.NET Web Forms, aby sprawdzić, czy działa prawidłowo</span><span class="sxs-lookup"><span data-stu-id="de9e6-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="de9e6-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="de9e6-119">Overview</span></span>

<span data-ttu-id="de9e6-120">W programie .NET 4,5, WIF i Autoryzacja oparta na oświadczeniach została uwzględniona jako integralna część struktury.</span><span class="sxs-lookup"><span data-stu-id="de9e6-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="de9e6-121">Wcześniej, jeśli chcesz uzyskać oświadczenia od użytkownika ASP.NET, musisz zainstalować WIF, a następnie rzutować interfejsy na obiekty Principal, takie jak `Thread.CurrentPrincipal` lub. `HttpContext.Current.User`</span><span class="sxs-lookup"><span data-stu-id="de9e6-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="de9e6-122">Teraz oświadczenia są automatycznie obsługiwane przez te obiekty główne.</span><span class="sxs-lookup"><span data-stu-id="de9e6-122">Now, claims are served automatically by these Principal objects.</span></span>

<span data-ttu-id="de9e6-123">Uwierzytelnianie formularzy zostało korzystne z uwzględnieniem WIF w programie .NET 4,5, ponieważ wszyscy użytkownicy uwierzytelnieni przez formularze automatycznie mają skojarzone z nimi oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="de9e6-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="de9e6-124">Możesz zacząć korzystać z tych oświadczeń natychmiast w aplikacji ASP.NET, która korzysta z uwierzytelniania formularzy, jak pokazano na tej liście.</span><span class="sxs-lookup"><span data-stu-id="de9e6-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="de9e6-125">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="de9e6-125">Summary of Steps</span></span>

- <span data-ttu-id="de9e6-126">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="de9e6-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="de9e6-127">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="de9e6-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

- <span data-ttu-id="de9e6-128">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="de9e6-128">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="de9e6-129">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="de9e6-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="de9e6-130">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="de9e6-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="de9e6-131">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="de9e6-131">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="de9e6-132">Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.</span><span class="sxs-lookup"><span data-stu-id="de9e6-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="de9e6-133">W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="de9e6-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="de9e6-134">W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="de9e6-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="de9e6-135">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="de9e6-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>

<span data-ttu-id="de9e6-136">W tym kroku dodasz wpis konfiguracyjny do pliku konfiguracji *Web. config* i edytujesz domyślny plik *. aspx* , aby wyświetlić informacje dotyczące oświadczeń dla konta.</span><span class="sxs-lookup"><span data-stu-id="de9e6-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>

### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="de9e6-137">Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="de9e6-137">To configure ASP.NET application for claims using Forms authentication</span></span>

1. <span data-ttu-id="de9e6-138">W pliku *default. aspx* Zastąp istniejący znacznik następującym:</span><span class="sxs-lookup"><span data-stu-id="de9e6-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>

    ```aspx
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>

    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">
        <p>
            This page displays the claims associated with a Forms authenticated user.
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

    <span data-ttu-id="de9e6-139">Ten krok powoduje dodanie kontrolki GridView do *domyślnej strony. aspx* , która zostanie uzupełniona o oświadczenia pobrane z uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="de9e6-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>

2. <span data-ttu-id="de9e6-140">Zapisz plik *default. aspx* , a następnie otwórz jego plik związany z kodem o nazwie *default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="de9e6-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="de9e6-141">Zastąp istniejący kod następującym:</span><span class="sxs-lookup"><span data-stu-id="de9e6-141">Replace the existing code with the following:</span></span>

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

                if (claimsPrincipal != null)
                {
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;
                    this.ClaimsGridView.DataBind();
                }
            }
        }
    }
    ```

    <span data-ttu-id="de9e6-142">Powyższy kod będzie wyświetlał oświadczenia dotyczące uwierzytelnionego użytkownika, w tym użytkowników zidentyfikowanych przez uwierzytelnianie formularzy.</span><span class="sxs-lookup"><span data-stu-id="de9e6-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>

## <a name="step-3--test-your-solution"></a><span data-ttu-id="de9e6-143">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="de9e6-143">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="de9e6-144">W tym kroku nastąpi przetestowanie aplikacji ASP.NET Web Forms i sprawdzenie, czy oświadczenia są wyświetlane, gdy użytkownik loguje się przy użyciu uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="de9e6-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>

### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="de9e6-145">Aby przetestować aplikację formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="de9e6-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>

1. <span data-ttu-id="de9e6-146">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="de9e6-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="de9e6-147">Powinna zostać wyświetlona *wartość default. aspx*, która zawiera linki **register** i **log** in w prawym górnym rogu strony.</span><span class="sxs-lookup"><span data-stu-id="de9e6-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="de9e6-148">Kliknij pozycję **zarejestruj**.</span><span class="sxs-lookup"><span data-stu-id="de9e6-148">Click **Register**.</span></span>

2. <span data-ttu-id="de9e6-149">Na stronie **Rejestr** Utwórz konto użytkownika, a następnie kliknij przycisk **zarejestruj**.</span><span class="sxs-lookup"><span data-stu-id="de9e6-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="de9e6-150">Twoje konto zostanie utworzone przy użyciu uwierzytelniania formularzy, a użytkownik zostanie automatycznie zalogowany.</span><span class="sxs-lookup"><span data-stu-id="de9e6-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>

3. <span data-ttu-id="de9e6-151">Po przekierowaniu do strony głównej powinna zostać wyświetlona tabela poniżej nagłówka **oświadczeń** , która zawiera informacje o wystawcy, **OriginalIssuer**, **Typ**, **wartość**i element **ValueType** oświadczenia dotyczące koncie.</span><span class="sxs-lookup"><span data-stu-id="de9e6-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
