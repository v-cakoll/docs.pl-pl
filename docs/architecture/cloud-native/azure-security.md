---
title: Zabezpieczenia platformy Azure dla aplikacji natywnych dla chmury
description: Projektowanie aplikacji platformy .NET natywnych dla chmury na platformie Azure | Aplikacje natywne usługi Azure Security for Cloud
ms.date: 06/30/2019
ms.openlocfilehash: 13b5ad7a883a83014913fa0a6a020610c28c524f
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989145"
---
# <a name="azure-security-for-cloud-native-apps"></a>Zabezpieczenia platformy Azure dla aplikacji natywnych dla chmury

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikacje natywne dla chmury mogą być łatwiejsze i trudniejsze do zabezpieczenia niż tradycyjne aplikacje. Na minus, trzeba zabezpieczyć więcej mniejszych aplikacji i poświęcić więcej energii, aby zbudować infrastrukturę zabezpieczeń. Niejednorodny charakter języków programowania i stylów w większości wdrożeń usług oznacza również, że należy zwrócić większą uwagę na biuletyny zabezpieczeń od wielu różnych dostawców.

Z drugiej strony mniejsze usługi, z których każda ma własny magazyn danych, ograniczają zakres ataku. Jeśli osoba atakująca naruszy jeden system, prawdopodobnie osobie atakującej trudniej jest przejść do innego systemu niż w aplikacji monolitycznej. Granice procesu są silne granice. Ponadto jeśli kopia zapasowa bazy danych wycieka, uszkodzenie jest bardziej ograniczone, ponieważ ta baza danych zawiera tylko podzbiór danych i jest mało prawdopodobne, aby zawierała dane osobowe.

## <a name="threat-modeling"></a>Threat Modeling

Bez względu na to, czy korzyści przewyższają wady aplikacji natywnych dla chmury, należy przestrzegać tego samego holistycznego sposobu myślenia o bezpieczeństwie. Bezpieczeństwo i bezpieczne myślenie muszą być częścią każdego kroku historii rozwoju i operacji. Podczas planowania aplikacji zadawaj pytania, takie jak:

- Jaki byłby wpływ utraty tych danych?
- Jak możemy ograniczyć szkody spowodowane złymi danymi wstrzykniętymi do tej usługi?
- Kto powinien mieć dostęp do tych danych?
- Czy istnieją zasady inspekcji dotyczące procesu opracowywania i wydawania?

