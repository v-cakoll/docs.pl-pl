---
title: Windows zintegrowane uwierzytelnianie przy użyciu mechanizmu rozszerzonej ochrony
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a78507226b87f005798d0c4824a827a72f1d657a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542768"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Windows zintegrowane uwierzytelnianie przy użyciu mechanizmu rozszerzonej ochrony
Wprowadzono ulepszenia, które wpływają na Windows jak zintegrowane uwierzytelnianie jest obsługiwane przez <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>, i pokrewne klasy w <xref:System.Net> i pokrewnych przestrzeniach nazw. Dodano obsługę ochrony rozszerzonej zwiększyć poziom bezpieczeństwa.  
  
 Te zmiany mogą mieć wpływ na aplikacje, które używają tych klas do żądań sieci web i otrzymywać odpowiedzi, w których jest stosowane zintegrowane uwierzytelnianie Windows. Ta zmiana może także wpłynąć na serwerach sieci web i aplikacji klienckich, które są skonfigurowane do korzystania ze zintegrowanego uwierzytelniania Windows.  
  
 Te zmiany może również wpływać na aplikacje, które używają tych klas na inne typy żądań i otrzymywać odpowiedzi, w których jest stosowane zintegrowane uwierzytelnianie Windows.  
  
 Zmiany do obsługi ochrony rozszerzonej są dostępne tylko dla aplikacji na Windows 7 i Windows Server 2008 R2. Funkcje rozszerzonej ochrony nie są dostępne we wcześniejszych wersjach systemu Windows.  
  
## <a name="overview"></a>Omówienie  
 Projekt zintegrowane uwierzytelnianie Windows umożliwia niektóre odpowiedzi żądania poświadczeń jako uniwersalny, co oznacza, mogą być ponownie używane lub przesyłane dalej. Odpowiedzi na żądania powinien być skonstruowany jako minimum, przy użyciu określonych informacji o docelowej, a najlepiej również niektóre informacje określonego kanału. Usługi mogą udzielić im ochrona rozszerzona, aby upewnić się, że odpowiedzi żądania poświadczeń zawierają usługi szczegółowe informacje, takie jak nazwy głównej nazwy usługi (SPN). Dzięki tym informacjom wymianę poświadczeń usługi mają możliwość zapewnienia lepszej ochrony przed złośliwym korzystaniem z odpowiedzi żądania poświadczeń, które mogą nieprawidłowo używane.  
  
 Projekt ochrony rozszerzonej jest ulepszeniem protokoły uwierzytelniania w celu złagodzenia ataków przekazywania uwierzytelniania. Opiera się funkcjonowanie myślą o kanału i informacje o powiązaniu do usługi.  
  
 Ogólne cele są następujące:  
  
1.  Jeśli klient zostanie zaktualizowany do obsługi ochrony rozszerzonej, aplikacje powinny dostarczyć wiązania kanałów i informacje o powiązaniu usługi na wszystkie protokoły obsługiwane uwierzytelnianie. Informacje o powiązaniu do kanału można podawać tylko po kanału (TLS), aby powiązać. Należy zawsze podać informacje o powiązaniu do usługi.  
  
2.  Zaktualizowane serwery, które są poprawnie skonfigurowane może sprawdzić kanału i informacje o powiązaniu do usługi, gdy nie jest obecny w tokenie uwierzytelniania klienta i odrzucić próby uwierzytelnienia, jeśli powiązania kanału nie są zgodne. W zależności od scenariusza wdrożenia serwerów może zweryfikować powiązania kanału, powiązania usługi lub obu.  
  
3.  Zaktualizowano serwery mają możliwość akceptowanie lub odrzucanie żądań klientów niskiego poziomu, które nie zawierają informacje o powiązaniu kanału, na podstawie zasad.  
  
 Informacje używane przez rozszerzonej ochrony zawiera jeden lub oba z następujących dwóch części:  
  
1.  Kanał powiązanie tokenu lub CBT.  
  
2.  Usługi informacje o powiązaniu w formie główna nazwa usługi lub nazwy SPN.  
  
 Powiązania usługi informacji jest wskazanie celem klienta do uwierzytelniania punktu końcowego określonej usługi. Jest przekazywane z klienta do serwera z następującymi właściwościami:  
  
