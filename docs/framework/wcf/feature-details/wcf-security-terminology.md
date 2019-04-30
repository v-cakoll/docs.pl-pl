---
title: Terminologia dotycząca zabezpieczeń programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
ms.openlocfilehash: f0d5ecccdd48da2799e3299406f219a10f47e84d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768618"
---
# <a name="wcf-security-terminology"></a>Terminologia dotycząca zabezpieczeń programu WCF
Niektóre z terminologią używaną podczas omawiania zabezpieczeń mogą być nieznane. Ten temat zawiera krótkie objaśnienia niektóre pojęcia dotyczące zabezpieczeń, ale nie mają na celu dostarczenie pełną dokumentację dla każdego elementu.  
  
 Aby uzyskać więcej informacji na temat pojęć używanych w dokumentacji usług Windows Communication Foundation (WCF), zobacz [podstawowe pojęcia programu Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 listy kontroli dostępu (ACL)  
 Lista zabezpieczenia mają zastosowanie do obiektu. (Obiekt może być plik, proces, zdarzenia lub wszystko inne potrzeby deskryptora zabezpieczeń). Wpis na liście ACL jest wpisu kontroli dostępu (ACE). Istnieją dwa typy list kontroli dostępu: poufne i systemu.  
  
 uwierzytelnianie  
 Proces sprawdzania, czy użytkownika, komputera, usługi lub procesu jest tym, za co się podaje.  
  
 autoryzacja  
 Czynność kontroli dostępu i uprawnień do zasobu. Na przykład umożliwiając użytkownikom jednej grupy do odczytu pliku, ale dzięki czemu tylko elementów członkowskich innej grupy, aby zmienić plik.  
  
 certyfikat urzędu certyfikacji  
 Identyfikuje urzędu certyfikacji, który wystawia certyfikaty uwierzytelniania serwera i klienta do serwerów i klientów, którzy żądać tych certyfikatów. Ponieważ zawiera klucz publiczny używany w podpisach cyfrowych, ona też nazywa się *certyfikat podpisu*. Jeśli urząd certyfikacji jest urzędem głównym, certyfikat urzędu certyfikacji może być określone jako *certyfikat główny*. Czasami nazywane *certyfikatu witryny*.  
  
 Hierarchii urzędów certyfikacji  
 Hierarchii urzędów certyfikacji zawiera wiele urzędów certyfikacji. Jest zorganizowany tak, aby każdego urzędu certyfikacji jest certyfikowany przez inny urząd certyfikacji w wyższym poziomie hierarchii do góry hierarchii, znany także jako *główny urząd*, zostanie osiągnięty.  
  
 certificate  
 Cyfrowo podpisaną deklaracją, który zawiera informacje o jednostce i klucz publiczny podmiotu, w związku z tym razem powiązanie tych dwóch rodzajów informacji. Certyfikat jest wystawiony przez zaufany urząd organizacji (lub jednostek) o nazwie to program certyfikacji, po urzędowi wykryła, że jednostka jest tożsamości jest.  
  
 Certyfikaty mogą zawierać różne typy danych. Na przykład certyfikat X.509 zawiera formatu certyfikatu, numer seryjny certyfikatu, a algorytm użyty do podpisania certyfikatu, nazwa urzędu certyfikacji, który wystawił certyfikat, nazwa i klucz publiczny podmiotu żądanie certyfikatu i podpisu urzędu certyfikacji.  
  
 Magazyn certyfikatów  
 Zazwyczaj są przechowywane magazynie trwałym, w którym certyfikaty, certyfikat list odwołania (CRL), a listy zaufania certyfikatów (CTL). Jest to możliwe, jednak, aby utworzyć i otworzyć magazynu certyfikatów wyłącznie w pamięci podczas pracy z certyfikatami, które nie powinny być umieszczane w magazynie trwałym.  
  
 oświadczenia  
 Informacje przekazywane z jednej jednostki do innej używane do ustalenia tożsamości nadawcy. Na przykład nazwę użytkownika i token hasła lub certyfikatu X.509.  
  
 certyfikat klienta  
 Odnosi się do certyfikatu używany do uwierzytelniania klientów, na przykład podczas uwierzytelniania w przeglądarce sieci Web na serwerze sieci Web. Gdy klient przeglądarki sieci Web próbuje uzyskać dostęp do zabezpieczonej serwera sieci Web, klient wysyła swojego certyfikatu do serwera, aby umożliwić go w celu zweryfikowania tożsamości klienta.  
  
 Poświadczenia  
 Dane logowania, które używa podmiotu zabezpieczeń w celu ustanowienia jego tożsamość, takie jak hasła lub biletu protokołu Kerberos został poprzednio uwierzytelniony. Poświadczenia są używane do kontrolowania dostępu do zasobów.  
  
 Wytrawiony danych  
 Typ zawartości danych zdefiniowane przez klucza kryptograficznego publiczny standard (PKCS) #7 składający się z dowolnego typu danych, a także skrót wiadomości (podsumowanie) zawartości.  
  
 Podpis cyfrowy  
 Dane, które wiąże tożsamość nadawcy informacje są wysyłane. Podpis cyfrowy może być powiązany z dowolnej wiadomości, plik lub innymi informacjami lub przekazywane oddzielnie. Podpisy cyfrowe są używane w środowiskach publicznych kluczy i świadczenia usług uwierzytelniania i integralności.  
  
 encoding  
 Proces Przekształcanie danych w strumieniu usługi bits. Kodowanie jest częścią procesu serializacji, który konwertuje dane do strumienia z nich i zera.  
  
 pary kluczy do programu Exchange  
 Parą kluczy publiczny/prywatny używany do szyfrowania kluczy sesji, tak aby można je bezpiecznie przechowywane i wymiany z innymi użytkownikami.  
  
 hash  
 Wartość numeryczna stałym rozmiarze uzyskany przez zastosowanie funkcji matematycznych (patrz algorytmem wyznaczania wartości skrótu) do dowolnej ilości danych. Dane obejmują zazwyczaj danych losowych, znane jako *jednorazowego*. Usługa i klient współtworzyć poprawni exchange spowodują wzrost złożoności wyniku. Wynik jest również nazywany *skrót wiadomości*. Wysyłanie wartość skrótu jest bezpieczniejszy niż wysyłanie poufnych danych, takich jak hasła, nawet, jeśli hasło jest szyfrowane. Skrót nadawcy i odbiorcy należy uzgodnić algorytmu wyznaczania wartości skrótu i poprawni tak, aby po otrzymaniu, można sprawdzić skrótu.  
  
 Algorytm wyznaczania wartości skrótu  
 Algorytm używany do uzyskiwania wartości mieszania danych, takich jak wiadomości lub klucz sesji. Typowe algorytmy wyznaczania wartości skrótu to MD2, MD4, MD5 i SHA-1.  
  
 Protokół Kerberos  
 Protokół, który definiuje sposób interakcji klientów z usługą uwierzytelniania sieci. Klient uzyskać bilety z Centrum dystrybucji kluczy (KDC) protokołu Kerberos i prezentować te bilety do serwerów, gdy nawiązywane są połączenia. Bilety protokołu Kerberos reprezentują poświadczenia sieci klienta.  
  
 Urząd zabezpieczeń lokalnych (LSA)  
 Chroniony podsystem, który uwierzytelnia użytkowników i loguje się do systemu lokalnego. LSA udostępnia również informacje dotyczące wszystkich aspektów zabezpieczeń lokalnych w systemie, nazywane zbiorczo zasady zabezpieczeń lokalnych systemu.  
  
 Negotiate  
 Dostawca obsługi zabezpieczeń (SSP) działającego jako warstwy aplikacji między interfejs obsługuje dostawca zabezpieczeń (SSPI) i udostępnieniem. Gdy aplikacja wywoła SSPI zalogować się do sieci, można określić SSP, aby przetworzyć żądanie. Jeśli aplikacja Określa `Negotiate`, `Negotiate` analizuje żądania i odpowiedzi wybiera najlepsze SSP obsłużyć żądania na podstawie zasad zabezpieczeń skonfigurowane przez klienta.  
  
 Identyfikator jednorazowy  
 Wartość losowo generowany używane w celu pokonania ataków "oparte na metodzie powtórzeń".  
  
 Niemożność wyparcia  
 Zdolność do identyfikacji użytkowników, którzy wykonali pewnych działań, w związku z tym irrefutably przeciwdziałanie wszelkie próby Odmów odpowiedzialności przez użytkownika. Na przykład system będą mogli zalogować się identyfikator użytkownika w każdym przypadku, gdy plik zostanie usunięty.  
  
 Standard kryptografii klucza publicznego (PKCS)  
 Specyfikacje wydzielana w celu przyspieszenia wdrażania kryptografii klucza publicznego RSA Data Security, Inc. we współpracy z programistami systemów zabezpieczeń na całym świecie.  
  
 PKCS #7  
 Standard składni wiadomości kryptograficznych. Ogólna składnia dla danych, do których kryptografii mogą być stosowane, takich jak podpisów cyfrowych i szyfrowania. Umożliwia także składnię do rozpowszechniania certyfikatów i list odwołania certyfikatów i innych atrybutów wiadomości, takich jak sygnatury czasowe, komunikat o.  
  
 zwykły tekst  
 Komunikat, który nie jest zaszyfrowany. Wiadomości w postaci zwykłego tekstu są czasami określane jako *jako zwykły tekst* wiadomości.  
  
 uprawnienie  
 Prawa użytkownika do wykonywania różnych operacji związanych z systemem, takie jak zamykania systemu, ładowanie sterowniki urządzeń lub zmieniając czas systemowy. Token dostępu użytkownika zawiera listę uprawnień, czy użytkownik lub przez użytkownika grupy wstrzymania.  
  
 klucz prywatny  
 Tajne połowie używany w algorytmie klucz publiczny z pary kluczy. Klucze prywatne są zazwyczaj używane do szyfrowania symetrycznego klucza sesji, cyfrowego podpisywania wiadomości lub odszyfrować wiadomości, które zostały zaszyfrowane przy użyciu odpowiedniego klucza publicznego. Zobacz też "klucz publiczny."  
  
 proces  
 Kontekst zabezpieczeń, w którym działa aplikacja. Zazwyczaj kontekst zabezpieczeń jest skojarzona z użytkownikiem, więc wszystkie aplikacje uruchomione w ramach danego procesu na uprawnienia i uprawnienia użytkownika będącego właścicielem.  
  
 pary kluczy publiczny/prywatny  
 Zestaw kluczami kryptograficznymi używanymi dla kryptografii klucza publicznego. Dla każdego użytkownika dostawcy usług kryptograficznych (CSP) zazwyczaj obsługuje dwie pary kluczy publiczny/prywatny: pary kluczy programu exchange i pary kluczy podpisu cyfrowego. Pary kluczy są przechowywane z sesji do sesji.  
  
 klucz publiczny  
 Klucz kryptograficzny zazwyczaj używane do odszyfrowywania klucza sesji lub podpis cyfrowy. Klucz publiczny można również zaszyfrować wiadomości, gwarantując, że tylko osoby z odpowiedniego klucza prywatnego może odszyfrować komunikatu.  
  
 szyfrowanie klucza publicznego  
 Szyfrowanie, który używa pary kluczy, jeden klucz szyfrowania danych i drugi klucz do odszyfrowania danych. Z kolei algorytmów szyfrowania symetrycznego, które korzystają z jednego klucza do szyfrowania i odszyfrowywania. W praktyce kryptografii klucza publicznego jest zazwyczaj używany do ochrony klucza sesji, który używa algorytmu szyfrowania symetrycznego. W tym przypadku klucz publiczny jest używany do szyfrowania klucza sesji, który z kolei używane do szyfrowania niektórych danych, a klucz prywatny jest używany do odszyfrowywania. Oprócz ochrony kluczy sesji, kryptografii klucza publicznego mogą również cyfrowe podpisywanie komunikat (przy użyciu klucza prywatnego) i sprawdzić poprawności podpisu (przy użyciu klucza publicznego).  
  
 infrastruktury kluczy publicznych (PKI)  
 Infrastruktury, zapewniając zintegrowany zestaw usług i narzędzi administracyjnych do tworzenia, wdrażania i zarządzania aplikacjami klucza publicznego.  
  
 odrzucenie  
 Możliwość błędnie Odmów wykonanie akcji podczas innych podmiotów użytkownik nie może potwierdzić inaczej. Na przykład użytkownik, który usuwa plik, i kto pomyślnie odmowy, zrobił.  
  
 główny urząd certyfikacji  
 Urząd certyfikacji, w górnej części hierarchii urzędów certyfikacji. Główny urząd certyfikacji poświadcza urzędów certyfikacji na następnym poziomie hierarchii.  
  
 Secure Hash Algorithm (SHA)  
 Algorytm wyznaczania wartości skrótu, który generuje skrót wiadomości. Za pomocą podpisów cyfrowych algorytm (DSA) w Digital Signature Standard (DSS), między innymi używany jest algorytm SHA. Istnieją cztery różne typy SHA: SHA-1, SHA-256, SHA-384 i SHA-512. SHA-1 generuje 160-bitowy skrót wiadomości. Algorytm SHA-256, SHA-384 i SHA-512 generować 256-bitowego, 384-bitowy i 512-bitowy, komunikatów skróty służące odpowiednio. Agent kondycji systemu został opracowany przez instytut National Institute of Standards and Technology (NIST) oraz przez National Security Agency (NSA).  
  
 Secure Sockets Layer (SSL)  
 Protokół komunikacji sieciowej bezpiecznej, korzystając z technologii kluczy publicznych i wpisu tajnego.  
  
 kontekst zabezpieczeń  
 Atrybuty zabezpieczeń lub reguły, działających w danej chwili. Na przykład: bieżący użytkownik zalogowany na komputerze lub osobistego numeru identyfikacyjnego wprowadzonej przez użytkownika karty inteligentnej. Dla interfejsu SSPI kontekst zabezpieczeń jest struktura nieprzezroczyste danych, która zawiera dane zabezpieczeń, które są odpowiednie do połączenia, np. klucza sesji lub wskazywać na czas trwania sesji.  
  
 podmiot zabezpieczeń  
 Jednostka rozpoznawane przez system zabezpieczeń. Podmiotów zabezpieczeń mogą obejmować użytkowników ludzi, a także autonomicznego procesów.  
  
 Dostawca obsługi zabezpieczeń (SSP)  
 Biblioteka dołączana dynamicznie (DLL), która implementuje interfejs SSPI, udostępniając co najmniej jeden pakiet zabezpieczeń do aplikacji. Każdy pakiet zabezpieczeń zawiera mapowania między wywołania funkcji SSPI aplikacji i funkcji na model zabezpieczeń rzeczywiste. Pakiety zabezpieczeń obsługuje protokoły zabezpieczeń, takie jak uwierzytelnianie Kerberos i Microsoft LAN Manager (LanMan).  
  
 Interfejs dostawcy obsługi zabezpieczeń (SSPI)  
 Wspólny interfejs między aplikacjami na poziomie transportu, takich jak Microsoft zdalnego wywołania procedury (RPC) i dostawców zabezpieczeń, takich jak Windows rozproszone zabezpieczeń. Interfejs SSPI pozwala aplikacjom transportu wywołać jedną z kilku dostawców zabezpieczeń, aby uzyskać uwierzytelnionego połączenia. Te wywołania nie wymagają obszerną wiedzę na temat szczegółów protokołu zabezpieczeń.  
  
 Usługa tokenu zabezpieczającego  
 Usługi zaprojektowane do wystawiania i zarządzania nimi tokenów zabezpieczających niestandardowe (wystawionych tokenów) w scenariuszu wielofunkcyjnych. Tokeny niestandardowe są zazwyczaj tokenów zabezpieczeń potwierdzenia Markup Language (SAML), które zawierają niestandardowe poświadczenia.  
  
 certyfikat serwera  
 Odnosi się do certyfikatu używany do uwierzytelniania serwera, na przykład podczas uwierzytelniania serwera sieci Web w przeglądarce internetowej. Gdy klient przeglądarki sieci Web próbuje uzyskać dostęp do zabezpieczonej serwera sieci Web, serwer wysyła swój certyfikat w przeglądarce, aby umożliwić go w celu zweryfikowania tożsamości serwera.  
  
 Sesji  
 Wymiana komunikatów w ramach ochrony pojedynczy materiału klucza. Na przykład sesji SSL Użyj jednego klucza do wysyłania wielu komunikatów i z powrotem w ramach tego klucza.  
  
 klucz sesji  
 Losowo generowany klucz, który jest używany jeden raz, a następnie zostaje odrzucone. Sesji są klucze symetryczne (używany do szyfrowania i odszyfrowywania). Są one wysyłane z wiadomością chronione przez szyfrowanie przy użyciu klucza publicznego z zamierzonym odbiorcą. Klucz sesji składa się z około 40 do 2000 bitów liczbę losową.  
  
 dodatkowe poświadczenia  
 Użyj poświadczeń dla podczas uwierzytelniania do domeny zabezpieczeń obcego podmiotu zabezpieczeń.  
  
 szyfrowanie symetryczne  
 Szyfrowanie, który korzysta z jednego klucza do szyfrowania i odszyfrowywania. Szyfrowania symetrycznego jest preferowana w przypadku szyfrowania dużych ilości danych. To niektóre z najczęściej algorytmów szyfrowania symetrycznego RC2, RC4 i Data Encryption Standard (DES).  
  
 Zobacz też "szyfrowanie kluczem publicznym."  
  
 Klucz symetryczny  
 Pojedynczy klucz używany do szyfrowania i odszyfrowywania. Klucze sesji są zazwyczaj symetryczne.  
  
 Token (token dostępu)  
 Token dostępu zawiera informacje dotyczące zabezpieczeń dla sesji logowania. System tworzy token dostępu, gdy użytkownik loguje się, a każdy proces wykonywany w imieniu użytkownika ma kopię tokenu. Token identyfikuje użytkownika, grupy użytkowników i uprawnień użytkownika. System używa tokenu do kontrolowania dostępu do zabezpieczanych obiektów oraz do sterowania użytkownikowi możliwość wykonywania różnych operacji związanych z systemu na komputerze lokalnym. Istnieją dwa rodzaje tokenów dostępu podstawowego i personifikacji.  
  
 Warstwa transportu  
 Warstwa sieci, która jest odpowiedzialny za obie jakości usług i dokładne dostarczania informacji. Wśród zadań wykonywanych w tej warstwie to wykrywanie błędów i korekty.  
  
 Lista zaufania (listy zaufania certyfikatów lub listę zaufania certyfikatów)  
 Wstępnie zdefiniowanej listy elementów, które zostały podpisane przez zaufane jednostki. Lista CTL może być dowolna, takich jak lista skrótów certyfikatów lub Podaj listę nazw plików. Wszystkie elementy na liście są uwierzytelniane (zatwierdzone) przez jednostkę podpisywania.  
  
 Dostawca zaufania  
 Oprogramowanie, które decyduje, czy dany plik jest zaufany. Ta decyzja opiera się na certyfikat skojarzony z plikiem.  
  
 główna nazwa użytkownika (UPN)  
 Nazwa konta użytkownika (czasami określane jako *nazwa logowania użytkownika*) i nazwa domeny identyfikującej domenę, w którym znajduje się konto użytkownika. Jest to standardowy używana do logowania do domeny Windows. Format to: someone@example.com (podobnie jak adres e-mail).  
  
> [!NOTE]
>  Oprócz standardowych formularza nazwy UPN WCF akceptuje nazwy UPN w postaci niskiego poziomu, na przykład cohowinery.com\someone.  
  
 X.509  
 Międzynarodowo standard dla certyfikatów definiujący ich wymagane elementy.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe pojęcia programu Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)
- [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
