---
title: Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości
description: Dowiedz się więcej o najważniejszych pojęciach programistycznych dotyczących modelu tożsamości WCF, modelu opartego na oświadczeniach na potrzeby wykonywania autoryzacji.
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- WCF security
- claims [WCF], managing with the Identity Model
- claims [WCF]
- authorization [WCF], managing with the Identity Model
ms.assetid: 099defbb-5d35-434e-9336-1a49b9ec7663
ms.openlocfilehash: 0d5687f8ac5021c008254f0f5cc453eda5e538c7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245131"
---
# <a name="managing-claims-and-authorization-with-the-identity-model"></a>Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości
Autoryzacja to proces określania, które jednostki mają uprawnienia do zmiany, wyświetlania lub dostępu do zasobu komputera. Na przykład w firmie tylko kierownicy mogą uzyskać dostęp do plików ich pracowników. Windows Communication Foundation (WCF) obsługuje dwa mechanizmy przetwarzania autoryzacji. Pierwszy mechanizm pozwala kontrolować autoryzację przy użyciu istniejących konstrukcji środowiska uruchomieniowego języka wspólnego (CLR). Drugi jest modelem opartym na oświadczeniach znanym jako *model tożsamości*. Usługa WCF używa modelu tożsamości do tworzenia oświadczeń z komunikatów przychodzących; Klasy modelu tożsamości można rozszerzyć, aby obsługiwać nowe typy roszczeń dla niestandardowych schematów autoryzacji. W tym temacie przedstawiono przegląd najważniejszych koncepcji programistycznych dotyczących modelu tożsamości, a także listę najważniejszych klas używanych przez funkcję.  
  
## <a name="identity-model-scenarios"></a>Scenariusze dotyczące modelu tożsamości  
 Poniższe scenariusze przedstawiają użycie modelu tożsamości.  
  
### <a name="scenario-1-supporting-identity-role-and-group-claims"></a>Scenariusz 1: Obsługa tożsamości, ról i oświadczeń grup  
 Użytkownicy wysyłają komunikaty do usługi sieci Web. Wymagania dotyczące kontroli dostępu usługi sieci Web używają tożsamości, ról lub grup. Nadawca wiadomości jest mapowany na zestaw ról lub grup. Informacje o roli lub grupie są używane do przeprowadzania kontroli dostępu.  
  
### <a name="scenario-2-supporting-rich-claims"></a>Scenariusz 2: obsługa rozbudowanych oświadczeń  
 Użytkownicy wysyłają komunikaty do usługi sieci Web. Wymagania dotyczące kontroli dostępu usługi sieci Web wymagają bardziej zaawansowanego modelu niż tożsamości, ról lub grup. Usługa sieci Web określa, czy dany użytkownik ma dostęp do konkretnego chronionego zasobu przy użyciu rozbudowanego modelu opartego na oświadczeniach. Na przykład jeden użytkownik może mieć możliwość odczytywania określonych informacji, takich jak informacje o wynagrodzeniu, do których inni użytkownicy nie mają dostępu.  
  
### <a name="scenario-3-mapping-disparate-claims"></a>Scenariusz 3. Mapowanie różnych oświadczeń  
 Użytkownik wysyła komunikat do usługi sieci Web. Użytkownik może określić swoje poświadczenia na wiele różnych sposobów: certyfikat X. 509, token nazwy użytkownika lub token Kerberos. Usługa sieci Web jest wymagana do sprawdzenia kontroli dostępu w taki sam sposób, niezależnie od typu poświadczeń użytkownika. Jeśli dodatkowe typy poświadczeń są obsługiwane w miarę upływu czasu, system powinien odpowiednio się rozwijać.  
  
### <a name="scenario-4-determining-access-to-multiple-resources"></a>Scenariusz 4: Określanie dostępu do wielu zasobów  
 Usługa sieci Web próbuje uzyskać dostęp do wielu zasobów. Usługa określa, które chronione zasoby, do których dany użytkownik ma dostęp, porównując oświadczenia powiązane z użytkownikiem z oświadczeniami wymaganymi w celu uzyskania dostępu do zasobu.  
  
