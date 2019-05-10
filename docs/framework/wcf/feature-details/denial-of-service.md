---
title: Odmowa usługi
ms.date: 03/30/2017
helpviewer_keywords:
- denial of service [WCF]
ms.assetid: dfb150f3-d598-4697-a5e6-6779e4f9b600
ms.openlocfilehash: 426429eefd038008340a956ab3fa3cba21906c84
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627022"
---
# <a name="denial-of-service"></a>Odmowa usługi
Odmowa usługi występuje, gdy system jest przeciążony w taki sposób, że nie można przetworzyć wiadomości lub są przetwarzane bardzo wolno.  
  
## <a name="excess-memory-consumption"></a>Użycie nadmierną ilość pamięci  
 Problem może wystąpić, gdy wczytywanie dokumentu XML z dużą liczbą unikatowych nazw lokalnych, przestrzenie nazw i prefiksy. Jeśli używasz klasy, która pochodzi od klasy <xref:System.Xml.XmlReader>, można wywołać <xref:System.Xml.XmlReader.LocalName%2A>, <xref:System.Xml.XmlReader.Prefix%2A> lub <xref:System.Xml.XmlReader.NamespaceURI%2A> właściwości dla każdego elementu zwróconym ciągu zostanie dodany do <xref:System.Xml.NameTable>. Kolekcja posiadaniu <xref:System.Xml.NameTable> nigdy nie zmniejsza rozmiar, tworzenia wirtualnej "przeciek pamięci" uchwytów ciągu.  
  
 Środki zaradcze obejmują:  
  
- Pochodzi od <xref:System.Xml.NameTable> klasy i wymuszanie przydziałów maksymalny rozmiar. (Nie może uniemożliwić korzystanie z <xref:System.Xml.NameTable> lub przełączyć <xref:System.Xml.NameTable> gdy jest pełny.)  
  
- Unikaj używania właściwości wymienionych — zamiast tego użyj <xref:System.Xml.XmlReader.MoveToAttribute%2A> metody z <xref:System.Xml.XmlReader.IsStartElement%2A> metody w miarę możliwości; tych metod nie zwracać ciągi i dlatego uniknąć problemu przepełnienie <xref:System.Xml.NameTable> kolekcji.  
  
## <a name="malicious-client-sends-excessive-license-requests-to-service"></a>Złośliwy klient wysyła żądania nadmierne licencji usługi  
 Złośliwego klienta bombards usługi za pomocą żądania nadmierne licencji, może spowodować serwer do użycia zbyt dużej ilości pamięci.  
  
 Środki zaradcze: Użyj następujących właściwości <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy:  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxCachedCookies%2A>: Określa maksymalną liczbę ograniczone czasowo `SecurityContextToken`s, który serwer buforuje po `SPNego` lub `SSL` negocjacji.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.IssuedCookieLifetime%2A>: Określa okres istnienia `SecurityContextTokens` , problemy z serwera następujące `SPNego` lub `SSL` negocjacji. Pamięci podręczne serwera `SecurityContextToken`s, w tym okresie czasu.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxPendingSessions%2A>: Określa maksymalną liczbę bezpiecznych konwersacji, które są ustalane na serwerze, ale żadne komunikaty aplikacji przetworzonych. Ten limit przydziału uniemożliwia klientom po ustanawianie bezpiecznej konwersacji na usługę, co powoduje usługi do zarządzania stanem na klienta, ale nigdy z nich korzystać.  
  
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.InactivityTimeout%2A>: Określa maksymalny czas, usługa utrzymuje bezpiecznej konwersacji aktywność bez otrzymania komunikatu aplikacji od klienta na potrzeby konwersacji. Ten limit przydziału uniemożliwia klientom po ustanawianie bezpiecznej konwersacji na usługę, co powoduje usługi do zarządzania stanem na klienta, ale nigdy z nich korzystać.  
  
