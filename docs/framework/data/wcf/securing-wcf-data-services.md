---
title: "Zabezpieczanie usługi danych WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c45da4ec1fa5d111be19437dde54035a89f9162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="securing-wcf-data-services"></a>Zabezpieczanie usługi danych WCF
W tym temacie opisano zagadnienia dotyczące zabezpieczeń, które są specyficzne dla tworzenie, wdrażanie i uruchamianie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] i aplikacje, które uzyskują dostęp do usług, które obsługują [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Należy również stosować zaleceń dotyczących tworzenia bezpiecznego [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.  
  
 Podczas planowania zabezpieczania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]— na podstawie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi, muszą spełnić zarówno uwierzytelniania, proces odnajdowania i weryfikowania tożsamości podmiotu zabezpieczeń, jak i autoryzacji, proces określania, czy uwierzytelnionego podmiot zabezpieczeń może uzyskać dostępu do żądanych zasobów. Należy również rozważyć, czy komunikat na być szyfrowany przy użyciu protokołu SSL.  
  
## <a name="authenticating-client-requests"></a>Uwierzytelnianie żądań klientów  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nie obsługuje żadnego rodzaju uwierzytelniania własnych, ale raczej opiera się na postanowienia uwierzytelniania hosta usługi danych. To oznacza, że usługa przyjęto założenie, że wszystkie żądania, który odbierze został już uwierzytelniony przez hosta i że host ma poprawnie określone zasady dla żądania odpowiednio za pośrednictwem interfejsów dostarczanych przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Te opcje uwierzytelniania i metody są wyszczególnione w [serii OData i uwierzytelniania](http://go.microsoft.com/fwlink/?LinkId=200381).  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>Opcje uwierzytelniania dla usługi danych programu WCF  
 W poniższej tabeli wymieniono niektóre z dostępnych mechanizmów uwierzytelniania, które pomagają w uwierzytelnieniu żądań kierowanych do usługi danych programu WCF.  
  
|Opcje uwierzytelniania|Opis|  
|----------------------------|-----------------|  
|Uwierzytelnianie anonimowe|Jeśli jest włączone uwierzytelnianie anonimowe HTTP, każdy podmiot zabezpieczeń jest w stanie połączyć się z usługą danych. W przypadku dostępu anonimowego nie są wymagane poświadczenia. Użyj tej opcji tylko wtedy, gdy każdemu użytkownikowi chcesz zezwolić na dostęp do usługi danych.|  
|Uwierzytelnianie podstawowe i szyfrowane|Do uwierzytelnienia są wymagane poświadczenia składające się z nazwy użytkownika i hasła. Obsługuje uwierzytelnianie klientów nieopartych na systemie Windows. **Uwaga dotycząca zabezpieczeń:** podstawowe poświadczenia uwierzytelniania (nazwa użytkownika i hasło) są wysyłane w zwykłym i może zostać przechwycony. W przypadku uwierzytelniania szyfrowanego wysyłana jest wartość skrótu oparta na podanych poświadczeniach, co sprawia, że jest ono bezpieczniejsze niż uwierzytelnianie podstawowe. Obie te metody są podatne na ataki man-in-middle. W przypadku korzystania z tych metod uwierzytelniania należy rozważyć szyfrowanie komunikacji między klientem a usługą danych przy użyciu protokołu Secure Sockets Layer (SSL). <br /><br /> Microsoft Internet Information Services (IIS), udostępnia implementację zarówno Basic i żądań uwierzytelniania szyfrowanego dla protokołu HTTP w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji. Ta implementacja dostawcy uwierzytelniania systemu Windows umożliwia aplikacji klienta programu .NET Framework podanie poświadczeń w nagłówku żądania HTTP skierowanego do usługi danych w celu bezproblemowego wynegocjowania uwierzytelnienia użytkownika systemu Windows. Aby uzyskać więcej informacji, zobacz [dokumentacja techniczna uwierzytelniania szyfrowanego](http://go.microsoft.com/fwlink/?LinkId=200408).<br /><br /> Jeśli chcesz, aby Twoje dane usługi użyj podstawowe uwierzytelnianie na podstawie niektóre niestandardowe uwierzytelnianie usługi i nie poświadczeń systemu Windows, musisz zaimplementować niestandardowego [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] moduł HTTP dla uwierzytelniania.<br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]jak używać schemat niestandardowe uwierzytelnianie podstawowe o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [niestandardowe uwierzytelnianie podstawowe](http://go.microsoft.com/fwlink/?LinkID=200388) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i serii uwierzytelniania.|  
|Uwierzytelnianie systemu Windows|Poświadczenia oparte na systemie Windows są wymieniane przy użyciu protokołu NTLM lub Kerberos. Ten mechanizm jest bezpieczniejszy niż uwierzytelnianie podstawowe lub szyfrowane, ale wymaga, aby klient był aplikacją opartą na systemie Windows. Usługi IIS oferują także stosowania uwierzytelniania systemu Windows dla żądań HTTP w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [omówienie uwierzytelniania formularzy ASP.NET](http://msdn.microsoft.com/library/099c1587-6934-476e-ac95-28f534bc9708).<br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]jak używać uwierzytelniania systemu Windows za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [uwierzytelniania systemu Windows](http://go.microsoft.com/fwlink/?LinkID=200384) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i serii uwierzytelniania.|  
|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Uwierzytelnianie formularzy|Uwierzytelnianie formularzy pozwala uwierzytelniać użytkowników przy użyciu własnego kodu, a następnie utrzymywać token uwierzytelniania w pliku cookie lub adresie URL strony. Uwierzytelniasz nazwy i hasła użytkowników używających utworzonego przez Ciebie formularza logowania. Nieuwierzytelnione żądania są przekierowywane na stronę logowania, gdzie użytkownik podaje poświadczenia i przesyła formularz. Jeśli aplikacja uwierzytelni żądanie, system wystawia bilet, który zawiera klucz umożliwiający ponowne ustalenie tożsamości dla kolejnych żądań. Aby uzyskać więcej informacji, zobacz [dostawcy uwierzytelniania formularzy](http://msdn.microsoft.com/library/77e21ba2-bad1-4967-a8ec-74942dea7e47). **Uwaga dotycząca zabezpieczeń:** domyślnie plik cookie zawierający biletu uwierzytelniania formularzy nie jest zabezpieczony korzystania z uwierzytelniania formularzy w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji sieci Web. Należy rozważyć wymaganie protokołu SSL w celu ochrony zarówno biletu uwierzytelniania, jak i początkowych poświadczeń logowania. <br /><br /> [!INCLUDE[crexample](../../../../includes/crexample-md.md)]jak używać formularzy uwierzytelniania za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [uwierzytelnianie formularzy](http://go.microsoft.com/fwlink/?LinkID=200389) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i serii uwierzytelniania.|  
|Uwierzytelnianie oparte na oświadczeniach|W przypadku uwierzytelniania opartego na oświadczeniach usługi danych zależy od zaufanego tożsamości "third-party" dostawcy usługi do uwierzytelnienia użytkownika. Dostawca tożsamości pozytywnie uwierzytelnia użytkownika, który żąda dostępu do zasobów usługi danych, i wystawia token udzielający dostępu do żądanych zasobów. Token ten jest następnie prezentowany usłudze danych, która udziela użytkownikowi dostępu na podstawie relacji zaufania z usługą tożsamości, która wystawiła token dostępu.<br /><br /> Zaletą używania dostawcy uwierzytelniania opartego na oświadczeniach jest to, że tej metody można używać do uwierzytelniania różnych typów klientów między domenami zaufania. Korzystając z takiego dostawcy innej firmy, usługa danych zdejmuje z siebie ciężar obsługi i uwierzytelniania użytkowników. OAuth 2.0 to protokół uwierzytelniania opartego na oświadczeniach, który jest obsługiwany jako usługa federacyjnej autoryzacji przez funkcję kontroli dostępu programu AppFabric systemu Microsoft Azure. Protokół ten obsługuje usługi oparte na protokole REST. [!INCLUDE[crexample](../../../../includes/crexample-md.md)]jak używać protokołu OAuth 2.0 z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], zobacz wpis na [OData i OAuth](http://go.microsoft.com/fwlink/?LinkId=200514) w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] i serii uwierzytelniania.|  
  
<a name="clientAuthentication"></a>   
### <a name="authentication-in-the-client-library"></a>Uwierzytelnianie w bibliotece klienta  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta nie dostarcza poświadczenia podczas tworzenia żądania [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi. Jeśli poświadczenia logowania są wymagane przez usługę danych do uwierzytelniania użytkownika, te poświadczenia mogą być dostarczane w <xref:System.Net.NetworkCredential> użytkowcy <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>, jak w poniższym przykładzie:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [porady: Określanie poświadczenia klienta żądania obsługi danych](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md).  
  
 Kiedy usługa danych wymaga poświadczenia logowania nie można określić za pomocą <xref:System.Net.NetworkCredential> obiektów, takich jak token opartego na oświadczeniach lub plik cookie, należy ręcznie ustawić nagłówków w żądaniu HTTP zazwyczaj `Authorization` i `Cookie` nagłówków. Aby uzyskać więcej informacji dotyczących tego rodzaju scenariuszu uwierzytelniania, zobacz wpis [OData i uwierzytelniania: przechwytuje po stronie klienta](http://go.microsoft.com/fwlink/?LinkID=200385). Na przykład sposobu ustawiania nagłówków HTTP w komunikacie żądania zobacz [porady: Ustawianie nagłówków w żądaniu klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md).  
  
## <a name="impersonation"></a>Personifikacja  
 Na ogół usługa danych uzyskuje dostęp do wymaganych zasobów, takich jak pliki na serwerze lub baza danych, przy użyciu poświadczeń procesu roboczego hostującego usługę danych. Personifikacji, używając [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji można wykonywać przy użyciu tożsamości systemu Windows (konto użytkownika) użytkownika zgłaszającego żądanie. Personifikacja jest powszechnie stosowana w aplikacjach, które przy uwierzytelnieniu użytkownika opierają się na programie IIS, i poświadczenia tego podmiotu zabezpieczeń są używane do uzyskiwania dostępu do wymaganych zasobów. Aby uzyskać więcej informacji, zobacz [personifikacji aplikacji ASP.NET](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d).  
  
## <a name="configuring-data-service-authorization"></a>Konfigurowanie autoryzacji usługi danych  
 Autoryzacja to udzielenie dostępu do zasobów aplikacji podmiotowi zabezpieczeń lub procesowi, który został zidentyfikowany na podstawie przeprowadzonego wcześniej pomyślnego uwierzytelnienia. Ogólną praktyką jest udzielanie użytkownikom usługi danych tylko uprawnień wystarczających do wykonywania operacji wymaganych przez aplikacje klienta.  
  
### <a name="restrict-access-to-data-service-resources"></a>Ograniczanie dostępu do zasobów usługi danych  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umożliwia przyznanie wspólnej odczytu i zapisu względem zasobów usługi danych (Ustaw jednostki i usługi operations) dla każdego użytkownika, który jest w stanie uzyskać dostęp do danych usługi. Reguły, które definiują prawa do odczytu i zapisu, można określić osobno dla każdego zestawu jednostek uwidacznianego przez usługę danych, a także dla każdej operacji usługi. Zaleca się zawężenie zarówno praw do odczytu, jak i do zapisu tylko do zasobów, które są wymagane przez aplikację klienta. Aby uzyskać więcej informacji, zobacz [minimalne wymagania dostępu do zasobów](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md#accessRequirements).  
  
### <a name="implement-role-based-interceptors"></a>Wdrażanie interceptorów opartych na rolach  
 Interceptory umożliwiają przechwytywanie żądań zasobów usługi danych, zanim zostaną one przetworzone przez usługę danych. Aby uzyskać więcej informacji, zobacz [Interceptory](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md). Interceptory pozwalają na podejmowanie decyzji dotyczących autoryzacji na podstawie uwierzytelnionego użytkownika, który wysłał żądanie. [!INCLUDE[crexample](../../../../includes/crexample-md.md)]jak ograniczyć dostęp do zasobów usługi danych oparte na tożsamość uwierzytelnionego użytkownika, zobacz [porady: Przechwytywanie danych komunikatów usługi](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>Ograniczanie dostępu do trwałego magazynu danych i zasobów lokalnych  
 Kontom, które są używane do uzyskiwania dostępu do magazynu trwałego, należy udzielić w bazie danych lub systemie plików praw wystarczających do obsługi wymagań usługi danych. Jeśli jest używane uwierzytelnianie anonimowe, jest to konto używane do uruchamiania aplikacji macierzystej. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych WCF działającą na serwerze IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md). Jeśli jest używana personifikacja, uwierzytelnionym użytkownikom należy udzielić dostępu do tych zasobów, zwykle jako części grupy systemu Windows.  
  
## <a name="other-security-considerations"></a>Inne uwagi dotyczące zabezpieczeń  
  
### <a name="secure-the-data-in-the-payload"></a>Zabezpieczanie danych w ładunku  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]jest oparty na protokole HTTP. W komunikacie HTTP nagłówek może zawierać cenne poświadczenia użytkownika, zależnie od uwierzytelniania implementowanego przez usługę danych. Treść komunikatu może również zawierać cenne dane klienta, które muszą być chronione. W obu tych przypadkach zaleca się używanie protokołu SSL do ochrony tych informacji w sieci.  
  
### <a name="ignored-message-headers-and-cookies"></a>Ignorowane nagłówki komunikatów i pliki cookie  
 Nagłówki żądania HTTP inne niż te, które deklarują typy zawartości i lokalizacje zasobów, są ignorowane i nigdy nie są ustawiane przez usługę danych.  
  
 Pliki cookie może służyć jako część schematu uwierzytelniania, takich jak z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uwierzytelniania formularzy. Jednak żadnych plików cookie HTTP, ustaw na żądanie przychodzące są ignorowane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Host usługi danych może przetworzyć pliku cookie, ale [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] środowiska uruchomieniowego nigdy nie analizuje lub zwraca plików cookie. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Również Biblioteka klienta nie przetwarza plików cookie wysłanych w odpowiedzi.  
  
### <a name="custom-hosting-requirements"></a>Niestandardowe wymagania hostingu  
 Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zostanie utworzona jako [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji hostowanej w usługach IIS. Pozwala to usłudze danych na korzystanie z zachowań związanych z zabezpieczeniami zaimplementowanych na tej platformie. Można zdefiniować [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] które są obsługiwane przez hosta niestandardowego. Aby uzyskać więcej informacji, zobacz [obsługujący usługę danych](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md). Składniki i platforma hostująca usługę danych muszą zapewnić następujące zachowania związane z zabezpieczeniami, aby zapobiec atakom na usługę danych:  
  
-   Ogranicz długość identyfikatora URI akceptowanego w żądaniu usługi danych dla wszystkich możliwych operacji.  
  
-   Ogranicz rozmiar przychodzących i wychodzących komunikatów HTTP.  
  
-   Ogranicz łączną liczbę zaległych żądań w danym momencie.  
  
-   Ogranicz rozmiar nagłówków HTTP i ich wartości i podaj [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dostęp do danych nagłówka.  
  
-   Wykrywaj i odpieraj znane ataki, takie jak TCP SYN i ataki przez powtórzenie komunikatu.  
  
### <a name="values-are-not-further-encoded"></a>Wartości nie są już kodowane  
 Wartości właściwości wysyłane do usługi danych nie są dodatkowo zakodowane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] środowiska wykonawczego. Jeśli na przykład właściwość ciągu jednostki zawiera sformatowaną zawartość HTML, znaczniki nie są kodowane w formacie HTML przez usługę danych. Ponadto usługa danych nie koduje już wartości właściwości w odpowiedzi. Biblioteka klienta również nie przeprowadza dodatkowego kodowania.  
  
### <a name="considerations-for-client-applications"></a>Uwagi dotyczące aplikacji klienta  
 Zastosuj następujące zagadnienia dotyczące zabezpieczeń dla aplikacji, które używają [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientowi dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usług:  
  
-   Biblioteka klienta zakłada, że protokoły używane w celu uzyskania dostępu do usługi danych zapewniają odpowiedni poziom zabezpieczeń.  
  
-   Biblioteka klienta używa wszystkich wartości domyślnych dla limitów czasu i opcji analizy podstawowych stosów transportu zapewnianych przez platformę.  
  
-   Biblioteka klienta nie odczytuje żadnych ustawień z plików konfiguracji aplikacji.  
  
-   Biblioteka klienta nie implementuje żadnych mechanizmów dostępu między domenami. W zamian opiera się na mechanizmach zapewnianych przez podstawowy stos HTTP.  
  
-   Biblioteka klienta nie ma żadnych elementów interfejsu użytkownika i nigdy nie próbuje wyświetlać ani renderować danych, które odbiera lub wysyła.  
  
-   Firma Microsoft zaleca, aby aplikacje klienta zawsze weryfikowały dane wprowadzone przez użytkownika, a także akceptowane dane pochodzące z niezaufanych usług.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
