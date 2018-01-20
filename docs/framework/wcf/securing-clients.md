---
title: "Zabezpieczanie klientów [WCF]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 611272f9d0369a89d401315e9b6379d2e8cd27c0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="securing-clients"></a>Zabezpieczanie klientów [WCF]
W [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], usługa nakazują wymagania dotyczące zabezpieczeń dla klientów. To, że usługa określa, jakie tryb zabezpieczeń, aby używać, i określa, czy klient musi dostarczyć poświadczenia. Zabezpieczanie klientów, w związku z tym, proces jest prosty: używanie metadanych uzyskane z usługi (jeśli jest publikowany) i kompilacji klienta. Metadane określa sposób konfigurowania klienta. Jeśli usługa wymaga to, że klient podać poświadczenia, należy uzyskać poświadczenia, która pasuje do wymagań. W tym temacie opisano proces bardziej szczegółowo. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Tworzenie bezpiecznej usługi, zobacz [zabezpieczania usług](../../../docs/framework/wcf/securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Usługa określa zabezpieczeń  
 Domyślnie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] powiązania ma włączone funkcje zabezpieczeń. (Wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding>.) W związku z tym jeśli usługa została utworzona przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], istnieje duże prawdopodobieństwo, że będzie implementowany zabezpieczeń, aby zapewnić uwierzytelnianie, poufność i integralność. W takim przypadku metadanych, który udostępnia usługi wskaże, co wymaga, aby ustanowić kanał bezpiecznej komunikacji. Jeśli metadane usługi nie ma żadnych wymagań dotyczących zabezpieczeń, nie istnieje sposób nałożyć schemat zabezpieczeń, takich jak Secure Sockets Layer (SSL) za pośrednictwem protokołu HTTP, w usłudze. Jeśli jednak usługa wymaga klienta podać poświadczenia, następnie deweloperowi klienta, narzędzia wdrażania lub administrator musisz podać poświadczenia rzeczywiste używanego przez klienta do samodzielnego uwierzytelnienia usługi.  
  
