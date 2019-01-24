---
title: Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
ms.openlocfilehash: 1f9881cd1a63e00aaf414f93c91885e57ea0b145
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540571"
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości
Autoryzacja to proces określania jednostek, które ma uprawnienia do zmiany, wyświetlania lub inny sposób uzyskać dostęp do zasobów komputera. Na przykład w biznesie, tylko menedżerowie może mieć możliwość dostępu do plików pracownikom. Windows Communication Foundation (WCF) obsługuje dwa mechanizmy do wykonywania operacji przetwarzania autoryzacji. Pierwszy mechanizm umożliwia sterowanie autoryzację przy użyciu istniejących typowych konstrukcji języka wspólnego (CLR). Drugim jest znany jako modelu opartego na oświadczeniach *modelu tożsamości*. Usługi WCF używa modelu tożsamości w celu utworzenia oświadczeń z wiadomości przychodzące; Klasy modelu tożsamości można rozszerzyć do obsługi nowych typów oświadczeń autoryzacji niestandardowych schematów. Ten temat zawiera omówienie główne pojęcia dotyczące programowania funkcji modelu tożsamości, a także listy najważniejszych klas, które korzysta z tej funkcji.  
  
## <a name="identity-model-scenarios"></a>Scenariusze modelu tożsamości  
 Następujące scenariusze reprezentują Użyj modelu tożsamości.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Scenariusz 1: Obsługa tożsamości, roli i oświadczenia grupy  
 Użytkownicy wysyłają komunikaty do usługi sieci Web. Wymagania dotyczące kontroli dostępu do usługi sieci Web, użyj tożsamości, ról lub grup. Nadawca wiadomości jest mapowany do zestawu ról lub grup. Informacje o roli lub grupy służy do wykonywania kontroli dostępu.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Scenariusz 2: Obsługa oświadczeń rozbudowane  
 Użytkownicy wysyłają komunikaty do usługi sieci Web. Wymagania dotyczące kontroli dostępu do usługi sieci Web wymagają bardziej rozbudowane modelu niż tożsamości, ról lub grup. Usługa sieci Web określa, czy dany użytkownik ma dostęp do określonego zasobu chronionego za pomocą zaawansowanych modelu opartego na oświadczeniach. Na przykład jeden użytkownik może mieć do określonych informacji, takie jak informacje wynagrodzenie, które inni użytkownicy nie mają dostępu do odczytu.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Scenariusz 3: Mapowania różnych oświadczeń  
 Użytkownik wysyła komunikat do usługi sieci Web. Użytkownik może określić poświadczeń na wiele różnych sposobów: Certyfikat X.509, token nazwy użytkownika lub tokenu protokołu Kerberos. Usługa sieci Web jest wymagane do wykonywania testów kontroli dostępu w taki sam sposób niezależnie od typu poświadczeń użytkownika. Jeśli poświadczenia dodatkowe typy są obsługiwane wraz z upływem czasu, system powinien się rozwijać, odpowiednio.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Scenariusz 4: Określanie dostęp do wielu zasobów  
 Usługa sieci Web próbuje uzyskać dostęp do wielu zasobów. Usługa Określa, w których chronionych zasobów, dany użytkownik ma dostęp do przez porównywanie oświadczeń skojarzonych z użytkownikiem z oświadczenia wymagane do uzyskania dostępu do zasobu.  
  
