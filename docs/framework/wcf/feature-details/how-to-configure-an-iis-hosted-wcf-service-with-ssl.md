---
title: 'Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: fb3e87021c3dce1172250f33fd302916920af74d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597231"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="ab4ab-102">Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="ab4ab-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="ab4ab-103">W tym temacie opisano sposób konfigurowania usługi WCF hostowanej przez usługi IIS do korzystania z zabezpieczeń transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="ab4ab-104">Zabezpieczenia transportu HTTP wymagają zarejestrowania certyfikatu SSL w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="ab4ab-105">Jeśli nie masz certyfikatu SSL, możesz użyć usług IIS do wygenerowania certyfikatu testowego.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="ab4ab-106">Następnie należy dodać powiązanie SSL do witryny sieci Web i skonfigurować właściwości uwierzytelniania witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="ab4ab-107">Na koniec należy skonfigurować usługę WCF do korzystania z protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="ab4ab-108">Tworzenie certyfikatu z podpisem własnym</span><span class="sxs-lookup"><span data-stu-id="ab4ab-108">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="ab4ab-109">Otwórz program Internet Information Services Manager (inetmgr. exe), a następnie wybierz nazwę komputera w widoku drzewa po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="ab4ab-110">Po prawej stronie ekranu wybierz pozycję Certyfikaty serwera.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="ab4ab-111">![Ekran główny Menedżera usług IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-111">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="ab4ab-112">W oknie Certyfikaty serwera kliknij pozycję Utwórz certyfikat z podpisem **własnym....**</span><span class="sxs-lookup"><span data-stu-id="ab4ab-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="ab4ab-113">Powiązań.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-113">Link.</span></span>  
  
     <span data-ttu-id="ab4ab-114">![Tworzenie certyfikatu z podpisem własnym&#45;przy użyciu usług IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-114">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="ab4ab-115">Wprowadź przyjazną nazwę certyfikatu z podpisem własnym, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="ab4ab-116">![Okno dialogowe Tworzenie certyfikatu z podpisem własnym&#45;](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-116">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="ab4ab-117">Nowo utworzone szczegóły certyfikatu z podpisem własnym są teraz wyświetlane w oknie **Certyfikaty serwera** .</span><span class="sxs-lookup"><span data-stu-id="ab4ab-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="ab4ab-118">![Okno certyfikatu serwera](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-118">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="ab4ab-119">Wygenerowany certyfikat jest instalowany w magazynie zaufanych głównych urzędów certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="ab4ab-120">Dodawanie powiązania SSL</span><span class="sxs-lookup"><span data-stu-id="ab4ab-120">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="ab4ab-121">W programie Internet Information Services Manager rozwiń folder **Lokacje** , a następnie folder **Domyślna witryna sieci Web** w widoku drzewa po lewej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="ab4ab-122">Kliknij pozycję **powiązania....**</span><span class="sxs-lookup"><span data-stu-id="ab4ab-122">Click the **Bindings….**</span></span> <span data-ttu-id="ab4ab-123">Link w sekcji **działania** w prawej górnej części okna.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="ab4ab-124">![Dodawanie powiązania SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-124">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="ab4ab-125">W oknie powiązania witryny kliknij przycisk **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="ab4ab-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="ab4ab-126">![Okno dialogowe powiązań witryny](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-126">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="ab4ab-127">W oknie dialogowym **Dodawanie powiązania witryny** wybierz opcję HTTPS dla typu i przyjaznej nazwy certyfikatu z podpisem własnym, który właśnie został utworzony.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="ab4ab-128">![Przykład powiązania witryny](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-128">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="ab4ab-129">Skonfiguruj katalog wirtualny dla protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="ab4ab-129">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="ab4ab-130">W programie Internet Information Services Manager wybierz katalog wirtualny zawierający bezpieczną usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="ab4ab-131">W środkowym okienku okna wybierz pozycję **Ustawienia protokołu SSL** w sekcji IIS.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="ab4ab-132">![Ustawienia protokołu SSL dla katalogu wirtualnego](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-132">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="ab4ab-133">W okienku Ustawienia protokołu SSL zaznacz pole wyboru **Wymagaj protokołu SSL** , a następnie kliknij link **Zastosuj** w sekcji **Akcje** po prawej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="ab4ab-134">![Ustawienia protokołu SSL katalogu wirtualnego](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="ab4ab-134">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="ab4ab-135">Konfigurowanie usługi WCF na potrzeby zabezpieczeń transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="ab4ab-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="ab4ab-136">W pliku Web. config usługi WCF Skonfiguruj powiązanie HTTP do korzystania z zabezpieczeń transportu, jak pokazano w poniższym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2. <span data-ttu-id="ab4ab-137">Określ punkt końcowy usługi i usługi, jak pokazano w poniższym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="ab4ab-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="ab4ab-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab4ab-138">Example</span></span>  
 <span data-ttu-id="ab4ab-139">Poniżej znajduje się kompletny przykład pliku Web. config dla usługi WCF korzystającej z zabezpieczeń transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="ab4ab-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab4ab-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab4ab-140">See also</span></span>

- [<span data-ttu-id="ab4ab-141">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="ab4ab-141">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="ab4ab-142">Instrukcje dotyczące hostowania internetowej usługi informacyjnej</span><span class="sxs-lookup"><span data-stu-id="ab4ab-142">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="ab4ab-143">Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych</span><span class="sxs-lookup"><span data-stu-id="ab4ab-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="ab4ab-144">Hostowanie usług IIS przy użyciu kodu wbudowanego</span><span class="sxs-lookup"><span data-stu-id="ab4ab-144">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
