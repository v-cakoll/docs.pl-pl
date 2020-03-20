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
ms.openlocfilehash: e09007e786772e838a9aaa76eb8ef7a3fe2b7cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174657"
---
# <a name="securing-wcf-data-services"></a>Zabezpieczanie usług danych WCF
W tym temacie opisano zagadnienia dotyczące zabezpieczeń, które są specyficzne dla tworzenia, wdrażania i uruchamiania usług danych WCF i aplikacji, które uzyskują dostęp do usług obsługujących protokół OData (Open Data Protocol). Należy również postępować zgodnie z zaleceniami dotyczącymi tworzenia bezpiecznych aplikacji .NET Framework.  
  
Planując sposób zabezpieczania usługi OData opartej na usługach danych WCF, należy zająć się zarówno uwierzytelnianiem, procesem odnajdowania i weryfikacji tożsamości podmiotu zabezpieczeń, jak i autoryzacją, procesem określania, czy uwierzytelniony podmiot zabezpieczeń jest dostęp do żądanych zasobów. Należy również rozważyć, czy komunikat na być szyfrowany przy użyciu protokołu SSL.  
  
## <a name="authenticating-client-requests"></a>Uwierzytelnianie żądań klientów  
Usługi WCF Data Services nie implementuje wszelkiego rodzaju uwierzytelniania własnych, ale raczej opiera się na przepisach uwierzytelniania hosta usługi danych. Oznacza to, że usługa zakłada, że każde żądanie, które otrzymuje, zostało już uwierzytelnione przez hosta sieciowego i że host prawidłowo zidentyfikował zasadę żądania za pośrednictwem interfejsów dostarczonych przez usługi WCF Data Services. Te opcje i podejścia uwierzytelniania są szczegółowo opisane w [wieloczęściowej serii OData i Authentication](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Opcje uwierzytelniania dla usługi danych programu WCF  
 W poniższej tabeli wymieniono niektóre z dostępnych mechanizmów uwierzytelniania, które pomagają w uwierzytelnieniu żądań kierowanych do usługi danych programu WCF.  
  
|Opcje uwierzytelniania|Opis|  
|----------------------------|-----------------|  
|Uwierzytelnianie anonimowe|Jeśli jest włączone uwierzytelnianie anonimowe HTTP, każdy podmiot zabezpieczeń jest w stanie połączyć się z usługą danych. W przypadku dostępu anonimowego nie są wymagane poświadczenia. Użyj tej opcji tylko wtedy, gdy każdemu użytkownikowi chcesz zezwolić na dostęp do usługi danych.|  
|Uwierzytelnianie podstawowe i szyfrowane|Do uwierzytelnienia są wymagane poświadczenia składające się z nazwy użytkownika i hasła. Obsługuje uwierzytelnianie klientów nieopartych na systemie Windows. **Uwaga dotycząca zabezpieczeń:**  Podstawowe poświadczenia uwierzytelniania (nazwa użytkownika i hasło) są wysyłane w sposób przejrzysty i mogą zostać przechwycone. W przypadku uwierzytelniania szyfrowanego wysyłana jest wartość skrótu oparta na podanych poświadczeniach, co sprawia, że jest ono bezpieczniejsze niż uwierzytelnianie podstawowe. Obie te metody są podatne na ataki man-in-middle. W przypadku korzystania z tych metod uwierzytelniania należy rozważyć szyfrowanie komunikacji między klientem a usługą danych przy użyciu protokołu Secure Sockets Layer (SSL). <br /><br /> Internetowe usługi informacyjne firmy Microsoft (IIS) zapewniają implementację uwierzytelniania podstawowego i szyfrowego dla żądań HTTP w aplikacji ASP.NET. Ta implementacja dostawcy uwierzytelniania systemu Windows umożliwia aplikacji klienta programu .NET Framework podanie poświadczeń w nagłówku żądania HTTP skierowanego do usługi danych w celu bezproblemowego wynegocjowania uwierzytelnienia użytkownika systemu Windows. Aby uzyskać więcej informacji, zobacz [Technical Reference uwierzytelniania szyfrowanego](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782794(v=ws.10)).<br /><br /> Jeśli chcesz, aby usługa danych używała uwierzytelniania podstawowego na podstawie niektórych usług uwierzytelniania niestandardowego, a nie poświadczeń systemu Windows, należy zaimplementować niestandardowy moduł ADP.NET HTTP do uwierzytelniania.<br /><br /> Na przykład, jak używać niestandardowego schematu uwierzytelniania podstawowego z usługami WCF Data Services, zobacz wpis w blogu [OData i uwierzytelnianie — część 6 – Uwierzytelnianie podstawowe niestandardowe](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/).|  
|Uwierzytelnianie systemu Windows|Poświadczenia oparte na systemie Windows są wymieniane przy użyciu protokołu NTLM lub Kerberos. Ten mechanizm jest bezpieczniejszy niż uwierzytelnianie podstawowe lub szyfrowane, ale wymaga, aby klient był aplikacją opartą na systemie Windows. Usługi IIS zapewniają również implementację uwierzytelniania systemu Windows dla żądań HTTP w aplikacji ASP.NET. Aby uzyskać więcej informacji, zobacz [ASP.NET Omówienie uwierzytelniania formularzy](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100)).<br /><br /> Na przykład sposobu korzystania z uwierzytelniania systemu Windows w usługach WCF Data Services zobacz wpis w blogu [OData i uwierzytelnianie – Część 2 – Uwierzytelnianie systemu Windows](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/).|  
|uwierzytelnianie formularzy ASP.NET|Uwierzytelnianie formularzy pozwala uwierzytelniać użytkowników przy użyciu własnego kodu, a następnie utrzymywać token uwierzytelniania w pliku cookie lub adresie URL strony. Uwierzytelniasz nazwy i hasła użytkowników używających utworzonego przez Ciebie formularza logowania. Nieuwierzytelnione żądania są przekierowywane na stronę logowania, gdzie użytkownik podaje poświadczenia i przesyła formularz. Jeśli aplikacja uwierzytelni żądanie, system wystawia bilet, który zawiera klucz umożliwiający ponowne ustalenie tożsamości dla kolejnych żądań. Aby uzyskać więcej informacji, zobacz [Dostawca uwierzytelniania formularzy](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100)). **Uwaga dotycząca zabezpieczeń:**  Domyślnie plik cookie zawierający bilet uwierzytelniania formularzy nie jest zabezpieczony podczas korzystania z uwierzytelniania formularzy w ASP.NET aplikacji sieci Web. Należy rozważyć wymaganie protokołu SSL w celu ochrony zarówno biletu uwierzytelniania, jak i początkowych poświadczeń logowania. <br /><br /> Na przykład sposobu korzystania z uwierzytelniania formularzy w usługach danych WCF można znaleźć w wpisie w blogu [OData i Uwierzytelnianie – część 7 – Uwierzytelnianie formularzy](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/).|  
|Uwierzytelnianie oparte na oświadczeniach|W uwierzytelnianiu opartym na oświadczeniach usługa danych opiera się na zaufanej usłudze dostawcy tożsamości "innej firmy" w celu uwierzytelnienia użytkownika. Dostawca tożsamości pozytywnie uwierzytelnia użytkownika, który żąda dostępu do zasobów usługi danych, i wystawia token udzielający dostępu do żądanych zasobów. Token ten jest następnie prezentowany usłudze danych, która udziela użytkownikowi dostępu na podstawie relacji zaufania z usługą tożsamości, która wystawiła token dostępu.<br /><br /> Zaletą używania dostawcy uwierzytelniania opartego na oświadczeniach jest to, że tej metody można używać do uwierzytelniania różnych typów klientów między domenami zaufania. Korzystając z takiego dostawcy innej firmy, usługa danych zdejmuje z siebie ciężar obsługi i uwierzytelniania użytkowników. OAuth 2.0 to protokół uwierzytelniania opartego na oświadczeniach, który jest obsługiwany jako usługa federacyjnej autoryzacji przez funkcję kontroli dostępu programu AppFabric systemu Microsoft Azure. Protokół ten obsługuje usługi oparte na protokole REST. Na przykład sposobu używania OAuth 2.0 z WCF Data Services, zobacz wpis w blogu [OData i uwierzytelnianie - Część 8 – OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/).|  
  