Wszystkie te pytania są częścią procesu zwanego [modelowania zagrożeń](https://docs.microsoft.com/azure/security/azure-security-threat-modeling-tool). Proces ten próbuje odpowiedzieć na pytanie, jakie zagrożenia są dla systemu, jak prawdopodobne są zagrożenia i potencjalne szkody z nich.

Po ustaleniu listy zagrożeń należy zdecydować, czy warto je ograniczyć. Czasami zagrożenie jest tak mało prawdopodobne i kosztowne, aby zaplanować, że nie warto wydawać na to energii. Na przykład niektóre aktora na poziomie stanu może wstrzyknąć zmiany w projekcie procesu, który jest używany przez miliony urządzeń. Teraz, zamiast uruchamiania pewnego fragmentu kodu w [Pierścieniu 3,](https://en.wikipedia.org/wiki/Protection_ring)ten kod jest uruchamiany w Pierścieniu 0. Umożliwia to wykorzystać, który można pominąć hypervisor i uruchomić kod ataku na komputerach z systemem gołym stanie metalowym, umożliwiając ataki na wszystkich maszynach wirtualnych, które są uruchomione na tym sprzęcie.

Zmienione procesory są trudne do wykrycia bez mikroskopu i zaawansowanej wiedzy na temat projektu krzemu tego procesora. Ten scenariusz jest mało prawdopodobne i kosztowne w celu złagodzenia, więc prawdopodobnie żaden model zagrożenia nie zaleca tworzenia ochrony przed exploitami dla niego.

Bardziej prawdopodobne zagrożenia, takie jak `Id` kontroli przerwanego dostępu, `Id=2` `Id=3` umożliwiające zwiększenie ataków (zastępując w adresie URL) lub iniekcji SQL, są bardziej atrakcyjne do tworzenia zabezpieczeń przed. Środki zaradcze dla tych zagrożeń są dość rozsądne, aby zbudować i zapobiec kłopotliwym lukom w zabezpieczeniach, które rozmazują reputację firmy.

## <a name="principle-of-least-privilege"></a>Zasada najmniejszego przywileju

Jednym z pomysłów założycieli w zakresie bezpieczeństwa komputerowego jest Zasada najmniejszych przywilejów (POLP). Jest to w rzeczywistości fundamentalny pomysł w większości każdej formy bezpieczeństwa, czy to cyfrowego, czy fizycznego. Krótko mówiąc, zasada jest taka, że każdy użytkownik lub proces powinien mieć najmniejszą liczbę praw możliwych do wykonania swojego zadania.

Na przykład pomyśl o kasjerach w banku: dostęp do sejfu jest niezbyt częstym działaniem. Tak więc przeciętny kasjer nie może samodzielnie otworzyć sejfu. Aby uzyskać dostęp, muszą eskalować swoje żądanie za pośrednictwem menedżera banku, który przeprowadza dodatkowe kontrole bezpieczeństwa.

W systemie komputerowym fantastycznym przykładem są prawa użytkownika łączącego się z bazą danych. W wielu przypadkach istnieje jedno konto użytkownika używane zarówno do tworzenia struktury bazy danych, jak i uruchamiania aplikacji. Z wyjątkiem przypadków w skrajnych przypadkach konto z uruchomieniem aplikacji nie wymaga możliwości aktualizowania informacji o schemacie. Powinno istnieć kilka kont, które zapewniają różne poziomy uprawnień. Aplikacja powinna używać tylko poziomu uprawnień, który udziela dostępu do odczytu i zapisu do danych w tabelach. Ten rodzaj ochrony wyeliminowałby ataki, które miały na celu upuszczenie tabel bazy danych lub wprowadzenie złośliwych wyzwalaczy.

Prawie każda część tworzenia aplikacji natywnej dla chmury może korzystać z zapamiętywania zasady najmniejszych uprawnień. Można go znaleźć w grze podczas konfigurowania zapór, grup zabezpieczeń sieci, ról i zakresów w kontroli dostępu opartej na rolach (RBAC).

## <a name="penetration-testing"></a>Testy penetracyjne

W miarę jak aplikacje stają się coraz bardziej skomplikowane, liczba wektorów ataku wzrasta w zastraszającym tempie. Modelowanie zagrożeń jest wadliwe, ponieważ zwykle jest wykonywane przez te same osoby budujące system. W ten sam sposób, że wielu deweloperów ma problemy z przewidywaniem interakcji użytkowników, a następnie budować bezużyteczne interfejsy użytkownika, większość deweloperów ma trudności z widzeniem każdego wektora ataku. Jest również możliwe, że deweloperzy budujący system nie są dobrze zorientowani w metodologii ataku i przegapić coś kluczowego.

Testy penetracyjne lub "testowanie pióra" polega na sprowadzeniu podmiotów zewnętrznych do próby ataku na system. Te osoby atakujące mogą być zewnętrzną firmą konsultingową lub innymi deweloperami z dobrą wiedzą o bezpieczeństwie z innej części firmy. Otrzymują carte blanche, aby spróbować obalić system. Często znajdują one rozległe luki w zabezpieczeniach, które należy załatać. Czasami wektor ataku będzie czymś zupełnie nieoczekiwanym, jak wykorzystanie ataku phishingowego na ceo.

Sama platforma Azure nieustannie atakuje [zespół hakerów w firmie Microsoft.](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/) Przez lata jako pierwsi znaleźli dziesiątki potencjalnie katastrofalnych wektorów ataku, zamykając je, zanim będą mogły zostać wykorzystane na zewnątrz. Im bardziej kuszący cel, tym większe prawdopodobieństwo, że wieczne podmioty będą próbowały go wykorzystać, a na świecie jest kilka celów bardziej kuszących niż platforma Azure.

## <a name="monitoring"></a>Monitorowanie

Jeśli osoba atakująca próbuje przeniknąć do aplikacji, powinno być pewne ostrzeżenie. Często ataki można zauważyć, badając dzienniki z usług. Ataki pozostawiają znaki ostrzegawcze, które można dostrzec, zanim się powiedzą. Na przykład osoba atakująca próbująca odgadnąć hasło spowoduje wiele żądań do systemu logowania. Monitorowanie wokół systemu logowania można wykryć dziwne wzorce, które są niezgodne z typowym wzorcem dostępu. To monitorowanie można przekształcić w alert, który z kolei może ostrzegać osobę operacji, aby aktywować jakiś mechanizm zaradczy. Bardzo dojrzały system monitorowania może nawet podjąć działania w oparciu o te odchylenia proaktywnie dodając reguły do blokowania żądań lub ograniczania odpowiedzi.

## <a name="securing-the-build"></a>Zabezpieczanie kompilacji

Jednym z miejsc, gdzie bezpieczeństwo jest często pomijane jest wokół procesu kompilacji. Nie tylko należy uruchomić kontroli zabezpieczeń kompilacji, takich jak skanowanie w poszukiwaniu niezabezpieczonych kodu lub poświadczeń zaewidencjonowanych, ale sama kompilacja powinna być bezpieczna. Jeśli serwer kompilacji zostanie naruszony, zapewnia fantastyczny wektor do wprowadzenia dowolnego kodu do produktu.

Wyobraź sobie, że osoba atakująca chce ukraść hasła osób logujących się do aplikacji internetowej. Mogą wprowadzić krok kompilacji, który modyfikuje wyewidencjonowany kod, aby dublować wszelkie żądania logowania na innym serwerze. Następnym razem kod przechodzi przez kompilacji, jest po cichu aktualizowane. Skanowanie luki w zabezpieczeniach kodu źródłowego nie spowoduje jej wyładania, ponieważ jest uruchamiane przed kompilacją. Podobnie nikt nie złapie go w przeglądzie kodu, ponieważ kroki kompilacji na żywo na serwerze kompilacji. Wykorzystany kod trafi do produkcji, gdzie może zbierać hasła. Prawdopodobnie nie ma żadnego dziennika inspekcji zmian w procesie kompilacji lub przynajmniej nikt nie monitoruje inspekcji.

Jest to doskonały przykład pozornie niskiej wartości docelowej, która może być użyta do włamania do systemu. Gdy osoba atakująca naruszy obwód systemu, może rozpocząć pracę nad znalezieniem sposobów podniesienia swoich uprawnień do tego stopnia, że może wyrządzić prawdziwą szkodę w dowolnym miejscu.

## <a name="building-secure-code"></a>Tworzenie bezpiecznego kodu

.NET Framework jest już dość bezpieczną strukturą. Unika niektórych pułapek niezarządzanego kodu, takich jak chodzenie poza końcami tablic. Aktywnie wykonuje się prace nad naprawą luk w zabezpieczeniach w miarę ich odkrywania. Istnieje nawet [program nagród za błędy,](https://www.microsoft.com/msrc/bounty) który płaci naukowcom za znalezienie problemów w ramach i zgłosić je zamiast je wykorzystywać.

Istnieje wiele sposobów, aby kod platformy .NET był bezpieczniejszy. Następujące wytyczne, takie jak [bezpieczne kodowania wskazówki dla .NET](https://docs.microsoft.com/dotnet/standard/security/secure-coding-guidelines) artykuł jest rozsądnym krokiem do podjęcia, aby upewnić się, że kod jest bezpieczny od podstaw. [OWASP top 10](https://owasp.org/www-project-top-ten/) jest inny nieoceniony przewodnik do tworzenia bezpiecznego kodu.

Proces kompilacji jest dobrym miejscem do umieszczenia narzędzi skanujących do wykrywania problemów w kodzie źródłowym, zanim dojdą do produkcji. Większość każdego projektu ma zależności od niektórych innych pakietów. Narzędzie, które można skanować w poszukiwaniu przestarzałych pakietów, spowoduje problemy w nocnej kompilacji. Nawet podczas tworzenia obrazów platformy Docker warto sprawdzić i upewnić się, że obraz podstawowy nie ma znanych luk w zabezpieczeniach. Inną rzeczą do sprawdzenia jest to, że nikt nie przypadkowo zaewidencjonował poświadczeń.

## <a name="built-in-security"></a>Wbudowane zabezpieczenia

Platforma Azure została zaprojektowana w celu zrównoważenia użyteczności i zabezpieczeń dla większości użytkowników. Różni użytkownicy będą mieli różne wymagania dotyczące zabezpieczeń, więc muszą dostosować swoje podejście do zabezpieczeń w chmurze. Firma Microsoft publikuje wiele informacji o zabezpieczeniach w [Centrum zaufania](https://azure.microsoft.com/support/trust-center/). Ten zasób powinien być pierwszym przystankiem dla tych specjalistów zainteresowanych zrozumieniem, jak działają wbudowane technologie łagodzenia ataków.

W witrynie Azure [portal, Usługa Azure Advisor](https://azure.microsoft.com/services/advisor/) to system, który stale skanuje środowisko i wydaje zalecenia. Niektóre z tych zaleceń są przeznaczone do oszczędzania pieniędzy użytkowników, ale inne są przeznaczone do identyfikowania potencjalnie niezabezpieczonych konfiguracji, takich jak posiadanie kontenera magazynu otwartego na świat i nie chronionego przez sieć wirtualną.

## <a name="azure-network-infrastructure"></a>Infrastruktura sieci platformy Azure

W lokalnym środowisku wdrażania duża ilość energii jest przeznaczona na tworzenie sieci. Konfigurowanie routerów, przełączników i taka jest skomplikowana praca. Sieci umożliwiają niektórym zasobom rozmawianie z innymi zasobami i w niektórych przypadkach uniemożliwiają dostęp. Częstą regułą sieci jest ograniczenie dostępu do środowiska produkcyjnego ze środowiska deweloperskiego na off szansa, że pół rozwinięty fragment kodu działa na opak i usuwa pokos danych.

Po wyjęciu z pudełka większość zasobów platformy PaaS Azure ma tylko najbardziej podstawową i permisywną konfigurację sieci. Na przykład każdy w Internecie może uzyskać dostęp do usługi aplikacji. Nowe wystąpienia programu SQL Server zazwyczaj są ograniczone, dzięki czemu zewnętrzne strony nie mogą uzyskać do nich dostępu, ale zakresy adresów IP używane przez samą platformę Azure są dozwolone za pośrednictwem. Tak, podczas gdy serwer SQL jest chroniony przed zagrożeniami zewnętrznymi, osoba atakująca musi tylko skonfigurować przyczółek platformy Azure, z którego może uruchamiać ataki na wszystkie wystąpienia SQL na platformie Azure.

Na szczęście większość zasobów platformy Azure można umieścić w sieci wirtualnej platformy Azure, która umożliwia lepszą kontrolę dostępu. Podobnie jak w przypadku sieci lokalnych, które ustanawiają sieci prywatne, które są chronione przed całym światem, sieci wirtualne są wyspami prywatnych adresów IP, które znajdują się w sieci platformy Azure.

![Rysunek 10-1 Sieć](./media/virtual-network.png)
wirtualna na**rysunku 10-1**platformy Azure . Sieć wirtualna na platformie Azure.

W ten sam sposób, w jaki sieci lokalne mają zaporę regulującą dostęp do sieci, można ustanowić podobną zaporę na granicy sieci wirtualnej. Domyślnie wszystkie zasoby w sieci wirtualnej mogą nadal rozmawiać z Internetem. To tylko połączenia przychodzące, które wymagają jakiejś formy jawnego wyjątku zapory.

Po ustanowieniu sieci zasoby wewnętrzne, takie jak konta magazynu, można skonfigurować tak, aby zezwalały tylko na dostęp przez zasoby, które są również w sieci wirtualnej. Ta zapora zapewnia dodatkowy poziom zabezpieczeń, gdyby klucze tego konta magazynu zostały ujawnione, osoby atakujące nie będą mogły połączyć się z nią w celu wykorzystania wyciekanych kluczy. Jest to kolejny przykład zasady najmniejszego przywileju.

Węzły w klastrze platformy Azure Kubernetes mogą uczestniczyć w sieci wirtualnej, podobnie jak inne zasoby, które są bardziej natywne dla platformy Azure. Ta funkcja nosi nazwę [interfejsu azure container networking.](https://github.com/Azure/azure-container-networking/blob/master/docs/cni.md) W efekcie przydziela podsieć w sieci wirtualnej, na której są przydzielane maszyny wirtualne i obrazy kontenerów.

Kontynuując ścieżkę ilustrowania zasady najmniejszych uprawnień, nie każdy zasób w sieci wirtualnej musi rozmawiać z każdym innym zasobem. Na przykład w aplikacji, która zapewnia internetowy interfejs API za pośrednictwem konta magazynu i bazy danych SQL, jest mało prawdopodobne, że baza danych i konto magazynu muszą ze sobą rozmawiać. Wszelkie udostępnianie danych między nimi będzie przejść za pośrednictwem aplikacji sieci web. Tak więc [sieciowej grupy zabezpieczeń (NSG)](https://docs.microsoft.com/azure/virtual-network/security-overview) może służyć do odmowy ruchu między tymi dwiema usługami.

Zasady odmawiania komunikacji między zasobami może być irytujące do zaimplementowania, zwłaszcza pochodzących z tła przy użyciu platformy Azure bez ograniczeń ruchu. W niektórych innych chmurach pojęcie grup zabezpieczeń sieci jest znacznie bardziej rozpowszechnione. Na przykład domyślną zasadą w udziale AWS jest to, że zasoby nie mogą komunikować się między sobą, dopóki nie są włączone przez reguły w sieciowej grupie sieciowej. Podczas gdy wolniej, aby to rozwinąć, bardziej restrykcyjne środowisko zapewnia bezpieczniejsze domyślne. Korzystanie z odpowiednich praktyk DevOps, zwłaszcza przy użyciu [usługi Azure Resource Manager lub Terraform](infrastructure-as-code.md) do zarządzania uprawnieniami może ułatwić kontrolowanie reguł.

Sieci wirtualne mogą być również przydatne podczas konfigurowania komunikacji między zasobami lokalnymi i chmurowymi. Wirtualna sieć prywatna może służyć do bezproblemowego łączenia dwóch sieci razem. Umożliwia to uruchamianie sieci wirtualnej bez jakiejkolwiek bramy dla scenariuszy, w których wszyscy użytkownicy są na miejscu. Istnieje wiele technologii, które mogą być wykorzystane do ustanowienia tej sieci. Najprostszym jest użycie [sieci VPN lokacji,](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#s2smulti) która może być ustanowiona między wieloma routerami a platformą Azure. Ruch jest szyfrowany i tunelowany przez Internet przy takim samym koszcie na bajt, jak każdy inny ruch. W scenariuszach, w których pożądane jest zwiększenie przepustowości lub więcej zabezpieczeń, platforma Azure oferuje usługę o nazwie [Express Route,](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways?toc=%2fazure%2fvirtual-network%2ftoc.json#ExpressRoute) która używa prywatnego obwodu między siecią lokalną a platformą Azure. Jest to bardziej kosztowne i trudne do ustalenia, ale także bezpieczniejsze.

## <a name="role-based-access-control-for-restricting-access-to-azure-resources"></a>Kontrola dostępu oparta na rolach w celu ograniczenia dostępu do zasobów platformy Azure

RBAC to system, który zapewnia tożsamość aplikacji uruchomionych na platformie Azure. Aplikacje mogą uzyskiwać dostęp do zasobów przy użyciu tej tożsamości zamiast lub oprócz używania kluczy lub haseł.

## <a name="security-principals"></a>Podmioty zabezpieczeń

Pierwszy składnik w RBAC jest podmiotem zabezpieczeń. Podmiot zabezpieczeń może być użytkownikiem, grupą, jednostką usługi lub tożsamością zarządzaną.

![Rysunek 10-2 Różne rodzaje](./media/rbac-security-principal.png)
zabezpieczeń**Rysunek 10-2**. Różne typy podmiotów zabezpieczeń.

- Użytkownik — każdy użytkownik, który ma konto w usłudze Azure Active Directory jest użytkownikiem.
- Grupa — kolekcja użytkowników z usługi Azure Active Directory. Jako członek grupy użytkownik wciela się w role tej grupy oprócz własnej.
- Podmiot usługi — tożsamość zabezpieczeń, w ramach której są uruchamiane usługi lub aplikacje.
- Tożsamość zarządzana — tożsamość usługi Azure Active Directory zarządzana przez platformę Azure. Tożsamości zarządzane są zazwyczaj używane podczas tworzenia aplikacji w chmurze, które zarządzają poświadczeniami do uwierzytelniania w usługach platformy Azure.

Podmiot zabezpieczeń można zastosować do większości dowolnego zasobu. Oznacza to, że można przypisać podmiot zabezpieczeń do kontenera uruchomionego w usłudze Azure Kubernetes, umożliwiając mu dostęp do wpisów tajnych przechowywanych w magazynie kluczy. Funkcja platformy Azure może mieć uprawnienia umożliwiające jej rozmawiać z wystąpieniem usługi Active Directory, aby sprawdzić poprawność JWT dla użytkownika wywołującego. Gdy usługi są włączone z jednostką usługi, ich uprawnienia mogą być zarządzane szczegółowo przy użyciu ról i zakresów.

## <a name="roles"></a>Role

Podmiot zabezpieczeń może przyjąć wiele ról lub, używając bardziej sartorial analogii, nosić wiele kapeluszy. Każda rola definiuje serię uprawnień, takich jak "Odczyt wiadomości z punktu końcowego usługi Azure Service Bus". Skuteczny zestaw uprawnień podmiotu zabezpieczeń to kombinacja wszystkich uprawnień przypisanych do wszystkich ról, które ma podmiot zabezpieczeń. Platforma Azure ma dużą liczbę wbudowanych ról, a użytkownicy mogą definiować własne role.

![Rysunek 10-3 definicje](./media/rbac-role-definition.png)
roli RBAC**Rysunek 10-3**. Definicje ról RBAC.

Wbudowane w platformę Azure są również szereg ról wysokiego poziomu, takich jak właściciel, współautor, czytnik i administrator konta użytkownika. Dzięki roli Właściciel podmiot zabezpieczeń może uzyskiwać dostęp do wszystkich zasobów i przypisywać uprawnienia innym osobom. Współautor ma ten sam poziom dostępu do wszystkich zasobów, ale nie może przypisać uprawnień. Czytnik może wyświetlać tylko istniejące zasoby platformy Azure, a administrator konta użytkownika może zarządzać dostępem do zasobów platformy Azure.

Bardziej szczegółowe wbudowane role, takie jak [dns zone contributor](https://docs.microsoft.com/azure/role-based-access-control/built-in-roles#dns-zone-contributor) mają prawa ograniczone do jednej usługi. Podmioty zabezpieczeń mogą przyjąć dowolną liczbę ról.

## <a name="scopes"></a>Zakresy

Role można zastosować do ograniczonego zestawu zasobów na platformie Azure. Na przykład stosując zakres do poprzedniego przykładu odczytu z kolejki usługi Service Bus, można zawęzić `blah.servicebus.windows.net/queue1`uprawnienia do pojedynczej kolejki: "Odczyt wiadomości z punktu końcowego usługi Azure Service Bus"

Zakres może być tak wąski, jak pojedynczy zasób lub może być stosowany do całej grupy zasobów, subskrypcji, a nawet grupy zarządzania.

Podczas testowania, jeśli podmiot zabezpieczeń ma pewne uprawnienia, kombinacja roli i zakresu są brane pod uwagę. Ta kombinacja zapewnia potężny mechanizm autoryzacji.

## <a name="deny"></a>Zablokuj

Wcześniej tylko reguły "zezwalaj" były dozwolone dla RBAC. To zachowanie sprawiło, że niektóre zakresy skomplikowane do kompilacji. Na przykład zezwalając podmiotowi zabezpieczeń na dostęp do wszystkich kont magazynu z wyjątkiem jednego wymaganego udzielenia jawnego uprawnienia do potencjalnie nieskończonej listy kont magazynu. Za każdym razem, gdy utworzono nowe konto magazynu, musiałoby ono zostać dodane do tej listy kont. To dodatkowe koszty zarządzania, które z pewnością nie było pożądane.

Reguły odmowy mają pierwszeństwo przed regułami zezwalania. Teraz reprezentujący ten sam zakres "zezwalaj na wszystko oprócz jednego" może być reprezentowany jako dwie reguły "zezwalaj wszystkim" i "odmów tego konkretnego". Odmów reguł nie tylko ułatwiaj zarządzanie, ale zezwalaj na zasoby, które są bardzo bezpieczne, odmawiając dostępu wszystkim.

## <a name="checking-access"></a>Sprawdzanie dostępu

Jak można sobie wyobrazić, posiadanie dużej liczby ról i zakresów może sprawić, że znalezienie skutecznego uprawnienia jednostki usługi jest dość trudne. Palowanie zaprzeczyć zasady na szczycie tego, służy tylko do zwiększenia złożoności. Na szczęście istnieje kalkulator uprawnień, który może wyświetlać skuteczne uprawnienia dla dowolnego podmiotu usługi. Zazwyczaj znajduje się w zakładce IAM w portalu, jak pokazano na rysunku 10-3.

![Rysunek 10-4 Kalkulator uprawnień](./media/check-rbac.png)
dla usługi aplikacji**Rysunek 10-4**. Kalkulator uprawnień dla usługi aplikacji.

## <a name="securing-secrets"></a>Zabezpieczanie wpisów tajnych

Hasła i certyfikaty są częstym wektorem ataku dla atakujących. Sprzęt do łamania haseł może zrobić brutalny atak i spróbować odgadnąć miliardy haseł na sekundę. Dlatego ważne jest, aby hasła używane do uzyskiwania dostępu do zasobów były silne, z dużą różnorodnością znaków. Te hasła są dokładnie tego rodzaju haseł, które są prawie niemożliwe do zapamiętania. Na szczęście hasła na platformie Azure w rzeczywistości nie muszą być znane przez żadnego człowieka.

Wielu [ekspertów w dziedzinie](https://www.troyhunt.com/password-managers-dont-have-to-be-perfect-they-just-have-to-be-better-than-not-having-one/) bezpieczeństwa sugeruje, że najlepszym rozwiązaniem jest używanie menedżera haseł do przechowywania własnych haseł. Podczas gdy centralizuje hasła w jednej lokalizacji, pozwala również na używanie bardzo złożonych haseł i zapewnia, że są unikatowe dla każdego konta. Ten sam system istnieje w ramach platformy Azure: centralny magazyn wpisów tajnych.

## <a name="azure-key-vault"></a>W usłudze Azure Key Vault

Usługa Azure Key Vault zapewnia scentralizowaną lokalizację do przechowywania haseł do takich rzeczy, jak bazy danych, klucze interfejsu API i certyfikaty. Gdy tajny zostanie wprowadzony do Skarbca, nigdy więcej nie zostanie pokazany, a polecenia do wyodrębnienia i wyświetlenia są celowo skomplikowane. Informacje w sejfie są chronione za pomocą szyfrowania programowego lub zatwierdzonych przez FIPS 140-2 Hardware Security Modules.

Dostęp do magazynu kluczy jest zapewniany za pośrednictwem rbaców, co oznacza, że nie tylko każdy użytkownik może uzyskać dostęp do informacji w przechowalni. Powiedzmy, że aplikacja sieci web chce uzyskać dostęp do ciągu połączenia bazy danych przechowywanego w usłudze Azure Key Vault. Aby uzyskać dostęp, aplikacje muszą działać przy użyciu jednostki usługi. W ramach tej zakładanej roli mogą odczytywać sekrety z sejfu. Istnieje wiele różnych ustawień zabezpieczeń, które mogą dodatkowo ograniczyć dostęp aplikacji do magazynu, dzięki czemu nie można zaktualizować wpisów tajnych, ale tylko je odczytać.

Dostęp do magazynu kluczy można monitorować, aby upewnić się, że tylko oczekiwane aplikacje uzyskują dostęp do magazynu. Dzienniki można zintegrować z powrotem do usługi Azure Monitor, odblokowując możliwość konfigurowania alertów, gdy wystąpią nieoczekiwane warunki.

## <a name="kubernetes"></a>Kubernetes

W usłudze Kubernetes istnieje podobna usługa do utrzymywania małych tajnych informacji. Wpisy tajne kubernetes można `kubectl` ustawić za pomocą typowego pliku wykonywalnego.

Tworzenie klucza tajnego jest tak proste, jak znalezienie wersji base64 wartości, które mają być przechowywane:

```console
echo -n 'admin' | base64
YWRtaW4=
echo -n '1f2d1e2e67df' | base64
MWYyZDFlMmU2N2Rm
```

Następnie dodanie go do `secret.yml` pliku wpisów tajnych o nazwie na przykład, który wygląda podobnie do następującego przykładu:

```yml
apiVersion: v1
kind: Secret
metadata:
  name: mysecret
type: Opaque
data:
  username: YWRtaW4=
  password: MWYyZDFlMmU2N2Rm
```

Na koniec ten plik można załadować do kubernetes, uruchamiając następujące polecenie:

```console
kubectl apply -f ./secret.yaml
```

Te wpisy tajne mogą być następnie montowane w woluminach lub narażone na procesy kontenera za pośrednictwem zmiennych środowiskowych. [Podejście aplikacji dwunastocelię](https://12factor.net/) do tworzenia aplikacji sugeruje użycie najniższego wspólnego mianownika do przesyłania ustawień do aplikacji. Zmienne środowiskowe są najniższym wspólnym mianownikiem, ponieważ są obsługiwane bez względu na system operacyjny lub aplikację.

Alternatywą dla korzystania z wbudowanych wpisów tajnych kubernetes jest dostęp do wpisów tajnych w usłudze Azure Key Vault z poziomu usługi Kubernetes. Najprostszym sposobem, aby to zrobić, jest przypisanie roli RBAC do kontenera, który chce załadować wpisy tajne. Aplikacja może następnie użyć interfejsów API usługi Azure Key Vault, aby uzyskać dostęp do wpisów tajnych. Jednak takie podejście wymaga modyfikacji kodu i nie jest zgodne ze wzorcem przy użyciu zmiennych środowiskowych. Zamiast tego można wstrzyknąć wartości do kontenera za pomocą [wtryskiwacza usługi Azure Key Vault.](https://mrdevops.io/introducing-azure-key-vault-to-kubernetes-931f82364354) Takie podejście jest rzeczywiście bardziej bezpieczne niż przy użyciu wpisów tajnych Kubernetes bezpośrednio, ponieważ mogą one być dostępne dla użytkowników w klastrze.

## <a name="encryption-in-transit-and-at-rest"></a>Szyfrowanie podczas przesyłania i odpoczynku

Zapewnienie bezpieczeństwa danych jest ważne, niezależnie od tego, czy są dostępne na dysku, czy między różnymi usługami. Najskuteczniejszym sposobem na nieszczelnienie danych jest zaszyfrowanie ich do formatu, który nie może być łatwo odczytany przez innych. Platforma Azure obsługuje szeroką gamę opcji szyfrowania.

### <a name="in-transit"></a>Przesyłanie

Istnieje kilka sposobów szyfrowania ruchu w sieci na platformie Azure. Dostęp do usług platformy Azure jest zazwyczaj wykonywane za pomocą połączeń, które używają zabezpieczeń warstwy transportu (TLS). Na przykład wszystkie połączenia z interfejsami API platformy Azure wymagają połączeń TLS. Podobnie połączenia z punktami końcowymi w magazynie platformy Azure mogą być ograniczone do pracy tylko za pomocą połączeń szyfrowanych TLS.

Protokół TLS jest skomplikowanym protokołem i po prostu wiedząc, że połączenie używa TLS nie jest wystarczające do zapewnienia bezpieczeństwa. Na przykład TLS 1.0 jest chronicznie niebezpieczny, a TLS 1.1 nie jest dużo lepszy. Nawet w wersjach protokołu TLS istnieją różne ustawienia, które mogą ułatwić odszyfrowanie połączeń. Najlepszym sposobem działania jest sprawdzenie i sprawdzenie, czy połączenie z serwerem używa aktualnych i dobrze skonfigurowanych protokołów.

Ten test może być wykonany przez usługę zewnętrzną, taką jak test serwera SSL laboratoriów SSL laboratoriów. Test uruchamiany względem punktu końcowego typowej platformy Azure, w tym przypadku punktu końcowego magistrali usług, daje prawie doskonały wynik A.

Nawet usługi, takie jak bazy danych SQL platformy Azure, używają szyfrowania TLS do ukrywania danych. Interesującą częścią szyfrowania przesyłanych danych przy użyciu protokołu TLS jest to, że nawet microsoft nie jest w stanie nasłuchiwać połączenia między komputerami z systemem TLS. Powinno to zapewnić komfort zainteresowanych firm, że ich dane mogą być zagrożone przez firmę Microsoft właściwego lub nawet podmiotu państwowego z więcej zasobów niż standardowy atakujący.

![Rysunek 10-5 SSL labs raport pokazujący wynik A dla punktu końcowego usługi Service Bus. ](./media/ssl-report.png)
 **Rysunek 10-5**. Raporty laboratoriów SSL pokazujące wynik A dla punktu końcowego usługi Service Bus.

Chociaż ten poziom szyfrowania nie będzie wystarczający przez cały czas, powinno to wzbudzić pewność, że połączenia TLS platformy Azure są dość bezpieczne. Platforma Azure będzie nadal rozwijać swoje standardy zabezpieczeń w miarę poprawy szyfrowania. Miło jest wiedzieć, że ktoś obserwuje standardy zabezpieczeń i aktualizuje platformę Azure w miarę ich ulepszania.

### <a name="at-rest"></a>Magazynowanie

W każdej aplikacji istnieje wiele miejsc, w których dane spoczywają na dysku. Sam kod aplikacji jest ładowany z niektórych mechanizmów magazynowania. Większość aplikacji korzysta również z pewnego rodzaju bazy danych, takich jak SQL Server, Cosmos DB, a nawet niezwykle efektywnego cenowo magazynu tabel. Wszystkie te bazy danych używają mocno zaszyfrowanego magazynu, aby upewnić się, że nikt inny niż aplikacje z odpowiednimi uprawnieniami może odczytać dane. Nawet operatorzy systemu nie mogą odczytać zaszyfrowanych danych. Dzięki czemu klienci mogą pozostać pewni, że ich tajne informacje pozostają tajne.

### <a name="storage"></a>Magazyn

Podstawą dużej części platformy Azure jest aparat usługi Azure Storage. Dyski maszyn wirtualnych są instalowane na górze usługi Azure Storage. Usługi Azure Kubernetes są uruchamiane na maszynach wirtualnych, które same są hostowane w usłudze Azure Storage. Nawet bezserwerowych technologii, takich jak usługi Azure Functions Apps i wystąpienia kontenerów platformy Azure, zabraknie dysku, który jest częścią usługi Azure Storage.

Jeśli usługa Azure Storage jest dobrze zaszyfrowana, zapewnia podstawę dla większości innych, które również mają być szyfrowane. Usługa Azure Storage [jest szyfrowana](https://docs.microsoft.com/azure/storage/common/storage-service-encryption) za pomocą [256-bitowego systemu AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)zgodnego ze standardem [FIPS 140-2.](https://en.wikipedia.org/wiki/FIPS_140) Jest to dobrze postrzegana technologia szyfrowania, która była przedmiotem szeroko zakrojonej kontroli akademickiej w ciągu ostatnich 20 lat. Obecnie nie ma znanego praktycznego ataku, który pozwoliłby komuś bez znajomości klucza odczytywać dane zaszyfrowane przez AES.

Domyślnie klucze używane do szyfrowania usługi Azure Storage są zarządzane przez firmę Microsoft. Istnieją rozbudowane zabezpieczenia w celu zapewnienia, aby zapobiec złośliwemu dostępowi do tych kluczy. Jednak użytkownicy z określonymi wymaganiami szyfrowania mogą również [zapewnić własne klucze magazynu,](https://docs.microsoft.com/azure/storage/common/storage-encryption-keys-powershell) które są zarządzane w usłudze Azure Key Vault. Klucze te można odwołać w dowolnym momencie, co skutecznie uczynić zawartość konta Magazynu przy użyciu ich niedostępne.

Maszyny wirtualne używają zaszyfrowanego magazynu, ale możliwe jest zapewnienie innej warstwy szyfrowania przy użyciu technologii, takich jak Funkcja BitLocker w systemie Windows lub DM-Crypt w systemie Linux. Technologie te oznaczają, że nawet jeśli obraz dysku wyciekł z pamięci masowej, jego odczytanie pozostanie prawie niemożliwe.

### <a name="azure-sql"></a>Azure SQL

Bazy danych hostowane w usłudze Azure SQL używają technologii o nazwie [Transparent Data Encryption (TDE),](/sql/relational-databases/security/encryption/transparent-data-encryption) aby zapewnić, że dane pozostają zaszyfrowane. Jest domyślnie włączona we wszystkich nowo utworzonych bazach danych SQL, ale musi być włączona ręcznie dla starszych baz danych. TDE wykonuje szyfrowanie w czasie rzeczywistym i odszyfrowywanie nie tylko bazy danych, ale także kopii zapasowych i dzienników transakcji.

Parametry szyfrowania są `master` przechowywane w bazie danych i podczas uruchamiania są odczytywane do pamięci dla pozostałych operacji. Oznacza to, `master` że baza danych musi pozostać niezaszyfrowana. Rzeczywisty klucz jest zarządzany przez firmę Microsoft. Jednak użytkownicy z wymagających wymagań zabezpieczeń może zapewnić własny klucz w usłudze Key Vault w taki sam sposób, jak to zrobić dla usługi Azure Storage. Magazyn kluczy zapewnia takie usługi, jak obracanie kluczy i odwoływanie.

"Przezroczysta" część TDS wynika z faktu, że nie ma zmian klienta potrzebnych do korzystania z zaszyfrowanej bazy danych. Takie podejście zapewnia dobre zabezpieczenia, wyciek hasła bazy danych wystarczy, aby użytkownicy mogli odszyfrować dane. Istnieje inne podejście, które szyfruje poszczególne kolumny lub tabele w bazie danych. [Zawsze zaszyfrowane](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted-azure-key-vault) zapewnia, że w żadnym momencie zaszyfrowane dane są wyświetlane w postaci zwykłego tekstu wewnątrz bazy danych.

Konfigurowanie tej warstwy szyfrowania wymaga uruchomienia za pomocą kreatora w programie SQL Server Management Studio, aby wybrać rodzaj szyfrowania i miejsce przechowywania skojarzonych kluczy w ucho w magazynie kluczy.

![Rysunek 10-6 Wybieranie kolumn w tabeli do](./media/always-encrypted.png)
zaszyfrowania przy użyciu zawsze zaszyfrowanego**rysunku 10-6**. Wybieranie kolumn w tabeli, które mają być szyfrowane przy użyciu opcji Zawsze zaszyfrowane.

Aplikacje klienckie, które odczytują informacje z tych zaszyfrowanych kolumn, muszą wprowadzać specjalne dodatki do odczytu zaszyfrowanych danych. Parametry połączenia muszą zostać `Column Encryption Setting=Enabled` zaktualizowane, a poświadczenia klienta muszą być pobierane z magazynu kluczy. Klient programu SQL Server musi być następnie zagruntowany kluczami szyfrowania kolumny. Po wykonaniu tej czynności pozostałe akcje używają standardowych interfejsów do klienta SQL. Oznacza to, że narzędzia takie jak Dapper i Entity Framework, które są zbudowane na kliencie SQL, będą nadal działać bez zmian. Zawsze zaszyfrowane może nie być jeszcze dostępne dla każdego sterownika programu SQL Server w każdym języku.

Połączenie TDE i Always Encrypted, które mogą być używane z kluczami specyficznymi dla klienta, zapewnia obsługę nawet najbardziej wymagających wymagań szyfrowania.

### <a name="cosmos-db"></a>Cosmos DB

Usługa Cosmos DB to najnowsza baza danych dostarczona przez firmę Microsoft na platformie Azure. Został zbudowany od podstaw z myślą o bezpieczeństwie i kryptografii. Szyfrowanie AES-256bit jest standardem dla wszystkich baz danych usługi Cosmos DB i nie można go wyłączyć. W połączeniu z tls 1.2 wymagania dotyczące komunikacji, całe rozwiązanie pamięci masowej jest szyfrowany.

![Rysunek 10-7 Przepływ szyfrowania danych](./media/cosmos-encryption.png)
w usłudze Cosmos DB**Rysunek 10-7**. Przepływ szyfrowania danych w usłudze Cosmos DB.

Chociaż usługa Cosmos DB nie zapewnia dostarczania kluczy szyfrowania klienta, zespół wykonał znaczną pracę, aby upewnić się, że bez tego jest zgodny z PCI-DSS. Usługa Cosmos DB również nie obsługuje żadnego rodzaju szyfrowania pojedynczej kolumny podobne do zawsze zaszyfrowane sql azure.

## <a name="keeping-secure"></a>Dbanie o bezpieczeństwo

Platforma Azure ma wszystkie narzędzia niezbędne do wydania wysoce bezpiecznego produktu. Jednak łańcuch jest tak silny, jak jego najsłabsze ogniwo. Jeśli aplikacje wdrożone na platformie Azure nie są opracowywane przy zastosowaniu odpowiedniego sposobu myślenia o zabezpieczeniach i dobrych inspekcji zabezpieczeń, stają się słabym ogniwem w łańcuchu. Istnieje wiele dużych narzędzi analizy statycznej, bibliotek szyfrowania i praktyk zabezpieczeń, które mogą służyć do zapewnienia, że oprogramowanie zainstalowane na platformie Azure jest tak bezpieczne, jak sama platforma Azure. Przykłady obejmują [narzędzia analizy statycznej,](https://www.whitesourcesoftware.com/) [biblioteki szyfrowania](https://www.libressl.org/)i [praktyki zabezpieczeń.](https://azure.microsoft.com/resources/videos/red-vs-blue-internal-security-penetration-testing-of-microsoft-azure/)

>[!div class="step-by-step"]
>[Poprzedni](security.md)
>[następny](devops.md)
