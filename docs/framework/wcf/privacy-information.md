---
title: Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: b724ff1ce85442f64980fdc972188705992d5a4f
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094985"
---
# <a name="windows-communication-foundation-privacy-information"></a>Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)
Firma Microsoft jest zobowiązana do ochrony prywatności użytkowników końcowych. W przypadku kompilowania aplikacji przy użyciu programu Windows Communication Foundation (WCF) w wersji 3,0 Aplikacja może mieć wpływ na prywatność użytkowników końcowych. Na przykład aplikacja może jawnie zbierać informacje kontaktowe użytkownika lub może zażądać lub wysłać informacje przesyłane przez Internet do witryny sieci Web. Jeśli osadzisz technologię firmy Microsoft w aplikacji, ta technologia może mieć własne zachowanie, które może mieć wpływ na prywatność. Usługa WCF nie wysyła żadnych informacji do firmy Microsoft z aplikacji, chyba że użytkownik lub użytkownik końcowy zdecyduje się wysłać do nas.  
  
## <a name="wcf-in-brief"></a>WCF w skrócie  
 WCF to dystrybuowana struktura obsługi komunikatów przy użyciu platformy Microsoft .NET, która umożliwia deweloperom tworzenie aplikacji rozproszonych. Komunikaty przesyłane między dwiema aplikacjami zawierają informacje o nagłówku i treści.  
  
 Nagłówki mogą zawierać routing wiadomości, informacje o zabezpieczeniach, transakcje i wiele więcej w zależności od usług używanych przez aplikację. Komunikaty są zwykle szyfrowane domyślnie. Jedynym wyjątkiem jest użycie `BasicHttpBinding`, który został zaprojektowany do użycia z niezabezpieczonymi, starszymi usługami sieci Web. Jako projektant aplikacji jest odpowiedzialny za końcowy projekt. Komunikaty w treści protokołu SOAP zawierają dane specyficzne dla aplikacji; Jednak te dane, takie jak zdefiniowane przez aplikację dane osobowe, mogą być chronione przy użyciu funkcji szyfrowania lub poufności programu WCF. W poniższych sekcjach opisano funkcje, które mogą mieć wpływ na prywatność.  
  
## <a name="messaging"></a>Obsługa komunikatów  
 Każdy komunikat WCF ma nagłówek adresu, który określa miejsce docelowe wiadomości i miejsce, w którym odpowiedź powinna zostać wysłana.  
  
 Składnik adresu punktu końcowego jest Uniform Resource Identifier (URI), który identyfikuje punkt końcowy. Adres może być adresem sieciowym lub adresem logicznym. Adres może zawierać nazwę komputera (nazwa hosta, w pełni kwalifikowaną nazwę domeny) i adres IP. Adres punktu końcowego może również zawierać unikatowy identyfikator globalny (GUID) lub kolekcję identyfikatorów GUID do tymczasowego adresowania służącego do rozpoznać każdego adresu. Każdy komunikat zawiera identyfikator, który jest identyfikatorem GUID. Ta funkcja jest zgodna ze standardem odwołania WS-Addressing.  
  
 Warstwa obsługi komunikatów WCF nie zapisuje żadnych danych osobowych na komputerze lokalnym. Jednak może ona propagować dane osobowe na poziomie sieci, jeśli deweloper usługi utworzył usługę, która udostępnia takie informacje (na przykład przy użyciu nazwy osoby w nazwie punktu końcowego lub w tym informacje osobiste w sieci Web punktu końcowego Usługi opisujące język, ale nie wymaga, aby klienci korzystali z protokołu HTTPS w celu uzyskania dostępu do języka WSDL. Ponadto, jeśli deweloper uruchamia narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) dla punktu końcowego, który uwidacznia dane osobowe, dane wyjściowe narzędzia mogą zawierać te informacje, a plik wyjściowy jest zapisywana na lokalnym dysku twardym.  
  
## <a name="hosting"></a>Hosting  
 Funkcja hostingu w programie WCF umożliwia uruchamianie aplikacji na żądanie lub Włączanie udostępniania portów między wieloma aplikacjami. Aplikacja WCF może być hostowana w Internet Information Services (IIS), podobnie jak ASP.NET.  
  
 Hosting nie ujawnia żadnych określonych informacji w sieci i nie przechowuje danych na komputerze.  
  