## <a name="wsdualhttpbinding-or-dual-custom-bindings-require-client-authentication"></a>WSDualHttpBinding lub podwójne powiązań niestandardowych wymagają uwierzytelniania klienta  
 Domyślnie <xref:System.ServiceModel.WSDualHttpBinding> ma włączoną obsługą zabezpieczeń. Możliwe jest, że jeśli uwierzytelnianie klienta jest jednak wyłączona przez ustawienie <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwości <xref:System.ServiceModel.MessageCredentialType.None>, złośliwy użytkownik może spowodować "odmowa usługi" w usłudze trzeci. Taka sytuacja może wystąpić, ponieważ złośliwego klienta można kierować usługi by wysłać strumień komunikatów do innych usług.  
  
 Aby temu zaradzić, nie należy ustawiać właściwości na `None`. Również należy pamiętać o tej możliwości podczas tworzenia niestandardowego powiązania, który ma wzorca dwóch komunikatów.  
  
## <a name="auditing-event-log-can-be-filled"></a>Dziennik zdarzeń inspekcji mogą być wypełnione  
 Jeśli złośliwy użytkownik rozumie, że inspekcja jest włączona, że atakujący może wysłać nieprawidłowe komunikaty, które powodują wpisy inspekcji są zapisywane. Jeśli wprowadzono w dzienniku inspekcji w ten sposób, inspekcji systemu nie powiedzie się.  
  
 Aby rozwiązać ten problem, należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwość `true` i używać właściwości podglądu zdarzeń w celu sterowania zachowaniem inspekcji. Aby uzyskać więcej informacji na temat wyświetlania i zarządzania dziennikami zdarzeń za pomocą Podglądu zdarzeń, zobacz [Podgląd zdarzeń](https://go.microsoft.com/fwlink/?LinkId=186123). Aby uzyskać więcej informacji, zobacz [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="invalid-implementations-of-iauthorizationpolicy-can-cause-service-hangs"></a>Nieprawidłowy implementacje zawiesza się usługi Przyczyna może IAuthorizationPolicy  
 Wywoływanie <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> metodę, uszkodzony wykonania <xref:System.IdentityModel.Policy.IAuthorizationPolicy> interfejs może spowodować, że usługa zawiesi się.  
  
 Środki zaradcze: Użyj tylko przez zaufany kod. Oznacza to, należy użyć tylko kod, który został zapisany i przetestowane, lub który pochodzi z zaufanego dostawcę. Nie zezwalaj na niezaufane rozszerzenia <xref:System.IdentityModel.Policy.IAuthorizationPolicy> być podłączony do kodu bez ukończenia brany pod uwagę. Dotyczy to wszystkich rozszerzeń używanych w implementacji usługi. Usługi WCF nie powoduje żadnych rozróżnienia między kodu aplikacji i obce kod, który jest podłączony przy użyciu punkty rozszerzeń.  
  
## <a name="kerberos-maximum-token-size-may-need-resizing"></a>Rozmiar tokenu maksymalny protokołu Kerberos może być konieczne zmiany rozmiaru  
 Jeśli klient należy do wielu grup (około 900, mimo że rzeczywista liczba różni się zależnie od grup), problem może wystąpić, gdy blok nagłówka komunikatu przekracza 64 kilobajtów. W takim przypadku można zwiększyć maksymalny rozmiar tokenu protokołu Kerberos, zgodnie z opisem w artykule firmy Microsoft Support "[uwierzytelniania protokołu Kerberos programu Internet Explorer zakończy się niepowodzeniem ze względu na niewystarczający bufor, nawiązywanie połączeń z usług IIS](https://go.microsoft.com/fwlink/?LinkId=89176)." Konieczne może również zwiększyć maksymalny rozmiar wiadomości WCF do obsługi większych tokenu protokołu Kerberos.  
  
## <a name="autoenrollment-results-in-multiple-certificates-with-same-subject-name-for-machine"></a>Wyniki automatycznej rejestracji w wielu certyfikatów o takiej samej nazwie podmiotu dla maszyny  
 *Autorejestrowania* to możliwość [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] można automatycznie zarejestrować użytkowników i komputerów pod kątem certyfikatów. Gdy komputer znajduje się w domenie z włączoną funkcją, certyfikat X.509 z przeznaczeniem uwierzytelniania klienta jest automatycznie tworzony i wstawiony w magazynie certyfikatów osobistych komputera lokalnego, zawsze wtedy, gdy nowy komputer jest dołączony do sieć. Jednak autorejestrowania używa tej samej nazwie podmiotu dla wszystkich certyfikatów, które tworzy się w pamięci podręcznej.  
  
 Wpływ jest, czy może zakończyć się niepowodzeniem usług WCF można otworzyć w domenach z automatycznej rejestracji. Dzieje się tak, ponieważ domyślne kryteria wyszukiwania poświadczeń X.509 usługi mogą być niejednoznaczne, ponieważ istnieje wiele certyfikatów z w pełni kwalifikowanej nazwy systemu nazw domen (DNS, Domain Name System) komputera. Jeden certyfikat pochodzi autorejestrowania; druga może być certyfikat wystawiony samodzielnie.  
  
 Aby rozwiązać ten problem, należy odwoływać się do dokładnie certyfikatu do użycia przy użyciu bardziej precyzyjne kryterium wyszukiwania na [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md). Na przykład użyć <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> opcji, a następnie określ certyfikat przez jego unikatowy odcisk palca (skrót).  
  
 Aby uzyskać więcej informacji na temat funkcji automatycznej rejestracji zobacz [autorejestrowanie certyfikatów w systemie Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=95166).  
  
## <a name="last-of-multiple-alternative-subject-names-used-for-authorization"></a>Ostatni wielu nazwy alternatywnej podmiotu używane na potrzeby autoryzacji  
 W rzadkich przypadkach, kiedy certyfikat X.509 zawiera wiele nazwy alternatywnej podmiotu i autoryzacji, za pomocą alternatywnej nazwy podmiotu, autoryzacja może zakończyć się niepowodzeniem.  
  
## <a name="protect-configuration-files-with-acls"></a>Ochrona plików konfiguracji przy użyciu list kontroli dostępu  
 Można określić wymaganych i opcjonalnych oświadczeń w kod i pliki konfiguracyjne dla [!INCLUDE[infocard](../../../../includes/infocard-md.md)] wystawionych tokenów. Skutkuje to odpowiednie elementy, które są emitowane w `RequestSecurityToken` wiadomości, które są wysyłane do zabezpieczenia tokenu usługi. Osoba atakująca można modyfikować kodu lub konfiguracji, aby usunąć wymaganego lub opcjonalnego roszczenia, potencjalnie wprowadzenie usługę tokenu zabezpieczającego, aby wystawić tokenu, który nie zezwala na dostęp do usługi docelowej.  
  
 Aby uniknąć: Wymaga dostępu do komputera, zmodyfikuj plik konfiguracji. Użyj kontroli dostępu do pliku listy (kontroli dostępu ACL) do zabezpieczenia plików konfiguracyjnych. Usługi WCF wymaga kodu w katalogu aplikacji lub w globalnej pamięci podręcznej zanim umożliwi taki kod, aby go załadować z konfiguracji. Użyj listy ACL katalogu, aby zabezpieczyć katalogi.  
  
## <a name="maximum-number-of-secure-sessions-for-a-service-is-reached"></a>Osiągnięto maksymalną liczbę bezpiecznej sesji dla usługi  
 Jeśli klient został pomyślnie uwierzytelniony przez usługę bezpiecznego ustanowiono połączenie z usługą, Usługa przechowuje informacje o sesji, dopóki klient go anuluje lub ważności sesji. Każdy ustanowienie sesji zmniejsza limit maksymalnej liczby aktywnych sesji jednoczesnych, za pomocą usługi. Po osiągnięciu tego limitu klientów, które próbują utworzyć nową sesję przy użyciu tej usługi są odrzucane, dopóki jedna lub więcej aktywne sesje wygaśnie lub zostanie anulowane przez klienta. Klient może mieć wiele sesji przy użyciu usługi, a limit liczony w każdej z nich tymi sesjami.  
  
> [!NOTE]
>  Gdy używasz stanowych sesji, nie ma zastosowania poprzednim akapicie. Aby uzyskać więcej informacji o sesjach stanowe, zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
 Aby rozwiązać ten problem, należy ustawić, ustawiając limit maksymalnej liczby aktywnych sesji, a maksymalny okres istnienia sesji <xref:System.ServiceModel.Channels.SecurityBindingElement> właściwość <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
