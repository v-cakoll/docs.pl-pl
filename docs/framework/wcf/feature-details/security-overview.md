---
title: Overview1 zabezpieczeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, security
- WCF, security
ms.assetid: f478c80d-792d-4e7a-96bd-a2ff0b6f65f9
caps.latest.revision: 37
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: a50b3d3ec2a99d53bc7d5817f3ed530ef92d474b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="security-overview"></a>Przegląd zabezpieczeń
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to SOAP oparta na komunikatach rozproszonej programowania platforma i zabezpieczanie komunikatów między klientami i usługami jest niezbędne do ochrony danych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia elastyczne i interoperacyjne platformę wymiany zabezpieczonych wiadomości na podstawie zarówno istniejącej infrastruktury zabezpieczeń i standardów zabezpieczeń rozpoznanym wiadomości protokołu SOAP.  
  
> [!NOTE]
>  Aby uzyskać kompletny przewodnik zabezpieczeń programu WCF, zobacz [wskazówki dotyczące zabezpieczeń WCF](http://go.microsoft.com/fwlink/?LinkID=158912).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pojęcia zastosowań, które są znane, jeśli utworzono bezpieczny, rozproszonych aplikacji z istniejących technologii, takich jak HTTPS, Windows zintegrowanych zabezpieczeń, lub nazwy użytkownika i hasła w celu uwierzytelniania użytkowników. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie tylko integruje się z istniejącą infrastrukturą zabezpieczeń, ale rozszerzają zabezpieczeń rozproszonych poza domeny tylko do systemu Windows przy użyciu bezpiecznych wiadomości protokołu SOAP. Należy wziąć pod uwagę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementację istniejące mechanizmy zabezpieczeń z głównych zaletą używania SOAP jako protokół oprócz istniejących protokołów. Na przykład poświadczenia, które identyfikują klienta lub usługi, takie jak nazwa użytkownika i hasło lub certyfikatów X.509 ma interoperacyjne profilów opartych na języku XML protokołu SOAP. Przy użyciu tych profilów, komunikaty są wymieniane bezpiecznego, korzystając z otwartych specyfikacji, takich jak podpisy cyfrowe XML i szyfrowanie XML. Lista specyfikacji, zobacz [sieci Web usług protokoły obsługiwane przez wiązania współdziałania System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
 Równoległe innego jest składnik modelu COM (Object) na platformie systemu Windows, która umożliwia bezpieczne, rozproszonych aplikacji. COM ma mechanizm kompleksowe zabezpieczeń, zgodnie z którymi mogą przepływać kontekstu zabezpieczeń między składnikami; Ten mechanizm wymusza integralności, poufność i uwierzytelnianie. Jednak COM nie obsługuje wielu platform, zabezpieczenia wiadomości, takie jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest. Przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], można utworzyć usług i klientów, obejmujące z domen systemu Windows przez Internet. Współdziałanie komunikatów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są niezbędne dla usługi dynamicznej, business opartych na kompilowanie ułatwiające po wzięciu pod bezpieczeństwa informacji użytkownika.  
  
## <a name="windows-communication-foundation-security-benefits"></a>Windows Communication Foundation zabezpieczeń korzyści  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozproszone platformy programowania opiera się na wiadomości SOAP. Przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], można tworzyć aplikacje tej funkcji jako usług i klientów usługi, tworzenia i przetwarzania komunikatów z nieograniczoną liczbę innych usług i klientów. W takich aplikacji rozproszonej wiadomości mogą przepływać z węzła do węzła, za pośrednictwem zapór do Internetu i za pośrednictwem pośredników SOAP wiele. Powstaje różnych zagrożeń bezpieczeństwa komunikatu. Poniższe przykłady przedstawiają niektóre typowe zagrożenia, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń mogą pomóc ograniczyć przypadki podczas wymiany wiadomości między jednostkami:  
  
-   Obserwacji ruchu sieciowego w celu uzyskania informacji poufnych. Na przykład w scenariuszu banku online, klient żąda transferu funduszy z jednego konta do innego. Złośliwy użytkownik przechwytuje wiadomości i o numer konta i hasło, później przeprowadza transferu funduszy z zagrożone konto.  
  
-   Jednostki nieautoryzowanymi działający jako usługi bez pogłębianie wiedzy na temat klienta. W tym scenariuszu złośliwy użytkownik (nieautoryzowanych) działa jako usługa online i przechwytuje wiadomości z klienta do uzyskania informacji poufnych. Następnie nieautoryzowanego używa kradzieży danych do transferowania funduszy z konta, którego bezpieczeństwo zostało naruszone. Takiego ataku jest również znany *ataku phishing*.  
  
-   Zmiana komunikaty, aby uzyskać różne wyniki niż obiekt wywołujący przeznaczone. Na przykład zmieniając numer konta, do której dokonywane jest depozytu umożliwia funduszy przejść do kont nieautoryzowanych.  
  
