---
title: Zintegrowane uwierzytelnianie systemu Windows z ochroną rozszerzoną
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: d69471f4be0f102381dee4fc5037e8f8b0c625c3
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144854"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Zintegrowane uwierzytelnianie systemu Windows z ochroną rozszerzoną
Wprowadzono ulepszenia, które mają wpływ na sposób obsługi zintegrowanego uwierzytelniania systemu Windows przez <xref:System.Net.HttpWebRequest> klasy,,, <xref:System.Net.HttpListener> <xref:System.Net.Mail.SmtpClient> <xref:System.Net.Security.SslStream> <xref:System.Net.Security.NegotiateStream> i powiązane, w <xref:System.Net> i powiązanych przestrzeniach nazw. Dodano obsługę rozszerzonej ochrony w celu zwiększenia bezpieczeństwa.  
  
 Te zmiany mogą mieć wpływ na aplikacje, które używają tych klas do żądania sieci Web i uzyskiwania odpowiedzi w przypadku używania zintegrowanego uwierzytelniania systemu Windows. Ta zmiana może również mieć wpływ na serwery sieci Web i aplikacje klienckie, które są skonfigurowane do korzystania ze zintegrowanego uwierzytelniania systemu Windows.  
  
 Te zmiany mogą również wpływać na aplikacje, które używają tych klas do podejmowania innych typów żądań i odbierać odpowiedzi, w przypadku których używane jest zintegrowane uwierzytelnianie systemu Windows.  
  
 Zmiany w celu obsługi ochrony rozszerzonej są dostępne tylko dla aplikacji w systemach Windows 7 i Windows Server 2008 R2. Funkcje ochrony rozszerzonej nie są dostępne we wcześniejszych wersjach systemu Windows.  
  
## <a name="overview"></a>Omówienie  
 Projektowanie zintegrowanego uwierzytelniania systemu Windows pozwala na uniwersalne odpowiedzi na żądania poświadczeń, co oznacza, że mogą być ponownie używane lub przekazywane. Odpowiedzi na wezwanie powinny być zbudowane co najmniej z konkretnymi informacjami docelowymi, a najlepiej z pewnymi informacjami specyficznymi dla kanału. Następnie usługi mogą zapewnić ochronę rozszerzoną w celu zapewnienia, że odpowiedzi na wezwania na żądania zawierają informacje specyficzne dla usługi, takie jak główna nazwa usługi (SPN). Dzięki tym informacjom w wymianie poświadczeń usługi są w stanie lepiej chronić przed złośliwym użyciem odpowiedzi na wyzwania, które mogły zostać nieprawidłowo użyte.  
  
 Zaprojektowana Ochrona rozszerzona to rozszerzenie protokołów uwierzytelniania zaprojektowanych w celu ograniczenia ataków przekazujących uwierzytelnienie. Koncentruje się na koncepcji informacji o powiązaniach kanału i usługi.  
  
 Ogólne cele są następujące:  
  
1. Jeśli klient został zaktualizowany do obsługi rozszerzonej ochrony, aplikacje powinny dostarczyć powiązanie kanału i informacje o powiązaniu usługi do wszystkich obsługiwanych protokołów uwierzytelniania. Informacje o powiązaniu kanału można podać tylko wtedy, gdy istnieje kanał (TLS), z którym ma zostać utworzone powiązanie. Należy zawsze podać informacje o powiązaniu usługi.  
  
2. Zaktualizowane serwery, które są prawidłowo skonfigurowane, mogą weryfikować informacje o powiązaniach kanału i usługi, gdy są obecne w tokenie uwierzytelniania klienta i odrzucać próbę uwierzytelnienia, jeśli powiązania kanałów nie są zgodne. W zależności od scenariusza wdrażania serwery mogą weryfikować powiązanie kanałów, powiązanie usługi lub oba te elementy.  
  
3. Zaktualizowane serwery mogą akceptować lub odrzucać żądania klientów niższego poziomu, które nie zawierają informacji o powiązaniach kanałów opartych na zasadach.  
  
 Informacje używane przez ochronę rozszerzoną składają się z jednej lub obu następujących dwóch części:  
  
1. Token powiązania kanału lub CBT.  
  