## <a name="message-security"></a>Zabezpieczenia komunikatów  
 Zabezpieczenia WCF zapewniają funkcje zabezpieczeń dla aplikacji do obsługi komunikatów. Dostępne funkcje zabezpieczeń obejmują uwierzytelnianie i autoryzację.  
  
 Uwierzytelnianie jest wykonywane przez przekazywanie poświadczeń między klientami i usługami. Uwierzytelnianie może należeć przez zabezpieczenia na poziomie transportu lub przez zabezpieczenia na poziomie komunikatów protokołu SOAP w następujący sposób:  
  
- W zabezpieczeniach protokołu SOAP uwierzytelnianie odbywa się za pośrednictwem poświadczeń, takich jak nazwa użytkownika/hasła, certyfikaty X. 509, bilety protokołu Kerberos i tokeny SAML, które mogą zawierać informacje osobiste, w zależności od wystawcy.  
  
- Korzystając z zabezpieczeń transportu, uwierzytelnianie odbywa się za pośrednictwem tradycyjnych mechanizmów uwierzytelniania transportowego, takich jak schematy uwierzytelniania HTTP (podstawowe, szyfrowane, negocjowanie, zintegrowane uwierzytelnianie systemu Windows, uwierzytelnianie NTLM, brak i anonimowe).  
  
 Uwierzytelnianie może spowodować ustanowienie bezpiecznej sesji między komunikującymi się punktami końcowymi. Sesja jest identyfikowana przez identyfikator GUID, który jest okresem istnienia sesji zabezpieczeń. W poniższej tabeli przedstawiono informacje o zachowaniu i miejscu.  
  
|Dane|Storage|  
|----------|-------------|  
|Poświadczenia prezentacji, takie jak nazwa użytkownika, certyfikaty X. 509, tokeny protokołu Kerberos i odwołania do poświadczeń.|Standardowe mechanizmy zarządzania poświadczeniami systemu Windows, takie jak magazyn certyfikatów systemu Windows.|  
|Informacje o członkostwie użytkowników, takie jak nazwy użytkowników i hasła.|ASP.NET dostawcy członkostwa.|  
|Informacje o tożsamości dotyczące usługi używanej do uwierzytelniania usługi dla klientów.|Adres punktu końcowego usługi.|  
|Informacje o obiekcie wywołującym.|Dzienniki inspekcji.|  
  
## <a name="auditing"></a>Inspekcja  
 Inspekcja rejestruje sukces i niepowodzenie uwierzytelniania i zdarzeń autoryzacji. Rekordy inspekcji zawierają następujące dane: identyfikator URI usługi, identyfikator URI akcji i identyfikator obiektu wywołującego.  
  
 Inspekcja jest rejestrowana także wtedy, gdy administrator modyfikuje konfigurację rejestrowania komunikatów (Włączanie lub wyłączanie), ponieważ rejestrowanie komunikatów może rejestrować dane specyficzne dla aplikacji w nagłówkach i treściach. W przypadku systemu Windows XP rekord jest rejestrowany w dzienniku zdarzeń aplikacji. W systemach Windows Vista i Windows Server 2003 rekord jest rejestrowany w dzienniku zdarzeń zabezpieczeń.  
  
## <a name="transactions"></a>Transakcje  
 Funkcja transakcji zapewnia usługi transakcyjne w aplikacji WCF.  
  
 Nagłówki transakcji używane w propagacji transakcji mogą zawierać identyfikatory transakcji lub identyfikatory rejestracji, które są identyfikatorami GUID.  
  
 Funkcja transakcji używa programu Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (składnik systemu Windows) do zarządzania stanem transakcji. Domyślnie komunikacja między menedżerami transakcji jest zaszyfrowana. Menedżerowie transakcji mogą rejestrować odwołania punktów końcowych, identyfikatory transakcji i identyfikatory rejestracji w ramach ich trwałego stanu. Okres istnienia tego stanu zależy od okresu istnienia pliku dziennika Menedżera transakcji. Usługa MSDTC jest własnością i utrzymuje ten dziennik.  
  
 Funkcja transakcji implementuje standardy transakcji WS-koordynacyjnych i WS-AT.  
  
