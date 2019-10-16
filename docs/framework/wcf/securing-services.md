---
title: Zabezpieczanie usług
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
ms.openlocfilehash: fa486c31a7c7310f28cbeaac208dddb05d7cf1e7
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320242"
---
# <a name="securing-services"></a>Zabezpieczanie usług
Bezpieczeństwo usługi Windows Communication Foundation (WCF) składa się z dwóch podstawowych wymagań: transferuje zabezpieczenia i autoryzację. (Trzecia wymagana Inspekcja zdarzeń zabezpieczeń jest opisana w temacie [Inspekcja](./feature-details/auditing-security-events.md)). W skrócie zabezpieczenia transferu obejmują uwierzytelnianie (sprawdzając tożsamość usługi i klienta), poufność (szyfrowanie wiadomości) oraz integralność (podpisywanie cyfrowe w celu wykrycia naruszenia). Autoryzacja to kontrola dostępu do zasobów, na przykład umożliwienie odczytywania plików tylko przez uprzywilejowanych użytkowników. Przy użyciu funkcji programu WCF te dwa podstawowe wymagania są łatwo implementowane.  
  
 Z wyjątkiem klasy <xref:System.ServiceModel.BasicHttpBinding> (lub elementu [> \<basicHttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md) w konfiguracji) zabezpieczenia transferu są domyślnie włączone dla wszystkich wstępnie zdefiniowanych powiązań. Tematy w tej sekcji obejmują dwa podstawowe scenariusze: implementowanie zabezpieczeń transferu i autoryzacji w usłudze intranetowej hostowanej na Internet Information Services (IIS) oraz implementowanie zabezpieczeń i autoryzacji transferu w usłudze hostowanej w usługach IIS.  
  
> [!NOTE]
> System Windows XP Home nie obsługuje uwierzytelniania systemu Windows. W związku z tym nie należy uruchamiać usługi w tym systemie.  
  
## <a name="security-basics"></a>Podstawowe informacje o zabezpieczeniach  
 Zabezpieczenia polegają na *poświadczeniach*. Poświadczenie potwierdza, że podmiot jest odpowiedzialny za to, czy jest to roszczenie. ( *Jednostką* może być osoba, proces oprogramowania, firma lub wszystkie elementy, które mogą być autoryzowane). Na przykład klient usługi zgłasza zgłoszenie *tożsamości*, a poświadczenie *to w* jakiś sposób. W typowym scenariuszu następuje wymiana poświadczeń. Najpierw Usługa tworzy zgłoszenie tożsamości i udowadnia go klientowi z poświadczeniami. Z drugiej strony klient tworzy zgłoszenie tożsamości i prezentuje poświadczenia do usługi. Jeśli obie strony ufają pozostałym poświadczeniami, można ustalić *bezpieczny kontekst* , w którym wszystkie komunikaty są wymieniane w poufności, a wszystkie komunikaty są podpisane, aby chronić ich integralność. Gdy usługa ustanowi tożsamość klienta, może następnie dopasować oświadczenia w powiązaniu do *roli* lub *członkostwa* w grupie. W obu przypadkach przy użyciu roli lub grupy, do której należy klient, usługa *autoryzuje* klienta do wykonania ograniczonego zestawu operacji na podstawie uprawnień roli lub grupy.  
  