-   Wartość SPN musi być dostępny serwer uwierzytelniania klienta w postaci zwykłego tekstu.  
  
-   Wartość nazwy SPN jest publiczny.  
  
-   Główna nazwa usługi musi być kryptograficznie chroniona przesyłania taki sposób, że atak typu man-in--middle nie może wstawić, usunąć lub zmodyfikować jego wartość.  
  
 CBT jest właściwością zewnętrznym bezpiecznego kanału (np. TLS) umożliwia powiązanie (bind) do konwersacji za pośrednictwem kanału wewnętrznej, uwierzytelniane przez klienta. CBT musi mieć następujące właściwości (także definicją IETF RFC 5056):  
  
-   Jeśli kanał zewnętrznego istnieje, wartość CBT musi być właściwością identyfikowania zewnętrzne kanału lub punkt końcowy serwera, niezależnie od siebie dotarły przez klienta i serwera strony w konwersacji.  
  
-   Wartość CBT wysłane przez klienta nie może być coś, co osoba atakująca może mieć wpływ.  
  
-   O tajemnicy wartość CBT stają się żadnych gwarancji. Nie jednak oznacza to, że wartość powiązania usługi, a także informacje o powiązaniu kanału zawsze można sprawdzić przez każdy inny, ale serwer uwierzytelniania, jako protokół wykonywania CBT może zaszyfrowanie go.  
  
-   CBT musi być kryptograficznie integralności chronionych podczas przesyłania w taki sposób, że osoba atakująca nie może wstawić, usunąć lub zmodyfikować jego wartość.  
  
 Powiązania kanału odbywa się przez klienta, przesłanie główną nazwę usługi i CBT serwera w sposób tamperproof. Serwer sprawdza informacje o powiązaniu kanału zgodnie z ich zasadami i odrzuca próby uwierzytelnienia, dla których ona nie uważa się zostały zamierzonym obiektem docelowym. W ten sposób dwa kanały kryptograficznie stają się ze sobą powiązane.  
  
 Aby zachować zgodność z istniejącymi klientami i aplikacjami, serwer może być skonfigurowane i umożliwiają prób uwierzytelnienia przez klientów, którzy jeszcze nie obsługuje ochrony rozszerzonej. Jest to określane jako "chroniony częściowo" Konfiguracja, w przeciwieństwie do konfiguracji "chroniony w pełni".  
  
 Wiele składników w <xref:System.Net> i <xref:System.Net.Security> przestrzenie nazw wykonać zintegrowane uwierzytelnianie Windows w imieniu aplikacji wywołującej. W tej sekcji opisano zmiany w przestrzeni nazw System.Net składników można dodawać ochronę rozszerzoną ich używane zintegrowane uwierzytelnianie Windows.  
  
 Rozszerzona ochrona jest obecnie obsługiwane w systemie Windows 7. Mechanizm jest dostarczany, aby aplikacji można określić, czy system operacyjny obsługuje ochrony rozszerzonej.  
  
## <a name="changes-to-support-extended-protection"></a>Zmiany do obsługi ochrony rozszerzonej  
 Proces uwierzytelniania używany przy użyciu zintegrowanego uwierzytelniania Windows, w zależności od protokołu uwierzytelniania używane, często obejmuje wyzwanie wystawiony przez komputer docelowy i wysyłane z powrotem do komputera klienckiego. Ochrona rozszerzona dodaje nowe funkcje do tego procesu uwierzytelniania  
  
 <xref:System.Security.Authentication.ExtendedProtection> Przestrzeń nazw zapewnia obsługę uwierzytelniania przy użyciu mechanizmu rozszerzonej ochrony aplikacji. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> Klasy w tej przestrzeni nazw reprezentuje wiązania kanałów. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Klasy w tej przestrzeni nazw reprezentuje zasady ochrony rozszerzonej używane przez serwer do weryfikowania przychodzących połączeń klienta. Innych składowych klasy są używane z ochroną rozszerzoną.  
  
 Dla aplikacji serwera w ramach tych zajęć są następujące:  
  
 Element <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zawierający następujące elementy:  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> Właściwość, która wskazuje, czy system operacyjny obsługuje zintegrowane uwierzytelnianie systemu windows przy użyciu mechanizmu rozszerzonej ochrony.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> wartość, która wskazuje, kiedy należy wymusić zasady ochrony rozszerzonej.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> wartość, która wskazuje scenariusza wdrażania. Wpływ na sposób Rozszerzona ochrona jest zaznaczone.  
  
