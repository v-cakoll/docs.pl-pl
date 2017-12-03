---
title: "Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b69c17b9fcb14bbd70b60c32965fb1163c22e765
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości
Autoryzacja jest proces określania, które mają uprawnienia do zmiany, Wyświetl lub dostęp do zasobu komputera, w przeciwnym razie. Na przykład w firmie, tylko menedżerowie mogą dozwolony dostęp do plików pracownikom. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]obsługuje dwa mechanizmy do wykonywania przetwarzania autoryzacji. Pierwszy mechanizm umożliwia sterowanie autoryzacji przy użyciu istniejących typowych konstrukcji języka wspólnego (CLR). Drugim jest znany jako modelu opartego na oświadczeniach *modelu tożsamości*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa modelu tożsamości można utworzyć oświadczenia na podstawie wiadomości przychodzących. Obsługuje nowe typy oświadczeń autoryzacji niestandardowej schematów można rozszerzyć klasy modelu tożsamości. Ten temat zawiera omówienie główne pojęcia dotyczące programowania funkcji modelu tożsamości, a także listę najważniejszych klas, które korzysta z funkcji.  
  
## <a name="identity-model-scenarios"></a>Scenariusze modelu tożsamości  
 Następujące scenariusze reprezentują Użyj modelu tożsamości.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Scenariusz 1: Obsługa tożsamości, roli i oświadczenia grupy  
 Użytkownicy wysyłać wiadomości do usługi sieci Web. Wymagania dotyczące kontroli dostępu usługi sieci Web, użyj tożsamości, role lub grupy. Nadawca komunikatu jest mapowany do zestawu ról lub grup. Informacje o roli lub grupy służy do wykonywania kontroli dostępu.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Scenariusz 2: Obsługa oświadczeń RTF  
 Użytkownicy wysyłać wiadomości do usługi sieci Web. Wymagania dotyczące kontroli dostępu do usługi sieci Web wymagają bardziej rozbudowane modelu niż tożsamości, role lub grupy. Usługa sieci Web określa, czy dany użytkownik ma dostęp do określonego zasobu chronionego za pomocą zaawansowanych modelu opartego na oświadczeniach. Na przykład jeden użytkownik możliwość szczegółowych informacji, takie jak informacje wynagrodzenie, które inni użytkownicy nie mają dostępu do odczytu.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Scenariusz 3: Mapowania różnych oświadczeń  
 Użytkownik wysyła komunikat do usługi sieci Web. Użytkownik może określić swoje poświadczenia na kilka różnych sposobów: certyfikat X.509, token nazwy użytkownika lub token protokołu Kerberos. Usługa sieci Web jest wymagane do przeprowadzenia testów kontroli dostępu w taki sam sposób, bez względu na typ poświadczeń użytkownika. Jeśli poświadczenia dodatkowe typy są obsługiwane w czasie, system należy odpowiednio rozwijać.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Scenariusz 4: Określanie dostęp do wielu zasobów  
 Usługi sieci Web próbuje uzyskać dostęp do wielu zasobów. Usługi określa, które zasoby chronione dany użytkownik ma dostęp do porównując oświadczeń skojarzonych z użytkownikiem z oświadczeniami wymagane dostępu do zasobu.  
  