## <a name="windows-security-mechanisms"></a>Mechanizmy zabezpieczeń systemu Windows  
 Jeśli klient i komputer usługi znajdują się w domenie systemu Windows, która wymaga logowania do sieci, poświadczenia są udostępniane przez infrastrukturę systemu Windows. W takim przypadku poświadczenia są ustanawiane, gdy użytkownik komputera loguje się do sieci. Każdy użytkownik i każdy komputer w sieci musi być zweryfikowany jako należący do zaufanego zestawu użytkowników i komputerów. W systemie Windows każdy taki użytkownik i komputer jest również znany jako *podmiot zabezpieczeń*.  
  
 W domenie systemu Windows objętej kontrolerem *Kerberos* kontroler Kerberos używa schematu opartego na udzielaniu biletów do każdego podmiotu zabezpieczeń. Bilety przyznane przez kontrolera są uznawane za zaufane przez innych kredytodawców biletów w systemie. Za każdym razem, gdy jednostka podejmie próbę wykonania jakiejś operacji lub uzyskania dostępu do *zasobu* (na przykład pliku lub katalogu na maszynie), bilet jest sprawdzany pod kątem jego ważności i, jeśli przekazuje, podmiot zabezpieczeń otrzymuje kolejny bilet dla operacji. Ta metoda przyznawania biletów jest bardziej wydajna niż alternatywa podczas próby zweryfikowania podmiotu zabezpieczeń dla każdej operacji.  
  
 Starszy, mniej bezpieczny mechanizm używany w domenach systemu Windows to NT LAN Manager (NTLM). W przypadkach, gdy nie można użyć protokołu Kerberos (zwykle poza domeną systemu Windows, na przykład w grupie roboczej), można użyć uwierzytelniania NTLM jako alternatywy. Protokół NTLM jest również dostępny jako opcja zabezpieczeń dla usług IIS.  
  
 W systemie Windows autoryzacja działa przez przypisanie każdego komputera i użytkownika do zestawu ról i grup. Na przykład każdy komputer z systemem Windows musi być skonfigurowany i kontrolowany przez osobę (lub grupę osób) w roli *administratora*. Inna rola to *użytkownik*, który ma znacznie więcej ograniczonego zestawu uprawnień. Oprócz roli użytkownicy są przypisani do grup. Grupa umożliwia wielu użytkownikom wykonywanie w tej samej roli. W związku z tym, komputer z systemem Windows jest zarządzany przez przypisanie użytkowników do grup. Na przykład kilku użytkowników może być przypisanych do grupy użytkowników komputera, a do grupy administratorów można przypisać znacznie bardziej ograniczony zestaw użytkowników. Na komputerze lokalnym administrator może również tworzyć nowe grupy i przypisywać innych użytkowników (lub nawet inne grupy) do grupy.  
  
 Na komputerze z systemem Windows każdy folder w katalogu może być chroniony. Oznacza to, że można wybrać folder i kontrolować, kto może uzyskać dostęp do plików, oraz czy można skopiować plik lub (w większości przypadków uprzywilejowanych) zmienić plik, usunąć plik lub dodać pliki do folderu. Jest to znane jako kontrola dostępu, a mechanizm dla niego jest znany jako lista kontroli dostępu (ACL). Podczas tworzenia listy ACL można przypisywać uprawnienia dostępu do dowolnych grup lub grup, a także poszczególnych członków domeny.  
  
 Infrastruktura WCF została zaprojektowana tak, aby korzystała z tych mechanizmów zabezpieczeń systemu Windows. W związku z tym, jeśli tworzysz usługę wdrożoną w intranecie, której klienci są ograniczeni do członków domeny systemu Windows, zabezpieczenia można łatwo zaimplementować. Tylko Prawidłowi użytkownicy mogą logować się do domeny. Po zalogowaniu się użytkowników kontroler protokołu Kerberos umożliwia każdemu użytkownikowi ustanowienie bezpiecznych kontekstów z dowolnym innym komputerem lub aplikacją. Na komputerze lokalnym grupy mogą być łatwo tworzone i w przypadku ochrony określonych folderów te grupy mogą służyć do przypisywania uprawnień dostępu na komputerze.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementowanie zabezpieczeń systemu Windows w usługach intranetowych  
 Aby zabezpieczyć aplikację, która działa wyłącznie w domenie systemu Windows, można użyć domyślnych ustawień zabezpieczeń dla powiązania <xref:System.ServiceModel.WSHttpBinding> lub <xref:System.ServiceModel.NetTcpBinding>. Domyślnie każdy w tej samej domenie systemu Windows może uzyskiwać dostęp do usług WCF. Ponieważ Ci użytkownicy byli zalogowani w sieci, są one zaufane. Komunikaty między usługą a klientem są szyfrowane w celu poufności i podpisywane pod kątem integralności. Aby uzyskać więcej informacji na temat sposobu tworzenia usługi korzystającej z zabezpieczeń systemu Windows, zobacz [How to: Secure a Service with Windows Credentials](how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autoryzacja przy użyciu klasy PrincipalPermissionAttribute  
 Jeśli trzeba ograniczyć dostęp do zasobów na komputerze, najprostszym sposobem jest użycie klasy <xref:System.Security.Permissions.PrincipalPermissionAttribute>. Ten atrybut umożliwia ograniczenie wywołania operacji usługi przez wymaganie, aby użytkownik znajdował się w określonej grupie lub roli systemu Windows lub być określonym użytkownikiem. Aby uzyskać więcej informacji, zobacz [How to: ograniczanie dostępu za pomocą klasy PrincipalPermissionAttribute](how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Personifikacja  
 Personifikacja jest innym mechanizmem, który służy do kontrolowania dostępu do zasobów. Domyślnie usługa hostowana przez usługi IIS będzie uruchamiana w ramach tożsamości konta ASPNET. Konto ASPNET może uzyskać dostęp tylko do zasobów, do których ma uprawnienia. Istnieje jednak możliwość ustawienia listy ACL dla folderu, aby wykluczyć konto usługi ASPNET, ale zezwolić określonym innym tożsamościom na dostęp do tego folderu. Następnie pytanie, jak zezwolić tym użytkownikom na dostęp do folderu, jeśli konto ASPNET nie jest dozwolone. Odpowiedź polega na użyciu personifikacji, za pomocą którego usługa może uzyskiwać dostęp do określonego zasobu przy użyciu poświadczeń klienta. Innym przykładem jest uzyskiwanie dostępu do bazy danych SQL Server, do której tylko niektórzy użytkownicy mają uprawnienia. Aby uzyskać więcej informacji o używaniu personifikacji, zobacz [How to: personifikuje klienta w ramach usługi](how-to-impersonate-a-client-on-a-service.md) i [delegowania oraz personifikacji](./feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Zabezpieczenia w Internecie  
 Zabezpieczenia w Internecie obejmują te same wymagania co zabezpieczenia w intranecie. Usługa musi przedstawić swoje poświadczenia, aby potwierdzić jego autentyczność, a klienci muszą udowodnić swoją tożsamość w usłudze. Po pobraniu tożsamości klienta usługa może kontrolować, jak dużo dostępu klient ma do zasobów. Jednak ze względu na niejednorodny charakter Internetu podane poświadczenia różnią się od tych używanych w domenie systemu Windows. Kontroler protokołu Kerberos obsługuje uwierzytelnianie użytkowników w domenie z biletami dla poświadczeń, w Internecie, usług i klientów polega na jednym z kilku różnych sposobów na zaprezentowanie poświadczeń. Celem tego tematu jest jednak zaprezentowanie typowego podejścia, które umożliwia utworzenie usługi WCF dostępnej w Internecie.  
  
### <a name="using-iis-and-aspnet"></a>Korzystanie z usług IIS i ASP.NET  
 Wymagania dotyczące zabezpieczeń internetowych oraz mechanizmów rozwiązywania tych problemów nie są nowe. Usługi IIS to serwer sieci Web firmy Microsoft dla Internetu i ma wiele funkcji zabezpieczeń, które są związane z tymi problemami. Ponadto ASP.NET zawiera funkcje zabezpieczeń, które mogą być używane przez usługi WCF. Aby skorzystać z tych funkcji zabezpieczeń, należy hostować usługę WCF w usługach IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Korzystanie z członkostwa ASP.NET i dostawców ról  
 ASP.NET obejmuje członkostwo i dostawcę ról. Dostawca to baza danych par nazwa użytkownika i hasło do uwierzytelniania wywołujących, które umożliwiają również Określanie uprawnień dostępu każdego wywołującego. Za pomocą programu WCF można łatwo korzystać z istniejącej członkostwa i dostawcy ról za pomocą konfiguracji. Aby zapoznać się z przykładową aplikacją, która ilustruje tę funkcję, zobacz przykład [członkostwa i dostawcy ról](./samples/membership-and-role-provider.md) .  
  
### <a name="credentials-used-by-iis"></a>Poświadczenia używane przez usługi IIS  
 W przeciwieństwie do domeny systemu Windows objętej kontrolerem Kerberos, Internet to środowisko bez jednego kontrolera do zarządzania milionów użytkowników logujących się w dowolnym momencie. Zamiast tego poświadczenia w Internecie najczęściej są w postaci certyfikatów X. 509 (znanych również jako SSL lub SSL, certyfikaty). Te certyfikaty są zwykle wydawane przez *urząd certyfikacji*, który może być firmą innej firmy, która zagwarantuje autentyczność certyfikatu i osobę, do której został wystawiony. Aby udostępnić usługę w Internecie, należy również podać certyfikat zaufany w celu uwierzytelnienia usługi.  
  
 W tym momencie pojawi się pytanie, jak uzyskać taki certyfikat? Jednym z rozwiązań jest przechodzenie do urzędu certyfikacji innej firmy, takiego jak Authenticode lub VeriSign, w przypadku gotowości do wdrożenia usługi i zakupu certyfikatu dla usługi. Jednak jeśli jesteś w fazie opracowywania w programie WCF i nie jest jeszcze gotowy do zatwierdzania zakupu certyfikatu, narzędzia i techniki istnieją do tworzenia certyfikatów X. 509, których można użyć do symulowania wdrożenia produkcyjnego. Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](./feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Tryby zabezpieczeń  
 Programowanie zabezpieczeń WCF obejmuje kilka krytycznych punktów decyzji. Jednym z najważniejszych jest wybór *trybu zabezpieczeń*. Dwa główne tryby zabezpieczeń to *Tryb transportu* i *tryb komunikatów*.  
  
 Trzeci tryb, który łączy semantykę obu trybów głównych, jest *transport z trybem poświadczeń komunikatów*.  
  
 Tryb zabezpieczeń określa sposób zabezpieczania wiadomości, a każdy wybór ma zalety i wady, jak wyjaśniono poniżej. Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń, zobacz [How to: Set a Security Mode](how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Tryb transportu  
 Istnieje kilka warstw między siecią i aplikacją. Jedną z nich jest warstwa *transportu* *,* która zarządza transferem komunikatów między punktami końcowymi. W obecnym przeznaczeniu należy zrozumieć, że program WCF korzysta z kilku protokołów transportu, z których każdy może zabezpieczyć transfer komunikatów. (Aby uzyskać więcej informacji na temat Transports, zobacz [Transports](./feature-details/transports.md)).  
  
 Powszechnie używanym protokołem jest HTTP; innym jest TCP. Każdy z tych protokołów może zabezpieczyć transfer komunikatów przez mechanizm (lub mechanizmy) określony dla protokołu. Na przykład protokół HTTP jest zabezpieczony przy użyciu protokołu SSL przez protokół HTTP, powszechnie skrócony jako "HTTPS". W takim przypadku wybranie trybu transportu dla zabezpieczeń polega na wybraniu mechanizmu do użycia przez protokół. Jeśli na przykład wybierzesz klasę <xref:System.ServiceModel.WSHttpBinding> i ustawisz jej tryb zabezpieczeń na transport, wybierasz protokół SSL za pośrednictwem protokołu HTTP (HTTPS) jako mechanizm zabezpieczeń. Zaletą trybu transportu jest wydajniejsze przekroczenie trybu komunikatów, ponieważ zabezpieczenia są zintegrowane na niskim poziomie. W przypadku korzystania z trybu transportu mechanizm zabezpieczeń musi być zaimplementowany zgodnie ze specyfikacją transportu, dzięki czemu komunikaty mogą być bezpiecznie przesyłane tylko z punktu do punktu w ramach transportu.  
  
#### <a name="message-mode"></a>Tryb wiadomości  
 W przeciwieństwie do trybu wiadomości zapewnia zabezpieczenia, dołączając dane zabezpieczeń w ramach każdej wiadomości. Przy użyciu nagłówków XML i SOAP Security, poświadczenia i inne dane potrzebne do zapewnienia integralności i poufności wiadomości są zawarte w każdej wiadomości. Każdy komunikat zawiera dane o zabezpieczeniach, dlatego w wyniku narzucania opłaty są narzucane, ponieważ każdy komunikat musi być przetworzony indywidualnie. (W trybie transportu po zabezpieczeniu warstwy transportu wszystkie komunikaty są swobodnie przepływem). Jednak zabezpieczenia komunikatów mają jedną korzyść w porównaniu z zabezpieczeniami transportu: jest to bardziej elastyczne. Oznacza to, że wymagania dotyczące zabezpieczeń nie są określane przez transport. Aby zabezpieczyć komunikat, można użyć dowolnego typu poświadczeń klienta. (W trybie transportu protokół transportu określa typ poświadczeń klienta, których można użyć).  
  
#### <a name="transport-with-message-credentials"></a>Transport z poświadczeniami wiadomości  
 Trzeci tryb polega na tym, że zarówno transport, jak i zabezpieczenia komunikatów. W tym trybie zabezpieczenia transportu są używane do wydajnego zapewnienia poufności i integralności każdej wiadomości. W tym samym czasie każdy komunikat zawiera dane poświadczeń, co umożliwia uwierzytelnienie komunikatu. Przy użyciu uwierzytelniania można również zaimplementować autoryzację. Przez uwierzytelnienie nadawcy można udzielić dostępu do zasobów (lub go odmówić) zgodnie z tożsamością nadawcy.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Określanie typu poświadczeń klienta i wartości poświadczeń  
 Po wybraniu trybu zabezpieczeń można także określić typ poświadczeń klienta. Typ poświadczeń klienta określa, jakiego typu klient musi użyć do samodzielnego uwierzytelnienia na serwerze.  
  
 Nie wszystkie scenariusze wymagają jednak typu poświadczeń klienta. Przy użyciu protokołu SSL za pośrednictwem protokołu HTTP (HTTPS) usługa uwierzytelnia siebie na kliencie. W ramach tego uwierzytelniania certyfikat usługi jest wysyłany do klienta w procesie nazywanym *negocjowaniem*. Transport zabezpieczony przy użyciu protokołu SSL gwarantuje, że wszystkie komunikaty są poufne.  
  
 Jeśli tworzysz usługę, która wymaga uwierzytelnienia klienta, wybór typu poświadczeń klienta zależy od transportu i wybranego trybu. Na przykład przy użyciu transportu HTTP i wybrania trybu transportu oferuje kilka opcji, takich jak podstawowa, skrót i inne. (Aby uzyskać więcej informacji na temat tych typów poświadczeń, zobacz [Opis uwierzytelniania HTTP](./feature-details/understanding-http-authentication.md)).  
  
 W przypadku tworzenia usługi w domenie systemu Windows, która będzie dostępna tylko dla innych użytkowników sieci, najłatwiej jest użyć typu poświadczeń klienta systemu Windows. Może być jednak konieczne dostarczenie usługi przy użyciu certyfikatu. Pokazano to w temacie [How to: Określanie wartości poświadczeń klienta](how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Wartości poświadczeń  
 *Wartość poświadczenia* to rzeczywiste poświadczenie wykorzystywane przez usługę. Po określeniu typu poświadczeń może być również konieczne skonfigurowanie usługi przy użyciu rzeczywistych poświadczeń. Jeśli wybrano opcję Windows (a usługa zostanie uruchomiona w domenie systemu Windows), nie należy określać rzeczywistej wartości poświadczeń.  
  
## <a name="identity"></a>Tożsamość  
 W programie WCF termin *tożsamość* ma inne znaczenie dla serwera i klienta. W krótkim czasie, podczas uruchamiania usługi, tożsamość jest przypisywana do kontekstu zabezpieczeń po uwierzytelnieniu. Aby wyświetlić rzeczywistą tożsamość, sprawdź właściwości <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> i <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> klasy <xref:System.ServiceModel.ServiceSecurityContext>. Aby uzyskać więcej informacji, zobacz [How to: Badanie kontekstu zabezpieczeń](how-to-examine-the-security-context.md).  
  
 W przeciwieństwie do klienta tożsamość jest używana do weryfikacji usługi. W czasie projektowania deweloper klienta może ustawić [\<identity >](../configure-apps/file-schema/wcf/identity.md) elementu na wartość uzyskaną z usługi. W czasie wykonywania klient sprawdza wartość elementu względem rzeczywistej tożsamości usługi. Jeśli sprawdzenie zakończy się niepowodzeniem, klient kończy komunikację. Wartość może być główną nazwą użytkownika (UPN), jeśli usługa jest uruchamiana w ramach tożsamości określonego użytkownika lub nazwy głównej usługi (SPN), jeśli usługa jest uruchomiona w ramach konta komputera. Aby uzyskać więcej informacji, zobacz [tożsamość usługi i uwierzytelnianie](./feature-details/service-identity-and-authentication.md). Poświadczenie może być również certyfikatem lub polem znalezionym w certyfikacie, który identyfikuje certyfikat.  
  
## <a name="protection-levels"></a>Poziomy ochrony  
 Właściwość `ProtectionLevel` występuje w przypadku kilku klas atrybutów (takich jak <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute>). Poziom ochrony to wartość określająca, czy komunikaty (lub części komunikatów) obsługujące usługę są podpisane, podpisane i szyfrowane lub wysyłane bez podpisu lub szyfrowania. Aby uzyskać więcej informacji na temat właściwości, zobacz [Opis poziomu ochrony](understanding-protection-level.md)i dla przykładów programowania, zobacz [How to: Set Właściwość ProtectionLevel](how-to-set-the-protectionlevel-property.md). Aby uzyskać więcej informacji na temat projektowania kontraktu usługi z `ProtectionLevel` w kontekście, zobacz [Projektowanie kontraktów usług](designing-service-contracts.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [Uwierzytelnianie i tożsamość usług](./feature-details/service-identity-and-authentication.md)
- [Omówienie poziomów ochrony](understanding-protection-level.md)
- [Delegowanie i personifikacja](./feature-details/delegation-and-impersonation-with-wcf.md)
- [Projektowanie kontraktów usług](designing-service-contracts.md)
- [Security](./feature-details/security.md)
- [Przegląd zabezpieczeń](./feature-details/security-overview.md)
- [Instrukcje: ustawianie właściwości ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Instrukcje: zabezpieczanie usługi za pomocą poświadczeń systemu Windows](how-to-secure-a-service-with-windows-credentials.md)
- [Instrukcje: ustawianie trybu zabezpieczeń](how-to-set-the-security-mode.md)
- [Instrukcje: określanie typu poświadczeń klienta](how-to-specify-the-client-credential-type.md)
- [Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute](how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Instrukcje: personifikowanie klienta w usłudze](how-to-impersonate-a-client-on-a-service.md)
- [Instrukcje: badanie kontekstu zabezpieczeń](how-to-examine-the-security-context.md)
