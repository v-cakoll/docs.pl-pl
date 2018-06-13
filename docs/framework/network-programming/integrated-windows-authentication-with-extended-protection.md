---
title: Zintegrowane uwierzytelnianie systemu Windows z ochrony rozszerzonej
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 88170162e4149580d532129666348d226540aced
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398134"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Zintegrowane uwierzytelnianie systemu Windows z ochrony rozszerzonej
Wprowadzono ulepszenia, które mają wpływ na sposób zintegrowane z systemem Windows uwierzytelnianie jest obsługiwane przez <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Mail.SmtpClient>, <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>, i powiązanych klas w <xref:System.Net> i związanych z przestrzeni nazw. Dodano obsługę ochrony rozszerzonej zwiększyć bezpieczeństwo.  
  
 Te zmiany mogą wpłynąć na aplikacji, które używają tych klas do żądań sieci web i odbierania odpowiedzi, gdzie jest używane zintegrowane uwierzytelnianie systemu Windows. Ta zmiana może wpłynąć na serwery sieci web i aplikacji klienckich, które są skonfigurowane do korzystania ze zintegrowanego uwierzytelniania systemu Windows.  
  
 Te zmiany mogą wpłynąć na aplikacji, które używają tych klas inne rodzaje żądań i odbierania odpowiedzi, gdzie jest używane zintegrowane uwierzytelnianie systemu Windows.  
  
 Zmiany do obsługi ochrony rozszerzonej są dostępne tylko dla aplikacji w systemie Windows 7 i Windows Server 2008 R2. Funkcje ochrony rozszerzonej nie są dostępne w starszych wersjach systemu Windows.  
  
## <a name="overview"></a>Omówienie  
 Projekt zintegrowane uwierzytelnianie systemu Windows umożliwia niektóre odpowiedzi żądania poświadczeń jako uniwersalny, czyli może być ponownie używane lub przesyłane dalej. Odpowiedzi na żądanie należy konstruować co najmniej z informacjami o określonych docelowych, najlepiej również pewne informacje określonego kanału. Usługi mogą udzielić im ochrona rozszerzona, aby upewnić się, że poświadczenia odpowiedzi na żądanie zawiera usługi określone informacje takie jak nazwy usługi (SPN). Dzięki tym informacjom wymiany poświadczeń usługi będą mogli lepiej chronić przed atakami odpowiedzi żądania poświadczeń, które może być niepoprawnie użyte.  
  
 Projekt ochrony rozszerzonej jest ulepszeniem protokoły uwierzytelniania w celu złagodzenia ataków przekazywania uwierzytelniania. Dotyczy on tego pojęcie kanału i informacje o powiązaniu usługi.  
  
 Ogólnych celów są następujące:  
  
1.  Jeśli klient zostanie zaktualizowany do obsługi ochrony rozszerzonej, aplikacje powinny dostarczyć wiązania kanałów i informacje o powiązaniu usługi do wszystkich protokołów uwierzytelniania obsługiwanych. Informacje o powiązaniu kanału można podać tylko po kanał (TLS), aby powiązać. Informacje o powiązaniu usługi należy zawsze podać.  
  
2.  Zaktualizowano serwerów, które są prawidłowo skonfigurowane i mogą Sprawdź kanału i informacje o powiązaniu usługi, gdy nie jest obecny w tokenie uwierzytelniania klienta i Odrzuć próby uwierzytelnienia, jeśli powiązania kanału nie są zgodne. W zależności od scenariusza wdrażania serwerów mogą sprawdzić powiązania kanałów, powiązania usługi lub oba.  
  
3.  Zaktualizowano serwery mają możliwość akceptowanie lub odrzucanie żądań klientów niskiego poziomu, które nie zawierają informacje o powiązaniu kanału, na podstawie zasad.  
  
 Informacje używane przez ochrona rozszerzona składa się z co najmniej jednej z następujących dwóch części:  
  
1.  Powiązanie tokenu kanału lub CBT.  
  
2.  Informacje o powiązaniu w postaci główna nazwa usługi lub nazwa SPN usług.  
  
 Powiązania usługi informacji jest oznaczenie założeń klienta do uwierzytelniania dla określonego punktu końcowego. Przesyłane z klienta do serwera z następującymi właściwościami:  
  
