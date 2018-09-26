---
title: 'Instrukcje: Przekształcanie oświadczeń przychodzących'
ms.date: 03/30/2017
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
author: BrucePerlerMS
ms.openlocfilehash: 8673b4520d9727ae1aa78ef0bc9f435defb02598
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171325"
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="4c369-102">Instrukcje: Przekształcanie oświadczeń przychodzących</span><span class="sxs-lookup"><span data-stu-id="4c369-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="4c369-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="4c369-103">Applies To</span></span>  
  
-   <span data-ttu-id="4c369-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="4c369-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="4c369-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="4c369-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="4c369-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="4c369-106">Summary</span></span>  
 <span data-ttu-id="4c369-107">Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji formularzy sieci Web programu ASP.NET obsługujących oświadczenia i przekształcanie oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="4c369-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="4c369-108">On również instrukcje testowania aplikacji, aby zweryfikować, że oświadczenia po przekształceniu są dostarczane, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="4c369-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="4c369-109">Spis treści</span><span class="sxs-lookup"><span data-stu-id="4c369-109">Contents</span></span>  
  
-   <span data-ttu-id="4c369-110">Cele</span><span class="sxs-lookup"><span data-stu-id="4c369-110">Objectives</span></span>  
  
-   <span data-ttu-id="4c369-111">Omówienie</span><span class="sxs-lookup"><span data-stu-id="4c369-111">Overview</span></span>  
  
-   <span data-ttu-id="4c369-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="4c369-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="4c369-113">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="4c369-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="4c369-114">Krok 2 — Implementowanie oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania</span><span class="sxs-lookup"><span data-stu-id="4c369-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="4c369-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4c369-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="4c369-116">Cele</span><span class="sxs-lookup"><span data-stu-id="4c369-116">Objectives</span></span>  
  
-   <span data-ttu-id="4c369-117">Skonfigurować aplikację ASP.NET Web Forms pod kątem uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="4c369-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="4c369-118">Przekształcanie oświadczeń przychodzących przez dodanie oświadczenie roli administratora</span><span class="sxs-lookup"><span data-stu-id="4c369-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="4c369-119">Testowanie aplikacji formularzy sieci Web ASP.NET, aby zobaczyć, czy działa prawidłowo</span><span class="sxs-lookup"><span data-stu-id="4c369-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="4c369-120">Omówienie</span><span class="sxs-lookup"><span data-stu-id="4c369-120">Overview</span></span>  
 <span data-ttu-id="4c369-121">Program WIF przedstawia klasę o nazwie <xref:System.Security.Claims.ClaimsAuthenticationManager> umożliwiającej użytkownikom na modyfikowanie oświadczeń, zanim zostaną one zaprezentowane na aplikację jednostki uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="4c369-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="4c369-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> Jest przydatne w przypadku separacji między uwierzytelniania i odpowiedni kod aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c369-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="4c369-123">W poniższym przykładzie przedstawiono sposób dodawania roli do roszczeń w przychodzącej <xref:System.Security.Claims.ClaimsPrincipal> , może być wymagane przez jednostkę Uzależnioną.</span><span class="sxs-lookup"><span data-stu-id="4c369-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="4c369-124">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="4c369-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="4c369-125">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="4c369-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="4c369-126">Krok 2 — Implementowanie oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania</span><span class="sxs-lookup"><span data-stu-id="4c369-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="4c369-127">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4c369-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="4c369-128">Krok 1. Tworzenie prostych aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="4c369-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="4c369-129">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="4c369-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="4c369-130">Aby utworzyć prostą aplikację platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4c369-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="4c369-131">Uruchom program Visual Studio w trybie podwyższonych uprawnień jako administrator.</span><span class="sxs-lookup"><span data-stu-id="4c369-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="4c369-132">W programie Visual Studio, kliknij przycisk **pliku**, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="4c369-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="4c369-133">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="4c369-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="4c369-134">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c369-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="4c369-135">Kliknij prawym przyciskiem myszy **TestApp** projekt **Eksploratora rozwiązań**, a następnie wybierz **tożsamościami i dostępem**.</span><span class="sxs-lookup"><span data-stu-id="4c369-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="4c369-136">**Tożsamościami i dostępem** zostanie wyświetlone okno.</span><span class="sxs-lookup"><span data-stu-id="4c369-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="4c369-137">W obszarze **dostawców**, wybierz opcję **testować swoją aplikację za pomocą lokalnej deweloperskiej usługi STS**, następnie kliknij przycisk **Zastosuj**.</span><span class="sxs-lookup"><span data-stu-id="4c369-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="4c369-138">W *Default.aspx* pliku, Zastąp istniejący kod znaczników następującym kodem, a następnie zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="4c369-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
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
  