## <a name="identity-model-terms"></a>Warunki modelu tożsamości  
 Poniższa lista zdefiniowano kluczowe terminy używane do opisywania pojęcia modelu tożsamości.  
  
 Zasady autoryzacji  
 Zestaw zasad mapowania zestawu wejściowego oświadczenia do zestawu oświadczeń wyjściowych. Sprawdzanie wyników zasad autoryzacji w zestawie oświadczeń dodawane do kontekstu oceny, a następnie kontekst autoryzacji.  
  
 Kontekst autoryzacji  
 Zbiór zestawów oświadczeń i zero lub więcej właściwości. Wynik obliczania wartości co najmniej jedne zasady autoryzacji.  
  
 Oświadczenie  
 Połączenie typu oświadczenia, prawo i wartość.  
  
 Zestaw oświadczeń  
 Zestaw oświadczeń wystawione przez określonego wystawcę.  
  
 Typ oświadczenia  
 Typ oświadczenia. Zdefiniowane przez interfejs API modelu tożsamości oświadczeń są właściwościami <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> klasy. Przykłady typów oświadczeń dostarczane przez system <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.System%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A>, i <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A>.  
  
 Kontekst oceny  
 Kontekst, w którym jest oceniana zasady autoryzacji. Zawiera zestawy właściwości i oświadczeń. Po zakończeniu oceny, staje się podstawą kontekst autoryzacji.  
  
 Oświadczenie tożsamości  
 Oświadczenie, w której po prawej stronie jest tożsamością.  
  
 Wystawcy  
 Zestaw oświadczeń, który zawiera co najmniej jedno oświadczenie tożsamości i uznaje się w celu wystawienia innego zestawu oświadczeń.  
  
 Właściwości  
 Zestaw informacje związane z kontekstu oceny lub kontekst autoryzacji.  
  
 Zasobu chronionego  
 Coś, co w systemie, którego można używać tylko, dostęp do lub zmieniane w przeciwnym razie, jeśli najpierw spełnienie niektórych wymagań.  
  
 Prawe  
 Możliwość wobec zasobu. Prawa zdefiniowane przez interfejs API modelu tożsamości są właściwościami <xref:System.IdentityModel.Claims.Rights> klasy. Przykłady praw dostarczane przez system <xref:System.IdentityModel.Claims.Rights.Identity%2A> i <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
 Wartość  
 Coś, nad którym dochodzi się po prawej stronie.  
  
## <a name="claims"></a>oświadczenia  
 Model tożsamości jest systemu opartego na oświadczeniach. Oświadczenia opis możliwości skojarzone z niektórych jednostek w systemie, często użytkownika tego systemu. Zestaw oświadczeń skojarzone z danej jednostki można traktować jako klucz. Konkretne oświadczenia, które definiują kształtu tego klucza, podobnie jak fizyczny klucz używany do otwierania blokady w drzwi. Oświadczenia są używane do uzyskania dostępu do zasobów. Dostęp do chronionego zasobu jest określany przez porównywanie oświadczeń, na potrzeby dostępu do tego zasobu przy użyciu oświadczeń skojarzone z próby dostępu do jednostki.  
  
 Oświadczenie to wyrażenie prawej w odniesieniu do określonej wartości. Po prawej stronie można mieć "Odczyt", "Write" lub "Execute". Wartość może być bazy danych, plików, skrzynki pocztowej lub właściwość. Oświadczenia również mieć typ oświadczenia. Połączenie typu oświadczenia i po prawej stronie udostępnia mechanizm do określania możliwości w odniesieniu do wartości. Na przykład oświadczenia typu "File" od prawej "Odczyt" na wartość "Biography.doc" oznacza, że jednostki, z którym takie oświadczenia jest skojarzona ma dostęp do odczytu do pliku Biography.doc. Oświadczenie typu "Name", z prawej "PossessProperty" na wartość "Martin" wskazuje, że jednostki, z którym takie oświadczenia jest skojarzona posiada właściwość nazwa z wartością "Martin".  
  
 Mimo że różnych typów oświadczeń i prawa są zdefiniowane jako część modelu tożsamości, system jest rozszerzalny, co różnych systemów, tworzenie na podstawie infrastruktury modelu tożsamości, aby zdefiniować dodatkowe oświadczenia i prawa zgodnie z potrzebami.  
  
### <a name="identity-claims"></a>Oświadczenia tożsamości  
 Jest jedną prawo określonej tożsamości. Oświadczenia, które posiadają to uprawnienie należy instrukcji dotyczących tożsamości podmiotu. Na przykład oświadczenia typu "główna nazwa użytkownika" (UPN) o wartości "someone@example.com" i po prawej stronie tożsamości wskazuje określonej tożsamości w określonej domenie.  
  
#### <a name="system-identity-claim"></a>Oświadczenie tożsamości systemu  
 Model tożsamości definiuje jedno oświadczenie tożsamości: System. Oświadczenia tożsamości systemu wskazuje, czy jednostka jest bieżącej aplikacji lub systemu.  
  