## <a name="identity-model-terms"></a>Warunki modelu tożsamości  
 Poniższa lista definiuje kluczowe terminy używane do opisywania koncepcji modelu tożsamości.  
  
 Zasady autoryzacji  
 Zestaw reguł do mapowania zestawu oświadczeń wejściowych do zestawu oświadczeń wyjściowych. Ocenianie wyników zasad autoryzacji w zestawach, które są dodawane do kontekstu oceny, a następnie kontekstu autoryzacji.  
  
 Kontekst autoryzacji  
 Zestaw zestawów i zero lub więcej właściwości. Wynik oceny co najmniej jednej zasady autoryzacji.  
  
 Claim  
 Kombinacja typu, praw i wartości.  
  
 Zestaw roszczeń  
 Zestaw oświadczeń wystawionych przez określonego wystawcy.  
  
 Typ oświadczenia  
 Rodzaj żądania. Oświadczenia zdefiniowane przez interfejs API modelu tożsamości są właściwościami <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> klasy. Przykłady typów roszczeń dostarczonych przez system to,,,,,,,,, <xref:System.IdentityModel.Claims.ClaimTypes.Dns%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Email%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Hash%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Sid%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Spn%2A> <xref:System.IdentityModel.Claims.ClaimTypes.System%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Uri%2A> , i <xref:System.IdentityModel.Claims.ClaimTypes.X500DistinguishedName%2A> .  
  
 Kontekst oceny  
 Kontekst, w którym są oceniane zasady autoryzacji. Zawiera właściwości i zestawy roszczeń. Jest podstawą kontekstu autoryzacji po zakończeniu szacowania.  
  
 Tożsamość tożsamości  
 Element Claim, którego prawo jest tożsamość.  
  
 Wystawca  
 Zestaw roszczeń, który zawiera co najmniej jedno zastrzeżenie tożsamości i jest uznawany za wystawiony inny zestaw roszczeń.  
  
 Właściwości  
 Zestaw informacji skojarzonych z kontekstem oceny lub kontekstem autoryzacji.  
  
 Zasób chroniony  
 Coś w systemie, który może być używany, dostępny lub w inny sposób manipulowany, jeśli niektóre wymagania zostały spełnione.  
  
 Prawe  
 Możliwość nad zasobem. Prawa zdefiniowane przez interfejs API modelu tożsamości są właściwościami <xref:System.IdentityModel.Claims.Rights> klasy. Przykłady praw dostarczonych przez system są <xref:System.IdentityModel.Claims.Rights.Identity%2A> i <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> .  
  
 Wartość  
 Coś, w którym zażądano prawa.  
  
## <a name="claims"></a>Oświadczenia  
 Model tożsamości to system oparty na oświadczeniach. Oświadczenia opisują możliwości związane z niektórymi jednostkami w systemie, często użytkownika tego systemu. Zestaw oświadczeń skojarzonych z daną jednostką może być uważany za klucz. Określone oświadczenia definiują kształt tego klucza, podobnie jak klucz fizyczny używany do otwierania blokady w drzwiach. Oświadczenia są używane w celu uzyskania dostępu do zasobów. Dostęp do danego chronionego zasobu jest określany przez porównanie oświadczeń wymaganych do uzyskania dostępu do tego zasobu z oświadczeniami skojarzonymi z jednostką próbującą uzyskać dostęp.  
  
 Element Claim jest wyrażeniem po prawej stronie względem określonej wartości. Prawo może wyglądać podobnie jak "read", "Write" lub "Execute". Wartością może być baza danych, plik, Skrzynka pocztowa lub właściwość. Oświadczenia mają również typ oświadczenia. Kombinacja typu "typ" i "Right" zapewnia mechanizm określania możliwości w odniesieniu do wartości. Na przykład, zgłoszenie typu "plik" z prawej strony "Odczyt" przez wartość "Biography.doc" wskazuje, że jednostka, z którą jest skojarzone takie zastrzeżenie, ma dostęp do odczytu do Biography.doc pliku. Zgłoszenie typu "name" z prawej strony "PossessProperty" na wartość "Martin" wskazuje, że jednostka, z którą jest skojarzone takie zgłoszenie, posiada właściwość Name o wartości "Martin".  
  
 Chociaż różne typy i prawa są zdefiniowane jako część modelu tożsamości, system jest rozszerzalny, co pozwala różnym systemom, które są tworzone w oparciu o infrastrukturę modelu tożsamości, w celu zdefiniowania dodatkowych typów i praw dostępu zgodnie z potrzebami.  
  
