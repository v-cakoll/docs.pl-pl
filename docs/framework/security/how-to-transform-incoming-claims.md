---
title: 'Instrukcje: Przekształcanie oświadczeń przychodzących'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: ce99b97007bf7608856345d6da87cd9e422d2266
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041479"
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="bb1b6-102">Instrukcje: Przekształcanie oświadczeń przychodzących</span><span class="sxs-lookup"><span data-stu-id="bb1b6-102">How To: Transform Incoming Claims</span></span>

## <a name="applies-to"></a><span data-ttu-id="bb1b6-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="bb1b6-103">Applies To</span></span>

- <span data-ttu-id="bb1b6-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="bb1b6-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="bb1b6-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="bb1b6-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="bb1b6-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="bb1b6-106">Summary</span></span>

<span data-ttu-id="bb1b6-107">Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms i przekształcania oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="bb1b6-108">Zawiera również instrukcje dotyczące testowania aplikacji, aby sprawdzić, czy po uruchomieniu aplikacji są prezentowane przekształcone oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>

## <a name="contents"></a><span data-ttu-id="bb1b6-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="bb1b6-109">Contents</span></span>

- <span data-ttu-id="bb1b6-110">Cele</span><span class="sxs-lookup"><span data-stu-id="bb1b6-110">Objectives</span></span>

- <span data-ttu-id="bb1b6-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="bb1b6-111">Overview</span></span>

- <span data-ttu-id="bb1b6-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="bb1b6-112">Summary of Steps</span></span>

- <span data-ttu-id="bb1b6-113">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="bb1b6-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="bb1b6-114">Krok 2 — implementowanie transformacji oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="bb1b6-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

- <span data-ttu-id="bb1b6-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bb1b6-115">Step 3 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="bb1b6-116">Cele</span><span class="sxs-lookup"><span data-stu-id="bb1b6-116">Objectives</span></span>

- <span data-ttu-id="bb1b6-117">Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="bb1b6-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>

- <span data-ttu-id="bb1b6-118">Przekształć oświadczenia przychodzące przez dodanie oświadczenia roli administratora</span><span class="sxs-lookup"><span data-stu-id="bb1b6-118">Transform incoming claims by adding an Administrator role claim</span></span>

- <span data-ttu-id="bb1b6-119">Przetestuj aplikację ASP.NET Web Forms, aby sprawdzić, czy działa prawidłowo</span><span class="sxs-lookup"><span data-stu-id="bb1b6-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>

## <a name="overview"></a><span data-ttu-id="bb1b6-120">Omówienie</span><span class="sxs-lookup"><span data-stu-id="bb1b6-120">Overview</span></span>

<span data-ttu-id="bb1b6-121">WIF uwidacznia klasę o nazwie <xref:System.Security.Claims.ClaimsAuthenticationManager> , która umożliwia użytkownikom modyfikowanie oświadczeń przed wyświetleniem ich w aplikacji jednostki uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="bb1b6-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="bb1b6-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Jest to przydatne w przypadku rozdzielenia problemów między uwierzytelnianiem a podstawowym kodem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="bb1b6-123">W poniższym przykładzie pokazano, jak dodać rolę do oświadczeń w przychodzących <xref:System.Security.Claims.ClaimsPrincipal> , które mogą być wymagane przez RP.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="bb1b6-124">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="bb1b6-124">Summary of Steps</span></span>

- <span data-ttu-id="bb1b6-125">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="bb1b6-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

- <span data-ttu-id="bb1b6-126">Krok 2 — implementowanie transformacji oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="bb1b6-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

- <span data-ttu-id="bb1b6-127">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bb1b6-127">Step 3 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="bb1b6-128">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="bb1b6-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>

<span data-ttu-id="bb1b6-129">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>

#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="bb1b6-130">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bb1b6-130">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="bb1b6-131">Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-131">Start Visual Studio in elevated mode as administrator.</span></span>

2. <span data-ttu-id="bb1b6-132">W programie Visual Studio kliknij pozycję **plik**, kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="bb1b6-133">W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

4. <span data-ttu-id="bb1b6-134">W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-134">In **Name**, enter `TestApp` and press **OK**.</span></span>

5. <span data-ttu-id="bb1b6-135">Kliknij prawym przyciskiem myszy projekt **TestApp** w obszarze **Eksplorator rozwiązań**, a następnie wybierz pozycję **tożsamość i dostęp**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

6. <span data-ttu-id="bb1b6-136">Zostanie wyświetlone okno **tożsamość i dostęp** .</span><span class="sxs-lookup"><span data-stu-id="bb1b6-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="bb1b6-137">W obszarze **dostawcy**wybierz pozycję **Testuj aplikację przy użyciu lokalnej usługi STS**, a następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>

