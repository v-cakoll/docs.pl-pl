---
title: "Porady: Tworzenie aplikacji formularzy sieci Web obsługujący oświadczenia ASP.NET za pomocą WIF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d5b81e20ed1b39c7750329718729905484eb7fa1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="8aa53-102">Porady: Tworzenie aplikacji formularzy sieci Web obsługujący oświadczenia ASP.NET za pomocą WIF</span><span class="sxs-lookup"><span data-stu-id="8aa53-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="8aa53-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="8aa53-103">Applies To</span></span>  
  
-   <span data-ttu-id="8aa53-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="8aa53-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="8aa53-105">ASP.NET® formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="8aa53-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="8aa53-106">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="8aa53-106">Summary</span></span>  
 <span data-ttu-id="8aa53-107">To instrukcje zawiera szczegółowe procedury krok po kroku dotyczące tworzenia prostej aplikacji obsługującej oświadczenia formularzy sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8aa53-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="8aa53-108">Umożliwia także instrukcje dotyczące testowania prostej aplikacji składnika ASP.NET Web Forms obsługujący oświadczenia dla pomyślnego wykonania uwierzytelniania federacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8aa53-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="8aa53-109">Ta porada nie ma szczegółowe instrukcje dotyczące tworzenia tokenu usługi zabezpieczenia (STS) i przyjęto założenie, że zostały już skonfigurowane usługi tokenu Zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="8aa53-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="8aa53-110">Spis treści</span><span class="sxs-lookup"><span data-stu-id="8aa53-110">Contents</span></span>  
  
-   <span data-ttu-id="8aa53-111">Cele</span><span class="sxs-lookup"><span data-stu-id="8aa53-111">Objectives</span></span>  
  
-   <span data-ttu-id="8aa53-112">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="8aa53-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="8aa53-113">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="8aa53-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="8aa53-114">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="8aa53-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="8aa53-115">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="8aa53-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="8aa53-116">Cele</span><span class="sxs-lookup"><span data-stu-id="8aa53-116">Objectives</span></span>  
  