### <a name="identity-claims"></a>Oświadczenia tożsamości  
 Jedną z nich jest prawo tożsamość. Oświadczenia, które posiadały to prawo, składają instrukcję dotyczącą tożsamości jednostki. Na przykład oświadczenie typu "główna nazwa użytkownika" (UPN) o wartości " someone@example.com " i po prawej stronie tożsamości wskazuje konkretną tożsamość w określonej domenie.  
  
#### <a name="system-identity-claim"></a>Systemowe zgłoszenie tożsamości  
 Model tożsamości definiuje jedno zgłoszenie tożsamości: System. Wystąpienie tożsamości systemowej wskazuje, że jednostką jest bieżąca aplikacja lub system.  
  
### <a name="sets-of-claims"></a>Zestawy oświadczeń  
 Model oświadczeń reprezentujący tożsamość jest ważny, ponieważ oświadczenia są zawsze wystawiane przez niektóre jednostki w systemie, nawet jeśli ta jednostka jest ostatecznie pewną koncepcją "samodzielne". Oświadczenia są pogrupowane jako zbiór, a każdy zestaw ma wystawcę. Wystawcy jest tylko zestaw oświadczeń. Takie relacje cykliczne muszą ostatecznie kończyć się, a każdy zestaw roszczeń może być własnym wystawcą.  
  
 Na poniższej ilustracji przedstawiono przykład trzech zestawów oświadczeń, w których jeden zestaw oświadczeń ma, jako wystawcy, inny zestaw oświadczeń, który z kolei ma ustawione oświadczenie systemowe jako wystawca. W związku z tym zestawy oświadczeń tworzą hierarchię, która może być arbitralnie głęboka.  
  
 ![Zestawy oświadczeń w hierarchii.](./media/managing-claims-and-authorization-with-the-identity-model/claims-sets-hierarchy.gif)  
  
 Wiele zestawów oświadczeń może mieć ten sam zestaw oświadczeń wystawiających, jak pokazano na poniższym rysunku:
  
 ![Wiele zestawów oświadczeń z tym samym zestawem wystawiania oświadczeń.](./media/managing-claims-and-authorization-with-the-identity-model/multiple-claim-sets-same-issuing-claim-set.gif)  
  
 Z wyjątkiem zestawu roszczeń, który jest jego własnym wystawcą, model tożsamości nie zapewnia żadnej obsługi zestawów roszczeń do tworzenia pętli. W związku z tym, gdy zestaw roszczeń A jest wystawiony przez zestaw roszczeń B, który jest wystawiony przez zestaw roszczeń A, może nigdy nie wystąpić. Ponadto model tożsamości nie zapewnia żadnej obsługi dla zestawów roszczeń mających wiele wystawców. Jeśli co najmniej jeden wystawca musi wydać określony zestaw oświadczeń, należy użyć wielu zestawów oświadczeń, z których każda zawiera te same oświadczenia, ale mają różne wystawcy.  
  
