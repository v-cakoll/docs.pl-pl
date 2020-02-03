---
title: Terminologia dotycząca zabezpieczeń programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
ms.openlocfilehash: 6751513b72f732bd7392de11a203467a9ead1bce
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743345"
---
# <a name="wcf-security-terminology"></a>Terminologia dotycząca zabezpieczeń programu WCF
Niektóre terminologii używane podczas omawiania zabezpieczeń mogą być nieznane. Ten temat zawiera krótkie objaśnienia niektórych warunków zabezpieczeń, ale nie stanowi wyczerpującej dokumentacji dla każdego elementu.  
  
 Aby uzyskać więcej informacji na temat terminów używanych w dokumentacji Windows Communication Foundation (WCF), zobacz [podstawowe pojęcia dotyczące Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 Lista kontroli dostępu (ACL)  
 Lista ochrony zabezpieczeń odnoszących się do obiektu. (Obiekt może być plikiem, procesem, zdarzeniem lub coś innego mającego deskryptor zabezpieczeń). Wpis na liście ACL to wpis kontroli dostępu (ACE). Istnieją dwa typy list ACL: uznaniowe i systemowe.  
  
 uwierzytelnianie  
 Proces sprawdzania, czy użytkownik, komputer, usługa lub proces to osoba lub jej oświadczenia.  
  
 autoryzacja  
 Czynność kontrolowania dostępu i praw do zasobu. Na przykład umożliwienie członkom jednej grupy odczytanie pliku, ale zezwolenie tylko członkom innej grupy na zmianę pliku.  
  
 certyfikat urzędu certyfikacji  
 Identyfikuje urząd certyfikacji, który wystawia certyfikaty uwierzytelniania serwera i klienta do serwerów i klientów żądających tych certyfikatów. Ponieważ zawiera klucz publiczny używany w podpisach cyfrowych, jest również określany jako *certyfikat sygnatury*. Jeśli urząd certyfikacji jest urzędem głównym, certyfikat urzędu certyfikacji może być określany jako *certyfikat główny*. Czasami nazywane także *certyfikatem lokacji*.  
  
 Hierarchia urzędu certyfikacji  
 Hierarchia urzędu certyfikacji zawiera wiele urzędów certyfikacji. Jest on zorganizowany tak, aby każdy urząd certyfikacji był certyfikowany przez inny urząd certyfikacji na wyższym poziomie hierarchii do momentu osiągnięcia górnej części hierarchii, znanej również jako *urząd główny*.  
  
 certificate  
 Podpisane cyfrowo oświadczenie zawierające informacje o jednostce i kluczu publicznym jednostki, w ten sposób powiązać te dwa informacje razem. Certyfikat jest wystawiany przez zaufaną organizację (lub jednostkę), nazywaną urzędem certyfikacji, po sprawdzeniu przez urząd, że jest on widoczny.  
  
 Certyfikaty mogą zawierać różne typy danych. Na przykład certyfikat X. 509 zawiera format certyfikatu, numer seryjny certyfikatu, algorytm używany do podpisywania certyfikatu, nazwę urzędu certyfikacji, który wystawił certyfikat, nazwę i klucz publiczny jednostki żądającej certyfikatu i podpis urzędu certyfikacji.  
  
 Magazyn certyfikatów  
 Zwykle magazyn trwały, w którym są przechowywane certyfikaty, listy odwołania certyfikatów (CRL) i listy zaufania certyfikatów (CTL). Istnieje jednak możliwość tworzenia i otwierania magazynu certyfikatów wyłącznie w pamięci podczas pracy z certyfikatami, które nie muszą być umieszczane w magazynie trwałym.  
  
 claims  
 Informacje przesyłane z jednej jednostki do innej używanej do ustanowienia tożsamości nadawcy. Na przykład nazwa użytkownika i token hasła lub certyfikat X. 509.  
  
 certyfikat klienta  
 Odnosi się do certyfikatu używanego do uwierzytelniania klienta, takiego jak uwierzytelnianie przeglądarki sieci Web na serwerze sieci Web. Gdy klient przeglądarki sieci Web próbuje uzyskać dostęp do zabezpieczonego serwera sieci Web, klient wysyła swój certyfikat do serwera, aby umożliwić mu zweryfikowanie tożsamości klienta.  
  
 uwierzytelniające  
 Wcześniej uwierzytelnione dane logowania używane przez podmiot zabezpieczeń do ustalenia własnej tożsamości, takie jak hasło, lub biletu protokołu Kerberos. Poświadczenia służą do kontrolowania dostępu do zasobów.  
  
 dane szyfrowane  
 Typ zawartości danych zdefiniowany przez #7 kryptograficzny (Public Key Cryptographic standard), który składa się z dowolnego typu danych oraz skrótu wiadomości (Digest) zawartości.  
  
 podpis cyfrowy  
 Dane wiążące tożsamość nadawcy z wysyłanymi informacjami. Podpis cyfrowy może być powiązany z dowolnym komunikatem, plikiem lub innymi informacjami zakodowanymi cyfrowo lub przesyłane osobno. Podpisy cyfrowe są używane w środowiskach kluczy publicznych i zapewniają usługi uwierzytelniania i integralności.  
  
 encoding  
 Proces przekształcania danych do strumienia bitów. Kodowanie jest częścią procesu serializacji, który konwertuje dane na strumień tych i zer.  
  
 para kluczy wymiany  
 Para kluczy publiczny/prywatny służąca do szyfrowania kluczy sesji, dzięki czemu mogą być bezpiecznie przechowywane i wymieniane z innymi użytkownikami.  
  
 hash  
 Wartość liczbowa o stałym rozmiarze uzyskana przez zastosowanie funkcji matematycznej (zobacz algorytm mieszania) do dowolnej ilości danych. Dane zazwyczaj zawierają dane losowe, znane jako identyfikator *jednorazowy*. Zarówno usługa, jak i klient tworzą program Exchange identyfikatorów jednorazowych, aby zwiększyć złożoność wyniku. Wynik jest również znany jako *skrót wiadomości*. Wysyłanie wartości skrótu jest bezpieczniejsze niż wysyłanie poufnych danych, takich jak hasło, nawet jeśli hasło jest szyfrowane. Nadawca i odbiorca skrótu muszą wyrazić zgodę na algorytm wyznaczania wartości skrótu i identyfikatorów jednorazowych, tak aby po otrzymaniu można było zweryfikować skrót.  
  
 algorytm wyznaczania wartości skrótu  
 Algorytm używany do tworzenia wartości skrótu dla pewnego fragmentu danych, na przykład wiadomości lub klucza sesji. Typowe algorytmy wyznaczania wartości skrótu to MD2, MD4, MD5 i SHA-1.  
  
 Protokół Kerberos  
 Protokół, który definiuje sposób, w jaki klienci współdziałają z usługą uwierzytelniania sieciowego. Klienci uzyskują bilety z centrum dystrybucji kluczy protokołu Kerberos (KDC) i przedstawią te bilety serwerowi w przypadku nawiązywania połączeń. Bilety protokołu Kerberos reprezentują poświadczenia sieciowe klienta.  
  
 Urząd zabezpieczeń lokalnych (LSA)  
 Chroniony podsystem służący do uwierzytelniania i rejestrowania użytkowników w systemie lokalnym. Urząd LSA utrzymuje również informacje o wszystkich aspektach zabezpieczeń lokalnych w systemie, które są określane zbiorczo jako zasady zabezpieczeń lokalnych systemu.  
  
 Negotiate  
 Dostawca obsługi zabezpieczeń (SSP), który działa jako warstwa aplikacji między interfejsem dostawcy obsługi zabezpieczeń (SSPI) a innym dostawców SSP. Gdy aplikacja wywołuje interfejs SSPI w celu zalogowania się do sieci, może określić dostawcę SSP, aby przetworzyć żądanie. Jeśli aplikacja określi `Negotiate`, `Negotiate` analizuje żądanie i wybiera najlepszą dostawcę SSP do obsługi żądania zgodnie z zasadami zabezpieczeń skonfigurowanymi przez klienta.  
  
 nonce  
 Generowana losowo wartość służąca do pokonania ataków "Replay".  
  
 niemożność wyparcia  
 Możliwość identyfikowania użytkowników, którzy wykonali pewne działania, a tym samym irrefutablyą wszelkie próby odmowy odpowiedzialności przez użytkownika. Na przykład system może rejestrować identyfikator użytkownika za każdym razem, gdy plik zostanie usunięty.  
  
 Standard kryptografii klucza publicznego (PKCS)  
 Specyfikacje opracowane przez firmę RSA Data Security, Inc. we współpracy z deweloperami bezpiecznych systemów na całym świecie w celu przyspieszenia wdrożenia kryptografii klucza publicznego.  
  
 PKCS #7  
 Standard składni wiadomości kryptograficznych. Ogólna składnia danych, do których można zastosować kryptografię, na przykład podpisy cyfrowe i szyfrowanie. Zawiera również składnię rozpowszechniania certyfikatów lub list odwołania certyfikatów oraz inne atrybuty komunikatów, takie jak sygnatury czasowe, do wiadomości.  
  
 formacie  
 Komunikat, który nie jest szyfrowany. Wiadomości w postaci zwykłego tekstu są czasami określane jako wiadomości ze *zwykłym tekstem* .  
  
 kont  
 Prawo użytkownika do wykonywania różnych operacji związanych z systemem, takich jak zamykanie systemu, ładowanie sterowników urządzeń lub zmiana czasu systemowego. Token dostępu użytkownika zawiera listę uprawnień, które są przechowywane przez użytkownika lub grupy użytkowników.  
  
 klucz prywatny  
 Tajna połowa pary kluczy używana w algorytmie klucza publicznego. Klucze prywatne są zwykle używane do szyfrowania symetrycznego klucza sesji, cyfrowego podpisywania wiadomości lub odszyfrowywania wiadomości, która została zaszyfrowana przy użyciu odpowiedniego klucza publicznego. Zobacz również "klucz publiczny".  
  
 proces  
 Kontekst zabezpieczeń, w którym działa aplikacja. Zazwyczaj kontekst zabezpieczeń jest skojarzony z użytkownikiem, więc wszystkie aplikacje działające w ramach danego procesu przyjmują uprawnienia i uprawnienia użytkownika będącego właścicielem.  
  
 para kluczy publiczny/prywatny  
 Zestaw kluczy kryptograficznych używanych na potrzeby kryptografii klucza publicznego. Dla każdego użytkownika dostawca usług kryptograficznych (CSP) zwykle utrzymuje dwie pary kluczy publicznych/prywatnych: parę kluczy wymiany i pary kluczy podpisu cyfrowego. Obie pary kluczy są utrzymywane z sesji na sesję.  
  
 klucz publiczny  
 Klucz kryptograficzny jest zazwyczaj używany podczas odszyfrowywania klucza sesji lub podpisu cyfrowego. Klucza publicznego można także użyć do zaszyfrowania komunikatu, gwarantując, że tylko osoba z odpowiednim kluczem prywatnym może odszyfrować komunikat.  
  
 szyfrowanie klucza publicznego  
 Szyfrowanie, które używa pary kluczy, jednego klucza do szyfrowania danych i drugiego klucza w celu odszyfrowania danych. W przeciwieństwie do algorytmów szyfrowania symetrycznego, które używają tego samego klucza do szyfrowania i odszyfrowywania. W tym przypadku Kryptografia klucza publicznego jest zwykle używana do ochrony klucza sesji używany algorytm szyfrowania symetrycznego. W takim przypadku klucz publiczny jest używany do szyfrowania klucza sesji, który z kolei został użyty do szyfrowania danych, a klucz prywatny jest używany do odszyfrowywania. Oprócz ochrony kluczy sesji Kryptografia klucza publicznego może również służyć do cyfrowego podpisywania wiadomości (przy użyciu klucza prywatnego) i weryfikowania podpisu (przy użyciu klucza publicznego).  
  
 infrastruktura kluczy publicznych (PKI)  
 Infrastruktura dostarczająca zintegrowany zestaw usług i narzędzi administracyjnych służących do tworzenia i wdrażania aplikacji i zarządzania nimi.  
  
 rzuca  
 Zdolność użytkownika do fałszywych odmowy wykonywania akcji, podczas gdy inne strony nie mogą udowodnić inaczej. Na przykład użytkownik, który usunął plik i który może pomyślnie odmówić wykonania.  
  
 urząd główny  
 Urząd certyfikacji w górnej części hierarchii urzędu certyfikacji. Urząd główny poświadcza urzędy certyfikacji na następnym poziomie hierarchii.  
  
 Algorytm bezpiecznego wyznaczania wartości skrótu (SHA)  
 Algorytm wyznaczania wartości skrótu, który generuje skrót wiadomości. SHA jest używany z algorytmem podpisu cyfrowego (DSA) w standardzie sygnatury cyfrowej (DSS) w innych miejscach. Istnieją cztery odmiany SHA-1, SHA-256, SHA-384 i SHA-512. Algorytm SHA-1 generuje 160-bitowy skrót wiadomości. Algorytm SHA-256, SHA-384 i SHA-512 generują odpowiednio skróty 256-bitowe, 384 i 512. Algorytm SHA został opracowany przez Narodowy Instytut standardów i technologii (NIST) oraz przez Agencję Bezpieczeństwa Narodowego.  
  
 SSL (SSL)  
 Protokół zabezpieczania komunikacji sieciowej przy użyciu kombinacji technologii publicznego i tajnego klucza.  
  
 kontekst zabezpieczeń  
 Atrybuty lub reguły zabezpieczeń, które są obecnie obowiązujące. Na przykład bieżący użytkownik zalogowany na komputerze lub osobisty numer identyfikacyjny wprowadzony przez użytkownika karty inteligentnej. W przypadku interfejsu SSPI kontekst zabezpieczeń jest nieprzezroczystą strukturą danych, która zawiera dane zabezpieczeń odpowiednie dla połączenia, takie jak klucz sesji lub wskazanie czasu trwania sesji.  
  
 podmiot zabezpieczeń  
 Jednostka rozpoznawana przez system zabezpieczeń. Podmioty zabezpieczeń mogą obejmować zarówno użytkowników ludzkich, jak i autonomiczne procesy.  
  
 Dostawca obsługi zabezpieczeń (SSP)  
 Biblioteka dołączana dynamicznie (DLL) implementująca interfejs SSPI przez udostępnienie co najmniej jednego pakietu zabezpieczeń dla aplikacji. Każdy pakiet zabezpieczeń zawiera mapowania między wywołaniami funkcji interfejsu SSPI aplikacji a rzeczywistymi funkcjami modelu zabezpieczeń. Pakiety zabezpieczeń obsługują protokoły zabezpieczeń, takie jak uwierzytelnianie Kerberos i Microsoft LAN Manager (LanMan).  
  
 Interfejs dostawcy obsługi zabezpieczeń (SSPI)  
 Wspólny interfejs między aplikacjami na poziomie transportu, takimi jak zdalne wywoływanie procedur (RPC) firmy Microsoft, oraz dostawcy zabezpieczeń, takie jak zabezpieczenia rozproszone systemu Windows. Interfejs SSPI umożliwia aplikacji transportowej wywoływanie jednego z kilku dostawców zabezpieczeń w celu uzyskania uwierzytelnionego połączenia. Te wywołania nie wymagają obszernej znajomości szczegółowych informacji o protokole zabezpieczeń.  
  
 Usługa tokenu zabezpieczającego  
 Usługi przeznaczone do wystawiania niestandardowych tokenów zabezpieczeń (wystawionych tokenów) i zarządzania nimi w scenariuszu wielousługowym. Tokeny niestandardowe to zazwyczaj tokeny języka SAML (Security Assertions Markup Language), które zawierają poświadczenia niestandardowe.  
  
 certyfikat serwera  
 Odnosi się do certyfikatu używanego do uwierzytelniania serwera, takiego jak uwierzytelnianie serwera sieci Web w przeglądarce internetowej. Gdy klient przeglądarki sieci Web próbuje uzyskać dostęp do zabezpieczonego serwera sieci Web, serwer wysyła swój certyfikat do przeglądarki, aby umożliwić mu zweryfikowanie tożsamości serwera.  
  
 obrad  
 Wymiana komunikatów w ramach ochrony jednego fragmentu materiału klucza. Na przykład sesje SSL używają jednego klucza do wysyłania wielu wiadomości z powrotem i w dół w ramach tego klucza.  
  
 klucz sesji  
 Losowo wygenerowany klucz, który jest używany raz, a następnie odrzucony. Klucze sesji są symetryczne (używane do szyfrowania i odszyfrowywania). Są one wysyłane z wiadomością chronioną przez szyfrowanie za pomocą klucza publicznego od zamierzonego odbiorcy. Klucz sesji składa się z losowej liczby około 40 do 2 000 bitów.  
  
 dodatkowe poświadczenia  
 Poświadczenia do użycia podczas uwierzytelniania podmiotu zabezpieczeń w obcych domenach zabezpieczeń.  
  
 szyfrowanie symetryczne  
 Szyfrowanie używające jednego klucza do szyfrowania i odszyfrowywania. Szyfrowanie symetryczne jest preferowane w przypadku szyfrowania dużych ilości danych. Niektóre z bardziej popularnych algorytmów szyfrowania symetrycznego to RC2, RC4 i Data Encryption Standard (DES).  
  
 Zobacz też "szyfrowanie klucza publicznego".  
  
 klucz symetryczny  
 Pojedynczy klucz używany do szyfrowania i odszyfrowywania. Klucze sesji są zwykle symetryczne.  
  
 token (token dostępu)  
 Token dostępu zawiera informacje o zabezpieczeniach dla sesji logowania. System tworzy token dostępu podczas logowania użytkownika, a każdy proces wykonywany w imieniu użytkownika ma kopię tokenu. Token identyfikuje użytkownika, grupy użytkowników i uprawnienia użytkownika. System używa tokenu, aby kontrolować dostęp do zabezpieczanych obiektów i kontrolować zdolność użytkownika do wykonywania różnych operacji związanych z systemem na komputerze lokalnym. Istnieją dwa rodzaje tokenów dostępu, podstawowe i personifikacja.  
  
 Warstwa transportu  
 Warstwa sieci, która jest odpowiedzialna za jakość usługi i dokładne dostarczanie informacji. Między zadaniami wykonywanymi w tej warstwie są wykrywanie i Korekcja błędów.  
  
 Lista zaufania (Lista zaufania certyfikatów lub CTL)  
 Wstępnie zdefiniowana lista elementów, które zostały podpisane przez zaufaną jednostkę. Lista CTL może mieć dowolną wartość, na przykład listę skrótów certyfikatów lub listę nazw plików. Wszystkie elementy na liście są uwierzytelniane (zatwierdzone) przez jednostkę podpisującą.  
  
 Dostawca zaufania  
 Oprogramowanie, które decyduje o tym, czy dany plik jest zaufany. Ta decyzja jest oparta na certyfikacie skojarzonym z plikiem.  
  
 główna nazwa użytkownika (UPN)  
 Nazwa konta użytkownika (czasem określana jako *Nazwa logowania użytkownika*) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika. Jest to standardowe użycie logowania do domeny systemu Windows. Format to: someone@example.com (jak w przypadku adresu e-mail).  
  
> [!NOTE]
> Oprócz standardowego formularza UPN, WCF akceptuje UPN w formularzu niskiego poziomu, na przykład cohowinery. com\someone.  
  
 X.509  
 Międzynarodowy, uznawany w międzynarodowym Standard dla certyfikatów, który definiuje ich wymagane części.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe pojęcia programu Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)
- [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
