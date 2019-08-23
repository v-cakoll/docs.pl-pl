---
title: Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 5f615af0340a68e43a184465ff99637e5e5e06c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965326"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF
Zalety migrowania usług sieci Web WSE 3,0 do Windows Communication Foundation (WCF) obejmują lepszą wydajność i obsługę dodatkowych transportów, dodatkowych scenariuszy zabezpieczeń i specyfikacji WS-*. Usługa sieci Web, która jest migrowana z WSE 3,0 do WCF, może mieć nawet 200% do 400% wydajności. Aby uzyskać więcej informacji na temat transportów obsługiwanych przez program WCF, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Listę scenariuszy obsługiwanych przez funkcję WCF można znaleźć w temacie [typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Lista specyfikacji obsługiwanych przez usługę WCF znajduje się w temacie [Przewodnik współdziałania protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Poniższe sekcje zawierają wskazówki dotyczące migrowania określonej funkcji usługi sieci Web WSE 3,0 do programu WCF.  
  
## <a name="general"></a>Ogólne  
 Aplikacje WSE 3,0 i WCF obejmują współdziałanie na poziomie przewodu oraz wspólny zestaw terminologii. Aplikacje WSE 3,0 i WCF są współdziałające w oparciu o zestaw specyfikacji WS-*, które są obsługiwane przez obie te funkcje. Po opracowaniu aplikacji WSE 3,0 lub WCF istnieje wspólny zestaw terminologii, takich jak nazwy zatwierdzeń zabezpieczeń gotowe w WSE i trybach uwierzytelniania.  
  
 Chociaż istnieje wiele podobnych aspektów między modelami programowania WCF i ASP.NET lub WSE 3,0, są one różne. Aby uzyskać szczegółowe informacje o modelu programowania WCF, zobacz podstawowe informacje o [cyklu programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
> Aby przeprowadzić migrację usługi sieci Web WSE do funkcji WCF, można użyć narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania klienta. Ten klient zawiera jednak interfejsy i klasy, których można użyć jako punktu wyjścia dla usługi WCF. Wygenerowane interfejsy mają <xref:System.ServiceModel.OperationContractAttribute> atrybut zastosowany do elementów członkowskich kontraktu <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> z właściwością ustawioną na `*`. Gdy klient WSE wywołuje usługę sieci Web przy użyciu tego ustawienia, zostanie zgłoszony następujący wyjątek: **Web. Services3. ResponseProcessingException: WSE910: Wystąpił błąd podczas przetwarzania komunikatu odpowiedzi i można znaleźć błąd w wyjątku**wewnętrznym. Aby rozwiązać ten problem, należy ustawić <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> Właściwość <xref:System.ServiceModel.OperationContractAttribute> `null` atrybutu na wartość nierówną, taką jak `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Zabezpieczenia  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Usługi sieci Web WSE 3,0 zabezpieczone przy użyciu pliku zasad  
 Usługi WCF mogą korzystać z pliku konfiguracji w celu zabezpieczenia usługi i ten mechanizm jest podobny do pliku zasad WSE 3,0. W WSE 3,0 w przypadku zabezpieczania usługi sieci Web przy użyciu pliku zasad należy użyć potwierdzenia zabezpieczeń gotowe lub potwierdzenia zasad niestandardowych. Potwierdzenia zabezpieczeń gotowe są mapowane blisko trybu uwierzytelniania elementu powiązania zabezpieczeń programu WCF. Nie tylko są tryby uwierzytelniania WCF i potwierdzenia zabezpieczeń WSE 3,0 gotowe o nazwie identycznej lub podobnej, jednak zabezpieczają komunikaty przy użyciu tych samych typów poświadczeń. Na przykład `usernameForCertificate` potwierdzenie zabezpieczeń gotowe w WSE 3,0 jest mapowane `UsernameForCertificate` na tryb uwierzytelniania w programie WCF. W poniższym przykładzie kodu pokazano, jak minimalne zasady, które korzystają `usernameForCertificate` z potwierdzenia zabezpieczeń gotowe w WSE 3,0, są `UsernameForCertificate` mapowane do trybu uwierzytelniania w programie WCF w ramach niestandardowego powiązania.  
  
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
  
 Aby przeprowadzić migrację ustawień zabezpieczeń usługi sieci Web WSE 3,0, które są określone w pliku zasad do WCF, należy utworzyć niestandardowe powiązanie w pliku konfiguracji, a potwierdzenie zabezpieczeń gotowe musi być ustawione na równoważny tryb uwierzytelniania. Dodatkowo niestandardowe powiązanie musi być skonfigurowane tak, aby korzystało z protokołu WS-Addressing z sierpnia 2004, gdy klienci WSE 3,0 komunikują się z usługą. Gdy migrowana usługa WCF nie wymaga komunikacji z klientami z systemem WSE 3,0 i musi zachować tylko parzystość zabezpieczeń, należy rozważyć użycie powiązań zdefiniowanych przez system w programie WCF z odpowiednimi ustawieniami zabezpieczeń zamiast tworzenia niestandardowego powiązania.  
  
 W poniższej tabeli wymieniono mapowanie między plikiem zasad WSE 3,0 i równoważnym powiązaniem niestandardowym w programie WCF.  
  
|WSE 3,0 gotowe Security Assertion|Konfiguracja niestandardowego powiązania WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security/>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych w programie WCF, zobacz [niestandardowe powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Usługi sieci Web WSE 3,0, które są zabezpieczone za pomocą kodu aplikacji  
 Niezależnie od tego, czy jest używany WSE 3,0 czy WCF, wymagania dotyczące zabezpieczeń można określić w kodzie aplikacji, a nie w konfiguracji. W WSE 3,0 jest to realizowane przez utworzenie klasy, która dziedziczy z `Policy` klasy, a następnie poprzez dodanie wymagań przez `Add` wywołanie metody. Aby uzyskać więcej informacji na temat określania wymagań dotyczących zabezpieczeń w kodzie [, zobacz How to: Zabezpiecz usługę sieci Web bez użycia pliku](https://go.microsoft.com/fwlink/?LinkId=73747)zasad. W programie WCF, aby określić wymagania dotyczące zabezpieczeń w kodzie, Utwórz wystąpienie <xref:System.ServiceModel.Channels.BindingElementCollection> klasy i Dodaj wystąpienie elementu <xref:System.ServiceModel.Channels.SecurityBindingElement> do <xref:System.ServiceModel.Channels.BindingElementCollection>. Wymagania dotyczące potwierdzenia zabezpieczeń są ustawiane przy użyciu metod <xref:System.ServiceModel.Channels.SecurityBindingElement> pomocnika trybu uwierzytelniania statycznego klasy. Aby uzyskać więcej informacji na temat określania wymagań dotyczących zabezpieczeń w kodzie za [pomocą programu WCF, zobacz How to: Utwórz niestandardowe powiązanie przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) i [instrukcje: Utwórz elementu SecurityBindingElement dla określonego trybu](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)uwierzytelniania.  
  
### <a name="wse-30-custom-policy-assertion"></a>Potwierdzenie zasad niestandardowych WSE 3,0  
 W WSE 3,0 istnieją dwa typy potwierdzeń zasad niestandardowych: te, które zabezpieczają komunikat protokołu SOAP i te, które nie zabezpieczają wiadomości protokołu SOAP. Zasady potwierdzają, że bezpieczne komunikaty protokołu SOAP pochodzą z `SecurityPolicyAssertion` klasy WSE 3,0, a koncepcyjne odpowiednik w <xref:System.ServiceModel.Channels.SecurityBindingElement> WCF jest klasą.  
  
 Ważną kwestią jest to, że potwierdzenia zabezpieczeń w WSE 3,0 gotowe są podzbiorem trybów uwierzytelniania programu WCF. Jeśli utworzono potwierdzenie zasad niestandardowych w programie WSE 3,0, może istnieć odpowiedni tryb uwierzytelniania WCF. Na przykład WSE 3,0 nie dostarcza potwierdzenia zabezpieczeń CertificateOverTransport, który jest odpowiednikiem `UsernameOverTransport` zabezpieczenia gotowe, ale używa certyfikatu X. 509 na potrzeby uwierzytelniania klientów. Jeśli zdefiniowano własne potwierdzenie zasad niestandardowych w tym scenariuszu, usługa WCF przetworzy prostą migrację. Funkcja WCF definiuje tryb uwierzytelniania w tym scenariuszu, dlatego można skorzystać z metod pomocnika trybu uwierzytelniania statycznego w celu skonfigurowania<xref:System.ServiceModel.Channels.SecurityBindingElement>programu WCF.  
  
 Jeśli nie istnieje tryb uwierzytelniania WCF, który jest równoważny z niestandardowym potwierdzeniem zasad, który zabezpiecza komunikaty protokołu SOAP, należy utworzyć <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>klasę <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> z <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>lub klasy WCF i określić odpowiedni element powiązania. Aby uzyskać więcej informacji, [zobacz How to: Utwórz niestandardowe powiązanie przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Aby przekonwertować niestandardowe potwierdzenie zasad, które nie zabezpiecza wiadomości protokołu SOAP, zobacz [filtrowanie](../../../../docs/framework/wcf/feature-details/filtering.md) i przykład [niestandardowego interceptora komunikatów](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Niestandardowy token zabezpieczający WSE 3,0  
 Model programowania WCF służący do tworzenia tokenów niestandardowych jest inny niż WSE 3,0. Aby uzyskać szczegółowe informacje na temat tworzenia tokenów niestandardowych w programie WSE, zobacz [Tworzenie niestandardowych tokenów zabezpieczających](https://go.microsoft.com/fwlink/?LinkID=73750). Aby uzyskać szczegółowe informacje na temat tworzenia tokenu niestandardowego w programie [WCF, zobacz How to: Utwórz token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)niestandardowy.  
  
### <a name="wse-30-custom-token-manager"></a>Menedżer niestandardowych tokenów WSE 3,0  
 Model programowania służący do tworzenia niestandardowego menedżera tokenów różni się od programu WCF niż WSE 3,0. Aby uzyskać szczegółowe informacje na temat sposobu tworzenia niestandardowego menedżera tokenów i innych składników, które są wymagane dla niestandardowego tokenu zabezpieczającego [, zobacz How to: Utwórz token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)niestandardowy.  
  
> [!NOTE]
> Jeśli utworzono niestandardowy `UsernameToken` Menedżer tokenów zabezpieczających, WCF oferuje łatwiejszy mechanizm określania logiki uwierzytelniania niż tworzenie niestandardowego menedżera tokenów zabezpieczeń. Aby uzyskać więcej informacji, [zobacz How to: Użyj niestandardowej nazwy użytkownika i modułu sprawdzania](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)haseł.  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Usługi sieci Web WSE 3,0 korzystające z zakodowanych komunikatów SOAP  
 Podobnie jak w przypadku aplikacji WSE 3, aplikacja WCF może określić kodowanie komunikatów MTOM w konfiguracji. Aby przeprowadzić migrację tego ustawienia, Dodaj [ \<> mtomMessageEncoding](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) do powiązania dla usługi. Poniższy przykład kodu demonstruje, jak Kodowanie MTOM jest określone w WSE 3,0 dla usługi, która jest równoważna w WCF.  
  
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
  
## <a name="messaging"></a>Obsługa komunikatów  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Aplikacje WSE 3,0 korzystające z interfejsu API obsługi komunikatów WSE  
 Gdy interfejs API komunikatów WSE Messaging jest używany do uzyskania bezpośredniego dostępu do pliku XML, który jest przekazywany między klientem a usługą sieci Web, aplikacja może zostać przekonwertowana w celu użycia "zwykłego starego XML" (POX). Aby uzyskać więcej informacji na temat POX, zobacz Współdziałanie [z aplikacjami POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Aby uzyskać więcej informacji na temat interfejsu API obsługi komunikatów WSE, zobacz [wysyłanie i otrzymywanie komunikatów SOAP przy użyciu interfejsu API obsługi WSE Messaging](https://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Transporty  
  
### <a name="tcp"></a>TCP  
 Domyślnie klienci WSE 3,0 i usługi sieci Web, które wysyłają komunikaty protokołu SOAP przy użyciu transportu TCP, nie współpracują z klientami i usługami sieci Web WCF. Niezgodność wynika z różnic w obciążeniu ramek używanych w protokole TCP i ze względów wydajnościowych. Jednak Przykładowa procedura WCF zawiera szczegółowe informacje dotyczące implementowania niestandardowej sesji protokołu TCP, która współdziała z WSE 3,0. Aby uzyskać szczegółowe informacje na temat tego [przykładu, zobacz Transport: Współdziałanie](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)TCP WSE 3,0.  
  
 Aby określić, że aplikacja WCF używa transportu TCP, użyj [ \<> NetTcpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transport niestandardowy  
 Odpowiednikiem WSE 3,0 Custom transport in WCF jest rozszerzenie kanału. Aby uzyskać szczegółowe informacje na temat tworzenia rozszerzenia kanału, zobacz [Rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowy cykl życia programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Instrukcje: Utwórz elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