### <a name="the-origin-of-claims"></a>Pochodzenie oświadczeń  
 Oświadczenia mogą pochodzić z różnych źródeł. Jednym ze wspólnych źródeł oświadczeń są poświadczenia prezentowane przez użytkownika, na przykład w ramach wiadomości wysyłanej do usługi sieci Web. System weryfikuje takie oświadczenia i staje się częścią zestawu oświadczeń skojarzonych z użytkownikiem. Inne składniki systemu mogą również być źródłami oświadczeń, w tym z systemem operacyjnym, stosem sieci, środowiskiem uruchomieniowym lub aplikacją. Ponadto usługi zdalne mogą również być źródłem oświadczeń.  
  
### <a name="authorization-policies"></a>Zasady autoryzacji  
 W modelu tożsamości oświadczenia są generowane w ramach procesu oceny zasad autoryzacji. Zasady autoryzacji badają (prawdopodobnie pusty) zestaw istniejących oświadczeń i mogą zdecydować się na dodanie dodatkowych oświadczeń na podstawie już obecnych oświadczeń i dodatkowych informacji. Zapewnia to podstawę mapowania między oświadczeniami. Obecność lub brak oświadczeń w systemie ma wpływ na zachowanie zasad autoryzacji w odniesieniu do tego, czy dodaje dodatkowe oświadczenia.  
  
 Na przykład zasady autoryzacji mają dostęp do bazy danych, która zawiera DataUrodzenia różnych jednostek korzystających z systemu. Zasady autoryzacji używają tych informacji w celu dodania do kontekstu żądania "Over18". Należy zauważyć, że to Over18 nie ujawnia żadnych informacji o jednostce innej niż fakt, że jest ona w wieku powyżej 18 lat. Należy zauważyć, że interpretacja "Over18" jest zależna od poznania semantyki tego żądania. Zasady autoryzacji, które dodaliśmy do żądania, rozumieją te semantykę na pewnym poziomie. Kod, który następnie sprawdza oświadczenia wynikające z oceny zasad, również jest informowany o tych semantyki.  
  
 Dane zasady autoryzacji mogą wymagać oceny wielu razy, ponieważ inne zasady autoryzacji dodają oświadczenia, że zasady autoryzacji mogą dodać jeszcze więcej oświadczeń. Model tożsamości został zaprojektowany w celu kontynuowania oceny do momentu dodania kolejnych oświadczeń do kontekstu przez żadną z zasad autoryzacji. Ta ciągła ocena zasad autoryzacji uniemożliwia wymaganie wymuszenia konkretnej kolejności oceny w odniesieniu do zasad autoryzacji. można je ocenić w dowolnej kolejności. Na przykład jeśli zasady X dodają tylko żądania Z, jeśli zasady A dodaliśmy zgłoszenie B, a następnie Jeśli X jest szacowana jako pierwszy, początkowo nie dodaje żądania Z. Następnie jest obliczany i dodawany jest wniosek B. X, a następnie obliczany jest drugi raz, a ten czas dodaje wartość Z.  
  
 W danym systemie może istnieć wiele zasad autoryzacji.  
  
### <a name="a-key-making-machine"></a>Komputer służący do tworzenia kluczy  
 Ocenianie grupy skojarzonych zasad autoryzacji jest podobne do korzystania z komputera, który tworzy klucze. Zasady autoryzacji są oceniane i są generowane zestawy oświadczeń, tworząc kształt klucza. Po zakończeniu kształtu klucza można go użyć do próby otwarcia niektórych blokad. Kształt klucza jest przechowywany w "kontekście autoryzacji", który jest tworzony przez Menedżera autoryzacji.  
  
### <a name="authorization-context"></a>Kontekst autoryzacji  
 Menedżer autoryzacji ocenia różne zasady autoryzacji zgodnie z opisem, a wynik jest kontekstem autoryzacji (zestawem zestawów roszczeń i niektórymi skojarzonymi właściwościami). Kontekst autoryzacji można sprawdzić, aby określić, jakie oświadczenia są obecne w tym kontekście, relacje między tymi różnymi oświadczeniami (na przykład zestaw oświadczeń wystawiających) i ostatecznie porównać je z pewnymi wymaganiami, które muszą spełniać, aby uzyskać dostęp do zasobu.  
  