## <a name="obtaining-metadata"></a>Uzyskiwanie metadanych  
 Podczas tworzenia klienta, pierwszym krokiem jest uzyskać metadanych dla usługi klienta będą komunikować się z. Można to zrobić na dwa sposoby. Po pierwsze, jeśli usługa publikuje punktu końcowego metadanych programu exchange (MEX) lub udostępnia metadanych za pośrednictwem protokołu HTTP lub HTTPS, można pobrać przy użyciu metadanych [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), zarówno generująca pliki kodu dla klienta, a także plik konfiguracji. ([!INCLUDE[crabout](../../../includes/crabout-md.md)] za pomocą narzędzia, zobacz [dostęp do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) Jeśli usługa nie jest publikowany punktu końcowego MEX i również nie powoduje jego metadanych dostępne za pośrednictwem protokołu HTTP lub HTTPS, należy skontaktuj się z autorem usługi dokumentacji, które opisują wymagania dotyczące zabezpieczeń i metadanych.  
  
> [!IMPORTANT]
>  Zaleca się, że metadane pochodzą z zaufanego źródła i że nie być zmodyfikowany. Metadane pobrany przy użyciu protokołu HTTP są wysyłane w postaci zwykłego tekstu i może zostać naruszone. Jeśli usługa używa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> i <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> właściwości, użyj adresu URL, twórca usługi dostarczone w celu pobierania danych przy użyciu protokołu HTTPS.  
  
## <a name="validating-security"></a>Sprawdzanie poprawności zabezpieczeń  
 Źródła metadanych można podzielić na dwie szerokie kategorie: zaufania źródeł i źródeł niezaufanych. Jeśli ufasz źródła i zostały pobrane kod klienta i innych metadanych z tego źródła bezpiecznego punktu końcowego MEX, a następnie można skompilować klienta, dostarczyć prawidłowych poświadczeń, a następnie uruchom go z nie innych problemów.  
  
 Jednak w przypadku wybrania pobranie z niezaufanego źródła niewiele więcej wiadomo na temat klienta i metadanych, należy koniecznie weryfikacji środków bezpieczeństwa, który korzysta z kodu. Na przykład użytkownik musi nie wystarczy utworzyć klienta, który wysyła do usługi informacji osobistych lub finansowych, jeśli usługa wymaga poufności i integralności (co najmniej). Właściciel usługi należy ufać w zakresie, w jakim zgadzasz się ujawnić takie informacje, ponieważ takie informacje będą widoczne dla niego.  
  
 Zgodnie z zasadą w związku z tym korzystając kodu i metadanych z niezaufanego źródła, zaznacz kod i metadanych, aby upewnić się, że spełnia on poziom zabezpieczeń, która jest wymagana.  
  
## <a name="setting-a-client-credential"></a>Ustawienie poświadczeń klienta  
 Ustawienie poświadczeń klienta na komputerze klienckim składa się z dwóch kroków:  
  
1.  Określić *typu poświadczeń klienta* wymaga usługi. Jest to osiągane przez jedną z dwóch metod. Po pierwsze, jeśli masz dokumentacji z twórca usługi, powinien on zawierać poświadczeń klienta wymaga usługi typu (jeśli istnieje). Po drugie Jeśli masz tylko plik konfiguracji generowany przez narzędzie Svcutil.exe należy zbadać poszczególnych powiązań, aby określić, jaki typ poświadczeń jest wymagany.  
  
2.  Określ poświadczenie klienta faktycznie. Poświadczenie klienta faktycznie jest nazywany *wartości poświadczeń klienta* odróżniający go od typu. Na przykład, jeśli typ poświadczeń klienta Określa certyfikat, należy podać certyfikat X.509, wystawiony przez urząd certyfikacji usługi relacji zaufania.  
  
### <a name="determining-the-client-credential-type"></a>Określanie typu poświadczeń klienta  
 Jeśli masz konfiguracji z narzędzia Svcutil.exe w wygenerowanych plików, sprawdź [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) sekcji, aby ustalić, jakiego typu poświadczeń klienta jest wymagana. W sekcji znajdują się elementy powiązania, które określają wymagania dotyczące zabezpieczeń. W szczególności zbadać \<zabezpieczeń > Element każdego powiązania. Ten element zawiera `mode` atrybut, który można ustawić na jeden z trzech wartości (`Message`, `Transport`, lub `TransportWithMessageCredential`). Wartość atrybutu określa tryb, a tryb Określa, które elementów podrzędnych jest znacząca.  
  
 `<security>` Element może zawierać albo `<transport>` lub `<message>` element lub oba. Istotny element jest zgodną z trybu zabezpieczeń. Na przykład następujący kod określa, że tryb zabezpieczeń jest `"Message"`i typu poświadczeń klienta `<message>` jest element `"Certificate"`. W takim przypadku `<transport>` elementu można zignorować. Jednak `<message>` element określa, że należy podać certyfikat X.509.  
  
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
  
 Należy pamiętać, że jeśli `clientCredentialType` atrybut ma ustawioną `"Windows"`, jak pokazano w poniższym przykładzie, nie należy podać wartość rzeczywista poświadczenia. Jest to spowodowane zintegrowane zabezpieczenia systemu Windows zawiera rzeczywiste poświadczeń (token protokołu Kerberos) osoby, która jest uruchomiony klient.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Ustawienie wartości poświadczeń klienta  
 Jeśli okaże się, że klient musi podać poświadczenia, użyj odpowiedniej metody, aby skonfigurować klienta. Na przykład aby określić certyfikat klienta, należy użyć <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody.  
  
 Typowe formę poświadczeń jest certyfikat X.509. Możesz podać poświadczenia na dwa sposoby:  
  
-   Przez programowania go w kodzie klienta (za pomocą `SetCertificate` metody).  
  
 Dodając [ \<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) sekcji pliku konfiguracji klienta i za pomocą `clientCredentials` elementu (pokazana poniżej).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Ustawienie \<clientCredentials > wartość w kodzie  
 Aby ustawić [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) wartości w kodzie, muszą uzyskać dostęp do <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy. Zwraca właściwości <xref:System.ServiceModel.Description.ClientCredentials> obiekt, który zezwala na dostęp do różnych typów poświadczeń, jak pokazano w poniższej tabeli.  
  
|Właściwość poświadczeń klienta|Opis|Uwagi|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Zwraca<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Reprezentuje certyfikat X.509 dostarczonych przez klienta do samodzielnego uwierzytelnienia usługi.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Zwraca<xref:System.ServiceModel.Security.HttpDigestClientCredential>|Reprezentuje poświadczenie HTTP digest. Poświadczenie jest skrót nazwy użytkownika i hasła.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Zwraca<xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Reprezentuje token zabezpieczający niestandardowych wystawiony przez usługę tokenu zabezpieczającego, często używane w scenariuszach federacji.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Zwraca<xref:System.ServiceModel.Security.PeerCredential>|Reprezentuje poświadczenia elementu równorzędnego dla udziału w siatki elementów równorzędnych w domenie systemu Windows.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Zwraca<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Reprezentuje certyfikat X.509 dostarczonych przez usługę w negocjacji poza pasmem.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Zwraca<xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Reprezentuje parę nazwa i hasło użytkownika.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Zwraca<xref:System.ServiceModel.Security.WindowsClientCredential>|Reprezentuje poświadczeń klienta systemu Windows (poświadczeń protokołu Kerberos). Właściwości klasy są tylko do odczytu.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Ustawienie \<clientCredentials > wartości w konfiguracji  
 Poświadczenie wartości są określane przy użyciu zachowanie punktu końcowego jako elementy podrzędne [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu. Element używany zależy od typu poświadczeń klienta. Na przykład w poniższym przykładzie przedstawiono konfigurację, aby ustawić certyfikatu X.509 przy użyciu <[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
  
 Aby ustawić poświadczenia klienta w konfiguracji, należy dodać [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) elementu do pliku konfiguracji. Ponadto musi być połączony element dodany zachowania punktu końcowego usługi za pomocą `behaviorConfiguration` atrybutu [ \<punktu końcowego >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element, jak pokazano w poniższym przykładzie. Wartość `behaviorConfiguration` atrybutu musi być zgodna z wartością zachowanie `name` atrybutu.  
  
 `<configuration>`  
  
 `<system.serviceModel>`  
  
 `<client>`  
  
 `<endpoint address="http://localhost/servicemodelsamples/service.svc"`  
  
 `binding="wsHttpBinding"`  
  
 `bindingConfiguration="Binding1"`  
  
 `behaviorConfiguration="myEndpointBehavior"`  
  
 `contract="Microsoft.ServiceModel.Samples.ICalculator" />`  
  
 `</client>`  
  
 `</system.serviceModel>`  
  
 `</configuration>`  
  
> [!NOTE]
>  Niektóre wartości poświadczeń klienta nie może być zestawu przy użyciu pliki konfiguracji aplikacji, na przykład, nazwę użytkownika i hasło, lub użytkownika systemu Windows i wartości hasła. Wartości te poświadczenia można określić tylko w kodzie.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Ustawienie poświadczeń klienta, zobacz [porady: Określanie wartości poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
> [!NOTE]
>  `ClientCredentialType`jest ignorowana, jeśli `SecurityMode` ustawiono `"TransportWithMessageCredential",` jak pokazano w poniższych Przykładowa konfiguracja.  
  
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
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [\<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
 [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [Instrukcje: określanie wartości poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Instrukcje: określanie typu poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
