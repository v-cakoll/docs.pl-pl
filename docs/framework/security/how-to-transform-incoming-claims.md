---
title: "Porady: Przekształcanie oświadczeń przychodzących"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="e6d89-102">Porady: Przekształcanie oświadczeń przychodzących</span><span class="sxs-lookup"><span data-stu-id="e6d89-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="e6d89-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="e6d89-103">Applies To</span></span>  
  
-   <span data-ttu-id="e6d89-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e6d89-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="e6d89-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="e6d89-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e6d89-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="e6d89-106">Summary</span></span>  
 <span data-ttu-id="e6d89-107">Porada ten zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji obsługującej oświadczenia formularzy sieci Web ASP.NET i przekształcanie oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e6d89-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="e6d89-108">Umożliwia także instrukcje dotyczące testowania aplikacji, aby zweryfikować, że oświadczenia po przekształceniu są dostarczane, gdy aplikacja jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="e6d89-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e6d89-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="e6d89-109">Contents</span></span>  
  
-   <span data-ttu-id="e6d89-110">Cele</span><span class="sxs-lookup"><span data-stu-id="e6d89-110">Objectives</span></span>  
  
-   <span data-ttu-id="e6d89-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e6d89-111">Overview</span></span>  
  
-   <span data-ttu-id="e6d89-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="e6d89-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e6d89-113">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="e6d89-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e6d89-114">Krok 2 — przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń wdrożenie</span><span class="sxs-lookup"><span data-stu-id="e6d89-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="e6d89-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e6d89-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="e6d89-116">Cele</span><span class="sxs-lookup"><span data-stu-id="e6d89-116">Objectives</span></span>  
  
-   <span data-ttu-id="e6d89-117">Skonfigurować aplikację ASP.NET Web Forms dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="e6d89-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="e6d89-118">Oświadczenia przychodzące przez dodanie oświadczenia roli administratora</span><span class="sxs-lookup"><span data-stu-id="e6d89-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="e6d89-119">Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa poprawnie</span><span class="sxs-lookup"><span data-stu-id="e6d89-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e6d89-120">Omówienie</span><span class="sxs-lookup"><span data-stu-id="e6d89-120">Overview</span></span>  
 <span data-ttu-id="e6d89-121">WIF udostępnia klasę o nazwie <xref:System.Security.Claims.ClaimsAuthenticationManager> , umożliwia użytkownikom na modyfikowanie oświadczeń, zanim zostaną przedstawione do jednostki uzależnionej aplikacji firm (RP).</span><span class="sxs-lookup"><span data-stu-id="e6d89-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="e6d89-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Jest przydatne w przypadku separacji między uwierzytelniania i źródłowy kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e6d89-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="e6d89-123">W poniższym przykładzie pokazano, jak dodać roli do oświadczeń z przychodzącego <xref:System.Security.Claims.ClaimsPrincipal> , co może być wymagane przez planu odzyskiwania.</span><span class="sxs-lookup"><span data-stu-id="e6d89-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e6d89-124">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="e6d89-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="e6d89-125">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="e6d89-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="e6d89-126">Krok 2 — przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń wdrożenie</span><span class="sxs-lookup"><span data-stu-id="e6d89-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="e6d89-127">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e6d89-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="e6d89-128">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="e6d89-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="e6d89-129">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="e6d89-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e6d89-130">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e6d89-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="e6d89-131">Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.</span><span class="sxs-lookup"><span data-stu-id="e6d89-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="e6d89-132">W programie Visual Studio, kliknij przycisk **pliku**, kliknij przycisk **nowy**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="e6d89-133">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="e6d89-134">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="e6d89-135">Kliknij prawym przyciskiem myszy **TestApp** projektu w obszarze **Eksploratora rozwiązań**, a następnie wybierz pozycję **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="e6d89-136">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="e6d89-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="e6d89-137">W obszarze **dostawców**, wybierz pozycję **testowania aplikacji z lokalnej usługi STS programowanie**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="e6d89-138">W *Default.aspx* pliku, Zastąp istniejące znaczników następującym kodem, a następnie zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="e6d89-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
          <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
