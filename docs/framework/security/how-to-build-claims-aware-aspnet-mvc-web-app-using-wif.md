---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji internetowej MVC ASP.NET za pomocą programu WIF'
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045445"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="4e37c-102">Instrukcje: Tworzenie obsługującej oświadczenia aplikacji internetowej MVC ASP.NET za pomocą programu WIF</span><span class="sxs-lookup"><span data-stu-id="4e37c-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="4e37c-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="4e37c-103">Applies To</span></span>  
  
- <span data-ttu-id="4e37c-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="4e37c-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="4e37c-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="4e37c-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="4e37c-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="4e37c-106">Summary</span></span>  
 <span data-ttu-id="4e37c-107">Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="4e37c-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="4e37c-108">Zawiera również instrukcje dotyczące testowania prostej aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń w celu pomyślnego wdrożenia uwierzytelniania opartego na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="4e37c-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="4e37c-109">Ta instrukcja nie zawiera szczegółowych instrukcji dotyczących tworzenia usługi tokenu zabezpieczającego (STS) i zakłada, że już skonfigurowano usługę STS.</span><span class="sxs-lookup"><span data-stu-id="4e37c-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="4e37c-110">Spis treści</span><span class="sxs-lookup"><span data-stu-id="4e37c-110">Contents</span></span>  
  
- <span data-ttu-id="4e37c-111">Cele</span><span class="sxs-lookup"><span data-stu-id="4e37c-111">Objectives</span></span>  
  
- <span data-ttu-id="4e37c-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="4e37c-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="4e37c-113">Krok 1 — Tworzenie prostej aplikacji ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="4e37c-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="4e37c-114">Krok 2 — Konfigurowanie aplikacji ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="4e37c-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="4e37c-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4e37c-115">Step 3 – Test Your Solution</span></span>  
  
- <span data-ttu-id="4e37c-116">Elementy pokrewne</span><span class="sxs-lookup"><span data-stu-id="4e37c-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="4e37c-117">Cele</span><span class="sxs-lookup"><span data-stu-id="4e37c-117">Objectives</span></span>  
  
- <span data-ttu-id="4e37c-118">Konfigurowanie aplikacji sieci Web ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="4e37c-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
- <span data-ttu-id="4e37c-119">Testowanie pomyślnej aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń</span><span class="sxs-lookup"><span data-stu-id="4e37c-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="4e37c-120">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="4e37c-120">Summary of Steps</span></span>  
  
- <span data-ttu-id="4e37c-121">Krok 1 — Tworzenie prostej aplikacji ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="4e37c-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
- <span data-ttu-id="4e37c-122">Krok 2 — Konfigurowanie aplikacji ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="4e37c-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="4e37c-123">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4e37c-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="4e37c-124">Krok 1 — Tworzenie prostej aplikacji ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="4e37c-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="4e37c-125">W tym kroku zostanie utworzona nowa aplikacja ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="4e37c-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="4e37c-126">Aby utworzyć prostą aplikację ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="4e37c-126">To create simple ASP.NET MVC application</span></span>  
  