## <a name="identity-model-terms"></a>Warunki modelu tożsamości  
 Poniższa lista definiuje kluczowe terminy opisuje pojęcia modelu tożsamości.  
  
 Zasady autoryzacji  
 Zestaw reguł do mapowania na zestaw oświadczeń wejściowych do zestawu oświadczeń wyjściowych. Ocena wyników zasad autoryzacji w oświadczeń ustawia dodawany do kontekstu wyznaczania wartości, a następnie kontekst autoryzacji.  
  
 Kontekst autoryzacji  
 Zbiór zestawów oświadczeń i właściwości zero lub więcej. Wynik oceny co najmniej jedne zasady autoryzacji.  
  
 Oświadczenie  
 Kombinacja typu oświadczenia, prawo, i wartość.  
  
 Zestaw oświadczeń  
 Zestaw oświadczeń wystawione przez konkretnego wystawcy.  
  
 Typ oświadczenia  
 Rodzaj oświadczeń. Właściwości są określone przez interfejs API modelu tożsamości oświadczeń <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> klasy. Przykłady typów oświadczeń dostarczane przez system <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.System%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A>, i <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A>.  
  
 kontekst oceny  
 Kontekst, w jakiej są oceniane zasad autoryzacji. Zawiera zestawy właściwości i oświadczeń. Po zakończeniu oceny staje się podstawę kontekst autoryzacji.  
  
 Oświadczenie tożsamości  
 Oświadczenie tożsamości jest których prawo.  
  
 Wystawcy  
 Zestaw oświadczeń, który zawiera co najmniej jedno oświadczenie tożsamości i jest uznawany za wystawiły inny zestaw oświadczeń.  
  
 Właściwości  
 Zestaw informacje związane z kontekstu wyznaczania lub kontekst autoryzacji.  
  
 Zasobu chronionego  
 Coś w systemie, którego można używać tylko, dostęp do lub manipulować w przeciwnym razie, jeśli najpierw są spełnione pewne wymagania.  
  
 Prawe  
 Możliwość przez zasób. Prawa zdefiniowane przez interfejs API modelu tożsamości są właściwości <xref:System.IdentityModel.Claims.Rights> klasy. Przykładami praw dostarczane przez system są <xref:System.IdentityModel.Claims.Rights.Identity%2A> i <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
 Wartość  
 Coś, w którym jest określona prawo.  
  
## <a name="claims"></a>Oświadczenia  
 Modelu tożsamości jest systemem opartego na oświadczeniach. Oświadczenia opisano możliwości skojarzone z jednostką niektórych w systemie, często użytkownika tego systemu. Zestaw oświadczeń skojarzone z daną jednostkę można traktować jako klucz. Konkretne oświadczenia, które definiują kształtu tego klucza, podobnie jak fizyczny klucz użyty do otwarcia blokady w drzwi. Oświadczenia są używane do uzyskania dostępu do zasobów. Dostęp do chronionego zasobu jest określana przez porównywanie oświadczeń musiał uzyskać dostęp z oświadczeń skojarzone z próby dostępu do jednostki tego zasobu.  
  
 Oświadczenia jest wyrażeniem prawa w odniesieniu do określonej wartości. Prawo może to wyglądać jak "Odczytu", "Write" lub "Execute". Wartość może być bazy danych, plików, skrzynki pocztowej lub właściwości. Oświadczenia ma także typ oświadczenia. Kombinacja typu oświadczenia i prawej zapewnia mechanizm służący do określania możliwości względem wartości. Na przykład oświadczenie typu "File", z prawej "odczytu" na wartość "Biography.doc" oznacza, że jednostka z jakich oświadczenia jest skojarzona ma dostęp do odczytu do pliku Biography.doc. Oświadczenie typu "Name", z prawej "PossessProperty" na wartość "Pole" wskazuje, czy jednostki, z którym takie oświadczenia jest skojarzona posiada właściwość Name o wartości "Pole".  
  
 Mimo że różnych typów oświadczeń i prawa są definiowane jako część modelu tożsamości, system jest rozszerzalny, dzięki czemu różnych systemów tworzenia na szczycie infrastruktury modelu tożsamości, aby zdefiniować dodatkowe oświadczenia i prawa zgodnie z wymaganiami.  
  
### <a name="identity-claims"></a>Oświadczenia tożsamości  
 Jednego określonego prawej jest to, że tożsamość. Oświadczenia, które posiadają to prawo należy oświadczenie o tożsamości jednostki. Na przykład oświadczenie typu "główna nazwa użytkownika" (UPN) z wartością "someone@example.com" oraz prawo tożsamości wskazuje określonej tożsamości w określonej domenie.  
  
#### <a name="system-identity-claim"></a>Oświadczenie tożsamości systemu  
 Modelu tożsamości definiuje jedno oświadczenie tożsamości: System. Oświadczenie tożsamości systemu oznacza jednostki bieżącej aplikacji lub systemu.  
  
