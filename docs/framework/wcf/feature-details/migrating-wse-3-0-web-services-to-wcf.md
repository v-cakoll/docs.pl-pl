---
title: "Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c97279b553a615feda1dd3a195ad033744d82983
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF
Zalety Migrowanie usług sieci Web programu WSE 3.0 do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obejmują lepszą wydajność i obsługę dodatkowych modułów transportu, scenariusze dodatkowe zabezpieczenia i WS-* specyfikacji. Usługi sieci Web, która jest migrowana z programu WSE 3.0 do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] może wystąpić do poprawy wydajności 200 – 400%. Aby uzyskać więcej informacji o transportu obsługiwane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Aby uzyskać listę scenariuszy obsługiwanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz [typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Lista specyfikacji, które są obsługiwane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz [przewodnik dotyczący współpracy protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Poniższe sekcje zawierają wskazówki dotyczące sposobu przeprowadzenia migracji określonych funkcji usługi sieci Web programu WSE 3.0 do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="general"></a>Ogólne  
 WSE 3.0 i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji obejmują współdziałanie poziomu podczas transmisji i wspólny zbiór terminologii. WSE 3.0 i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje są podczas transmisji na poziomie współdziałanie oparte na zestawie WS-* specyfikacje obsługujących oba. Gdy WSE 3.0 lub [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zaprojektowano w aplikacji jest wspólny zbiór terminologii, takich jak nazwy potwierdzeń zabezpieczeń gotowe WSE i tryby uwierzytelniania.  
  
 Istnieje wiele aspektów podobne między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i ASP.NET lub WSE 3.0 modele programowania są różne. Aby uzyskać więcej informacji o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu programowania, zobacz [podstawowy cykl życia programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  Aby przeprowadzić migrację usługi sieci Web programu WSE do programu WCF [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie może służyć do generowania klienta. Ten klient zawiera jednak interfejsów i klasy, które mogą być używane jako początkowy punkt usługi WCF za. Interfejsy, które są generowane mają <xref:System.ServiceModel.OperationContractAttribute> atrybut zastosowany do elementów członkowskich umowy z <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> ustawioną właściwość `*`. Gdy klient programu WSE wywołania usługi sieci Web z tego ustawienia, następującego wyjątku: **Web.Services3.ResponseProcessingException: WSE910: Wystąpił błąd podczas przetwarzania komunikatu odpowiedzi i błędu można znaleźć w wewnętrznych wyjątek**. Aby temu zaradzić, ustaw <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> właściwość <xref:System.ServiceModel.OperationContractAttribute> atrybutu niż`null` wartości, takich jak `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Zabezpieczenia  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Usługi sieci Web programu WSE 3.0, które są chronione przy użyciu pliku zasad  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usługi można użyć pliku konfiguracji do zabezpieczania usługi i mechanizmu jest podobny do pliku zasad programu WSE 3.0. W WSE 3.0 zabezpieczania usługi sieci Web przy użyciu pliku zasad Użyj potwierdzenia zabezpieczeń gotowe lub potwierdzenia zasad niestandardowych. Potwierdzenia zabezpieczeń gotowe ściśle mapowania na tryb uwierzytelniania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elementu powiązania zabezpieczeń. Są nie tylko [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tryby uwierzytelniania i zapewnienia bezpieczeństwa gotowe WSE 3.0 taką samą nazwę lub podobnie ich zabezpieczonych wiadomości przy użyciu takich samych typach poświadczeń. Na przykład `usernameForCertificate` mapuje potwierdzenia zabezpieczeń gotowe WSE 3.0 `UsernameForCertificate` tryb uwierzytelniania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. W poniższych przykładach kodu pokazano sposób minimalnego zasad, które korzystają `usernameForCertificate` mapuje potwierdzenia zabezpieczeń gotowe WSE 3.0 `UsernameForCertificate` tryb uwierzytelniania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do niestandardowego powiązania.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **USŁUGI WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Aby przeprowadzić migrację ustawień zabezpieczeń usług sieci Web programu WSE 3.0 określonych w pliku zasad w celu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], należy utworzyć niestandardowego powiązania w pliku konfiguracji i potwierdzenia gotowe zabezpieczeń musi być ustawiona na tryb jego odpowiednik uwierzytelniania. Ponadto niestandardowego powiązania musi być skonfigurowana w taki sposób, do korzystania z sierpnia 2004 specyfikacji WS-Addressing, gdy klienci programu WSE 3.0 komunikują się z usługą. Gdy migrowanych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi nie wymaga komunikacji z klientami programu WSE 3.0 i muszą zachować tylko parzystości zabezpieczeń, należy rozważyć użycie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązań zdefiniowanych przez system, przy użyciu ustawień zabezpieczeń odpowiednich zamiast tworzenia niestandardowego wiązanie.  
  
 W poniższej tabeli wymieniono mapowanie między pliku zasad programu WSE 3.0 i jego odpowiednik niestandardowe powiązanie w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|WSE 3.0 zabezpieczeń gotowe potwierdzenia|Konfiguracji usługi WCF wiązania niestandardowego|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Aby uzyskać więcej informacji o tworzeniu powiązań niestandardowych w programie WCF, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Usługi sieci Web programu WSE 3.0, które są chronione przy użyciu kodu aplikacji  
 Czy WSE 3.0 lub [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest używana, wymagania dotyczące zabezpieczeń można określić w kodzie aplikacji, a nie w konfiguracji. W WSE 3.0, jest to osiągane przez utworzenie klasy, która pochodzi z `Policy` klasy, a następnie przez dodanie wymagania przez wywołanie metody `Add` metody. Aby uzyskać więcej informacji na temat określania wymagań bezpieczeństwa w kodzie, zobacz [porady: zabezpieczenia sieci Web usługi bez za pomocą pliku zasad](http://go.microsoft.com/fwlink/?LinkId=73747). W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], aby określić wymagania dotyczące zabezpieczeń w kodzie, Utwórz wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy i dodać wystąpienia <xref:System.ServiceModel.Channels.SecurityBindingElement> do <xref:System.ServiceModel.Channels.BindingElementCollection>. Wymagania dotyczące potwierdzenia zabezpieczeń są ustawiane przy użyciu metody pomocnika trybu uwierzytelniania statyczne z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. Aby uzyskać więcej informacji o określaniu wymagania dotyczące zabezpieczeń przy użyciu kodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz [jak: utworzyć niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) i [porady: Tworzenie elementu SecurityBindingElement dla Określony tryb uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 zasad niestandardowych asercji  
 W WSE 3.0 istnieją dwa typy potwierdzeń niestandardowych zasad: te, które zabezpieczenia wiadomości protokołu SOAP i tych, które nie zabezpieczyć komunikatu protokołu SOAP. Potwierdzeń zasad, które Zabezpieczanie komunikatów SOAP pochodzi od WSE 3.0 `SecurityPolicyAssertion` klasy i pojęciach odpowiednik w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.  
  
 Istotne należy pamiętać, jest to podzbiór potwierdzeń zabezpieczeń gotowe WSE 3.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tryby uwierzytelniania. Jeśli utworzono potwierdzenia zasad niestandardowych w WSE 3.0, może być równoważny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tryb uwierzytelniania. Na przykład programu WSE 3.0 nie zapewnia CertificateOverTransport potwierdzenia zabezpieczeń, który jest odpowiednikiem `UsernameOverTransport` potwierdzenia zabezpieczeń gotowe, ale używa certyfikatu X.509 na potrzeby uwierzytelniania klienta. Jeśli zdefiniowano własne potwierdzenia zasad niestandardowych, w tym scenariuszu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sprawia, że migracja jest proste. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Definiuje tryb uwierzytelniania dla tego scenariusza, dzięki czemu można korzystać statycznych uwierzytelniania trybu metody pomocnicze, aby skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Gdy nie ma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tryb uwierzytelniania, który jest odpowiednikiem potwierdzenia zasad niestandardowych, które zabezpiecza wiadomości SOAP wyprowadzenia klasy z <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy i określ równoważne powiązania element. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Aby dokonać konwersji potwierdzenia zasad niestandardowych, które nie zabezpieczyć komunikatu protokołu SOAP, zobacz [filtrowanie](../../../../docs/framework/wcf/feature-details/filtering.md) i próbka [niestandardowy element przechwytujący](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 zabezpieczeń niestandardowy Token  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programowania do tworzenia niestandardowych token jest inna niż WSE 3.0. Aby uzyskać więcej informacji o tworzeniu niestandardowych token w WSE, zobacz [Tworzenie niestandardowych tokeny zabezpieczające](http://go.microsoft.com/fwlink/?LinkID=73750). Szczegółowe informacje na temat tworzenia niestandardowych token w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz [porady: Tworzenie niestandardowego tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 Menedżer tokenów niestandardowych  
 Model programowania do tworzenia niestandardowych Menedżer tokenów jest inna w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niż WSE 3.0. Aby uzyskać więcej informacji o sposobie tworzenia niestandardowych Menedżer tokenów i innymi składnikami, które są wymagane dla tokenu zabezpieczającego niestandardowych, zobacz [porady: Tworzenie niestandardowego tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Jeśli utworzono niestandardowe `UsernameToken` Menedżer tokenów zabezpieczających [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] udostępnia mechanizm łatwiejsze do określenia logika uwierzytelniania niż Tworzenie niestandardowych zabezpieczeń Menedżer tokenów. Aby uzyskać więcej informacji, zobacz [porady: Użyj niestandardowej nazwy użytkownika i modułu weryfikacji hasła](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Usługi sieci Web programu WSE 3.0, które korzystają MTOM zakodowane wiadomości SOAP  
 Aplikację WSE 3, takich jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji można określić kodowania w konfiguracji komunikatu MTOM. Aby przeprowadzić migrację tego ustawienia, Dodaj [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) do powiązania dla usługi. W poniższym przykładzie kodu pokazano, jak kodowanie MTOM jest określona w WSE 3.0 do usługi, która jest równoważna [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **USŁUGI WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Obsługa wiadomości  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Aplikacje programu WSE 3.0, korzystające z interfejsu API programu WSE wiadomości  
 W przypadku interfejsu API programu WSE wiadomości do uzyskania bezpośredniego dostępu do pliku XML, który jest przekazywane między klientem a usługą sieci Web aplikacji może zostać przekonwertowany do użycia "XML starego zwykły" (POX). Aby uzyskać więcej informacji na temat POX zobacz [współdziałanie z aplikacjami POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Aby uzyskać więcej informacji na temat interfejsu API programu WSE wiadomości zobacz [wysyłanie i odbieranie wiadomości przy użyciu programu WSE Messaging API SOAP](http://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Transporty  
  
### <a name="tcp"></a>TCP  
 Domyślnie klienci programu WSE 3.0 i usług sieci Web, który wysyła wiadomości SOAP przy użyciu transportu TCP nie współpracować ze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów i usług sieci Web. Jest to niezgodności z powodu różnic w ramek używany w protokole TCP oraz ze względu na wydajność. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbki szczegóły implementowania niestandardowych sesji TCP, który współdziała z programu WSE 3.0. Aby uzyskać szczegółowe informacje dotyczące tego przykładu, zobacz [Transport: współdziałanie protokołu TCP programu WSE 3.0](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Aby określić, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacja używa transportu TCP, użyj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Niestandardowe transportu  
 Odpowiednik transportu niestandardowego programu WSE 3.0 w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to rozszerzenie kanału. Aby uzyskać więcej informacji o tworzeniu rozszerzenia kanału, zobacz [rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowy cykl życia programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Porady: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
