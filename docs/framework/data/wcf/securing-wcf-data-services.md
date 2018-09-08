---
title: Zabezpieczanie usług danych WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: 56ece9c2c81f05047e85ab681e7cfe0da65f35b9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195755"
---
# <a name="securing-wcf-data-services"></a>Zabezpieczanie usług danych WCF
W tym temacie opisano zagadnienia dotyczące zabezpieczeń, które są specyficzne dla opracowywanie, wdrażanie i uruchamianie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] i aplikacje uzyskujące dostęp do usług, które obsługują [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Należy również przestrzegać zaleceń dotyczących tworzenia bezpiecznych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.  
  
 Podczas planowania zabezpieczania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]— na podstawie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi, należy rozwiązać zarówno uwierzytelnianie, czyli proces odnajdywania i weryfikowania tożsamości podmiotu zabezpieczeń, jak i autoryzację, czyli proces określania, czy uwierzytelniony podmiot zabezpieczeń może uzyskać dostępu do żądanych zasobów. Należy również rozważyć, czy komunikat na być szyfrowany przy użyciu protokołu SSL.  
  
## <a name="authenticating-client-requests"></a>Uwierzytelnianie żądań klientów  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] nie implementują żadnego rodzaju uwierzytelniania, ale opierają się na funkcjach uwierzytelniania hosta usługi danych. Oznacza to, że usługa zakłada, że każde żądanie, które otrzymuje, zostało już uwierzytelnione przez hosta sieci i że host poprawnie zidentyfikował podmiot zabezpieczeń dla żądania za pośrednictwem interfejsów zapewnianych przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Te opcje uwierzytelniania i podejścia są szczegółowo opisane w [serii protokół OData i uwierzytelnianie](https://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Opcje uwierzytelniania dla usługi danych programu WCF  
 W poniższej tabeli wymieniono niektóre z dostępnych mechanizmów uwierzytelniania, które pomagają w uwierzytelnieniu żądań kierowanych do usługi danych programu WCF.  
  