### <a name="sets-of-claims"></a>Zestawy oświadczeń  
 Model oświadczenia, które reprezentują tożsamość jest ważne, ponieważ oświadczeń zawsze są wystawiane przez niektóre jednostki w systemie, nawet jeśli jednostkę jest ostatecznie niektóre pojęcia "self". Oświadczenia są zgrupowane jako zestaw i każdy zestaw ma wystawcę. Wystawca jest tylko zestaw oświadczeń. Relację cykliczną ostatecznie musi być zakończona i wszelkie oświadczenia zestaw może być własną wystawcy.  
  
 Na poniższej ilustracji przedstawiono przykład trzech zestawów oświadczeń, w której jeden zestaw oświadczeń zawiera, jako jego wystawcę inny zestaw oświadczeń, który z kolei ma System zestawu jako jego wystawca oświadczeń. W związku z tym zestawy oświadczeń tworzą hierarchii, które mogą być arbitralnie bezpośrednich.  
  
 ![Zarządzanie oświadczeniami i autoryzacją](../../../../docs/framework/wcf/feature-details/media/claimshierarchy.gif "claimshierarchy")  
  
 Wiele zestawów oświadczeń mogą mieć tej samej wydawania oświadczeń zestawu, jak pokazano na poniższej ilustracji.  
  
 ![Zarządzanie oświadczeniami i autoryzacją](../../../../docs/framework/wcf/feature-details/media/multiplesetsofclaims.gif "multiplesetsofclaims")  
  
 Z wyjątkiem zestaw oświadczeń, który jest jego własnej wystawcy modelu tożsamości nie zapewnia żadnych obsługę zestawów oświadczeń do tworzą pętli. W związku z tym sytuacji, w której zestaw oświadczeń A jest wystawiony przez zestaw oświadczeń B, który jest elementem wystawiony przez zestaw oświadczeń A, nigdy nie mogą wystąpić. Ponadto modelu tożsamości nie zapewnia wszelkie wsparcie dla zestawów oświadczeń ma wiele wystawców. Jeśli co najmniej dwa wystawców należy wygenerować danego zestawu oświadczeń, konieczne jest użycie wielu zestawów oświadczeń, każdy zawierającym tego samego oświadczenia, ale o różnych wystawców.  
  
### <a name="the-origin-of-claims"></a>Punkt początkowy oświadczeń  
 Oświadczenia mogą pochodzić z różnych źródeł. Jedno źródło wspólnej oświadczeń jest poświadczenia przedstawione przez użytkownika, na przykład jako część komunikatu wysłanego do usługi sieci Web. System weryfikuje tych oświadczeń i stają się one częścią zestawu oświadczeń skojarzonych z użytkownikiem. Inne składniki systemu mogą być również źródeł roszczenia, w tym między innymi systemu operacyjnego, stos sieciowy, środowisko wykonawcze lub aplikacji. Ponadto usługi zdalnego może być również źródłem oświadczeń.  
  
### <a name="authorization-policies"></a>Zasady autoryzacji  
 W modelu tożsamości oświadczeń są generowane jako część procesu oceny zasad autoryzacji. Zasady autoryzacji sprawdza zestaw (prawdopodobnie pusta) istniejącego oświadczeń i może wybrać dodać dodatkowe oświadczenia na podstawie oświadczeń, które jeszcze nie istnieje i dodatkowe informacje dyspozycji. Zapewnia to podstawę mapowanie między oświadczeń. Obecności lub braku oświadczeń w systemie wpływa na zachowanie zasady autoryzacji, w odniesieniu do tego, czy dodawane dodatkowe oświadczeń.  
  
 Na przykład zasady autoryzacji ma dostęp do bazy danych, która obejmuje birthdates różnych jednostek przy użyciu systemu. Zasady autoryzacji używa tych informacji, aby dodać oświadczenie "Over18" do kontekstu. Należy zwrócić uwagę, to oświadczenie Over18 nie ujawnia żadnych informacji o Jednostka inna niż fakt, że jest ponad 18 roku życia. Należy pamiętać, interpretacja oświadczenia "Over18" zależy opis semantyki roszczenia. Zasady autoryzacji, który dodaje oświadczenie rozumie tych semantyki na określonym poziomie. Kod, który następnie sprawdza oświadczenia, wynikające z oceny zasad być powiadamiane o tych semantyki.  
  
 Zasady autoryzacji danego może wymagać, czy można go obliczyć wielokrotnie ponieważ jak inne zasady autoryzacji Dodaj oświadczenia, te zasady autoryzacji może dodać jeszcze więcej oświadczeń. Modelu tożsamości zaprojektowano w celu oceny kontynuacja nie więcej oświadczenia są dodawane do kontekstu przy użyciu jednej z zasad autoryzacji w życie. Tej ciągłej oceny zasad autoryzacji uniemożliwia wymaganie wymusić w dowolnej kolejności oceny określonego w odniesieniu do zasady autoryzacji; oceną w dowolnej kolejności. Na przykład jeśli zasady X dodaje oświadczeń Z tylko, jeśli zasady A został dodany B z oświadczeń, następnie jeśli X jest szacowana jako pierwsza, początkowo nie dodaje Z oświadczeń. Później A jest obliczane i dodaje oświadczenie B. X jest oceniane oddzielnie po raz drugi i teraz dodaje Z oświadczeń.  
  
 Dany system może mieć wiele zasad autoryzacji w życie.  
  
