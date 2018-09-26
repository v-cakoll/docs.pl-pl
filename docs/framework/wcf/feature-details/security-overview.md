---
title: Overview1 zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
author: BrucePerlerMS
ms.openlocfilehash: 54cb952e2f3bffc9c37f2d75059c931d78f29eee
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088512"
---
# <a name="security-overview"></a>Przegląd zabezpieczeń
Windows Communication Foundation (WCF) jest SOAP oparta na komunikatach rozproszonej platformy programowania i zabezpieczanie komunikatów między klientami i usługami jest podstawą ochrony danych. Usługi WCF zapewnia platformę wszechstronne i interoperacyjne wymiany zabezpieczonych wiadomości na podstawie istniejącej infrastruktury zabezpieczeń i standardy zabezpieczeń rozpoznawanym komunikaty protokołu SOAP.  
  
> [!NOTE]
>  Aby uzyskać kompletny przewodnik po zabezpieczeniach WCF, zobacz [wskazówki dotyczące zabezpieczeń programu WCF](https://go.microsoft.com/fwlink/?LinkID=158912).  
  
 Pojęcia używa WCF, które są znane, jeśli skompilowałeś bezpieczne, rozproszone aplikacje z istniejącymi technologiami, taki jak HTTPS, Windows zintegrowane zabezpieczenia, lub nazwy użytkownika i hasła do uwierzytelniania użytkowników. Usługi WCF nie tylko integruje się z istniejącymi infrastrukturami zabezpieczeń, ale rozszerzają rozproszone zabezpieczeń poza domeny tylko do Windows przy użyciu zabezpieczonych wiadomości protokołu SOAP. Należy rozważyć implementację istniejących mechanizmów zabezpieczeń z głównych zalet przy użyciu protokołu SOAP, jako protokół oprócz istniejącej protokołów WCF. Na przykład poświadczenia, które identyfikują klienta lub usługi, takie jak nazwa użytkownika i hasło lub certyfikatów X.509 mieć interoperacyjne profilów opartych na języku XML protokołu SOAP. Korzystając z tych profilów, komunikaty są wymieniane bezpieczne, wykorzystując specyfikacji open, takich jak XML podpisów cyfrowych i szyfrowania XML. Aby uzyskać listę specyfikacje, zobacz [Web Services protokoły obsługiwane przez wiązania współdziałania System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Równoległe innego jest Component Object Model (COM) na platformie Windows, która umożliwia bezpieczne, rozproszonych aplikacji. COM ma mechanizm kompleksowych funkcji zabezpieczeń, zgodnie z którą mogą przepływać kontekstu zabezpieczeń między składnikami; Ten mechanizm wymusza integralności, poufności i uwierzytelniania. Jednak COM nie obsługuje dla wielu platform, bezpiecznej wymiany komunikatów, takie jak WCF jest. Przy użyciu usługi WCF, możesz tworzyć usług i klientów, które rozciągają się w domenach Windows przez Internet. Międzyoperacyjne komunikatów WCF są niezbędne do tworzenia dynamicznych, oparte na firm usług po wzięciu pod bezpieczeństwa informacji użytkownika.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation zabezpieczeń zapewnianych  
 Usługi WCF jest to rozproszona platforma programowania oparte na komunikaty protokołu SOAP. Przy użyciu usługi WCF, można utworzyć aplikacje tej funkcji jako usługi oraz obsługi klientów, tworzenia i przetwarzania komunikatów z nieograniczonej liczby innych usług i klientów. W takich aplikacji rozproszonej wiadomości może przepływać z węzła do węzła, za pośrednictwem zapory do Internetu oraz liczne pośredników SOAP. Wprowadza szereg zagrożenia bezpieczeństwa komunikatu. W poniższych przykładach pokazano niektóre typowe zagrożenia, które zabezpieczeń programu WCF można ograniczyć podczas wymiany komunikatów między obiektami:  
  
-   Obserwowanie ruchu sieciowego w celu uzyskania informacji poufnych. Na przykład w scenariuszu bankowość online, klient zażąda transferu środków z jednego konta na inny. Złośliwy użytkownik przechwytuje wiadomości, a później numer konta i hasła, wykonuje transferu środków z konta którego bezpieczeństwo zostało naruszone.  
  
-   Jednostki wydawaniem pełniący funkcję usług bez świadomości klienta. W tym scenariuszu złośliwy użytkownik (nieautoryzowany) działa jako usługa online i przechwytuje wiadomości od klienta do uzyskania informacji poufnych. Następnie nieautoryzowany używa kradzieży danych do transferu środków z konta którego bezpieczeństwo zostało naruszone. Ten rodzaj ataku jest również znane *ataku*.  
  
-   Zmiana komunikaty, aby uzyskać różne wyniki niż obiekt wywołujący przeznaczone. Na przykład zmieniając numer konta, do którego ma zostać depozytu umożliwia środków przejść do nieautoryzowanego konta.  
  
-   Odtworzenie haker, w których haker uciążliwy powoduje ponowne uruchomienie tego samego zamówienia zakupu. Na przykład księgarni online odbiera setki zamówień i wysyła książki do klienta, który nie ma ich uporządkowane.  
  
-   Niezdolność usługi do uwierzytelniania klienta. W tym przypadku usługa nie dają pewność, że odpowiednie osoby wykonywane transakcji.  
  
 Podsumowując bezpieczeństwie transferu zapewnia następujące gwarancje:  
  
-   Usługa uwierzytelniania punktu końcowego (respondenta).  
  
-   Uwierzytelnianie jednostki (Inicjator) klienta.  
  
-   Integralność wiadomości.  
  
-   Poufność komunikatów.  
  
-   Wykrywanie powtarzania.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integracja z istniejącymi infrastrukturami zabezpieczeń  
 Często wdrożeń usług internetowych dysponować istniejących rozwiązań zabezpieczeń, na przykład protokołu Secure Sockets Layer (SSL) lub protokołu Kerberos. Niektóre z zalet infrastruktura zabezpieczeń, która została już wdrożona, takich jak Windows domen usługi Active Directory. Często zachodzi zintegrować z istniejącymi technologiami, te podczas oceniania i przyjęcie nowszej z nich.  
  
 Zabezpieczenia WCF integruje się z istniejącymi zabezpieczeń transportu i mogą korzystać z istniejącej infrastruktury dla nowszej transferu zabezpieczeń modeli w oparciu o zabezpieczeniach wiadomości SOAP.  
  
### <a name="integration-with-existing-authentication-models"></a>Integracja z istniejącymi uwierzytelniania  
 Ważnym elementem każdego modelu zabezpieczeń komunikacji jest możliwość identyfikowania i uwierzytelniania jednostki w komunikacie. Tych jednostek w ramach komunikacji umożliwia "cyfrowego tożsamości" lub poświadczenia, uwierzytelniają się przy użyciu komunikujące się elementów równorzędnych. Jak ewoluował komunikacji rozproszonych platform, zostały zaimplementowane różnych poświadczeń uwierzytelniania i modeli powiązanych zabezpieczeń. Na przykład w Internecie, typowe jest użycie nazwy użytkownika i hasło do identyfikowania użytkowników. W sieci intranet Użyj protokołu Kerberos kontrolera domeny, aby utworzyć kopię zapasową usługi uwierzytelniania użytkowników i staje się wspólnej. W niektórych scenariuszach takich jak między dwoma partnerami biznesowymi, certyfikaty mogą służyć do wzajemnego uwierzytelniania, partnerów.  
  
 W związku z tym na całym świecie usług sieci Web, gdzie tej samej usługi mogą być ujawniane także co partnerom zewnętrznym wewnętrznych klientów firmowych lub klientów internetowych, ważne jest, że infrastruktura przewiduje integrację z tych istniejących zabezpieczeń modele uwierzytelniania. Zabezpieczenia WCF obsługuje wiele typów poświadczeń (modele uwierzytelniania) w tym:  
  
-   Anonimowy obiekt wywołujący.  
  
-   Poświadczenia klienta nazwy użytkownika.  
  
-   Certyfikat poświadczeń klienta.  
  
-   Windows (protokół Kerberos i LanMan NT [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standardy i współdziałanie  
 W świecie przy użyciu istniejących wdrożeń w dużych zasady jednolitości jest rzadkie. Platformy obliczeniowej/komunikacji rozproszonej muszą współpracować przy użyciu technologii, oferowanych przez różnych dostawców. Podobnie zabezpieczeń, musi być międzyoperacyjnych.  
  
 Aby włączyć systemów zabezpieczeń międzyoperacyjnych, przedsiębiorstwa działające w branży usług sieci Web zostały zredagowane różnych standardów. W szczególności dotyczące zabezpieczeń, zostały zaproponowane kilka standardów istotne: WS-Security: zabezpieczenia wiadomości SOAP (zaakceptowane przez organizację OASIS treść standardów i znana wcześniej jako usługi WS-Security), WS-Trust, WS-SecureConversation i WS-SecurityPolicy.  
  
 Usługi WCF obsługuje szeroką gamę scenariuszach współpracy. <xref:System.ServiceModel.BasicHttpBinding> Klasa jest przeznaczona na podstawowe profil zabezpieczeń (BSP) i <xref:System.ServiceModel.WSHttpBinding> klasa jest przeznaczona dla najnowszych standardów zabezpieczeń, takich jak usługi WS-Security 1.1 i WS-SecureConversation. Dzięki przestrzeganiu tych standardów, zabezpieczeniach WCF można współpracować i integracja z usługami sieci Web, obsługiwanych systemów operacyjnych i platform innych niż Microsoft Windows.  
  
## <a name="wcf-security-functional-areas"></a>Obszarów funkcjonalnych zabezpieczeń programu WCF  
 Zabezpieczenia WCF dzieli się na trzy obszary funkcjonalne: transfer zabezpieczeń, kontroli dostępu i inspekcji. W poniższych sekcjach krótko omówiono tych obszarów i zawierają łącza, aby uzyskać więcej informacji.  
  
### <a name="transfer-security"></a>Przeniesienie zabezpieczeń  
 Przeniesienie zabezpieczeń obejmuje trzech głównych funkcji zabezpieczeń: integralności, poufności i uwierzytelniania. *Integralność* jest możliwość wykrywania, czy wiadomość została naruszona. *Poufność* jest możliwość przechowywania wiadomości nie można go odczytać przez nikogo innego niż zamierzony recipient; jest to realizowane poprzez kryptografii. *Uwierzytelnianie* jest możliwość weryfikowania tożsamości. Razem te trzy funkcje ułatwiają upewnij się, że bezpieczne nadejścia z jednego miejsca do drugiego.  
  
#### <a name="transport-and-message-security-modes"></a>Transport i tryby zabezpieczeń komunikatów  
 Dwa główne mechanizmy są używane do implementowania bezpieczeństwie transferu programu WCF: *transportu* trybu zabezpieczeń i *komunikat* tryb zabezpieczeń.  
  
-   *Tryb zabezpieczeń Transport* korzysta protokół poziomu transportu, taki jak HTTPS, aby osiągnąć bezpieczeństwie transferu. Tryb transportu zaletą jest szeroko stosowanych, dostępna na wielu platformach i mniejsze wymagania złożonego. Ma jednak wadą Zabezpieczanie komunikatów tylko z typu punkt-punkt.  
  
-   *Tryb zabezpieczeń wiadomości*, a na drugiej strony, używa WS-Security (i inne specyfikacje) Aby zaimplementować zabezpieczenia transferu. Ponieważ zabezpieczeń wiadomości jest stosowane bezpośrednio do komunikaty protokołu SOAP i znajduje się wewnątrz koperty protokołu SOAP, wraz z danymi aplikacji ma prowadzoną zabezpieczeń transportu niezależne od protokołu, bardziej rozszerzalny i zapewnianie end-to-end (w przeciwieństwie do point-to-point); ma ona wadą jest kilka razy wolniej niż tryb zabezpieczeń transport, ponieważ ma ona do czynienia z charakterem XML protokołu SOAP wiadomości.  
  
 Aby uzyskać więcej informacji dotyczących tych różnic, zobacz [zabezpieczania usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Trzeci tryb zabezpieczeń używa oba tryby poprzedniej i oferuje zalety obu tych elementów. Ten tryb jest nazywany `TransportWithMessageCredential`. W tym trybie Zabezpieczenia wiadomości jest używany do uwierzytelniania klienta i zabezpieczeń transportu jest używany do uwierzytelniania serwera i zapewnić poufność komunikatów i integralność. Dzięki tym `TransportWithMessageCredential` trybu zabezpieczeń jest prawie tak szybko, jak tryb zabezpieczeń transport i zapewnia rozszerzalność uwierzytelniania klienta w taki sam sposób, jak zabezpieczenia wiadomości. Jednak w przeciwieństwie do trybu zabezpieczenia wiadomości, zapewnia ona pełnymi zabezpieczeniami end-to-end.  
  
### <a name="access-control"></a>Kontrola dostępu  
 *Kontrola dostępu* jest także znana jako autoryzacji. *Autoryzacja* umożliwia różnych użytkowników może mieć różne uprawnienia do wyświetlania danych. Na przykład ponieważ pliki zarządzania zasobami ludzkimi firmy zawierają dane poufne pracowników, tylko menedżerowie mogą wyświetlać dane pracowników. Ponadto menedżerowie mogą wyświetlać tylko dane dla swoich raportów bezpośrednio. W tym przypadku kontroli dostępu zależy zarówno roli ("menedżerem"), jak i określone tożsamość menedżera (Aby zapobiec jednego z kierowników sprawę patrząc na innego menedżera rekordy pracowników).  
  
 W programie WCF, funkcje kontroli dostępu są dostępne za pośrednictwem integracja plików wykonywalnych języka wspólnego (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> i za pomocą zestawu interfejsów API, znane jako *modelu tożsamości*. Aby uzyskać szczegółowe informacje o kontroli dostępu i autoryzacja oparta na oświadczeniach, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Inspekcja  
 *Inspekcja* jest rejestrowanie zdarzeń związanych z zabezpieczeniami w dzienniku zdarzeń Windows. Umożliwia rejestrowanie zdarzeń związanych z zabezpieczeniami, takie jak błędy uwierzytelniania (lub sukcesów). Aby uzyskać więcej informacji, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Programowania szczegółowe informacje, zobacz [instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Zabezpieczanie usług](../../../../docs/framework/wcf/securing-services.md)  
 [Typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 [Konfigurowanie usług za pomocą plików konfiguracji](../../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
