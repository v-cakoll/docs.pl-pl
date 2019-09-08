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
ms.openlocfilehash: 642ff5fe3427509a4d4782fb8640f4b755d58459
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790342"
---
# <a name="securing-wcf-data-services"></a>Zabezpieczanie usług danych WCF
W tym temacie opisano zagadnienia dotyczące zabezpieczeń, które są specyficzne dla opracowywania, wdrażania i uruchamiania Usługi danych programu WCF i aplikacji, które obsługują usługę Open Data Protocol (OData). Należy również postępować zgodnie z zaleceniami dotyczącymi tworzenia bezpiecznych aplikacji .NET Framework.  
  
Planując sposób zabezpieczania usługi OData opartej na Usługi danych programu WCF, należy rozwiązać oba uwierzytelnianie, proces odnajdywania i weryfikowania tożsamości podmiotu zabezpieczeń oraz autoryzację, proces określania, czy uwierzytelniony podmiot zabezpieczeń jest zezwolenie na dostęp do żądanych zasobów. Należy również rozważyć, czy komunikat na być szyfrowany przy użyciu protokołu SSL.  
  
## <a name="authenticating-client-requests"></a>Uwierzytelnianie żądań klientów  
Usługi danych programu WCF nie implementuje żadnego rodzaju uwierzytelniania, ale raczej opiera się na postanowieniach uwierzytelniania hosta usługi danych. Oznacza to, że usługa zakłada, że wszelkie odebrane żądania zostały już uwierzytelnione przez hosta sieci i że host prawidłowo zidentyfikował zasadę dla żądania odpowiednio za pośrednictwem interfejsów zapewnianych przez Usługi danych programu WCF. Te opcje uwierzytelniania i podejścia opisano szczegółowo w wieloczęściowych [seriach OData i uwierzytelniania](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Opcje uwierzytelniania dla usługi danych programu WCF  
 W poniższej tabeli wymieniono niektóre z dostępnych mechanizmów uwierzytelniania, które pomagają w uwierzytelnieniu żądań kierowanych do usługi danych programu WCF.  
  
|Opcje uwierzytelniania|Opis|  
|----------------------------|-----------------|  
|Uwierzytelnianie anonimowe|Jeśli jest włączone uwierzytelnianie anonimowe HTTP, każdy podmiot zabezpieczeń jest w stanie połączyć się z usługą danych. W przypadku dostępu anonimowego nie są wymagane poświadczenia. Użyj tej opcji tylko wtedy, gdy każdemu użytkownikowi chcesz zezwolić na dostęp do usługi danych.|  
|Uwierzytelnianie podstawowe i szyfrowane|Do uwierzytelnienia są wymagane poświadczenia składające się z nazwy użytkownika i hasła. Obsługuje uwierzytelnianie klientów nieopartych na systemie Windows. **Uwaga dotycząca zabezpieczeń:**  Poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane jako niezaszyfrowane i mogą zostać przechwycone. W przypadku uwierzytelniania szyfrowanego wysyłana jest wartość skrótu oparta na podanych poświadczeniach, co sprawia, że jest ono bezpieczniejsze niż uwierzytelnianie podstawowe. Obie te metody są podatne na ataki man-in-middle. W przypadku korzystania z tych metod uwierzytelniania należy rozważyć szyfrowanie komunikacji między klientem a usługą danych przy użyciu protokołu Secure Sockets Layer (SSL). <br /><br /> Program Microsoft Internet Information Services (IIS) zapewnia implementację zarówno uwierzytelniania podstawowego, jak i szyfrowanego dla żądań HTTP w aplikacji ASP.NET. Ta implementacja dostawcy uwierzytelniania systemu Windows umożliwia aplikacji klienta programu .NET Framework podanie poświadczeń w nagłówku żądania HTTP skierowanego do usługi danych w celu bezproblemowego wynegocjowania uwierzytelnienia użytkownika systemu Windows. Aby uzyskać więcej informacji, zobacz [Informacje techniczne dotyczące uwierzytelniania szyfrowanego](https://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Jeśli chcesz, aby usługa danych korzystała z uwierzytelniania podstawowego na podstawie pewnej niestandardowej usługi uwierzytelniania, a nie poświadczeń systemu Windows, musisz zaimplementować niestandardowy moduł HTTP ADP.NET na potrzeby uwierzytelniania.<br /><br /> Przykład używania niestandardowego schematu uwierzytelniania podstawowego z Usługi danych programu WCF można znaleźć w blogu wpis [OData i uwierzytelnianie — część 6 — niestandardowe uwierzytelnianie podstawowe](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Uwierzytelnianie systemu Windows|Poświadczenia oparte na systemie Windows są wymieniane przy użyciu protokołu NTLM lub Kerberos. Ten mechanizm jest bezpieczniejszy niż uwierzytelnianie podstawowe lub szyfrowane, ale wymaga, aby klient był aplikacją opartą na systemie Windows. Usługi IIS zapewniają również implementację uwierzytelniania systemu Windows dla żądań HTTP w aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [Omówienie uwierzytelniania formularzy ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Przykład korzystania z uwierzytelniania systemu Windows za pomocą Usługi danych programu WCF można znaleźć w blogu wpis [OData i uwierzytelnianie — część 2 — uwierzytelnianie systemu Windows](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|Uwierzytelnianie formularzy ASP.NET|Uwierzytelnianie formularzy pozwala uwierzytelniać użytkowników przy użyciu własnego kodu, a następnie utrzymywać token uwierzytelniania w pliku cookie lub adresie URL strony. Uwierzytelniasz nazwy i hasła użytkowników używających utworzonego przez Ciebie formularza logowania. Nieuwierzytelnione żądania są przekierowywane na stronę logowania, gdzie użytkownik podaje poświadczenia i przesyła formularz. Jeśli aplikacja uwierzytelni żądanie, system wystawia bilet, który zawiera klucz umożliwiający ponowne ustalenie tożsamości dla kolejnych żądań. Aby uzyskać więcej informacji, zobacz temat [dostawca uwierzytelniania formularzy](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Uwaga dotycząca zabezpieczeń:**  Domyślnie plik cookie zawierający bilet uwierzytelniania formularzy nie jest zabezpieczony, gdy używane jest uwierzytelnianie formularzy w aplikacji sieci Web ASP.NET. Należy rozważyć wymaganie protokołu SSL w celu ochrony zarówno biletu uwierzytelniania, jak i początkowych poświadczeń logowania. <br /><br /> Przykład korzystania z uwierzytelniania formularzy przy użyciu Usługi danych programu WCF można znaleźć w blogu wpis [OData i uwierzytelnianie — część 7 — uwierzytelnianie formularzy](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Uwierzytelnianie oparte na oświadczeniach|W przypadku uwierzytelniania opartego na oświadczeniach usługa danych opiera się na zaufanej usłudze dostawcy tożsamości "innej firmy" w celu uwierzytelnienia użytkownika. Dostawca tożsamości pozytywnie uwierzytelnia użytkownika, który żąda dostępu do zasobów usługi danych, i wystawia token udzielający dostępu do żądanych zasobów. Token ten jest następnie prezentowany usłudze danych, która udziela użytkownikowi dostępu na podstawie relacji zaufania z usługą tożsamości, która wystawiła token dostępu.<br /><br /> Zaletą używania dostawcy uwierzytelniania opartego na oświadczeniach jest to, że tej metody można używać do uwierzytelniania różnych typów klientów między domenami zaufania. Korzystając z takiego dostawcy innej firmy, usługa danych zdejmuje z siebie ciężar obsługi i uwierzytelniania użytkowników. OAuth 2.0 to protokół uwierzytelniania opartego na oświadczeniach, który jest obsługiwany jako usługa federacyjnej autoryzacji przez funkcję kontroli dostępu programu AppFabric systemu Microsoft Azure. Protokół ten obsługuje usługi oparte na protokole REST. Przykład korzystania z protokołu OAuth 2,0 z Usługi danych programu WCF można znaleźć w blogu wpis [OData i uwierzytelnianie — część 8 — Zawijanie OAuth](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Uwierzytelnianie w bibliotece klienta  
 Domyślnie Biblioteka klienta Usługi danych programu WCF nie dostarcza poświadczeń podczas wykonywania żądania do usługi OData. Poświadczenia logowania są wymagane przez usługę danych do uwierzytelnienia użytkownika, ale te poświadczenia mogą być dostarczane w <xref:System.Net.NetworkCredential> celu uzyskania dostępu <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> z właściwości <xref:System.Data.Services.Client.DataServiceContext>, jak w poniższym przykładzie:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [jak: Określ poświadczenia klienta dla żądania](specify-client-creds-for-a-data-service-request-wcf.md)usługi danych.  
  
 Gdy usługa danych wymaga poświadczeń logowania, których nie można określić za pomocą <xref:System.Net.NetworkCredential> obiektu, takiego jak token lub plik cookie oparty na oświadczeniach, należy ręcznie ustawić nagłówki w żądaniu HTTP, `Authorization` zazwyczaj w nagłówkach i `Cookie` . Aby uzyskać więcej informacji na temat tego rodzaju scenariusza uwierzytelniania, zobacz wpis w blogu dane [OData i uwierzytelnianie — część 3 — punkty zaczepienia opóźnienie](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Aby zapoznać się z przykładem sposobu ustawiania nagłówków HTTP w komunikacie żądania, [zobacz How to: Ustaw nagłówki w żądaniu](how-to-set-headers-in-the-client-request-wcf-data-services.md)klienta.  
  
## <a name="impersonation"></a>Personifikacja  
 Na ogół usługa danych uzyskuje dostęp do wymaganych zasobów, takich jak pliki na serwerze lub baza danych, przy użyciu poświadczeń procesu roboczego hostującego usługę danych. W przypadku korzystania z personifikacji aplikacje ASP.NET mogą być wykonywane przy użyciu tożsamości systemu Windows (konta użytkownika) użytkownika wysyłającego żądanie. Personifikacja jest powszechnie stosowana w aplikacjach, które przy uwierzytelnieniu użytkownika opierają się na programie IIS, i poświadczenia tego podmiotu zabezpieczeń są używane do uzyskiwania dostępu do wymaganych zasobów. Aby uzyskać więcej informacji, zobacz [ASP.NET personifikacji](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurowanie autoryzacji usługi danych  
 Autoryzacja to udzielenie dostępu do zasobów aplikacji podmiotowi zabezpieczeń lub procesowi, który został zidentyfikowany na podstawie przeprowadzonego wcześniej pomyślnego uwierzytelnienia. Ogólną praktyką jest udzielanie użytkownikom usługi danych tylko uprawnień wystarczających do wykonywania operacji wymaganych przez aplikacje klienta.  
  
### <a name="restrict-access-to-data-service-resources"></a>Ograniczanie dostępu do zasobów usługi danych  
 Domyślnie Usługi danych programu WCF umożliwia przyznawanie typowego dostępu do odczytu i zapisu do zasobów usługi danych (zestawów jednostek i operacji usługi) wszystkim użytkownikom, którzy mogą uzyskać dostęp do usługi danych. Reguły, które definiują prawa do odczytu i zapisu, można określić osobno dla każdego zestawu jednostek uwidacznianego przez usługę danych, a także dla każdej operacji usługi. Zaleca się zawężenie zarówno praw do odczytu, jak i do zapisu tylko do zasobów, które są wymagane przez aplikację klienta. Aby uzyskać więcej informacji, zobacz [minimalne wymagania dotyczące dostępu do zasobów](configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Wdrażanie interceptorów opartych na rolach  
 Interceptory umożliwiają przechwytywanie żądań zasobów usługi danych, zanim zostaną one przetworzone przez usługę danych. Aby uzyskać więcej informacji, zobacz [Interceptory](interceptors-wcf-data-services.md). Interceptory pozwalają na podejmowanie decyzji dotyczących autoryzacji na podstawie uwierzytelnionego użytkownika, który wysłał żądanie. Aby zapoznać się z przykładem ograniczenia dostępu do zasobów usługi danych na podstawie tożsamości uwierzytelnionego użytkownika, zobacz [How to: Komunikaty](how-to-intercept-data-service-messages-wcf-data-services.md)usługi przechwytywania danych.  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Ograniczanie dostępu do trwałego magazynu danych i zasobów lokalnych  
 Kontom, które są używane do uzyskiwania dostępu do magazynu trwałego, należy udzielić w bazie danych lub systemie plików praw wystarczających do obsługi wymagań usługi danych. Jeśli jest używane uwierzytelnianie anonimowe, jest to konto używane do uruchamiania aplikacji macierzystej. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych programu WCF działającej w](how-to-develop-a-wcf-data-service-running-on-iis.md)usługach IIS. Jeśli jest używana personifikacja, uwierzytelnionym użytkownikom należy udzielić dostępu do tych zasobów, zwykle jako części grupy systemu Windows.  
  
## <a name="other-security-considerations"></a>Inne uwagi dotyczące zabezpieczeń  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpieczanie danych w ładunku  
Usługa OData jest oparta na protokole HTTP. W komunikacie HTTP nagłówek może zawierać cenne poświadczenia użytkownika, zależnie od uwierzytelniania implementowanego przez usługę danych. Treść komunikatu może również zawierać cenne dane klienta, które muszą być chronione. W obu tych przypadkach zaleca się używanie protokołu SSL do ochrony tych informacji w sieci.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorowane nagłówki komunikatów i pliki cookie  
 Nagłówki żądania HTTP inne niż te, które deklarują typy zawartości i lokalizacje zasobów, są ignorowane i nigdy nie są ustawiane przez usługę danych.  
  
 Pliki cookie mogą służyć jako część schematu uwierzytelniania, na przykład z uwierzytelnianiem formularzy ASP.NET. Jednak wszystkie pliki cookie HTTP ustawione w żądaniu przychodzącym są ignorowane przez usługi DataService. Host usługi danych może przetworzyć plik cookie, ale środowisko uruchomieniowe Usługi danych programu WCF nigdy nie analizuje ani nie zwraca plików cookie. Biblioteka klienta Usługi danych programu WCF również nie przetwarza plików cookie wysyłanych w odpowiedzi.  
  
### <a name="custom-hosting-requirements"></a>Niestandardowe wymagania hostingu  
 Domyślnie Usługi danych programu WCF jest tworzona jako aplikacja ASP.NET hostowana w usługach IIS. Pozwala to usłudze danych na korzystanie z zachowań związanych z zabezpieczeniami zaimplementowanych na tej platformie. Można zdefiniować Usługi danych programu WCF, które są hostowane przez niestandardowego hosta. Aby uzyskać więcej informacji, zobacz [hosting usługi danych](hosting-the-data-service-wcf-data-services.md). Składniki i platforma hostująca usługę danych muszą zapewnić następujące zachowania związane z zabezpieczeniami, aby zapobiec atakom na usługę danych:  
  
- Ogranicz długość identyfikatora URI akceptowanego w żądaniu usługi danych dla wszystkich możliwych operacji.  
  
- Ogranicz rozmiar przychodzących i wychodzących komunikatów HTTP.  
  
- Ogranicz łączną liczbę zaległych żądań w danym momencie.  
  
- Ogranicz rozmiar nagłówków HTTP i ich wartości oraz Zapewnij Usługi danych programu WCF dostęp do danych nagłówka.  
  
- Wykrywaj i odpieraj znane ataki, takie jak TCP SYN i ataki przez powtórzenie komunikatu.  
  
### <a name="values-are-not-further-encoded"></a>Wartości nie są już kodowane  
 Wartości właściwości wysyłane do usługi danych nie są jeszcze kodowane przez środowisko uruchomieniowe Usługi danych programu WCF. Jeśli na przykład właściwość ciągu jednostki zawiera sformatowaną zawartość HTML, znaczniki nie są kodowane w formacie HTML przez usługę danych. Ponadto usługa danych nie koduje już wartości właściwości w odpowiedzi. Biblioteka klienta również nie przeprowadza dodatkowego kodowania.  
  
### <a name="considerations-for-client-applications"></a>Uwagi dotyczące aplikacji klienta  
 Następujące zagadnienia dotyczące zabezpieczeń dotyczą aplikacji korzystających z Usługi danych programu WCF klienta programu w celu uzyskiwania dostępu do usług OData:  
  
- Biblioteka klienta zakłada, że protokoły używane w celu uzyskania dostępu do usługi danych zapewniają odpowiedni poziom zabezpieczeń.  
  
- Biblioteka klienta używa wszystkich wartości domyślnych dla limitów czasu i opcji analizy podstawowych stosów transportu zapewnianych przez platformę.  
  
- Biblioteka klienta nie odczytuje żadnych ustawień z plików konfiguracji aplikacji.  
  
- Biblioteka klienta nie implementuje żadnych mechanizmów dostępu między domenami. W zamian opiera się na mechanizmach zapewnianych przez podstawowy stos HTTP.  
  
- Biblioteka klienta nie ma żadnych elementów interfejsu użytkownika i nigdy nie próbuje wyświetlać ani renderować danych, które odbiera lub wysyła.  
  
- Firma Microsoft zaleca, aby aplikacje klienta zawsze weryfikowały dane wprowadzone przez użytkownika, a także akceptowane dane pochodzące z niezaufanych usług.  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
