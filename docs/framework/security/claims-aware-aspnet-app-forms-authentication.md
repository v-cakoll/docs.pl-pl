---
title: "Porady: Tworzenie aplikacji obsługującej oświadczenia ASP.NET przy użyciu uwierzytelniania opartego na formularzach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 987157bc3663330d9c610c1016787890e9dc6137
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="47cb6-102">Porady: Tworzenie aplikacji obsługującej oświadczenia ASP.NET przy użyciu uwierzytelniania opartego na formularzach</span><span class="sxs-lookup"><span data-stu-id="47cb6-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="47cb6-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="47cb6-103">Applies To</span></span>  
  
-   <span data-ttu-id="47cb6-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="47cb6-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="47cb6-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="47cb6-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="47cb6-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="47cb6-106">Summary</span></span>  
 <span data-ttu-id="47cb6-107">Ta porada zawiera szczegółowe procedury krok po kroku dotyczące tworzenia proste obsługujący oświadczenia aplikacji formularzy sieci Web ASP.NET, która korzysta z uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="47cb6-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="47cb6-108">Umożliwia także instrukcje dotyczące testowania aplikacji, aby zweryfikować, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="47cb6-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="47cb6-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="47cb6-109">Contents</span></span>  
  
-   <span data-ttu-id="47cb6-110">Cele</span><span class="sxs-lookup"><span data-stu-id="47cb6-110">Objectives</span></span>  
  
-   <span data-ttu-id="47cb6-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="47cb6-111">Overview</span></span>  
  
-   <span data-ttu-id="47cb6-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="47cb6-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="47cb6-113">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="47cb6-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="47cb6-114">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="47cb6-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="47cb6-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="47cb6-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="47cb6-116">Cele</span><span class="sxs-lookup"><span data-stu-id="47cb6-116">Objectives</span></span>  
  
-   <span data-ttu-id="47cb6-117">Skonfigurować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="47cb6-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="47cb6-118">Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa poprawnie</span><span class="sxs-lookup"><span data-stu-id="47cb6-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="47cb6-119">Omówienie</span><span class="sxs-lookup"><span data-stu-id="47cb6-119">Overview</span></span>  
 <span data-ttu-id="47cb6-120">W programie .NET 4.5 WIF i jego autoryzacji opartej na oświadczeniach zostały uwzględnione w ramach struktury.</span><span class="sxs-lookup"><span data-stu-id="47cb6-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="47cb6-121">Wcześniej, jeśli chce oświadczenia przez użytkownika ASP.NET, możesz były wymagane do zainstalowania programu WIF, a następnie rzutowania interfejsy do podmiotu zabezpieczeń obiekty takie jak `Thread.CurrentPrincipal` lub `HttpContext.Current.User`.</span><span class="sxs-lookup"><span data-stu-id="47cb6-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="47cb6-122">Teraz oświadczenia są obsługiwane automatycznie przez głównych tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="47cb6-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="47cb6-123">Uwierzytelnianie formularzy uzyskał WIF jego włączenia w programie .NET 4.5, ponieważ wszyscy użytkownicy uwierzytelnieni przez formularze automatycznie oświadczeń skojarzonych z nimi.</span><span class="sxs-lookup"><span data-stu-id="47cb6-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="47cb6-124">Aby rozpocząć, przy użyciu tych oświadczeń bezpośrednio w aplikacji ASP.NET, która korzysta z uwierzytelniania formularzy, jak pokazano to instrukcje.</span><span class="sxs-lookup"><span data-stu-id="47cb6-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="47cb6-125">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="47cb6-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="47cb6-126">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="47cb6-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="47cb6-127">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="47cb6-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="47cb6-128">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="47cb6-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="47cb6-129">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="47cb6-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="47cb6-130">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="47cb6-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="47cb6-131">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="47cb6-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="47cb6-132">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="47cb6-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="47cb6-133">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="47cb6-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="47cb6-134">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="47cb6-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="47cb6-135">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="47cb6-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="47cb6-136">W tym kroku spowoduje dodanie pozycji konfiguracji, aby *Web.config* pliku konfiguracji i edytowanie *Default.aspx* plik, aby wyświetlić oświadczeń informacji o koncie.</span><span class="sxs-lookup"><span data-stu-id="47cb6-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="47cb6-137">Aby skonfigurować aplikację ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="47cb6-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="47cb6-138">W *Default.aspx* pliku, Zastąp istniejące znaczników następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="47cb6-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
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
  
     <span data-ttu-id="47cb6-139">Ten krok powoduje dodanie kontrolce GridView do Twojej *Default.aspx* strona, która zostanie wypełniona oświadczenia jest pobierana z uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="47cb6-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="47cb6-140">Zapisz *Default.aspx* pliku, a następnie otwórz jego plik CodeBehind o nazwie *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="47cb6-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="47cb6-141">Zastąp istniejący kod poniżej:</span><span class="sxs-lookup"><span data-stu-id="47cb6-141">Replace the existing code with the following:</span></span>  
  
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
  
     <span data-ttu-id="47cb6-142">Powyższy kod zostaną wyświetlone oświadczenia dotyczące uwierzytelnionego użytkownika, w tym użytkowników identyfikowanych na podstawie uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="47cb6-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="47cb6-143">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="47cb6-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="47cb6-144">W tym kroku zostanie testowania aplikacji formularzy sieci Web ASP.NET i sprawdź, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="47cb6-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="47cb6-145">Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="47cb6-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="47cb6-146">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="47cb6-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="47cb6-147">Powinna pojawić się *Default.aspx*, który ma **zarejestrować** i **Zaloguj się za** łącza w górnym rogu strony.</span><span class="sxs-lookup"><span data-stu-id="47cb6-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="47cb6-148">Kliknij przycisk **zarejestrować**.</span><span class="sxs-lookup"><span data-stu-id="47cb6-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="47cb6-149">Na **zarejestrować** , Utwórz konto użytkownika, a następnie kliknij przycisk **zarejestrować**.</span><span class="sxs-lookup"><span data-stu-id="47cb6-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="47cb6-150">Twoje konto zostanie utworzone przy użyciu uwierzytelniania formularzy, a użytkownik zostanie automatycznie zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="47cb6-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="47cb6-151">Po nastąpiło przekierowanie do strony głównej, powinna zostać wyświetlona tabela poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacje o Twoim koncie.</span><span class="sxs-lookup"><span data-stu-id="47cb6-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
