---
title: 'Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 336c3800fc033cc12bd9c3fe168ae219b72cab91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214121"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="bc9e5-102">Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="bc9e5-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="bc9e5-103">W tym temacie opisano sposób konfigurowania usługi WCF hostowanej przez usługi IIS do używania zabezpieczeń transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="bc9e5-104">Zabezpieczenia transportu HTTP wymaga certyfikatu SSL w celu zarejestrowana w programie IIS.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="bc9e5-105">Jeśli nie masz certyfikat SSL, usługi IIS można użyć do wygenerowania certyfikatu testowego.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="bc9e5-106">Następnie należy dodać powiązanie protokołu SSL do witryny sieci web i skonfigurować właściwości uwierzytelniania witryny sieci web.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="bc9e5-107">Na koniec należy skonfigurować usługi WCF do używania protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="bc9e5-108">Tworzenie certyfikatu z podpisem własnym</span><span class="sxs-lookup"><span data-stu-id="bc9e5-108">Creating a Self-Signed Certificate</span></span>  
  
1.  <span data-ttu-id="bc9e5-109">Otwórz Menedżera internetowych usług informacyjnych (inetmgr.exe), a następnie wybierz nazwę komputera w widoku drzewa po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="bc9e5-110">Po prawej stronie ekranu wybierz certyfikaty serwera</span><span class="sxs-lookup"><span data-stu-id="bc9e5-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="bc9e5-111">![Ekranu głównego menedżera usług IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-111">![IIS Manager Home Screen](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2.  <span data-ttu-id="bc9e5-112">Kliknij w oknie Certyfikaty serwera **Utwórz certyfikat z podpisem własnym...**</span><span class="sxs-lookup"><span data-stu-id="bc9e5-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="bc9e5-113">łącze.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-113">Link.</span></span>  
  
     <span data-ttu-id="bc9e5-114">![Tworzenie własnym&#45;podpisany certyfikat z usługami IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-114">![Creating a self&#45;signed certificate with IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3.  <span data-ttu-id="bc9e5-115">Wprowadź przyjazną nazwę certyfikatu z podpisem własnym, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="bc9e5-116">![Utwórz własny&#45;okna dialogowego certyfikatu podpisanego](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="bc9e5-117">Szczegóły nowo utworzonego certyfikatu z podpisem własnym są teraz wyświetlane w **certyfikaty serwera** okna.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="bc9e5-118">![Okno certyfikatu serwera](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-118">![Server Certificate Window](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="bc9e5-119">Wygenerowany certyfikat został zainstalowany w zaufanych głównych urzędów certyfikacji przechowywane.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="bc9e5-120">Dodaj powiązanie SSL</span><span class="sxs-lookup"><span data-stu-id="bc9e5-120">Add SSL Binding</span></span>  
  
1.  <span data-ttu-id="bc9e5-121">Nadal w Internet Information Services Manager, rozwiń węzeł **witryn** folder i następnie **domyślna witryna sieci Web** folder w widoku drzewa po lewej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2.  <span data-ttu-id="bc9e5-122">Kliknij przycisk **powiązania...**</span><span class="sxs-lookup"><span data-stu-id="bc9e5-122">Click the **Bindings….**</span></span> <span data-ttu-id="bc9e5-123">Łącze w **akcje** sekcji w prawym górnym części okna.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="bc9e5-124">![Dodanie wiązania SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-124">![Adding an SSL binding](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3.  <span data-ttu-id="bc9e5-125">W oknie powiązania witryny kliknij **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="bc9e5-126">![Okno dialogowe powiązania witryny](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-126">![Site Bindings Dialog](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4.  <span data-ttu-id="bc9e5-127">W **Dodawanie powiązania witryny** okno dialogowe, wybierz opcję https typu oraz przyjazną nazwę certyfikatu z podpisem własnym został właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="bc9e5-128">![Przykład powiązanie witryny](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-128">![Site binding example](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="bc9e5-129">Konfiguruj katalog wirtualny dla protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="bc9e5-129">Configure Virtual Directory for SSL</span></span>  
  
1.  <span data-ttu-id="bc9e5-130">W Menedżerze internetowych usług informacyjnych wybierz katalogu wirtualnego, który zawiera bezpieczne usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2.  <span data-ttu-id="bc9e5-131">W środkowym okienku okna, wybierz **ustawienia protokołu SSL** w sekcji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="bc9e5-132">![Ustawienia protokołu SSL dla katalogu wirtualnego](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-132">![SSL Settings for virtual directory](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3.  <span data-ttu-id="bc9e5-133">W okienku ustawienia protokołu SSL, zaznacz **Wymagaj protokołu SSL** pole wyboru i kliknij przycisk **Zastosuj** łącze w **akcje** sekcji po prawej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="bc9e5-134">![Ustawienia protokołu SSL katalog wirtualny](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="bc9e5-134">![Virtual directory SSL settings](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="bc9e5-135">Konfigurowanie usługi WCF do zabezpieczenia transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="bc9e5-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1.  <span data-ttu-id="bc9e5-136">W programie WCF web.config usługi skonfigurować powiązania protokołu HTTP w celu użycia zabezpieczeń transportu, jak pokazano w poniższym formacie XML.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2.  <span data-ttu-id="bc9e5-137">Określ usługi i punktu końcowego usługi, jak pokazano w poniższym formacie XML.</span><span class="sxs-lookup"><span data-stu-id="bc9e5-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bc9e5-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc9e5-138">Example</span></span>  
 <span data-ttu-id="bc9e5-139">Oto kompletny przykładowy plik web.config dla usługi WCF, za pomocą zabezpieczeń transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="bc9e5-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc9e5-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc9e5-140">See also</span></span>

- [<span data-ttu-id="bc9e5-141">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="bc9e5-141">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="bc9e5-142">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="bc9e5-142">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="bc9e5-143">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="bc9e5-143">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="bc9e5-144">Hostowanie usług IIS przy użyciu kodu wbudowanego</span><span class="sxs-lookup"><span data-stu-id="bc9e5-144">IIS Hosting Using Inline Code</span></span>](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
