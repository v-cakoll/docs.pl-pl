---
title: Zabezpieczanie klientów [WCF]
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: 7f9a02bc650f54338dfcb1d3f41397e745483430
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959536"
---
# <a name="securing-clients"></a>Zabezpieczanie klientów [WCF]
W programie Windows Communication Foundation (WCF) usługa wymusza wymagania dotyczące zabezpieczeń dla klientów. Oznacza to, że usługa określa tryb zabezpieczeń, który ma być używany, oraz czy klient musi podać poświadczenie. W związku z tym proces zabezpieczania klienta jest prosty: Użyj metadanych uzyskanych z usługi (jeśli jest publikowany) i skompiluj klienta. Metadane określają sposób konfigurowania klienta programu. Jeśli usługa wymaga podania poświadczeń przez klienta, należy uzyskać poświadczenia spełniające wymagania. W tym temacie omówiono proces bardziej szczegółowo. Aby uzyskać więcej informacji na temat tworzenia bezpiecznej usługi, zobacz [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Usługa określa zabezpieczenia  
 Domyślnie powiązania WCF mają włączone funkcje zabezpieczeń. (Wyjątek to <xref:System.ServiceModel.BasicHttpBinding>.) W związku z tym, jeśli usługa została utworzona przy użyciu programu WCF, istnieje możliwość, że Zaimplementuj zabezpieczenia, aby zapewnić uwierzytelnianie, poufność i integralność. W takim przypadku metadane udostępniane przez usługę będą wskazywać, czego potrzebuje do ustanowienia bezpiecznego kanału komunikacyjnego. Jeśli metadane usługi nie obejmują żadnych wymagań dotyczących zabezpieczeń, nie ma możliwości narzucenia schematu zabezpieczeń, takiego jak SSL (SSL) przez protokół HTTP, w usłudze. Jeśli jednak usługa wymaga od klienta podania poświadczeń, deweloper klienta, program wdrażania lub administrator musi podać rzeczywiste poświadczenia, które będą używane przez klienta do samodzielnego uwierzytelnienia w usłudze.  
  
## <a name="obtaining-metadata"></a>Uzyskiwanie metadanych  
 Podczas tworzenia klienta pierwszy krok polega na uzyskaniu metadanych dla usługi, z którą komunikuje się klient. Można to zrobić na dwa sposoby. Po pierwsze, jeśli usługa publikuje punkt końcowy wymiany metadanych (MEX) lub udostępni metadane za pośrednictwem protokołu HTTP lub HTTPS, można pobrać metadane za pomocą narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), które generuje pliki kodu dla klienta. również plik konfiguracji. (Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)). Jeśli usługa nie publikuje punktu końcowego MEX i nie udostępnia swoich metadanych za pośrednictwem protokołu HTTP lub HTTPS, należy skontaktować się z twórcą usługi w celu uzyskania dokumentacji opisującej wymagania dotyczące zabezpieczeń i metadanych.  
  
> [!IMPORTANT]
> Zaleca się, aby metadane pochodzą z zaufanego źródła i nie zostały naruszone. Metadane pobrane przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i mogą być modyfikowane przez program. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> właściwości i <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> , użyj adresu URL dostarczonego przez twórcę usługi, aby pobrać dane przy użyciu protokołu HTTPS.  
  
## <a name="validating-security"></a>Sprawdzanie poprawności zabezpieczeń  
 Źródła metadanych można podzielić na dwie szerokie Kategorie: źródła zaufania i źródła niezaufane. Jeśli ufasz źródłu i pobrano kod klienta oraz inne metadane z bezpiecznego elementu końcowego MEX tego źródła, można skompilować klienta, dostarczyć go z prawidłowymi poświadczeniami i uruchomić go bez żadnych innych problemów.  
  
 Jeśli jednak zdecydujesz się pobrać klienta i metadane z nieznanego źródła, pamiętaj o sprawdzeniu, czy miary zabezpieczeń są używane w kodzie. Na przykład nie można po prostu utworzyć klienta wysyłającego informacje osobiste lub finansowe do usługi, chyba że usługa wymaga poufności i integralności (co najmniej). Należy zaufać właścicielowi usługi w zakresie, w jakim użytkownik chce ujawnić takie informacje, ponieważ takie informacje będą widoczne dla niego.  
  
 W związku z tym w przypadku używania kodu i metadanych z niezaufanego źródła Sprawdź kod i metadane, aby upewnić się, że spełnia on wymagany poziom zabezpieczeń.  
  
## <a name="setting-a-client-credential"></a>Ustawianie poświadczeń klienta  
 Ustawienie poświadczeń klienta na kliencie składa się z dwóch kroków:  
  
1. Określ *Typ poświadczeń klienta* wymagany przez usługę. Jest to realizowane przez jedną z dwóch metod. Najpierw w przypadku posiadania dokumentacji od twórcy usługi należy określić typ poświadczeń klienta (jeśli istnieje) wymagana przez usługę. Po drugie, jeśli masz tylko plik konfiguracyjny wygenerowany przez narzędzie Svcutil. exe, możesz sprawdzić poszczególne powiązania, aby określić, jaki typ poświadczeń jest wymagany.  
  
2. Określ rzeczywiste poświadczenie klienta. Rzeczywiste poświadczenie klienta nazywa się *wartością poświadczenia klienta* , aby odróżnić ją od typu. Na przykład, jeśli typ poświadczeń klienta określa certyfikat, należy podać certyfikat X. 509 wystawiony przez urząd certyfikacji, którym ufają usługi.  
  
