---
title: Zabezpieczanie klientów [WCF]
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: 1200875baf39c5fdff613cfd21d4027cd5d8df1b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606051"
---
# <a name="securing-clients"></a>Zabezpieczanie klientów [WCF]
W Windows Communication Foundation (WCF), usługa decyduje o wymagania dotyczące zabezpieczeń dla klientów. Oznacza to, że usługa określa jakie tryb zabezpieczeń do użycia i określa, czy klient musi podać poświadczenia. Zabezpieczanie klienta, w związku z tym, proces jest prosty: metadane uzyskane z usługi (jeśli jest publikowany) oraz tworzyć klienta. Metadane określa sposób konfigurowania klienta. Jeśli usługa wymaga, że klient podać poświadczenia, należy uzyskać poświadczenia, która pasuje do wymagań. W tym temacie omówiono proces bardziej szczegółowo. Aby uzyskać więcej informacji na temat tworzenia usługi bezpiecznego zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Usługa określa zabezpieczeń  
 Domyślnie powiązaniami WCF zabezpieczeń funkcje są włączone. (Wyjątek stanowi <xref:System.ServiceModel.BasicHttpBinding>.) W związku z tym jeśli usługa została utworzona przy użyciu usługi WCF, istnieje duże prawdopodobieństwo, że wdroży zabezpieczeń, aby zapewnić uwierzytelnianie, poufności i integralności. W takim przypadku metadanych, które zapewnia usługa poinformuje, co wymaga nawiązać bezpieczny kanał komunikacyjny. Jeśli metadane usługi nie ma żadnych wymagań dotyczących zabezpieczeń, nie ma możliwości celu nałożenia zabezpieczeń systemu, takich jak Secure Sockets Layer (SSL) przy użyciu protokołu HTTP, w usłudze. Jeśli jednak usługa wymaga klienta podać poświadczenia, następnie dewelopera klienta, wdrażania lub administrator musisz podać rzeczywiste poświadczenia, który będzie używany przez klienta do samodzielnego uwierzytelnienia usługi.  
  