<a name="clientAuthentication"></a>
### <a name="authentication-in-the-client-library"></a>Uwierzytelnianie w bibliotece klienta  
 Domyślnie biblioteka klienta usług danych WCF nie dostarcza poświadczeń podczas żądania do usługi OData. Gdy dane logowania są wymagane przez usługę danych do uwierzytelniania użytkownika, te <xref:System.Net.NetworkCredential> poświadczenia mogą <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> być <xref:System.Data.Services.Client.DataServiceContext>dostarczane w właściwości , jak w poniższym przykładzie:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Jak: Określanie poświadczeń klienta dla żądania usługi danych](specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Gdy usługa danych wymaga poświadczeń logowania, których nie można określić za pomocą <xref:System.Net.NetworkCredential> obiektu, takiego jak token oparty `Authorization` na `Cookie` oświadczeniach lub plik cookie, należy ręcznie ustawić nagłówki w żądaniu HTTP, zwykle nagłówki i nagłówki. Aby uzyskać więcej informacji na temat tego rodzaju scenariusza uwierzytelniania, zobacz wpis w blogu [OData i uwierzytelnianie - Część 3 – ClientSide Hooks](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/). Na przykład ustawiania nagłówków HTTP w komunikacie żądania zobacz [Jak: Ustawianie nagłówków w żądaniu klienta](how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Personifikacja  
 Na ogół usługa danych uzyskuje dostęp do wymaganych zasobów, takich jak pliki na serwerze lub baza danych, przy użyciu poświadczeń procesu roboczego hostującego usługę danych. Podczas korzystania z personifikacji, ASP.NET aplikacje można wykonać za pomocą tożsamości systemu Windows (konto użytkownika) użytkownika składającego żądanie. Personifikacja jest powszechnie stosowana w aplikacjach, które przy uwierzytelnieniu użytkownika opierają się na programie IIS, i poświadczenia tego podmiotu zabezpieczeń są używane do uzyskiwania dostępu do wymaganych zasobów. Aby uzyskać więcej informacji, zobacz [ASP.NET personifikacji](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100)).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurowanie autoryzacji usługi danych  
 Autoryzacja to udzielenie dostępu do zasobów aplikacji podmiotowi zabezpieczeń lub procesowi, który został zidentyfikowany na podstawie przeprowadzonego wcześniej pomyślnego uwierzytelnienia. Ogólną praktyką jest udzielanie użytkownikom usługi danych tylko uprawnień wystarczających do wykonywania operacji wymaganych przez aplikacje klienta.  
  
### <a name="restrict-access-to-data-service-resources"></a>Ograniczanie dostępu do zasobów usługi danych  
 Domyślnie usługi WCF Data Services umożliwia udzielanie wspólnego dostępu do odczytu i zapisu względem zasobów usługi danych (operacji zestawu jednostek i usług) każdemu użytkownikowi, który ma dostęp do usługi danych. Reguły, które definiują prawa do odczytu i zapisu, można określić osobno dla każdego zestawu jednostek uwidacznianego przez usługę danych, a także dla każdej operacji usługi. Zaleca się zawężenie zarówno praw do odczytu, jak i do zapisu tylko do zasobów, które są wymagane przez aplikację klienta. Aby uzyskać więcej informacji, zobacz [Minimalne wymagania dotyczące dostępu do zasobów](configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Wdrażanie interceptorów opartych na rolach  
 Interceptory umożliwiają przechwytywanie żądań zasobów usługi danych, zanim zostaną one przetworzone przez usługę danych. Aby uzyskać więcej informacji, zobacz [Interceptors](interceptors-wcf-data-services.md). Interceptory pozwalają na podejmowanie decyzji dotyczących autoryzacji na podstawie uwierzytelnionego użytkownika, który wysłał żądanie. Na przykład jak ograniczyć dostęp do zasobów usługi danych na podstawie uwierzytelnionej tożsamości użytkownika, zobacz [Jak: Przechwytywanie komunikatów usługi danych](how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Ograniczanie dostępu do trwałego magazynu danych i zasobów lokalnych  
 Kontom, które są używane do uzyskiwania dostępu do magazynu trwałego, należy udzielić w bazie danych lub systemie plików praw wystarczających do obsługi wymagań usługi danych. Jeśli jest używane uwierzytelnianie anonimowe, jest to konto używane do uruchamiania aplikacji macierzystej. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie usługi danych WCF uruchomionej na usługach IIS](how-to-develop-a-wcf-data-service-running-on-iis.md). Jeśli jest używana personifikacja, uwierzytelnionym użytkownikom należy udzielić dostępu do tych zasobów, zwykle jako części grupy systemu Windows.  
  
## <a name="other-security-considerations"></a>Inne uwagi dotyczące zabezpieczeń  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpieczanie danych w ładunku  
OData jest oparty na protokole HTTP. W komunikacie HTTP nagłówek może zawierać cenne poświadczenia użytkownika, zależnie od uwierzytelniania implementowanego przez usługę danych. Treść komunikatu może również zawierać cenne dane klienta, które muszą być chronione. W obu tych przypadkach zaleca się używanie protokołu SSL do ochrony tych informacji w sieci.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorowane nagłówki komunikatów i pliki cookie  
 Nagłówki żądania HTTP inne niż te, które deklarują typy zawartości i lokalizacje zasobów, są ignorowane i nigdy nie są ustawiane przez usługę danych.  
  
 Pliki cookie mogą być używane jako część schematu uwierzytelniania, na przykład z uwierzytelnianiem ASP.NET formularzy. Jednak wszystkie pliki cookie HTTP ustawione na żądanie przychodzące są ignorowane przez usługi danych WCF. Host usługi danych może przetwarzać plik cookie, ale środowisko wykonawcze WCF Data Services nigdy nie analizuje ani nie zwraca plików cookie. Biblioteka klienta usług danych WCF nie przetwarza również plików cookie wysyłanych w odpowiedzi.  
  
### <a name="custom-hosting-requirements"></a>Niestandardowe wymagania hostingu  
 Domyślnie usługi WCF Data Services są tworzone jako aplikacja ASP.NET hostowana w usługach IIS. Pozwala to usłudze danych na korzystanie z zachowań związanych z zabezpieczeniami zaimplementowanych na tej platformie. Można zdefiniować usługi danych WCF, które są hostowane przez hosta niestandardowego. Aby uzyskać więcej informacji, zobacz [Hostowanie usługi danych](hosting-the-data-service-wcf-data-services.md). Składniki i platforma hostująca usługę danych muszą zapewnić następujące zachowania związane z zabezpieczeniami, aby zapobiec atakom na usługę danych:  
  
- Ogranicz długość identyfikatora URI akceptowanego w żądaniu usługi danych dla wszystkich możliwych operacji.  
  
- Ogranicz rozmiar przychodzących i wychodzących komunikatów HTTP.  
  
- Ogranicz łączną liczbę zaległych żądań w danym momencie.  
  
- Ogranicz rozmiar nagłówków HTTP i ich wartości oraz zapewnij usługom danych WCF dostęp do danych nagłówka.  
  
- Wykrywaj i odpieraj znane ataki, takie jak TCP SYN i ataki przez powtórzenie komunikatu.  
  
### <a name="values-are-not-further-encoded"></a>Wartości nie są już kodowane  
 Wartości właściwości wysyłane do usługi danych nie są dalej kodowane przez środowisko uruchomieniowe WCF Data Services. Jeśli na przykład właściwość ciągu jednostki zawiera sformatowaną zawartość HTML, znaczniki nie są kodowane w formacie HTML przez usługę danych. Ponadto usługa danych nie koduje już wartości właściwości w odpowiedzi. Biblioteka klienta również nie przeprowadza dodatkowego kodowania.  
  
### <a name="considerations-for-client-applications"></a>Uwagi dotyczące aplikacji klienta  
 Następujące zagadnienia dotyczące zabezpieczeń mają zastosowanie do aplikacji korzystających z klienta usług danych WCF w celu uzyskania dostępu do usług OData:  
  
- Biblioteka klienta zakłada, że protokoły używane w celu uzyskania dostępu do usługi danych zapewniają odpowiedni poziom zabezpieczeń.  
  
- Biblioteka klienta używa wszystkich wartości domyślnych dla limitów czasu i opcji analizy podstawowych stosów transportu zapewnianych przez platformę.  
  
- Biblioteka klienta nie odczytuje żadnych ustawień z plików konfiguracji aplikacji.  
  
- Biblioteka klienta nie implementuje żadnych mechanizmów dostępu między domenami. W zamian opiera się na mechanizmach zapewnianych przez podstawowy stos HTTP.  
  
- Biblioteka klienta nie ma żadnych elementów interfejsu użytkownika i nigdy nie próbuje wyświetlać ani renderować danych, które odbiera lub wysyła.  
  
- Firma Microsoft zaleca, aby aplikacje klienta zawsze weryfikowały dane wprowadzone przez użytkownika, a także akceptowane dane pochodzące z niezaufanych usług.  
  
## <a name="see-also"></a>Zobacz też

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