### <a name="sets-of-claims"></a>Zestawy oświadczeń  
 Model oświadczeń, które reprezentują tożsamość jest ważne, ponieważ są zawsze wydawane oświadczenia przez niektóre jednostki w systemie, nawet w przypadku tej jednostki ostatecznie niektóre pojęcia "self". Oświadczenia są grupowane według stawki ustalonej i każdy zestaw ma wystawcę. Wystawca jest po prostu zestaw oświadczeń. Ostatecznie kończyć relacji cyklicznej i dowolny oświadczeń zestawu może być własną wystawcy.  
  
 Poniższa ilustracja przedstawia przykład trzech zestawów oświadczeń, gdzie jeden zestaw oświadczeń zawiera, jako jego wystawcę inny zestaw oświadczeń, tożsamości, która z kolei ma System zestawu jako jego wystawca oświadczeń. W związku z tym zestawy oświadczeń tworzą hierarchię, które mogą być arbitralnie głębokie.  
  
 ![Zarządzanie oświadczeniami i autoryzacją](../../../../docs/framework/wcf/feature-details/media/claimshierarchy.gif "claimshierarchy")  
  
 Wiele zestawów oświadczeń mogą mieć tego samego wydawania oświadczeń w zestawie, jak pokazano na poniższej ilustracji.  
  
 ![Zarządzanie oświadczeniami i autoryzacją](../../../../docs/framework/wcf/feature-details/media/multiplesetsofclaims.gif "multiplesetsofclaims")  
  
 Z wyjątkiem będącego wystawcy swój własny zestaw oświadczeń modelu tożsamości nie zapewnia pomocy technicznej dla zestawów oświadczeń w celu utworzenia pętli. Ten sposób sytuacji, w którym zestaw oświadczeń A jest wystawiany przez zestaw oświadczeń B, która sama wystawiony przez zestaw oświadczeń A, nigdy nie mogą wystąpić. Ponadto modelu tożsamości nie świadczenia pomocy technicznej dla zestawów oświadczeń mieć wielu wystawców. Jeśli co najmniej dwóch wystawców należy wygenerować danego zestawu oświadczeń, następnie należy użyć wielu zestawów oświadczeń, każdy zawierającym oświadczenia ten sam, ale o różnych wydawców.  
  
### <a name="the-origin-of-claims"></a>Pochodzenie oświadczeń  
 Oświadczenia mogą pochodzić z różnych źródeł. Jedno źródło typowych oświadczeń jest poświadczenia przedstawione przez użytkownika, na przykład jako część komunikat wysłany do usługi sieci Web. System sprawdza poprawność roszczeniami i staną się częścią zestawu oświadczeń skojarzonych z użytkownikiem. Inne składniki systemu mogą być również źródeł roszczenia, w tym między innymi systemu operacyjnego, stos sieci, środowisko wykonawcze lub aplikacji. Ponadto usługi zdalnej, również może być źródłem oświadczeń.  
  
### <a name="authorization-policies"></a>Zasady autoryzacji  
 W modelu tożsamości oświadczeń są generowane jako część procesu oceny zasad autoryzacji. Zasady autoryzacji sprawdza (prawdopodobnie pusta) zestaw istniejących oświadczeń i może wybrać dodać dodatkowe oświadczenia na podstawie już występuje na oświadczeniach i dodatkowe informacje w swojej dyspozycji. Zapewnia to podstawę mapowanie między oświadczeń. Obecność lub brak oświadczeń w systemie ma wpływ na zachowanie zasady autoryzacji w odniesieniu do tego, czy dodaje dodatkowe oświadczenia.  
  
 Na przykład zasady autoryzacji ma dostęp do bazy danych, która obejmuje dat urodzin różnych jednostek przy użyciu systemu. Zasady autoryzacji używa tych informacji, aby dodać oświadczenie "Over18" do kontekstu. Należy zwrócić uwagę na to oświadczenie Over18 nie ujawnia żadnych informacji o jednostce, poza tym, że jest ona ponad 18 lat. Należy pamiętać, że interpretacja oświadczenia "Over18" zależy od zrozumienie semantyka tego oświadczenia. Zasady autoryzacji, który dodaje oświadczenie rozumie tych semantyki w pewien poziom. Kod, który następnie sprawdza, czy oświadczenia, które są wynikiem oceny zasad być powiadamiane o tych semantyki.  
  
 Zasady autoryzacji danego może wymagać, że jej obliczony wielokrotnie ponieważ jak inne zasady autoryzacji dodawać oświadczenia, że zasady autoryzacji dodać jeszcze więcej oświadczeń. Model tożsamości jest przystosowana do kontynuowania oceny, dopóki nie więcej oświadczenia są dodawane do kontekstu przez dowolne zasady autoryzacji w życie. Ta ciągła ocena zasad autoryzacji zapobiega konieczności wymuszanie w dowolnej kolejności określonej wersji ewaluacyjnej, w odniesieniu do zasady autoryzacji; one może zostać oceniony w dowolnej kolejności. Na przykład jeśli zasady X dodaje oświadczenie Z tylko, jeśli zasady A dodał B oświadczenia, następnie jeśli X jest stosowana jako pierwsza, początkowo nie dodaje Z oświadczeń. Później A jest obliczane i dodaje oświadczenie B. X jest następnie oceniany po raz drugi i tym razem dodaje oświadczenie Z.  
  
 Dany system może mieć wiele zasad autoryzacji w życie.  
  
