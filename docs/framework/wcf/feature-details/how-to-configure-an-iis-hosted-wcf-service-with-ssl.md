---
title: "Porady: Konfigurowanie usługi WCF hostowanych przez usługi IIS przy użyciu protokołu SSL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cb6a0b7913434be70efdc5af780980b971b5bc6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="3c5c6-102">Porady: Konfigurowanie usługi WCF hostowanych przez usługi IIS przy użyciu protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="3c5c6-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="3c5c6-103">W tym temacie opisano konfigurowanie usługi WCF hostowanych przez usługi IIS, aby użyć zabezpieczeń transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="3c5c6-104">Zabezpieczenia transportu HTTP wymaga certyfikatu SSL do zarejestrowana w programie IIS.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="3c5c6-105">Jeśli nie ma certyfikatu SSL można używać usług IIS do wygenerowania certyfikatu testowego.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="3c5c6-106">Następnie musi dodać powiązanie protokołu SSL do witryny sieci web i skonfiguruj właściwości uwierzytelniania witryny sieci web.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="3c5c6-107">Na koniec należy skonfigurować usługi WCF do używania protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="3c5c6-108">Tworzenie certyfikatu z podpisem własnym</span><span class="sxs-lookup"><span data-stu-id="3c5c6-108">Creating a Self-Signed Certificate</span></span>  
  
1.  <span data-ttu-id="3c5c6-109">Otwórz Menedżera internetowych usług informacyjnych (inetmgr.exe), a następnie wybierz nazwę komputera w widoku drzewa po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="3c5c6-110">Po prawej stronie ekranu wybierz certyfikaty serwera</span><span class="sxs-lookup"><span data-stu-id="3c5c6-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="3c5c6-111">![Ekran głównej Menedżera usług IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-111">![IIS Manager Home Screen](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2.  <span data-ttu-id="3c5c6-112">Kliknij w oknie Certyfikaty serwera **Tworzenie certyfikatu z podpisem własnym...**</span><span class="sxs-lookup"><span data-stu-id="3c5c6-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="3c5c6-113">Łącze.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-113">Link.</span></span>  
  
     <span data-ttu-id="3c5c6-114">![Tworzenie własnym &#45; podpisany certyfikat z programem IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-114">![Creating a self&#45;signed certificate with IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3.  <span data-ttu-id="3c5c6-115">Wprowadź przyjazną nazwę certyfikatu z podpisem własnym, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="3c5c6-116">![Utwórz własny &#45; Okno dialogowe certyfikatu podpisanego](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="3c5c6-117">Szczegóły nowo utworzonego certyfikatu z podpisem własnym są wyświetlane w **certyfikaty serwera** okna.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="3c5c6-118">![Okno certyfikatu serwera](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-118">![Server Certificate Window](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="3c5c6-119">Wygenerowany certyfikat został zainstalowany w zaufane główne urzędy certyfikacji przechowywania.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="3c5c6-120">Dodaj powiązanie SSL</span><span class="sxs-lookup"><span data-stu-id="3c5c6-120">Add SSL Binding</span></span>  
  
1.  <span data-ttu-id="3c5c6-121">W Menedżerze internetowych usług informacyjnych, rozwiń węzeł **witryny** folder, a następnie **domyślna witryna sieci Web** folderu w widoku drzewa po lewej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2.  <span data-ttu-id="3c5c6-122">Kliknij przycisk **powiązań...**</span><span class="sxs-lookup"><span data-stu-id="3c5c6-122">Click the **Bindings….**</span></span> <span data-ttu-id="3c5c6-123">Łącze w **akcje** sekcji w prawym górnym części okna.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="3c5c6-124">![Dodawanie powiązania SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-124">![Adding an SSL binding](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3.  <span data-ttu-id="3c5c6-125">W oknie powiązania witryny kliknij **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="3c5c6-126">![Okno dialogowe powiązania witryny](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-126">![Site Bindings Dialog](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4.  <span data-ttu-id="3c5c6-127">W **Dodawanie powiązania witryny** okno dialogowe, wybierz https typu oraz przyjazną nazwę certyfikatu z podpisem własnym właśnie utworzone.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="3c5c6-128">![Przykład powiązanie witryny](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-128">![Site binding example](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="3c5c6-129">Skonfiguruj katalog wirtualny dla protokołu SSL</span><span class="sxs-lookup"><span data-stu-id="3c5c6-129">Configure Virtual Directory for SSL</span></span>  
  
1.  <span data-ttu-id="3c5c6-130">W Menedżerze internetowych usług informacyjnych wybierz katalogu wirtualnego, który zawiera bezpiecznego usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2.  <span data-ttu-id="3c5c6-131">W środkowym okienku okna, wybierz **ustawienia protokołu SSL** w sekcji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="3c5c6-132">![Ustawienia protokołu SSL dla katalogu wirtualnego](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-132">![SSL Settings for virtual directory](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3.  <span data-ttu-id="3c5c6-133">W okienku ustawień protokołu SSL, wybierz **Wymagaj protokołu SSL** wyboru i kliknij przycisk **Zastosuj** łącze w **akcje** sekcji po prawej stronie ekranu.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="3c5c6-134">![Ustawienia protokołu SSL katalog wirtualny](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="3c5c6-134">![Virtual directory SSL settings](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="3c5c6-135">Konfigurowanie usługi WCF dla zabezpieczeń transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="3c5c6-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1.  <span data-ttu-id="3c5c6-136">W programie WCF web.config usługi skonfigurować wiązanie HTTP, aby użyć zabezpieczeń transportu, jak pokazano w poniższych XML.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2.  <span data-ttu-id="3c5c6-137">Określ usługi, a punkt końcowy usługi, jak pokazano w poniższych XML.</span><span class="sxs-lookup"><span data-stu-id="3c5c6-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="3c5c6-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c5c6-138">Example</span></span>  
 <span data-ttu-id="3c5c6-139">Poniżej znajduje się pełny przykład pliku web.config dla usługi WCF, za pomocą zabezpieczeń transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="3c5c6-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c5c6-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c5c6-140">See Also</span></span>  
 [<span data-ttu-id="3c5c6-141">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="3c5c6-141">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="3c5c6-142">Informacje o usługi instrukcje dotyczące hostowania internetowej</span><span class="sxs-lookup"><span data-stu-id="3c5c6-142">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="3c5c6-143">Internetowe usługi informacyjne najlepsze rozwiązania dotyczące hostowania</span><span class="sxs-lookup"><span data-stu-id="3c5c6-143">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="3c5c6-144">Hostowanie usług IIS przy użyciu kodu wbudowanego</span><span class="sxs-lookup"><span data-stu-id="3c5c6-144">IIS Hosting Using Inline Code</span></span>](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