-   Wartość Nazwa SPN musi być dostępny dla serwera uwierzytelniania klienta w postaci zwykłego tekstu.  
  
-   Wartość nazwy SPN jest publiczny.  
  
-   Nazwa SPN muszą być kryptograficznie chronione przesyłania taki sposób, że atak typu man-in--middle nie może wstawić, usunąć lub zmodyfikować jego wartość.  
  
 CBT jest właściwością zewnętrznym bezpiecznego kanału (na przykład TLS) używane do powiązania (bind) do konwersacji za pośrednictwem kanału wewnętrznej, uwierzytelniane przez klienta. CBT musi mieć następujące właściwości (również zdefiniowany przez organizację IETF RFC 5056):  
  
-   Gdy kanał zewnętrznego istnieje, wartość CBT musi być właściwością identyfikowania zewnętrzne kanału lub serwera punktu końcowego, niezależnie dotarły przez klienta i serwera strony konwersacji.  
  
-   Wartość CBT wysłane przez klienta nie może być coś, które osoba atakująca może mieć wpływ.  
  
-   O tajemnicy wartości CBT nie zajdą żadnych gwarancji. Jednak to oznacza, że wartość powiązania usługi, a także informacje o powiązaniu kanału można zawsze badane przez innych, ale serwer uwierzytelniania, jako protokół wykonywania CBT może zaszyfrowanie go.  
  
-   CBT musi być kryptograficznie integralności chronione podczas przesyłania w taki sposób, że osoba atakująca nie może wstawić, usunąć lub zmodyfikować jego wartość.  
  
 Powiązania kanałów odbywa się przez klienta przesłanie główną nazwę usługi i CBT w sposób tamperproof do serwera. Serwer sprawdza informacje o powiązaniu kanału zgodnie z jego zasad i odrzuca próby uwierzytelnienia, dla których go nie uważa, aby były docelową. W ten sposób dwa kanały kryptograficznie stają się ze sobą powiązane.  
  
 Aby zachować zgodność z istniejących klientów i aplikacji, serwer może być skonfigurowane i umożliwiają prób uwierzytelnienia przez klientów, którzy jeszcze nie obsługuje ochrony rozszerzonej. Jest to określane jako "chroniony częściowo" Konfiguracja, w przeciwieństwie do "chroniony w pełni" konfiguracji.  
  
 Wiele składników w <xref:System.Net> i <xref:System.Net.Security> przestrzenie nazw wykonać zintegrowane uwierzytelnianie systemu Windows w imieniu aplikacji wywołującej. W tej sekcji opisano zmiany System.Net składników, aby dodać ochrona rozszerzona w ich używania zintegrowanego uwierzytelniania systemu Windows.  
  
 Ochrona rozszerzona jest obecnie obsługiwany w systemie Windows 7. Mechanizm jest zapewniana dzięki aplikacji można określić, czy system operacyjny obsługuje rozszerzonej ochrony.  
  
## <a name="changes-to-support-extended-protection"></a>Zmiany do obsługi ochrony rozszerzonej  
 Proces uwierzytelniania używane z zintegrowane uwierzytelnianie systemu Windows, w zależności od protokołu uwierzytelniania używane, często obejmuje żądanie wystawiony przez komputer docelowy, a następnie wysyłane z powrotem do komputera klienckiego. Ochrona rozszerzona dodaje nowe funkcje do tego procesu uwierzytelniania  
  
 <xref:System.Security.Authentication.ExtendedProtection> Przestrzeń nazw zapewnia obsługę uwierzytelniania przy użyciu ochrony rozszerzonej dla aplikacji. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> Klasy w tej przestrzeni nazw reprezentuje powiązania kanałów. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> Klasy w tej przestrzeni nazw reprezentuje zasada ochrony rozszerzonej używana przez serwer do walidacji przychodzących połączeń klientów. O innych elementach członkowskich klasy są używane z ochrony rozszerzonej.  
  
 Dla aplikacji serwerowych tych klas są następujące:  
  
 A <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> mający następujące elementy:  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> Właściwość, która wskazuje, czy system operacyjny obsługuje zintegrowane uwierzytelnianie systemu windows z ochrony rozszerzonej.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> wartość, która wskazuje, kiedy należy wymusić zasady ochrony rozszerzonej.  
  
