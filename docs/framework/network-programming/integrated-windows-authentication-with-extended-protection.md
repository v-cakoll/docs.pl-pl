---
title: Zintegrowane uwierzytelnianie systemu Windows z ochroną rozszerzoną
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
ms.openlocfilehash: c4afc008f600c9be0040f8d7623f5e20623dfd7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74444233"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>Zintegrowane uwierzytelnianie systemu Windows z ochroną rozszerzoną
Wprowadzono ulepszenia wpływające na sposób obsługi zintegrowanego <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpListener>uwierzytelniania systemu Windows przez , , <xref:System.Net.Mail.SmtpClient> <xref:System.Net.Security.SslStream>, <xref:System.Net.Security.NegotiateStream>i powiązane klasy w <xref:System.Net> powiązanych przestrzeniach nazw. Dodano obsługę rozszerzonej ochrony w celu zwiększenia bezpieczeństwa.  
  
 Te zmiany mogą mieć wpływ na aplikacje, które używają tych klas do tworzenia żądań sieci web i odbierania odpowiedzi, w których używane jest zintegrowane uwierzytelnianie systemu Windows. Ta zmiana może również mieć wpływ na serwery sieci Web i aplikacje klienckie skonfigurowane do używania zintegrowanego uwierzytelniania systemu Windows.  
  
 Te zmiany mogą również wpływać na aplikacje, które używają tych klas do tworzenia innych typów żądań i odbierania odpowiedzi, w których używane jest zintegrowane uwierzytelnianie systemu Windows.  
  
 Zmiany dotyczące ochrony rozszerzonej są dostępne tylko dla aplikacji w systemach Windows 7 i Windows Server 2008 R2. Rozszerzone funkcje ochrony nie są dostępne we wcześniejszych wersjach systemu Windows.  
  
## <a name="overview"></a>Omówienie  
 Projekt zintegrowanego uwierzytelniania systemu Windows pozwala na niektóre odpowiedzi wyzwanie poświadczeń być uniwersalne, co oznacza, że mogą być ponownie używane lub przekazywane dalej. Odpowiedzi na wyzwania powinny być konstruowane co najmniej z docelowymi konkretnymi informacjami, a najlepiej również z pewnymi informacjami dotyczącymi poszczególnych kanałów. Usługi mogą następnie zapewnić rozszerzoną ochronę, aby upewnić się, że odpowiedzi na wyzwania poświadczeń zawierają informacje specyficzne dla usługi, takie jak nazwa główna usługi (SPN). Dzięki tym informacjom w wymianie poświadczeń usługi są w stanie lepiej chronić przed złośliwym użyciem odpowiedzi na wyzwania poświadczeń, które mogły być niewłaściwie używane.  
  
 Projekt ochrony rozszerzonej jest rozszerzenie protokołów uwierzytelniania mające na celu ograniczenie ataków przekazywania uwierzytelniania. Koncentruje się wokół koncepcji kanału i usługi powiązania informacji.  
  
 Ogólne cele są następujące:  
  
1. Jeśli klient jest aktualizowany w celu obsługi rozszerzonej ochrony, aplikacje powinny dostarczać informacje o powiązaniach kanału i usługi do wszystkich obsługiwanych protokołów uwierzytelniania. Informacje o powiązaniu kanału mogą być dostarczane tylko wtedy, gdy istnieje kanał (TLS) do powiązania. Informacje dotyczące powiązania usługi powinny być zawsze dostarczane.  
  
2. Zaktualizowane serwery, które są poprawnie skonfigurowane, mogą weryfikować informacje o powiązaniu kanału i usługi, gdy są obecne w tokenie uwierzytelniania klienta i odrzucać próbę uwierzytelnienia, jeśli powiązania kanału nie są zgodne. W zależności od scenariusza wdrażania serwery mogą weryfikować powiązanie kanału, powiązanie usługi lub oba te elementy.  
  
3. Zaktualizowane serwery mają możliwość akceptowania lub odrzucania żądań klientów na poziomie podrzędnym, które nie zawierają informacji o powiązaniu kanału opartych na zasadach.  
  
 Informacje wykorzystywane przez ochronę rozszerzoną składają się z jednej lub obu z następujących dwóch części:  
  
1. Token powiązania kanału lub CBT.  
  
2. Informacje o powiązaniach usługi w postaci nazwy głównej usługi lub nazwy SPN.  
  
 Informacje o powiązaniu usługi jest wskazanie intencji klienta do uwierzytelniania do określonego punktu końcowego usługi. Jest przekazywana z klienta do serwera z następującymi właściwościami:  
  