-   Opcjonalny <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> zawierający listy niestandardowej nazwy SPN, który jest używany do dopasowywania główną nazwę usługi udostępniane przez klienta jako docelową uwierzytelniania.  
  
-   Opcjonalny <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> zawierający powiązanie niestandardowy kanał do użycia w celu weryfikacji. Ten scenariusz nie jest często zdarza  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> Przestrzeń nazw zapewnia obsługę dla konfiguracji uwierzytelniania przy użyciu mechanizmu rozszerzonej ochrony aplikacji.  
  
 Wprowadzono szereg zmian funkcji do obsługi ochrony rozszerzonej w istniejącym <xref:System.Net> przestrzeni nazw. Te zmiany są następujące:  
  
-   Nowy <xref:System.Net.TransportContext> dodawane do klasy <xref:System.Net> przestrzeni nazw, który reprezentuje kontekst transportu.  
  
-   Nowe <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> i <xref:System.Net.HttpWebRequest.GetRequestStream%2A> przeciążenia metody <xref:System.Net.HttpWebRequest> klasę, która umożliwia pobieranie <xref:System.Net.TransportContext> do obsługi ochrony rozszerzonej dla aplikacji klienckich.  
  
-   Dodatki do <xref:System.Net.HttpListener> i <xref:System.Net.HttpListenerRequest> klasy, aby umożliwić obsługę aplikacji serwera.  
  
 Funkcja zmiany do obsługi ochrony rozszerzonej dla aplikacji klienckich SMTP w istniejącym <xref:System.Net.Mail> przestrzeni nazw:  
  
-   A <xref:System.Net.Mail.SmtpClient.TargetName%2A> właściwość <xref:System.Net.Mail.SmtpClient> klasa, która reprezentuje nazwę SPN można używać do uwierzytelniania w przypadku korzystania z rozszerzonej ochrony klienta SMTP aplikacji.  
  
 Wprowadzono szereg zmian funkcji do obsługi ochrony rozszerzonej w istniejącym <xref:System.Net.Security> przestrzeni nazw. Te zmiany są następujące:  
  
-   Nowe <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> i <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> przeciążenia metody <xref:System.Net.Security.NegotiateStream> klasę, która będzie zezwalać na przekazywanie CBT do obsługi ochrony rozszerzonej dla aplikacji klienckich.  
  
-   Nowe <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> i <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> przeciążenia metody <xref:System.Net.Security.NegotiateStream> klasę, która zezwalanie na przekazywanie <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> do obsługi ochrony rozszerzonej dla aplikacji serwerowych.  
  
-   Nowy <xref:System.Net.Security.SslStream.TransportContext%2A> właściwość <xref:System.Net.Security.SslStream> klasy do obsługi ochrony rozszerzonej dla klienta i serwera aplikacji.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement> właściwość została dodana do obsługi konfiguracji ochrony rozszerzonej dla klientów SMTP w <xref:System.Net.Security> przestrzeni nazw.  
  