8.  <span data-ttu-id="4c369-139">Otwórz plik związany z kodem o nazwie *Default.aspx.cs*.</span><span class="sxs-lookup"><span data-stu-id="4c369-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="4c369-140">Zastąp istniejący kod następującym kodem i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="4c369-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="4c369-141">Krok 2 — Implementowanie oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager przekształcania</span><span class="sxs-lookup"><span data-stu-id="4c369-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="4c369-142">W tym kroku spowoduje przesłonięcie funkcje domyślne w <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy, aby dodać rolę administratora do jednostki przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="4c369-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="4c369-143">Aby zaimplementować przekształcania oświadczeń przy użyciu niestandardowych ClaimsAuthenticationManager</span><span class="sxs-lookup"><span data-stu-id="4c369-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="4c369-144">W programie Visual Studio, kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj**, a następnie kliknij przycisk **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="4c369-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="4c369-145">W **Dodaj nowy projekt** wybierz **biblioteki klas** z **Visual C#** szablony list, wprowadź `ClaimsTransformation`, a następnie naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c369-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="4c369-146">Nowy projekt zostanie utworzony w folderze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4c369-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="4c369-147">Kliknij prawym przyciskiem myszy **odwołania** w obszarze **ClaimsTransformation** projektu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="4c369-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="4c369-148">W **Menadżer odwołań** wybierz **System.IdentityModel**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c369-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="4c369-149">Otwórz **Class1.cs**, lub jeśli nie istnieje, kliknij prawym przyciskiem myszy **ClaimsTransformation**, kliknij przycisk **Dodaj**, następnie kliknij przycisk **klasy...**</span><span class="sxs-lookup"><span data-stu-id="4c369-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="4c369-150">Dodaj następujące dyrektywy using do pliku kodu:</span><span class="sxs-lookup"><span data-stu-id="4c369-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="4c369-151">Dodaj następujące klasy i metody w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="4c369-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="4c369-152">Poniższy kod jest wyłącznie demonstracyjny; Upewnij się, aby zweryfikować swoje uprawnienia zamierzone, w kodzie produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="4c369-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
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
  
8.  <span data-ttu-id="4c369-153">Zapisz plik i skompiluj **ClaimsTransformation** projektu.</span><span class="sxs-lookup"><span data-stu-id="4c369-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="4c369-154">W swojej **TestApp** projektu ASP.NET, kliknij prawym przyciskiem myszy na odwołań, a następnie kliknij **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="4c369-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="4c369-155">W **Menadżer odwołań** wybierz **rozwiązania** z menu po lewej stronie wybierz **ClaimsTransformation** z wypełnione opcje, a następnie kliknij przycisk  **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c369-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="4c369-156">W katalogu głównym **Web.config** pliku, przejdź do folderu  **\<system.identityModel >** wpisu.</span><span class="sxs-lookup"><span data-stu-id="4c369-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="4c369-157">W ramach  **\<identityConfiguration >** elementów, Dodaj następujący wiersz i Zapisz plik:</span><span class="sxs-lookup"><span data-stu-id="4c369-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="4c369-158">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4c369-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="4c369-159">W tym kroku zostanie testowanie aplikacji ASP.NET Web Forms i sprawdź, czy są prezentowane oświadczenia, gdy użytkownik zaloguje się za pomocą uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="4c369-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="4c369-160">Aby przetestować aplikację ASP.NET Web Forms oświadczenia, za pomocą uwierzytelniania formularzy</span><span class="sxs-lookup"><span data-stu-id="4c369-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="4c369-161">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="4c369-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="4c369-162">Powinna pojawić się *Default.aspx*.</span><span class="sxs-lookup"><span data-stu-id="4c369-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="4c369-163">Na *Default.aspx* strony powinna zostać wyświetlona tabela poniżej **Your oświadczeń** nagłówek, który zawiera **wystawcy**, **Wystawca_oryginalny**, **Typu**, **wartość**, i **ValueType** oświadczeń informacji o Twoim koncie.</span><span class="sxs-lookup"><span data-stu-id="4c369-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="4c369-164">Ostatni wiersz powinno zostać wyświetlone w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4c369-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="4c369-165">URZĄD LOKALNY</span><span class="sxs-lookup"><span data-stu-id="4c369-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="4c369-166">URZĄD LOKALNY</span><span class="sxs-lookup"><span data-stu-id="4c369-166">LOCAL AUTHORITY</span></span>|http://schemas.microsoft.com/ws/2008/06/identity/claims/role|<span data-ttu-id="4c369-167">Administrator</span><span class="sxs-lookup"><span data-stu-id="4c369-167">Admin</span></span>|http://www.w3.org/2001/XMLSchema#string|