- Wartość SPN musi być dostępna dla serwera wykonującego uwierzytelnianie klienta w postaci zwykłego tekstu.  
  
- Wartość nazwy SPN jest publiczna.  
  
- Nazwa SPN musi być kryptograficznie chronione podczas przesyłania w taki sposób, że atak typu man-in-the-middle nie może wstawić, usunąć lub zmodyfikować jego wartości.  
  
 CBT jest właściwością zewnętrznego bezpiecznego kanału (takiego jak TLS) używanego do powiązania (powiązania) go z konwersacją za pomocą wewnętrznego kanału uwierzytelnionego przez klienta. CBT musi mieć następujące właściwości (również zdefiniowane przez IETF RFC 5056):  
  
- Gdy istnieje kanał zewnętrzny, wartość CBT musi być właściwością identyfikującą kanał zewnętrzny lub punkt końcowy serwera, niezależnie dotarty zarówno przez klienta, jak i strony serwera konwersacji.  
  
- Wartość CBT wysyłane przez klienta nie może być coś osoba atakująca może mieć wpływ.  
  
- Nie udziela się żadnych gwarancji dotyczących tajemnicy wartości CBT. Nie oznacza to jednak, że wartość powiązania usługi, a także informacje o powiązaniach kanału zawsze mogą być badane przez inne, ale serwer wykonujący uwierzytelnianie, ponieważ protokół zawierający CBT może go szyfrować.  
  
- CBT musi być kryptograficznie integralność chroniona podczas przesyłania w taki sposób, aby osoba atakująca nie może wstawić, usunąć lub zmodyfikować jego wartości.  
  
 Powiązanie kanału jest realizowane przez klienta, który przenosi nazwę SPN i CBT na serwer w sposób odporny na manipulacje. Serwer sprawdza poprawność informacji o powiązaniu kanału zgodnie ze swoimi zasadami i odrzuca próby uwierzytelnienia, dla których nie uważa się za zamierzony cel. W ten sposób dwa kanały stają się kryptograficznie powiązane ze sobą.  
  
 Aby zachować zgodność z istniejącymi klientami i aplikacjami, serwer może być skonfigurowany tak, aby zezwalał na próby uwierzytelnienia przez klientów, którzy jeszcze nie obsługują ochrony rozszerzonej. Jest to określane jako "częściowo utwardzona" konfiguracja, w przeciwieństwie do "w pełni hartowane" konfiguracji.  
  
 Wiele składników <xref:System.Net> w <xref:System.Net.Security> przestrzeniach nazw i obszarach nazw wykonuje zintegrowane uwierzytelnianie systemu Windows w imieniu aplikacji wywołującej. W tej sekcji opisano zmiany składników System.Net, aby dodać rozszerzoną ochronę podczas korzystania ze zintegrowanego uwierzytelniania systemu Windows.  
  
 Ochrona rozszerzona jest obecnie obsługiwana w systemie Windows 7. Mechanizm jest dostarczany, dzięki czemu aplikacja może określić, czy system operacyjny obsługuje ochronę rozszerzoną.  
  
## <a name="changes-to-support-extended-protection"></a>Zmiany w obsłudze ochrony rozszerzonej  
 Proces uwierzytelniania używany ze zintegrowanym uwierzytelnianiem systemu Windows, w zależności od używanego protokołu uwierzytelniania, często zawiera wyzwanie wydane przez komputer docelowy i odesłane z powrotem do komputera klienckiego. Rozszerzona ochrona dodaje nowe funkcje do tego procesu uwierzytelniania  
  
 Obszar <xref:System.Security.Authentication.ExtendedProtection> nazw zapewnia obsługę uwierzytelniania przy użyciu rozszerzonej ochrony aplikacji. Klasa <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> w tej przestrzeni nazw reprezentuje powiązanie kanału. Klasa <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> w tym obszarze nazw reprezentuje rozszerzone zasady ochrony używane przez serwer do sprawdzania poprawności przychodzących połączeń klientów. Inne elementy członkowskie klasy są używane z rozszerzoną ochroną.  
  
 W przypadku aplikacji serwerowych te klasy są następujące:  
  
 A, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> który ma następujące elementy:  
  
- Właściwość wskazująca, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> czy system operacyjny obsługuje zintegrowane uwierzytelnianie systemu Windows z rozszerzoną ochroną.  
  