-   Odtworzenie hakerom, w których haker niedogodności odtwarzaniem takiej samej kolejności zakupu. Na przykład księgarni odbiera setki zleceń i wysyła do klienta, który nie ma ich uporządkowane podręcznikach.  
  
-   Niezdolność usługi do uwierzytelniania klienta. W takim przypadku usługa nie może zapewnić osobą wykonanie transakcji.  
  
 Podsumowując transfer zabezpieczeń zawiera następujące warunki:  
  
-   Usługa uwierzytelniania punktu końcowego (respondenta).  
  
-   Uwierzytelnienia (inicjatora) podmiotu zabezpieczeń klienta.  
  
-   Integralność wiadomości.  
  
-   Poufność wiadomości.  
  
-   Wykrywania powtarzania.  
  
### <a name="integration-with-existing-security-infrastructures"></a>Integracja z istniejącą infrastrukturą zabezpieczeń  
 Często wdrożenia usługi sieci Web mają istniejących rozwiązań zabezpieczeń w miejscu, na przykład protokołu Secure Sockets Layer (SSL) lub protokołu Kerberos. Niektóre korzystać z infrastruktury zabezpieczeń, która została już wdrożona, takich jak domen systemu Windows przy użyciu usługi Active Directory. Często jest niezbędne do integracji z tych technologii istniejących podczas obliczania i przyjęcie te nowsze.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczenia integruje się z istniejącymi zabezpieczeń transportu i wykorzystanie istniejącej infrastruktury dla nowszej modeli zabezpieczeń transfer oparte na zabezpieczenia wiadomości protokołu SOAP.  
  
### <a name="integration-with-existing-authentication-models"></a>Integracja z istniejącymi uwierzytelniania  
 Ważnym elementem modelu zabezpieczeń wszystkie komunikacji jest możliwość identyfikację i uwierzytelnienie jednostki w komunikacie. Te jednostki w komunikacie Użyj "tożsamości cyfrowych" lub poświadczeń uwierzytelnienia komunikacji elementów równorzędnych. Jak ewoluował komunikacji rozproszonej platformy, zostało wdrożonych różnych poświadczeń uwierzytelniania i modele dotyczące zabezpieczeń. Na przykład w Internecie, użycie nazwy użytkownika i hasło, aby zidentyfikować użytkowników jest wspólnej. W sieci intranet Użyj kontrolera domeny Kerberos, aby utworzyć kopię zapasową usługi uwierzytelniania użytkowników i staje się coraz powszechne. W pewnych sytuacjach takich jak między dwoma partnerami biznesowymi, certyfikaty może być używany do wzajemnego uwierzytelniania partnerów.  
  
 W związku z tym w świecie usługi sieci Web, gdzie tej samej usługi mogą być ujawniane także dotyczące partnerami zewnętrznymi wewnętrznych klientów firmy lub klientów internetowych, ważne jest, że infrastruktura przewiduje integracji z tych zabezpieczeń istniejących modele uwierzytelniania. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczenia obsługują szeroką gamę typów poświadczeń (modele uwierzytelniania) w tym:  
  
-   Anonimowy obiekt wywołujący.  
  
-   Poświadczenie klienta nazwy użytkownika.  
  
-   Certyfikat poświadczeń klienta.  
  
-   Systemu Windows (protokołu Kerberos i LanMan NT [NTLM]).  
  
### <a name="standards-and-interoperability"></a>Standardy i współdziałanie  
 W świecie przy dużych wdrożeniach istniejących jednolitości jest rzadko. Platformach obliczeniowych/komunikacji rozproszonej muszą współpracować z technologii, które oferują różnych dostawców. Podobnie zabezpieczeń należy również interoperacyjne.  
  
 Aby włączyć współdziałanie zabezpieczeń systemów, przedsiębiorstwa działające w branży usług sieci Web utworzone przez użytkownika różnych standardów. W szczególności dotyczących zabezpieczeń, kilka istotnych standardów zostały proponowane: WS-Security: zabezpieczenia komunikatów SOAP (zaakceptowane przez jednostkę standardów języka OASIS i znanego wcześniej jako WS-Security), WS-Trust, WS-SecureConversation i WS-SecurityPolicy.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje wiele scenariuszy współdziałania. <xref:System.ServiceModel.BasicHttpBinding> Klasy jest przeznaczona na podstawowych zabezpieczeń profilu (podstawowego dostawcy) i <xref:System.ServiceModel.WSHttpBinding> najnowszych standardów zabezpieczeń, takich jak WS-Security 1.1 i WS-SecureConversation celem klasy. Przez przestrzegać tych standardów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń można współdziałanie i integracja z usługami sieci Web, obsługiwanych systemów operacyjnych i platform innych niż Microsoft Windows.  
  