-   A <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> wartość, która wskazuje scenariusz wdrażania. Ma to wpływ na sposób rozszerzonej ochrony jest zaznaczony.  
  
-   Opcjonalny <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> zawierający listę nazw SPN niestandardową jest używany do dopasowywania SPN dostarczonych przez klienta jako docelową uwierzytelniania.  
  
-   Opcjonalny <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> zawiera powiązanie niestandardowego kanału do użycia w celu weryfikacji. Ten scenariusz nie jest często zdarza  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> Przestrzeń nazw zapewnia obsługę konfiguracji uwierzytelniania za pomocą ochrony rozszerzonej dla aplikacji.  
  
 Wprowadzono szereg funkcji zmiany do obsługi ochrony rozszerzonej w istniejących <xref:System.Net> przestrzeni nazw. Następujące zmiany:  
  
-   Nowy <xref:System.Net.TransportContext> dodany do klasy <xref:System.Net> przestrzeni nazw, która reprezentuje kontekst transportu.  
  
-   Nowy <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> i <xref:System.Net.HttpWebRequest.GetRequestStream%2A> przeciążanie metod w <xref:System.Net.HttpWebRequest> klasy, która umożliwia pobieranie <xref:System.Net.TransportContext> do obsługi ochrony rozszerzonej dla aplikacji klienckich.  
  
-   Dodatki do <xref:System.Net.HttpListener> i <xref:System.Net.HttpListenerRequest> klasy do obsługi aplikacji serwera.  
  
 Funkcja zmiany do obsługi ochrony rozszerzonej dla aplikacji klienckich SMTP w istniejących <xref:System.Net.Mail> przestrzeni nazw:  
  
-   A <xref:System.Net.Mail.SmtpClient.TargetName%2A> właściwości w <xref:System.Net.Mail.SmtpClient> klasa, która reprezentuje nazwę SPN, aby używać do uwierzytelniania w przypadku korzystania z rozszerzonej ochrony klienta SMTP aplikacji.  
  
 Wprowadzono szereg funkcji zmiany do obsługi ochrony rozszerzonej w istniejących <xref:System.Net.Security> przestrzeni nazw. Następujące zmiany:  
  
-   Nowy <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> i <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> przeciążenia metody <xref:System.Net.Security.NegotiateStream> klasy, która umożliwia przekazywanie CBT do obsługi ochrony rozszerzonej dla aplikacji klienckich.  
  
-   Nowy <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> i <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> przeciążanie metod w <xref:System.Net.Security.NegotiateStream> klasy, która umożliwia przekazywanie <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> do obsługi ochrony rozszerzonej dla aplikacji serwera.  
  
-   Nowy <xref:System.Net.Security.SslStream.TransportContext%2A> właściwości w <xref:System.Net.Security.SslStream> klasy do obsługi ochrony rozszerzonej dla klienta i serwera aplikacji.  
  
 A <xref:System.Net.Configuration.SmtpNetworkElement> właściwość została dodana do obsługi konfiguracji ochrony rozszerzonej dla klientów SMTP w <xref:System.Net.Security> przestrzeni nazw.  
  