7. <span data-ttu-id="bb1b6-138">W pliku *default. aspx* Zastąp istniejący znacznik następującym zapisem, a następnie Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="bb1b6-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>

    ```aspx-csharp
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

8. <span data-ttu-id="bb1b6-139">Otwórz plik związany z kodem o nazwie *default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="bb1b6-140">Zastąp istniejący kod następującym kodem, a następnie Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="bb1b6-140">Replace the existing code with the following, then save the file:</span></span>

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

## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="bb1b6-141">Krok 2 — implementowanie transformacji oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="bb1b6-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>

<span data-ttu-id="bb1b6-142">W tym kroku zastąpisz funkcję domyślną w <xref:System.Security.Claims.ClaimsAuthenticationManager> klasie w celu dodania roli administratora do przychodzącego podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>

#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="bb1b6-143">Aby zaimplementować transformację oświadczeń przy użyciu niestandardowego ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="bb1b6-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>

1. <span data-ttu-id="bb1b6-144">W programie Visual Studio kliknij prawym przyciskiem myszy na rozwiązaniu, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="bb1b6-145">W oknie **Dodaj nowy projekt** wybierz pozycję **Biblioteka klas** z listy Szablony  **C# wizualizacji** , `ClaimsTransformation`a następnie naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="bb1b6-146">Nowy projekt zostanie utworzony w folderze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-146">The new project will be created in your solution folder.</span></span>

3. <span data-ttu-id="bb1b6-147">Kliknij prawym przyciskiem myszy pozycję **odwołania** w projekcie **ClaimsTransformation** , a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>

4. <span data-ttu-id="bb1b6-148">W oknie **Menedżer odwołań** wybierz pozycję **System. IdentityModel**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>

5. <span data-ttu-id="bb1b6-149">Otwórz **Class1.cs**lub jeśli nie istnieje, kliknij prawym przyciskiem myszy pozycję **ClaimsTransformation**, kliknij polecenie **Dodaj**, a następnie kliknij pozycję **Klasa...**</span><span class="sxs-lookup"><span data-stu-id="bb1b6-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>

6. <span data-ttu-id="bb1b6-150">Dodaj następujące dyrektywy using do pliku kodu:</span><span class="sxs-lookup"><span data-stu-id="bb1b6-150">Add the following using directives to the code file:</span></span>

    ```csharp
    using System.Security.Claims;
    using System.Security.Principal;
    ```

7. <span data-ttu-id="bb1b6-151">Dodaj do pliku kodu następującą klasę i metodę.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-151">Add the following class and method in the code file.</span></span>

    > [!WARNING]
    > <span data-ttu-id="bb1b6-152">Poniższy kod służy tylko do celów demonstracyjnych. Upewnij się, że masz pewność, że zamierzone uprawnienia są sprawdzane w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>

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

8. <span data-ttu-id="bb1b6-153">Zapisz plik i skompiluj projekt **ClaimsTransformation** .</span><span class="sxs-lookup"><span data-stu-id="bb1b6-153">Save the file and build the **ClaimsTransformation** project.</span></span>

9. <span data-ttu-id="bb1b6-154">W projekcie **TestApp** ASP.NET kliknij prawym przyciskiem myszy pozycję odwołania, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>

10. <span data-ttu-id="bb1b6-155">W oknie **Menedżer odwołań** wybierz pozycję **rozwiązanie** z menu po lewej stronie, wybierz pozycję **ClaimsTransformation** z opcji wypełnionych, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>

11. <span data-ttu-id="bb1b6-156">W głównym pliku **Web. config** przejdź do  **\<wpisu > System. IdentityModel** .</span><span class="sxs-lookup"><span data-stu-id="bb1b6-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="bb1b6-157">W IdentityConfiguration elementy > Dodaj następujący wiersz i Zapisz plik:  **\<**</span><span class="sxs-lookup"><span data-stu-id="bb1b6-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>

    ```xml
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />
    ```

## <a name="step-3--test-your-solution"></a><span data-ttu-id="bb1b6-158">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bb1b6-158">Step 3 – Test Your Solution</span></span>

<span data-ttu-id="bb1b6-159">W tym kroku nastąpi przetestowanie aplikacji ASP.NET Web Forms i sprawdzenie, czy oświadczenia są wyświetlane, gdy użytkownik loguje się przy użyciu uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>

#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="bb1b6-160">Aby przetestować aplikację formularzy sieci Web ASP.NET dla oświadczeń przy użyciu uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="bb1b6-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>

1. <span data-ttu-id="bb1b6-161">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="bb1b6-162">Powinna zostać wyświetlona *wartość default. aspx*.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-162">You should be presented with *Default.aspx*.</span></span>

2. <span data-ttu-id="bb1b6-163">Na stronie *default. aspx* powinna zostać wyświetlona tabela poniżej nagłówka **oświadczeń** , która zawiera informacje o wystawce **, OriginalIssuer**, **typie**, **wartości**i **ValueType** oświadczenia dotyczące Twojego konta.</span><span class="sxs-lookup"><span data-stu-id="bb1b6-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="bb1b6-164">Ostatni wiersz powinien być przedstawiony w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bb1b6-164">The last row should be presented in the following way:</span></span>

    ||||||
    |-|-|-|-|-|
    |<span data-ttu-id="bb1b6-165">URZĄD LOKALNY</span><span class="sxs-lookup"><span data-stu-id="bb1b6-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="bb1b6-166">URZĄD LOKALNY</span><span class="sxs-lookup"><span data-stu-id="bb1b6-166">LOCAL AUTHORITY</span></span>|`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`|<span data-ttu-id="bb1b6-167">Administrator</span><span class="sxs-lookup"><span data-stu-id="bb1b6-167">Admin</span></span>|<https://www.w3.org/2001/XMLSchema#string>|