2. Informacje o powiązaniu usługi w postaci nazwy głównej usługi lub SPN.  
  
 Informacje o powiązaniu usługi to wskaźnik zamiaru klienta do uwierzytelnienia w określonym punkcie końcowym usługi. Jest on przekazywany z klienta do serwera z następującymi właściwościami:  
  
- Wartość SPN musi być dostępna dla serwera wykonującego uwierzytelnianie klienta w postaci zwykłego tekstu.  
  
- Wartość SPN jest publiczna.  
  
- Nazwa SPN musi być chroniona kryptograficznie w tranzycie, tak że atak typu man-in-the-Middle nie może wstawiać, usuwać ani modyfikować jego wartości.  
  
 CBT to właściwość zewnętrznego bezpiecznego kanału (na przykład protokołu TLS) służąca do wiązania powiązania z konwersacją w ramach wewnętrznego, uwierzytelnionego przez klienta kanału. CBT musi mieć następujące właściwości (również zdefiniowane przez grupę IETF RFC 5056):  
  
- Gdy istnieje kanał zewnętrzny, wartość CBT musi być właściwością identyfikującą kanał zewnętrzny lub punkt końcowy serwera, niezależnie od tego, że nastąpi zarówno po stronie klienta, jak i serwera.  
  
- Wartość CBT wysyłanej przez klienta nie może być elementem, którego może mieć osoba atakująca.  
  
- Nie są wykonywane żadne gwarancje dotyczące tajemnicy wartości CBT. Nie oznacza to jednak, że wartość powiązania usługi oraz informacje o powiązaniu kanału mogą być zawsze badane przez inne, ale serwer wykonujący uwierzytelnianie, ponieważ protokół z CBT może być szyfrowany.  
  
- CBT musi być chroniona kryptograficznie integralności w tranzycie, co oznacza, że osoba atakująca nie może wstawić, usunąć ani zmodyfikować jej wartości.  
  
 Powiązanie kanału jest realizowane przez klienta przekazującego nazwę SPN i CBT do serwera w Tamperproof sposób. Serwer sprawdza poprawność informacji o powiązaniach kanału zgodnie z zasadami i odrzuca próby uwierzytelniania, dla których nie jest to zamierzony cel. Dzięki temu dwa kanały stają się kryptograficznie powiązane ze sobą.  
  
 Aby zachować zgodność z istniejącymi klientami i aplikacjami, serwer można skonfigurować tak, aby zezwalał na próby uwierzytelniania klientów, którzy jeszcze nie obsługują ochrony rozszerzonej. Jest to nazywane "częściowo zaostrzoną" konfiguracją w przeciwieństwie do konfiguracji "w pełni wzmocnionej".  
  
 Wiele składników w <xref:System.Net> <xref:System.Net.Security> przestrzeniach nazw i wykonuje zintegrowane uwierzytelnianie systemu Windows w imieniu aplikacji wywołującej. W tej sekcji opisano zmiany w składnikach System.Net w celu dodania ochrony rozszerzonej przy użyciu zintegrowanego uwierzytelniania systemu Windows.  
  
 Ochrona rozszerzona jest obecnie obsługiwana w systemie Windows 7. Zapewnia mechanizm, aby aplikacja mogła określić, czy system operacyjny obsługuje ochronę rozszerzoną.  
  
## <a name="changes-to-support-extended-protection"></a>Zmiany w celu obsługi ochrony rozszerzonej  
 Proces uwierzytelniania używany z zintegrowanym uwierzytelnianiem systemu Windows, w zależności od używanego protokołu uwierzytelniania, często zawiera wyzwanie wystawione przez komputer docelowy i wysłane z powrotem do komputera klienckiego. Ochrona rozszerzona dodaje nowe funkcje do tego procesu uwierzytelniania  
  
 <xref:System.Security.Authentication.ExtendedProtection>Przestrzeń nazw zapewnia obsługę uwierzytelniania przy użyciu rozszerzonej ochrony aplikacji. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding>Klasa w tej przestrzeni nazw reprezentuje powiązanie kanału. <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>Klasa w tej przestrzeni nazw reprezentuje zasady ochrony rozszerzonej używane przez serwer do weryfikowania przychodzących połączeń klienta. Inne elementy członkowskie klasy są używane z rozszerzoną ochroną.  
  
 W przypadku aplikacji serwerowych następujące klasy obejmują:  
  
 A <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> , który ma następujące elementy:  
  