### <a name="a-key-making-machine"></a>Maszyna wprowadzania klucza  
 Ocena grupy zasad autoryzacji skojarzony jest przy użyciu na komputerze, który sprawia, że klucze. Zasady autoryzacji są oceniane w każdej i zestawy oświadczeń są generowane, tworzenie kształtu klucza. Po zakończeniu kształtu klucza może służyć próby otwarcia niektórych blokad. Kształt klucz jest przechowywany w "kontekst autoryzacji," utworzony przez Menedżera autoryzacji.  
  
### <a name="authorization-context"></a>Kontekst autoryzacji  
 Menedżer autoryzacji ocenia się różne zasady autoryzacji, zgodnie z opisem, a wynik jest kontekst autoryzacji (zestawu zestawów oświadczeń i niektóre właściwości). Aby ustalić, jakie oświadczenia są obecne w tym kontekście relacje między tych różnych oświadczeń (na przykład zestawie oświadczeń wystawiających certyfikaty), a ostatecznie porównać je niektóre wymagania, muszą one odpowiadać na dostęp można zbadać kontekst autoryzacji zasób.  
  
### <a name="locks"></a>Blokady  
 Jeśli kontekst autoryzacji (zestaw oświadczeń) to klucz, wymagania, które muszą być spełnione, aby udzielić dostępu do określonego zasobu chronionego stanowią blokady, który musi znajdować się w kluczu. Modelu tożsamości nie formalnego, jak te wymagania są wyrażane, ale na podstawie oświadczeń charakter systemu, wymagają one porównywanie oświadczeń w kontekście autoryzacji przed niektórych zestaw oświadczeń wymagane.  
  
