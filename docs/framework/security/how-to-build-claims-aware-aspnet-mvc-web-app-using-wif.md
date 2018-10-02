---
title: 'Instrukcje: Tworzenie aplikacji sieci Web obsługującej oświadczenia platformy ASP.NET MVC przy użyciu programu WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4a003acbf4e182a0493368b586a3add229d8b526
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036005"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="1a561-102">Instrukcje: Tworzenie aplikacji sieci Web obsługującej oświadczenia platformy ASP.NET MVC przy użyciu programu WIF</span><span class="sxs-lookup"><span data-stu-id="1a561-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="1a561-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="1a561-103">Applies To</span></span>  
  
-   <span data-ttu-id="1a561-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="1a561-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="1a561-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="1a561-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="1a561-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="1a561-106">Summary</span></span>  
 <span data-ttu-id="1a561-107">Niniejszy instruktaż zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostego obsługującej oświadczenia aplikacji sieci web platformy ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="1a561-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="1a561-108">Zawiera również instrukcje dotyczące testowania prostą aplikację sieci web obsługującej oświadczenia platformy ASP.NET MVC w dla pomyślnego wdrożenia opartego na oświadczeniach uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1a561-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="1a561-109">Niniejszy instruktaż nie zawiera szczegółowych instrukcji tworzenia Usługa tokenu zabezpieczającego (STS), a przyjęto założenie, że zostały już skonfigurowane usługi tokenu Zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="1a561-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="1a561-110">Spis treści</span><span class="sxs-lookup"><span data-stu-id="1a561-110">Contents</span></span>  
  
-   <span data-ttu-id="1a561-111">Cele</span><span class="sxs-lookup"><span data-stu-id="1a561-111">Objectives</span></span>  
  
-   <span data-ttu-id="1a561-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="1a561-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="1a561-113">Krok 1 — utworzenie aplikacji proste platformy ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="1a561-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="1a561-114">Krok 2 — Konfigurowanie aplikacji platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="1a561-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="1a561-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1a561-115">Step 3 – Test Your Solution</span></span>  
  
-   <span data-ttu-id="1a561-116">Powiązane elementy</span><span class="sxs-lookup"><span data-stu-id="1a561-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="1a561-117">Cele</span><span class="sxs-lookup"><span data-stu-id="1a561-117">Objectives</span></span>  
  
-   <span data-ttu-id="1a561-118">Konfigurowanie aplikacji sieci web platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="1a561-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="1a561-119">Testowanie pomyślne obsługującej oświadczenia aplikacji sieci web platformy ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="1a561-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="1a561-120">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="1a561-120">Summary of Steps</span></span>  
  
-   <span data-ttu-id="1a561-121">Krok 1 — utworzenie aplikacji proste platformy ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="1a561-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="1a561-122">Krok 2 — Konfigurowanie aplikacji platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="1a561-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="1a561-123">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1a561-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="1a561-124">Krok 1 — utworzenie aplikacji proste platformy ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="1a561-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="1a561-125">W tym kroku utworzysz nową aplikację ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="1a561-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="1a561-126">Aby utworzyć prostą aplikację platformy ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="1a561-126">To create simple ASP.NET MVC application</span></span>  
  
