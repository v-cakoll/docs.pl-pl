---
title: Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 8f79674350109d111fe263704dee6c40c1a12451
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184570"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrowanie usług sieci Web programu WSE 3.0 do usługi WCF
Korzyści z migracji usług sieci Web gpw 3.0 do programu Windows Communication Foundation (WCF) obejmują lepszą wydajność i obsługę dodatkowych transportów, dodatkowe scenariusze zabezpieczeń i specyfikacje WS-*. Usługa sieci Web, która jest migrowana z usługi WSE 3.0 do WCF może wystąpić do 200% do 400% poprawy wydajności. Aby uzyskać więcej informacji na temat transportów obsługiwanych przez WCF, zobacz [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Aby uzyskać listę scenariuszy obsługiwanych przez WCF, zobacz [Typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Aby uzyskać listę specyfikacji obsługiwanych przez WCF, zobacz [Przewodnik interoperacyjności protokołów usług sieci Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 W poniższych sekcjach przedstawiono wskazówki dotyczące migracji określonej funkcji usługi sieci Web GPW 3.0 do WCF.  
  
## <a name="general"></a>Ogólne  
 Aplikacje WSE 3.0 i WCF obejmują interoperacyjność na poziomie drutu i wspólny zestaw terminologii. Aplikacje WSE 3.0 i WCF są interoperacyjne na poziomie drutu w oparciu o zestaw specyfikacji WS-*, które obsługują. Po opracowaniu aplikacji WSE 3.0 lub WCF istnieje wspólny zestaw terminologii, taki jak nazwy potwierdzeń zabezpieczeń "pod klucz" na gpw i tryby uwierzytelniania.  
  
 Chociaż istnieje wiele podobnych aspektów między WCF i ASP.NET lub GPW 3.0 modeli programowania, są one różne. Aby uzyskać szczegółowe informacje na temat modelu programowania WCF, zobacz [Podstawowy cykl życia programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
> Aby przeprowadzić migrację usługi sieci Web WSE do WCF, narzędzie [Narzędzie do metadanych ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może służyć do generowania klienta. Ten klient zawiera jednak interfejsy i klasy, które mogą być używane jako punkt wyjścia dla usługi WCF zbyt. Interfejsy, które są <xref:System.ServiceModel.OperationContractAttribute> generowane mają atrybut stosowany do członków <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> umowy `*`z właściwością ustawioną na . Gdy klient GPW wywołuje usługę sieci Web z tym ustawieniem, zgłaszany jest następujący wyjątek: **Web.Services3.ResponseProcessingException: WSE910: Wystąpił błąd podczas przetwarzania komunikatu odpowiedzi i można znaleźć błąd w wewnętrznym wyjątku**. Aby to złagodzić, <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> ustaw właściwość atrybutu <xref:System.ServiceModel.OperationContractAttribute> na`null` wartość niewartościową, taką jak `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Zabezpieczenia  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Usługi sieci Web GPW 3.0 zabezpieczone za pomocą pliku zasad  
 Usługi WCF można użyć pliku konfiguracji w celu zabezpieczenia usługi i mechanizm ten jest podobny do pliku zasad GPW 3.0. Na stronie GPW 3.0 podczas zabezpieczania usługi sieci Web przy użyciu pliku zasad można użyć potwierdzenia zabezpieczeń "pod klucz" lub potwierdzenia zasad niestandardowych. Potwierdzeń zabezpieczeń "pod klucz" mapuje ściśle do trybu uwierzytelniania elementu wiązania zabezpieczeń WCF. Nie tylko tryby uwierzytelniania WCF i WSE 3.0 "pod klucz" potwierdzenia zabezpieczeń o tej samej lub podobnej nazwie, zabezpieczają wiadomości przy użyciu tych samych typów poświadczeń. Na przykład `usernameForCertificate` twierdzenie zabezpieczeń "pod klucz" w gpw 3.0 mapuje do trybu `UsernameForCertificate` uwierzytelniania w WCF. Poniższe przykłady kodu pokazują, jak minimalne `usernameForCertificate` zasady, która używa potwierdzenia zabezpieczeń "pod klucz" na gpw 3.0 mapuje do trybu `UsernameForCertificate` uwierzytelniania w WCF w powiązaniu niestandardowym.  
  
 **GPW 3.0**  
  
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
  
 Aby przeprowadzić migrację ustawień zabezpieczeń usługi sieci Web gpw 3.0 określonych w pliku zasad do WCF, w pliku konfiguracyjnym należy utworzyć powiązanie niestandardowe, a asercja zabezpieczeń "pod klucz" musi być ustawiona na równoważny tryb uwierzytelniania. Ponadto niestandardowe powiązanie musi być skonfigurowane do używania specyfikacji adresowania WS z sierpnia 2004 r., gdy klienci usługi WSE 3.0 komunikują się z usługą. Gdy zmigrowana usługa WCF nie wymaga komunikacji z klientami WSE 3.0 i może zachowywać tylko parzystość zabezpieczeń, należy rozważyć użycie powiązań zdefiniowanych przez system WCF z odpowiednimi ustawieniami zabezpieczeń zamiast tworzenia niestandardowego powiązania.  
  
 W poniższej tabeli wymieniono mapowanie między plikiem zasad GPW 3.0 a równoważnym powiązaniem niestandardowym w WCF.  
  
|WSE 3.0 Twierdzenie zabezpieczeń "pod klucz"|Niestandardowa konfiguracja wiązania WCF|  
|----------------------------------------|--------------------------------------|  
|\<nazwa użytkownikaOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Bezpieczeństwo />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<nazwa użytkownikaForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Bezpieczeństwo />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Aby uzyskać więcej informacji na temat tworzenia niestandardowych powiązań w WCF, zobacz [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Usługi sieci Web GPW 3.0 zabezpieczone za pomocą kodu aplikacji  
 Niezależnie od tego, czy jest używany WSE 3.0 lub WCF, wymagania dotyczące zabezpieczeń można określić w kodzie aplikacji, a nie w konfiguracji. W gpse 3.0 jest to realizowane przez utworzenie klasy, `Policy` która pochodzi z klasy, a `Add` następnie przez dodanie wymagań przez wywołanie metody. Aby uzyskać więcej informacji na temat określania wymagań dotyczących zabezpieczeń w kodzie, zobacz [Jak: Zabezpieczanie usługi sieci Web bez użycia pliku zasad](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10)). W WCF, aby określić wymagania dotyczące zabezpieczeń <xref:System.ServiceModel.Channels.BindingElementCollection> w kodzie, należy <xref:System.ServiceModel.Channels.SecurityBindingElement> utworzyć <xref:System.ServiceModel.Channels.BindingElementCollection>wystąpienie klasy i dodać wystąpienie a do . Wymagania dotyczące asercji zabezpieczeń są ustawiane przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement> metod pomocniczych trybu uwierzytelniania statycznego klasy. Aby uzyskać więcej informacji na temat określania wymagań zabezpieczeń w kodzie przy użyciu WCF, zobacz [Jak: Tworzenie niestandardowego powiązania przy użyciu securitybindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md) i [jak: Tworzenie SecurityBindingElement dla określonego trybu uwierzytelniania](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Twierdzenie zasad niestandardowych GPW 3.0  
 Na gpw 3.0 istnieją dwa typy potwierdzeń zasad niestandardowych: te, które zabezpieczają komunikat PROTOKOŁU SOAP i te, które nie zabezpieczają komunikatu SOAP. Twierdzenia zasad, które bezpieczne komunikaty PROTOKOŁU SOAP pochodzą `SecurityPolicyAssertion` z klasy WSE 3.0, a koncepcyjny odpowiednik w WCF jest klasą. <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 Ważnym punktem należy zauważyć, że potwierdzenia zabezpieczeń GPW 3.0 "pod klucz" są podzbiorem trybów uwierzytelniania WCF. Jeśli utworzono asercja zasad niestandardowych w gpw 3.0, może istnieć równoważny tryb uwierzytelniania WCF. Na przykład gpse 3.0 nie zapewnia CertificateOverTransport asencja `UsernameOverTransport` zabezpieczeń, który jest odpowiednikiem potwierdzenia zabezpieczeń pod klucz, ale używa certyfikatu X.509 do celów uwierzytelniania klienta. Jeśli zdefiniowano własne asercja zasad niestandardowych dla tego scenariusza, WCF sprawia, że migracja jest prosta. WCF definiuje tryb uwierzytelniania dla tego scenariusza, dzięki czemu można skorzystać z metod pomocnika<xref:System.ServiceModel.Channels.SecurityBindingElement>trybu uwierzytelniania statycznego, aby skonfigurować WCF .  
  
 Jeśli nie ma trybu uwierzytelniania WCF, który jest odpowiednikiem potwierdzenia zasad niestandardowych, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>który zabezpiecza komunikaty SOAP, wywoż klasę z <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, lub WCF klas i określić równoważny element wiązania. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie niestandardowego powiązania przy użyciu securitybindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Aby przekonwertować niestandardowe twierdzenie zasad, które nie zabezpiecza wiadomości PROTOKOŁU SOAP, zobacz [Filtrowanie](../../../../docs/framework/wcf/feature-details/filtering.md) i przykładowy [element przechwytujący wiadomości niestandardowe](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Niestandardowy token zabezpieczający GPW 3.0  
 Model programowania WCF do tworzenia tokenu niestandardowego różni się od GPW 3.0. Aby uzyskać szczegółowe informacje na temat tworzenia tokenu niestandardowego na gpw, zobacz [Tworzenie niestandardowych tokenów zabezpieczających](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10)). Aby uzyskać szczegółowe informacje na temat tworzenia tokenu niestandardowego w WCF, zobacz [Jak: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>Niestandardowy menedżer tokenów GPW 3.0  
 Model programowania do tworzenia menedżera tokenów niestandardowych jest inny w WCF niż WSE 3.0. Aby uzyskać szczegółowe informacje dotyczące tworzenia niestandardowego menedżera tokenów i innych składników, które są wymagane dla niestandardowego tokenu zabezpieczającego, zobacz [Jak: Tworzenie tokenu niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
> Jeśli utworzono `UsernameToken` niestandardowy menedżer tokenów zabezpieczeń, WCF zapewnia łatwiejszy mechanizm do określenia logiki uwierzytelniania niż tworzenie niestandardowego menedżera tokenów zabezpieczających. Aby uzyskać więcej informacji, zobacz [Jak: Używanie niestandardowej nazwy użytkownika i walidatora hasła](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Usługi sieci Web WSE 3.0 korzystające z komunikatów PROTOKOŁU SOAP zakodowanych w mtom  
 Podobnie jak w aplikacji GPW 3, aplikacja WCF można określić kodowanie komunikatów MTOM w konfiguracji. Aby przeprowadzić migrację tego ustawienia, dodaj [ \<>kodowania mtomMessageencoding](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) do powiązania usługi. Poniższy przykład kodu pokazuje, jak kodowanie MTOM jest określony w GPW 3.0 dla usługi, która jest równoważna w WCF.  
  
 **GPW 3.0**  
  
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
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Aplikacje WSE 3.0 korzystające z interfejsu API wiadomości GPW  

 Gdy interfejs API obsługi wiadomości WSE jest używany do uzyskiwania bezpośredniego dostępu do kodu XML, który jest komunikowany między klientem a usługą sieci Web, aplikacja może zostać przekonwertowana na użycie "Zwykłego starego kodu XML" (POX). Aby uzyskać więcej informacji na temat pox, zobacz [Interoperacyjność z aplikacjami POX](interoperability-with-pox-applications.md). Aby uzyskać więcej informacji na temat interfejsu API wiadomości GPW, zobacz [Wysyłanie i odbieranie wiadomości MYDŁA za pomocą interfejsu API wiadomości WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10)).  
  
## <a name="transports"></a>Transporty  
  
### <a name="tcp"></a>TCP  
 Domyślnie klienci WSE 3.0 i usługi sieci Web, które wysyłają wiadomości PROTOKOŁU SOAP przy użyciu transportu TCP, nie współdziałają z klientami WCF i usługami sieci Web. Ta niezgodność wynika z różnic w ramkach używanych w protokole TCP i ze względu na wydajność. Jednak WCF przykładu szczegółowe sposób implementacji niestandardowej sesji TCP, która współdziała z GPW 3.0. Aby uzyskać szczegółowe informacje na temat tego [przykładu, zobacz Transport: GPW 3.0 Interoperacyjność TCP](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Aby określić, że aplikacja WCF używa transportu TCP, użyj [ \<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transport niestandardowy  
 Odpowiednik transportu niestandardowego GPW 3.0 w WCF jest rozszerzeniem kanału. Aby uzyskać szczegółowe informacje na temat tworzenia rozszerzenia kanału, zobacz [Rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowy cykl życia programowania](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