- Wartość <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> wskazująca, kiedy zasady ochrony rozszerzonej powinny być wymuszane.  
  
- Wartość, <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> która wskazuje scenariusz wdrażania. Wpływa to na sposób sprawdzania rozszerzonej ochrony.  
  
- Opcjonalnie, <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> który zawiera niestandardową listę SPN, która jest używana do dopasowania do nazwy SPN dostarczonej przez klienta jako zamierzony cel uwierzytelniania.  
  
- Opcjonalny, <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> który zawiera niestandardowe powiązanie kanału do użycia do sprawdzania poprawności. Ten scenariusz nie jest częstym przypadkiem  
  
 Obszar <xref:System.Security.Authentication.ExtendedProtection.Configuration> nazw zapewnia obsługę konfiguracji uwierzytelniania przy użyciu rozszerzonej ochrony aplikacji.  
  
 Wprowadzono szereg zmian funkcji w celu obsługi rozszerzonej ochrony w istniejącym <xref:System.Net> obszarze nazw. Zmiany te są następujące:  
  
- Nowa <xref:System.Net.TransportContext> klasa dodana <xref:System.Net> do obszaru nazw, który reprezentuje kontekst transportu.  
  
- Nowe <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> <xref:System.Net.HttpWebRequest.GetRequestStream%2A> i przeciążenia <xref:System.Net.HttpWebRequest> metody w klasie, które umożliwiają pobieranie do obsługi rozszerzonej <xref:System.Net.TransportContext> ochrony aplikacji klienckich.  
  
- Dodatki do <xref:System.Net.HttpListener> i <xref:System.Net.HttpListenerRequest> klas do obsługi aplikacji serwera.  
  
 W celu obsługi rozszerzonej ochrony aplikacji klienckich SMTP w istniejącym <xref:System.Net.Mail> obszarze nazw została wniesieniem zmiany funkcji:  
  
- Właściwość <xref:System.Net.Mail.SmtpClient.TargetName%2A> w <xref:System.Net.Mail.SmtpClient> klasie reprezentującej nazwę SPN do użycia do uwierzytelniania podczas korzystania z rozszerzonej ochrony aplikacji klienckich SMTP.  
  
 Wprowadzono szereg zmian funkcji w celu obsługi rozszerzonej ochrony w istniejącym <xref:System.Net.Security> obszarze nazw. Zmiany te są następujące:  
  
- Nowe <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> i przeciążenia <xref:System.Net.Security.NegotiateStream> metody w klasie, które umożliwiają przekazywanie CBT do obsługi rozszerzonej ochrony aplikacji klienckich.  
  
- Nowe <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> i przeciążenia <xref:System.Net.Security.NegotiateStream> metody w <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> klasie, które umożliwiają przekazywanie do obsługi rozszerzonej ochrony aplikacji serwera.  
  
- Nowa <xref:System.Net.Security.SslStream.TransportContext%2A> właściwość <xref:System.Net.Security.SslStream> w klasie do obsługi rozszerzonej ochrony aplikacji klienckich i serwerowych.  
  
 Dodano <xref:System.Net.Configuration.SmtpNetworkElement> właściwość do obsługi konfiguracji rozszerzonej ochrony klientów <xref:System.Net.Security> SMTP w obszarze nazw.  
  
## <a name="extended-protection-for-client-applications"></a>Rozszerzona ochrona aplikacji klienckich  
 Rozszerzona obsługa ochrony dla większości aplikacji klienckich odbywa się automatycznie. I <xref:System.Net.HttpWebRequest> <xref:System.Net.Mail.SmtpClient> klasy obsługują rozszerzoną ochronę za każdym razem, gdy podstawowa wersja systemu Windows obsługuje ochronę rozszerzoną. Wystąpienie <xref:System.Net.HttpWebRequest> wysyła nazwę SPN <xref:System.Uri>skonstruowaną z pliku . Domyślnie wystąpienie <xref:System.Net.Mail.SmtpClient> wysyła nazwę SPN skonstruowaną na podstawie nazwy hosta serwera poczty SMTP.  
  
 W przypadku uwierzytelniania niestandardowego <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> aplikacje <xref:System.Net.HttpWebRequest> klienckie mogą <xref:System.Net.TransportContext> używać metod lub <xref:System.Net.TransportContext.GetChannelBinding%2A> w klasie, które umożliwiają pobieranie i CBT przy użyciu metody.  
  
 Nazwa SPN do użycia do zintegrowanego uwierzytelniania systemu Windows wysyłane przez <xref:System.Net.HttpWebRequest> <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> wystąpienie do danej usługi można zastąpić przez ustawienie właściwości.  
  
 Właściwości <xref:System.Net.Mail.SmtpClient.TargetName%2A> można użyć do ustawienia niestandardowej nazwy SPN do użycia do zintegrowanego uwierzytelniania systemu Windows dla połączenia SMTP.  
  