- <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A>Właściwość, która wskazuje, czy system operacyjny obsługuje zintegrowane uwierzytelnianie systemu Windows z rozszerzoną ochroną.  
  
- <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>Wartość wskazująca, kiedy należy wymusić zasady ochrony rozszerzonej.  
  
- <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario>Wartość wskazująca scenariusz wdrażania. Ma to wpływ na sposób sprawdzania ochrony rozszerzonej.  
  
- Opcjonalne <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> , które zawiera listę niestandardowych nazw SPN, która jest używana do dopasowania do nazwy SPN dostarczonej przez klienta jako zamierzonego celu uwierzytelniania.  
  
- Opcjonalna <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> , która zawiera niestandardowe powiązanie kanałów do użycia na potrzeby walidacji. Ten scenariusz nie jest powszechnym przypadkiem  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>Przestrzeń nazw zapewnia obsługę konfiguracji uwierzytelniania przy użyciu rozszerzonej ochrony aplikacji.  
  
 Wprowadzono wiele zmian funkcji do obsługi rozszerzonej ochrony w istniejącej <xref:System.Net> przestrzeni nazw. Są to następujące zmiany:  
  
- Nowa <xref:System.Net.TransportContext> Klasa dodana do <xref:System.Net> przestrzeni nazw, która reprezentuje kontekst transportu.  
  
- <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A>Metody New i Overload w klasie umożliwiającej <xref:System.Net.HttpWebRequest.GetRequestStream%2A> <xref:System.Net.HttpWebRequest> pobranie programu w <xref:System.Net.TransportContext> celu zapewnienia obsługi rozszerzonej ochrony aplikacji klienckich.  
  
- Dodatkowe <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest> klasy i do obsługi aplikacji serwera.  
  
 Wprowadzono zmianę funkcji w celu obsługi rozszerzonej ochrony aplikacji klienckich SMTP w istniejącej <xref:System.Net.Mail> przestrzeni nazw:  
  
- <xref:System.Net.Mail.SmtpClient.TargetName%2A>Właściwość <xref:System.Net.Mail.SmtpClient> klasy, która reprezentuje nazwę SPN służącą do uwierzytelniania w przypadku korzystania z rozszerzonej ochrony aplikacji klienckich SMTP.  
  
 Wprowadzono wiele zmian funkcji do obsługi rozszerzonej ochrony w istniejącej <xref:System.Net.Security> przestrzeni nazw. Są to następujące zmiany:  
  
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A>Metody New i Overload <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> w <xref:System.Net.Security.NegotiateStream> klasie, która umożliwia przekazywanie CBT do obsługi rozszerzonej ochrony aplikacji klienckich.  
  
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A>Metody New i Overload <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> w <xref:System.Net.Security.NegotiateStream> klasie, która umożliwia przekazywanie <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> do obsługi rozszerzonej ochrony aplikacji serwerowych.  
  
- Nowa <xref:System.Net.Security.SslStream.TransportContext%2A> Właściwość <xref:System.Net.Security.SslStream> klasy do obsługi rozszerzonej ochrony aplikacji klienta i serwera.  
  
 <xref:System.Net.Configuration.SmtpNetworkElement>Dodano właściwość do obsługi konfiguracji rozszerzonej ochrony dla klientów SMTP w <xref:System.Net.Security> przestrzeni nazw.  
  
