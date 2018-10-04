---
title: 'Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: 7d3d23dc1f2e081c0a7c53fbdfaef749c9729fd4
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584406"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="dc217-102">Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF</span><span class="sxs-lookup"><span data-stu-id="dc217-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="dc217-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="dc217-103">Applies To</span></span>  
  
-   <span data-ttu-id="dc217-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="dc217-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
-   <span data-ttu-id="dc217-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="dc217-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="dc217-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="dc217-106">Summary</span></span>  
 <span data-ttu-id="dc217-107">W tym temacie opisano sposób wyświetlania znak w stanie w aplikacji ASP.NET z włączoną obsługą programu WIF.</span><span class="sxs-lookup"><span data-stu-id="dc217-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="dc217-108">Program WIF oferuje mechanizm do tworzenia Twojej aplikacji obsługujących oświadczenia i zarządzanie uwierzytelniania i autoryzacji dla zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc217-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="dc217-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="dc217-109">Contents</span></span>  
  
-   <span data-ttu-id="dc217-110">Omówienie</span><span class="sxs-lookup"><span data-stu-id="dc217-110">Overview</span></span>  
  
-   <span data-ttu-id="dc217-111">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="dc217-111">Summary of Steps</span></span>  
  
-   <span data-ttu-id="dc217-112">Krok 1: Zainstaluj tożsamość i dostęp do rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="dc217-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="dc217-113">Krok 2 — Tworzenie aplikacji jednostki uzależnionej strona ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="dc217-114">Krok 3 — Włączanie lokalnej deweloperskiej usługi STS do uwierzytelniania kont użytkowników</span><span class="sxs-lookup"><span data-stu-id="dc217-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="dc217-115">Krok 4 — zmodyfikować aplikację ASP.NET w celu wyświetlania logowania w stan</span><span class="sxs-lookup"><span data-stu-id="dc217-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="dc217-116">Krok 5: Testowanie integracji między programu WIF i aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="dc217-117">Omówienie</span><span class="sxs-lookup"><span data-stu-id="dc217-117">Overview</span></span>  
 <span data-ttu-id="dc217-118">W tym temacie przedstawiono sposób tworzenia prostej aplikacji obsługującej oświadczenia, za pomocą programu WIF oraz jak łatwo wyświetlać, czy użytkownik jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="dc217-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="dc217-119">Użyto lokalnej deweloperskiej usługi STS dołączoną tożsamości i dostępu rozszerzenie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc217-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="dc217-120">Local Development STS jest przeznaczony dla środowisk testowych i programistycznych środowisku w celu zapewnienia to prosta metoda integrowania oświadczeń do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc217-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="dc217-121">Go nie należy używać w środowisku produkcyjnym, ponieważ nie wykonuje faktycznego uwierzytelniania i poświadczenia nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="dc217-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="dc217-122">Jednak kodu imperatywnego w poniższych krokach jest taka sama dla aplikacji gotowych do produkcji rzeczywistego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dc217-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="dc217-123">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="dc217-123">Summary of Steps</span></span>  
  
-   <span data-ttu-id="dc217-124">Krok 1: Zainstaluj tożsamość i dostęp do rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="dc217-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="dc217-125">Krok 2 — Tworzenie aplikacji jednostki uzależnionej strona ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="dc217-126">Krok 3 — Włączanie lokalnej deweloperskiej usługi STS do uwierzytelniania kont użytkowników</span><span class="sxs-lookup"><span data-stu-id="dc217-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="dc217-127">Krok 4 — zmodyfikować aplikację ASP.NET w celu wyświetlania logowania w stan</span><span class="sxs-lookup"><span data-stu-id="dc217-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="dc217-128">Krok 5: Testowanie integracji między programu WIF i aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="dc217-129">Krok 1: Zainstaluj tożsamość i dostęp do rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="dc217-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="dc217-130">W tym kroku opisano sposób konfigurowania rozszerzenia tożsamościami i dostępem do programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="dc217-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="dc217-131">To rozszerzenie automatyzuje proces konfigurowania aplikacji do komunikowania się z punktami końcowymi usługi STS.</span><span class="sxs-lookup"><span data-stu-id="dc217-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="dc217-132">Aby zainstalować rozszerzenie tożsamościami i dostępem</span><span class="sxs-lookup"><span data-stu-id="dc217-132">To install the Identity and Access extension</span></span>  
  
1.  <span data-ttu-id="dc217-133">Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.</span><span class="sxs-lookup"><span data-stu-id="dc217-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="dc217-134">W programie Visual Studio, kliknij przycisk **narzędzia** i kliknij przycisk **Menedżera rozszerzeń**.</span><span class="sxs-lookup"><span data-stu-id="dc217-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="dc217-135">**Menedżera rozszerzeń** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="dc217-135">The **Extension Manager** window appears.</span></span>  
  