### <a name="a-recap"></a>— Podsumowanie  
 Modelu tożsamości opiera się wokół pojęcie oświadczeń. Oświadczenia są pogrupowane w zestawy i zagregowane w kontekście autoryzacji. Kontekst autoryzacji zawiera zestaw oświadczeń i jest wynikiem obliczenia co najmniej jedne zasady autoryzacji, skojarzone z Menedżera autoryzacji. Oświadczeń ustawia można zbadać w celu określenia, czy zostały spełnione wymagania dotyczące dostępu. Na poniższej ilustracji przedstawiono relacje między tych pojęć różnych modelu tożsamości.  
  
 ![Zarządzanie oświadczeniami i autoryzacją](../../../../docs/framework/wcf/feature-details/media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>Program WCF i modelu tożsamości  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa infrastruktury modelu tożsamości jako podstawy do wykonywania autoryzacji. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasa pozwala na określenie *autoryzacji* zasad jako część usługi. Te zasady autoryzacji są określane jako *zasady autoryzacji zewnętrznych*, i mogą wykonywać przetwarzania oświadczenia na podstawie zasad lokalnych lub wyniku interakcji z usługi zdalnej. Menedżer autoryzacji reprezentowany przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasy ocenia zasady autoryzacji zewnętrznych wraz z zasady autoryzacji, które rozpoznają poświadczeń różnych typów (tokeny) i wypełnia, co jest nazywane  *kontekst autoryzacji* z oświadczeniami odpowiednie do przychodzącego komunikatu. Kontekst autoryzacji jest reprezentowana przez <xref:System.IdentityModel.Policy.AuthorizationContext> klasy.  
  
## <a name="identity-model-programming"></a>Tożsamość Model programowania  
 W poniższej tabeli opisano model obiektów używany do rozszerzenia modelu tożsamości programów. Te wszystkie klasy istnieje albo <xref:System.IdentityModel.Policy> lub <xref:System.IdentityModel.Claims> przestrzeni nazw.  
  
|Class|Opis|  
|-----------|-----------------|  
|Składnik autoryzacji|Klasa modelu tożsamości, który implementuje <xref:System.IdentityModel.Policy.IAuthorizationComponent> interfejsu.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Interfejs, który udostępnia właściwości jednego ciągu tylko do odczytu: identyfikator. Wartość tej właściwości jest unikatowy dla każdego wystąpienia w systemie, który implementuje ten interfejs.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|*Składnik autoryzacji* zawierający zestaw `ClaimSet` wystąpień zero lub więcej właściwości; wynik oceny co najmniej jedne zasady autoryzacji.|  
|<xref:System.IdentityModel.Claims.Claim>|Kombinacja typu oświadczenia uprawnienia, i wartość. Części prawo i wartości są ograniczone przez typ oświadczenia.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Abstrakcyjna klasa podstawowa. Kolekcja `Claim` wystąpień.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Klasy zapieczętowanej. Implementacja interfejsu `ClaimSet` klasy.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Abstrakcyjna klasa podstawowa. Przekazany w zasadach autoryzacji podczas oceny zasad.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Interfejs pochodny `IAuthorizationComponent` i implementowane przez klasy zasad autoryzacji.|  
|<xref:System.IdentityModel.Claims.Rights>|Klasa statyczna zawiera wstępnie zdefiniowane wartości prawo.|  
  
 Następujące klasy są również używane dla tożsamości modelu programowania, ale nie został znaleziony w <xref:System.IdentityModel.Policy> lub <xref:System.IdentityModel.Claims> przestrzeni nazw.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Klasa, która udostępnia metodę — <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>— przeprowadzić autoryzacji na podstawie oświadczenia, sprawdza dla każdej operacji w usłudze. Musi pochodzić z klasy i zastąpić metodę.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Klasy zapieczętowanej zapewnia różne właściwości związane z zachowaniem usługi w odniesieniu do autoryzacji.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Klasa udostępniająca kontekstu zabezpieczeń, w tym kontekście autoryzacji, aktualnie uruchomionych (lub jest uruchomiony) operacji. Wystąpienie tej klasy jest częścią <xref:System.ServiceModel.OperationContext>.|  
  
### <a name="significant-members"></a>Istotne elementy członkowskie  
 Następujące elementy członkowskie są często używane do tworzenia nowe typy oświadczeń.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Klasy pochodne zaimplementować tę metodę do wykonywania kontroli dostępu na podstawie oświadczeń przed uruchomieniem operacji w usłudze. Wszystkie informacje w podane <xref:System.ServiceModel.OperationContext>, lub w innym miejscu, można zbadać podczas wprowadzania dostępu, sprawdź decyzji. Jeśli <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> zwraca `true`, zostanie przyznany dostęp i operacja jest dozwolona do uruchomienia. Jeśli `CheckAccessCore` zwraca `false`, odmowa dostępu i nie można uruchomić operację. Na przykład zobacz [porady: tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Zwraca <xref:System.ServiceModel.ServiceAuthorizationManager> dla usługi. <xref:System.ServiceModel.ServiceAuthorizationManager> Jest odpowiedzialny za podejmowania decyzji dotyczących autoryzacji.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Kolekcja zasad autoryzacji niestandardowej określonych dla usługi. Te zasady są oceniane oprócz tych zasad skojarzonych z poświadczeń w komunikatach przychodzących.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Policy.EvaluationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationComponent>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims>  
 <xref:System.IdentityModel.Policy>  
 <xref:System.IdentityModel.Tokens>  
 <xref:System.IdentityModel.Selectors>  
 [Oświadczenia i tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Oświadczenia i odmawianie dostępu do zasobów](../../../../docs/framework/wcf/feature-details/claims-and-denying-access-to-resources.md)  
 [Tworzenie oświadczenia i wartości zasobów](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Porady: tworzenie oświadczenia niestandardowego](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)  
 [Porady: porównywanie oświadczeń](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [Porady: Tworzenie niestandardowych zasad autoryzacji](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-policy.md)  
 [Porady: tworzenie Menedżera autoryzacji niestandardowej dla usługi](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