## <a name="wcf-security-functional-areas"></a>Obszarów funkcjonalnych zabezpieczeń WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń jest podzielone na trzy obszarów funkcjonalnych: transfer zabezpieczeń, kontroli dostępu i inspekcji. Krótko w poniższych sekcjach omówiono konfigurowanie tych obszarów i udostępniają linki, aby uzyskać więcej informacji.  
  
### <a name="transfer-security"></a>Transfer zabezpieczeń  
 Transfer zabezpieczeń obejmuje trzech głównych funkcji zabezpieczeń: integralności, poufność i uwierzytelnianie. *Integralność* jest możliwość wykrywania, czy wiadomość została naruszona. *Poufność* jest możliwość przechowywania wiadomości niemożliwe do odczytania przez nikt inny oprócz adresata; jest to osiągane przez kryptografii. *Uwierzytelnianie* jest możliwość weryfikowania tożsamości. Te trzy funkcje ułatwiają ze sobą, upewnij się, że wiadomości bezpiecznie dostarczone z jednego miejsca do innego.  
  
#### <a name="transport-and-message-security-modes"></a>Tryby zabezpieczeń komunikatu i transportu  
 Dwa główne mechanizmy są używane do implementowania zabezpieczeń transfer w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: *transportu* trybu zabezpieczeń i *komunikat* tryb zabezpieczeń.  
  
-   *Tryb zabezpieczeń Transport* wykorzystuje protokół poziomu transportu, taki jak HTTPS, umożliwia transfer zabezpieczeń. Zaletą powszechnie przyjęta, dostępna na wielu platformach i mniejsze wymagania złożonych jest trybu transportu. Ma jednak wadą Zabezpieczanie komunikatów tylko z point-to-point.  
  
-   *Tryb zabezpieczeń wiadomości*, inne strony, używa WS-Security (i inne specyfikacje) do zaimplementowania transfer zabezpieczeń. Ponieważ zabezpieczenia wiadomości są stosowane bezpośrednio do komunikatów SOAP i znajduje się wewnątrz koperty protokołu SOAP, oraz dane aplikacji ma prowadzoną zabezpieczeń na trasie niezależne od protokołu extensible więcej i zapewnienie transportu (w przeciwieństwie do point-to-point); ma ona wadą jest kilka razy mniejsza niż tryb zabezpieczeń transport, ponieważ ma ona radzenia sobie z natury XML wiadomości SOAP.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] te różnice, zobacz [zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).  
  
 Trzeci trybu zabezpieczeń używa oba tryby poprzedniej i oferuje zalety obu. Ten tryb jest nazywany `TransportWithMessageCredential`. W tym trybie Zabezpieczenia wiadomości jest używany do uwierzytelniania klienta i zabezpieczeń transportu jest używany do uwierzytelniania serwera i zagwarantować poufność komunikatów i integralność. Dzięki temu `TransportWithMessageCredential` trybu zabezpieczeń jest niemal tak szybko, jak tryb zabezpieczeń transport i udostępnia rozszerzalności uwierzytelniania klienta w taki sam sposób jak zabezpieczenia wiadomości. Jednak w przeciwieństwie do trybu zabezpieczenia wiadomości, nie zapewnia ona pełną zabezpieczeń na trasie.  
  
### <a name="access-control"></a>Kontrola dostępu  
 *Kontrola dostępu* jest także znana jako autoryzacji. *Autoryzacji* umożliwia użytkownikom różnych mają różne uprawnienia do wyświetlania danych. Na przykład, ponieważ pliki zasobów ludzkich firmy zawierają dane poufne pracownika, tylko menedżerowie mogą wyświetlać dane pracownika. Ponadto menedżerowie mogą wyświetlać tylko dane dla swoich bezpośrednich podwładnych. W takim przypadku kontroli dostępu jest oparty na zarówno roli ("menedżerem"), a także określonych tożsamości menedżera (Aby zapobiec jednego menedżera z spojrzenie na pracownikach innego menedżera).  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], funkcje kontroli dostępu są dostarczane dzięki integracji z środowisko uruchomieniowe języka wspólnego (CLR) <xref:System.Security.Permissions.PrincipalPermissionAttribute> i za pomocą zestawu interfejsów API, znany jako *modelu tożsamości*. Aby uzyskać szczegółowe informacje o kontroli dostępu i autoryzacja oparte na oświadczeniach, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md).  
  
### <a name="auditing"></a>Inspekcja  
 *Inspekcja* jest rejestrowanie zdarzeń zabezpieczeń w dzienniku zdarzeń systemu Windows. Może rejestrować zdarzeń związanych z zabezpieczeniami, takich jak błędy uwierzytelniania (czy sukcesów). Aby uzyskać więcej informacji, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md). Dla programowania uzyskać więcej informacji, zobacz [porady: zdarzenia inspekcji zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
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
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