## <a name="extended-protection-for-client-applications"></a>Ochrona rozszerzona na potrzeby aplikacji klienckich  
 Ochrona rozszerzona obsługa większości aplikacji klienckich odbywa się automatycznie. <xref:System.Net.HttpWebRequest> i <xref:System.Net.Mail.SmtpClient> klasy obsługi ochrony rozszerzonej zawsze wtedy, gdy podstawowy wersję Windows obsługuje ochrony rozszerzonej. <xref:System.Net.HttpWebRequest> Wystąpienia wysyła nazwę SPN skonstruowany na podstawie <xref:System.Uri>. Domyślnie <xref:System.Net.Mail.SmtpClient> wystąpienia wysyła nazwę SPN zbudowane na podstawie nazwy hosta serwera poczty SMTP.  
  
 Niestandardowe aplikacje klienckie mogą używać, <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> lub <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> metody <xref:System.Net.HttpWebRequest> klasę, która umożliwia pobieranie <xref:System.Net.TransportContext> i używanie CBT <xref:System.Net.TransportContext.GetChannelBinding%2A> metody.  
  
 Nazwy SPN na potrzeby zintegrowane uwierzytelnianie Windows wysyłane przez <xref:System.Net.HttpWebRequest> wystąpienie danej usługi, mogą zostać zastąpione przez ustawienie <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> właściwości.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> Właściwość można ustawić niestandardowe nazwy SPN na potrzeby zintegrowane uwierzytelnianie Windows dla połączenia protokołu SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Ochrona rozszerzona na potrzeby aplikacji serwera  
 <xref:System.Net.HttpListener> automatycznie zapewnia mechanizmy sprawdzania poprawności powiązania usługi podczas przeprowadzania uwierzytelniania HTTP.  
  
 Najbezpieczniejszą scenariusz jest ochrona rozszerzona na potrzeby prefiksy HTTPS://. W takim przypadku ustawić <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> do <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> z <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> równa <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, i <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> równa <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> wartość <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> umieszcza <xref:System.Net.HttpListener> w trybie chroniony częściowo podczas <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odnosi się do w pełni zaostrzony tryb.  
  
 W tej konfiguracji po wysłaniu żądania do serwera przy użyciu zewnętrznym bezpiecznego kanału channel zewnętrzne zostaje przesłane zapytanie wiązania kanałów. Tego powiązania kanału jest przekazywany do wywołania interfejsu SSPI uwierzytelniania, których sprawdzanie poprawności, które powiązania kanału dopasowanie blob uwierzytelniania w. Istnieją trzy możliwe wyniki:  
  
1.  System operacyjny serwera nie obsługuje ochrony rozszerzonej. Żądanie nie będzie widoczna dla aplikacji, a odpowiedź (401) nieautoryzowane zostanie zwrócony do klienta. Komunikat zostaną zarejestrowane <xref:System.Net.HttpListener> źródła śledzenia, określania przyczyny niepowodzenia.  
  
2.  Wywołania interfejsu SSPI nie powiodło się wskazujący, że klient określono powiązania kanału, który nie odpowiada oczekiwanej wartości pobierane z zewnętrznych kanału lub klient nie może dostarczyć powiązania kanału, gdy skonfigurowano zasady ochrony rozszerzonej na serwerze Aby uzyskać <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>. W obu przypadkach żądanie, nie będzie ona widoczna dla aplikacji, a odpowiedź (401) nieautoryzowane zostanie zwrócony do klienta. Komunikat zostaną zarejestrowane <xref:System.Net.HttpListener> źródła śledzenia, określania przyczyny niepowodzenia.  
  