3.  <span data-ttu-id="dc217-136">W **Menedżera rozszerzeń**, kliknij przycisk **rozszerzeń Online** menu po lewej stronie, następnie wybierz pozycję **galerii Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="dc217-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4.  <span data-ttu-id="dc217-137">W prawym górnym rogu **Menedżera rozszerzeń**, wyszukaj *tożsamościami i dostępem*.</span><span class="sxs-lookup"><span data-stu-id="dc217-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5.  <span data-ttu-id="dc217-138">**Tożsamościami i dostępem** element zostanie wyświetlony w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="dc217-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="dc217-139">Kliknij go, a następnie kliknij przycisk **Pobierz**.</span><span class="sxs-lookup"><span data-stu-id="dc217-139">Click it, and then click **Download**.</span></span>  
  
6.  <span data-ttu-id="dc217-140">**Pobierz i zainstaluj** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="dc217-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="dc217-141">Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **zainstalować**.</span><span class="sxs-lookup"><span data-stu-id="dc217-141">If you agree with the license terms, click **Install**.</span></span>  
  
7.  <span data-ttu-id="dc217-142">Gdy **tożsamościami i dostępem** instalacja rozszerzenia została ukończona, uruchom program Visual Studio w trybie administratora.</span><span class="sxs-lookup"><span data-stu-id="dc217-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="dc217-143">Krok 2 — Tworzenie aplikacji jednostki uzależnionej strona ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="dc217-144">Tym kroku opisano sposób tworzenia jednostki uzależnionej ze stron aplikacji formularzy sieci Web ASP.NET, która integruje się z programu WIF.</span><span class="sxs-lookup"><span data-stu-id="dc217-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="dc217-145">Aby utworzyć prostą aplikację platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-145">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="dc217-146">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="dc217-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="dc217-147">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="dc217-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="dc217-148">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="dc217-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="dc217-149">Krok 3 — Włączanie lokalnej deweloperskiej usługi STS do uwierzytelniania kont użytkowników</span><span class="sxs-lookup"><span data-stu-id="dc217-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="dc217-150">W tym kroku opisano, jak włączyć lokalnej deweloperskiej usługi STS w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc217-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="dc217-151">Lokalnej deweloperskiej usługi STS jest włączona, przy użyciu rozszerzenia tożsamości i dostępu dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc217-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="dc217-152">Aby włączyć lokalnej deweloperskiej usługi STS w aplikacji programu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1.  <span data-ttu-id="dc217-153">W programie Visual Studio, kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="dc217-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2.  <span data-ttu-id="dc217-154">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="dc217-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="dc217-155">W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="dc217-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="dc217-156">Krok 4 — zmodyfikować aplikację ASP.NET w celu wyświetlania logowania w stan</span><span class="sxs-lookup"><span data-stu-id="dc217-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="dc217-157">W tym kroku opisano, jak zmodyfikować aplikację ASP.NET w celu dynamicznego wyświetlania, czy bieżący użytkownik jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="dc217-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="dc217-158">Po skonfigurowaniu dostawcy usługi STS program WIF obsługuje oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="dc217-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="dc217-159">Teraz należy skonfigurować kod aplikacji, aby wyświetlić wynik uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="dc217-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="dc217-160">Aby wyświetlić logowania w stan</span><span class="sxs-lookup"><span data-stu-id="dc217-160">To display sign in status</span></span>  
  
1.  <span data-ttu-id="dc217-161">W programie Visual Studio, otwórz **Default.aspx** plik **TestApp** projektu.</span><span class="sxs-lookup"><span data-stu-id="dc217-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2.  <span data-ttu-id="dc217-162">Zastąp istniejący kod znaczników w **Default.aspx** pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="dc217-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
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
  
3.  <span data-ttu-id="dc217-163">Zapisz **Default.aspx**, a następnie otwórz jego kod związany z pliku o nazwie **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="dc217-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc217-164">**Default.aspx.cs** może być ukryty pod **Default.aspx** w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="dc217-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="dc217-165">Jeśli **Default.aspx.cs** nie jest widoczny, rozwiń węzeł **Default.aspx** , klikając trójkąta obok niej.</span><span class="sxs-lookup"><span data-stu-id="dc217-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4.  <span data-ttu-id="dc217-166">Zastąp istniejący kod w **Default.aspx.cs** następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="dc217-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
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
  
5.  <span data-ttu-id="dc217-167">Zapisz **Default.aspx.cs**i utworzyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="dc217-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="dc217-168">Krok 5: Testowanie integracji między programu WIF i aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="dc217-169">W tym kroku opisano, jak można przetestować integrację programu WIF i aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dc217-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="dc217-170">Aby przetestować integrację programu WIF i platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dc217-170">To test the integration between WIF and ASP.NET</span></span>  
  
1.  <span data-ttu-id="dc217-171">W programie Visual Studio, naciśnij klawisz **F5** można rozpocząć debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc217-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="dc217-172">Jeśli nie znaleziono żadnych błędów, zostanie otwarte nowe okno przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="dc217-172">If no errors are found, a new browser window will open.</span></span>  
  
2.  <span data-ttu-id="dc217-173">Możesz zauważyć, że przeglądarki dyskretnie przekierowuje żądanie do usługi STS, a następnie spowoduje otwarcie strony Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="dc217-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="dc217-174">Jeśli program WIF jest poprawnie skonfigurowany, powinien zostać wyświetlony witryny, wyświetl następujący tekst: **"Użytkownik jest zalogowany"**.</span><span class="sxs-lookup"><span data-stu-id="dc217-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