## <a name="extended-protection-for-client-applications"></a>Ochrona rozszerzona na potrzeby aplikacji klienckich  
 Ochrona rozszerzona obsługa większości aplikacji klienckich odbywa się automatycznie. <xref:System.Net.HttpWebRequest> i <xref:System.Net.Mail.SmtpClient> klasy obsługuje rozszerzonej ochrony, gdy podstawowej wersji systemu Windows obsługuje rozszerzonej ochrony. <xref:System.Net.HttpWebRequest> Wystąpienia wysyła nazwę SPN utworzone na podstawie <xref:System.Uri>. Domyślnie <xref:System.Net.Mail.SmtpClient> wystąpienia wysyła nazwę SPN utworzone na podstawie nazwy hosta serwera poczty SMTP.  
  
 Niestandardowe aplikacje klienckie mogą używać, <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> lub <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> metod w <xref:System.Net.HttpWebRequest> klasy, która umożliwia pobieranie <xref:System.Net.TransportContext> i używanie CBT <xref:System.Net.TransportContext.GetChannelBinding%2A> metody.  
  
 Nazwę SPN, aby używać zintegrowanego uwierzytelniania systemu Windows, wysyłane przez <xref:System.Net.HttpWebRequest> wystąpienie danej usługi może zostać zastąpione przez ustawienie <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> właściwości.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> Właściwości można ustawić niestandardowe nazwę SPN, aby używać zintegrowanego uwierzytelniania systemu Windows dla połączeń SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Ochrona rozszerzona na potrzeby aplikacji serwera  
 <xref:System.Net.HttpListener> automatycznie zapewnia mechanizmów sprawdzania poprawności powiązania, przeprowadzania uwierzytelniania HTTP.  
  
 Najbezpieczniejszą scenariusz jest umożliwienie ochrona rozszerzona na potrzeby prefiksy HTTPS://. W takim przypadku należy ustawić <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> do <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> z <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> ustawioną <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, i <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> ustawioną <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> wartość <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> umieszcza <xref:System.Net.HttpListener> w trybie zaostrzonym częściowo podczas <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpowiada pełni zaostrzony tryb.  
  
 W tej konfiguracji po wysłaniu żądania do serwera za pośrednictwem bezpiecznego kanału zewnętrzne zewnętrzne kanału zostanie zapytany o powiązania kanałów. Tego powiązania kanału jest przekazywany do wywołania interfejsu SSPI uwierzytelniania, których sprawdzanie poprawności, które powiązania kanałów w dopasowań blob uwierzytelniania. Istnieją trzy możliwe wyniki:  
  
1.  System operacyjny serwera nie obsługuje ochrony rozszerzonej. Żądanie nie będzie ona widoczna dla aplikacji, a nieautoryzowanego odpowiedzi (401) zostanie zwrócony do klienta. Wiadomości są rejestrowane <xref:System.Net.HttpListener> źródło śladu Określanie przyczynę błędu.  
  
2.  Wywołanie SSPI nie powiedzie się wskazującą, czy klient określono powiązania kanału, który nie odpowiada oczekiwanej wartości pobierane z zewnętrznego kanału lub klient nie może dostarczyć powiązanie kanału, gdy skonfigurowano zasady ochrony rozszerzonej na serwerze Aby uzyskać <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>. W obu przypadkach żądania nie będzie ona widoczna dla aplikacji, a odpowiedź (401) nieautoryzowane zostanie zwrócony do klienta. Wiadomości są rejestrowane <xref:System.Net.HttpListener> źródło śladu Określanie przyczynę błędu.  
  
