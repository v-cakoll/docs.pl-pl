---
title: Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: 717e38b15767b744816c0a57c97827a1a35c95b3
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086677"
---
# <a name="windows-communication-foundation-privacy-information"></a>Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)
Firma Microsoft jest zaangażowana w ochronę prywatności użytkowników końcowych. Podczas tworzenia aplikacji przy użyciu funkcji Windows Communication Foundation (WCF), wersja 3.0, aplikacja może mieć wpływ na prywatność użytkowników końcowych. Na przykład aplikacja jawnie może zbierać informacje kontaktowe użytkownika, lub może zażądać lub wysyłanie informacji przez Internet do witryny sieci Web. Technologii firmy Microsoft w przypadku osadzenia w aplikacji, technologia ta może mieć własną zachowanie, które mogą mieć wpływ na prywatność. Usługi WCF nie wysyła żadnych informacji do firmy Microsoft z aplikacji, chyba że użytkownik lub użytkownik końcowy chce wysłać ją do nas.  
  
## <a name="wcf-in-brief"></a>Usługi WCF w skrócie  
 Usługi WCF jest platforma obsługi komunikatów rozproszonych przy użyciu programu Microsoft .NET Framework, która umożliwia deweloperom tworzenie aplikacji rozproszonych. Komunikaty przekazywane między dwiema aplikacjami zawierają informacje, nagłówek i treść.  
  
 Może zawierać nagłówki, routing komunikatów, informacje o zabezpieczeniach, transakcji i dłużej w zależności od usług używanych przez aplikację. Komunikaty są zazwyczaj domyślne szyfrowanie przekazywanego materiału. Jedynym wyjątek polega na użyciu `BasicHttpBinding`, który został zaprojektowany do użytku z niezabezpieczonych, starszej wersji usługi sieci Web. Projektant aplikacji odpowiedzialność za ostatecznego projektu. Komunikaty w treści protokołu SOAP zawierają dane specyficzne dla aplikacji; Jednak te dane, takie jak zdefiniowane przez aplikację informacje osobiste mogą być chronione za pomocą funkcji szyfrowania lub poufności WCF. W poniższych sekcjach opisano funkcje, które mogłoby to wpłynąć na zachowania.  
  