8.  <span data-ttu-id="e6d89-139">Otwórz plik CodeBehind o nazwie *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="e6d89-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="e6d89-140">Zastąp istniejący kod poniżej, następnie zapisz ten plik:</span><span class="sxs-lookup"><span data-stu-id="e6d89-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="e6d89-141">Krok 2 — przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń wdrożenie</span><span class="sxs-lookup"><span data-stu-id="e6d89-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="e6d89-142">W tym kroku zostanie zastąpione domyślna funkcjonalność w <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, aby dodać rolę administratora do przychodzącego podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e6d89-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="e6d89-143">Aby zaimplementować przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania oświadczeń</span><span class="sxs-lookup"><span data-stu-id="e6d89-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="e6d89-144">W programie Visual Studio, kliknij prawym przyciskiem myszy na rozwiązanie, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="e6d89-145">W **Dodawanie nowego projektu** wybierz **biblioteki klas** z **Visual C#** szablony list, wprowadź `ClaimsTransformation`, a następnie naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="e6d89-146">Nowy projekt zostanie utworzony w folderze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e6d89-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="e6d89-147">Kliknij prawym przyciskiem myszy **odwołania** w obszarze **ClaimsTransformation** projektu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="e6d89-148">W **Menedżera odwołań** wybierz **System.IdentityModel**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="e6d89-149">Otwórz **Class1.cs**, lub jeśli nie istnieje, kliknij prawym przyciskiem myszy **ClaimsTransformation**, kliknij przycisk **Dodaj**, następnie kliknij przycisk **klasy...**</span><span class="sxs-lookup"><span data-stu-id="e6d89-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="e6d89-150">Dodaj następujący kod do pliku kodu przy użyciu dyrektyw:</span><span class="sxs-lookup"><span data-stu-id="e6d89-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="e6d89-151">Dodaj następujące klasy i metody w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="e6d89-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="e6d89-152">Następujący kod jest tylko w celach demonstracyjnych Upewnij się, że Sprawdź swoje uprawnienia zamierzonego w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="e6d89-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
    ```csharp  
    public class ClaimsTransformationModule : ClaimsAuthenticationManager  
    {  
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)  
        {  
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)  
            {  
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));  
            }  
  
            return incomingPrincipal;  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="e6d89-153">Zapisz plik i kompilacji **ClaimsTransformation** projektu.</span><span class="sxs-lookup"><span data-stu-id="e6d89-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="e6d89-154">W Twojej **TestApp** projektu ASP.NET, kliknij prawym przyciskiem myszy na odwołania, a następnie kliknij **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="e6d89-155">W **Menedżera odwołań** wybierz **rozwiązania** z menu po lewej stronie wybierz **ClaimsTransformation** z wypełnione opcje, a następnie kliknij przycisk  **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6d89-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="e6d89-156">W folderze głównym **Web.config** pliku, przejdź do  **\<system.identityModel >** wpisu.</span><span class="sxs-lookup"><span data-stu-id="e6d89-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="e6d89-157">W ramach  **\<identityConfiguration >** elementów, Dodaj następujący wiersz i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="e6d89-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="e6d89-158">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e6d89-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="e6d89-159">W tym kroku zostanie testowania aplikacji formularzy sieci Web ASP.NET i sprawdź, że oświadczenia są dostarczane, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="e6d89-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="e6d89-160">Aby przetestować aplikację ASP.NET Web Forms dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="e6d89-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="e6d89-161">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="e6d89-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="e6d89-162">Powinna pojawić się *Default.aspx*.</span><span class="sxs-lookup"><span data-stu-id="e6d89-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="e6d89-163">Na *Default.aspx* strony, powinna zostać wyświetlona tabela poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacje o Twoim koncie.</span><span class="sxs-lookup"><span data-stu-id="e6d89-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="e6d89-164">Ostatni wiersz powinny być prezentowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e6d89-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="e6d89-165">URZĄD LOKALNY</span><span class="sxs-lookup"><span data-stu-id="e6d89-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="e6d89-166">URZĄD LOKALNY</span><span class="sxs-lookup"><span data-stu-id="e6d89-166">LOCAL AUTHORITY</span></span>|<span data-ttu-id="e6d89-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span><span class="sxs-lookup"><span data-stu-id="e6d89-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span></span>|<span data-ttu-id="e6d89-168">Administrator</span><span class="sxs-lookup"><span data-stu-id="e6d89-168">Admin</span></span>|<span data-ttu-id="e6d89-169">http://www.w3.org/2001/XMLSchema#String</span><span class="sxs-lookup"><span data-stu-id="e6d89-169">http://www.w3.org/2001/XMLSchema#string</span></span>|
