---
title: Zabezpieczanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 742d9c4360f6b314ac86b2e8d39185f5291f1aff
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808842"
---
# <a name="securing-services"></a>Zabezpieczanie usług
Obejmuje dwa podstawowe wymagania zabezpieczeń usługi Windows Communication Foundation (WCF): transfer zabezpieczeń i autoryzacji. (Trzeci wymaganie, przeprowadzanie inspekcji zdarzeń zabezpieczeń jest opisany w [inspekcji](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Krótko mówiąc transfer zabezpieczeń obejmuje uwierzytelniania (weryfikacji tożsamości klienta i usługi), poufność (szyfrowanie wiadomości) i integralności (cyfrowego podpisywania przed naruszeniem). Autoryzacja jest kontrola dostępu do zasobów, na przykład, dzięki czemu tylko użytkownicy o odpowiednich uprawnieniach do odczytu pliku. Przy użyciu funkcji usługi WCF, dwa podstawowe wymagania są łatwo zaimplementować.  
  
 Z wyjątkiem produktów <xref:System.ServiceModel.BasicHttpBinding> klasy (lub [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element w konfiguracji), transfer zabezpieczeń jest domyślnie włączona dla wszystkich wstępnie zdefiniowanych powiązań. Tematy w tej sekcji opisano dwa podstawowe scenariusze: implementacja transfer zabezpieczeń oraz autoryzacji intranet usługi hostowanej na Internet Information Services (IIS) i implementowanie zabezpieczeń transfer i autoryzacji w usłudze hostowanej w usługach IIS.  
  
> [!NOTE]
>  Windows XP Home nie obsługuje uwierzytelniania systemu Windows. W związku z tym nie należy uruchamiać usługę w tym systemie.  
  
## <a name="security-basics"></a>Podstawy zabezpieczeń  
 Zależy od zabezpieczeń *poświadczenia*. Poświadczenie okaże się jednostki jest, który się podaje. ( *Jednostki* może być osoba, proces oprogramowania, firma lub wszystko, co może być upoważnionych.) Na przykład klient usługi przesyła *oświadczeń* z *tożsamości*, a poświadczenia potwierdza, że oświadczeń w sposób. W typowy scenariusz występuje wymiany poświadczeń. Najpierw usługi powoduje, że oświadczenie tożsamości i okaże się do klienta z poświadczeniami. Z drugiej strony klient wykonuje oświadczenie tożsamości oraz prezentuje poświadczenia do usługi. Jeśli obie strony zaufania drugiego poświadczenia, a następnie *bezpiecznym kontekście* można ustalić, w którym wszystkie komunikaty są wymieniane w poufności i wszystkie komunikaty są podpisane ochrony ich integralność. Po usługi ustanawia tożsamości klienta, następnie może dopasować oświadczeń z poświadczenia, aby *roli* lub *członkostwa* w grupie. W obu przypadkach za pomocą roli lub grupy, do której należy dany klient, usługa *autoryzuje* do wykonywania określonych operacji klienta oparte na uprawnienia roli lub grupy.  
  
## <a name="windows-security-mechanisms"></a>Mechanizmy zabezpieczeń systemu Windows  
 Jeśli klient i komputer z usługą znajdują się w domenie systemu Windows, wymagającego zarówno do logowania się do sieci, poświadczenia są dostarczane przez Windows infrastruktury. W takim przypadku poświadczenia są ustalone, gdy użytkownik komputera loguje się do sieci. Każdy użytkownik i każdy komputer w sieci musi zostać zweryfikowany jako należące do zaufanych zbioru użytkowników i komputerów. W systemie Windows, co takiego użytkownika i komputer jest również nazywany *podmiotu zabezpieczeń*.  
  
 W domenie systemu Windows przez *Kerberos* kontrolera, protokołu Kerberos kontrolera wykorzystuje schemat oparte na przyznawania biletów w każdym podmiotu zabezpieczeń. Bilety przyznaje kontrolera są zaufane przez inne biletu udzielające w systemie. Zawsze, gdy próbuje wykonać niektórych operacji lub dostęp do jednostki *zasobów* (takich jak plik lub katalog na komputerze), biletu jest zbadać jego ważności i, jeśli przekazuje ono podmiot zabezpieczeń uzyskuje bilet innej operacji. Ta metoda przyznawania biletów jest bardziej efektywne niż alternatywnej z próby weryfikacji podmiot zabezpieczeń dla każdej operacji.  
  
 Mechanizm starszej, mniej bezpiecznych używany w domenach systemu Windows jest NT LAN Manager (NTLM). W przypadkach, gdy (zazwyczaj spoza domeny systemu Windows, takich jak grupy roboczej), w którym nie można użyć protokołu Kerberos NTLM może służyć jako alternatywę. Uwierzytelnianie NTLM jest również dostępna jako opcja zabezpieczeń dla usług IIS.  
  
 W systemie Windows autoryzacja działa przez przypisanie każdego komputera i użytkownika do zestawu ról i grup. Na przykład, każdy komputer z systemem Windows należy skonfigurować i kontrolowane przez osobę (lub grupa osób) w roli *administratora*. Inną rolą jest *użytkownika*, który zawiera zbiór bardziej ograniczone uprawnienia. Oprócz tej roli użytkownicy są przypisane do grup. Grupy umożliwia wielu użytkownikom do wykonywania w tej samej roli. W praktyce w związku z tym maszynę z systemem Windows jest zarządzany przez przypisywania użytkowników do grup. Na przykład można przypisać wielu użytkowników do grupy Użytkownicy komputerów i bardziej ograniczone zbiór użytkowników można przypisać do grupy Administratorzy. Na komputerze lokalnym administrator można również tworzyć nowe grupy i przypisz do grupy innych użytkowników (lub nawet inne grupy).  
  
 Na komputerze z systemem Windows co folder w katalogu mogą być chronione. Oznacza to możesz wybrać folder i kontrolowania, kto może uzyskać dostępu do plików i lub nie można skopiować pliku lub (w przypadku najbardziej uprzywilejowanym) Zmień pliku, usuń plik lub Dodaj pliki do folderu. Jest to nazywane kontroli dostępu i mechanizm jest znany jako lista kontroli dostępu (ACL). Podczas tworzenia listy ACL, można przypisać uprawnienia dostępu do żadnych grup lub grup, a także poszczególnych członków domeny.  
  
 Infrastruktura WCF jest przeznaczona do użycia tych mechanizmów zabezpieczeń systemu Windows. W związku z tym w przypadku tworzenia usługi wdrożonej w sieci intranet, a których klienci są ograniczone do elementów członkowskich domeny systemu Windows, zabezpieczenia łatwo jest zaimplementowana. Tylko uprawnieni użytkownicy mogą zalogować się do domeny. Po zalogowaniu użytkownicy kontrolera Kerberos umożliwia poszczególnych użytkowników w celu ustanowienia bezpiecznego kontekstów z innego komputera lub aplikacji. Na komputerze lokalnym można łatwo tworzyć grupy, a podczas ochrony określonych folderów, te grupy mogą być używane do przypisywania uprawnień dostępu na komputerze.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementacja zabezpieczeń systemu Windows na usługach sieci Intranet  
 Aby zabezpieczyć aplikację, która działa wyłącznie w domenie systemu Windows, można użyć domyślnych ustawień zabezpieczeń albo <xref:System.ServiceModel.WSHttpBinding> lub <xref:System.ServiceModel.NetTcpBinding> powiązania. Domyślnie każdy użytkownik w tej samej domenie systemu Windows ma dostęp do usługi WCF. Ponieważ ci użytkownicy są zalogowani do sieci, są zaufane. Wiadomości między usługą i klienta są szyfrowane w celu zachowania poufności i podpisany w celu zapewnienia integralności. Aby uzyskać więcej informacji o tym, jak utworzyć usługę korzystającą z zabezpieczeń systemu Windows, zobacz [porady: Zabezpieczanie usługi za pomocą poświadczeń systemu Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autoryzacji przy użyciu klasy PrincipalPermissionAttribute  
 Jeśli chcesz ograniczyć dostęp do zasobów na komputerze, najprostszym sposobem jest użycie <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasy. Ten atrybut można ograniczyć wywołania operacji usługi przez wymaganie, które użytkownik jest w określonej grupy systemu Windows lub roli lub być określonego użytkownika. Aby uzyskać więcej informacji, zobacz [porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Personifikacja  
 Personifikacja jest innym mechanizmem, który służy do kontrolowania dostępu do zasobów. Domyślnie usługa hostowanych przez usługi IIS będzie uruchamiana z tożsamością konto ASPNET. Konto ASPNET można uzyskać dostępu do zasobów, dla których ma uprawnienia. Istnieje możliwość ustawienia listy ACL dla folder do wykluczenia ASPNET konta usługi, ale zezwala niektórych innych tożsamości dostępu do tego folderu. Następnie pytanie staje się jak zezwalają na dostęp do folderu, jeśli konto ASPNET nie jest dozwolone w tym celu. Odpowiedź jest należy używać personifikacji, zgodnie z którymi usługa może używać poświadczeń klienta do uzyskania dostępu do określonego zasobu. Innym przykładem jest podczas uzyskiwania dostępu do bazy danych SQL Server, do którego tylko niektórzy użytkownicy mają uprawnienia. Aby uzyskać więcej informacji o używaniu personifikacji, zobacz [porady: Personifikowanie klienta w usługi](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) i [delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Zabezpieczenia w Internecie  
 Zabezpieczenia w Internecie składa się z te same wymagania co zabezpieczeń w sieci intranet. Usługa musi przedstawić swoje poświadczenia dla potwierdzenia autentyczności jego, a klienci muszą potwierdzić swoją tożsamość w usłudze. Po sprawdzone tożsamości klienta usługi można kontrolować dostęp, ile klient ma do zasobów. Ze względu na specyfikę heterogenicznych Internetu, przedstawionych poświadczeń różnią się od w domenie systemu Windows. Natomiast kontroler Kerberos obsługuje uwierzytelnianie użytkowników w domenie z biletów dla poświadczeń w Internecie, usług i klientów polegać na jednym z kilka różnych sposobów przedstawiać poświadczeń. Celem tego tematu jest jednak do prezentowania typowym podejściem, która umożliwia tworzenie usługi WCF, który jest dostępny w Internecie.  
  
### <a name="using-iis-and-aspnet"></a>Za pomocą usług IIS i platformy ASP.NET  
 Wymagania zabezpieczeń internetowych i mechanizmu rozwiązywania tych problemów, nie są nowe. Usługi IIS jest serwerem sieci Web firmy Microsoft przez Internet i oferuje wiele funkcji zabezpieczeń umożliwiające rozwiązanie tych problemów. Ponadto [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] obejmuje funkcje zabezpieczeń, których może używać usługi WCF. Aby móc korzystać z tych funkcji zabezpieczeń, host usługi WCF w programie IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Za pomocą członkostwa programu ASP.NET i dostawców ról  
 Program ASP.NET zawiera dostawcy członkostwa i ról. Dostawca jest bazą danych pary nazwa/hasło użytkownika w celu uwierzytelniania wywołań, które również umożliwia określenie uprawnień dostępu do obiektu wywołującego. Usługi WCF można łatwo użyć istniejącego Dostawca członkostwa i ról za pomocą konfiguracji. Przykładową aplikację prezentującą to, zobacz [Dostawca członkostwa i ról](../../../docs/framework/wcf/samples/membership-and-role-provider.md) próbki.  
  
### <a name="credentials-used-by-iis"></a>Poświadczenia używane przez usługi IIS  
 W przeciwieństwie do domeny systemu Windows przez kontroler protokołu Kerberos Internet jest środowisku bez pojedynczy kontroler zarządzania miliony użytkowników logujących się w dowolnym momencie. Zamiast tego poświadczenia w Internecie są najczęściej w postaci certyfikatów X.509 (nazywany także certyfikaty protokołu Secure Sockets Layer lub SSL). Te certyfikaty są zwykle wydawane przez *urzędu certyfikacji*, które mogą być innej firmy, który gwarantuje autentyczności certyfikat i osoby zostały wydane dla. Aby aktywować usługi w Internecie, należy również podać zaufanych certyfikatów do uwierzytelniania usługi.  
  
 Powstaje pytanie w tym momencie, jak można uzyskać taki certyfikat? Jednym z podejść jest urząd certyfikacji innych firm, takich jak Authenticode lub VeriSign, gdy wszystko będzie gotowe do wdrożenia usługi, a następnie Kup certyfikat dla usługi. Jednak jeśli jest na etapie projektowania z programem WCF, a nie jeszcze gotowy można przekazać do zakupu certyfikatu, narzędzi i technik tworzenia certyfikatów X.509, który służy do symulowania wdrożenia produkcyjnego. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Tryby zabezpieczeń  
 Programowanie zabezpieczeń WCF pociąga za sobą kilka punktów krytycznych decyzji. Jednym z najbardziej podstawowa jest wybór *tryb zabezpieczeń*. Są dwa tryby zabezpieczeń głównych *trybu transportu* i *tryb wiadomości*.  
  
 Trzeci tryb, który łączy semantykę oba tryby główne, jest *transportu z trybem poświadczeń komunikatu*.  
  
 Określa tryb zabezpieczeń, jak są zabezpieczone wiadomości, a każdy wybór ma zalety i wady, co zostało opisane poniżej. Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń, zobacz [porady: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Tryb transportu  
 Istnieje kilka warstw między siecią i aplikacji. Jednym z nich jest *transportu* warstwy *,* który zarządza transferu wiadomości między punktami końcowymi. W celu istnieje, jest on tylko wymagane zrozumieć, że WCF używa kilku protokołów transportu, z których każdy bezpiecznego transferu komunikatów. (Aby uzyskać więcej informacji na temat transportów, zobacz [transportów](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Często używane protokół jest HTTP; drugi to TCP. Każdy z tych protokołów, można zabezpieczyć określonego transfer przez mechanizm (lub mechanizmów) komunikatu protokołu. Na przykład protokołu HTTP jest zabezpieczone przy użyciu protokołu SSL za pośrednictwem protokołu HTTP, zwykle skrót "HTTPS". W związku z tym po wybraniu trybu transportu dla zabezpieczeń są Wybieranie używać mechanizmu zgodnie z ustawieniem protokołu. Na przykład w przypadku wybrania <xref:System.ServiceModel.WSHttpBinding> klasy, a jego tryb zabezpieczeń Transport, wybierasz SSL za pośrednictwem protokołu HTTP (HTTPS) jako mechanizm zabezpieczeń. Zaletą trybu transportu jest bardziej efektywne niż tryb wiadomości, ponieważ zabezpieczenia są zintegrowane na stosunkowo niskim poziomie. W trybie transportu mechanizm zabezpieczeń musi być implementowana według specyfikacji dla transportu, a w związku z tym komunikaty mogą przepływać bezpiecznie tylko z point-to-point za pomocą transportu.  
  
#### <a name="message-mode"></a>Tryb wiadomości  
 Z kolei trybu wiadomości bezpieczeństwo przy tym danych zabezpieczeń w ramach każdej wiadomości. Za pomocą XML i zabezpieczeń nagłówki SOAP, poświadczenia i inne dane potrzebne do zapewnienia integralności i poufności wiadomości są dołączone do każdej wiadomości. Każdy komunikat zawiera dane zabezpieczeń tak powoduje w przez na wydajność, ponieważ każdy komunikat muszą być przetwarzane pojedynczo. (W trybie transportu po zabezpieczeniu warstwy transportowej, wszystkie komunikaty przepływać za darmo.) Jednak zabezpieczenia komunikatów ma jedną z zalet za pośrednictwem zabezpieczeń transportu: jest bardziej elastyczne. Oznacza to wymagania dotyczące zabezpieczeń nie są określane przez transport. Można użyć dowolnego typu poświadczeń klienta do zabezpieczenia wiadomości. (W trybie transportu protokołu transportu Określa typ poświadczeń klienta, który można użyć).  
  
#### <a name="transport-with-message-credentials"></a>Transport z poświadczeniami komunikatu  
 Trzeci tryb łączy najlepsze zabezpieczenia transportowe i komunikatu. W tym trybie zabezpieczeń transportu umożliwia wydajne zapewnić poufność i integralności każdej wiadomości. W tym samym czasie co komunikat zawiera jego dane poświadczeń, dzięki czemu komunikat, który ma zostać uwierzytelnione. Przy użyciu uwierzytelniania autoryzacji również może być zaimplementowany. Uwierzytelniając nadawcy, dostęp do zasobów można udzielić (lub odmówić) zgodnie z tożsamość nadawcy.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Określanie typu poświadczeń klienta i wartość poświadczenia  
 Po wybraniu trybu zabezpieczeń, można również określić typ poświadczeń klienta. Typ poświadczeń klienta określa, jakiego typu użyć klienta do samodzielnego uwierzytelnienia do serwera.  
  
 Nie wszystkie scenariusze wymagają jednak typu poświadczeń klienta. Przy użyciu protokołu SSL za pośrednictwem protokołu HTTP (HTTPS), usługa uwierzytelnia się do klienta. W ramach tego uwierzytelnienia, usługi certyfikat zostanie wysłany do klienta w procesie nazywanym *negocjacji*. Transport zabezpieczonego protokołem SSL zapewnia, że wszystkie komunikaty są poufne.  
  
 W przypadku tworzenia usługi, która wymaga uwierzytelnienia klienta, wybór typu poświadczeń klienta zależy transportu i tryb. Na przykład przy użyciu protokołu HTTP i Wybieranie trybu transportu zapewnia kilka opcji, takich jak podstawowe, szyfrowane i inne. (Aby uzyskać więcej informacji o tych poświadczeń typów, zobacz [opis uwierzytelniania HTTP](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 W przypadku tworzenia usługi w domenie systemu Windows, która będzie dostępna tylko do innych użytkowników w sieci, największa łatwość użycia jest typu poświadczeń klienta Windows. Jednak może być również konieczne podanie usługi przy użyciu certyfikatu. Przedstawiono to w [porady: Określanie wartości poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Wartości poświadczeń  
 A *poświadczeń wartość* jest rzeczywiste poświadczenia używane przez usługę. Po określeniu typu poświadczeń również może być konieczne skonfigurowanie usługi przy użyciu poświadczeń rzeczywistych. Jeśli wybrano systemu Windows (usługa zostanie uruchomiona w domenie systemu Windows), nie Określ wartość rzeczywista poświadczenia.  
  
## <a name="identity"></a>Tożsamość  
 W programie WCF termin *tożsamości* ma inną funkcję do serwera i klienta. Krótko mówiąc, podczas uruchamiania usługi, tożsamość jest przypisana do kontekstu zabezpieczeń po uwierzytelnieniu. Aby wyświetlić rzeczywiste tożsamości, sprawdź <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> właściwości <xref:System.ServiceModel.ServiceSecurityContext> klasy. Aby uzyskać więcej informacji, zobacz [porady: badanie kontekstu zabezpieczeń](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Z kolei na kliencie, tożsamość służy do sprawdzania usługi. W czasie projektowania można ustawić deweloperowi klienta [ \<tożsamości >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementu na wartość uzyskane z usługi. W czasie wykonywania klient sprawdza wartość elementu względem rzeczywistej tożsamości usługi. Jeśli sprawdzenie zakończy się niepowodzeniem, klient przerywa komunikacji. Wartość może być główna nazwa użytkownika (UPN), jeśli usługa jest uruchamiana tożsamości danego użytkownika lub główną nazwę usługi (SPN) Jeśli usługa jest uruchamiana na koncie komputera. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usługi](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). Poświadczenia mogą być również certyfikat lub pole znaleziono certyfikatu identyfikujący certyfikat.  
  
## <a name="protection-levels"></a>Poziomy ochrony  
 `ProtectionLevel` Właściwość występuje na kilka klas atrybutów (takie jak <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> klasy). Poziom ochrony jest wartość, która określa, czy wiadomości (lub części wiadomości) obsługujące usługi są podpisywane, podpisane i szyfrowane lub wysyłane bez podpisy i szyfrowania. Aby uzyskać więcej informacji dotyczących właściwości, zobacz [poziom ochrony opis](../../../docs/framework/wcf/understanding-protection-level.md)oraz przykłady programowania, zobacz [porady: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). Aby uzyskać więcej informacji o projektowaniu kontraktu usługi z `ProtectionLevel` w kontekście, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Uwierzytelnianie i tożsamość usług](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Omówienie poziomów ochrony](../../../docs/framework/wcf/understanding-protection-level.md)  
 [Delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Zabezpieczenia](../../../docs/framework/wcf/feature-details/security.md)  
 [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Instrukcje: ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Instrukcje: zabezpieczanie usługi za pomocą poświadczeń systemu Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [Instrukcje: ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Instrukcje: określanie typu poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)  
 [Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Instrukcje: personifikowanie klienta w usłudze](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Instrukcje: badanie kontekstu zabezpieczeń](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
