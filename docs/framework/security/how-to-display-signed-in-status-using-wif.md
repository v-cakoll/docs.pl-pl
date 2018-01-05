---
title: "Porady: Wyświetlanie zalogowany stanu przy użyciu WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f6951eb6c9df7a3fef09f5972f3cb5fcabe5496f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="92fb5-102">Porady: Wyświetlanie zalogowany stanu przy użyciu WIF</span><span class="sxs-lookup"><span data-stu-id="92fb5-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="92fb5-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="92fb5-103">Applies To</span></span>  
  
-   <span data-ttu-id="92fb5-104">Microsoft Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="92fb5-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
-   <span data-ttu-id="92fb5-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="92fb5-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="92fb5-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="92fb5-106">Summary</span></span>  
 <span data-ttu-id="92fb5-107">W tym temacie opisano sposób wyświetlania znaku w stan w aplikacji z obsługą WIF ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="92fb5-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="92fb5-108">WIF udostępnia mechanizm do tworzenia aplikacji oświadczenia i zarządzanie uwierzytelniania i autoryzacji dla zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92fb5-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="92fb5-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="92fb5-109">Contents</span></span>  
  
-   <span data-ttu-id="92fb5-110">Omówienie</span><span class="sxs-lookup"><span data-stu-id="92fb5-110">Overview</span></span>  
  
-   <span data-ttu-id="92fb5-111">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="92fb5-111">Summary of Steps</span></span>  
  
-   <span data-ttu-id="92fb5-112">Krok 1: Instalowanie tożsamości i uzyskiwać dostęp do rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="92fb5-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="92fb5-113">Krok 2 — Tworzenie aplikacji ASP.NET firm jednostki uzależnionej</span><span class="sxs-lookup"><span data-stu-id="92fb5-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="92fb5-114">Krok 3 — Włączanie lokalne działania projektowe STS do uwierzytelniania użytkowników</span><span class="sxs-lookup"><span data-stu-id="92fb5-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="92fb5-115">Krok 4: modyfikowanie aplikacji ASP.NET do wyświetlenia w ramach stanu logowania</span><span class="sxs-lookup"><span data-stu-id="92fb5-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="92fb5-116">Krok 5: Testowanie integracji między WIF i przez aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92fb5-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="92fb5-117">Omówienie</span><span class="sxs-lookup"><span data-stu-id="92fb5-117">Overview</span></span>  
 <span data-ttu-id="92fb5-118">W tym temacie przedstawiono sposób tworzenia prostej aplikacji obsługujących oświadczenia przy użyciu WIF oraz łatwo wyświetlać, czy użytkownik jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="92fb5-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="92fb5-119">Poniższe kroki, użyj lokalnej usługi STS programowanie dołączonego tożsamości i rozszerzenia programu Visual Studio dostępu.</span><span class="sxs-lookup"><span data-stu-id="92fb5-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="92fb5-120">Lokalnej usługi STS programowanie jest przeznaczony dla środowiska badań i rozwoju to prosta metoda integrowanie oświadczenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92fb5-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="92fb5-121">Nigdy nie powinien można użyć w środowisku produkcyjnym jako nie wykonuje rzeczywistą uwierzytelniania i poświadczenia nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="92fb5-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="92fb5-122">Jednak konieczne kod w następujących krokach jest taki sam dla aplikacji gotowych do produkcji, przy użyciu uwierzytelniania prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="92fb5-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="92fb5-123">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="92fb5-123">Summary of Steps</span></span>  
  
-   <span data-ttu-id="92fb5-124">Krok 1: Instalowanie tożsamości i uzyskiwać dostęp do rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="92fb5-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="92fb5-125">Krok 2 — Tworzenie aplikacji ASP.NET firm jednostki uzależnionej</span><span class="sxs-lookup"><span data-stu-id="92fb5-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="92fb5-126">Krok 3 — Włączanie lokalne działania projektowe STS do uwierzytelniania użytkowników</span><span class="sxs-lookup"><span data-stu-id="92fb5-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="92fb5-127">Krok 4: modyfikowanie aplikacji ASP.NET do wyświetlenia w ramach stanu logowania</span><span class="sxs-lookup"><span data-stu-id="92fb5-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="92fb5-128">Krok 5: Testowanie integracji między WIF i przez aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92fb5-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="92fb5-129">Krok 1: Instalowanie tożsamości i uzyskiwać dostęp do rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="92fb5-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="92fb5-130">W tym kroku opisano sposób konfigurowania rozszerzenia tożsamościami i dostępem do programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="92fb5-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="92fb5-131">To rozszerzenie automatyzuje proces konfigurowania aplikacji do komunikowania się z punktów końcowych usługi STS.</span><span class="sxs-lookup"><span data-stu-id="92fb5-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="92fb5-132">Aby zainstalować rozszerzenie tożsamościami i dostępem</span><span class="sxs-lookup"><span data-stu-id="92fb5-132">To install the Identity and Access extension</span></span>  
  
1.  <span data-ttu-id="92fb5-133">Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.</span><span class="sxs-lookup"><span data-stu-id="92fb5-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="92fb5-134">W programie Visual Studio, kliknij przycisk **narzędzia** i kliknij przycisk **Menedżera rozszerzenia**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="92fb5-135">**Menedżera rozszerzenia** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="92fb5-135">The **Extension Manager** window appears.</span></span>  
  
