---
title: "Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
caps.latest.revision: "34"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53fc4be67fd3f6a7b2b8c914c11fb6540b28c199
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-privacy-information"></a>Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)
Firma Microsoft dba o ochronę prywatności użytkowników końcowych. Podczas budowania aplikacji przy użyciu [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], wersja 3.0, aplikacja może mieć wpływ na prywatność użytkowników końcowych. Na przykład aplikacja jawnie może zbierać informacje kontaktowe użytkownika lub może zażądać, lub wysłać informacje przez Internet do witryny sieci Web. Jeśli technologii firmy Microsoft możesz osadzić w aplikacji, technologia ta może być własną zachowanie, które mogą mieć wpływ na prywatność. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]nie wysyła żadnych informacji do firmy Microsoft z aplikacji, chyba że użytkownik lub użytkownik końcowy wybrać do wysyłania do nas.  
  
## <a name="wcf-in-brief"></a>Usługi WCF w Brief  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]rozproszone framework komunikatów używa programu Microsoft .NET Framework, która umożliwia deweloperom tworzenie aplikacji rozproszonych. Komunikaty przekazywane między dwiema aplikacjami zawierają informacje nagłówek i treść.  
  
 Nagłówki może zawierać rozsyłania wiadomości, informacje o zabezpieczeniach transakcji i dłużej w zależności od usługi używane przez aplikację. Komunikaty są zwykle domyślnie szyfrowane. Jedynym wyjątkiem jest przy użyciu `BasicHttpBinding`, który został zaprojektowany do użytku z usługami sieci Web nie jest zabezpieczony, starszej wersji. Projektant aplikacji jest odpowiedzialny za ostatecznego projektu. W treści protokołu SOAP wiadomości dane specyficzne dla aplikacji; Jednak te dane, takie jak zdefiniowane przez aplikację informacje osobiste, mogą być chronione przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] funkcje szyfrowania i poufności. W poniższych sekcjach opisano funkcje, które mogą mieć wpływ na prywatność.  
  
