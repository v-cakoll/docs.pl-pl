---
title: 'Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL'
description: Dowiedz się, jak skonfigurować usługi WCF hostowanej przez usługi IIS do korzystania z zabezpieczeń transportu HTTP, które wymagają certyfikatu zarejestrowanego w usługach IIS.
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 8dc4692863d93e407a122c0ba93ae38323b8b213
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245261"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="5ef8f-103">Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="5ef8f-103">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="5ef8f-104">W tym temacie opisano sposób konfigurowania usługi WCF hostowanej przez usługi IIS do korzystania z zabezpieczeń transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-104">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="5ef8f-105">Zabezpieczenia transportu HTTP wymagają zarejestrowania certyfikatu SSL w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-105">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="5ef8f-106">Jeśli nie masz certyfikatu SSL, możesz użyć usług IIS do wygenerowania certyfikatu testowego.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-106">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="5ef8f-107">Następnie należy dodać powiązanie SSL do witryny sieci Web i skonfigurować właściwości uwierzytelniania witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-107">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="5ef8f-108">Na koniec należy skonfigurować usługę WCF do korzystania z protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-108">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="5ef8f-109">Tworzenie certyfikatu z podpisem własnym</span><span class="sxs-lookup"><span data-stu-id="5ef8f-109">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="5ef8f-110">Otwórz Menedżera Internet Information Services (inetmgr.exe) i wybierz nazwę komputera w widoku drzewa po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-110">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="5ef8f-111">Po prawej stronie ekranu wybierz pozycję Certyfikaty serwera.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-111">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="5ef8f-112">![Ekran główny Menedżera usług IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-112">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="5ef8f-113">W oknie Certyfikaty serwera kliknij pozycję Utwórz certyfikat z podpisem **własnym....**</span><span class="sxs-lookup"><span data-stu-id="5ef8f-113">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="5ef8f-114">Powiązań.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-114">Link.</span></span>  
  
     <span data-ttu-id="5ef8f-115">![Tworzenie certyfikatu z podpisem własnym&#45;przy użyciu usług IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-115">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="5ef8f-116">Wprowadź przyjazną nazwę certyfikatu z podpisem własnym, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-116">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="5ef8f-117">![Okno dialogowe Tworzenie certyfikatu z podpisem własnym&#45;](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-117">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="5ef8f-118">Nowo utworzone szczegóły certyfikatu z podpisem własnym są teraz wyświetlane w oknie **Certyfikaty serwera** .</span><span class="sxs-lookup"><span data-stu-id="5ef8f-118">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="5ef8f-119">![Okno certyfikatu serwera](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-119">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="5ef8f-120">Wygenerowany certyfikat jest instalowany w magazynie zaufanych głównych urzędów certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-120">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="5ef8f-121">Dodawanie powiązania SSL</span><span class="sxs-lookup"><span data-stu-id="5ef8f-121">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="5ef8f-122">W programie Internet Information Services Manager rozwiń folder **Lokacje** , a następnie folder **Domyślna witryna sieci Web** w widoku drzewa po lewej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-122">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="5ef8f-123">Kliknij pozycję **powiązania....**</span><span class="sxs-lookup"><span data-stu-id="5ef8f-123">Click the **Bindings….**</span></span> <span data-ttu-id="5ef8f-124">Link w sekcji **działania** w prawej górnej części okna.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-124">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="5ef8f-125">![Dodawanie powiązania SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-125">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="5ef8f-126">W oknie powiązania witryny kliknij przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="5ef8f-126">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="5ef8f-127">![Okno dialogowe powiązań witryny](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-127">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="5ef8f-128">W oknie dialogowym **Dodawanie powiązania witryny** wybierz opcję HTTPS dla typu i przyjaznej nazwy certyfikatu z podpisem własnym, który właśnie został utworzony.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-128">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="5ef8f-129">![Przykład powiązania witryny](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-129">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="5ef8f-130">Skonfiguruj katalog wirtualny dla protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="5ef8f-130">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="5ef8f-131">W programie Internet Information Services Manager wybierz katalog wirtualny zawierający bezpieczną usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-131">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="5ef8f-132">W środkowym okienku okna wybierz pozycję **Ustawienia protokołu SSL** w sekcji IIS.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-132">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="5ef8f-133">![Ustawienia protokołu SSL dla katalogu wirtualnego](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-133">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="5ef8f-134">W okienku Ustawienia protokołu SSL zaznacz pole wyboru **Wymagaj protokołu SSL** , a następnie kliknij link **Zastosuj** w sekcji **Akcje** po prawej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-134">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="5ef8f-135">![Ustawienia protokołu SSL katalogu wirtualnego](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="5ef8f-135">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="5ef8f-136">Konfigurowanie usługi WCF na potrzeby zabezpieczeń transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="5ef8f-136">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="5ef8f-137">W web.config usługi WCF Skonfiguruj powiązanie HTTP do korzystania z zabezpieczeń transportu, jak pokazano w poniższym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-137">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2. <span data-ttu-id="5ef8f-138">Określ punkt końcowy usługi i usługi, jak pokazano w poniższym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="5ef8f-138">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="5ef8f-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ef8f-139">Example</span></span>  
 <span data-ttu-id="5ef8f-140">Poniżej znajduje się kompletny przykład pliku web.config dla usługi WCF korzystającej z zabezpieczeń transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="5ef8f-140">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ef8f-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ef8f-141">See also</span></span>

- [<span data-ttu-id="5ef8f-142">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="5ef8f-142">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="5ef8f-143">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="5ef8f-143">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="5ef8f-144">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="5ef8f-144">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="5ef8f-145">Hostowanie usług IIS przy użyciu kodu wbudowanego</span><span class="sxs-lookup"><span data-stu-id="5ef8f-145">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
