---
title: Zabezpieczanie klientów [WCF]
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: bfb980e629ffb8f8543937a1850430c9bf6e9199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183133"
---
# <a name="securing-clients"></a>Zabezpieczanie klientów [WCF]
W programie Windows Communication Foundation (WCF) usługa dyktuje wymagania dotyczące zabezpieczeń dla klientów. Oznacza to, że usługa określa, jaki tryb zabezpieczeń do użycia i czy klient musi podać poświadczenia. Proces zabezpieczania klienta jest zatem prosty: użyj metadanych uzyskanych z usługi (jeśli zostanie opublikowana) i skompiluj klienta. Metadane określa sposób konfigurowania klienta. Jeśli usługa wymaga, aby klient dostarczał poświadczenia, należy uzyskać poświadczenie, które pasuje do wymagań. W tym temacie omówiono proces bardziej szczegółowo. Aby uzyskać więcej informacji na temat tworzenia bezpiecznej usługi, zobacz [Zabezpieczanie usług](securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Usługa określa zabezpieczenia  
 Domyślnie powiązania WCF mają włączone funkcje zabezpieczeń. (Wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding>.) W związku z tym jeśli usługa została utworzona przy użyciu WCF, istnieje większa szansa, że zaimplementuje zabezpieczeń w celu zapewnienia uwierzytelniania, poufności i integralności. W takim przypadku metadane, które zapewnia usługa, wskazują, czego wymaga ustanowienia bezpiecznego kanału komunikacji. Jeśli metadane usługi nie zawierają żadnych wymagań dotyczących zabezpieczeń, nie ma możliwości narzucenia usługi schematu zabezpieczeń, takiego jak secure sockets Layer (SSL) za pośrednictwem protokołu HTTP. Jeśli jednak usługa wymaga od klienta dostarczenia poświadczeń, deweloper klienta, wdrażający lub administrator musi podać rzeczywiste poświadczenia, które klient będzie używał do uwierzytelniania się w usłudze.  
  
## <a name="obtaining-metadata"></a>Uzyskiwanie metadanych  
 Podczas tworzenia klienta pierwszym krokiem jest uzyskanie metadanych dla usługi, z którą klient będzie się komunikować. Można to zrobić na dwa sposoby. Po pierwsze, jeśli usługa publikuje punkt końcowy wymiany metadanych (MEX) lub udostępnia swoje metadane za pośrednictwem protokołu HTTP lub HTTPS, można pobrać metadane za pomocą [narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe),](servicemodel-metadata-utility-tool-svcutil-exe.md)które generuje zarówno pliki kodu dla klienta, jak i plik konfiguracyjny. (Aby uzyskać więcej informacji na temat korzystania z narzędzia, zobacz [Uzyskiwanie dostępu do usług przy użyciu klienta WCF](accessing-services-using-a-wcf-client.md).) Jeśli usługa nie publikuje punktu końcowego MEX, a także nie udostępnia swoich metadanych za pośrednictwem protokołu HTTP lub HTTPS, należy skontaktować się z twórcą usługi w celu uzyskania dokumentacji opisującej wymagania dotyczące zabezpieczeń i metadane.  
  
> [!IMPORTANT]
> Zaleca się, aby metadane pochodziły z zaufanego źródła i nie były modyfikowane. Metadane pobrane przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i mogą być modyfikowane. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> i <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> właściwości, użyj adresu URL twórcy usługi podane do pobrania danych przy użyciu protokołu HTTPS.  
  
