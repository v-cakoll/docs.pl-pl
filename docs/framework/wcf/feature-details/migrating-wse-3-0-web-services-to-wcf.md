---
title: Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 21e36be178bb0dd0c52213d8c4c1387a564a0e5a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580307"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF
Zalety migracji usług sieci Web programu WSE 3.0 do usługi Windows Communication Foundation (WCF) obejmują lepszą wydajność i obsługę dodatkowych transportów scenariuszach zapewnienia dodatkowych zabezpieczeń i WS-* specyfikacji. Usługa sieci Web, która jest migrowana z usługami WSE 3.0 do usługi WCF, mogą występować maksymalnie 200 – 400% zwiększenie wydajności. Aby uzyskać więcej informacji na temat transportu obsługiwane przez architekturę WCF, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Aby uzyskać listę scenariuszy obsługiwanych przez architekturę WCF, zobacz [typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Aby uzyskać listę specyfikacje, które są obsługiwane przez architekturę WCF, zobacz [przewodnik dotyczący współpracy protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Poniższe sekcje zawierają wskazówki dotyczące sposobu przeprowadzenia migracji określonych funkcji usługi sieci Web programu WSE 3.0 do usługi WCF.  
  
## <a name="general"></a>Ogólne  
 Aplikacje programu WSE 3.0 i WCF obejmują protokół sieciowy niskiego poziomu współpracy i wspólny zbiór terminologii. Aplikacje programu WSE 3.0 i WCF to protokół sieciowy niskiego poziomu interoperacyjne a oparte na zestawie WS-* specyfikacje, które obsługują oba. Gdy opracowywana zostaje aplikacja WCF i usługami WSE 3.0 istnieje wspólny zbiór terminologii, takich jak nazwy potwierdzeń zabezpieczeń gotowej do użycia w trybach uwierzytelniania i WSE.  
  
 Chociaż istnieje wiele aspektów podobne między WCF i platforma ASP.NET lub programu WSE 3.0 modeli programowania, różnią się one. Aby uzyskać szczegółowe informacje o modelu programowania usługi WCF, zobacz [podstawowy cykl życia programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  Aby przeprowadzić migrację usługi sieci Web programu WSE WCF [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie może służyć do generowania klienta. Ten klient jednak zawiera interfejsy i klas, które mogą być używane jako początkowy punkt dla usługi WCF zbyt. Interfejsy, które są generowane mają <xref:System.ServiceModel.OperationContractAttribute> zastosowany do elementów członkowskich kontrakt o <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> właściwością `*`. Gdy klient programu WSE wywołuje usługę sieci Web to ustawienie, jest zgłaszany następujący wyjątek: **Web.Services3.ResponseProcessingException: WSE910: Wystąpił błąd podczas przetwarzania komunikatu odpowiedzi i prowadzą błąd wewnętrzny wyjątek**. Aby rozwiązać ten problem, należy ustawić <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> właściwość <xref:System.ServiceModel.OperationContractAttribute> atrybutu do innej niż`null` wartości, takich jak `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Zabezpieczenia  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Usługi sieci Web programu WSE 3.0, które są chronione przy użyciu pliku zasad  
 Usług WCF można użyć pliku konfiguracyjnego zabezpieczyć usługę, a ten mechanizm jest podobny do pliku zasad programu WSE 3.0. Programu WSE 3.0 zabezpieczania usługi sieci Web przy użyciu pliku zasad Użyj asercji zabezpieczeń gotowej do użycia lub asercję zasad niestandardowych. Potwierdzenia gotowej do użycia zabezpieczeń są ściśle mapowane na tryb uwierzytelniania elementu powiązania zabezpieczeń programu WCF. Nie tylko są tryby uwierzytelniania usługi WCF i potwierdzeń zabezpieczeń gotowej do użycia programu WSE 3.0 samej nazwie lub podobnie ich zabezpieczanie wiadomości przy użyciu takich samych typach poświadczeń. Na przykład `usernameForCertificate` asercji zabezpieczeń gotowej do użycia w programu WSE 3.0 mapuje `UsernameForCertificate` tryb uwierzytelniania programu WCF. Poniższe przykłady kodu ilustrują sposób minimalne zasady, które używa `usernameForCertificate` asercji zabezpieczeń gotowej do użycia w programu WSE 3.0 mapuje `UsernameForCertificate` tryb uwierzytelniania programu WCF do niestandardowego powiązania.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Aby przeprowadzić migrację ustawień zabezpieczeń usługi sieci Web programu WSE 3.0, które są określone w pliku zasad do programu WCF, należy utworzyć niestandardowego powiązania w pliku konfiguracji i potwierdzenie gotowej do użycia zabezpieczeń musi być równa jej tryb uwierzytelniania równoważne. Ponadto niestandardowego powiązania musi być skonfigurowana w taki sposób, do użycia z sierpnia 2004 r. specyfikacji WS-Addressing, gdy klienci programu WSE 3.0 komunikują się z usługą. Jeśli zmigrowane usługi WCF nie wymaga komunikacji z klientami programu WSE 3.0, należy zachować tylko parzystości zabezpieczeń należy wziąć pod uwagę przy użyciu powiązań zdefiniowanych przez system WCF przy użyciu ustawień zabezpieczeń odpowiednich zamiast tworzenia niestandardowego powiązania.  
  
 W poniższej tabeli wymieniono mapowanie między plik zasad programu WSE 3.0 i równoważne niestandardowego powiązania programu WCF.  
  
|Programu WSE 3.0 zabezpieczeń gotowej do użycia potwierdzenia|Konfiguracja powiązania niestandardowego programu WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych w programie WCF, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Usługi sieci Web programu WSE 3.0, które są chronione przy użyciu kodu aplikacji  
 Czy ma być używana programu WSE 3.0 lub usługi WCF, wymagania dotyczące zabezpieczeń można określić w kodzie aplikacji, a nie w konfiguracji. W programu WSE 3.0 to odbywa się przez utworzenie klasy, która pochodzi od klasy `Policy` klasy, a następnie przez dodanie wymagania, wywołując `Add` metody. Aby uzyskać więcej informacji na temat określania wymagań dotyczących zabezpieczeń w kodzie, zobacz [instrukcje: Zabezpieczanie sieci Web usługi bez za pomocą pliku zasad](https://go.microsoft.com/fwlink/?LinkId=73747). W programie WCF, aby określić wymagania dotyczące zabezpieczeń w kodzie, Utwórz wystąpienie obiektu <xref:System.ServiceModel.Channels.BindingElementCollection> klasy i dodaje wystąpienie <xref:System.ServiceModel.Channels.SecurityBindingElement> do <xref:System.ServiceModel.Channels.BindingElementCollection>. Wymagania potwierdzenia zabezpieczeń są ustawiane przy użyciu metody pomocnicze trybu uwierzytelniania statyczne z <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy. Aby uzyskać więcej informacji na temat określania wymagań dotyczących zabezpieczeń w kodzie przy użyciu usługi WCF, zobacz [porady: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) i [porady: Tworzenie elementu SecurityBindingElement dla określonych Tryb uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Programu WSE 3.0 zasad niestandardowych asercji  
 W programu WSE 3.0 istnieją dwa typy niestandardowych asercji zasad: te, które zabezpieczenia wiadomości SOAP i te, które nie zostanie zabezpieczony komunikatu protokołu SOAP. Asercji zasad, które zabezpieczają komunikaty protokołu SOAP pochodzi z usługami WSE 3.0 `SecurityPolicyAssertion` klasy i pojęciach równoważne w programie WCF jest <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.  
  
 To ważny punkt, należy pamiętać, to potwierdzeń zabezpieczeń gotowej do użycia programu WSE 3.0 podzbiór tryby uwierzytelniania usługi WCF. Jeśli utworzono potwierdzeń niestandardowych zasad programu WSE 3.0, może być równoważne trybu uwierzytelniania usługi WCF. Na przykład programu WSE 3.0 nie zapewnia CertificateOverTransport asercji zabezpieczeń, który jest odpowiednikiem `UsernameOverTransport` asercji zabezpieczeń gotowej do użycia, ale używa certyfikatu X.509 na potrzeby uwierzytelniania klienta. Jeśli zdefiniowano własne asercji zasad niestandardowych, w tym scenariuszu WCF sprawia, że migracja proste. Usługi WCF definiuje tryb uwierzytelniania dla tego scenariusza, dzięki czemu można wykorzystać statyczne uwierzytelniania trybu metody pomocnika do skonfigurowania usługi WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Jeśli nie jest WCF tryb uwierzytelniania, który jest odpowiednikiem asercji zasad niestandardowych, który zabezpiecza komunikaty protokołu SOAP, należy wyprowadzić klasę z <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF klasy i określ element powiązania równoważne. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Aby dokonać konwersji asercji zasad niestandardowych, które nie zabezpiecza komunikatu protokołu SOAP, zobacz [filtrowanie](../../../../docs/framework/wcf/feature-details/filtering.md) i próbki [niestandardowy element przechwytujący](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Token programu WSE 3.0 zabezpieczeń niestandardowe  
 Model programowania WCF do utworzenia tokenu niestandardowego różni się od programu WSE 3.0. Aby uzyskać szczegółowe informacje o tworzeniu niestandardowy token w WSE, zobacz [tworzenie niestandardowe tokeny zabezpieczające](https://go.microsoft.com/fwlink/?LinkID=73750). Aby uzyskać szczegółowe informacje o tworzeniu niestandardowy token w usłudze WCF, zobacz [jak: utworzyć niestandardowe tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 Menedżer tokenów niestandardowych  
 Model programowania do tworzenia niestandardowych Menedżer tokenów różni się w usłudze WCF od programu WSE 3.0. Aby uzyskać szczegółowe informacje o sposobie tworzenia niestandardowych Menedżer tokenów i innymi składnikami, które są wymagane dla tokenu zabezpieczającego niestandardowych, zobacz [porady: Tworzenie niestandardowego tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Jeśli utworzono niestandardowe `UsernameToken` Menedżer tokenów zabezpieczeń, WCF udostępnia mechanizm łatwiej określić logiki uwierzytelniania niż Tworzenie niestandardowego zabezpieczeń Menedżer tokenów. Aby uzyskać więcej informacji, zobacz [porady: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Usługi sieci Web programu WSE 3.0, które korzystają z MTOM zakodowany komunikaty protokołu SOAP  
 Podobnie jak w przypadku aplikacji WSE 3 aplikacji WCF można określić kodowania w konfiguracji komunikatu MTOM. Aby przeprowadzić migrację tego ustawienia, należy dodać [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) powiązanie dla usługi. Poniższy przykład kodu pokazuje, jak kodowanie MTOM określono programu WSE 3.0 do usługi, która jest równoważna w programie WCF.  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Obsługa wiadomości  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Aplikacje programu WSE 3.0, używanego przez interfejs API komunikatów WSE  
 Gdy interfejs API komunikatów WSE jest używany do uzyskania bezpośredniego dostępu do pliku XML, które są przekazywane między klientem a usługą sieci Web, aplikacji, można je przekształcić pod kątem "Zwykłego starego kodu XML" (POX). Aby uzyskać więcej szczegółów na temat POX zobacz [współdziałanie z aplikacjami POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Aby uzyskać więcej szczegółów na temat interfejsu API programu WSE wiadomości zobacz [wysyłanie i odbieranie wiadomości przy użyciu programu WSE Messaging API SOAP](https://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Transporty  
  
### <a name="tcp"></a>TCP  
 Domyślnie klienci programu WSE 3.0 i usług sieci Web, które wysyłają komunikaty protokołu SOAP, za pomocą transportu TCP nie współdziałać z WCF klientów i usług sieci Web. Ta niezgodność jest z powodu różnic w ramki używane w protokole TCP oraz ze względu na wydajność. Jednak próbkę WCF szczegółowo opisuje sposób implementacji niestandardową sesję protokołu TCP, który współdziała z usługami WSE 3.0. Aby uzyskać szczegółowe informacje dotyczące tego przykładu, zobacz [Transport: współdziałanie protokołu TCP z usługami WSE 3.0](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Aby określić, że aplikacja WCF korzysta z warstwy transportowej TCP, użyj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transport w niestandardowych  
 Wielokrotność transportu niestandardowe programu WSE 3.0 w programie WCF jest rozszerzeniem kanału. Aby uzyskać szczegółowe informacje o tworzeniu rozszerzenia kanału, zobacz [rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowy cykl życia programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
