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
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL
W tym temacie opisano sposób konfigurowania usługi WCF hostowanej przez usługi IIS do używania zabezpieczeń transportu HTTP. Zabezpieczenia transportu HTTP wymaga certyfikatu SSL w celu zarejestrowana w programie IIS. Jeśli nie masz certyfikat SSL, usługi IIS można użyć do wygenerowania certyfikatu testowego. Następnie należy dodać powiązanie protokołu SSL do witryny sieci web i skonfigurować właściwości uwierzytelniania witryny sieci web. Na koniec należy skonfigurować usługi WCF do używania protokołu HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Tworzenie certyfikatu z podpisem własnym  
  
1.  Otwórz Menedżera internetowych usług informacyjnych (inetmgr.exe), a następnie wybierz nazwę komputera w widoku drzewa po lewej stronie. Po prawej stronie ekranu wybierz certyfikaty serwera  
  
     ![Ekranu głównego menedżera usług IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  Kliknij w oknie Certyfikaty serwera **Utwórz certyfikat z podpisem własnym...** łącze.  
  
     ![Tworzenie własnym&#45;podpisany certyfikat z usługami IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  Wprowadź przyjazną nazwę certyfikatu z podpisem własnym, a następnie kliknij przycisk **OK**.  
  
     ![Utwórz własny&#45;okna dialogowego certyfikatu podpisanego](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     Szczegóły nowo utworzonego certyfikatu z podpisem własnym są teraz wyświetlane w **certyfikaty serwera** okna.  
  
     ![Okno certyfikatu serwera](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Wygenerowany certyfikat został zainstalowany w zaufanych głównych urzędów certyfikacji przechowywane.  
  
### <a name="add-ssl-binding"></a>Dodaj powiązanie SSL  
  
1.  Nadal w Internet Information Services Manager, rozwiń węzeł **witryn** folder i następnie **domyślna witryna sieci Web** folder w widoku drzewa po lewej stronie ekranu.  
  
2.  Kliknij przycisk **powiązania...** Łącze w **akcje** sekcji w prawym górnym części okna.  
  
     ![Dodanie wiązania SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  W oknie powiązania witryny kliknij **Dodaj** przycisku.  
  
     ![Okno dialogowe powiązania witryny](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  W **Dodawanie powiązania witryny** okno dialogowe, wybierz opcję https typu oraz przyjazną nazwę certyfikatu z podpisem własnym został właśnie utworzony.  
  
     ![Przykład powiązanie witryny](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Konfiguruj katalog wirtualny dla protokołu SSL  
  
1.  W Menedżerze internetowych usług informacyjnych wybierz katalogu wirtualnego, który zawiera bezpieczne usługi WCF.  
  
2.  W środkowym okienku okna, wybierz **ustawienia protokołu SSL** w sekcji usług IIS.  
  
     ![Ustawienia protokołu SSL dla katalogu wirtualnego](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  W okienku ustawienia protokołu SSL, zaznacz **Wymagaj protokołu SSL** pole wyboru i kliknij przycisk **Zastosuj** łącze w **akcje** sekcji po prawej stronie ekranu.  
  
     ![Ustawienia protokołu SSL katalog wirtualny](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Konfigurowanie usługi WCF do zabezpieczenia transportu HTTP  
  
1.  W programie WCF web.config usługi skonfigurować powiązania protokołu HTTP w celu użycia zabezpieczeń transportu, jak pokazano w poniższym formacie XML.  
  
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
  
2.  Określ usługi i punktu końcowego usługi, jak pokazano w poniższym formacie XML.  
  
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
 Oto kompletny przykładowy plik web.config dla usługi WCF, za pomocą zabezpieczeń transportu HTTP  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [Instrukcje dotyczące hostowania internetowej usługi informacyjnej](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Hostowanie usług IIS przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
