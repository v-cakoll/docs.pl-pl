---
title: "Terminologia dotycząca zabezpieczeń programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF], terminology
- security glossary [WCF]
- security terms [WCF]
ms.assetid: 68dde024-8e51-40ba-804f-ec52d85e9ca9
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 352615238d95cf02788cf88ef412a11ffd2faf37
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="wcf-security-terminology"></a>Terminologia dotycząca zabezpieczeń programu WCF
Niektóre z terminologią używaną w opisach zabezpieczeń mogą być nieznane. Ten temat zawiera krótkie objaśnienia niektóre pojęcia dotyczące zabezpieczeń, ale nie mają na celu dostarczenie wyczerpujące dla każdego elementu.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] terminów używanych w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dokumentacji, zobacz [podstawowe pojęcia programu Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md).  
  
 listy kontroli dostępu (ACL)  
 Lista zabezpieczeń obiektu. (Obiekt może być pliku, procesu, zdarzenia lub niczego else o deskryptora zabezpieczeń). Wpis na liście kontroli dostępu jest wpisu kontroli dostępu (ACE). Istnieją dwa typy list kontroli dostępu: DACL i systemu.  
  
 uwierzytelnianie  
 Proces sprawdzania, czy użytkownika, komputera, usługi lub procesu jest kto lub co się podaje.  
  
 autoryzacja  
 Czynność kontroli dostępu i uprawnienia do zasobu. Na przykład co pozwala użytkownikom jednej grupy do odczytu pliku, ale stosowanie tylko elementami członkowskimi innej grupy, aby zmienić plik.  
  
 certyfikat urzędu certyfikacji  
 Identyfikuje urzędu certyfikacji, który wystawia certyfikaty uwierzytelniania serwera i klienta dla serwerów i klientów, którzy żądać tych certyfikatów. Ponieważ zawiera klucz publiczny używany w podpisów cyfrowych, jest ona również określana jako *certyfikat podpisu*. Jeśli urząd certyfikacji jest urzędem głównym, certyfikatu urzędu certyfikacji może być traktowana jako *certyfikat główny*. Czasami nazywane *certyfikatu witryny*.  
  
 Hierarchii urzędów certyfikacji  
 Hierarchia certyfikacji zawiera wiele urzędów certyfikacji. Jest zorganizowana, dzięki czemu w każdym urzędzie certyfikacji jest certyfikowany przez inny urząd certyfikacji w wyższego poziomu hierarchii do góry hierarchii, znanej także jako *główny urząd*, który limit zostanie osiągnięty.  
  
 certificate  
 Instrukcja podpisane cyfrowo, która zawiera informacje dotyczące jednostki i klucz publiczny podmiotu, w związku z tym razem powiązanie tych dwóch rodzajów informacji. Certyfikat jest wystawiony przez zaufany urząd organizacji (lub jednostek), nazywany certyfikacji, po urząd zweryfikował, że jednostka jest tożsamości jest.  
  
 Certyfikaty mogą zawierać różne typy danych. Na przykład certyfikat X.509 zawiera formatu certyfikatu, numer seryjny certyfikatu algorytm używany do podpisywania certyfikatu, nazwy urzędu certyfikacji, który wystawił certyfikat, nazwa i klucz publiczny podmiotu żądanie certyfikatu , a podpisu urzędu certyfikacji.  
  
 Magazyn certyfikatów  
 Zazwyczaj są przechowywane magazynie trwałym, gdzie, certyfikatów list odwołania (CRL), a listy zaufania certyfikatów (CTL). Jest to możliwe, jednak do tworzenia i otwierania magazynu certyfikatów wyłącznie w pamięci podczas pracy z certyfikatami, które nie muszą znajdować się w magazynie trwałym.  
  
 Oświadczenia  
 Informacje przekazywane z jednego obiektu do innego używany do ustanawiania tożsamość nadawcy. Na przykład nazwę użytkownika i hasło tokenu lub certyfikatu X.509.  
  
 Certyfikat klienta  
 Odwołuje się do certyfikatu używany do uwierzytelniania klientów, takich jak uwierzytelnianie przeglądarki sieci Web na serwerze sieci Web. Gdy klient przeglądarki sieci Web próbuje uzyskać dostęp do zabezpieczonych serwera sieci Web, klient wysyła swój certyfikat do serwera, aby umożliwić go do weryfikacji tożsamości klienta.  
  
 poświadczenia  
 Dane logowania, korzystającą z podmiotu zabezpieczeń w celu ustalenia jego tożsamość, takie jak hasła lub biletu protokołu Kerberos został poprzednio uwierzytelniony. Poświadczenia są używane do kontrolowania dostępu do zasobów.  
  
 porządkowanej danych  
 Typ zawartości danych zdefiniowany przez publicznego klucza kryptograficznego standard (PKCS) #7 składający się z dowolnego typu danych oraz skrót wiadomości (skrót) zawartości.  
  
 Podpis cyfrowy  
 Dane, które wiąże tożsamość nadawcy informacje są wysyłane. Podpis cyfrowy może dołączany do wiadomości, plik lub innymi informacjami lub przesyłane oddzielnie. Podpisy cyfrowe są używane w środowiskach klucza publicznego i świadczenia usług uwierzytelniania i integralności.  
  
 encoding  
 Proces przekształcania danych w strumieniu bitów. Kodowanie jest częścią procesu serializacji, który konwertuje dane na strumień jedynek i zer.  
  
 pary kluczy programu Exchange  
 Parą kluczy publiczny/prywatny używany do szyfrowania kluczy sesji, dzięki czemu można je bezpiecznie przechowywane i wymieniane z innymi użytkownikami.  
  
 hash  
 Wartość numeryczna stałym rozmiarze uzyskany przez zastosowanie funkcji matematycznych (patrz algorytmem wyznaczania wartości skrótu) do dowolnej ilości danych. Dane zwykle obejmują losowe dane, znany jako *identyfikator jednorazowy*. Usługa i klient współtworzenia identyfikatorów jednorazowych programu exchange w celu zwiększenia złożoności wyniku. Wynik jest także znana jako *skrót wiadomości*. Wysyłanie wartość skrótu jest bezpieczniejsza niż wysyłanie poufnych danych, takich jak hasła, nawet jeśli hasło jest szyfrowane. Skrót nadawcę i odbiorcę należy uzgodnić algorytmu wyznaczania wartości skrótu i identyfikatorów jednorazowych tak, aby po otrzymaniu, można zweryfikować wartości skrótu.  
  
 Algorytm wyznaczania wartości skrótu  
 Algorytm używany do uzyskiwania wartości skrótu danych, takich jak wiadomość lub klucz sesji. Typowe algorytmy wyznaczania wartości skrótu to MD2, MD4, MD5 i SHA-1.  
  
 Protokół Kerberos  
 Protokół, który definiuje sposób interakcji klientów z usługą uwierzytelniania sieci. Klienci uzyskać biletów z Centrum dystrybucji kluczy (KDC) protokołu Kerberos i stanowią one tych biletów do serwerów, gdy nawiązywane są połączenia. Bilety Kerberos reprezentują poświadczenia sieci klienta.  
  
 Urząd zabezpieczeń lokalnych (LSA)  
 Chroniony podsystem, który uwierzytelnia użytkowników i loguje się do systemu lokalnego. LSA przechowuje również informacje dotyczące wszystkich aspektów zabezpieczeń lokalnych w systemie, nazywanych zbiorczo zasady zabezpieczeń lokalnych systemu.  
  
 Negotiate  
 Dostawca obsługi zabezpieczeń (SSP), który działa jako warstwy aplikacji między interfejs obsługuje dostawcy zabezpieczeń (SSPI) i innych dostawców. Gdy aplikacja wywołuje do interfejsu SSPI, aby zalogować się do sieci, może określać SSP przetwarzania żądania. Jeśli aplikacja Określa `Negotiate`, `Negotiate` analizuje żądanie i wybiera najlepsze SSP można obsłużyć żądania na podstawie zasad zabezpieczeń skonfigurowane przez klienta.  
  
 Identyfikator jednorazowy  
 Wartość losowo generowany pozwala pokonać "powtarzania" ataków.  
  
 niemożność  
 Zdolność do identyfikowania użytkowników, którzy wykonać pewne akcje, w związku z tym irrefutably przeciwdziałanie wszelkie próby Odmów odpowiedzialność przez użytkownika. Na przykład system mogą rejestrować identyfikator użytkownika, zawsze, gdy plik zostanie usunięty.  
  
 Standard kryptografii klucza publicznego (PKCS)  
 Specyfikacje utworzonego przez RSA Data Security, Inc. we współpracy z programistami na całym świecie systemów zabezpieczeń w celu przyspieszenia wdrażania kryptografii klucza publicznego.  
  
 PKCS #7  
 Standard składni wiadomości kryptograficznych. Ogólna składnia dla danych do szyfrowania, które można stosować, na przykład podpisów cyfrowych i szyfrowania. Zapewnia także składni rozpowszechniania certyfikatów lub list odwołania certyfikatów i inne atrybuty wiadomości, takie jak sygnatury czasowe do wiadomości.  
  
 w postaci zwykłego tekstu  
 Komunikat, który nie jest zaszyfrowany. Wiadomości w postaci zwykłego tekstu są czasami określane jako *zwykłym tekstem* wiadomości.  
  
 uprawnień  
 Prawa użytkownika do wykonywania różnych operacji związanych z systemu, takie jak zamykania systemu, ładowanie sterowniki urządzeń lub zmieniając czas systemowy. Token dostępu użytkownika zawiera listę uprawnień, że użytkownik lub użytkownika grupy blokady.  
  
 klucz prywatny  
 Tajny połowę pary kluczy używanych w algorytm klucza publicznego. Klucze prywatne są zazwyczaj używane do szyfrowania symetrycznego klucza sesji, cyfrowego podpisywania wiadomości lub odszyfrowywania wiadomości, które zostały zaszyfrowane przy użyciu odpowiedniego klucza publicznego. Zobacz też "klucz publiczny".  
  
 proces  
 Kontekst zabezpieczeń, w którym działa aplikacja. Zazwyczaj kontekst zabezpieczeń jest skojarzony z użytkownikiem, więc wszystkie aplikacje uruchomione w danym procesie przybrać uprawnienia i uprawnienia użytkownika będący właścicielem.  
  
 pary kluczy publiczny/prywatny  
 Zestaw z kluczami kryptograficznymi używanymi dla kryptografii klucza publicznego. Dla każdego użytkownika dostawcy usług kryptograficznych (CSP) zwykle przechowuje dwie pary kluczy publiczny/prywatny: exchange pary kluczy i podpis cyfrowy pary kluczy. Pary kluczy są obsługiwane z sesji do sesji.  
  
 klucz publiczny  
 Klucz kryptograficzny zazwyczaj używane do odszyfrowywania klucza sesji lub podpis cyfrowy. Klucz publiczny mogą służyć do szyfrowania wiadomości, gwarantując, że tylko osoby przy użyciu odpowiedniego klucza prywatnego można odszyfrować wiadomości.  
  
 szyfrowanie klucza publicznego  
 Szyfrowanie używającej parę kluczy, jeden klucz szyfrowania danych i innych klucza do odszyfrowania danych. Z kolei algorytmów szyfrowania symetrycznego, które korzystają z jednego klucza do szyfrowania i odszyfrowywania. W praktyce kryptografii klucza publicznego jest zwykle używana do ochrony klucza sesji, który używa algorytmu szyfrowania symetrycznego. W takim przypadku klucz publiczny jest używany do szyfrowania klucza sesji, który z kolei używane do szyfrowania niektórych danych, a klucz prywatny jest używany do odszyfrowywania. Oprócz ochrony kluczy sesji, kryptografii klucza publicznego może również cyfrowe podpisywanie wiadomości (przy użyciu klucza prywatnego) i sprawdzić poprawności podpisu (przy użyciu klucza publicznego).  
  
 Infrastruktury kluczy publicznych (PKI)  
 Infrastruktura zapewnienie zintegrowany zestaw usług i narzędzi administracyjnych dla tworzenie, wdrażanie i zarządzanie aplikacjami klucza publicznego.  
  
 odrzucenie  
 Możliwość użytkownika fałszywie Odmów o wykonać akcji, gdy inne strony nie może okazać się inaczej. Na przykład użytkownik, który usuwa plik i kto pomyślnie Odmów, to.  
  
 główny urząd certyfikacji  
 Urząd certyfikacji na szczycie hierarchii urzędu certyfikacji. Główny urząd certyfikacji poświadcza następny poziom hierarchii urzędów certyfikacji.  
  
 Secure Hash Algorithm (SHA)  
 Algorytm wyznaczania wartości skrótu, który generuje skrót wiadomości. Agent kondycji systemu jest używany z podpisów cyfrowych algorytm (DSA) w Digital Signature Standard (DSS), między innymi. Istnieją cztery odmian SHA: SHA-1, SHA-256, SHA-384 i SHA-512. SHA-1 generuje 160-bitowy skrót wiadomości. Algorytm SHA-256, SHA-384 i SHA-512 Generowanie 256-bitowego, 384-bitowy, a komunikat 512-bitowe skróty służące odpowiednio. Agent kondycji systemu został opracowany przez National Institute of Standards and Technology (NIST) i przez National Security Agency (NSA).  
  
 Secure Sockets Layer (SSL)  
 Protokół komunikacji sieciowej bezpiecznej, korzystając z technologii kluczy publicznych i tajny.  
  
 kontekst zabezpieczeń  
 Atrybuty zabezpieczeń lub reguły, które są obecnie efekt. Na przykład bieżący użytkownik zalogowany na komputerze lub osobisty numer identyfikacyjny wprowadzonych przez użytkownika karty inteligentnej. Dla interfejsu SSPI kontekst zabezpieczeń jest struktura nieprzezroczyste danych, która zawiera dane zabezpieczeń odpowiednich do połączenia, takie jak klucz sesji lub oznaczeniem podczas sesji.  
  
 podmiot zabezpieczeń  
 Jednostka rozpoznawane przez system zabezpieczeń. Podmioty zabezpieczeń mogą obejmować ludzi, jak również autonomicznego procesów.  
  
 Dostawca obsługi zabezpieczeń (SSP)  
 Biblioteki dołączanej (dynamicznie DLL), który implementuje interfejs SSPI dokonując co najmniej jednego pakietu zabezpieczeń dostępne dla aplikacji. Każdy pakiet zabezpieczeń zawiera mapowań między wywołania funkcji SSPI aplikacji i funkcji modelu zabezpieczeń rzeczywistych. Pakiety zabezpieczeń obsługuje protokoły zabezpieczeń, takich jak uwierzytelnianie Kerberos i Microsoft LAN Manager (LanMan).  
  
 Interfejs dostawcy obsługi zabezpieczeń (SSPI)  
 Wspólny interfejs między aplikacjami poziomu transportu, takich jak Microsoft zdalnego wywołania procedury (RPC) i dostawców zabezpieczeń, takich jak Windows rozproszonych zabezpieczeń. Interfejs SSPI pozwala transportu aplikacjom wywoływanie jednego z kilku dostawców zabezpieczeń można uzyskać uwierzytelnionego połączenia. Tych wywołań nie wymagają doskonałej znajomości szczegóły protokołu zabezpieczeń.  
  
 Usługa tokenu zabezpieczającego  
 Usługi umożliwiają wystawianie i zarządzanie tokeny zabezpieczające niestandardowe (wystawionych tokenów) w scenariuszu wielofunkcyjnych. Tokeny niestandardowe są zazwyczaj tokenów zabezpieczeń potwierdzenia Markup Language (SAML), które zawierają niestandardowe poświadczenia.  
  
 certyfikat serwera  
 Odwołuje się do certyfikatu używany do uwierzytelniania serwera, takich jak uwierzytelnianie serwera sieci Web w przeglądarce sieci Web. Gdy klient przeglądarki sieci Web próbuje uzyskać dostęp do zabezpieczonych serwera sieci Web, serwer wysyła swój certyfikat w przeglądarce, aby umożliwić jego można zweryfikować tożsamości serwera.  
  
 Sesji  
 Wymiana wiadomości ochroną pojedynczy materiału klucza. Na przykład sesji SSL użyć jednego klucza do wysyłania wiadomości wiele i z powrotem w tym kluczu.  
  
 klucz sesji  
 Losowo wygenerowany klucz, który jest używany jeden raz, a następnie zostaje odrzucone. Klucze sesji są symetryczne (używany do szyfrowania i odszyfrowywania). Są one wysyłane z wiadomością chronione przez szyfrowanie za pomocą klucza publicznego z zamierzonym odbiorcą. Klucz sesji składa się z losową liczbę około 40 do 2000 bitów.  
  
 dodatkowe poświadczenia  
 Użyj poświadczeń dla w uwierzytelnianiu do domen zabezpieczeń obcego podmiotu zabezpieczeń.  
  
 szyfrowanie symetryczne  
 Szyfrowanie, który korzysta z jednego klucza do szyfrowania i odszyfrowywania. Szyfrowanie symetryczne jest preferowana w przypadku szyfrowania dużych ilości danych. Są niektóre z najczęściej algorytmów szyfrowania symetrycznego RC2, RC4 i szyfrowania DES (Data Standard).  
  
 Zobacz też "szyfrowanie klucza publicznego."  
  
 Klucz symetryczny  
 Jeden klucz używany do szyfrowania i odszyfrowywania. Klucze sesji są zwykle symetrycznego.  
  
 Token (token dostępu)  
 Token dostępu zawiera informacje dotyczące zabezpieczeń dla sesji logowania. System tworzy token dostępu, gdy użytkownik loguje się, a każdy proces wykonywany w imieniu użytkownika ma kopię tokenu. Token identyfikuje użytkowników, grup użytkowników i uprawnienia użytkownika. System używa tokenu do kontrolowania dostępu do zabezpieczanych obiektów oraz do sterowania użytkownika możliwość wykonywania różnych operacji związanych z systemu na komputerze lokalnym. Istnieją dwa rodzaje tokenów dostępu, podstawowy i personifikacji.  
  
 Warstwa transportu  
 Warstwa sieci, która jest odpowiedzialny za zarówno jakości usług i dokładne dostarczania informacji. Wśród zadań wykonywanych w tej warstwie to wykrywanie błędów i korekty.  
  
 Lista zaufania (listy zaufania certyfikatów lub listę zaufania certyfikatów)  
 Wstępnie zdefiniowanej listy elementów, które zostały podpisane przez zaufane jednostki. Lista CTL może być dowolna, takich jak lista skrótów certyfikatów lub listę nazw plików. Wszystkie elementy na liście są uwierzytelniane (zatwierdzone) przez jednostkę podpisywania.  
  
 Dostawca zaufania  
 Oprogramowanie, które decyduje o tym, czy dany plik jest zaufany. Ta decyzja opiera się na certyfikat skojarzony z plikiem.  
  
 Główna nazwa użytkownika (UPN)  
 Nazwa konta użytkownika (czasem nazywane *nazwa logowania użytkownika*) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika. Jest to standardowy używana do logowania do domeny systemu Windows. Format: someone@example.com (podobnie jak w przypadku adresu e-mail).  
  
> [!NOTE]
>  Oprócz standardowego formularza UPN [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] akceptuje nazwy UPN w formie niskiego poziomu, na przykład cohowinery.com\someone.  
  
 X.509  
 Uznanych standard certyfikatów definiujący ich wymagane części.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe pojęcia programu Windows Communication Foundation](../../../../docs/framework/wcf/fundamental-concepts.md)  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
