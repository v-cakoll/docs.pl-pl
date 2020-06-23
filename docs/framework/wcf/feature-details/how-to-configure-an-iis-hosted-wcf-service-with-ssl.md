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
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Instrukcje: konfigurowanie usługi WCF hostowanej przez Internetowe usługi informacyjne za pomocą protokołu SSL
W tym temacie opisano sposób konfigurowania usługi WCF hostowanej przez usługi IIS do korzystania z zabezpieczeń transportu HTTP. Zabezpieczenia transportu HTTP wymagają zarejestrowania certyfikatu SSL w usługach IIS. Jeśli nie masz certyfikatu SSL, możesz użyć usług IIS do wygenerowania certyfikatu testowego. Następnie należy dodać powiązanie SSL do witryny sieci Web i skonfigurować właściwości uwierzytelniania witryny sieci Web. Na koniec należy skonfigurować usługę WCF do korzystania z protokołu HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Tworzenie certyfikatu z podpisem własnym  
  
1. Otwórz Menedżera Internet Information Services (inetmgr.exe) i wybierz nazwę komputera w widoku drzewa po lewej stronie. Po prawej stronie ekranu wybierz pozycję Certyfikaty serwera.  
  
     ![Ekran główny Menedżera usług IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2. W oknie Certyfikaty serwera kliknij pozycję Utwórz certyfikat z podpisem **własnym....** Powiązań.  
  
     ![Tworzenie certyfikatu z podpisem własnym&#45;przy użyciu usług IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3. Wprowadź przyjazną nazwę certyfikatu z podpisem własnym, a następnie kliknij przycisk **OK**.  
  
     ![Okno dialogowe Tworzenie certyfikatu z podpisem własnym&#45;](media/mg-mycert.jpg "mg_MyCert")  
  
     Nowo utworzone szczegóły certyfikatu z podpisem własnym są teraz wyświetlane w oknie **Certyfikaty serwera** .  
  
     ![Okno certyfikatu serwera](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Wygenerowany certyfikat jest instalowany w magazynie zaufanych głównych urzędów certyfikacji.  
  
### <a name="add-ssl-binding"></a>Dodawanie powiązania SSL  
  
1. W programie Internet Information Services Manager rozwiń folder **Lokacje** , a następnie folder **Domyślna witryna sieci Web** w widoku drzewa po lewej stronie ekranu.  
  
2. Kliknij pozycję **powiązania....** Link w sekcji **działania** w prawej górnej części okna.  
  
     ![Dodawanie powiązania SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3. W oknie powiązania witryny kliknij przycisk **Dodaj** .  
  
     ![Okno dialogowe powiązań witryny](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4. W oknie dialogowym **Dodawanie powiązania witryny** wybierz opcję HTTPS dla typu i przyjaznej nazwy certyfikatu z podpisem własnym, który właśnie został utworzony.  
  
     ![Przykład powiązania witryny](media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Skonfiguruj katalog wirtualny dla protokołu SSL  
  
1. W programie Internet Information Services Manager wybierz katalog wirtualny zawierający bezpieczną usługę WCF.  
  
2. W środkowym okienku okna wybierz pozycję **Ustawienia protokołu SSL** w sekcji IIS.  
  
     ![Ustawienia protokołu SSL dla katalogu wirtualnego](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3. W okienku Ustawienia protokołu SSL zaznacz pole wyboru **Wymagaj protokołu SSL** , a następnie kliknij link **Zastosuj** w sekcji **Akcje** po prawej stronie ekranu.  
  
     ![Ustawienia protokołu SSL katalogu wirtualnego](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Konfigurowanie usługi WCF na potrzeby zabezpieczeń transportu HTTP  
  
1. W web.config usługi WCF Skonfiguruj powiązanie HTTP do korzystania z zabezpieczeń transportu, jak pokazano w poniższym kodzie XML.  
  
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
  
2. Określ punkt końcowy usługi i usługi, jak pokazano w poniższym kodzie XML.  
  
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
 Poniżej znajduje się kompletny przykład pliku web.config dla usługi WCF korzystającej z zabezpieczeń transportu HTTP  
  
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

- [Hostowanie przez Internetowe usługi informacyjne](hosting-in-internet-information-services.md)
- [Instrukcje dotyczące hostowania internetowej usługi informacyjnej](../samples/internet-information-service-hosting-instructions.md)
- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](internet-information-services-hosting-best-practices.md)
- [Hostowanie usług IIS przy użyciu kodu wbudowanego](../samples/iis-hosting-using-inline-code.md)