## <a name="validating-security"></a>Sprawdzanie poprawności zabezpieczeń  
 Źródła metadanych można podzielić na dwie szerokie kategorie: źródła zaufania i niezaufane źródła. Jeśli ufasz źródłu i pobrałeś kod klienta i inne metadane z bezpiecznego punktu końcowego MEX tego źródła, możesz utworzyć klienta, podać mu odpowiednie poświadczenia i uruchomić go bez innych problemów.  
  
 Jeśli jednak zdecydujesz się pobrać klienta i metadane ze źródła, o których niewiele wiesz, upewnij się, że środki bezpieczeństwa są używane przez kod. Na przykład nie należy po prostu tworzyć klienta, który wysyła twoje dane osobowe lub finansowe do usługi, chyba że usługa wymaga poufności i integralności (co najmniej). Należy ufać właścicielowi usługi w zakresie, w jakim jesteś gotów ujawnić takie informacje, ponieważ takie informacje będą dla nich widoczne.  
  
 Z reguły, korzystając z kodu i metadanych z niezaufanego źródła, sprawdź kod i metadane, aby upewnić się, że spełnia wymagany poziom zabezpieczeń.  
  
## <a name="setting-a-client-credential"></a>Ustawianie poświadczeń klienta  
 Ustawianie poświadczeń klienta na kliencie składa się z dwóch kroków:  
  
1. Określ *typ poświadczeń klienta,* którego wymaga usługa. Jest to realizowane przez jedną z dwóch metod. Po pierwsze, jeśli masz dokumentację od twórcy usługi, należy określić typ poświadczeń klienta (jeśli istnieje) usługa wymaga. Po drugie, jeśli masz tylko plik konfiguracji wygenerowany przez narzędzie Svcutil.exe, można sprawdzić poszczególne powiązania, aby określić, jaki typ poświadczeń jest wymagany.  
  
2. Określ rzeczywiste poświadczenia klienta. Rzeczywiste poświadczenia klienta jest nazywany *wartość poświadczeń klienta,* aby odróżnić go od typu. Na przykład jeśli typ poświadczeń klienta określa certyfikat, należy dostarczyć certyfikat X.509 wystawiony przez urząd certyfikacji, któremu ufa usługa.  
  
### <a name="determining-the-client-credential-type"></a>Określanie typu poświadczeń klienta  
 Jeśli masz plik konfiguracji wygenerowane narzędzie Svcutil.exe, sprawdź [ \<powiązania>](../configure-apps/file-schema/wcf/bindings.md) sekcji, aby określić, jaki typ poświadczeń klienta jest wymagany. W sekcji są elementy wiązania, które określają wymagania dotyczące zabezpieczeń. W szczególności należy \<zbadać zabezpieczeń> element każdego powiązania. Ten element `mode` zawiera atrybut, który można ustawić na jedną`Message` `Transport`z `TransportWithMessageCredential`trzech możliwych wartości ( , , , lub ). Wartość atrybutu określa tryb, a tryb określa, który z elementów podrzędnych jest istotny.  
  
 Element `<security>` może zawierać `<transport>` lub `<message>` element lub obu. Istotnym elementem jest ten, który pasuje do trybu zabezpieczeń. Na przykład poniższy kod określa, że `"Message"`tryb zabezpieczeń jest , `<message>` a `"Certificate"`typ poświadczeń klienta dla elementu jest . W takim przypadku `<transport>` element może być ignorowany. Jednak `<message>` element określa, że certyfikat X.509 musi być dostarczony.  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 Należy zauważyć, `clientCredentialType` że jeśli `"Windows"`atrybut jest ustawiony na , jak pokazano w poniższym przykładzie, nie trzeba podawać rzeczywistą wartość poświadczeń. Dzieje się tak, ponieważ zintegrowane zabezpieczenia systemu Windows zapewniają rzeczywiste poświadczenia (token Protokołu Kerberos) osoby, która jest uruchomiona klientem.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Ustawianie wartości poświadczeń klienta  
 Jeśli zostanie ustalone, że klient musi podać poświadczenie, użyj odpowiedniej metody, aby skonfigurować klienta. Na przykład, aby ustawić certyfikat <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> klienta, użyj metody.  
  
 Powszechną formą poświadczeń jest certyfikat X.509. Poświadczenia można podać na dwa sposoby:  
  