|Opcje uwierzytelniania|Opis|  
|----------------------------|-----------------|  
|Uwierzytelnianie anonimowe|Jeśli jest włączone uwierzytelnianie anonimowe HTTP, każdy podmiot zabezpieczeń jest w stanie połączyć się z usługą danych. W przypadku dostępu anonimowego nie są wymagane poświadczenia. Użyj tej opcji tylko wtedy, gdy każdemu użytkownikowi chcesz zezwolić na dostęp do usługi danych.|  
|Uwierzytelnianie podstawowe i szyfrowane|Do uwierzytelnienia są wymagane poświadczenia składające się z nazwy użytkownika i hasła. Obsługuje uwierzytelnianie klientów nieopartych na systemie Windows. **Uwaga dotycząca zabezpieczeń:** poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane jako niezaszyfrowane i mogą zostać przechwycone. W przypadku uwierzytelniania szyfrowanego wysyłana jest wartość skrótu oparta na podanych poświadczeniach, co sprawia, że jest ono bezpieczniejsze niż uwierzytelnianie podstawowe. Obie te metody są podatne na ataki man-in-middle. W przypadku korzystania z tych metod uwierzytelniania należy rozważyć szyfrowanie komunikacji między klientem a usługą danych przy użyciu protokołu Secure Sockets Layer (SSL). <br /><br /> Microsoft Internet Information Services (IIS) oferuje implementację zarówno podstawowe i uwierzytelnianie szyfrowane dla protokołu HTTP żądania w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji. Ta implementacja dostawcy uwierzytelniania systemu Windows umożliwia aplikacji klienta programu .NET Framework podanie poświadczeń w nagłówku żądania HTTP skierowanego do usługi danych w celu bezproblemowego wynegocjowania uwierzytelnienia użytkownika systemu Windows. Aby uzyskać więcej informacji, zobacz [dokumentacja techniczna uwierzytelniania szyfrowanego](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Jeśli chcesz mieć swoje dane usługi używała uwierzytelniania podstawowego na podstawie niektórych niestandardowej usłudze uwierzytelniania i nie Windows poświadczeń, musi implementować niestandardowe [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] moduł HTTP do uwierzytelniania.<br /><br /> Na przykład jak używać niestandardowego schematu uwierzytelniania podstawowego z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [niestandardowe uwierzytelnianie podstawowe](https://go.microsoft.com/fwlink/?LinkID=200388) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i uwierzytelniania.|  
|Uwierzytelnianie systemu Windows|Poświadczenia oparte na systemie Windows są wymieniane przy użyciu protokołu NTLM lub Kerberos. Ten mechanizm jest bezpieczniejszy niż uwierzytelnianie podstawowe lub szyfrowane, ale wymaga, aby klient był aplikacją opartą na systemie Windows. Usługi IIS oferuje również implementację uwierzytelniania Windows dla żądań HTTP w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [omówienie uwierzytelniania formularzy programu ASP.NET](https://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> Aby uzyskać przykład sposobu korzystania z uwierzytelniania Windows za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [uwierzytelniania Windows](https://go.microsoft.com/fwlink/?LinkID=200384) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i uwierzytelniania.|  
|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Uwierzytelnianie formularzy|Uwierzytelnianie formularzy pozwala uwierzytelniać użytkowników przy użyciu własnego kodu, a następnie utrzymywać token uwierzytelniania w pliku cookie lub adresie URL strony. Uwierzytelniasz nazwy i hasła użytkowników używających utworzonego przez Ciebie formularza logowania. Nieuwierzytelnione żądania są przekierowywane na stronę logowania, gdzie użytkownik podaje poświadczenia i przesyła formularz. Jeśli aplikacja uwierzytelni żądanie, system wystawia bilet, który zawiera klucz umożliwiający ponowne ustalenie tożsamości dla kolejnych żądań. Aby uzyskać więcej informacji, zobacz [dostawcy uwierzytelniania formularzy](https://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Uwaga dotycząca zabezpieczeń:** domyślnie plik cookie zawierający bilet uwierzytelniania formularzy nie jest zabezpieczony podczas używania uwierzytelniania formularzy w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web. Należy rozważyć wymaganie protokołu SSL w celu ochrony zarówno biletu uwierzytelniania, jak i początkowych poświadczeń logowania. <br /><br /> Na przykład jak używać uwierzytelniania formularzy z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [uwierzytelnianie formularzy](https://go.microsoft.com/fwlink/?LinkID=200389) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i uwierzytelniania.|  
|Uwierzytelnianie oparte na oświadczeniach|W przypadku uwierzytelniania opartego na oświadczeniach Usługa danych zależy od usługi dostawcy zaufanej tożsamości "third-party" w celu uwierzytelnienia użytkownika. Dostawca tożsamości pozytywnie uwierzytelnia użytkownika, który żąda dostępu do zasobów usługi danych, i wystawia token udzielający dostępu do żądanych zasobów. Token ten jest następnie prezentowany usłudze danych, która udziela użytkownikowi dostępu na podstawie relacji zaufania z usługą tożsamości, która wystawiła token dostępu.<br /><br /> Zaletą używania dostawcy uwierzytelniania opartego na oświadczeniach jest to, że tej metody można używać do uwierzytelniania różnych typów klientów między domenami zaufania. Korzystając z takiego dostawcy innej firmy, usługa danych zdejmuje z siebie ciężar obsługi i uwierzytelniania użytkowników. OAuth 2.0 to protokół uwierzytelniania opartego na oświadczeniach, który jest obsługiwany jako usługa federacyjnej autoryzacji przez funkcję kontroli dostępu programu AppFabric systemu Microsoft Azure. Protokół ten obsługuje usługi oparte na protokole REST. Aby uzyskać przykład sposobu korzystania z protokołu OAuth 2.0 z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [OData i OAuth](https://go.microsoft.com/fwlink/?LinkId=200514) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i uwierzytelniania.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Uwierzytelnianie w bibliotece klienta  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta nie podaje poświadczeń, gdy kieruje żądanie do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi. Gdy poświadczenia logowania do uwierzytelnienia użytkownika są wymagane przez usługę danych, te poświadczenia mogą być podawane w <xref:System.Net.NetworkCredential> dostępne z <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>, jak w poniższym przykładzie:  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Określanie poświadczeń klienta dla żądania obsługi danych](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Kiedy usługa danych wymaga poświadczeń logowania, których nie można określić za pomocą <xref:System.Net.NetworkCredential> obiektów, takich jak token oparty na oświadczeniach czy plik cookie, należy ręcznie ustawić nagłówki w żądaniu HTTP zazwyczaj `Authorization` i `Cookie` nagłówków. Aby uzyskać więcej informacji na temat tego rodzaju scenariusza uwierzytelniania, zobacz wpis [protokół OData i uwierzytelnianie: punkty zaczepienia po stronie klienta](https://go.microsoft.com/fwlink/?LinkID=200385). Na przykład sposobu ustawiania nagłówków HTTP w komunikacie żądania zobacz [porady: Ustawianie nagłówków w żądaniu klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Personifikacja  
 Na ogół usługa danych uzyskuje dostęp do wymaganych zasobów, takich jak pliki na serwerze lub baza danych, przy użyciu poświadczeń procesu roboczego hostującego usługę danych. Jeśli korzystanie z personifikacji, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji można wykonywać przy użyciu tożsamości Windows (konto użytkownika) użytkownika zgłaszającego żądanie. Personifikacja jest powszechnie stosowana w aplikacjach, które przy uwierzytelnieniu użytkownika opierają się na programie IIS, i poświadczenia tego podmiotu zabezpieczeń są używane do uzyskiwania dostępu do wymaganych zasobów. Aby uzyskać więcej informacji, zobacz [personifikacji aplikacji ASP.NET](https://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurowanie autoryzacji usługi danych  
 Autoryzacja to udzielenie dostępu do zasobów aplikacji podmiotowi zabezpieczeń lub procesowi, który został zidentyfikowany na podstawie przeprowadzonego wcześniej pomyślnego uwierzytelnienia. Ogólną praktyką jest udzielanie użytkownikom usługi danych tylko uprawnień wystarczających do wykonywania operacji wymaganych przez aplikacje klienta.  
  
### <a name="restrict-access-to-data-service-resources"></a>Ograniczanie dostępu do zasobów usługi danych  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pozwala na udzielanie typowych odczytu i zapisu względem zasobów usługi danych (zestawu jednostek i operacji usługi) każdemu użytkownikowi, który jest w stanie uzyskać dostępu do usługi danych. Reguły, które definiują prawa do odczytu i zapisu, można określić osobno dla każdego zestawu jednostek uwidacznianego przez usługę danych, a także dla każdej operacji usługi. Zaleca się zawężenie zarówno praw do odczytu, jak i do zapisu tylko do zasobów, które są wymagane przez aplikację klienta. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące dostępu do zasobów co najmniej](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Wdrażanie interceptorów opartych na rolach  
 Interceptory umożliwiają przechwytywanie żądań zasobów usługi danych, zanim zostaną one przetworzone przez usługę danych. Aby uzyskać więcej informacji, zobacz [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Interceptory pozwalają na podejmowanie decyzji dotyczących autoryzacji na podstawie uwierzytelnionego użytkownika, który wysłał żądanie. Na przykład jak ograniczyć dostęp do zasobów usługi danych, w oparciu o tożsamość uwierzytelnionego użytkownika zobacz [jak: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Ograniczanie dostępu do trwałego magazynu danych i zasobów lokalnych  
 Kontom, które są używane do uzyskiwania dostępu do magazynu trwałego, należy udzielić w bazie danych lub systemie plików praw wystarczających do obsługi wymagań usługi danych. Jeśli jest używane uwierzytelnianie anonimowe, jest to konto używane do uruchamiania aplikacji macierzystej. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającej na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Jeśli jest używana personifikacja, uwierzytelnionym użytkownikom należy udzielić dostępu do tych zasobów, zwykle jako części grupy systemu Windows.  
  
## <a name="other-security-considerations"></a>Inne uwagi dotyczące zabezpieczeń  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpieczanie danych w ładunku  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jest oparta na protokole HTTP. W komunikacie HTTP nagłówek może zawierać cenne poświadczenia użytkownika, zależnie od uwierzytelniania implementowanego przez usługę danych. Treść komunikatu może również zawierać cenne dane klienta, które muszą być chronione. W obu tych przypadkach zaleca się używanie protokołu SSL do ochrony tych informacji w sieci.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorowane nagłówki komunikatów i pliki cookie  
 Nagłówki żądania HTTP inne niż te, które deklarują typy zawartości i lokalizacje zasobów, są ignorowane i nigdy nie są ustawiane przez usługę danych.  
  
 Pliki cookie może służyć jako część schematu uwierzytelniania, takich jak za pomocą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uwierzytelniania formularzy. Jednak wszelkie pliki cookie HTTP, ustaw w żądaniu przychodzącym są ignorowane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Host usługi danych może przetworzyć plik cookie, ale [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] środowiska uruchomieniowego nigdy nie analizuje ani nie zwraca plików cookie. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta również nie przetwarza plików cookie przesyłanych w odpowiedzi.  
  
### <a name="custom-hosting-requirements"></a>Niestandardowe wymagania hostingu  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] jest tworzona jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji hostowanej w usługach IIS. Pozwala to usłudze danych na korzystanie z zachowań związanych z zabezpieczeniami zaimplementowanych na tej platformie. Można zdefiniować [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługiwane przez hosta niestandardowego. Aby uzyskać więcej informacji, zobacz [Hosting usługi danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Składniki i platforma hostująca usługę danych muszą zapewnić następujące zachowania związane z zabezpieczeniami, aby zapobiec atakom na usługę danych:  
  
-   Ogranicz długość identyfikatora URI akceptowanego w żądaniu usługi danych dla wszystkich możliwych operacji.  
  
-   Ogranicz rozmiar przychodzących i wychodzących komunikatów HTTP.  
  
-   Ogranicz łączną liczbę zaległych żądań w danym momencie.  
  
-   Ogranicz rozmiar nagłówków HTTP i ich wartości, a następnie podaj [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostępu do danych w nagłówkach.  
  
-   Wykrywaj i odpieraj znane ataki, takie jak TCP SYN i ataki przez powtórzenie komunikatu.  
  
### <a name="values-are-not-further-encoded"></a>Wartości nie są już kodowane  
 Wartości właściwości wysyłanych do usługi danych nie są już kodowane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] środowiska uruchomieniowego. Jeśli na przykład właściwość ciągu jednostki zawiera sformatowaną zawartość HTML, znaczniki nie są kodowane w formacie HTML przez usługę danych. Ponadto usługa danych nie koduje już wartości właściwości w odpowiedzi. Biblioteka klienta również nie przeprowadza dodatkowego kodowania.  
  
### <a name="considerations-for-client-applications"></a>Uwagi dotyczące aplikacji klienta  
 Obowiązują następujące zastrzeżenia zabezpieczeń do aplikacji, które używają [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta w celu uzyskania dostępu do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usług:  
  
-   Biblioteka klienta zakłada, że protokoły używane w celu uzyskania dostępu do usługi danych zapewniają odpowiedni poziom zabezpieczeń.  
  
-   Biblioteka klienta używa wszystkich wartości domyślnych dla limitów czasu i opcji analizy podstawowych stosów transportu zapewnianych przez platformę.  
  
-   Biblioteka klienta nie odczytuje żadnych ustawień z plików konfiguracji aplikacji.  
  
-   Biblioteka klienta nie implementuje żadnych mechanizmów dostępu między domenami. W zamian opiera się na mechanizmach zapewnianych przez podstawowy stos HTTP.  
  
-   Biblioteka klienta nie ma żadnych elementów interfejsu użytkownika i nigdy nie próbuje wyświetlać ani renderować danych, które odbiera lub wysyła.  
  
-   Firma Microsoft zaleca, aby aplikacje klienta zawsze weryfikowały dane wprowadzone przez użytkownika, a także akceptowane dane pochodzące z niezaufanych usług.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