3.  <span data-ttu-id="92fb5-136">W **Menedżera rozszerzenia**, kliknij przycisk **rozszerzeń Online** z menu po lewej stronie, następnie wybierz **galerii programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4.  <span data-ttu-id="92fb5-137">W prawym górnym rogu **Menedżera rozszerzenia**, wyszukaj *tożsamościami i dostępem*.</span><span class="sxs-lookup"><span data-stu-id="92fb5-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5.  <span data-ttu-id="92fb5-138">**Tożsamościami i dostępem** element zostanie wyświetlony w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="92fb5-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="92fb5-139">Kliknij go, a następnie kliknij przycisk **Pobierz**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-139">Click it, and then click **Download**.</span></span>  
  
6.  <span data-ttu-id="92fb5-140">**Pobierz i zainstaluj** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="92fb5-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="92fb5-141">Jeśli zgadzasz się z warunkami licencji, kliknij przycisk **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-141">If you agree with the license terms, click **Install**.</span></span>  
  
7.  <span data-ttu-id="92fb5-142">Gdy **tożsamościami i dostępem** rozszerzenia zakończył instalowanie, uruchom ponownie program Visual Studio w trybie administratora.</span><span class="sxs-lookup"><span data-stu-id="92fb5-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="92fb5-143">Krok 2 — Tworzenie aplikacji ASP.NET firm jednostki uzależnionej</span><span class="sxs-lookup"><span data-stu-id="92fb5-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="92fb5-144">W tym kroku opisano sposób tworzenia uzależnioną aplikacji formularzy sieci Web ASP.NET, która zostanie zintegrowana z WIF.</span><span class="sxs-lookup"><span data-stu-id="92fb5-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="92fb5-145">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92fb5-145">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="92fb5-146">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="92fb5-147">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="92fb5-148">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="92fb5-149">Krok 3 — Włączanie lokalne działania projektowe STS do uwierzytelniania użytkowników</span><span class="sxs-lookup"><span data-stu-id="92fb5-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="92fb5-150">W tym kroku opisano sposób włączania lokalnej usługi STS Programowanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92fb5-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="92fb5-151">Lokalne programowanie STS jest włączona przy użyciu rozszerzenia tożsamościami i dostępem dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="92fb5-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="92fb5-152">Aby włączyć lokalne STS Programowanie w aplikacji platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92fb5-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1.  <span data-ttu-id="92fb5-153">W programie Visual Studio, kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2.  <span data-ttu-id="92fb5-154">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="92fb5-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="92fb5-155">W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="92fb5-156">Krok 4: modyfikowanie aplikacji ASP.NET do wyświetlenia w ramach stanu logowania</span><span class="sxs-lookup"><span data-stu-id="92fb5-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="92fb5-157">W tym kroku opisano sposób modyfikowania aplikacji platformy ASP.NET można dynamicznie stwierdzenie, czy bieżący użytkownik jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="92fb5-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="92fb5-158">Po skonfigurowaniu dostawcy usługi STS WIF obsługuje oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="92fb5-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="92fb5-159">Teraz należy skonfigurować kod aplikacji, aby wyświetlić wynik uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="92fb5-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="92fb5-160">Aby wyświetlić znak w stan</span><span class="sxs-lookup"><span data-stu-id="92fb5-160">To display sign in status</span></span>  
  
1.  <span data-ttu-id="92fb5-161">W programie Visual Studio Otwórz **Default.aspx** plików w obszarze **TestApp** projektu.</span><span class="sxs-lookup"><span data-stu-id="92fb5-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2.  <span data-ttu-id="92fb5-162">Zastąp istniejący kod znaczników w **Default.aspx** pliku z następujący kod:</span><span class="sxs-lookup"><span data-stu-id="92fb5-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  <span data-ttu-id="92fb5-163">Zapisz **Default.aspx**, a następnie otwórz jego kodzie pliku o nazwie **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92fb5-164">**Default.aspx.cs** mogą być ukryte pod **Default.aspx** w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="92fb5-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="92fb5-165">Jeśli **Default.aspx.cs** nie jest widoczny, rozwiń węzeł **Default.aspx** , klikając trójkąt obok niej.</span><span class="sxs-lookup"><span data-stu-id="92fb5-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4.  <span data-ttu-id="92fb5-166">Zastąp istniejący kod w **Default.aspx.cs** następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="92fb5-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="92fb5-167">Zapisz **Default.aspx.cs**i kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92fb5-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="92fb5-168">Krok 5: Testowanie integracji między WIF i przez aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92fb5-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="92fb5-169">W tym kroku opisano, jak można sprawdzić integrację między WIF i przez aplikację ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="92fb5-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="92fb5-170">Aby sprawdzić integrację między usługami WIF i platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92fb5-170">To test the integration between WIF and ASP.NET</span></span>  
  
1.  <span data-ttu-id="92fb5-171">W programie Visual Studio, naciśnij klawisz **F5** można rozpocząć debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92fb5-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="92fb5-172">Jeśli nie zostaną znalezione żadne błędy, zostanie otwarte nowe okno przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="92fb5-172">If no errors are found, a new browser window will open.</span></span>  
  
2.  <span data-ttu-id="92fb5-173">Można zauważyć dyskretnie przekierowuje żądanie do usługi STS przeglądarki, a następnie otwiera stronę Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="92fb5-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="92fb5-174">Jeśli WIF jest skonfigurowany prawidłowo, powinien zostać wyświetlony lokacji, wyświetl następujący tekst: **"Użytkownik jest zalogowany"**.</span><span class="sxs-lookup"><span data-stu-id="92fb5-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