### <a name="a-key-making-machine"></a>Maszyny wprowadzania klucza  
 Ocenianie grupy zasad autoryzacji skojarzone przypomina przy użyciu komputera, który sprawia, że klucze. Zasady autoryzacji są oceniane w każdej, i zestawy oświadczeń są generowane, budowanie kształt klucza. Po ukończeniu kształt klucza może służyć do próby otwarcia niektórych blokad. Kształt klucz jest przechowywany w "kontekst autoryzacji," który jest tworzony przez Menedżera autoryzacji.  
  
### <a name="authorization-context"></a>Kontekst autoryzacji  
 Menedżer autoryzacji ocenia się różne zasady autoryzacji, zgodnie z opisem, a wynik jest kontekst autoryzacji (zbiór zestawów oświadczeń i niektóre właściwości). Aby ustalić, jakie oświadczenia są obecne w tym kontekście, relacje między tymi różnych oświadczeń (na przykład wystawiającego zestawu oświadczeń), a ostatecznie porównać ich pewne wymagania, które muszą spełniać dostęp do można zbadać kontekst autoryzacji zasób.  
  
### <a name="locks"></a>Blokady  
 Jeśli kontekst autoryzacji (zestaw oświadczeń) jest klucz, wymagania, które muszą zostać spełnione, aby udzielić dostępu do określonego zasobu chronionego stanowią blokadę, która klucza muszą być zgodne. Model tożsamości nie formalnego, jak te wymagania są wyrażone, ale ze względu na charakter oparta na oświadczeniach systemu, obejmują, porównywanie oświadczeń w kontekście autoryzacji dla niektórych zbiór wymagane oświadczenia.  
  