-   <span data-ttu-id="8aa53-117">Konfigurowanie aplikacji składnika ASP.NET Web Forms dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="8aa53-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="8aa53-118">Testowanie pomyślne obsługujący oświadczenia aplikacji formularzy sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8aa53-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="8aa53-119">Zestawienie czynności</span><span class="sxs-lookup"><span data-stu-id="8aa53-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="8aa53-120">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="8aa53-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="8aa53-121">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla uwierzytelniania federacyjnego</span><span class="sxs-lookup"><span data-stu-id="8aa53-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
-   <span data-ttu-id="8aa53-122">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="8aa53-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="8aa53-123">Krok 1: tworzenie aplikacji formularzy sieci Web ASP.NET proste</span><span class="sxs-lookup"><span data-stu-id="8aa53-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="8aa53-124">W tym kroku utworzysz nową aplikację ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="8aa53-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="8aa53-125">Aby utworzyć prostą aplikację ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8aa53-125">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="8aa53-126">Uruchom program Visual Studio, a następnie kliknij przycisk **pliku**, **nowy**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="8aa53-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="8aa53-127">W **nowy projekt** okna, kliknij przycisk **aplikacji formularzy sieci Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="8aa53-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="8aa53-128">W **nazwa**, wprowadź `TestApp` i naciśnij klawisz **OK**.</span><span class="sxs-lookup"><span data-stu-id="8aa53-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="8aa53-129">Krok 2: Konfigurowanie aplikacji formularzy sieci Web platformy ASP.NET dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="8aa53-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="8aa53-130">W tym kroku zostanie dodania wpisów konfiguracji do *Web.config* pliku konfiguracji aplikacji składnika ASP.NET Web Forms dokonanie obsługujący oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="8aa53-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="8aa53-131">Aby skonfigurować aplikację ASP.NET do uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="8aa53-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="8aa53-132">Dodaj następujące wpisy sekcji konfiguracji do *Web.config* plik konfiguracyjny natychmiast po  **\<konfiguracji >** otwarcia elementu:</span><span class="sxs-lookup"><span data-stu-id="8aa53-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="8aa53-133">Dodaj  **\<lokalizacji >** elementu, który umożliwia dostęp do metadanych Federacji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8aa53-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="8aa53-134">Dodaj następujące pozycje konfiguracji w ramach  **\<system.web >** elementy, aby uniemożliwić użytkownikom, Wyłącz uwierzytelnianie macierzystego i Włącz WIF zarządzać uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="8aa53-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="8aa53-135">Dodaj  **\<system.webServer >** element, który definiuje modułów uwierzytelniania federacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8aa53-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="8aa53-136">Należy pamiętać, że *PublicKeyToken* atrybut musi być taka sama jak *PublicKeyToken* atrybutu dla  **\<configSections >** wpisy dodane wcześniej:</span><span class="sxs-lookup"><span data-stu-id="8aa53-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  <span data-ttu-id="8aa53-137">Dodaj następujące Windows Identity Foundation powiązane pozycje konfiguracji i upewnij się, że adres URL aplikacji platformy ASP.NET i numer portu pasują do wartości w  **\<audienceUris >** wpisu, **obszaru**  atrybutu  **\<wsFederation >** elementu i **odpowiedzi** atrybutu  **\<wsFederation >**elementu.</span><span class="sxs-lookup"><span data-stu-id="8aa53-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="8aa53-138">Ponadto upewnij się, że **wystawcy** wartość pasuje do adresu URL zabezpieczeń usługi tokenów (STS).</span><span class="sxs-lookup"><span data-stu-id="8aa53-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
6.  <span data-ttu-id="8aa53-139">Dodaj odwołanie do <xref:System.IdentityModel> zestawu.</span><span class="sxs-lookup"><span data-stu-id="8aa53-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7.  <span data-ttu-id="8aa53-140">Skompiluj rozwiązanie, aby upewnić się, że nie ma żadnych błędów.</span><span class="sxs-lookup"><span data-stu-id="8aa53-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="8aa53-141">Krok 3 — Przetestowanie rozwiązania</span><span class="sxs-lookup"><span data-stu-id="8aa53-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="8aa53-142">W tym kroku zostanie testowania aplikacji składnika ASP.NET Web Forms skonfigurowany do uwierzytelniania opartego na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="8aa53-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="8aa53-143">Aby wykonać podstawowy test, należy dodać kodu, który wyświetla oświadczenia w tokenie wystawiony przez zabezpieczenia usługi tokenów (STS).</span><span class="sxs-lookup"><span data-stu-id="8aa53-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="8aa53-144">Aby przetestować aplikację formularza sieci Web platformy ASP.NET dla uwierzytelniania opartego na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="8aa53-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="8aa53-145">Otwórz **Default.aspx** plików w obszarze **TestApp** projektu i zastąp jego istniejących znaczników następujący kod:</span><span class="sxs-lookup"><span data-stu-id="8aa53-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
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
  
2.  <span data-ttu-id="8aa53-146">Zapisz **Default.aspx**, a następnie otwórz jego kodzie pliku o nazwie **Default.aspx.cs**.</span><span class="sxs-lookup"><span data-stu-id="8aa53-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8aa53-147">**Default.aspx.cs** mogą być ukryte pod **Default.aspx** w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="8aa53-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="8aa53-148">Jeśli **Default.aspx.cs** nie jest widoczny, rozwiń węzeł **Default.aspx** , klikając trójkąt obok niej.</span><span class="sxs-lookup"><span data-stu-id="8aa53-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3.  <span data-ttu-id="8aa53-149">Zastąp istniejący kod w **Page_Load** metody **Default.aspx.cs** następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="8aa53-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
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
  
4.  <span data-ttu-id="8aa53-150">Zapisz **Default.aspx.cs**i Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="8aa53-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5.  <span data-ttu-id="8aa53-151">Uruchom rozwiązanie, naciskając klawisz **F5** klucza.</span><span class="sxs-lookup"><span data-stu-id="8aa53-151">Run the solution by pressing the **F5** key.</span></span>  
  
6.  <span data-ttu-id="8aa53-152">Powinna pojawić na stronie zostaną wyświetlone oświadczenia w tokenie, który został wystawiony przez usługę tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="8aa53-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
