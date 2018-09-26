---
title: 'Instrukcje: Tworzenie aplikacji ASP.NET obsługującej oświadczenia przy użyciu uwierzytelniania opartego na formularzach'
ms.date: 03/30/2017
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
author: BrucePerlerMS
ms.openlocfilehash: 8dab5cfbcf14707699e6672017f5f80db232f01d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47110440"
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="e8eaf-102">Instrukcje: Tworzenie aplikacji ASP.NET obsługującej oświadczenia przy użyciu uwierzytelniania opartego na formularzach</span><span class="sxs-lookup"><span data-stu-id="e8eaf-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="e8eaf-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="e8eaf-103">Applies To</span></span>  
  
-   <span data-ttu-id="e8eaf-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e8eaf-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="e8eaf-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="e8eaf-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e8eaf-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="e8eaf-106">Summary</span></span>  
 <span data-ttu-id="e8eaf-107">Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia korzystającej z uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="e8eaf-108">On również instrukcje testowania aplikacji pozwalające sprawdzić, czy są prezentowane oświadczenia, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e8eaf-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="e8eaf-109">Contents</span></span>  
  
-   <span data-ttu-id="e8eaf-110">Cele</span><span class="sxs-lookup"><span data-stu-id="e8eaf-110">Objectives</span></span>  
  
-   <span data-ttu-id="e8eaf-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e8eaf-111">Overview</span></span>  
  
-   <span data-ttu-id="e8eaf-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="e8eaf-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e8eaf-113">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="e8eaf-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e8eaf-114">Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="e8eaf-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="e8eaf-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e8eaf-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="e8eaf-116">Cele</span><span class="sxs-lookup"><span data-stu-id="e8eaf-116">Objectives</span></span>  
  
-   <span data-ttu-id="e8eaf-117">Skonfigurować aplikację ASP.NET Web Forms pod kątem oświadczeń za pomocą uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="e8eaf-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="e8eaf-118">Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa prawidłowo</span><span class="sxs-lookup"><span data-stu-id="e8eaf-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e8eaf-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e8eaf-119">Overview</span></span>  
 <span data-ttu-id="e8eaf-120">W .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach Framework.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="e8eaf-121">Wcześniej, jeśli chce oświadczeń użytkownika ASP.NET należało do zainstalowania programu WIF, i następnie rzutowania interfejsy z podmiotem zabezpieczeń obiektów takich jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="e8eaf-122">Obecnie oświadczeń są obsługiwane automatycznie przez te jednostki obiektów.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="e8eaf-123">Uwierzytelnianie formularzy skorzystał z włączenia programu WIF w .NET 4.5, ponieważ wszyscy użytkownicy uwierzytelnieni przez formularze automatycznie oświadczenia skojarzone z nimi.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="e8eaf-124">Możesz rozpocząć korzystanie z tych oświadczeń bezpośrednio w aplikacji ASP.NET, która korzysta z uwierzytelniania formularzy, tak jak pokazano w tym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e8eaf-125">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="e8eaf-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e8eaf-126">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="e8eaf-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e8eaf-127">Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="e8eaf-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="e8eaf-128">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e8eaf-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="e8eaf-129">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="e8eaf-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="e8eaf-130">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e8eaf-131">Aby utworzyć prostą aplikację platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e8eaf-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="e8eaf-132">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="e8eaf-133">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="e8eaf-134">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e8eaf-135">Krok 2 — Konfigurowanie aplikacji ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="e8eaf-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="e8eaf-136">W tym kroku dodasz wpis konfiguracyjny do *Web.config* pliku konfiguracji i Edytuj *Default.aspx* plik, aby wyświetlić oświadczenia informacji o koncie.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e8eaf-137">Aby skonfigurować aplikację ASP.NET dla oświadczeń za pomocą uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="e8eaf-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="e8eaf-138">W *Default.aspx* pliku, Zastąp istniejący kod znaczników następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="e8eaf-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="e8eaf-139">Ten krok powoduje dodanie kontrolki widoku siatki do Twojej *Default.aspx* strony, który zostanie wypełniony oświadczenia jest pobierana z uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="e8eaf-140">Zapisz *Default.aspx* pliku, a następnie otwórz jego pliku związanego z kodem o nazwie *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="e8eaf-141">Zastąp istniejący kod następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="e8eaf-141">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="e8eaf-142">Powyższy kod wyświetli oświadczenia dotyczące uwierzytelnionego użytkownika, w tym użytkowników identyfikowanych na podstawie uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="e8eaf-143">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e8eaf-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="e8eaf-144">W tym kroku zostanie testowanie aplikacji ASP.NET Web Forms i sprawdź, czy są prezentowane oświadczenia, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e8eaf-145">Aby przetestować aplikację ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="e8eaf-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="e8eaf-146">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="e8eaf-147">Powinna pojawić się *Default.aspx*, który ma **zarejestrować** i **Zaloguj się** łącza w prawym górnym rogu strony.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="e8eaf-148">Kliknij przycisk **zarejestrować**.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="e8eaf-149">Na **zarejestrować** strony, Utwórz konto użytkownika, a następnie kliknij przycisk **zarejestrować**.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="e8eaf-150">Twoje konto zostanie utworzone za pomocą uwierzytelniania formularzy, a użytkownik zostanie automatycznie zalogowany.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="e8eaf-151">Po nastąpiło przekierowanie do strony głównej, powinien zostać wyświetlony tabelę poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacji o Twoim koncie.</span><span class="sxs-lookup"><span data-stu-id="e8eaf-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