### <a name="a-recap"></a>Podsumowanie  
 Model tożsamości opiera się wokół koncepcji oświadczeń. Oświadczenia są pogrupowane w zestawy, a następnie agregowane w kontekście autoryzacji. Kontekst autoryzacji zawiera zestaw oświadczeń i wynik obliczania wartości co najmniej jedne zasady autoryzacji skojarzone z Menedżera autoryzacji. Te oświadczenia, że zestawy mogą być sprawdzane w celu określenia, jeśli zostały spełnione wymagania dotyczące dostępu. Na poniższej ilustracji przedstawiono relacje między te różne pojęcia modelu tożsamości.  
  
 ![Zarządzanie oświadczeniami i autoryzacją](../../../../docs/framework/wcf/feature-details/media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>Program WCF i modelu tożsamości  
 Usługi WCF infrastruktury modelu tożsamości jest używany jako podstawa do wykonywania autoryzacji. W programie WCF <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasa służy do określania *autoryzacji* zasad jako część usługi. Takie zasady autoryzacji, są znane jako *zasady autoryzacji dla zewnętrznych*, a użytkownicy mogą wykonywać przetwarzania oświadczenia na podstawie zasad lokalnych lub przez interakcję z usługą zdalną. Menedżer autoryzacji, reprezentowane przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasy ocenia zasady autoryzacji dla zewnętrznych wraz z zasady autoryzacji, które rozpoznają poświadczeń różnych typów (tokeny) i wypełnia, co jest nazywane  *kontekst autoryzacji* roszczeń odpowiednie dla wiadomości przychodzących. Kontekst autoryzacji jest reprezentowany przez <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.  
  
## <a name="identity-model-programming"></a>Tożsamość modelu programowania  
 W poniższej tabeli opisano model obiektów, używane do rozszerzenia modelu tożsamości programów. Wszystkie te klasy istnieje albo <xref:System.IdentityModel.Policy> lub <xref:System.IdentityModel.Claims> przestrzeni nazw.  
  
|Class|Opis|  
|-----------|-----------------|  
|Składnik autoryzacji|Klasa modelu tożsamości, która implementuje <xref:System.IdentityModel.Policy.IAuthorizationComponent> interfejsu.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Interfejs, który udostępnia właściwości pojedynczy ciąg tylko do odczytu: Id. Wartość tej właściwości jest unikatowy dla każdego wystąpienia w systemie, który implementuje ten interfejs.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|*Składnika autoryzacji* zawierający zestaw `ClaimSet` wystąpień z zero lub więcej właściwości; wynik obliczania wartości co najmniej jedne zasady autoryzacji.|  
|<xref:System.IdentityModel.Claims.Claim>|Połączenie typu oświadczenia i wartość. Elementy po prawej stronie i wartości są ograniczone przez typ oświadczenia.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Abstrakcyjna klasa bazowa. Kolekcja `Claim` wystąpień.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Klasa zapieczętowana. Implementacja `ClaimSet` klasy.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Abstrakcyjna klasa bazowa. Przekazane w zasadach autoryzacji podczas oceny zasad.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Interfejs jest pochodną `IAuthorizationComponent` i implementowane przez klasy zasad autoryzacji.|  
|<xref:System.IdentityModel.Claims.Rights>|Klasa statyczna, która zawiera wstępnie zdefiniowane odpowiednie wartości.|  
  
 Następujące klasy są również używane dla tożsamości modelu programowania, ale nie znajdują się w <xref:System.IdentityModel.Policy> lub <xref:System.IdentityModel.Claims> przestrzeni nazw.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Klasa, która udostępnia metodę — <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>— do wykonania na podstawie oświadczeń autoryzacji sprawdza, czy dla każdej operacji w usłudze. Musi pochodzić od klasy i zastąpić metodę.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Klasy zapieczętowanej zapewnia różne właściwości związane z zachowaniem, usługi w odniesieniu do autoryzacji.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Klasa, która dostarcza kontekst zabezpieczeń, łącznie z kontekstem autoryzacji, aktualnie uruchomione (lub jest uruchomiony) operacji. Wystąpienie tej klasy jest częścią <xref:System.ServiceModel.OperationContext>.|  
  
### <a name="significant-members"></a>Istotne elementy członkowskie  
 Następujące elementy członkowskie są często używane do tworzenia nowych typów oświadczeń.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Klasy pochodne zaimplementować tę metodę w celu sprawdzania dostępu oparta na oświadczeniach przed uruchomieniem operacji w usłudze. Wszystkie informacje w podanym <xref:System.ServiceModel.OperationContext>, lub w innym miejscu, można zbadać podczas wprowadzania dostępu, sprawdź decyzji. Jeśli <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> zwraca `true`, a następnie dostęp jest udzielany i operacja może być uruchomiona. Jeśli `CheckAccessCore` zwraca `false`, a następnie odmowa dostępu i nie można uruchomić operację. Aby uzyskać przykład, zobacz [jak: Tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Zwraca <xref:System.ServiceModel.ServiceAuthorizationManager> dla usługi. <xref:System.ServiceModel.ServiceAuthorizationManager> Jest odpowiedzialny za podejmowania decyzji dotyczących autoryzacji.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Kolekcja zasad autoryzacji niestandardowej, określony dla usługi. Te zasady są oceniane oprócz tych zasad skojarzonych z poświadczenia usługi w przychodzących wiadomości.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Policy.EvaluationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationComponent>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims>
- <xref:System.IdentityModel.Policy>
- <xref:System.IdentityModel.Tokens>
- <xref:System.IdentityModel.Selectors>
- [Oświadczenia i tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Oświadczenia i odmawianie dostępu do zasobów](../../../../docs/framework/wcf/feature-details/claims-and-denying-access-to-resources.md)
- [Tworzenie oświadczenia i wartości zasobów](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Instrukcje: Tworzenie oświadczenia niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
- [Instrukcje: Porównywanie oświadczeń](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)
- [Instrukcje: Tworzenie niestandardowych zasad autoryzacji](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-policy.md)
- [Instrukcje: Tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