## <a name="messaging"></a>Obsługa wiadomości  
 Każdy komunikat WCF ma nagłówek adres, który określa miejsce docelowe wiadomości i gdzie odpowiedzi.  
  
 Składnik adresu adresu punktu końcowego jest jednolite zasobów identyfikator (URI), który identyfikuje punkt końcowy. Adres może być adresu sieciowego lub adres logiczny. Adres może zawierać nazwy komputera (nazwa hosta, w pełni kwalifikowana nazwa domeny) i adres IP. Adres punktu końcowego może również zawierać unikatowy identyfikator globalny (GUID) lub zbiór identyfikatorów GUID do adresowania tymczasowe umożliwia brakowi rozróżnienia każdego z adresów. Każdy komunikat zawiera identyfikator komunikatu, który jest identyfikatorem GUID. Ta funkcja postępuje zgodnie ze standardowym odwołanie WS-Addressing.  
  
 Warstwa obsługi komunikatów usługi WCF nie zapisuje żadnych danych osobowych do komputera lokalnego. Jednak go może propagację informacje osobiste, na poziomie sieci jeśli deweloper usługi został utworzony, to usługa, która udostępnia takie informacje (np. przez przy użyciu nazwy osoby w nazwy punktu końcowego lub w tym informacje osobiste w sieci Web punktu końcowego Usługi języka opisu, ale nie wymaga klientom dostęp do pliku WSDL przy użyciu protokołu https). Ponadto jeśli deweloper działa [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie względem punktu końcowego, który udostępnia informacje osobiste, dane wyjściowe narzędzia firmy mogą zawierać te informacje, i jest zapisywany plik wyjściowy lokalny dysk twardy.  
  
## <a name="hosting"></a>Hosting  
 Hostingu funkcji w programie WCF umożliwia aplikacjom, które można uruchomić na żądanie lub włączanie udostępniania portów między wieloma aplikacjami. Aplikacja usługi WCF, mogą być hostowane w Internet Information Services (IIS), podobnie jak [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
 Hostingu nie ujawnia żadnych konkretnych informacji o sieci i nie przechowuje danych na maszynie.  
  
## <a name="message-security"></a>Zabezpieczenia komunikatów  
 Zabezpieczenia programu WCF zapewnia funkcje zabezpieczeń dla aplikacji do obsługi wiadomości. Dostępne funkcje zabezpieczeń obejmują uwierzytelnianie i autoryzację.  
  
 Uwierzytelnianie jest wykonywane przez przekazywanie poświadczeń między klientami i usługami. Uwierzytelnianie można za pomocą zabezpieczeń na poziomie transportu lub za pośrednictwem protokołu SOAP wiadomości zabezpieczenia na poziomie, w następujący sposób:  
  
-   W ramach zabezpieczeń komunikatów protokołu SOAP uwierzytelnianie będzie przeprowadzane przy użyciu poświadczeń, takie jak nazwy użytkownika i hasła, certyfikaty X.509, bilety protokołu Kerberos i tokeny SAML, które mogą zawierać informacje osobiste, w zależności od wystawcy.  
  
-   Za pomocą zabezpieczeń transportu, uwierzytelnianie odbywa się za pośrednictwem tradycyjnych transportu mechanizmów uwierzytelniania, takich jak schematy uwierzytelniania HTTP (Basic, Digest, Negotiate, zintegrowanej autoryzacji Windows, NTLM, None i anonimowych) i uwierzytelniania formularzy.  
  
 Uwierzytelnianie może spowodować bezpiecznej sesji między komunikujące się punkty końcowe. Sesja jest identyfikowana przez identyfikator GUID, który trwa okres istnienia sesji zabezpieczeń. W poniższej tabeli przedstawiono, jakie są przechowywane i gdzie.  
  
|Dane|Magazyn|  
|----------|-------------|  
|Prezentacja poświadczenia, takie jak nazwa użytkownika, certyfikatów X.509, tokenów protokołu Kerberos i odwołania do poświadczeń.|Standardowa Windows poświadczeń mechanizmami zarządzania, takich jak Sklep Windows certyfikatu.|  
|Członkostwo w informacje o użytkowniku, takie jak nazwy użytkowników i hasła.|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] dostawcy członkostwa.|  
|Informacje identyfikacyjne dotyczące usługi używany do uwierzytelniania usługi dla klientów.|Adres punktu końcowego usługi.|  
|Informacje o wywołującym.|Dzienniki inspekcji.|  
  
## <a name="auditing"></a>Inspekcja  
 Inspekcja rejestruje sukcesów i niepowodzeń zdarzenia uwierzytelniania i autoryzacji. Rekordy inspekcji zawierają następujące dane: identyfikator URI, identyfikator URI akcji oraz identyfikator obiektu wywołującego.  
  
 Inspekcja również są rejestrowane po administrator Modyfikuje konfigurację rejestrowania komunikatów (Włączanie on lub off), ponieważ rejestrowanie komunikatów mogą rejestrować dane specyficzne dla aplikacji w nagłówki i treść. Aby uzyskać [!INCLUDE[wxp](../../../includes/wxp-md.md)], rekord jest rejestrowane w dzienniku zdarzeń aplikacji. Aby uzyskać [!INCLUDE[wv](../../../includes/wv-md.md)] i [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], rekord jest rejestrowane w dzienniku zdarzeń zabezpieczeń.  
  
## <a name="transactions"></a>Transakcje  
 Funkcja transakcji udostępnia transakcyjne usługi aplikacji WCF.  
  
 Nagłówki transakcji używanych w propagacji transakcji może zawierać identyfikatory transakcji lub identyfikatorów rejestracji, które są identyfikatory GUID.  
  
 Funkcja transakcji używa transakcji Koordynator MSDTC (Microsoft Distributed) Menedżera transakcji (składnik Windows) do zarządzania stanem transakcji. Domyślnie komunikacja między menedżerami transakcje są szyfrowane. Menedżerowie transakcji mogą rejestrować się odwołania do endpoint, identyfikatory transakcji i identyfikatorów rejestracji, w ramach stanu trwałego. Okres istnienia tego stanu jest określana przez okres istnienia pliku dziennika Menedżera transakcji. Usługa MSDTC jest właścicielem i przechowuje ten dziennik.  
  
 Funkcja transakcji implementuje standardów WS koordynacji i WS-Atomic Transaction.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje w programie WCF zapewniają przesyłanie wiadomości, gdy transportu lub pośredniczący błędy występują. Zapewniają one dokładnie — raz przesyłanie komunikatów, nawet wtedy, gdy transportu źródłowego odłącza (np. połączenia protokołu TCP w sieci bezprzewodowej) lub utraci komunikat (serwer proxy HTTP porzucenie wiadomości wychodzące lub przychodzące). Niezawodne sesje także odzyskać komunikat zmiany kolejności (co może się zdarzyć w przypadku routing wielościeżkowego), jednoczesnym zapewnieniu właściwej kolejności, w jakiej zostały wysłane wiadomości.  
  
 Niezawodne sesje są implementowane przy użyciu protokołu WS-ReliableMessaging (WS-RM). Dodają WS-RM nagłówki, które zawierają informacje o sesji, który jest używany do identyfikowania wszystkie komunikaty skojarzone z określonym niezawodnej sesji. Każda sesja WS-RM ma identyfikator, który jest identyfikatorem GUID.  
  
 Żadne informacje osobiste nie są przechowywane na komputerze użytkownika końcowego.  
  
## <a name="queued-channels"></a>Kanały umieszczonych w kolejce  
 Kolejki przechowywanie komunikatów w aplikacji wysyłającej w imieniu aplikacji odbierającej i później przekazuje te komunikaty odbierający aplikacji. Łatwiej jest zapewnić przesyłanie wiadomości z aplikacji wysyłającej aplikacje odbierające, gdy na przykład aplikacja odbierająca jest przejściowy. Usługi WCF zapewnia obsługę usługi kolejkowania wiadomości przy użyciu Microsoft usługi kolejkowania komunikatów (MSMQ) jako transportu.  
  
 Funkcja kanały umieszczonych w kolejce nie dodaje nagłówki do wiadomości. Zamiast tego tworzy komunikatów usługi kolejkowania komunikatów za pomocą odpowiedni zestaw właściwości komunikatów usługi kolejkowania komunikatów i wywołuje metody usługi kolejkowania komunikatów, aby przełączyć komunikat do kolejki usługi kolejkowania komunikatów. Usługa kolejkowania komunikatów jest opcjonalnym składnikiem, który jest dostarczany z programem Windows.  
  
 Żadne informacje nie są przechowywane na komputerze użytkownika końcowego przez funkcję kanały umieszczonych w kolejce, ponieważ używa ona usługi kolejkowania komunikatów jako infrastruktura do kolejkowania.  
  
## <a name="com-integration"></a>Integracja modelu COM+  
 Ta funkcja jest zawijany istniejących funkcji COM i COM +, do tworzenia usług, które są zgodne z usługi WCF. Ta funkcja nie używa określone nagłówki i nie zachowuje danych na komputerze użytkownika końcowego.  
  
## <a name="com-service-moniker"></a>COM monikera  
 Zapewnia to niezarządzanych otoki standardowe klienta programu WCF. Ta funkcja nie ma określonych nagłówków na potrzeby przesyłu ani jest zachować dane na maszynie.  
  
## <a name="peer-channel"></a>Kanał elementu równorzędnego  
 Kanał elementu równorzędnego umożliwia tworzenie wielostronnej aplikacji przy użyciu usługi WCF. Komunikaty wielostronnej występuje w kontekście siatki. Oczek są identyfikowane przez nazwę, która dołączyć do węzłów. Każdy węzeł w kanał elementu równorzędnego tworzy odbiornika TCP w porcie określonych przez użytkownika i ustanawia połączenie z innymi węzłami w siatce w celu zapewnienia odporności. Aby połączyć z innych węzłów w siatce, węzły wymiany niektóre dane, w tym adres odbiornika i adresy IP na komputerze, z innych węzłów w siatce. Komunikaty wysyłane wokół w siatce może zawierać informacje o zabezpieczeniach, które odnoszą się do nadawcy, aby zapobiec fałszowanie wiadomości i manipulowania.  
  
 Żadne informacje osobiste nie są przechowywane na komputerze użytkownika końcowego.  
  
## <a name="it-professional-experience"></a>Profesjonalne środowisko IT  
  
### <a name="tracing"></a>Śledzenie  
 Funkcję diagnostyki, infrastruktura WCF rejestruje komunikaty, które przechodzą przez transportu i warstwy modelu usług i działania oraz zdarzeń związanych z tych komunikatów. Ta funkcja jest domyślnie wyłączona. Jest włączona, przy użyciu pliku konfiguracji aplikacji i zachowanie śledzenia może być modyfikowany, przy użyciu dostawcy WMI usługi WCF w czasie wykonywania. Po włączeniu Infrastruktura śledzenia emituje śledzenia diagnostycznego, który zawiera komunikaty, działań i przetwarzanie zdarzeń do odbiorników skonfigurowanych. Format i lokalizację danych wyjściowych są określane przez opcje konfiguracji odbiornika administratora, ale zazwyczaj jest sformatowany plik XML. Administrator jest odpowiedzialny za ustawiania listy kontroli dostępu (ACL) plików śledzenia. W szczególności gdy hostowany przez System Windows Activation (WAS), administrator powinien upewnij się, że pliki nie są obsługiwane z publicznego katalogu wirtualnego, jeśli nie jest wymagana.  
  
 Istnieją dwa typy śledzenia: rejestrowanie komunikatów i Model usługi diagnostyczne śledzenia, opisane w poniższej sekcji. Każdy typ jest skonfigurowana za pośrednictwem źródła śledzenia: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> i <xref:System.ServiceModel>. Oba te źródła śledzenia rejestrowania przechwytywania danych, które są lokalne dla aplikacji.  
  
### <a name="message-logging"></a>Rejestrowanie komunikatów  
 Rejestrowanie źródła śledzenia komunikatów (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umożliwia administratorom komunikaty dziennika z tego przepływu za pośrednictwem systemu. Za pomocą konfiguracji użytkownik może zdecydować o dziennika całej wiadomości lub tylko nagłówki komunikatu, czy mają być rejestrowane w modelu warstwy transportu i/lub usługę i czy mają zostać dołączone źle sformułowane komunikaty. Ponadto użytkownik może skonfigurować filtrowanie, aby ograniczyć zakres komunikatów są rejestrowane.  
  
 Domyślnie rejestrowanie komunikatów jest wyłączona. Administratorem komputera lokalnego można zapobiec włączenie komunikat logowania administratora dodatku poziomu aplikacji.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Rejestrowanie komunikatów zaszyfrowany i odszyfrowany  
 Komunikaty są rejestrowane, szyfrowane lub odszyfrować, zgodnie z opisem w następujących warunkach.  
  
 Rejestrowanie transportu  
 Rejestruje komunikaty odbieranych i wysyłanych na poziomie transportu. Te komunikaty zawierają wszystkie nagłówki i może być zaszyfrowany przed wysłaniem przesyłania i podczas jego odebrania.  
  
 Jeśli komunikaty są szyfrowane przed wysłaniem przesyłania, a po ich odebraniu są rejestrowane są również szyfrowane. Wyjątkiem jest, gdy protokół zabezpieczeń jest używana (https): są następnie rejestrowane odszyfrowywany przed wysłaniem i po odbierane, nawet jeśli są one zaszyfrowane na łączu.  
  
 Rejestrowanie usługi  
 Rejestruje komunikaty odebrania lub wysłania na poziomie modelu usługi, po kanału nagłówka zostało wykonane przetwarzanie, tuż przed i po wprowadzeniu kodu użytkownika.  
  
 Komunikaty zarejestrowane na tym poziomie są odszyfrowywane, nawet jeśli były one chronione i szyfrowane w sieci.  
  
 Rejestrowanie komunikatów źle sformułowany  
 Rejestruje komunikaty infrastruktura WCF nie może zrozumieć i przetworzyć.  
  
 Komunikaty są rejestrowane jako — oznacza to zaszyfrowane, czy nie  
  
 Gdy komunikaty są rejestrowane formie odszyfrowany lub niezaszyfrowanym domyślnie WCF usuwa kluczy zabezpieczeń i potencjalnie dane osobowe z komunikatów przed ich zalogowaniem. W kolejnych sekcjach opisano, jakie informacje są usuwane i kiedy. Administrator maszyny i jednocześnie wdrażania aplikacji należy wykonać określone akcje konfiguracji, aby zmienić domyślne zachowanie logowania kluczy i potencjalnie dane osobowe.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informacje — usunięte z nagłówków komunikatu podczas logowania się odszyfrować niezaszyfrowanej wiadomości  
 Gdy komunikaty są rejestrowane w odszyfrować niezaszyfrowanej postaci kluczy zabezpieczeń i potencjalnie dane osobowe są usuwane domyślnie na podstawie nagłówków wiadomości oraz treść wiadomości przed ich zarejestrowaniu. Na poniższej liście przedstawiono, jakie WCF uwzględnia kluczy i potencjalnie dane osobowe.  
  
 Klucze, które są usuwane:  
  
 \- Aby uzyskać xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst:BinarySecret  
  
 Wst:Entropy  
  
 \- Aby uzyskać xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Password  
  
 wsse:nonce  
  
 Informacje osobiste potencjalnie, który zostanie usunięty:  
  
 \- Aby uzyskać xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \- Aby uzyskać xmlns:saml = "urn: oasis: nazwy: tc: SAML:1.0:assertion" elementy pogrubione (poniżej) są usuwane:  
  
 \<potwierdzenie  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 AssertionId="[ID]"  
  
 Wystawca = "[string]"  
  
 IssueInstant="[dateTime]"  
  
 >  
  
 \<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]">  
  
 \<AudienceRestrictionCondition >  
  
 \<Audience>[uri]\</Audience>+  
  
 \</AudienceRestrictionCondition>*  
  
 \<DoNotCacheCondition / > *  
  
 <\!--abstrakcji typu podstawowego  
  
 \<Warunek / > *  
  
 -->  
  
 \</ Warunki >?  
  
 \<Doradztwo >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > *  
  
 \<Potwierdzenie > [asercji]\</Assertion > *  
  
 [any] *  
  
 \</ Porady dotyczące >?  
  
 <\!--Abstrakcyjne typy podstawowe  
  
 \<Instrukcja / > *  
  
 \<SubjectStatement>  
  
 \<Temat >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation>  
  
 \<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +  
  
 \<SubjectConfirmationData > [any]\</SubjectConfirmationData >?  
  
 \<ds:KeyInfo>...\</ds:KeyInfo>?  
  
 \</SubjectConfirmation>?  
  
 \</Subject>  
  
 \</SubjectStatement>*  
  
 -->  
  
 \<AuthenticationStatement  
  
 AuthenticationMethod = "[identyfikator uri]"  
  
 AuthenticationInstant="[dateTime]"  
  
 >  
  
 [Tematu]  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <AuthorityBinding  
  
 AuthorityKind="[QName]"  
  
 Lokalizacja = "[identyfikator uri]"  
  
 Binding="[uri]"  
  
 />*  
  
 \</AuthenticationStatement>*  
  
 \<AttributeStatement>  
  
 [Tematu]  
  
 \<Atrybut  
  
 AttributeName="[string]"  
  
 AttributeNamespace="[uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</Attribute>+  
  
 \</AttributeStatement>*  
  
 \<AuthorizationDecisionStatement  
  
 Zasób = "[identyfikator uri]"  
  
 Decision="[Permit&#124;Deny&#124;Indeterminate]"  
  
 >  
  
 [Tematu]  
  
 \<Akcja, Namespace = "[identyfikator uri]" > [string]\<Action > +  
  
 \<Dowód >  
  
 \<AssertionIDReference > [ID]\</AssertionIDReference > +  
  
 \<Potwierdzenie > [asercji]\</Assertion > +  
  
 \</ Dowód >?  
  
 \</AuthorizationDecisionStatement>*  
  
 \</Assertion>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informacje — usunięte z treści wiadomości, podczas logowania się odszyfrować niezaszyfrowanej wiadomości  
 Jak opisano wcześniej, klucze usuwa WCF i znane potencjalnie osobowych z nagłówków komunikatu rejestrowane komunikaty odszyfrować niezaszyfrowane. Ponadto WCF usuwa klucze i znanych potencjalnie dane osobowe z treści wiadomości elementy treści i działań na poniższej liście, które opisują komunikaty zabezpieczeń związane z wymiany kluczy.  
  
 Dla następujących przestrzeni nazw:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (na przykład, jeśli brak dostępnych akcji)  
  
 Informacje są usuwane dla tych elementów treści, które obejmują wymiany kluczy:  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Informacje są również usuwane dla każdego z następujących czynności:  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Informacje nie zostaną usunięte z nagłówków specyficzne dla aplikacji i danych treści  
 Usługi WCF nie śledzi informacje osobiste w nagłówkach specyficzne dla aplikacji (na przykład ciągów zapytań) lub dane treści (na przykład numer karty kredytowej).  
  
 Jeśli rejestrowanie komunikatów jest włączona, informacje osobiste w nagłówkach specyficzne dla aplikacji i treść informacji mogą być widoczne w dziennikach. Ponownie narzędzia do wdrażania aplikacji jest odpowiedzialna za ustawienie listy kontroli dostępu dla plików dziennika i konfiguracji. Może on także wyłączyć rejestrowanie, jeśli użytkownik nie chce, aby te informacje mają być wyświetlane lub może on filtrować te informacje w plikach dziennika po jej zarejestrowaniu.  
  
### <a name="service-model-tracing"></a>Śledzenie modelu usług  
 Źródło śladu Model usługi (<xref:System.ServiceModel>) umożliwia śledzenie działań i zdarzenia związane z przetwarzania wiadomości. Ta funkcja korzysta z funkcji diagnostycznych systemu .NET Framework z <xref:System.Diagnostics>. Podobnie jak w przypadku <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> właściwości, lokalizację i jego listy ACL są konfigurowanych przez użytkownika za pomocą plików konfiguracji aplikacji .NET Framework. Podobnie jak w przypadku rejestrowania komunikatów lokalizacja pliku jest zawsze konfigurowane podczas administrator włącza śledzenie; w związku z tym administrator steruje listy ACL.  
  
 Ślady zawierają nagłówki wiadomości, gdy komunikat jest w zakresie. Zastosuj te same zasady stosowania ukrywanie potencjalnie osobowe w nagłówkach wiadomości w poprzedniej sekcji: wcześniej zidentyfikować dane osobowe są usuwane domyślnie z nagłówków w śladach. Administrator maszyny i wdrażania aplikacji należy zmodyfikować konfigurację rejestrowania potencjalnie dane osobowe. Jednak informacji osobistych znajdujących się w nagłówkach specyficzne dla aplikacji jest rejestrowane w śladach. Narzędzia do wdrażania aplikacji jest odpowiedzialna za ustawienie listy kontroli dostępu dla plików konfiguracji i śledzenia. On również wyłączyć śledzenie Jeśli użytkownik nie chce, aby te informacje mają być wyświetlane lub on można odfiltrować te informacje z plików śledzenia, po ich zarejestrowaniem.  
  
 W ramach modelu ServiceModel śledzenia, unikatowe identyfikatory (nazywane identyfikatory aktywności i zazwyczaj identyfikator GUID) łączenie różnych działań jako wiadomość odbywa się za pośrednictwem różnych części infrastruktury.  
  
#### <a name="custom-trace-listeners"></a>Obiekty nasłuchujące śledzenia niestandardowe  
 Dla obu komunikatu rejestrowania i śledzenia można skonfigurować odbiornik śledzenia niestandardowego, który można wysłać danych śledzenia i wiadomości na łączu (na przykład do zdalnej bazy danych). Narzędzia do wdrażania aplikacji jest odpowiedzialny za konfigurowanie niestandardowe odbiorniki lub umożliwienie użytkownikom to zrobić. Jest on również odpowiedzialny za wszelkie informacje osobiste, które zostały ujawnione w lokalizacji zdalnej i prawidłowo zastosowania list ACL do tej lokalizacji.  
  
### <a name="other-features-for-it-professionals"></a>Inne funkcje dla specjalistów IT  
 Usługi WCF jest dostawca WMI, która udostępnia informacje o konfiguracji infrastruktury usług WCF za pomocą usługi WMI (dostarczane z programem Windows). Domyślnie interfejs usługi WMI są dostępne dla administratorów.  
  
 Mechanizm konfiguracji .NET Framework korzysta z konfiguracji usługi WCF. Pliki konfiguracji są przechowywane na komputerze. Deweloper aplikacji i administrator tworzyć pliki konfiguracji i listy ACL dla każdego wymagania aplikacji. Plik konfiguracji może zawierać adresy punktów końcowych i łącza do certyfikatów w magazynie certyfikatów. Certyfikaty mogą służyć do zapewnienia danych aplikacji, aby skonfigurować różne właściwości funkcje używane przez aplikację.  
  
 Usługi WCF również korzysta z funkcji zrzutu procesu .NET Framework, wywołując <xref:System.Environment.FailFast%2A> metody.  
  
### <a name="it-pro-tools"></a>IT Pro Tools  
 Usługi WCF zapewnia również następujące IT profesjonalne narzędzia, które są dostępne w zestawie Windows SDK.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 Przeglądarka wyświetla pliki śledzenia WCF. Podgląd pokazuje wszelkie informacje zawarte w śladów.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Edytor zezwala użytkownikowi na tworzenie i edytowanie plików konfiguracyjnych WCF. Edytor pokazuje dowolne informacje są zawarte w plikach konfiguracji. Tego samego zadania można wykonywać za pomocą edytora tekstów.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 To narzędzie umożliwia użytkownikowi zarządzanie ServiceModel instaluje na komputerze. Narzędzie wyświetla komunikaty o stanie w oknie konsoli, gdy go, w procesie, mogą być wyświetlane informacje o konfiguracji instalacji usługi WCF.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe i WSATUI.dll  
 Te narzędzia umożliwiają specjalistom IT Konfigurowanie obsługi sieci w usłudze interoperacyjne WS-AtomicTransaction programu WCF. Narzędzia, wyświetlaj i Zezwalaj użytkownikowi na zmianę wartości najczęściej używanych ustawień WS-AtomicTransaction przechowywane w rejestrze.  
  
## <a name="cross-cutting-features"></a>Funkcje ogólne  
 Następujące funkcje są kompleksowymi. Oznacza to mogą być złożone z żadnym z powyższych funkcji.  
  
### <a name="service-framework"></a>Struktura usługi  
 Nagłówki może zawierać Identyfikatora wystąpienia, który jest identyfikatorem GUID, który kojarzy wiadomość z wystąpieniem klasy CLR.  
  
 Web Services Description Language (WSDL) zawiera definicję portu. Każdy port ma adres punktu końcowego i powiązania, który reprezentuje usług używanych przez aplikację. Udostępnianie WSDL można wyłączyć za pomocą konfiguracji. Żadne informacje nie są przechowywane na komputerze.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Communication Foundation](https://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [Zabezpieczenia](../../../docs/framework/wcf/feature-details/security.md)