## <a name="messaging"></a>Obsługa wiadomości  
 Każdy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wiadomość zawiera nagłówek adres, który określa lokalizację docelową wiadomości i gdzie odpowiedzi.  
  
 Składnik adres adresu punktu końcowego jest zasobów identyfikator URI (Uniform), który identyfikuje punkt końcowy. Adres może być adresu sieciowego lub adres logiczny. Adres może zawierać nazwy komputera (nazwa hosta, pełna nazwa domeny) i adres IP. Adres punktu końcowego może również zawierać unikatowy identyfikator globalny (GUID) lub kolekcja identyfikatorów GUID adresowania tymczasowych używany do wykrycia każdy adres. Każdy komunikat zawiera identyfikator wiadomości, który jest identyfikatorem GUID. Ta funkcja jest zgodna standardowego wzorca WS-Addressing.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Warstwa obsługi wiadomości nie zapisuje żadnych informacji osobistych na komputerze lokalnym. Jednak go może propagowania informacji osobistych na poziomie sieci Jeśli dewelopera usługi utworzył to usługa, która udostępnia takie informacje (na przykład za pomocą nazwisko osoby w nazwie punktu końcowego, lub w tym informacje osobiste w sieci Web punktu końcowego Services Description Language, ale nie wymaga klientów do używania protokołu https można uzyskać dostępu do WSDL). Ponadto, gdy działa dewelopera [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie względem punktu końcowego, który opisuje informacje osobiste, dane wyjściowe narzędzia mogą zawierać te informacje i są zapisywane w pliku docelowym lokalny dysk twardy.  
  
## <a name="hosting"></a>Hosting  
 Funkcję hostingu w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] umożliwia aplikacjom można uruchomić na żądanie lub włączyć Udostępnianie portów między wieloma aplikacjami. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Aplikacji może być hostowana w Internet Information Services (IIS), podobny do [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  
  
 Hosting nie ujawnia żadnych określonych informacji w sieci i nie przechowuje danych na tym komputerze.  
  
## <a name="message-security"></a>Zabezpieczenia komunikatów  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]funkcja zabezpieczenia oferuje funkcje zabezpieczeń dla aplikacji do obsługi wiadomości. Dostępne funkcje zabezpieczeń obejmują uwierzytelniania i autoryzacji.  
  
 Uwierzytelnianie jest wykonywane przez przekazanie poświadczeń między klientami i usługami. Uwierzytelniania mogą być przez zabezpieczenia na poziomie transportu lub za pośrednictwem protokołu SOAP wiadomości poziomu zabezpieczeń, w następujący sposób:  
  
-   W ramach zabezpieczeń komunikatów SOAP uwierzytelnianie jest przeprowadzane za pomocą poświadczeń, takie jak nazwa użytkownika/hasła, certyfikaty X.509 biletów Kerberos i tokeny SAML, które mogą zawierać informacje osobiste, w zależności od wystawcy.  
  
-   Za pomocą zabezpieczeń transportu, uwierzytelnianie odbywa się za pośrednictwem tradycyjnych transportu mechanizmów uwierzytelniania, takich jak schematy uwierzytelniania HTTP (Basic, Digest, Negotiate, zintegrowanej autoryzacji systemu Windows, NTLM, None i anonimowe) i uwierzytelniania formularzy.  
  
 Uwierzytelnianie może spowodować bezpiecznej sesji między komunikacji punktów końcowych. Sesja jest identyfikowany przez identyfikator GUID, który jest ważny przez czas ich istnienia sesji zabezpieczeń. W poniższej tabeli pokazano, co jest zachowywane i gdzie.  
  
|Dane|Magazyn|  
|----------|-------------|  
|Poświadczenia prezentacji, takie jak nazwa użytkownika, certyfikaty X.509, tokeny protokołu Kerberos i odwołania do poświadczeń.|Standardowy system Windows poświadczeń mechanizmów zarządzania, takich jak magazynu certyfikatów systemu Windows.|  
|Członkostwo informacje o użytkowniku, takie jak nazwy użytkowników i hasła.|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]dostawcy członkostwa.|  
|Informacje dotyczące usługi używany do uwierzytelniania usługi dla klientów tożsamości.|Adres punktu końcowego usługi.|  
|Informacje o wywołującym.|Dzienniki inspekcji.|  
  
## <a name="auditing"></a>Inspekcja  
 Inspekcja rejestruje sukces i niepowodzenie zdarzeń uwierzytelniania i autoryzacji. Rekordy inspekcji zawierają następujące dane: z identyfikatora URI, identyfikator URI akcji i identyfikator obiektu wywołującego.  
  
 Inspekcja również są rejestrowane podczas administrator Modyfikuje konfigurację rejestrowanie komunikatów (Włączanie on lub off), ponieważ rejestrowanie komunikatów mogą rejestrować dane specyficzne dla aplikacji w nagłówkach i treści. Aby uzyskać [!INCLUDE[wxp](../../../includes/wxp-md.md)], rekord jest rejestrowane w dzienniku zdarzeń aplikacji. Aby uzyskać [!INCLUDE[wv](../../../includes/wv-md.md)] i [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], rekord jest rejestrowane w dzienniku zdarzeń zabezpieczeń.  
  
