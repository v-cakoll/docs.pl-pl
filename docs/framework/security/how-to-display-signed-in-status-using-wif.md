---
title: 'Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF'
ms.date: 03/30/2017
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
author: BrucePerlerMS
ms.openlocfilehash: e44dc80260e46b81ac723ada32085390a18a153a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945700"
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="df5ca-102">Instrukcje: Wyświetlanie stanu zalogowania przy użyciu programu WIF</span><span class="sxs-lookup"><span data-stu-id="df5ca-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="df5ca-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="df5ca-103">Applies To</span></span>  
  
- <span data-ttu-id="df5ca-104">Microsoft® Windows® Identity Foundation (WIF) 4,5</span><span class="sxs-lookup"><span data-stu-id="df5ca-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
- <span data-ttu-id="df5ca-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="df5ca-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="df5ca-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="df5ca-106">Summary</span></span>  
 <span data-ttu-id="df5ca-107">W tym temacie opisano sposób wyświetlania stanu logowania w aplikacji ASP.NET z włączoną obsługą WIF.</span><span class="sxs-lookup"><span data-stu-id="df5ca-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="df5ca-108">WIF zapewnia mechanizm tworzenia oświadczeń aplikacji i zarządzania uwierzytelnianiem i autoryzacją zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df5ca-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="df5ca-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="df5ca-109">Contents</span></span>  
  
- <span data-ttu-id="df5ca-110">Omówienie</span><span class="sxs-lookup"><span data-stu-id="df5ca-110">Overview</span></span>  
  
- <span data-ttu-id="df5ca-111">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="df5ca-111">Summary of Steps</span></span>  
  
- <span data-ttu-id="df5ca-112">Krok 1 — Instalowanie tożsamości i rozszerzenia dostępu</span><span class="sxs-lookup"><span data-stu-id="df5ca-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="df5ca-113">Krok 2 — Tworzenie aplikacji ASP.NET jednostki uzależnionej</span><span class="sxs-lookup"><span data-stu-id="df5ca-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="df5ca-114">Krok 3 — włączenie lokalnego programu STS do uwierzytelniania użytkowników</span><span class="sxs-lookup"><span data-stu-id="df5ca-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="df5ca-115">Krok 4 — modyfikowanie aplikacji ASP.NET na potrzeby wyświetlania stanu logowania</span><span class="sxs-lookup"><span data-stu-id="df5ca-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="df5ca-116">Krok 5 — testowanie integracji między WIF i ASP.NET aplikacji</span><span class="sxs-lookup"><span data-stu-id="df5ca-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="df5ca-117">Omówienie</span><span class="sxs-lookup"><span data-stu-id="df5ca-117">Overview</span></span>  
 <span data-ttu-id="df5ca-118">W tym temacie pokazano, jak utworzyć prostą aplikację obsługującą oświadczenia przy użyciu WIF oraz jak łatwo wyświetlać informacje o tym, czy użytkownik jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="df5ca-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="df5ca-119">W poniższych krokach użyto lokalnego tworzenia usługi STS dołączonego do rozszerzenia tożsamości i dostępu do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df5ca-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="df5ca-120">Lokalna programowanie w usłudze STS jest przeznaczone dla środowiska testowania i programowania, aby zapewnić prostą metodę integrowania oświadczeń z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="df5ca-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="df5ca-121">Nigdy nie powinna być używana w środowisku produkcyjnym, ponieważ nie wykonuje rzeczywistego uwierzytelniania i poświadczenia nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="df5ca-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="df5ca-122">Jednak bezwzględny kod w poniższych krokach jest taki sam dla aplikacji gotowej do użycia w środowisku produkcyjnym przy użyciu rzeczywistego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="df5ca-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="df5ca-123">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="df5ca-123">Summary of Steps</span></span>  
  