## <a name="extended-protection-for-client-applications"></a>Rozszerzona ochrona aplikacji klienckich  
 Rozszerzona obsługa ochrony większości aplikacji klienckich odbywa się automatycznie. <xref:System.Net.HttpWebRequest>Klasy i <xref:System.Net.Mail.SmtpClient> obsługują ochronę rozszerzoną zawsze, gdy podstawowa wersja systemu Windows obsługuje ochronę rozszerzoną. <xref:System.Net.HttpWebRequest>Wystąpienie wysyła nazwę SPN konstruowaną z <xref:System.Uri> . Domyślnie <xref:System.Net.Mail.SmtpClient> wystąpienie wysyła nazwę SPN skonstruowaną z nazwy hosta serwera poczty SMTP.  
  
 W przypadku uwierzytelniania niestandardowego aplikacje klienckie mogą używać <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> metod lub <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest> klasy, które umożliwiają pobieranie <xref:System.Net.TransportContext> i CBT przy użyciu <xref:System.Net.TransportContext.GetChannelBinding%2A> metody.  
  
 Nazwa SPN do użycia na potrzeby zintegrowanego uwierzytelniania systemu Windows wysyłanego przez <xref:System.Net.HttpWebRequest> wystąpienie do danej usługi może zostać przesłonięta przez ustawienie <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> właściwości.  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A>Właściwość może służyć do ustawiania niestandardowej nazwy SPN do użycia na potrzeby zintegrowanego uwierzytelniania systemu Windows na potrzeby połączenia SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Ochrona rozszerzona dla aplikacji serwerowych  
 <xref:System.Net.HttpListener>automatycznie udostępnia mechanizmy sprawdzania powiązań usługi podczas przeprowadzania uwierzytelniania za pośrednictwem protokołu HTTP.  
  
 Najbardziej bezpiecznym scenariuszem jest włączenie rozszerzonej ochrony dla `HTTPS://` prefiksów. W takim przypadku należy ustawić <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> na <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> wartość ustawioną na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> , i <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> ustawić opcję <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> umieszczania <xref:System.Net.HttpListener> w trybie częściowo zaostrzonym, a jednocześnie <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpowiada tryb w pełni zaostrzony.  
  
 W tej konfiguracji, gdy żądanie jest wysyłane do serwera za pośrednictwem zewnętrznego bezpiecznego kanału, do kanału zewnętrznego jest wysyłane zapytanie dla powiązania kanału. To powiązanie kanału jest przesyłane do wywołań SSPI uwierzytelniania, które sprawdzają, czy powiązanie kanału w obiekcie blob uwierzytelniania jest zgodne. Istnieją trzy możliwe wyniki:  
  
1. Podstawowy system operacyjny serwera nie obsługuje ochrony rozszerzonej. Żądanie nie zostanie ujawnione w aplikacji, a do klienta zostanie zwrócona nieautoryzowana odpowiedź (401). Wiadomość zostanie zarejestrowana w <xref:System.Net.HttpListener> źródle śledzenia, określając przyczynę niepowodzenia.  
  
2. Wywołanie interfejsu SSPI kończy się niepowodzeniem, wskazując, że klient określił powiązanie kanału, które nie pasuje do oczekiwanej wartości pobranej z kanału zewnętrznego lub klient nie może dostarczyć powiązania kanału, gdy skonfigurowano zasady ochrony rozszerzonej na serwerze <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> . W obu przypadkach żądanie nie zostanie uwidocznione w aplikacji, a do klienta zostanie zwrócona nieautoryzowana odpowiedź (401). Wiadomość zostanie zarejestrowana w <xref:System.Net.HttpListener> źródle śledzenia, określając przyczynę niepowodzenia.  
  