### <a name="locks"></a>Blokady  
 Jeśli kontekst autoryzacji (zestaw oświadczeń) jest kluczem, wymagania, które muszą zostać spełnione, aby udzielić dostępu do określonego chronionego zasobu stanowią blokadę, którą musi dopasować klucz. Model tożsamości nie prace prowadzone, w jaki sposób te wymagania są wyrażane, ale w przypadku opartego na oświadczeniach charakteru systemu, obejmują porównanie oświadczeń w kontekście autoryzacji z określonym zestawem wymaganych oświadczeń.  
  
### <a name="a-recap"></a>Podsumowanie  
 Model tożsamości jest oparty na koncepcji oświadczeń. Oświadczenia są pogrupowane w zestawy i agregowane w kontekście autoryzacji. Kontekst autoryzacji zawiera zestaw oświadczeń i jest wynikiem oceny jednej lub większej liczby zasad autoryzacji skojarzonych z Menedżerem autoryzacji. Te zestawy roszczeń można sprawdzić w celu ustalenia, czy zostały spełnione wymagania dotyczące dostępu. Na poniższej ilustracji przedstawiono relacje między tymi różnymi koncepcjami modelu tożsamości.  
  
 ![Zarządzanie oświadczeniami i autoryzacją](media/xsi-recap.gif "xsi_recap")  
  
## <a name="wcf-and-identity-model"></a>WCF i model tożsamości  
 Usługa WCF używa infrastruktury modelu tożsamości jako podstawy do wykonywania autoryzacji. W programie WCF <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Klasa umożliwia określenie zasad *autoryzacji* w ramach usługi. Takie zasady autoryzacji są nazywane *zewnętrznymi zasadami autoryzacji*i mogą wykonywać przetwarzanie roszczeń na podstawie lokalnych zasad lub interakcji z usługą zdalną. Menedżer autoryzacji reprezentowany przez <xref:System.ServiceModel.ServiceAuthorizationManager> klasę ocenia zewnętrzne zasady autoryzacji wraz z zasadami autoryzacji, które rozpoznają różne typy poświadczeń (tokeny) i wypełniają informacje o nazwie *kontekstu autoryzacji* z oświadczeniami właściwymi dla wiadomości przychodzącej. Kontekst autoryzacji jest reprezentowany przez <xref:System.IdentityModel.Policy.AuthorizationContext> klasę.  
  
## <a name="identity-model-programming"></a>Programowanie modelu tożsamości  
 W poniższej tabeli opisano model obiektów używany do programowania rozszerzeń modelu tożsamości. Wszystkie te klasy istnieją w <xref:System.IdentityModel.Policy> <xref:System.IdentityModel.Claims> przestrzeni nazw lub.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|Składnik autoryzacji|Klasa modelu tożsamości, która implementuje <xref:System.IdentityModel.Policy.IAuthorizationComponent> interfejs.|  
