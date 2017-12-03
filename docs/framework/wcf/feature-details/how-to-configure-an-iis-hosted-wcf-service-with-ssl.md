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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e43aca439ee354557cac42ba88599b6ea105b097
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Porady: Konfigurowanie usługi WCF hostowanych przez usługi IIS przy użyciu protokołu SSL
W tym temacie opisano konfigurowanie usługi WCF hostowanych przez usługi IIS, aby użyć zabezpieczeń transportu HTTP. Zabezpieczenia transportu HTTP wymaga certyfikatu SSL do zarejestrowana w programie IIS. Jeśli nie ma certyfikatu SSL można używać usług IIS do wygenerowania certyfikatu testowego. Następnie musi dodać powiązanie protokołu SSL do witryny sieci web i skonfiguruj właściwości uwierzytelniania witryny sieci web. Na koniec należy skonfigurować usługi WCF do używania protokołu HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Tworzenie certyfikatu z podpisem własnym  
  
1.  Otwórz Menedżera internetowych usług informacyjnych (inetmgr.exe), a następnie wybierz nazwę komputera w widoku drzewa po lewej stronie. Po prawej stronie ekranu wybierz certyfikaty serwera  
  
     ![Ekran głównej Menedżera usług IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  Kliknij w oknie Certyfikaty serwera **Tworzenie certyfikatu z podpisem własnym...** Łącze.  
  
     ![Tworzenie własnym &#45; podpisany certyfikat z programem IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  Wprowadź przyjazną nazwę certyfikatu z podpisem własnym, a następnie kliknij przycisk **OK**.  
  
     ![Utwórz własny &#45; Okno dialogowe certyfikatu podpisanego](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     Szczegóły nowo utworzonego certyfikatu z podpisem własnym są wyświetlane w **certyfikaty serwera** okna.  
  
     ![Okno certyfikatu serwera](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Wygenerowany certyfikat został zainstalowany w zaufane główne urzędy certyfikacji przechowywania.  
  
### <a name="add-ssl-binding"></a>Dodaj powiązanie SSL  
  
1.  W Menedżerze internetowych usług informacyjnych, rozwiń węzeł **witryny** folder, a następnie **domyślna witryna sieci Web** folderu w widoku drzewa po lewej stronie ekranu.  
  
2.  Kliknij przycisk **powiązań...** Łącze w **akcje** sekcji w prawym górnym części okna.  
  
     ![Dodawanie powiązania SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  W oknie powiązania witryny kliknij **Dodaj** przycisku.  
  
     ![Okno dialogowe powiązania witryny](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  W **Dodawanie powiązania witryny** okno dialogowe, wybierz https typu oraz przyjazną nazwę certyfikatu z podpisem własnym właśnie utworzone.  
  
     ![Przykład powiązanie witryny](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Skonfiguruj katalog wirtualny dla protokołu SSL  
  
1.  W Menedżerze internetowych usług informacyjnych wybierz katalogu wirtualnego, który zawiera bezpiecznego usługi WCF.  
  
2.  W środkowym okienku okna, wybierz **ustawienia protokołu SSL** w sekcji usług IIS.  
  
     ![Ustawienia protokołu SSL dla katalogu wirtualnego](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  W okienku ustawień protokołu SSL, wybierz **Wymagaj protokołu SSL** wyboru i kliknij przycisk **Zastosuj** łącze w **akcje** sekcji po prawej stronie ekranu.  
  
     ![Ustawienia protokołu SSL katalog wirtualny](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Konfigurowanie usługi WCF dla zabezpieczeń transportu HTTP  
  
1.  W programie WCF web.config usługi skonfigurować wiązanie HTTP, aby użyć zabezpieczeń transportu, jak pokazano w poniższych XML.  
  
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
  
2.  Określ usługi, a punkt końcowy usługi, jak pokazano w poniższych XML.  
  
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
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się pełny przykład pliku web.config dla usługi WCF, za pomocą zabezpieczeń transportu HTTP  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Informacje o usługi instrukcje dotyczące hostowania internetowej](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Internetowe usługi informacyjne najlepsze rozwiązania dotyczące hostowania](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Hostowanie usług IIS przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