## <a name="transactions"></a>Transakcje  
 Funkcja transakcji zapewnia transakcyjnych usług [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji.  
  
 Nagłówki transakcji używanych w propagacji transakcji mogą zawierać identyfikatorów transakcji lub rejestracji identyfikatorów, które są identyfikatorami GUID.  
  
 Funkcja transakcji używa Menedżera transakcji koordynatora transakcji rozproszonych (MSDTC) (składnik systemu Windows) do zarządzania stanem transakcji. Domyślnie komunikacja między menedżerami transakcje są szyfrowane. Menedżerowie transakcji mogą rejestrować odwołania do punktu końcowego, identyfikatory transakcji i identyfikatory rejestracji w ramach stanu trwałego. Okres istnienia tego stanu jest określana przez okres istnienia pliku dziennika Menedżera transakcji. Usługa MSDTC jest właścicielem i przechowuje ten dziennik.  
  
 Funkcja transakcji implementuje standardy koordynacji WS i protokołu WS-AT.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] przesyłanie komunikatów, gdy występują błędy transportu lub pośrednika. Udostępniają one dokładnie — raz transferu wiadomości, nawet wtedy, gdy transportu źródłowego rozłącza (na przykład połączenie TCP w sieci bezprzewodowej) lub utraci wiadomości (serwer proxy HTTP porzucenie komunikat wychodzące lub przychodzące). Niezawodne sesje także odzyskać komunikat zmianę kolejności (co może się tak zdarzyć w przypadku wielu ścieżek routing), zachowując kolejności, w jakiej zostały wysłane wiadomości.  
  
 Niezawodne sesje są implementowane za pomocą protokołu WS-ReliableMessaging (WS-RM). Dodaj one nagłówków protokołu WS-RM, zawierające informacje sesji, który jest używany do identyfikowania komunikatów wszystkich skojarzonych z określonym niezawodnej sesji. Każdej sesji protokołu WS-RM ma identyfikator, który jest identyfikatorem GUID.  
  
 Żadne informacje osobiste nie są przechowywane na komputerze użytkownika końcowego.  
  
## <a name="queued-channels"></a>Kanały w kolejce  
 Kolejki przechowywania komunikatów z aplikacja wysyłająca imieniu aplikację i później przekazywanie tych wiadomości do aplikacji odbierającej. One zapewnić transferu wiadomości z aplikacji wysyłającej aplikacje odbierające, na przykład aplikacja odbierająca jest przejściowy. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]zapewnia obsługę dla usługi kolejkowania wiadomości przy użyciu usługi kolejkowania wiadomości firmy Microsoft (MSMQ) do ich przenoszenia.  
  
 Funkcja kanałów w kolejce nie dodaje nagłówki na wiadomość. Zamiast tego tworzy komunikatów usługi kolejkowania komunikatów z odpowiedniego zbioru właściwości komunikatów usługi kolejkowania komunikatów i wywołuje metody kolejkowania put wiadomości w kolejce usługi kolejkowania komunikatów. Usługa kolejkowania komunikatów jest opcjonalnym składnikiem, który jest dostarczany z systemem Windows.  
  
 Nie informacje są przechowywane na komputerze użytkownika końcowego przez funkcję umieszczonych w kolejce kanałów, ponieważ używa usługi kolejkowania komunikatów jako kolejkowania infrastruktury.  
  
## <a name="com-integration"></a>Integracja modelu COM+  
 Ta funkcja jest zawijana istniejące funkcje COM i COM + do tworzenia usług, które są zgodne z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług. Ta funkcja nie korzysta z określonych nagłówków i nie zachowuje danych na komputerze użytkownika końcowego.  
  
## <a name="com-service-moniker"></a>Moniker usługi COM  
 Zapewnia to niezarządzany otoki do standardowego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta. Ta funkcja nie ma określonego nagłówki przesyłania ani jest utrwalenia danych na tym komputerze.  
  