## <a name="reliable-sessions"></a>Niezawodne sesje  
 Niezawodne sesje w programie WCF zapewniają transfer komunikatów w przypadku wystąpienia niepowodzeń transportu lub pośrednika. Zapewniają one dokładnie jeden raz transfer komunikatów, nawet gdy podstawowy transport rozłącza się (na przykład połączenie TCP w sieci bezprzewodowej) lub utraci komunikat (serwer proxy HTTP porzuca komunikat wychodzący lub przychodzący). Niezawodne sesje również odnoszą się do zmiany kolejności komunikatów (mogą wystąpić w przypadku routingu wielościeżkowego), zachowując kolejność przesyłania komunikatów.  
  
 Niezawodne sesje są implementowane przy użyciu protokołu WS-ReliableMessaging (WS-RM). Dodają nagłówki WS-RM zawierające informacje o sesji, które służą do identyfikowania wszystkich komunikatów skojarzonych z określoną niezawodną sesją. Każda sesja WS-RM ma identyfikator, który jest identyfikatorem GUID.  
  
 Na komputerze użytkownika końcowego nie są przechowywane żadne informacje osobiste.  
  
## <a name="queued-channels"></a>Kanały w kolejce  
 Kolejki przechowują wiadomości z aplikacji wysyłającej w imieniu aplikacji odbiorczej, a następnie przesyłają je dalej do aplikacji odbiorczej. Mogą one pomóc w zapewnieniu przesyłania komunikatów wysyłanych do aplikacji, gdy na przykład aplikacja do odbioru jest przejściowa. Usługa WCF zapewnia obsługę kolejkowania przy użyciu usługi kolejkowania komunikatów (MSMQ) firmy Microsoft jako transportu.  
  
 Funkcja kanałów umieszczonych w kolejce nie dodaje nagłówków do wiadomości. Zamiast tego tworzy komunikat usługi kolejkowania komunikatów z odpowiednimi właściwościami komunikatów usługi kolejkowania komunikatów i wywołuje metody usługi kolejkowania komunikatów, aby umieścić komunikat w kolejce usługi kolejkowania komunikatów. Usługa kolejkowania komunikatów jest opcjonalnym składnikiem dostarczanym z systemem Windows.  
  
 Funkcja kanałów umieszczonych w kolejce nie zachowuje żadnych informacji na komputerze użytkownika końcowego, ponieważ używa usługi kolejkowania komunikatów jako infrastruktury kolejkowania.  
  
## <a name="com-integration"></a>Integracja modelu COM+  
 Ta funkcja otacza istniejące funkcje COM i COM+ w celu tworzenia usług zgodnych z usługami WCF. Ta funkcja nie korzysta z określonych nagłówków i nie przechowuje danych na komputerze użytkownika końcowego.  
  
## <a name="com-service-moniker"></a>Moniker usługi COM  
 Zapewnia to niezarządzaną otokę dla standardowego klienta WCF. Ta funkcja nie ma określonych nagłówków w sieci ani nie utrzymuje danych na komputerze.  
  
## <a name="peer-channel"></a>Kanał elementu równorzędnego  
 Kanał równorzędny umożliwia programowanie aplikacji wieloczęściowych przy użyciu programu WCF. Obsługa komunikatów wieloczęściowych odbywa się w kontekście siatki. Siatki są identyfikowane przez nazwę, którą mogą przyłączać węzły. Każdy węzeł w kanale równorzędnym tworzy odbiornik TCP na porcie określonym przez użytkownika i ustanawia połączenia z innymi węzłami w siatce w celu zapewnienia odporności. Aby nawiązać połączenie z innymi węzłami w sieci, węzły również wymieniają pewne dane, w tym adres odbiornika i adresy IP maszyny, z innymi węzłami w sieci. Komunikaty wysyłane w siatce mogą zawierać informacje o zabezpieczeniach, które odnoszą się do nadawcy, aby zapobiec fałszowaniu i manipulowaniu wiadomościami.  
  
 Na komputerze użytkownika końcowego nie są przechowywane żadne informacje osobiste.  
  