- Programowanie go w kodzie `SetCertificate` klienta (przy użyciu metody).  
  
 Dodając [ \<zachowanie>](../configure-apps/file-schema/wcf/behaviors.md) sekcji pliku konfiguracyjnego dla klienta i `clientCredentials` używając elementu (pokazanego poniżej).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Ustawianie \<klientaCredentials> wartość w kodzie  
 Aby ustawić [ \<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) wartość w kodzie, należy uzyskać <xref:System.ServiceModel.ClientBase%601> dostęp do <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwości klasy. Właściwość zwraca <xref:System.ServiceModel.Description.ClientCredentials> obiekt, który umożliwia dostęp do różnych typów poświadczeń, jak pokazano w poniższej tabeli.  
  
|Właściwość ClientCredential|Opis|Uwagi|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Zwraca<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Reprezentuje certyfikat X.509 dostarczony przez klienta w celu uwierzytelnienia się w usłudze.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Zwraca<xref:System.ServiceModel.Security.HttpDigestClientCredential>|Reprezentuje poświadczenie skrótu HTTP. Poświadczenie jest skrótem nazwy użytkownika i hasła.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Zwraca<xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Reprezentuje niestandardowy token zabezpieczający wystawiony przez usługę tokenu zabezpieczającego, powszechnie używany w scenariuszach federacji.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Zwraca a<xref:System.ServiceModel.Security.PeerCredential>|Reprezentuje poświadczenia równorzędne do udziału w siatce równorzędnej w domenie systemu Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Zwraca<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Reprezentuje certyfikat X.509 dostarczony przez usługę w negocjacjach pozapasmowych.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Zwraca a<xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Reprezentuje parę nazwy użytkownika i hasła.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Zwraca a<xref:System.ServiceModel.Security.WindowsClientCredential>|Reprezentuje poświadczenia klienta systemu Windows (poświadczenie protokołu Kerberos). Właściwości klasy są tylko do odczytu.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Ustawianie \<wartości> klienta w konfiguracji  
 Wartości poświadczeń są określane przy użyciu zachowania punktu końcowego jako elementy [ \<podrzędne clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element. Używany element zależy od typu poświadczeń klienta. Na przykład w poniższym przykładzie przedstawiono konfigurację ustawiania certyfikatu X.509 przy użyciu <[ \<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 Aby ustawić poświadczenia klienta w konfiguracji, dodaj [ \<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) element do pliku konfiguracji. Ponadto dodany element zachowania musi być połączony z punktem `behaviorConfiguration` końcowym usługi przy użyciu atrybutu [ \<> punktu końcowego \<elementu>klienta,](../configure-apps/file-schema/wcf/endpoint-of-client.md) jak pokazano w poniższym przykładzie. Wartość atrybutu `behaviorConfiguration` musi być zgodna z `name` wartością atrybutu zachowania.  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> Niektóre wartości poświadczeń klienta nie można ustawić przy użyciu plików konfiguracyjnych aplikacji, na przykład nazwy użytkownika i hasła lub wartości użytkownika i hasła systemu Windows. Takie wartości poświadczeń można określić tylko w kodzie.  
  
 Aby uzyskać więcej informacji na temat ustawiania poświadczeń klienta, zobacz [Jak: Określanie wartości poświadczeń klienta](how-to-specify-client-credential-values.md).  
  
> [!NOTE]
> `ClientCredentialType`jest ignorowana, `SecurityMode` gdy `"TransportWithMessageCredential",` jest ustawiona na jak pokazano w poniższej konfiguracji przykładowej.  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<wiązania>](../configure-apps/file-schema/wcf/bindings.md)
- [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [Zabezpieczanie usług](securing-services.md)
- [Uzyskiwanie dostępu do usług za pomocą klienta WCF](accessing-services-using-a-wcf-client.md)
- [Instrukcje: określanie wartości poświadczeń klienta](how-to-specify-client-credential-values.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: określanie typu poświadczeń klienta](how-to-specify-the-client-credential-type.md)