3.  Klient określa powiązania w poprawnym kanale lub może nawiązać połączenie bez określenia powiązania kanału, ponieważ zasady ochrony rozszerzonej na serwerze jest skonfigurowany przy użyciu <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> żądania jest zwracana do aplikacji w celu przetworzenia. Nie wyboru nazwa usługi jest realizowane automatycznie. Aplikacja może wybrać do wykonania własnej usługi nazwa weryfikacji za pomocą <xref:System.Net.HttpListenerRequest.ServiceName%2A> właściwości, ale w poniższych sytuacjach jest nadmiarowe.  
  
 Jeśli aplikacja sprawia, że jego własnej wywołania interfejsu SSPI, aby przeprowadzać uwierzytelnianie oparte na obiekty BLOB przekazane i z powrotem w treści żądania HTTP i chce obsługiwać powiązania kanału, musi pobrać wiązania kanałów oczekiwanych z zewnętrznym bezpiecznego kanału, za pomocą <xref:System.Net.HttpListener> aby można było przekazać go do natywnego Win32 [działanie funkcji AcceptSecurityContext](https://go.microsoft.com/fwlink/?LinkId=147021) funkcji. Aby to zrobić, należy użyć <xref:System.Net.HttpListenerRequest.TransportContext%2A> właściwości i wywołania <xref:System.Net.TransportContext.GetChannelBinding%2A> metodę, która pobierze CBT. Obsługiwane są tylko powiązania punktu końcowego. Jeśli niczego poza <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> jest określony, <xref:System.NotSupportedException> zostanie zgłoszony. Jeśli system operacyjny obsługuje wiązania kanałów <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda zwróci <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> zawijania wskaźnik do powiązania odpowiedni do przekazania do kanału [działanie funkcji AcceptSecurityContext](https://go.microsoft.com/fwlink/?LinkId=147021) — funkcja jako pvBuffer członka struktury SecBuffer przekazanej `pInput` parametru. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> Właściwość zawiera długość w bajtach, powiązania kanału. Jeśli system operacyjny nie obsługuje powiązań kanałów, funkcja zwróci `null`.  
  
 Inny scenariusz możliwe jest ochrona rozszerzona na potrzeby prefiksy HTTP://, gdy serwery proxy nie są używane. W takim przypadku ustawić <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> do <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> z <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> równa <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, i <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> równa <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> wartość <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> umieszcza <xref:System.Net.HttpListener> w trybie chroniony częściowo podczas <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odnosi się do w pełni zaostrzony tryb.  
  
 Domyślną listę dozwolonych usługi nazw jest oparta na prefiksy, które zostały zarejestrowane przy użyciu <xref:System.Net.HttpListener>. Ta lista domyślne można zbadać za pomocą <xref:System.Net.HttpListener.DefaultServiceNames%2A> właściwości. Jeśli ta lista nie jest wyczerpująca, aplikacja może określić kolekcję usługa niestandardowa nazwa w Konstruktorze <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> klasy, które będą używane zamiast domyślnej listy nazw usług.  
  
 W tej konfiguracji po wysłaniu żądania do serwera bez zewnętrznym bezpiecznego uwierzytelniania kanału przetwarzane w zwykły sposób bez powiązania wyboru kanału. Jeśli uwierzytelnianie zakończy się powodzeniem, kontekst zostaje przesłane zapytanie dla nazwy usługi, czy klient podane, a następnie weryfikowany pod kątem listy nazw usług dopuszczalne. Istnieją cztery możliwe wyniki:  
  
1.  System operacyjny serwera nie obsługuje ochrony rozszerzonej. Żądanie nie będzie widoczna dla aplikacji, a odpowiedź (401) nieautoryzowane zostanie zwrócony do klienta. Komunikat zostaną zarejestrowane <xref:System.Net.HttpListener> źródła śledzenia, określania przyczyny niepowodzenia.  
  
2.  System operacyjny klienta nie obsługuje ochrony rozszerzonej. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfigurację, próba uwierzytelnienia zostanie wykonane pomyślnie i żądania, które zostaną zwrócone do aplikacji. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfiguracji, próba uwierzytelnienia nie powiedzie się. Żądanie nie będzie widoczna dla aplikacji, a odpowiedź (401) nieautoryzowane zostanie zwrócony do klienta. Komunikat zostaną zarejestrowane <xref:System.Net.HttpListener> źródła śledzenia, określania przyczyny niepowodzenia.  
  
3.  System operacyjny klienta obsługuje rozszerzonej ochrony, ale aplikacja nie określiła powiązania usługi. Żądanie nie będzie widoczna dla aplikacji, a odpowiedź (401) nieautoryzowane zostanie zwrócony do klienta. Komunikat zostaną zarejestrowane <xref:System.Net.HttpListener> źródła śledzenia, określania przyczyny niepowodzenia.  
  
4.  Klient określone powiązanie usługi. Powiązanie usługi jest porównywana do listy dozwolonych powiązania. Jeśli jest zgodny, żądanie jest zwracana do aplikacji. W przeciwnym razie nie zostaną ujawnione żądania do aplikacji i odpowiedź (401) nieautoryzowane zostanie automatycznie przywrócony do klienta. Komunikat zostaną zarejestrowane <xref:System.Net.HttpListener> źródła śledzenia, określania przyczyny niepowodzenia.  
  
 Jeśli to proste podejście przy użyciu listy dozwolonych dla nazwy usługi dopuszczalne jest niewystarczająca, aplikacja może podać swój własny sprawdzanie poprawności nazwy usługi, badając <xref:System.Net.HttpListenerRequest.ServiceName%2A> właściwości. W przypadku 1 i 2 powyżej, zwróci właściwość `null`. W przypadku, gdy 3, zwróci pusty ciąg. W przypadku, gdy 4, zostaną zwrócone z nazwą usługi określoną przez klienta.  
  
 Te funkcje ochrony rozszerzonej mogą również przez aplikacje serwera do uwierzytelniania przy użyciu innych typów żądań i użycie zaufanych serwerów proxy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Authentication.ExtendedProtection>  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>
