---
title: 'Instrukcje: Tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF'
ms.date: 03/30/2017
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
author: BrucePerlerMS
ms.openlocfilehash: 82b0649a7324987581cc3c97570a0fc42ffdf6d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941298"
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="e35f8-102">Instrukcje: Tworzenie obsługującej oświadczenia aplikacji formularzy internetowych ASP.NET za pomocą programu WIF</span><span class="sxs-lookup"><span data-stu-id="e35f8-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="e35f8-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="e35f8-103">Applies To</span></span>  
  
- <span data-ttu-id="e35f8-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="e35f8-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="e35f8-105">ASP.NET® Web Forms</span><span class="sxs-lookup"><span data-stu-id="e35f8-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="e35f8-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="e35f8-106">Summary</span></span>  
 <span data-ttu-id="e35f8-107">Ten sposób zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostych aplikacji opartych na oświadczeniach ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="e35f8-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="e35f8-108">Zawiera również instrukcje dotyczące testowania prostej aplikacji opartej na oświadczeniach ASP.NET Web Forms w celu pomyślnego wdrożenia uwierzytelniania federacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e35f8-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="e35f8-109">Ta instrukcja nie zawiera szczegółowych instrukcji dotyczących tworzenia usługi tokenu zabezpieczającego (STS) i zakłada, że już skonfigurowano usługę STS.</span><span class="sxs-lookup"><span data-stu-id="e35f8-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="e35f8-110">Spis treści</span><span class="sxs-lookup"><span data-stu-id="e35f8-110">Contents</span></span>  
  
- <span data-ttu-id="e35f8-111">Cele</span><span class="sxs-lookup"><span data-stu-id="e35f8-111">Objectives</span></span>  
  
- <span data-ttu-id="e35f8-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="e35f8-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="e35f8-113">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="e35f8-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="e35f8-114">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="e35f8-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
- <span data-ttu-id="e35f8-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e35f8-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="e35f8-116">Cele</span><span class="sxs-lookup"><span data-stu-id="e35f8-116">Objectives</span></span>  
  
- <span data-ttu-id="e35f8-117">Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="e35f8-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
- <span data-ttu-id="e35f8-118">Testowanie pomyślnej aplikacji formularzy sieci Web ASP.NET obsługujących oświadczenia</span><span class="sxs-lookup"><span data-stu-id="e35f8-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="e35f8-119">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="e35f8-119">Summary of Steps</span></span>  
  
- <span data-ttu-id="e35f8-120">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="e35f8-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
- <span data-ttu-id="e35f8-121">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania federacyjnego</span><span class="sxs-lookup"><span data-stu-id="e35f8-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
- <span data-ttu-id="e35f8-122">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e35f8-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="e35f8-123">Krok 1 — Tworzenie prostej aplikacji ASP.NET Web Forms</span><span class="sxs-lookup"><span data-stu-id="e35f8-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="e35f8-124">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="e35f8-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="e35f8-125">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e35f8-125">To create a simple ASP.NET application</span></span>  
  