3. Klient określa poprawne powiązanie kanałów lub może nawiązać połączenie bez określania powiązania kanału, ponieważ zasady ochrony rozszerzonej na serwerze są skonfigurowane z <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> żądaniem zwracanym do aplikacji w celu przetworzenia. Sprawdzanie nazw usług nie jest wykonywane automatycznie. Aplikacja może zdecydować się na wykonanie własnej weryfikacji nazw usług przy użyciu <xref:System.Net.HttpListenerRequest.ServiceName%2A> właściwości, ale w tych okolicznościach jest to nadmiarowe.  
  
 Jeśli aplikacja wykonuje własne wywołania interfejsu SSPI do uwierzytelniania na podstawie obiektów BLOB przekazanych z powrotem i do wewnątrz treści żądania HTTP i chce obsługiwać powiązanie kanałów, musi pobrać oczekiwane powiązanie kanału z zewnętrznego bezpiecznego kanału przy użyciu polecenia, <xref:System.Net.HttpListener> Aby przekazać je do natywnej funkcji Win32 [działanie funkcji AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) . W tym celu należy użyć <xref:System.Net.HttpListenerRequest.TransportContext%2A> właściwości i metody Call <xref:System.Net.TransportContext.GetChannelBinding%2A> do pobrania CBT. Obsługiwane są tylko powiązania punktów końcowych. Jeśli <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> jest określona jakakolwiek inna wartość, <xref:System.NotSupportedException> zostanie zgłoszony. Jeśli podstawowy system operacyjny obsługuje powiązanie kanałów, metoda zwróci <xref:System.Net.TransportContext.GetChannelBinding%2A> <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> otokę wskaźnika do powiązania kanału odpowiednie do przekazywania funkcji [działanie funkcji AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) jako element członkowski pvBuffer struktury SecBuffer przekazaną w `pInput` parametrze. <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A>Właściwość zawiera długość powiązania kanału wyrażoną w bajtach. Jeśli podstawowy system operacyjny nie obsługuje powiązań kanałów, funkcja zwróci wartość `null` .  
  
 Innym możliwym scenariuszem jest włączenie rozszerzonej ochrony dla `HTTP://` prefiksów, gdy serwery proxy nie są używane. W takim przypadku należy ustawić <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> na <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> wartość ustawioną na <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> , i <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> ustawić opcję <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> umieszczania <xref:System.Net.HttpListener> w trybie częściowo zaostrzonym, a jednocześnie <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> odpowiada tryb w pełni zaostrzony.  
  
 Domyślna lista dozwolonych nazw usług jest tworzona na podstawie prefiksów, które zostały zarejestrowane w programie <xref:System.Net.HttpListener> . Tę listę domyślną można sprawdzić za pomocą <xref:System.Net.HttpListener.DefaultServiceNames%2A> właściwości. Jeśli ta lista nie jest kompletna, aplikacja może określić niestandardową kolekcję nazw usług w konstruktorze dla <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> klasy, która będzie używana zamiast domyślnej listy nazw usług.  
  
 W tej konfiguracji, gdy żądanie jest nawiązywane na serwerze bez uwierzytelniania przy użyciu zewnętrznego bezpiecznego kanału, zazwyczaj bez sprawdzania powiązania kanałów. Jeśli uwierzytelnianie powiedzie się, kontekst jest pytany dla nazwy usługi dostarczonej przez klienta i zweryfikowanej na liście akceptowalnych nazw usług. Istnieją cztery możliwe wyniki:  
  
1. Podstawowy system operacyjny serwera nie obsługuje ochrony rozszerzonej. Żądanie nie zostanie ujawnione w aplikacji, a do klienta zostanie zwrócona nieautoryzowana odpowiedź (401). Wiadomość zostanie zarejestrowana w <xref:System.Net.HttpListener> źródle śledzenia, określając przyczynę niepowodzenia.  
  
2. Podstawowy system operacyjny klienta nie obsługuje ochrony rozszerzonej. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfiguracji próba uwierzytelnienia powiedzie się, a żądanie zostanie zwrócone do aplikacji. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfiguracji próba uwierzytelnienia nie powiedzie się. Żądanie nie zostanie ujawnione w aplikacji, a do klienta zostanie zwrócona nieautoryzowana odpowiedź (401). Wiadomość zostanie zarejestrowana w <xref:System.Net.HttpListener> źródle śledzenia, określając przyczynę niepowodzenia.  
  
3. Podstawowy system operacyjny klienta obsługuje ochronę rozszerzoną, ale aplikacja nie określiła powiązania usługi. Żądanie nie zostanie ujawnione w aplikacji, a do klienta zostanie zwrócona nieautoryzowana odpowiedź (401). Wiadomość zostanie zarejestrowana w <xref:System.Net.HttpListener> źródle śledzenia, określając przyczynę niepowodzenia.  
  
4. Klient określił powiązanie usługi. Powiązanie usługi jest porównywane z listą dozwolonych powiązań usług. Jeśli jest to zgodne, żądanie jest zwracane do aplikacji. W przeciwnym razie żądanie nie zostanie uwidocznione w aplikacji, a odpowiedź (401) nie zostanie automatycznie zwrócona do klienta. Wiadomość zostanie zarejestrowana w <xref:System.Net.HttpListener> źródle śledzenia, określając przyczynę niepowodzenia.  
  
 Jeśli proste podejście wykorzystujące dozwoloną listę dozwolonych nazw usług jest niewystarczające, aplikacja może zapewnić własną weryfikację nazw usług, wykonując zapytania dotyczące <xref:System.Net.HttpListenerRequest.ServiceName%2A> właściwości. W przypadkach 1 i 2 powyżej właściwość zwróci wartość `null` . W przypadku 3 zostanie zwrócony pusty ciąg. W przypadku 4 zostanie zwrócona nazwa usługi określona przez klienta.  
  
 Te funkcje rozszerzonej ochrony mogą być również używane przez aplikacje serwera do uwierzytelniania z innymi typami żądań i w przypadku używania zaufanych serwerów proxy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