## <a name="it-professional-experience"></a>Specjalista IT  
  
### <a name="tracing"></a>Śledzenie  
 Funkcja diagnostyki infrastruktury WCF rejestruje komunikaty przekazywane przez warstwy transportu i modelu usług oraz działania i zdarzenia skojarzone z tymi komunikatami. Ta funkcja jest domyślnie wyłączona. Jest on włączony przy użyciu pliku konfiguracji aplikacji, a zachowanie śledzenia może być modyfikowane przy użyciu dostawcy WMI usługi WCF w czasie wykonywania. Po włączeniu infrastruktury śledzenia emituje śledzenie diagnostyczne zawierające komunikaty, działania i zdarzenia przetwarzania do skonfigurowanych odbiorników. Format i lokalizacja danych wyjściowych są określane przez opcje konfiguracji odbiorników administratora, ale zazwyczaj jest to plik w formacie XML. Administrator jest odpowiedzialny za ustawianie listy kontroli dostępu (ACL) dla plików śledzenia. W szczególności, gdy jest obsługiwany przez system aktywacji systemu Windows (WAS), administrator powinien upewnić się, że pliki nie są obsługiwane z publicznego wirtualnego katalogu głównego, jeśli nie jest to potrzebne.  
  
 Istnieją dwa typy śledzenia: rejestrowanie komunikatów i śledzenie diagnostyki modelu usług, opisane w następnej sekcji. Każdy typ jest konfigurowany przy użyciu własnego źródła śledzenia: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> i <xref:System.ServiceModel>. Oba te źródła śledzenia rejestrowania przechwytują dane, które są lokalne dla aplikacji.  
  