1.  <span data-ttu-id="1a561-127">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **New**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="1a561-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="1a561-128">W **nowy projekt** okna, kliknij przycisk **aplikacji sieci Web programu ASP.NET MVC 3**.</span><span class="sxs-lookup"><span data-stu-id="1a561-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3.  <span data-ttu-id="1a561-129">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a561-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="1a561-130">W **nowego projektu programu ASP.NET MVC 3** okno dialogowe, wybierz opcję **aplikacji internetowej** spośród dostępnych szablonów, upewnij się, **aparat widoku** ustawiono **Razor**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="1a561-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="1a561-131">Po otwarciu nowego projektu, kliknij prawym przyciskiem myszy **TestApp** projektu w **Eksploratora rozwiązań** i wybierz **właściwości** opcji.</span><span class="sxs-lookup"><span data-stu-id="1a561-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6.  <span data-ttu-id="1a561-132">Na stronie właściwości projektu, kliknąć **Web** karcie po lewej stronie, a następnie upewnij się, że **użycia lokalnego serwera sieci Web usług IIS** opcja jest zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="1a561-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="1a561-133">Krok 2 — Konfigurowanie aplikacji platformy ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="1a561-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="1a561-134">W tym kroku dodasz wpisy konfiguracji *Web.config* pliku konfiguracji aplikacji sieci web platformy ASP.NET MVC, aby obsługujących oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="1a561-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="1a561-135">Aby skonfigurować aplikację ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="1a561-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="1a561-136">Dodaj następujące definicje konfiguracji w sekcji, aby *Web.config* pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1a561-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="1a561-137">Te definiują sekcji konfiguracji wymaganych przez program Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="1a561-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="1a561-138">Dodaj definicje natychmiast po  **\<konfiguracji >** otwarcia elementu:</span><span class="sxs-lookup"><span data-stu-id="1a561-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="1a561-139">Dodaj  **\<lokalizacja >** elementu, który umożliwia dostęp do metadanych Federacji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="1a561-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="1a561-140">Dodaj następujące wpisy konfiguracji w ramach  **\<system.web >** elementy, aby odmówić użytkownikom, Wyłącz uwierzytelnianie natywnych i włączanie programu WIF zarządzać uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="1a561-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="1a561-141">Dodaj następujące Windows Identity Foundation powiązane wpisy konfiguracji i upewnij się, że adres URL aplikacji ASP.NET i numer portu pasuje do wartości w  **\<audienceUris >** wpisu **obszaru**  atrybutu  **\<wsFederation >** elementu, a **odpowiedzi** atrybutu  **\<wsFederation >** elementu.</span><span class="sxs-lookup"><span data-stu-id="1a561-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="1a561-142">Ponadto upewnij się, że **wystawcy** pasuje do wartości adresu URL Usługa tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="1a561-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5.  <span data-ttu-id="1a561-143">Dodaj odwołanie do <xref:System.IdentityModel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="1a561-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6.  <span data-ttu-id="1a561-144">Skompiluj rozwiązanie, aby upewnić się, że ma błędów.</span><span class="sxs-lookup"><span data-stu-id="1a561-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="1a561-145">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1a561-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="1a561-146">W tym kroku przetestujesz aplikację sieci web platformy ASP.NET MVC, skonfigurowany do uwierzytelniania opartego na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="1a561-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="1a561-147">Aby wykonać podstawowy test należy dodać prosty kod, który przedstawia oświadczenia w tokenie, wystawiony przez Usługa tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="1a561-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="1a561-148">Aby przetestować aplikację ASP.NET MVC dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="1a561-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="1a561-149">W **Eksploratora rozwiązań**, rozwiń węzeł **kontrolerów** folder i Otwórz *HomeController.cs* plik w edytorze.</span><span class="sxs-lookup"><span data-stu-id="1a561-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="1a561-150">Dodaj następujący kod do **indeksu** metody:</span><span class="sxs-lookup"><span data-stu-id="1a561-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  <span data-ttu-id="1a561-151">W **Eksploratora rozwiązań** rozwiń **widoków** i następnie **Home** folderów i Otwórz *Index.cshtml* plik w edytorze.</span><span class="sxs-lookup"><span data-stu-id="1a561-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="1a561-152">Usunąć jej zawartość i Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="1a561-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3.  <span data-ttu-id="1a561-153">Uruchom rozwiązanie, naciskając klawisz **F5** klucza.</span><span class="sxs-lookup"><span data-stu-id="1a561-153">Run the solution by pressing the **F5** key.</span></span>  
  
4.  <span data-ttu-id="1a561-154">Powinno zostać wyświetlone ze stroną, które zostaną wyświetlone oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="1a561-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="1a561-155">Powiązane elementy</span><span class="sxs-lookup"><span data-stu-id="1a561-155">Related Items</span></span>  
  
-   [<span data-ttu-id="1a561-156">Instrukcje: tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF</span><span class="sxs-lookup"><span data-stu-id="1a561-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