## <a name="extended-protection-for-server-applications"></a>Rozszerzona ochrona aplikacji serwerowych  
 <xref:System.Net.HttpListener>automatycznie udostępnia mechanizmy sprawdzania poprawności powiązań usługi podczas wykonywania uwierzytelniania HTTP.  
  
 Najbezpieczniejszym scenariuszem jest włączenie rozszerzonej ochrony przedrostek HTTPS://. W takim <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> przypadku, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ustawić <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> z <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>zestawem <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> do <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> , <xref:System.Net.HttpListener> i ustawić wartość A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> stawia w trybie częściowo hartowane, podczas gdy odpowiada trybowi w pełni hartowane.  
  
 W tej konfiguracji, gdy żądanie jest składane do serwera za pośrednictwem zewnętrznego bezpiecznego kanału, zewnętrzny kanał jest wyszukiwany dla powiązania kanału. To powiązanie kanału jest przekazywane do uwierzytelniania SSPI wywołania, które sprawdź, czy powiązanie kanału w uwierzytelniania obiektu blob pasuje. Istnieją trzy możliwe wyniki:  
  
1. Podstawowy system operacyjny serwera nie obsługuje rozszerzonej ochrony. Żądanie nie będzie widoczne dla aplikacji, a nieautoryzowana odpowiedź (401) zostanie zwrócona do klienta. Komunikat zostanie zarejestrowany do <xref:System.Net.HttpListener> źródła śledzenia określając przyczynę błędu.  
  
2. Wywołanie SSPI kończy się niepowodzeniem, wskazując, że klient określił powiązanie kanału, które nie odpowiada oczekiwanej wartości pobranej z kanału zewnętrznego lub klient <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>nie może dostarczyć powiązania kanału, gdy skonfigurowano rozszerzone zasady ochrony na serwerze . W obu przypadkach żądanie nie będzie widoczne dla aplikacji, a nieautoryzowana odpowiedź (401) zostanie zwrócona do klienta. Komunikat zostanie zarejestrowany do <xref:System.Net.HttpListener> źródła śledzenia określając przyczynę błędu.  
  
3. Klient określa prawidłowe powiązanie kanału lub może łączyć się bez określania powiązania kanału, ponieważ <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> rozszerzone zasady ochrony na serwerze są skonfigurowane za pomocą Żądania jest zwracany do aplikacji do przetwarzania. Sprawdzanie nazwy usługi nie jest wykonywane automatycznie. Aplikacja może zdecydować się na wykonanie własnej <xref:System.Net.HttpListenerRequest.ServiceName%2A> weryfikacji nazwy usługi przy użyciu właściwości, ale w tych okolicznościach jest nadmiarowy.  
  
 Jeśli aplikacja wykonuje własne wywołania SSPI do wykonywania uwierzytelniania na podstawie obiektów blob przekazywane tam iz powrotem w treści żądania HTTP i <xref:System.Net.HttpListener> chce obsługiwać powiązanie kanału, musi pobrać powiązanie oczekiwanego kanału z zewnętrznego bezpiecznego kanału przy użyciu w celu przekazania go do natywnej funkcji [Win32 AcceptSecurityContext.](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) Aby to zrobić, <xref:System.Net.HttpListenerRequest.TransportContext%2A> należy <xref:System.Net.TransportContext.GetChannelBinding%2A> użyć właściwości i wywołać metody, aby pobrać CBT. Obsługiwane są tylko powiązania punktu końcowego. Jeśli cokolwiek innego <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint> <xref:System.NotSupportedException> jest określony, a zostanie rzucony. Jeśli podstawowy system operacyjny obsługuje <xref:System.Net.TransportContext.GetChannelBinding%2A> powiązanie kanału, <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> <xref:System.Runtime.InteropServices.SafeHandle> metoda zwróci zawijania wskaźnik do powiązania kanału nadaje się do przekazywania do [AcceptSecurityContext](/windows/win32/api/sspi/nf-sspi-acceptsecuritycontext) funkcji jako pvBuffer element członkowski secbuffer struktury przekazywane w parametrze. `pInput` Właściwość <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> zawiera długość w bajtach powiązania kanału. Jeśli podstawowy system operacyjny nie obsługuje powiązań kanału, funkcja powróci `null`.  
  
 Innym możliwym scenariuszem jest włączenie rozszerzonej ochrony prefiksów HTTP://, gdy serwery proxy nie są używane. W takim <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> przypadku, <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> ustawić <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> z <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always>zestawem <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> do <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected> lub <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> , <xref:System.Net.HttpListener> i ustawić wartość A <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> stawia w trybie częściowo hartowane, podczas gdy odpowiada trybowi w pełni hartowane.  
  
 Domyślna lista dozwolonych nazw usług jest tworzona na podstawie <xref:System.Net.HttpListener>prefiksów, które zostały zarejestrowane w pliku . Tę listę domyślną <xref:System.Net.HttpListener.DefaultServiceNames%2A> można zbadać za pośrednictwem właściwości. Jeśli ta lista nie jest wyczerpująca, aplikacja może określić kolekcję nazw usługi niestandardowej w konstruktorze <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> dla klasy, która będzie używana zamiast domyślnej listy nazw usługi.  
  
 W tej konfiguracji, gdy żądanie jest składane do serwera bez zewnętrznego bezpiecznego kanału uwierzytelniania przebiega normalnie bez sprawdzania powiązania kanału. Jeśli uwierzytelnianie zakończy się pomyślnie, kontekst jest pytany o nazwę usługi, którą klient dostarczył i zweryfikował względem listy dopuszczalnych nazw usług. Istnieją cztery możliwe wyniki:  
  