## <a name="peer-channel"></a>Kanał elementu równorzędnego  
 Kanał elementu równorzędnego umożliwia programowanie wielopartyjnej aplikacji przy użyciu [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Wiadomości wielopartyjnej występuje w kontekście siatki. Siatki są identyfikowane przez nazwę, która może dołączać węzłów. Każdy węzeł w kanału równorzędnego tworzy odbiornika TCP w porcie określone przez użytkownika i ustanawia połączenie z innych węzłach w sieci w celu zapewnienia odporności. Aby połączyć inne węzły w siatce, węzły wymiany niektórych danych, w tym adres odbiornika i adresów IP na komputerze, na innych węzłach w sieci. Komunikaty wysyłane wokół w siatce może zawierać zabezpieczeń informacji dotyczących nadawcy, aby uniknąć fałszowania wiadomości i naruszeniu.  
  
 Żadne informacje osobiste nie są przechowywane na komputerze użytkownika końcowego.  
  
## <a name="it-professional-experience"></a>Środowisko pracy specjalistów IT  
  
### <a name="tracing"></a>Śledzenie  
 Funkcja diagnostyki [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastruktury rejestruje komunikaty, które przechodzą przez warstwy modelu transportu i usługi oraz działania i zdarzeń związanych z tych wiadomości. Ta funkcja jest domyślnie wyłączona. Jest włączone, za pomocą pliku konfiguracji aplikacji i zachowanie śledzenia może zostać zmodyfikowany za pomocą [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] dostawcy WMI w czasie wykonywania. Po włączeniu Infrastruktura śledzenia emituje śledzenia diagnostycznego, zawierający wiadomości, działań i odbiorników skonfigurowanych przetwarzania zdarzeń. Format i lokalizacja danych wyjściowych zależą od opcji konfiguracji odbiornika administratora, ale jest zwykle sformatowanym plikiem XML. Administrator jest odpowiedzialny za ustawienie listy kontroli dostępu (ACL) dla plików śledzenia. W szczególności obsługiwany przez System aktywacji systemu Windows (WAS), administrator powinien upewnij się, że pliki nie są obsługiwane z katalogu publiczny wirtualnego katalogu głównego, jeśli nie jest wymagana.  
  
 Istnieją dwa typy śledzenie: rejestrowanie komunikatów i modelu usługi diagnostyczne śledzenia, opisane w poniższej sekcji. Każdy typ jest skonfigurowana za pośrednictwem źródła śledzenia: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> i <xref:System.ServiceModel>. Oba te źródła śledzenia rejestrowania przechwytywania danych, które są lokalne dla aplikacji.  
  
### <a name="message-logging"></a>Rejestrowanie komunikatów  
 Rejestrowanie źródła śledzenia komunikatów (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umożliwia administratorom komunikaty dziennika przepływające za pośrednictwem systemu. Za pomocą konfiguracji użytkownik może zadecydować o dziennika całego wiadomości lub tylko nagłówki komunikatu, czy mają być rejestrowane w modelu warstwy transportu i/lub usługi i czy mają być źle sformułowane wiadomości. Ponadto użytkownik może konfigurować filtrowania do ograniczenia, które komunikaty są rejestrowane.  
  
 Domyślnie rejestrowanie komunikatów jest wyłączona. Administratora komputera lokalnego uniemożliwi włączanie komunikat logowania administratora poziomie aplikacji.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Rejestrowanie komunikatów zaszyfrowane i odszyfrowane  
 Komunikaty są rejestrowane, szyfrowane lub odszyfrować, zgodnie z opisem w następujących warunkach.  
  
 Rejestrowanie transportu  
 Rejestruje komunikaty odebranych i wysłanych na poziomie transportu. Te komunikaty zawierają wszystkie nagłówki i może być zaszyfrowany przed wysłaniem przesyłania i podczas odbierane.  
  
 W przypadku wiadomości są szyfrowane przed wysłaniem przesyłania i po odebraniu, są rejestrowane również szyfrowane. Wyjątek jest gdy protokół zabezpieczeń jest używana (https): są następnie rejestrowane odszyfrować przed wysłaniem i po nich odbierane, nawet jeśli są one zaszyfrowane w trakcie przesyłania.  
  
 Usługa rejestrowania  
 Rejestruje komunikaty odebranych lub wysłanych na poziomie modelu usługi, po podczas przetwarzania nagłówka kanału, bezpośrednio przed i po wprowadzeniu kodu użytkownika.  
  
 Komunikaty zarejestrowane na tym poziomie są odszyfrowywane, nawet jeśli były zabezpieczone i zaszyfrowane w trakcie przesyłania.  
  
 Rejestrowanie komunikatów źle sformułowany  
 Dzienniki wiadomości, które [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastruktury nie może zrozumieć lub przetworzenia.  
  
 Komunikaty są rejestrowane jako — to znaczy szyfrowane lub nie  
  
 Jeśli komunikaty są rejestrowane odszyfrować lub niezaszyfrowanej postaci domyślnie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usuwa kluczy zabezpieczeń i potencjalnie dane osobowe z komunikatów przed ich zalogowaniem. Kolejne sekcje opisują, jakie informacje zostaną usunięte oraz kiedy. Administrator maszyny i jednocześnie wdrażania aplikacji należy wykonać pewne akcje konfiguracji, aby zmienić domyślne zachowanie logowania kluczy i potencjalnie danych osobowych.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informacje o usunięte z nagłówków komunikatu podczas logowania się odszyfrować niezaszyfrowane wiadomości  
 Jeśli komunikaty są rejestrowane w odszyfrować niezaszyfrowanej postaci kluczy zabezpieczeń i potencjalnie danych osobowych są usuwane domyślnie nagłówki komunikatów i treści wiadomości, zanim są rejestrowane. Na poniższej liście przedstawiono co [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uwzględnia kluczy i potencjalnie danych osobowych.  
  
 Klucze, które zostały usunięte:  
  
 \-Xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 Wst:BinarySecret  
  
 Wst:Entropy  
  
 \-Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:Password  
  
 wsse:nonce  
  
 Potencjalnie osobiste informacje zostaną usunięte:  
  
 \-Xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse:username  
  
 wsse:BinarySecurityToken  
  
 \-Dla xmlns:saml = "urn: oasis: nazwy: tc: SAML:1.0:assertion" są usuwane elementy pogrubione (poniżej):  
  
 \<Potwierdzenia  
  
 MajorVersion = "1"  
  
 MinorVersion = "1"  
  
 Identyfikator potwierdzenia = "[identyfikator]"  
  
 Wystawca = "[parametry]"  
  
 IssueInstant = "[dateTime]"  
  
 >  
  
 \<Warunki nie wcześniej niż = "[dateTime]" NotOnOrAfter = "[dateTime]" >  
  
 \<AudienceRestrictionCondition >  
  
 \<Grupy odbiorców > [identyfikator uri]\</Audience > +  
  
 \</ AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition / > *  
  
 <\!--abstrakcyjnej typu podstawowego  
  
 \<Warunek / > *  
  
 -->  
  
 \</ Warunki >?  
  
 \<Porady >  
  
 \<AssertionIDReference > [identyfikator]\</AssertionIDReference > *  
  
 \<Potwierdzenie > [potwierdzenie]\</Assertion > *  
  
 [any] *  
  
 \</ Porady >?  
  
 <\!--Abstrakcyjnych typów podstawowych  
  
 \<Instrukcja / > *  
  
 \<SubjectStatement >  
  
 \<Temat >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation >  
  
 \<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +  
  
 \<SubjectConfirmationData > [any]\</SubjectConfirmationData >?  
  
 \<DS:KeyInfo >... \</ds:KeyInfo >?  
  
 \</ SubjectConfirmation >?  
  
 \</ Temat >  
  
 \</ SubjectStatement > *  
  
 -->  
  
 \<AuthenticationStatement  
  
 AuthenticationMethod = "[identyfikator uri]"  
  
 AuthenticationInstant = "[dateTime]"  
  
 >  
  
 [Podmiotu]  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 < AuthorityBinding  
  
 Atrybut AuthorityKind = "[QName]"  
  
 Lokalizacja = "[identyfikator uri]"  
  
 Powiązanie = "[identyfikator uri]"  
  
 />*  
  
 \</ AuthenticationStatement > *  
  
 \<AttributeStatement >  
  
 [Podmiotu]  
  
 \<Atrybut  
  
 AttributeName = "[parametry]"  
  
 AttributeNamespace = "[identyfikator uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</ Atrybut > +  
  
 \</ AttributeStatement > *  
  
 \<AuthorizationDecisionStatement  
  
 Zasób = "[identyfikator uri]"  
  
 Decyzja = "[zezwolenia &#124; Odmów &#124; nieokreślony]"  
  
 >  
  
 [Podmiotu]  
  
 \<Akcja Namespace = "[identyfikator uri]" > [parametry]\<Action > +  
  
 \<Dowód >  
  
 \<AssertionIDReference > [identyfikator]\</AssertionIDReference > +  
  
 \<Potwierdzenie > [potwierdzenie]\</Assertion > +  
  
 \</ Dowody >?  
  
 \</ AuthorizationDecisionStatement > *  
  
 \</ Potwierdzenie >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informacje o usuwane z treści wiadomości, gdy rejestrowanie komunikatów odszyfrować niezaszyfrowanej  
 Jak opisano wcześniej, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usuwa klucze i znanych potencjalnie dane osobowe z nagłówki komunikatów zarejestrowane komunikaty odszyfrować niezaszyfrowane. Ponadto [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usuwa klucze i znanych potencjalnie dane osobowe z treści wiadomości treści elementy i działania na poniższej liście, które opisują komunikaty zabezpieczeń związane z wymiany kluczy.  
  
 Dla następujących przestrzeni nazw:  
  
 xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (na przykład, jeśli brak dostępnych akcji)  
  
 Informacje są usuwane z tych elementów treści, które obejmują wymiany kluczy:  
  
 Wst:RequestSecurityToken  
  
 Wst:RequestSecurityTokenResponse  
  
 Wst:RequestSecurityTokenResponseCollection  
  
 Informacje są również usuwane dla każdego z następujących czynności:  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/validate  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/renew  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel  
  
 http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RST/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RSTR/SCT  
  
 http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RST/SCT-Amend  
  
 http://schemas.xmlsoap.org/ws/2004/04/Security/Trust/RSTR/SCT-Amend  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Informacje nie zostaną usunięte z nagłówków specyficzne dla aplikacji i danych treści  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]nie śledzi informacje osobiste w nagłówkach specyficzne dla aplikacji (na przykład ciągi zapytań) lub treści danych (na przykład numer karty kredytowej).  
  
 Po włączeniu rejestrowania komunikatów informacje osobiste w nagłówkach specyficzne dla aplikacji i informacje mogą być widoczne w dziennikach. Ponownie wdrażania aplikacji jest odpowiedzialny za ustawienie listy kontroli dostępu dla plików dziennika i konfiguracji. Może on również wyłączenie rejestrowania, jeśli on nie chce, aby te informacje mają być wyświetlane lub może on filtrować te informacje z plików dziennika po jest rejestrowany.  
  
### <a name="service-model-tracing"></a>Śledzenie modelu usług  
 Źródła śledzenia modelu usług (<xref:System.ServiceModel>) umożliwia śledzenie działań i zdarzenia związane z przetwarzania komunikatów. Ta funkcja korzysta z funkcji diagnostycznych .NET Framework z <xref:System.Diagnostics>. Jak <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> właściwości, lokalizację i jego listy ACL są użytkownika — można skonfigurować za pomocą plików konfiguracji aplikacji .NET Framework. Podobnie jak w przypadku rejestrowania komunikatów lokalizacja pliku jest zawsze konfigurowane gdy administrator włączy śledzenie; w związku z tym administrator kontroluje listy ACL.  
  
 Ślady zawierał nagłówków komunikatów, gdy komunikat jest w zakresie. Te same zasady ukrywania potencjalnie osobowych w nagłówkach wiadomości w poprzedniej sekcji: dane osobowe wcześniej ustaloną jest usuwane domyślnie z nagłówków śladów. Zarówno administrator maszyny i wdrażania aplikacji musi zmodyfikować konfigurację, aby można było zalogować potencjalnie danych osobowych. Jednak osobiste informacje zawarte w nagłówkach specyficzne dla aplikacji są rejestrowane w śladów. Narzędzia wdrażania aplikacji jest odpowiedzialny za ustawienie listy kontroli dostępu do plików konfiguracji i śledzenia. On również wyłączyć śledzenie Jeśli on nie chce, aby te informacje mają być wyświetlane lub on można odfiltrować te informacje z plików śledzenia, po jest rejestrowany.  
  
 W ramach śledzenia ServiceModel unikatowe identyfikatory (nazywane identyfikatory aktywności i zazwyczaj identyfikator GUID) łączenie różnych działań jako wiadomości przez różne części infrastruktury.  
  
#### <a name="custom-trace-listeners"></a>Obiekty nasłuchujące śledzenia niestandardowych  
 Dla obu komunikat rejestrowania i śledzenia można skonfigurować odbiornik śledzenia niestandardowego, który może wysyłać dane śledzenia i komunikaty umieszczonego w (na przykład do zdalnej bazy danych). Narzędzia wdrażania aplikacji jest odpowiedzialny za konfigurowanie niestandardowych odbiorników lub umożliwienie użytkownikom to zrobić. Odpowiada on też żadnych informacji osobistych widoczne w lokalizacji zdalnej i stosowania prawidłowo listy kontroli dostępu do tej lokalizacji.  
  
### <a name="other-features-for-it-professionals"></a>Inne funkcje dla specjalistów IT  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]ma dostawcę WMI, który ujawnia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] informacje o konfiguracji infrastruktury za pomocą usługi WMI (dostarczane z systemem Windows). Domyślnie interfejs WMI są dostępne dla administratorów.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Konfiguracja korzysta z mechanizmu konfiguracji .NET Framework. Pliki konfiguracji są przechowywane na tym komputerze. Deweloper aplikacji i administrator utworzyć pliki konfiguracji i listy ACL dla każdego wymagania aplikacji. Plik konfiguracji może zawierać adresy punktów końcowych i łącza do certyfikaty w magazynie certyfikatów. Certyfikaty mogą służyć do zapewnienia danych aplikacji, aby skonfigurować różne właściwości funkcje używane przez aplikację.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]używa również funkcje .NET Framework zrzutu procesu przez wywołanie metody <xref:System.Environment.FailFast%2A> metody.  
  
### <a name="it-pro-tools"></a>IT Pro Tools  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]dostępne są także następujące narzędzia specjalistów IT, które są dostępne w zestawie Windows SDK.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 Wyświetla podgląd [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pliki śledzenia. Podgląd pokazuje, niezależnie od informacji znajduje się w dane śledzenia.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Edytor zezwala użytkownikowi na tworzenie i edytowanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] plików konfiguracyjnych. Edytor pokazuje, niezależnie od informacje są przechowywane w plikach konfiguracji. Tego samego zadania można osiągnąć za pomocą edytora tekstu.  
  
#### <a name="servicemodelreg"></a>ServiceModel_Reg  
 To narzędzie umożliwia użytkownikom zarządzanie ServiceModel instaluje na komputerze. Narzędzie wyświetla komunikaty o stanie w oknie konsoli, kiedy uruchamia i, w rezultacie mogą być wyświetlane informacje o konfiguracji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] instalacji.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig.exe i WSATUI.dll  
 Te narzędzia umożliwiają specjalistów IT skonfigurować interoperacyjne Obsługa sieci WS-AtomicTransaction w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Narzędzia wyświetlania i Zezwalaj użytkownikowi na zmianę wartości najczęściej używane ustawienia protokołu WS-AtomicTransaction przechowywane w rejestrze.  
  
## <a name="cross-cutting-features"></a>Kompleksowe funkcje  
 Następujące funkcje są powiązane. Oznacza to, że można je składa się z żadnym z powyższych funkcji.  
  
### <a name="service-framework"></a>Struktura usługi  
 Nagłówki może zawierać identyfikator wystąpienia, który jest identyfikatorem GUID, który kojarzy komunikat z wystąpienia klasy CLR.  
  
 Web Services Description Language (WSDL) zawiera definicję portu. Każdy port ma adres punktu końcowego i powiązania, które reprezentuje usługi używane przez aplikację. Udostępnianie WSDL można wyłączyć za pomocą konfiguracji. Żadne informacje nie są przechowywane na tym komputerze.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Communication Foundation](http://msdn.microsoft.com/en-us/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [Zabezpieczeń](../../../docs/framework/wcf/feature-details/security.md)