## <a name="obtaining-metadata"></a>Uzyskiwanie metadanych  
 Podczas tworzenia klienta, pierwszym krokiem jest można uzyskać metadanych dla usługi, który klient komunikuje się z. Można to zrobić na dwa sposoby. Po pierwsze, jeśli usługa publikuje punkt końcowy metadanych programu exchange (MEX) lub sprawia, że jego metadane dostępne za pośrednictwem protokołu HTTP lub HTTPS, możesz pobrać przy użyciu metadanych [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), które zarówno generuje pliki kodu dla klienta, jak również w pliku konfiguracji. (Aby uzyskać więcej informacji na temat korzystania z narzędzia, zobacz [uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) Jeśli usługa nie publikuje do punktu końcowego MEX i również nie powoduje jego metadane dostępne za pośrednictwem protokołu HTTP lub HTTPS, możesz skontaktować się twórcą usługi dla dokumentacji, która opisuje wymagania dotyczące zabezpieczeń i metadanych.  
  
> [!IMPORTANT]
>  Zalecane jest, że metadane pochodzą z zaufanego źródła i że nie zostać zmodyfikowany. Metadane pobrany przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i może zostać zmieniony. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> i <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> właściwości, użyj adresu URL, twórcy usługi dostarczane do pobierania danych przy użyciu protokołu HTTPS.  
  
## <a name="validating-security"></a>Sprawdzanie zabezpieczeń  
 Metadane źródła można podzielić na dwie szerokie kategorie: zaufanie do źródła i źródeł niezaufanych. Jeśli ufasz źródła i zostały pobrane kod klienta i inne metadane z tego źródła bezpiecznego punktu końcowego MEX, a następnie można skompilować klienta, dostarczyć prawidłowe poświadczenia, a jego uruchomienie z nie innych problemów.  
  
 Jednak gdy użytkownik wybierze opcję Pobierz klienta i metadane ze źródła, który znasz trochę o upewnij się sprawdzić poprawność środki bezpieczeństwa, używanych przez kod. Na przykład należy po prostu tworzysz klienta, który wysyła informacji osobistych lub finansowych do usługi, chyba że usługa wymaga poufności i integralności (co najmniej). Właściciel usługi powinien ufać w zakresie, w jakim chcesz ujawniać informacje takie, ponieważ takie informacje będą widoczne dla niego.  
  
 Zgodnie z zasadą w związku z tym, korzystając z kodu i metadanych z niezaufanego źródła, sprawdź kod i metadanych, aby upewnić się, że spełnia on poziom zabezpieczeń, która jest wymagana.  
  
## <a name="setting-a-client-credential"></a>Ustawianie poświadczeń klienta  
 Ustawianie poświadczeń klienta na komputerze klienckim składa się z dwóch kroków:  
  
1. Określić *typu poświadczeń klienta* usługa wymaga. Jest to realizowane za pomocą jednej z dwóch metod. Po pierwsze, w przypadku dokumentacji z twórcą usługi go określić poświadczeń klienta wymaga usługi typu (jeśli istnieje). Po drugie Jeśli masz tylko plik konfiguracji, które są generowane przez narzędzia Svcutil.exe, można sprawdzić poszczególnych powiązań, aby ustalić, jaki typ poświadczeń jest wymagany.  
  
2. Określ poświadczenie rzeczywistym klientem. Poświadczenia klienta faktycznie jest nazywany *wartości poświadczeń klienta* odróżniający go od typu. Na przykład, jeśli typ poświadczeń klienta Określa certyfikat, musisz podać certyfikat X.509 wystawiony przez urząd certyfikacji usługi relacji zaufania.  
  
### <a name="determining-the-client-credential-type"></a>Określanie typu poświadczeń klienta  
 W przypadku konfiguracji narzędzia Svcutil.exe wygenerowanych plików, sprawdź [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji, aby określić, jakiego typu poświadczeń klienta jest wymagany. W ramach tej sekcji są elementy wiązania, które określają wymagania w zakresie zabezpieczeń. W szczególności sprawdź \<zabezpieczeń > Element każdego powiązania. Ten element zawiera `mode` atrybut, który można ustawić jedną z trzech wartości (`Message`, `Transport`, lub `TransportWithMessageCredential`). Wartość atrybutu określa tryb, a tryb Określa, które z elementów podrzędnych ma znaczenie.  
  
 `<security>` Element może zawierać albo `<transport>` lub `<message>` elementu lub obu. Istotny element jest odpowiedni tryb zabezpieczeń. Na przykład, poniższy kod określa, czy tryb zabezpieczeń jest `"Message"`i klienta, typ dla poświadczeń `<message>` element jest `"Certificate"`. W tym przypadku `<transport>` elementu można zignorować. Jednak `<message>` element określa, czy należy podać certyfikat X.509.  

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

 Należy pamiętać, że jeśli `clientCredentialType` ma ustawioną wartość atrybutu `"Windows"`, jak pokazano w poniższym przykładzie, nie trzeba podawać wartości rzeczywiste poświadczenia. Jest to spowodowane zintegrowanych zabezpieczeń Windows zawiera rzeczywiste poświadczenia (tokenu protokołu Kerberos) osobie, która jest uruchomiony klient.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Ustawienie wartości poświadczeń klienta  
 Jeśli okaże się, że klient musi podać poświadczenia, użyj odpowiedniej metody w celu skonfigurowania klienta. Na przykład, aby ustawić certyfikat klienta, użyj <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.  
  
 Używany typ poświadczeń jest certyfikatu X.509. Możesz podać poświadczenia na dwa sposoby:  
  
- Programując w kodzie klienta (przy użyciu `SetCertificate` metody).  
  
 Dodając [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) sekcję pliku konfiguracji dla klienta i za pomocą `clientCredentials` — element (pokazana poniżej).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Ustawienie \<clientCredentials > wartość w kodzie  
 Aby ustawić [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) wartości w kodzie, należy przejść do <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy. Zwraca właściwość <xref:System.ServiceModel.Description.ClientCredentials> obiekt, który zezwala na dostęp do różnych typów poświadczeń, jak pokazano w poniższej tabeli.  
  
|Właściwość ClientCredential|Opis|Uwagi|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Zwraca <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Reprezentuje certyfikat X.509 dostarczonych przez klienta do samodzielnego uwierzytelnienia usługi.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Zwraca <xref:System.ServiceModel.Security.HttpDigestClientCredential>|Reprezentuje poświadczeń usługi HTTP digest. Poświadczenie jest skrót nazwy użytkownika i hasła.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Zwraca <xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Reprezentuje token zabezpieczeń niestandardowych, wystawiony przez usługę tokenu zabezpieczającego, często używane w scenariuszach federacji.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Zwraca <xref:System.ServiceModel.Security.PeerCredential>|Reprezentuje poświadczenia elementu równorzędnego dla udziału w siatki elementów równorzędnych w domenie Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Zwraca <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Reprezentuje certyfikat X.509, udostępniane przez usługę w negocjacji poza pasmem.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Zwraca <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Reprezentuje parę nazwa i hasło użytkownika.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Zwraca <xref:System.ServiceModel.Security.WindowsClientCredential>|Reprezentuje poświadczeń klienta Windows (poświadczenia protokołu Kerberos). Właściwości klasy są tylko do odczytu.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Ustawienie \<clientCredentials > z wartości w konfiguracji  
 Określone wartości poświadczeń za pomocą zachowanie punktu końcowego jako elementy podrzędne [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu. Element używany jest zależna od typu poświadczeń klienta. Na przykład w poniższym przykładzie pokazano konfigurację, aby ustawić certyfikat X.509 przy użyciu <[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Aby ustawić konfigurację poświadczeń klienta, należy dodać [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element do pliku konfiguracji. Ponadto element dodano zachowania muszą zostać połączone do punktu końcowego usługi za pomocą `behaviorConfiguration` atrybutu [ \<punktu końcowego > z \<klienta >](../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu, jak pokazano w poniższym przykładzie. Wartość `behaviorConfiguration` atrybutu musi odpowiadać wartości zachowania `name` atrybutu.  

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
>  Niektóre wartości poświadczeń klienta nie może być zestaw za pomocą plików konfiguracji aplikacji, na przykład, nazwę użytkownika i hasła, lub Windows użytkownika i wartości haseł. Wartości tych poświadczeń można określić tylko w przypadku kodu.  
  
 Aby uzyskać więcej informacji na temat ustawiania poświadczeń klienta, zobacz [jak: Określanie wartości poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
> [!NOTE]
>  `ClientCredentialType` jest ignorowany, kiedy `SecurityMode` ustawiono `"TransportWithMessageCredential",` jak pokazano w poniższym Przykładowa konfiguracja.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)
- [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)
- [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [Instrukcje: Określanie wartości poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: Określanie typu poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