1. <span data-ttu-id="4e37c-127">Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.</span><span class="sxs-lookup"><span data-stu-id="4e37c-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="4e37c-128">W oknie **Nowy projekt** kliknij pozycję **ASP.NET aplikacji sieci Web MVC 3**.</span><span class="sxs-lookup"><span data-stu-id="4e37c-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3. <span data-ttu-id="4e37c-129">W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e37c-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4. <span data-ttu-id="4e37c-130">W oknie dialogowym **Nowy projekt ASP.NET MVC 3** wybierz pozycję **aplikacja internetowa** z dostępnych szablonów, upewnij się, że jest ustawiony **aparat widoku** **Razor**, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4e37c-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5. <span data-ttu-id="4e37c-131">Gdy zostanie otwarty nowy projekt, kliknij prawym przyciskiem myszy projekt **TestApp** w **Eksplorator rozwiązań** i wybierz opcję **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="4e37c-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6. <span data-ttu-id="4e37c-132">Na stronie właściwości projektu kliknij kartę **Sieć Web** po lewej stronie i upewnij się, że wybrano opcję **Użyj lokalnego serwera sieci Web usług IIS** .</span><span class="sxs-lookup"><span data-stu-id="4e37c-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="4e37c-133">Krok 2 — Konfigurowanie aplikacji ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="4e37c-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="4e37c-134">W tym kroku dodasz wpisy konfiguracyjne do pliku konfiguracyjnego *Web. config* aplikacji sieci Web ASP.NET MVC, aby zapewnić obsługę oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="4e37c-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="4e37c-135">Aby skonfigurować aplikację ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="4e37c-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="4e37c-136">Dodaj następujące definicje sekcji konfiguracji do pliku konfiguracyjnego *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="4e37c-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="4e37c-137">Definiują sekcje konfiguracyjne wymagane przez program Windows Identity Foundation.</span><span class="sxs-lookup"><span data-stu-id="4e37c-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="4e37c-138">Dodaj definicje bezpośrednio po  **\<elemencie Configuration >** otwierającym:</span><span class="sxs-lookup"><span data-stu-id="4e37c-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="4e37c-139">Dodaj **lokalizację > elementu, który umożliwia dostęp do metadanych federacji aplikacji: \<**</span><span class="sxs-lookup"><span data-stu-id="4e37c-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="4e37c-140">Dodaj następujące wpisy konfiguracji w  **\<elementach system. Web >** , aby odmówić użytkowników, wyłączyć uwierzytelnianie natywne i włączyć WIF do zarządzania uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="4e37c-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="4e37c-141">Dodaj następujące wpisy konfiguracji powiązane z usługą Windows Identity Foundation i upewnij się, że adres URL i numer portu aplikacji ASP.NET są zgodne z wartościami we  **\<wpisie audienceUris >** , atrybut obszaru  **\<wsFederation >** element i atrybut odpowiedzi elementu wsFederation >.  **\<**</span><span class="sxs-lookup"><span data-stu-id="4e37c-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="4e37c-142">Upewnij się również, że wartość **wystawcy** mieści się w adresie URL usługi tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="4e37c-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
5. <span data-ttu-id="4e37c-143">Dodaj odwołanie do <xref:System.IdentityModel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="4e37c-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6. <span data-ttu-id="4e37c-144">Skompiluj rozwiązanie, aby upewnić się, że wystąpiły błędy.</span><span class="sxs-lookup"><span data-stu-id="4e37c-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="4e37c-145">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4e37c-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="4e37c-146">W tym kroku przetestujesz aplikację sieci Web ASP.NET MVC skonfigurowaną pod kątem uwierzytelniania opartego na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="4e37c-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="4e37c-147">Aby przeprowadzić podstawowy test, należy dodać prosty kod, który wyświetla oświadczenia w tokenie wystawionym przez usługę tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="4e37c-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="4e37c-148">Aby przetestować aplikację ASP.NET MVC na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="4e37c-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="4e37c-149">W **Eksplorator rozwiązań**rozwiń folder **controllers** i Otwórz plik *HomeController.cs* w edytorze.</span><span class="sxs-lookup"><span data-stu-id="4e37c-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="4e37c-150">Dodaj następujący kod do metody **index** :</span><span class="sxs-lookup"><span data-stu-id="4e37c-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. <span data-ttu-id="4e37c-151">W **Eksplorator rozwiązań** rozwiń **Widok widoki** , a następnie folder Foldery **Główne** i Otwórz plik *index. cshtml* w edytorze.</span><span class="sxs-lookup"><span data-stu-id="4e37c-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="4e37c-152">Usuń jego zawartość i Dodaj następujące znaczniki:</span><span class="sxs-lookup"><span data-stu-id="4e37c-152">Delete its contents and add the following markup:</span></span>  
  
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
  
3. <span data-ttu-id="4e37c-153">Uruchom rozwiązanie, naciskając klawisz **F5** .</span><span class="sxs-lookup"><span data-stu-id="4e37c-153">Run the solution by pressing the **F5** key.</span></span>  
  
4. <span data-ttu-id="4e37c-154">Powinna zostać wyświetlona strona zawierająca oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="4e37c-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="4e37c-155">Elementy pokrewne</span><span class="sxs-lookup"><span data-stu-id="4e37c-155">Related Items</span></span>  
  
- [<span data-ttu-id="4e37c-156">Instrukcje: Tworzenie aplikacji opartych na oświadczeniach ASP.NET Web Forms przy użyciu WIF</span><span class="sxs-lookup"><span data-stu-id="4e37c-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