### <a name="message-logging"></a>Rejestrowanie komunikatów  
 Źródło śladu rejestrowania komunikatów (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umożliwia administratorowi zarejestrowanie komunikatów przesyłanych przez system. Za pomocą konfiguracji użytkownik może zdecydować się na zarejestrowanie całych komunikatów lub tylko nagłówków wiadomości, tylko to, czy należy rejestrować warstwy transportu i/lub modelu usług oraz czy mają być uwzględniane źle sformułowane komunikaty. Ponadto użytkownik może skonfigurować filtrowanie, aby ograniczyć liczbę rejestrowanych komunikatów.  
  
 Domyślnie rejestrowanie komunikatów jest wyłączone. Administrator komputera lokalnego może uniemożliwić administratorowi na poziomie aplikacji włączenie rejestrowania komunikatów.  
  
#### <a name="encrypted-and-decrypted-message-logging"></a>Rejestrowanie zaszyfrowanych i odszyfrowanych komunikatów  
 Komunikaty są rejestrowane, szyfrowane lub odszyfrowywane, zgodnie z opisem w poniższych warunkach.  
  
 Rejestrowanie transportu  
 Rejestruje komunikaty odebrane i wysłane na poziomie transportu. Te komunikaty zawierają wszystkie nagłówki i mogą być szyfrowane przed wysłaniem do sieci i w momencie odebrania.  
  
 Jeśli komunikaty są szyfrowane przed wysłaniem do sieci, a po ich odebraniu są one zaszyfrowane. Wyjątek polega na tym, że jest używany protokół zabezpieczeń (https): są one następnie rejestrowane przed wysłaniem i po odebraniu, nawet jeśli są szyfrowane w sieci.  
  
 Rejestrowanie usługi  
 Rejestruje komunikaty odebrane lub wysłane na poziomie modelu usługi, po przetworzeniu nagłówka kanału, tuż przed wprowadzeniem kodu użytkownika i po nim.  
  
 Komunikaty zarejestrowane na tym poziomie są odszyfrowywane, nawet jeśli zostały zabezpieczone i zaszyfrowane w sieci.  
  
 Źle sformułowane rejestrowanie komunikatów  
 Rejestruje komunikaty, które nie mogą zrozumieć lub przetworzyć Infrastruktura WCF.  
  
 Komunikaty są rejestrowane jako-is, czyli szyfrowane lub nie  
  
 Gdy wiadomości są rejestrowane w postaci odszyfrowanej lub niezaszyfrowanej, domyślnie program WCF usuwa klucze zabezpieczeń i potencjalnie dane osobowe z komunikatów przed ich zarejestrowaniem. W następnych sekcjach opisano, jakie informacje są usuwane i kiedy. Aby zmienić domyślne zachowanie kluczy dziennika i potencjalnie informacji osobistych, administrator maszyny i narzędzie wdrażania aplikacji muszą wykonać pewne czynności konfiguracyjne.  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a>Informacje usunięte z nagłówków komunikatów podczas rejestrowania odszyfrowanych/nieszyfrowanych wiadomości  
 Gdy wiadomości są rejestrowane w postaci odszyfrowanej/nieszyfrowanej, klucze zabezpieczeń i potencjalnie dane osobowe są domyślnie usuwane z nagłówków wiadomości i treści wiadomości przed ich zarejestrowaniem. Na poniższej liście przedstawiono, co usługa WCF traktuje klucze i potencjalnie dane osobowe.  
  
 Usunięte klucze:  
  
 \- dla xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"  
  
 wst:BinarySecret  
  
 wst: Entropia  
  
 \- dla xmlns: WSSE = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns: WSSE = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse: hasło  
  
 wsse: Identyfikator jednorazowy  
  
 Potencjalnie usunięte informacje osobiste:  
  
 \- dla xmlns: WSSE = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns: WSSE = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"  
  
 wsse: Nazwa użytkownika  
  
 wsse:BinarySecurityToken  
  
 \- dla xmlns: SAML = "urn: języka Oasis: names: TC: SAML: 1.0: Assertion" usunięto elementy pogrubione (poniżej):  
  
 Potwierdzenie \<  
  
 MajorVersion="1"  
  
 MinorVersion="1"  
  
 AssertionId="[ID]"  
  
 Issuer = "[ciąg]"  
  
 IssueInstant="[dateTime]"  
  
 >  
  
 Warunki \<NotBefore = "[dateTime]" NotOnOrAfter = "[dateTime]" >  
  
 \<element AudienceRestrictionCondition >  
  
 \<> odbiorców [URI]\</Audience > +  
  
 \</AudienceRestrictionCondition > *  
  
 \<DoNotCacheCondition/> *  
  
 <\!— abstrakcyjny typ podstawowy  
  
 \<warunek/> *  
  
 -->  
  
 \</Conditions >?  
  
 \<wskazówki >  
  
 \<Advice > [ID]\</AssertionIDReference > *  
  
 \<Assertion > [Assertion]\</Assertion > *  
  
 [any] *  
  
 \</Advice >?  
  
 <\!— abstrakcyjne typy podstawowe  
  
 \<instrukcja/> *  
  
 \<SubjectStatement >  
  
 \<podmiot >  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 \<SubjectConfirmation >  
  
 \<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +  
  
 \<danych SubjectConfirmationData > [any]\</SubjectConfirmationData >?  
  
 \<DS: KeyInfo >...\</DS: KeyInfo >?  
  
 \</SubjectConfirmation >?  
  
 \</subject >  
  
 \</SubjectStatement > *  
  
 -->  
  
 \<AuthenticationStatement  
  
 Wartość uwierzytelniania = "[URI]"  
  
 AuthenticationInstant="[dateTime]"  
  
 >  
  
 Dawane  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <AuthorityBinding  
  
 AuthorityKind="[QName]"  
  
 Location = "[URI]"  
  
 Binding="[uri]"  
  
 />*  
  
 \</AuthenticationStatement > *  
  
 \<AttributeStatement >  
  
 Dawane  
  
 Atrybut \<  
  
 AttributeName="[string]"  
  
 AttributeNamespace="[uri]"  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 \</Attribute > +  
  
 \</AttributeStatement > *  
  
 \<AuthorizationDecisionStatement  
  
 Resource="[uri]"  
  
 Decision="[Permit&#124;Deny&#124;Indeterminate]"  
  
 >  
  
 Dawane  
  
 \<akcji namespace = "[URI]" > [ciąg]\</Action > +  
  
 \<dowód >  
  
 \<Advice > [ID]\</AssertionIDReference > +  
  
 \<Assertion > [Assertion]\</Assertion > +  
  
 \</Evidence >?  
  
 \</AuthorizationDecisionStatement > *  
  
 \</Assertion >  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a>Informacje usunięte z treści komunikatów podczas rejestrowania odszyfrowanych/nieszyfrowanych wiadomości  
 Jak opisano wcześniej, usługa WCF usuwa klucze i znane potencjalnie dane osobowe z nagłówków komunikatów dla rejestrowanych, odszyfrowanych/nieszyfrowanych wiadomości. Ponadto WCF usuwa klucze i znane potencjalnie dane osobowe z treści wiadomości dla elementów treści i działań na poniższej liście, które opisują komunikaty zabezpieczeń związane z wymianą kluczy.  
  
 Dla następujących przestrzeni nazw:  
  
 xmlns: wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns: wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (na przykład jeśli żadna akcja nie jest dostępna)  
  
 Informacje są usuwane dla tych elementów treści, które obejmują wymianę kluczy:  
  
 wst:RequestSecurityToken  
  
 wst:RequestSecurityTokenResponse  
  
 wst:RequestSecurityTokenResponseCollection  
  
 Informacje są również usuwane dla każdej z następujących akcji:  
  
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
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a>Żadne informacje nie są usuwane z nagłówków i danych treści specyficznych dla aplikacji  
 Funkcja WCF nie śledzi informacji osobistych w nagłówkach specyficznych dla aplikacji (na przykład ciągi zapytań) ani danych treści (na przykład numeru karty kredytowej).  
  
 Po włączeniu rejestrowania komunikatów informacje osobiste w nagłówkach i informacjach o treściach specyficznych dla aplikacji mogą być widoczne w dziennikach. Ponownie program wdrażania aplikacji jest odpowiedzialny za ustawianie list kontroli dostępu w plikach konfiguracji i dziennika. Mogą oni również wyłączyć rejestrowanie, jeśli nie chcą, aby te informacje były widoczne, lub odfiltrować te informacje z plików dziennika po ich zarejestrowaniu.  
  
### <a name="service-model-tracing"></a>Śledzenie modelu usług  
 Źródło śledzenia modelu usług (<xref:System.ServiceModel>) umożliwia śledzenie działań i zdarzeń związanych z przetwarzaniem komunikatów. Ta funkcja używa funkcji diagnostyki .NET Framework z <xref:System.Diagnostics>. Podobnie jak w przypadku właściwości <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> lokalizacja i jej lista ACL są konfigurowane przez użytkownika przy użyciu plików konfiguracji aplikacji .NET Framework. Podobnie jak w przypadku rejestrowania komunikatów, lokalizacja pliku jest zawsze konfigurowana, gdy administrator włączy śledzenie; w tym celu administrator kontroluje listę ACL.  
  
 Ślady zawierają nagłówki wiadomości, gdy komunikat jest w zakresie. Te same reguły ukrywania potencjalnie osobistych informacji w nagłówkach wiadomości w poprzedniej sekcji dotyczą: informacje osobiste zidentyfikowane wcześniej są usuwane domyślnie z nagłówków śledzenia. Zarówno administrator komputera, jak i narzędzie wdrażania aplikacji muszą zmodyfikować konfigurację, aby rejestrować potencjalnie dane osobowe. Jednak dane osobowe zawarte w nagłówkach specyficznych dla aplikacji są rejestrowane w śladach. Narzędzie wdrażania aplikacji jest odpowiedzialne za ustawianie list kontroli dostępu dla plików konfiguracji i śledzenia. Mogą również wyłączyć śledzenie, aby ukryć te informacje lub odfiltrować te informacje z plików śledzenia po ich zarejestrowaniu.  
  
 W ramach śledzenia ServiceModel, unikatowe identyfikatory (nazywane identyfikatorami aktywności i zazwyczaj identyfikator GUID) łączą różne działania wraz z przepływem komunikatów przez różne części infrastruktury.  
  
#### <a name="custom-trace-listeners"></a>Niestandardowa odbiorniki śledzenia  
 W przypadku rejestrowania i śledzenia komunikatów można skonfigurować odbiornik niestandardowego śledzenia, który może wysyłać ślady i komunikaty w sieci (na przykład do zdalnej bazy danych). Narzędzie wdrażania aplikacji jest odpowiedzialne za konfigurowanie odbiorników niestandardowych lub umożliwienie użytkownikom wykonania tej czynności. Są one również odpowiedzialne za wszystkie dane osobowe ujawniane w lokalizacji zdalnej oraz odpowiednie stosowanie list ACL do tej lokalizacji.  
  
### <a name="other-features-for-it-professionals"></a>Inne funkcje dla specjalistów IT  
 Program WCF ma dostawcę WMI, który uwidacznia informacje o konfiguracji infrastruktury WCF za pomocą usługi WMI (dostarczanej z systemem Windows). Domyślnie interfejs usługi WMI jest dostępny dla administratorów.  
  
 Konfiguracja usługi WCF używa mechanizmu konfiguracji .NET Framework. Pliki konfiguracji są przechowywane na komputerze. Deweloper aplikacji i administrator tworzą pliki konfiguracji i listę ACL dla każdej z wymagań aplikacji. Plik konfiguracji może zawierać adresy punktów końcowych i linki do certyfikatów w magazynie certyfikatów. Certyfikaty mogą służyć do dostarczania danych aplikacji w celu skonfigurowania różnych właściwości funkcji używanych przez aplikację.  
  
 Funkcja WCF używa również funkcji zrzutów procesów .NET Framework, wywołując metodę <xref:System.Environment.FailFast%2A>.  
  
### <a name="it-pro-tools"></a>Narzędzia Pro IT  
 Usługa WCF udostępnia również następujące narzędzia profesjonalne, które są dostarczane w Windows SDK.  
  
#### <a name="svctraceviewerexe"></a>SvcTraceViewer.exe  
 W podglądzie są wyświetlane pliki śledzenia WCF. Podgląd pokazuje, jakie informacje są zawarte w śladach.  
  
#### <a name="svcconfigeditorexe"></a>SvcConfigEditor.exe  
 Edytor umożliwia użytkownikowi tworzenie i edytowanie plików konfiguracji WCF. Edytor pokazuje, jakie informacje są zawarte w plikach konfiguracji. To samo zadanie można wykonać za pomocą edytora tekstu.  
  
#### <a name="servicemodel_reg"></a>ServiceModel_Reg  
 To narzędzie umożliwia użytkownikowi zarządzanie instalacjami ServiceModel na komputerze. Narzędzie wyświetla komunikaty o stanie w oknie konsoli, gdy jest ono uruchomione, a w procesie może wyświetlać informacje o konfiguracji instalacji programu WCF.  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a>WSATConfig. exe i WSATUI. dll  
 Te narzędzia umożliwiają specjalistom IT skonfigurowanie międzyoperacyjnego obsługi sieci WS-AtomicTransaction w programie WCF. Narzędzia wyświetlają i umożliwiają użytkownikowi zmianę wartości najczęściej używanych ustawień protokołu WS-AtomicTransaction przechowywanych w rejestrze.  
  
## <a name="cross-cutting-features"></a>Funkcje wycinania krzyżowego  
 Następujące funkcje są krzyżowe. Oznacza to, że mogą one składać się z dowolnej z powyższych funkcji.  
  
### <a name="service-framework"></a>Struktura usługi  
 Nagłówki mogą zawierać identyfikator wystąpienia, który jest identyfikatorem GUID, który kojarzy komunikat z wystąpieniem klasy CLR.  
  
 Web Services Description Language (WSDL) zawiera definicję portu. Każdy port ma adres punktu końcowego i powiązanie, które reprezentuje usługi używane przez aplikację. Uwidacznianie WSDL można wyłączyć za pomocą konfiguracji. Na maszynie nie są przechowywane żadne informacje.  
  
## <a name="see-also"></a>Zobacz też

- [Windows Communication Foundation](index.md)
- [Bezpieczeństwo](./feature-details/security.md)