- <span data-ttu-id="df5ca-124">Krok 1 — Instalowanie tożsamości i rozszerzenia dostępu</span><span class="sxs-lookup"><span data-stu-id="df5ca-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
- <span data-ttu-id="df5ca-125">Krok 2 — Tworzenie aplikacji ASP.NET jednostki uzależnionej</span><span class="sxs-lookup"><span data-stu-id="df5ca-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
- <span data-ttu-id="df5ca-126">Krok 3 — włączenie lokalnego programu STS do uwierzytelniania użytkowników</span><span class="sxs-lookup"><span data-stu-id="df5ca-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
- <span data-ttu-id="df5ca-127">Krok 4 — modyfikowanie aplikacji ASP.NET na potrzeby wyświetlania stanu logowania</span><span class="sxs-lookup"><span data-stu-id="df5ca-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
- <span data-ttu-id="df5ca-128">Krok 5 — testowanie integracji między WIF i ASP.NET aplikacji</span><span class="sxs-lookup"><span data-stu-id="df5ca-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="df5ca-129">Krok 1 — Instalowanie tożsamości i rozszerzenia dostępu</span><span class="sxs-lookup"><span data-stu-id="df5ca-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="df5ca-130">W tym kroku opisano sposób konfigurowania rozszerzenia tożsamości i dostępu do programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="df5ca-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="df5ca-131">To rozszerzenie automatyzuje proces konfigurowania aplikacji w celu komunikowania się z punktami końcowymi usługi STS.</span><span class="sxs-lookup"><span data-stu-id="df5ca-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="df5ca-132">Aby zainstalować tożsamość i rozszerzenie dostępu</span><span class="sxs-lookup"><span data-stu-id="df5ca-132">To install the Identity and Access extension</span></span>  
  
1. <span data-ttu-id="df5ca-133">Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.</span><span class="sxs-lookup"><span data-stu-id="df5ca-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2. <span data-ttu-id="df5ca-134">W programie Visual Studio kliknij pozycję **Narzędzia** , a następnie kliknij pozycję **Menedżer rozszerzeń**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="df5ca-135">Zostanie wyświetlone okno **Menedżer rozszerzeń** .</span><span class="sxs-lookup"><span data-stu-id="df5ca-135">The **Extension Manager** window appears.</span></span>  
  
3. <span data-ttu-id="df5ca-136">W **Menedżerze rozszerzeń**kliknij pozycję **rozszerzenia online** w menu po lewej stronie, a następnie wybierz pozycję **Galeria Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4. <span data-ttu-id="df5ca-137">W prawym górnym rogu **Menedżera rozszerzeń**Wyszukaj pozycję *tożsamość i dostęp*.</span><span class="sxs-lookup"><span data-stu-id="df5ca-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5. <span data-ttu-id="df5ca-138">**Tożsamość i element dostępu** będą widoczne w wynikach wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="df5ca-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="df5ca-139">Kliknij go, a następnie kliknij pozycję **Pobierz**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-139">Click it, and then click **Download**.</span></span>  
  
6. <span data-ttu-id="df5ca-140">Zostanie wyświetlone okno dialogowe **pobieranie i Instalowanie** .</span><span class="sxs-lookup"><span data-stu-id="df5ca-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="df5ca-141">Jeśli zgadzasz się z postanowieniami licencyjnymi, kliknij przycisk **Instaluj**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-141">If you agree with the license terms, click **Install**.</span></span>  
  
