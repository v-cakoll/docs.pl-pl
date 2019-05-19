---
title: Zabezpieczanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: c4ac823b5419d845437ef8e89f5123adafda0c5a
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881362"
---
# <a name="securing-services"></a>Zabezpieczanie usług
Zabezpieczenia usługi Windows Communication Foundation (WCF) składa się z dwóch podstawowe wymagania: transfer zabezpieczeń i autoryzacja. (Wymaganie trzeci, inspekcja zdarzeń zabezpieczeń jest opisana w [inspekcji](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Krótko mówiąc bezpieczeństwie transferu zawiera uwierzytelniania (potwierdzenia tożsamości klienta i usługę), poufności (szyfrowanie wiadomości) i integralności (cyfrowego podpisywania naruszeniem). Autoryzacja jest kontrola dostępu do zasobów, na przykład, dzięki czemu tylko użytkownicy uprzywilejowani do odczytu pliku. Korzystając z funkcji usługi WCF, dwa podstawowe wymagania są łatwo zaimplementować.  
  
 Z wyjątkiem produktów <xref:System.ServiceModel.BasicHttpBinding> klasy (lub [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element w konfiguracji), bezpieczeństwie transferu jest domyślnie włączona dla wszystkich wstępnie zdefiniowanych powiązań. Tematy w tej sekcji obejmują dwa podstawowe scenariusze: Implementowanie bezpieczeństwie transferu i autoryzacji na intranetową usługę hostowanych na Internet Information Services (IIS) i implementowanie transferu zabezpieczeń i autoryzacja w usłudze hostowanych w usługach IIS.  
  
> [!NOTE]
>  Windows XP Home nie obsługuje uwierzytelniania Windows. W związku z tym nie należy uruchamiać usługę w tym systemie.  
  
## <a name="security-basics"></a>Podstawy zabezpieczeń  
 Zależy od zabezpieczeń *poświadczenia*. Poświadczenia okazuje się, czy jednostka jest kto się podaje. ( *Jednostki* może być osobą, proces oprogramowania, firmy lub wszystko, co może być autoryzowane.) Na przykład klient usługi sprawia, że *oświadczenia* z *tożsamości*, a poświadczenia potwierdza to roszczenie w jakikolwiek sposób. W typowym scenariuszu występuje wymiany poświadczeń. Najpierw usługa sprawia, że oświadczenia swojej tożsamości i okazuje się do klienta przy użyciu poświadczeń. Z drugiej strony klient wykonuje oświadczeń, tożsamości oraz prezentuje poświadczeń z usługą. Jeśli obie strony zaufania poświadczeń drugiej strony, a następnie *bezpiecznym kontekście* można ustalić, w których wszystkie komunikaty są wymieniane w poufności i wszystkie komunikaty zalogowano się do ochrony swoich integralności. Po usługi ustanawia tożsamość klienta, następnie można dopasować oświadczenia w poświadczenie, które *roli* lub *członkostwa* w grupie. W obu przypadkach przy użyciu roli lub grupy, do której należy dany klient, usługa *autoryzuje* klient może wykonywać ograniczony zestaw operacji zależności od uprawnień roli lub grupy.  
  
## <a name="windows-security-mechanisms"></a>Mechanizmy zabezpieczeń Windows  
 Jeśli klient i komputer z usługą są w domenie Windows, która wymaga zarówno do logowania się do sieci, poświadczenia są dostarczane przez infrastrukturę Windows. W takim przypadku poświadczenia są określane podczas logowania użytkownika komputera z siecią. Każdy użytkownik i każdy komputer w sieci muszą być zakwalifikowanymi należących do zaufanych zbioru użytkowników i komputerów. W systemie Windows, co takiego użytkownika i komputera jest także znana jako *podmiotu zabezpieczeń*.  
  
 W domenie Windows objęta *Kerberos* kontrolera, kontroler Kerberos używa schematu, oparte na udzielanie biletów na każdy podmiot zabezpieczeń. Bilety przyznaje kontrolera są zaufane przez inne biletu udzielające w systemie. Zawsze, gdy próbuje wykonać kilka operacji lub dostęp do jednostki *zasobów* (np. plik lub katalog na komputerze),--ticket jest sprawdzany pod kątem jego ważności i, jeśli pomyślnie przejdzie, podmiot zabezpieczeń uzyskuje bilet innej operacji. Ta metoda przyznawania biletów jest bardziej wydajne niż alternatywne próby weryfikacji jednostki dla każdej operacji.  
  
 Starsze, mniej bezpieczne mechanizm używany w domenach Windows jest NT LAN Manager (NTLM). W przypadkach, gdy (zazwyczaj spoza domeny Windows, takich jak grupy roboczej), w którym nie można użyć protokołu Kerberos NTLM może służyć jako alternatywa. Uwierzytelnianie NTLM jest również dostępny jako opcję zabezpieczeń dla usług IIS.  
  
 W systemie Windows autoryzacja działa, przypisując każdego komputera i użytkownika do zestawu ról i grup. Na przykład, musisz skonfigurować i kontrolowane przez osobę (lub grupa osób) w roli każdy komputer Windows *administratora*. Inną rolą jest *użytkownika*, która zawiera zbiór znacznie bardziej ograniczone uprawnienia. Oprócz tej roli użytkownicy są przypisane do grup. Grupy umożliwia wielu użytkownikom do wykonywania w tej samej roli. W praktyce w związku z tym, komputer Windows jest podawana przez przypisywanie użytkowników do grup. Na przykład można przypisać wielu użytkowników do grupy użytkowników komputera i znacznie bardziej ograniczonego zestawu użytkowników można przypisać do grupy administratorów. Na komputerze lokalnym administrator może również tworzyć nowe grupy i przypisanie do grupy innych użytkowników (lub nawet inne grupy).  
  
 Na komputerze z systemem Windows każdy folder w katalogu mogą być chronione. Oznacza to możesz wybrać folder i kontrolowanie, kto może uzyskać dostęp do plików i czy można skopiować pliku lub (w przypadku najbardziej uprzywilejowanych) Zmień pliku, usunięcia pliku lub Dodaj pliki do folderu. Jest to nazywane kontroli dostępu i mechanizmu dla niej jest znany jako listy kontroli dostępu (ACL). Podczas tworzenia listy ACL, można przypisać uprawnienia dostępu do żadnych grup lub grup, a także poszczególnych elementów członkowskich domeny.  
  
 Infrastruktura WCF jest przeznaczony do stosowania tych mechanizmów zabezpieczeń Windows. W związku z tym Jeśli tworzysz usługę wdrożoną w sieci intranet, a których klienci są ograniczone do elementów członkowskich domeny Windows security łatwo jest zaimplementowana. Tylko uprawnieni użytkownicy mogą logować się do domeny. Po zalogowaniu użytkownicy kontrolera Kerberos umożliwia każdemu użytkownikowi na do ustanowienia bezpiecznego kontekstów za pomocą dowolnego komputera lub aplikacji. Na komputerze lokalnym można łatwo tworzyć grupy, a podczas ochrony konkretnych folderów, tych grup można przypisać uprawnienia dostępu na komputerze.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementowanie zabezpieczeń Windows w usługach sieci Intranet  
 Aby zabezpieczyć aplikację, która działa wyłącznie w domenie Windows, można użyć domyślnych ustawień zabezpieczeń albo <xref:System.ServiceModel.WSHttpBinding> lub <xref:System.ServiceModel.NetTcpBinding> powiązania. Domyślnie wszyscy użytkownicy tej samej domenie Windows dostęp do usług WCF. Ponieważ tych użytkowników zalogowanych do sieci, są one zaufane. Wiadomości między usługą i klienta są zaszyfrowane w celu zachowania poufności i podpisana w celu zapewnienia integralności. Aby uzyskać więcej informacji o tym, jak utworzyć usługę, która używa zabezpieczeń Windows, zobacz [jak: Zabezpieczanie usługi za pomocą poświadczeń Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autoryzacja przy użyciu klasy PrincipalPermissionAttribute  
 Jeśli musisz ograniczyć dostęp do zasobów na komputerze, najprostszym sposobem jest użycie <xref:System.Security.Permissions.PrincipalPermissionAttribute> klasy. Ten atrybut pozwala ograniczyć wywoływanie operacji usługi przez wymaganie użytkownika znajdować się w określonej grupie Windows lub roli lub do określonego użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Personifikacja  
 Personifikacja jest inny mechanizm, który służy do kontrolowania dostępu do zasobów. Domyślnie usługa hostowanych przez usługi IIS będzie uruchamiana z tożsamością konto ASPNET. Konto ASPNET dostęp tylko do zasobów, dla których ma uprawnienia. Jednak jest możliwe ustawienie listy ACL dla folderu, aby wykluczyć ASPNET konta usługi, ale w niektórych innych tożsamości dostępu do folderu. Pytanie, następnie staje się jak zezwalają na dostęp do folderu, jeśli konto ASPNET nie jest dozwolone w tym celu. Odpowiedź polega na użyciu personifikacji, według której usługa jest dozwolone użycie poświadczeń klienta w celu uzyskania dostępu do określonego zasobu. Innym przykładem jest podczas uzyskiwania dostępu do bazy danych SQL Server, do którego tylko niektórzy użytkownicy mają uprawnienia. Aby uzyskać więcej informacji na temat Korzystanie z personifikacji, zobacz [jak: Personifikowanie klienta w usłudze](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) i [delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Zabezpieczenia w Internecie  
 Zabezpieczenia w Internecie składa się z takie same wymagania dotyczące bezpieczeństwa w sieci intranet. Usługa musi przedstawić swoje poświadczenia, aby udowodnić, że jego autentyczności, a klienci muszą potwierdzić swoją tożsamość w usłudze. Gdy klient tożsamość jest sprawdzana, usługi można kontrolować jak szeroki dostęp klient ma do zasobów. Ze względu na charakter heterogenicznych Internet, przedstawionych poświadczeń różnią się od tych używanych w domenie Windows. Natomiast kontrolerem Kerberos obsługuje uwierzytelnianie użytkowników w domenie z biletów dla poświadczeń w Internecie, usług i klientów opierają się na jednym z kilka różnych sposobów, aby przedstawić poświadczeń. Celem tego tematu jest jednak przedstawić typowe podejście, które pozwala na tworzenie usługi WCF, który jest dostępny w Internecie.  
  
### <a name="using-iis-and-aspnet"></a>Za pomocą usług IIS i platformy ASP.NET  
 Wymagania dotyczące zabezpieczeń internetowych i mechanizmy rozwiązać te problemy, nie są nowością. Usługi IIS to serwer sieci Web firmy Microsoft do korzystania z Internetu i oferuje wiele funkcji zabezpieczeń, umożliwiające rozwiązanie tych problemów. Ponadto program ASP.NET zawiera funkcje zabezpieczeń, które mogą używać usług WCF. Aby móc korzystać z tych funkcji zabezpieczeń, hostowanie usługi WCF w programie IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Przy użyciu członkostwa platformy ASP.NET i dostawców ról  
 Program ASP.NET zawiera dostawcy członkostwa i ról. Dostawca jest bazą danych pary nazwa/hasło użytkownika do uwierzytelniania wywołań, w których również można określić uprawnienia dostępu do obiektu wywołującego. WCF można łatwo użyć istniejących Dostawca członkostwa i ról za pomocą konfiguracji. Dla przykładowej aplikacji, która pokazuje to, zobacz [Dostawca członkostwa i ról](../../../docs/framework/wcf/samples/membership-and-role-provider.md) próbki.  
  
### <a name="credentials-used-by-iis"></a>Poświadczenia używane przez usługi IIS  
 W przeciwieństwie do domeny Windows objęte kontrolerze protokołu Kerberos Internet jest środowisku bez pojedynczy kontroler Zarządzanie milionami logowania użytkowników w dowolnym momencie. Zamiast tego poświadczenia w Internecie są w większości przypadków w formie certyfikatu x.509 (nazywanego także certyfikaty protokołu Secure Sockets Layer lub SSL). Te certyfikaty są zwykle wydawane przez *urzędu certyfikacji*, które mogą być innej firmy, który gwarantuje autentyczności certyfikat i osoby zostały wydane dla. Aby udostępnić swoje usługi w Internecie, należy również podać zaufanego certyfikatu do uwierzytelniania usługi.  
  
 Powstaje pytanie na tym etapie jak się dostać takiego certyfikatu? Jedno z podejść jest urząd certyfikacji innych firm, takich jak Authenticode lub VeriSign, gdy wszystko jest gotowe do wdrożenia usługi, a następnie Kup certyfikat dla usługi. Jednakże jeśli jesteś w fazie projektowania z programem WCF, a nie jeszcze gotowy, aby zatwierdzić zakupie certyfikatu, narzędzia i techniki tworzenia certyfikatów X.509, który służy do symulowania wdrożenia produkcyjnego. Aby uzyskać więcej informacji, zobacz [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Tryby zabezpieczeń  
 Programowanie zabezpieczeń WCF pociąga za sobą kilka punktów decyzyjnych krytycznych. Jednym z najbardziej podstawowa jest wybór *tryb zabezpieczeń*. Są dwa tryby zabezpieczenia *trybu transportu* i *tryb wiadomości*.  
  
 Trzeci trybu, który łączy semantykę oba tryby główne, jest *transportu z trybem poświadczeń komunikatu*.  
  
 Tryb zabezpieczeń określa, jak są zabezpieczone wiadomości, a każdy ma zalety i wady, co zostało opisane poniżej. Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń, zobacz [jak: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Tryb transportu  
 Istnieje kilka warstw między siecią i aplikacji. Jednym z nich jest *transportu* warstwy *,* której zarządza przesyłaniem komunikatów między punktami końcowymi. W celu istnieje, jest tylko wymagane, że rozumiesz, że WCF używa protokołów transportowych kilka, z których każdy można zabezpieczyć przesyłanie wiadomości. (Aby uzyskać więcej informacji na temat transportów zobacz [transportów](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Protokół najczęściej używany jest protokół HTTP; inny korzysta z protokołu TCP. Każda z tych protokołów można zabezpieczyć określonego transferu za pomocą mechanizmu (lub mechanizmów) komunikatu protokołu. Na przykład protokołu HTTP jest zabezpieczony przy użyciu protokołu SSL za pośrednictwem protokołu HTTP, zwykle skrót "HTTPS". W związku z tym po wybraniu trybu transportu dla zabezpieczeń, wybierania użycie mechanizmu, zgodnie z ustawieniem protokołu. Na przykład w przypadku wybrania <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń Transport, wybierasz protokołu SSL za pośrednictwem protokołu HTTPS (HTTP) jako mechanizmu zabezpieczeń. Zaletą trybu transportu jest ona bardziej efektywne niż tryb wiadomości ponieważ zabezpieczenia są zintegrowane w stosunkowo niski poziom. Podczas korzystania z trybu transportu mechanizm zabezpieczeń muszą być zaimplementowane zgodnie ze specyfikacją dla transportu, a zatem komunikaty mogą przepływać bezpiecznie tylko z point-to-point za pomocą transportu.  
  
#### <a name="message-mode"></a>Tryb wiadomości  
 Z kolei tryb wiadomości zapewnia bezpieczeństwo, umieszczając dane zabezpieczeń w ramach każdej wiadomości. Za pomocą XML i nagłówki zabezpieczeń protokołu SOAP, poświadczenia i inne dane potrzebne do upewnij się, że integralności i poufności wiadomości są dołączone do każdej wiadomości. Każdy komunikat zawiera dane zabezpieczeń, więc wyniki w płatny na wydajność, ponieważ każdy komunikat muszą być przetwarzane osobno. (W trybie transportu, gdy warstwa transportu jest zabezpieczony, wszystkie komunikaty przepływ za darmo.) Jednak zabezpieczenia wiadomości ma jedną z zalet za pośrednictwem zabezpieczeń transportowych: jest bardziej elastyczna. Oznacza to, że wymagania dotyczące zabezpieczeń nie są określane przez transportu. Można użyć dowolnego typu poświadczeń klienta do zabezpieczenia wiadomości. (W trybie transportu protokołu transportowego Określa typ poświadczeń klienta, którego można używać).  
  
#### <a name="transport-with-message-credentials"></a>Transport z poświadczeniami komunikatu  
 Trzeci trybu łączy najlepsze cechy zabezpieczeń transportu i komunikatów. W tym trybie zabezpieczenia transportu służy do wydajnego upewnij się, poufności i integralności każdej wiadomości. W tym samym czasie co komunikat zawiera swoje dane poświadczeń, co pozwala komunikat, który ma zostać uwierzytelniony. Za pomocą uwierzytelniania autoryzacji mogą być implementowane. Korzystając z uwierzytelniania nadawcy, dostęp do zasobów można udzielić (lub odmowa) zgodnie z tożsamością nadawcy.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Określanie typu poświadczeń klienta i wartość poświadczenia  
 Po wybraniu tryb zabezpieczeń, można również określanie typu poświadczeń klienta. Typ poświadczeń klienta określa, jakiego typu klient musi używać do samodzielnego uwierzytelnienia do serwera.  
  
 Nie wszystkie scenariusze wymagają typu poświadczeń klienta, jednak. Przy użyciu protokołu SSL za pośrednictwem protokołu HTTPS (HTTP), usługa samodzielnie przeprowadza uwierzytelnianie klienta. W ramach tego uwierzytelniania, certyfikat usługi zostanie wysłany do klienta w procesie nazywanym *negocjacji*. Transportu zabezpieczonego protokołem SSL gwarantuje, że wszystkie komunikaty są poufne.  
  
 W przypadku tworzenia usługi wymagającej uwierzytelnienia klienta, wybór typu poświadczeń klienta zależy od transportu i tryb. Na przykład za pomocą protokołu HTTP i Wybieranie trybu transportu zapewnia kilka opcji, takich jak podstawowe, szyfrowane i inne. (Aby uzyskać więcej informacji o tych poświadczeń typów, zobacz [opis uwierzytelniania HTTP](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 W przypadku tworzenia usługi w domenie Windows, która będzie dostępna tylko dla innych użytkowników sieci, najprościej jest użyć jest typu poświadczeń klienta Windows. Jednak może być również konieczne świadczenia usług przy użyciu certyfikatu. Jest to pokazane w [jak: Określanie wartości poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Wartości poświadczeń  
 A *poświadczeń wartość* jest rzeczywiste poświadczenia używane przez usługę. Po określeniu typu poświadczeń, również może być konieczne skonfigurowanie usługi przy użyciu rzeczywistego poświadczeń. Jeśli wybrano Windows (i usługa zostanie uruchomiona w domenie Windows), nie można określić wartość rzeczywiste poświadczenia.  
  
## <a name="identity"></a>Tożsamość  
 W programie WCF termin *tożsamości* ma różne znaczenie do serwera i klienta. Krótko mówiąc, po którym jest uruchomiona usługa, tożsamość jest przypisana do kontekstu zabezpieczeń po uwierzytelnieniu. Aby wyświetlić rzeczywistej tożsamości, sprawdź <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> właściwości <xref:System.ServiceModel.ServiceSecurityContext> klasy. Aby uzyskać więcej informacji, zobacz [jak: Badanie kontekstu zabezpieczeń](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Z kolei na kliencie, tożsamość jest używana do weryfikacji usługi. W czasie projektowania można ustawić dewelopera klienta [ \<tożsamości >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementu uzyskaną z usługi. W czasie wykonywania klient sprawdza wartość elementu względem rzeczywistej tożsamości usługi. Jeśli sprawdzenie zakończy się niepowodzeniem, klient przerywa komunikacji. Wartość może być główną nazwę użytkownika (UPN), jeśli usługa jest uruchamiana w ramach tożsamości danego użytkownika lub główną nazwę usługi (SPN), jeśli usługa jest uruchamiana w ramach konta komputera. Aby uzyskać więcej informacji, zobacz [uwierzytelnianie i tożsamość usług](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). Poświadczenia mogą być również certyfikatu lub pola znalezione w certyfikacie, który identyfikuje certyfikatu.  
  
## <a name="protection-levels"></a>Poziomów ochrony  
 `ProtectionLevel` Właściwość występuje na kilka klas atrybutów (takie jak <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> klasy). Poziom ochrony jest wartość, która określa, czy wiadomości (lub części wiadomości) obsługujące usługi są podpisane, podpisane i szyfrowane lub wysyłane bez podpisy i szyfrowania. Aby uzyskać więcej informacji na temat właściwości, zobacz [zrozumieć poziom ochrony](../../../docs/framework/wcf/understanding-protection-level.md)i przykłady programowania, zobacz [jak: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). Aby uzyskać więcej informacji na temat projektowania kontrakt usługi o `ProtectionLevel` w kontekście, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Uwierzytelnianie i tożsamość usług](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Omówienie poziomów ochrony](../../../docs/framework/wcf/understanding-protection-level.md)
- [Delegowanie i personifikacja](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)
- [Zabezpieczenia](../../../docs/framework/wcf/feature-details/security.md)
- [Przegląd zabezpieczeń](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Instrukcje: Ustawianie właściwości ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Instrukcje: Zabezpieczanie usługi za pomocą poświadczeń Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Instrukcje: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
- [Instrukcje: Określanie typu poświadczeń klienta](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
- [Instrukcje: Ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Instrukcje: Personifikowanie klienta w usłudze](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)
- [Instrukcje: Badanie kontekstu zabezpieczeń](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