|<xref:System.IdentityModel.Policy.IAuthorizationComponent>|Interfejs, który udostępnia pojedynczą Właściwość ciągu tylko do odczytu: ID. Wartość tej właściwości jest unikatowa dla każdego wystąpienia w systemie, który implementuje ten interfejs.|  
|<xref:System.IdentityModel.Policy.AuthorizationContext>|*Składnik autoryzacji* , który zawiera zestaw `ClaimSet` wystąpień z zerową lub większą liczbą właściwości; wynik oceny co najmniej jednej zasady autoryzacji.|  
|<xref:System.IdentityModel.Claims.Claim>|Kombinacja typu, praw i wartości. Części prawej i wartości są ograniczone przez typ zgłoszenia.|  
|<xref:System.IdentityModel.Claims.ClaimSet>|Abstrakcyjna klasa bazowa. Kolekcja `Claim` wystąpień.|  
|<xref:System.IdentityModel.Claims.DefaultClaimSet>|Klasa zapieczętowana. Implementacja `ClaimSet` klasy.|  
|<xref:System.IdentityModel.Policy.EvaluationContext>|Abstrakcyjna klasa bazowa. Przeszedł do zasad autoryzacji podczas oceny zasad.|  
|<xref:System.IdentityModel.Policy.IAuthorizationPolicy>|Interfejs pochodzący z `IAuthorizationComponent` i implementowany przez klasy zasad autoryzacji.|  
|<xref:System.IdentityModel.Claims.Rights>|Klasa statyczna, która zawiera wstępnie zdefiniowane prawidłowe wartości.|  
  
 Poniższe klasy są również używane do programowania modelu tożsamości, ale nie znajdują się w <xref:System.IdentityModel.Policy> <xref:System.IdentityModel.Claims> przestrzeni nazw ani.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager>|Klasa, która dostarcza metodę — <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> do wykonywania kontroli autoryzacji opartej na zastosowaniach dla każdej operacji w usłudze. Musisz pochodzić z klasy i zastąpić metodę.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>|Klasa zapieczętowana, która zapewnia różne właściwości związane z zachowaniem usługi w odniesieniu do autoryzacji.|  
|<xref:System.ServiceModel.ServiceSecurityContext>|Klasa, która dostarcza kontekst zabezpieczeń, w tym kontekst autoryzacji, dla aktualnie uruchomionej (lub o uruchamianej) operacji. Wystąpienie tej klasy jest częścią <xref:System.ServiceModel.OperationContext> .|  
  
### <a name="significant-members"></a>Znaczące elementy członkowskie  
 Następujące składowe są często używane do tworzenia nowych typów roszczeń.  
  
|Członek|Opis|  
|------------|-----------------|  
|<xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>|Klasy pochodne implementują tę metodę w celu przeprowadzania kontroli dostępu opartej na żądaniach przed uruchomieniem operacji w usłudze. Wszelkie informacje zawarte w dostarczonym <xref:System.ServiceModel.OperationContext> lub innym miejscu mogą być badane podczas podejmowania decyzji o sprawdzeniu dostępu. Jeśli <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> zwraca `true` , zostanie udzielony dostęp, a operacja może być uruchomiona. W przypadku `CheckAccessCore` powracania `false` następuje odmowa dostępu, a operacja nie zostanie uruchomiona. Aby zapoznać się z przykładem, zobacz [How to: Create an Custom Authorization Manager for a Service](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md).|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A>|Zwraca <xref:System.ServiceModel.ServiceAuthorizationManager> dla usługi. <xref:System.ServiceModel.ServiceAuthorizationManager>Jest odpowiedzialny za podejmowanie decyzji dotyczących autoryzacji.|  
|<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>|Kolekcja niestandardowych zasad autoryzacji określonych dla usługi. Te zasady są oceniane oprócz zasad skojarzonych z poświadczeniami w wiadomościach przychodzących.|  
  
## <a name="see-also"></a>Zobacz też

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
- [Oświadczenia i tokeny](claims-and-tokens.md)
- [Oświadczenia i odmawianie dostępu do zasobów](claims-and-denying-access-to-resources.md)
- [Tworzenie oświadczenia i wartości zasobów](claim-creation-and-resource-values.md)
- [Instrukcje: Tworzenie oświadczenia niestandardowego](../extending/how-to-create-a-custom-claim.md)
- [Porady: Porównywanie oświadczeń](../extending/how-to-compare-claims.md)
- [Instrukcje: Tworzenie niestandardowych zasad autoryzacji](../extending/how-to-create-a-custom-authorization-policy.md)
- [Instrukcje: tworzenie menedżera autoryzacji niestandardowej dla usługi](../extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [Przegląd zabezpieczeń](security-overview.md)
- [Autoryzacja](authorization-in-wcf.md)