7. <span data-ttu-id="df5ca-142">Po zakończeniu instalacji rozszerzenia **tożsamości i dostępu** Uruchom ponownie program Visual Studio w trybie administratora.</span><span class="sxs-lookup"><span data-stu-id="df5ca-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="df5ca-143">Krok 2 — Tworzenie aplikacji ASP.NET jednostki uzależnionej</span><span class="sxs-lookup"><span data-stu-id="df5ca-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="df5ca-144">W tym kroku opisano sposób tworzenia aplikacji ASP.NET Web Forms jednostki uzależnionej, która zostanie zintegrowana z WIF.</span><span class="sxs-lookup"><span data-stu-id="df5ca-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="df5ca-145">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="df5ca-145">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="df5ca-146">Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="df5ca-147">W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="df5ca-148">W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="df5ca-149">Krok 3 — włączenie lokalnego programu STS do uwierzytelniania użytkowników</span><span class="sxs-lookup"><span data-stu-id="df5ca-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="df5ca-150">W tym kroku opisano sposób włączania lokalnego tworzenia usługi STS w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df5ca-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="df5ca-151">Lokalna programowanie usługi STS jest włączona przy użyciu rozszerzenia tożsamości i dostępu dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="df5ca-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="df5ca-152">Aby włączyć lokalne programowanie usługi STS w aplikacji ASP.NET</span><span class="sxs-lookup"><span data-stu-id="df5ca-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1. <span data-ttu-id="df5ca-153">W programie Visual Studio kliknij prawym przyciskiem myszy projekt **TestApp** w obszarze **Eksplorator rozwiązań**, a następnie wybierz pozycję **tożsamość i dostęp**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2. <span data-ttu-id="df5ca-154">Zostanie wyświetlone okno **tożsamość i dostęp** .</span><span class="sxs-lookup"><span data-stu-id="df5ca-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="df5ca-155">W obszarze **dostawcy**wybierz pozycję **Testuj aplikację przy użyciu lokalnej usługi STS**, a następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="df5ca-156">Krok 4 — modyfikowanie aplikacji ASP.NET na potrzeby wyświetlania stanu logowania</span><span class="sxs-lookup"><span data-stu-id="df5ca-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="df5ca-157">W tym kroku opisano sposób modyfikowania aplikacji ASP.NET w celu dynamicznego wyświetlania, czy bieżący użytkownik jest zalogowany.</span><span class="sxs-lookup"><span data-stu-id="df5ca-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="df5ca-158">Po skonfigurowaniu dostawcy usługi STS WIF obsługuje oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="df5ca-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="df5ca-159">Teraz musisz skonfigurować kod aplikacji, aby wyświetlić wynik uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="df5ca-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
### <a name="to-display-sign-in-status"></a><span data-ttu-id="df5ca-160">Aby wyświetlić stan logowania</span><span class="sxs-lookup"><span data-stu-id="df5ca-160">To display sign in status</span></span>  
  
1. <span data-ttu-id="df5ca-161">W programie Visual Studio Otwórz plik **default. aspx** w projekcie **TestApp** .</span><span class="sxs-lookup"><span data-stu-id="df5ca-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2. <span data-ttu-id="df5ca-162">Zastąp istniejący znacznik w pliku **default. aspx** następującym znacznikiem:</span><span class="sxs-lookup"><span data-stu-id="df5ca-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
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
  
3. <span data-ttu-id="df5ca-163">Zapisz plik **default. aspx**, a następnie otwórz jego kod w pliku o nazwie **default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="df5ca-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="df5ca-164">**Default.aspx.cs** może być ukryty poniżej **default. aspx** w Eksplorator rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="df5ca-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="df5ca-165">Jeśli **default.aspx.cs** nie jest widoczny, rozwiń plik **default. aspx** , klikając trójkąt obok niego.</span><span class="sxs-lookup"><span data-stu-id="df5ca-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4. <span data-ttu-id="df5ca-166">Zastąp istniejący kod w **default.aspx.cs** następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="df5ca-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
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
  
5. <span data-ttu-id="df5ca-167">Zapisz **default.aspx.cs**i skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="df5ca-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="df5ca-168">Krok 5 — testowanie integracji między WIF i ASP.NET aplikacji</span><span class="sxs-lookup"><span data-stu-id="df5ca-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="df5ca-169">W tym kroku opisano, jak można testować integrację między programem WIF i aplikacją ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="df5ca-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="df5ca-170">Aby przetestować integrację między WIF i ASP.NET</span><span class="sxs-lookup"><span data-stu-id="df5ca-170">To test the integration between WIF and ASP.NET</span></span>  
  
1. <span data-ttu-id="df5ca-171">W programie Visual Studio naciśnij klawisz **F5** , aby rozpocząć debugowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="df5ca-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="df5ca-172">Jeśli nie zostaną znalezione żadne błędy, zostanie otwarte nowe okno przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="df5ca-172">If no errors are found, a new browser window will open.</span></span>  
  
2. <span data-ttu-id="df5ca-173">Możesz zauważyć, że przeglądarka w trybie dyskretnym przekierowuje żądanie do usługi STS, a następnie otworzy stronę Default. aspx.</span><span class="sxs-lookup"><span data-stu-id="df5ca-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="df5ca-174">Jeśli WIF jest prawidłowo skonfigurowany, powinna zostać wyświetlona następująca treść witryny: **"Jesteś zalogowany"** .</span><span class="sxs-lookup"><span data-stu-id="df5ca-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