### <a name="determining-the-client-credential-type"></a>Określanie typu poświadczeń klienta  
 Jeśli masz plik konfiguracyjny narzędzia Svcutil. exe, zapoznaj się z sekcją [ \<powiązań >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) , aby określić, jaki typ poświadczeń klienta jest wymagany. W sekcji znajdują się elementy wiążące, które określają wymagania dotyczące zabezpieczeń. W celu przeanalizowania \<elementu > zabezpieczeń każdego powiązania. Ten element zawiera `mode` atrybut, który można ustawić na jedną z trzech możliwych wartości (`Message`, `Transport`lub `TransportWithMessageCredential`). Wartość atrybutu określa tryb, a tryb określa, który z elementów podrzędnych jest znaczący.  
  
 Element może zawierać `<transport>` element lub `<message>` albo oba te elementy. `<security>` Istotny element to ten, który jest zgodny z trybem zabezpieczeń. Na przykład poniższy kod określa, że tryb zabezpieczeń to `"Message"`, a typ poświadczeń klienta `<message>` dla elementu to `"Certificate"`. W takim przypadku `<transport>` element może być ignorowany. `<message>` Jednak element określa, że należy podać certyfikat X. 509.  

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

 Należy pamiętać, że `clientCredentialType` Jeśli atrybut jest ustawiony `"Windows"`na, jak pokazano w poniższym przykładzie, nie trzeba podawać rzeczywistej wartości poświadczeń. Wynika to z faktu, że zintegrowane zabezpieczenia systemu Windows zapewniają rzeczywiste poświadczenie (token Kerberos) osoby, która korzysta z klienta programu.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Ustawianie wartości poświadczeń klienta  
 Jeśli okaże się, że klient musi podać poświadczenia, użyj odpowiedniej metody w celu skonfigurowania klienta. Na przykład aby ustawić certyfikat klienta, należy użyć <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.  
  
 Typową poświadczeniem jest certyfikat X. 509. Poświadczenie można podać na dwa sposoby:  
  
- Poprzez programowanie w kodzie klienta (za pomocą `SetCertificate` metody).  
  
 `clientCredentials` [ Dodanie\<zachowań >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) sekcji pliku konfiguracji klienta i użycie elementu (pokazanego poniżej).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Ustawianie wartości \<elementu ClientCredentials > w kodzie  
 Aby ustawić obiekt [ \<ClientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) wartość w kodzie, należy uzyskać dostęp <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> do właściwości <xref:System.ServiceModel.ClientBase%601> klasy. Właściwość zwraca <xref:System.ServiceModel.Description.ClientCredentials> obiekt, który umożliwia dostęp do różnych typów poświadczeń, jak pokazano w poniższej tabeli.  
  
|Właściwość ClientCredential|Opis|Uwagi|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Zwraca wartość<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Reprezentuje certyfikat X. 509 dostarczony przez klienta w celu samodzielnego uwierzytelnienia w usłudze.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Zwraca wartość<xref:System.ServiceModel.Security.HttpDigestClientCredential>|Reprezentuje poświadczenie protokołu HTTP digest. Poświadczenie jest skrótem nazwy użytkownika i hasła.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Zwraca wartość<xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Reprezentuje niestandardowy token zabezpieczający wystawiony przez usługę tokenu zabezpieczającego, powszechnie używany w scenariuszach federacyjnych.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Zwraca wartość<xref:System.ServiceModel.Security.PeerCredential>|Reprezentuje poświadczenie elementu równorzędnego dla udziału w sieci równorzędnej w domenie systemu Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Zwraca wartość<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Reprezentuje certyfikat X. 509 dostarczony przez usługę w ramach negocjacji poza pasmem.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Zwraca wartość<xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Reprezentuje parę nazwa użytkownika i hasło.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Zwraca wartość<xref:System.ServiceModel.Security.WindowsClientCredential>|Reprezentuje poświadczenie klienta systemu Windows (poświadczenie protokołu Kerberos). Właściwości klasy są tylko do odczytu.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Ustawianie wartości \<elementu ClientCredentials > w konfiguracji  
 Wartości poświadczeń są określane przy użyciu zachowania punktu końcowego jako elementów [ \<](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) podrzędnych elementu ClientCredentials >. Używany element zależy od typu poświadczeń klienta. Na przykład poniższy przykład pokazuje konfigurację służącą do ustawiania certyfikatu X. 509 przy użyciu[\<> < ClientCertificate](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
  
 Aby ustawić poświadczenie klienta w konfiguracji, Dodaj [ \<element endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) do pliku konfiguracji. Ponadto dodanie elementu zachowania musi być powiązane z punktem końcowym usługi przy użyciu `behaviorConfiguration` atrybutu [ \<punktu końcowego > \<elementu klienta >](../configure-apps/file-schema/wcf/endpoint-of-client.md) , jak pokazano w poniższym przykładzie. Wartość `behaviorConfiguration` atrybutu musi być zgodna z wartością atrybutu Behavior `name` .  

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
> Niektórych wartości poświadczeń klienta nie można ustawić przy użyciu plików konfiguracji aplikacji, na przykład nazwy użytkownika i hasła lub wartości użytkownika i hasła systemu Windows. Takie wartości poświadczeń można określić tylko w kodzie.  
  
 Aby uzyskać więcej informacji na temat ustawiania poświadczeń klienta, [zobacz How to: Określ wartości](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)poświadczeń klienta.  
  
> [!NOTE]
> `ClientCredentialType`jest ignorowany `SecurityMode` , gdy jest `"TransportWithMessageCredential",` ustawiona na tak, jak pokazano w poniższej konfiguracji przykładowej.  
  
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
- [\<> powiązań](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)
- [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)
- [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [Instrukcje: Określ wartości poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: Określ typ poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