1. Podstawowy system operacyjny serwera nie obsługuje rozszerzonej ochrony. Żądanie nie będzie widoczne dla aplikacji, a nieautoryzowana odpowiedź (401) zostanie zwrócona do klienta. Komunikat zostanie zarejestrowany do <xref:System.Net.HttpListener> źródła śledzenia określając przyczynę błędu.  
  
2. Podstawowy system operacyjny klienta nie obsługuje rozszerzonej ochrony. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> konfiguracji próba uwierzytelnienia zakończy się pomyślnie i żądanie zostanie zwrócone do aplikacji. W <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> konfiguracji próba uwierzytelnienia zakończy się niepowodzeniem. Żądanie nie będzie widoczne dla aplikacji, a nieautoryzowana odpowiedź (401) zostanie zwrócona do klienta. Komunikat zostanie zarejestrowany do <xref:System.Net.HttpListener> źródła śledzenia określając przyczynę błędu.  
  
3. Podstawowy system operacyjny klienta obsługuje ochronę rozszerzoną, ale aplikacja nie określiła powiązania usługi. Żądanie nie będzie widoczne dla aplikacji, a nieautoryzowana odpowiedź (401) zostanie zwrócona do klienta. Komunikat zostanie zarejestrowany do <xref:System.Net.HttpListener> źródła śledzenia określając przyczynę błędu.  
  
4. Klient określił powiązanie usługi. Powiązanie usługi jest porównywany z listą dozwolonych powiązań usługi. Jeśli jest zgodny, żądanie jest zwracane do aplikacji. W przeciwnym razie żądanie nie będzie widoczne dla aplikacji, a nieautoryzowana odpowiedź (401) zostanie automatycznie zwrócona do klienta. Komunikat zostanie zarejestrowany do <xref:System.Net.HttpListener> źródła śledzenia określając przyczynę błędu.  
  
 Jeśli to proste podejście przy użyciu listy dozwolonych nazw usług jest niewystarczająca, aplikacja <xref:System.Net.HttpListenerRequest.ServiceName%2A> może zapewnić własną weryfikację nazwy usługi, wykonując kwerendę właściwości. W przypadku 1 i 2 powyżej, obiekt zwróci. `null` W przypadku 3 zwróci pusty ciąg. W przypadku 4 zostanie zwrócona nazwa usługi określona przez klienta.  
  
 Te rozszerzone funkcje ochrony mogą być również używane przez aplikacje serwera do uwierzytelniania z innymi typami żądań i gdy używane są zaufane serwery proxy.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Security.Authentication.ExtendedProtection>
- <xref:System.Security.Authentication.ExtendedProtection.Configuration>
