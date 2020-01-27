---
title: Przegląd zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
ms.openlocfilehash: 1e551572fa6d94e9fd1170eb7e3b258f2e8fb926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728890"
---
# <a name="windows-communication-foundation-security-overview"></a>Omówienie zabezpieczeń Windows Communication Foundation
Windows Communication Foundation (WCF) to platforma programowania oparta na komunikatach protokołu SOAP, a zabezpieczenia komunikatów między klientami i usługami są niezbędne do ochrony danych. Funkcja WCF zapewnia uniwersalną i międzyplatformową platforma do wymiany bezpiecznych komunikatów opartych na istniejącej infrastrukturze zabezpieczeń i uznanych standardach zabezpieczeń dla komunikatów protokołu SOAP.  
  
> [!NOTE]
> Aby uzyskać kompleksowy przewodnik dotyczący zabezpieczeń WCF, zobacz [wskazówki dotyczące zabezpieczeń WCF](https://archive.codeplex.com/?p=WCFSecurity).  
  
 W programie WCF są używane koncepcje, które są znane, jeśli masz wbudowane bezpieczne, rozproszone aplikacje z istniejącymi technologiami, takimi jak HTTPS, zintegrowane zabezpieczenia systemu Windows lub nazwy użytkowników i hasła do uwierzytelniania użytkowników. WCF nie tylko integruje się z istniejącymi infrastrukturami zabezpieczeń, ale również rozszerza zabezpieczenia rozproszone poza domeny systemu Windows przy użyciu bezpiecznych komunikatów protokołu SOAP. Należy rozważyć implementację istniejących mechanizmów zabezpieczeń w programie WCF przy użyciu funkcji SOAP jako protokołu oprócz istniejących protokołów. Na przykład poświadczenia identyfikujące klienta lub usługę, takie jak nazwa użytkownika i hasło lub certyfikaty X. 509, mają międzyoperacyjnych profilów protokołu SOAP opartych na języku XML. Korzystając z tych profilów, wiadomości są bezpiecznie wymieniane przez skorzystanie z zalet otwartych specyfikacji, takich jak podpisy cyfrowe XML i szyfrowanie XML. Aby zapoznać się z listą specyfikacji, zobacz [Protokoły usług sieci Web obsługiwane przez powiązania współdziałania dostarczone przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Kolejną równoległością jest Component Object Model (COM) na platformie Windows, co umożliwia bezpieczne, rozproszone aplikacje. Model COM ma kompleksowy mechanizm zabezpieczeń, dzięki któremu kontekst zabezpieczeń może być przepływany między składnikami; Ten mechanizm wymusza integralność, poufność i uwierzytelnianie. Jednak COM nie włącza międzyplatformowych, zabezpieczonych komunikatów, takich jak WCF. Korzystając z programu WCF, można tworzyć usługi i klientów, które rozciągają się od domen systemu Windows przez Internet. Komunikaty interoperacyjne programu WCF są niezbędne do tworzenia dynamicznych, opartych na biznesie usług, które ułatwiają ochronę informacji użytkownika.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation korzyści z zabezpieczeń  
 WCF to rozproszona platforma programistyczna oparta na komunikatach protokołu SOAP. Korzystając z programu WCF, można tworzyć aplikacje, które działają zarówno jako usługi, jak i klienci usług, tworząc i przetwarzając komunikaty z nieograniczonej liczby innych usług i klientów. W takiej aplikacji rozproszonej komunikaty mogą przepływać z węzła do węzła, za pośrednictwem zapór, Internetu i wielu pośredników SOAP. W ten sposób wprowadzono różne zagrożenia bezpieczeństwa komunikatów. Poniższe przykłady ilustrują niektóre typowe zagrożenia, które zabezpieczenia WCF mogą pomóc wyeliminować podczas wymiany komunikatów między jednostkami:  
  
- Obserwacja ruchu sieciowego w celu uzyskania poufnych informacji. Na przykład w scenariuszu online Bank klient żąda transferu środków z jednego konta do innego. Złośliwy użytkownik przechwytuje komunikat i ma numer konta i hasło w późniejszym czasie wykonuje transfer środków ze złamanego konta.  
  
- Nieautoryzowane podmioty działające jako usługi bez świadomości klienta. W tym scenariuszu złośliwy użytkownik (nieautoryzowany) działa jako usługa online i przechwytuje komunikaty z klienta w celu uzyskania poufnych informacji. Następnie złośliwe dane są wykorzystywane do transferowania środków z zagrożonego konta. Atakujący jest również znany *atak wyłudzania informacji*.  
  
- Zmiana komunikatów w celu uzyskania innego wyniku niż przewidziany dla obiektu wywołującego. Na przykład zmiana numeru konta, na które jest dokonywana kaucja, umożliwia funduszom przechodzenie do nieautoryzowanego konta.  
  
- Haker odtwarza, w którym uciążliwy haker odtwarza takie samo zamówienie zakupu. Na przykład księgarni online odbiera setki zamówień i wysyła je do klienta, który go nie zamówił.  
  
- Niezdolność usługi do uwierzytelniania klienta. W takim przypadku usługa nie może zagwarantować, że odpowiednia osoba wykona transakcję.  
  
 Podsumowując, zabezpieczenia transferu zapewniają następujące gwarancje:  
  
- Uwierzytelnianie punktu końcowego usługi.  
  
- Uwierzytelnianie podmiotu zabezpieczeń (inicjator) klienta.  
  
- Integralność komunikatów.  
  
- Poufność komunikatów.  
  
- Wykrywanie powtarzania.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integracja z istniejącymi infrastrukturami zabezpieczeń  
 Często wdrożenia usługi sieci Web mają istniejące rozwiązania zabezpieczeń, na przykład SSL (SSL) lub protokół Kerberos. Niektóre z nich korzystają z infrastruktury zabezpieczeń, która została już wdrożona, na przykład domen systemu Windows korzystających z Active Directory. Często konieczne jest zintegrowanie z tymi istniejącymi technologiami podczas oceniania i przyjmowania nowszych.  
  
 Zabezpieczenia WCF integrują się z istniejącymi modelami zabezpieczeń transportu i mogą korzystać z istniejącej infrastruktury dla nowszych modeli zabezpieczeń transferów opartych na zabezpieczeniach protokołu SOAP.  
  
### <a name="integration-with-existing-authentication-models"></a>Integracja z istniejącymi modelami uwierzytelniania  
 Ważną częścią dowolnego modelu zabezpieczeń komunikacji jest możliwość identyfikowania i uwierzytelniania jednostek w komunikacji. Te jednostki w komunikacji używają "tożsamości cyfrowych" lub poświadczeń, aby uwierzytelniać się za pomocą komunikacji równorzędnej. W miarę rozwoju platform komunikacji rozproszonej zostały zaimplementowane różne uwierzytelnianie poświadczeń i powiązane modele zabezpieczeń. Na przykład w Internecie użyto nazwy użytkownika i hasła do identyfikowania użytkowników. W intranecie korzystanie z kontrolera domeny protokołu Kerberos do tworzenia kopii zapasowej uwierzytelniania użytkowników i usług staje się wspólne. W niektórych scenariuszach, takich jak między dwoma partnerami biznesowymi, certyfikaty mogą być używane do wzajemnego uwierzytelniania partnerów.  
  
 W tym celu w świecie usług sieci Web, w których ta sama usługa może być narażona na wewnętrznych klientów firmy, a także do partnerów zewnętrznych lub klientów internetowych, ważne jest, aby infrastruktura zapewniała integrację z tymi istniejącymi zabezpieczeniami modele uwierzytelniania. Zabezpieczenia WCF obsługują szeroką gamę typów poświadczeń (modele uwierzytelniania), w tym:  
  
- Anonimowy obiekt wywołujący.  
  
- Poświadczenie klienta nazwy użytkownika.  
  
- Poświadczenie klienta certyfikatu.  
  
- Windows (protokół Kerberos i serwer NT LanMan [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standardy i współdziałanie  
 W świecie z dużymi istniejącymi wdrożeniami jednorodność jest bardzo rzadki. Rozproszone platformy przetwarzania/komunikacji muszą współdziałać z ofertami różnych dostawców. Ponadto zabezpieczenia muszą być również interoperacyjne.  
  
 Aby włączyć interoperacyjne systemy zabezpieczeń, firmy aktywne w branży usług sieci Web, które utworzyły różne standardy. W odniesieniu do zabezpieczeń zaproponowano kilka istotnych standardów: WS-Security: zabezpieczenia komunikatów protokołu SOAP (zaakceptowane przez treść języka Oasis Standards i dawniej znane jako WS-Security), WS-Trust, WS-SecureConversation i WS-SecurityPolicy.  
  
 Usługa WCF obsługuje szeroką gamę scenariuszy współdziałania. Klasa <xref:System.ServiceModel.BasicHttpBinding> jest przeznaczona dla podstawowego profilu zabezpieczeń (zestawu Winsock), a Klasa <xref:System.ServiceModel.WSHttpBinding> jest przeznaczona dla najnowszych standardów zabezpieczeń, takich jak WS-Security 1,1 i WS-SecureConversation. Dzięki przestrzeganiu tych standardów zabezpieczenia WCF mogą współdziałać i integrować z usługami sieci Web, które są hostowane w systemach operacyjnych i na platformach innych niż Microsoft Windows.  
  
## <a name="wcf-security-functional-areas"></a>Obszary funkcjonalne zabezpieczeń WCF  
 Zabezpieczenia WCF są podzielone na trzy obszary funkcjonalne: zabezpieczenia transferu, kontrola dostępu i inspekcja. Poniższe sekcje krótko omawiają te obszary i zawierają linki umożliwiające więcej informacji.  
  
### <a name="transfer-security"></a>Zabezpieczenia transferu  
 Zabezpieczenia transferu obejmują trzy główne funkcje zabezpieczeń: integralność, poufność i uwierzytelnianie. *Integralność* to możliwość wykrywania, czy wiadomość została naruszona. *Poufność* jest możliwość, aby komunikat nie był czytelny przez kogoś innego niż zamierzony odbiorca; jest to realizowane za poorednictwem kryptografii. *Uwierzytelnianie* umożliwia zweryfikowanie tożsamości, której dotyczy żądanie. Razem te trzy funkcje pomagają zapewnić, że komunikaty są bezpiecznie odbierane z jednego punktu do drugiego.  
  
#### <a name="transport-and-message-security-modes"></a>Tryby zabezpieczeń transportu i komunikatów  
 Do implementowania zabezpieczeń transferu w programie WCF służą dwa podstawowe mechanizmy: tryb zabezpieczeń *transportu* i tryb zabezpieczeń *komunikatów* .  
  
- *Tryb zabezpieczeń transportu* używa protokołu na poziomie transportu, takiego jak https, aby osiągnąć zabezpieczenia transferu. W trybie transportu zaletą jest powszechnie przyjęte, dostępne na wielu platformach i mniej skomplikowane. Niemniej jednak ma wady zabezpieczania komunikatów tylko z punktu do punktu.  
  
- Z drugiej strony *tryb zabezpieczeń wiadomości*używa protokołu WS-Security (i innych specyfikacji) do implementowania zabezpieczeń transferu. Ze względu na to, że zabezpieczenia komunikatów są stosowane bezpośrednio do komunikatów protokołu SOAP i znajdują się w kopertach protokołu SOAP, wraz z danymi aplikacji, jest to zalety transportu niezależne od protokołu, bardziej rozszerzalne i zapewniające kompleksowe zabezpieczenia (w przeciwieństwie do punktów); jest to wadą kilku razy wolniej niż tryb zabezpieczeń transportu, ponieważ musi ona zajmować się charakterem XML komunikatów protokołu SOAP.  
  
 Aby uzyskać więcej informacji na temat tych różnic, zobacz [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Trzeci tryb zabezpieczeń używa powyższych trybów i oferuje zalety obu tych elementów. Ten tryb jest nazywany `TransportWithMessageCredential`. W tym trybie zabezpieczenia komunikatów są używane do uwierzytelniania klienta, a zabezpieczenia transportu są używane do uwierzytelniania serwera i zapewniania poufności i integralności komunikatów. Dzięki temu tryb zabezpieczeń `TransportWithMessageCredential` jest prawie tak szybko jak tryb zabezpieczeń transportu i zapewnia rozszerzalność uwierzytelniania klienta w taki sam sposób, jak w przypadku zabezpieczeń komunikatów. Jednak, w przeciwieństwie do trybu zabezpieczeń wiadomości, nie zapewnia pełnego zabezpieczenia kompleksowego.  
  
### <a name="access-control"></a>Kontrola dostępu  
 *Kontrola dostępu* jest również znana jako autoryzacja. *Autoryzacja* pozwala różnym użytkownikom mieć różne uprawnienia do wyświetlania danych. Na przykład, ponieważ pliki zasobów ludzkich firmy zawierają poufne dane pracownika, tylko menedżerowie mogą wyświetlać dane pracowników. Ponadto menedżerowie mogą wyświetlać tylko dane dla ich bezpośrednich raportów. W takim przypadku kontrola dostępu jest oparta na roli (kierowniku), a także w określonej tożsamości Menedżera (aby uniemożliwić jednemu z nich przeglądanie rekordów pracowników innego kierownika).  
  
 W programie WCF funkcje kontroli dostępu są udostępniane w ramach integracji z <xref:System.Security.Permissions.PrincipalPermissionAttribute> środowiska uruchomieniowego języka wspólnego (CLR) i za pomocą zestawu interfejsów API znanych jako *model tożsamości*. Aby uzyskać szczegółowe informacje na temat kontroli dostępu i autoryzacji opartej na oświadczeniach, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Inspekcja  
 *Inspekcja* to rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows. Można rejestrować zdarzenia związane z zabezpieczeniami, takie jak błędy uwierzytelniania (lub sukcesy). Aby uzyskać więcej informacji, zobacz [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Aby uzyskać szczegółowe informacje dotyczące programowania, zobacz [jak: Inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Zabezpieczanie usług](../../../../docs/framework/wcf/securing-services.md)
- [Typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
- [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Konfigurowanie usług za pomocą plików konfiguracji](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