1. <span data-ttu-id="e35f8-126">Uruchom program Visual Studio i kliknij kolejno pozycje **plik**, **Nowy**i **projekt**.</span><span class="sxs-lookup"><span data-stu-id="e35f8-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2. <span data-ttu-id="e35f8-127">W oknie **Nowy projekt** kliknij pozycję **ASP.NET Web Forms aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="e35f8-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3. <span data-ttu-id="e35f8-128">W polu **Nazwa**wprowadź `TestApp` i naciśnij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e35f8-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="e35f8-129">Krok 2 — Konfigurowanie aplikacji formularzy sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="e35f8-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="e35f8-130">W tym kroku dodasz wpisy konfiguracyjne do pliku konfiguracyjnego *Web. config* aplikacji ASP.NET Web Forms, aby zapewnić obsługę oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="e35f8-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="e35f8-131">Aby skonfigurować aplikację ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="e35f8-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="e35f8-132">Dodaj następujące wpisy sekcji konfiguracji do pliku konfiguracyjnego *Web. config* bezpośrednio po  **\<elemencie Configuration >** otwierającym:</span><span class="sxs-lookup"><span data-stu-id="e35f8-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. <span data-ttu-id="e35f8-133">Dodaj **lokalizację > elementu, który umożliwia dostęp do metadanych federacji aplikacji: \<**</span><span class="sxs-lookup"><span data-stu-id="e35f8-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3. <span data-ttu-id="e35f8-134">Dodaj następujące wpisy konfiguracji w  **\<elementach system. Web >** , aby odmówić użytkowników, wyłączyć uwierzytelnianie natywne i włączyć WIF do zarządzania uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="e35f8-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. <span data-ttu-id="e35f8-135">Dodaj element System. WebServer >, który definiuje moduły uwierzytelniania federacyjnego.  **\<**</span><span class="sxs-lookup"><span data-stu-id="e35f8-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="e35f8-136">Należy zauważyć, że atrybut *PublicKeyToken* musi być taki sam jak  **\<** atrybut PublicKeyToken dla wpisów configSections > dodane wcześniej:</span><span class="sxs-lookup"><span data-stu-id="e35f8-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5. <span data-ttu-id="e35f8-137">Dodaj następujące wpisy konfiguracji powiązane z usługą Windows Identity Foundation i upewnij się, że adres URL i numer portu aplikacji ASP.NET są zgodne z wartościami we  **\<wpisie audienceUris >** , atrybut obszaru  **\<wsFederation >** element i atrybut odpowiedzi elementu wsFederation >.  **\<**</span><span class="sxs-lookup"><span data-stu-id="e35f8-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="e35f8-138">Upewnij się również, że wartość wystawcy mieści się w adresie URL usługi tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="e35f8-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
            <cookieHandler requireSsl="true" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="true" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
6. <span data-ttu-id="e35f8-139">Dodaj odwołanie do <xref:System.IdentityModel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="e35f8-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7. <span data-ttu-id="e35f8-140">Skompiluj rozwiązanie, aby upewnić się, że nie ma żadnych błędów.</span><span class="sxs-lookup"><span data-stu-id="e35f8-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="e35f8-141">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e35f8-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="e35f8-142">W tym kroku zostanie przetestowana aplikacja formularzy sieci Web ASP.NET skonfigurowana pod kątem uwierzytelniania opartego na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="e35f8-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="e35f8-143">Aby przeprowadzić podstawowy test, należy dodać kod, który będzie wyświetlał oświadczenia w tokenie wystawionym przez usługę tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="e35f8-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="e35f8-144">Aby przetestować aplikację formularza sieci Web ASP.NET na potrzeby uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="e35f8-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1. <span data-ttu-id="e35f8-145">Otwórz plik **default. aspx** w projekcie **TestApp** i Zastąp istniejący znacznik następującym znacznikiem:</span><span class="sxs-lookup"><span data-stu-id="e35f8-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2. <span data-ttu-id="e35f8-146">Zapisz plik **default. aspx**, a następnie otwórz jego kod w pliku o nazwie **default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="e35f8-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e35f8-147">**Default.aspx.cs** może być ukryty poniżej **default. aspx** w Eksplorator rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="e35f8-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="e35f8-148">Jeśli **default.aspx.cs** nie jest widoczny, rozwiń plik **default. aspx** , klikając trójkąt obok niego.</span><span class="sxs-lookup"><span data-stu-id="e35f8-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3. <span data-ttu-id="e35f8-149">Zastąp istniejący kod w metodzie **Page_Load** **default.aspx.cs** następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="e35f8-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4. <span data-ttu-id="e35f8-150">Zapisz **default.aspx.cs**i skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e35f8-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5. <span data-ttu-id="e35f8-151">Uruchom rozwiązanie, naciskając klawisz **F5** .</span><span class="sxs-lookup"><span data-stu-id="e35f8-151">Run the solution by pressing the **F5** key.</span></span>  
  
6. <span data-ttu-id="e35f8-152">Powinna zostać wyświetlona strona zawierająca oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="e35f8-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