3.  Klient określa powiązania kanałów poprawne lub może nawiązać połączenie bez określenia powiązania kanału, ponieważ zasada ochrony rozszerzonej na serwerze skonfigurowano <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> żądania jest zwracana do aplikacji w celu przetwarzania. Bez sprawdzania nazwy usługi odbywa się automatycznie. Aplikacji może wybrać przeprowadzić własne usługi nazwa weryfikacji przy użyciu <xref:System.Net.HttpListenerRequest.ServiceName%2A> właściwości, ale w tych warunkach jest nadmiarowy.  
  
 Jeśli aplikacja sprawia, że jego własnej wywołania interfejsu SSPI, aby wykonać uwierzytelnianie oparte na obiekty BLOB i z powrotem przekazany w treści żądania HTTP i chce obsługuje powiązań kanałów, należy go pobrać powiązania kanałów oczekiwanego z zewnętrznym bezpiecznego kanału, za pomocą <xref:System.Net.HttpListener> aby przekazywanie ich do natywnego Win32 [działanie funkcji AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) funkcji. Aby to zrobić, użyj <xref:System.Net.HttpListenerRequest.TransportContext%2A> właściwości i wywołanie <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda pobierania CBT. Są obsługiwane tylko powiązania punktu końcowego. Jeśli wszystko inne <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> jest określony, <xref:System.NotSupportedException> zostanie wygenerowany. Jeśli system operacyjny obsługuje powiązania kanałów <xref:System.Net.TransportContext.GetChannelBinding%2A> metoda zwróci <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> zawijania wskaźnik do powiązania odpowiednie do przekazania do kanału [działanie funkcji AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) — funkcja jako pvBuffer elementu członkowskiego struktury SecBuffer przekazano `pInput` parametru. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> Właściwość zawiera długość w bajtach powiązania kanałów. Jeśli system operacyjny nie obsługuje powiązań kanałów, funkcja zwróci `null`.  
  
 Inny możliwy scenariusz jest umożliwienie ochrona rozszerzona na potrzeby prefiksy HTTP://, gdy serwery proxy nie są używane. W takim przypadku należy ustawić <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> do <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> z <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> ustawioną <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>, i <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> ustawioną <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> wartość <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> umieszcza <xref:System.Net.HttpListener> w trybie zaostrzonym częściowo podczas <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpowiada pełni zaostrzony tryb.  
  
 Domyślną listę nazw usług dozwolonych jest tworzone w oparciu prefiksów, które zostały zarejestrowane w <xref:System.Net.HttpListener>. Ta lista domyślne można zbadać za pomocą <xref:System.Net.HttpListener.DefaultServiceNames%2A> właściwości. Jeśli ta lista nie jest wyczerpująca, aplikację można określić Kolekcja nazw usług niestandardowych w Konstruktorze <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> klasy, która będzie używana zamiast domyślnej listy nazwy usługi.  
  
 W tej konfiguracji po wysłaniu żądania do serwera bez zewnętrznym bezpiecznego uwierzytelniania kanału przetwarzane w zwykły sposób bez sprawdzania powiązania kanałów. Jeśli uwierzytelnianie się powiedzie, kontekst zostanie zapytany o nazwę usługi, że klient podane ani weryfikowana pod kątem lista akceptowalnych nazw usług. Istnieją cztery możliwe wyniki:  
  
1.  System operacyjny serwera nie obsługuje ochrony rozszerzonej. Żądanie nie będzie ona widoczna dla aplikacji, a nieautoryzowanego odpowiedzi (401) zostanie zwrócony do klienta. Wiadomości są rejestrowane <xref:System.Net.HttpListener> źródło śladu Określanie przyczynę błędu.  
  
2.  System operacyjny klienta nie obsługuje ochrony rozszerzonej. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfiguracji, próba uwierzytelniania powiedzie się i żądanie zostanie zwrócony do aplikacji. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfiguracji, uwierzytelnianie nie powiedzie się. Żądanie nie będzie ona widoczna dla aplikacji, a nieautoryzowanego odpowiedzi (401) zostanie zwrócony do klienta. Wiadomości są rejestrowane <xref:System.Net.HttpListener> źródło śladu Określanie przyczynę błędu.  
  
3.  System operacyjny klienta obsługuje rozszerzonej ochrony, ale nie określono powiązania usługi aplikacji. Żądanie nie będzie ona widoczna dla aplikacji, a nieautoryzowanego odpowiedzi (401) zostanie zwrócony do klienta. Wiadomości są rejestrowane <xref:System.Net.HttpListener> źródło śladu Określanie przyczynę błędu.  
  
4.  Klient określone powiązanie usługi. Powiązanie usługi jest porównywany do listy dozwolonych powiązania. Jeśli jest on zgodny, żądanie jest zwracana do aplikacji. W przeciwnym razie żądania nie będzie ona widoczna dla aplikacji i nieautoryzowanym odpowiedzi (401) automatycznie powróci do klienta. Wiadomości są rejestrowane <xref:System.Net.HttpListener> źródło śladu Określanie przyczynę błędu.  
  
 Jeśli takie podejście proste za pomocą listy dozwolonych akceptowalnych nazw usług jest niewystarczająca, aplikacja może dostarcza własną Sprawdzanie nazwy usługi badając <xref:System.Net.HttpListenerRequest.ServiceName%2A> właściwości. W przypadku 1 i 2. powyżej, właściwość, którą będzie zwracać `null`. W przypadku 3 zwróci ciąg pusty. W przypadku 4 zostanie zwrócony z nazwą usługi określoną przez klienta.  
  
 Te funkcje ochrony rozszerzonej mogą również przez aplikacje serwera do uwierzytelniania przy użyciu innych typów żądań i zaufanych serwerów proxy są używane.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Authentication.ExtendedProtection>  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>
