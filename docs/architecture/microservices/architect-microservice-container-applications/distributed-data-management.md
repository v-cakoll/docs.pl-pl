---
title: Wyzwania i rozwiązania dotyczące rozproszonego zarządzania danymi
description: Zapoznaj się z wyzwaniami i rozwiązaniami dotyczącymi rozproszonego zarządzania danymi na świecie mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: c30de24591d5a73fd34087f34a69e9c7ed54cd35
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834457"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Wyzwania i rozwiązania dotyczące rozproszonego zarządzania danymi

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Wyzwanie \#1: jak definiować granice każdej mikrousługi

Definiowanie granic mikrousług jest prawdopodobnie pierwszym wyzwaniem. Każda mikrousługa musi być częścią aplikacji, a każda mikrousługa powinna być autonomiczna ze wszystkimi korzyściami i wyzwaniami, które przekazuje. Ale jak zidentyfikować te granice?

Najpierw należy skoncentrować się na modelach domeny logicznej aplikacji i powiązanych danych. Spróbuj zidentyfikować oddzielone Wyspy danych i różne konteksty w tej samej aplikacji. Każdy kontekst może mieć inny język biznesowy (różne warunki biznesowe). Konteksty należy definiować i zarządzać niezależnie. Warunki i jednostki, które są używane w tych różnych kontekstach mogą wyglądać podobnie, ale można je wykryć w określonym kontekście, pojęcie biznesowe z jedną z nich jest używane do innego celu w innym kontekście i może nawet mieć inną nazwę. Na przykład użytkownik może być określony jako użytkownik w kontekście tożsamości lub członkostwa, jako klient w kontekście programu CRM, jako kupujący w kontekście porządkowania i tak dalej.

Sposób identyfikacji granic między wieloma kontekstami aplikacji z inną domeną dla każdego kontekstu to dokładne określenie granic dla każdej mikrousługi biznesowej i powiązanego modelu domeny i danych. Zawsze należy podjąć próbę zminimalizowania sprzęgu między tymi mikrousługami. Ten przewodnik zawiera bardziej szczegółowe informacje o tej identyfikacji i projekcie modelu domeny w sekcji [Identyfikowanie granic modelu domeny dla każdej mikrousługi](identify-microservice-domain-model-boundaries.md) później.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Wyzwanie \#2: jak tworzyć zapytania, które pobierają dane z kilku mikrousług

Drugim wyzwaniem jest zaimplementowanie zapytań, które pobierają dane z kilku mikrousług, jednocześnie unikając komunikacji między mikrousługami ze zdalnych aplikacji klienckich. Przykładem może być pojedynczy ekran z poziomu aplikacji mobilnej, który musi zawierać informacje o użytkowniku, którego właścicielem jest koszyk, katalog i mikrousługi tożsamości użytkowników. Innym przykładem jest złożony raport obejmujący wiele tabel znajdujących się w wielu mikrousługach. Odpowiednie rozwiązanie zależy od złożoności zapytań. Jednak w dowolnym przypadku trzeba będzie mieć możliwość agregowania informacji, jeśli chcesz zwiększyć efektywność komunikacji w systemie. Poniżej przedstawiono najpopularniejsze rozwiązania.

**Brama interfejsu API.** W przypadku prostej agregacji danych z wielu mikrousług należących do różnych baz danych Zalecanym podejściem jest mikrousługa agregacji, nazywana bramą interfejsu API. Należy jednak zachować ostrożność podczas implementowania tego wzorca, ponieważ może to być punkt podlewka w systemie i może naruszać zasadę autonomii mikrousług. Aby wyeliminować tę możliwość, można mieć wiele bram interfejsów API z ograniczeniami, które koncentrują się na pionowych "wycinkach" lub w obszarze roboczym systemu. Wzorzec bramy interfejsu API został wyjaśniony bardziej szczegółowo w [sekcji bramy interfejsu API](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) .

**CQRS z tabelami zapytań/odczytów.** Innym rozwiązaniem do agregowania danych z wielu mikrousług jest [wzorzec widoku materiału](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). W tej metodzie generowane są z góry (przygotowanie nieznormalizowanych danych przed rzeczywistymi zapytania), tabela tylko do odczytu z danymi należącymi do wielu mikrousług. Tabela ma format odpowiedni dla potrzeb aplikacji klienta.

Rozważ coś takiego jak ekran aplikacji mobilnej. Jeśli masz pojedynczą bazę danych, możesz ściągnąć dane dla tego ekranu za pomocą zapytania SQL, które wykonuje złożone sprzężenie obejmujące wiele tabel. Jeśli jednak masz wiele baz danych, a każda baza danych jest własnością innej mikrousługi, nie można wykonać zapytania o te bazy danych i utworzyć sprzężenia SQL. Zapytanie złożone jest wyzwaniem. Wymagania można rozwiązać przy użyciu podejścia CQRSego — można utworzyć nieznormalizowaną tabelę w innej bazie danych, która jest używana tylko w przypadku zapytań. Tabela może być zaprojektowana specjalnie dla danych, które są potrzebne dla zapytania złożonego, z relacją jeden do jednego między polami wymaganymi przez ekran aplikacji a kolumnami w tabeli zapytania. Może również być używany do celów raportowania.

Takie podejście nie tylko rozwiązuje pierwotny problem (jak wysyłać zapytania i sprzęgać je na mikrousługi), ale również znacznie zwiększa wydajność w porównaniu z złożonym sprzężeniem, ponieważ masz już dane wymagane przez aplikację w tabeli zapytań. Oczywiście korzystanie z Command and Query Responsibility Segregation (CQRS) z tabelami zapytań/odczytów oznacza dodatkowe prace programistyczne i konieczność zapewnienia spójności ostatecznej. Niemniej jednak wymagania dotyczące wydajności i wysokiej skalowalności w [scenariuszach współpracy](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (lub scenariuszach konkurencyjnych, w zależności od punktu widzenia) to miejsce, w którym należy zastosować CQRS z wieloma bazami danych.

**"Zimne dane" w centralnych bazach danych.** W przypadku złożonych raportów i zapytań, które mogą nie wymagać danych w czasie rzeczywistym, typowym podejściem jest wyeksportowanie "gorące dane" (dane transakcyjne z mikrousług) jako "zimne dane" do dużych baz danych, które są używane tylko na potrzeby raportowania. System centralnej bazy danych może być opartym na danych Big systemowym, takim jak Hadoop, magazynem danych, takim jak serwer, na podstawie Azure SQL Data Warehouse, a nawet z pojedynczą bazą danych SQL, która jest używana tylko do raportów (Jeśli rozmiar nie będzie problemem).

Należy pamiętać, że ta Scentralizowana baza danych byłaby używana tylko w przypadku zapytań i raportów, które nie wymagają danych w czasie rzeczywistym. Oryginalne aktualizacje i transakcje, jako źródło prawdy, muszą znajdować się w danych mikrousług. Aby synchronizować dane, można użyć komunikacji opartej na zdarzeniach (podanej w następnych sekcjach) lub przy użyciu innych narzędzi do importowania/eksportowania infrastruktury bazy danych. W przypadku korzystania z komunikacji opartej na zdarzeniach proces integracji będzie podobny do sposobu propagowania danych zgodnie z wcześniejszym opisem dla tabel zapytań CQRS.

Jeśli jednak projekt aplikacji obejmuje stałe agregowanie informacji z wielu mikrousług dla złożonych zapytań, może to być objawem nieprawidłowego projektu — mikrousługa powinna być tak izolowana jak to możliwe z innych mikrousług. (Spowoduje to wykluczenie raportów/analiz, które zawsze powinny korzystać z scentralizowanych centralnych baz danych). Występowanie tego problemu często może być przyczyną scalania mikrousług. Należy zrównoważyć autonomię ewolucji i wdrożenia każdej mikrousługi przy użyciu silnych zależności, spójności i agregacji danych.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Wyzwanie \#3: jak zapewnić spójność w wielu mikrousługach

Jak wspomniano wcześniej, dane należące do każdej mikrousługi są prywatne dla tej mikrousługi i można uzyskać do nich dostęp tylko przy użyciu interfejsu API mikrousług. Z tego względu zaprezentowano wyzwanie polegające na implementacji kompleksowych procesów firmy przy zachowaniu spójności w wielu mikrousługach.

Aby przeanalizować ten problem, przyjrzyjmy się przykładowi z [aplikacji eShopOnContainers Reference](https://aka.ms/eshoponcontainers). Mikrousługa katalogu przechowuje informacje o wszystkich produktach, w tym o cenie produktu. Mikrousługa koszyka zarządza danymi czasowymi dotyczącymi elementów produktu, które użytkownicy są dodawani do koszyków zakupów, co obejmuje cenę elementów w momencie dodania ich do koszyka. Gdy cena produktu jest aktualizowana w katalogu, Cena ta powinna być również aktualizowana w przypadku aktywnych koszyków, w których znajduje się ten sam produkt, a system powinien prawdopodobnie ostrzegać użytkownika o tym, że cena określonego elementu zmieniła się od dodania do koszyka.

W hipotetycznej wersji monolitycznej tej aplikacji po zmianie ceny w tabeli Products podsystem wykazu może po prostu użyć transakcji KWASowej do zaktualizowania bieżącej ceny w tabeli koszyka.

Jednak w aplikacji opartej na mikrousługach tabele produktów i koszyka są własnością odpowiednich mikrousług. Żadna mikrousługa nie powinna obejmować tabel/magazynów należących do innej mikrousług w swoich własnych transakcjach, a nie nawet zapytań bezpośrednich, jak pokazano na rysunku 4-9.

![Diagram przedstawiający, że dane bazy danych mikrousług nie mogą być udostępniane.](./media/distributed-data-management/indepentent-microservice-databases.png)

**Rysunek 4-9**. Mikrousługa nie może bezpośrednio uzyskać dostępu do tabeli w innej mikrousłudze

Mikrousługa katalogu nie powinna aktualizować tabeli koszyka bezpośrednio, ponieważ jest ona własnością usługi koszyka. Aby przeprowadzić aktualizację mikrousługi koszyka, usługa Catalog powinna korzystać z spójności ostatecznej na podstawie komunikacji asynchronicznej, takiej jak zdarzenia integracji (komunikacja oparta na komunikatach i zdarzeniach). Jest to sposób, w jaki aplikacja referencyjna [eShopOnContainers](https://aka.ms/eshoponcontainers) wykonuje ten typ spójności na mikrousługach.

Jak określono w [theorem Cap](https://en.wikipedia.org/wiki/CAP_theorem), należy wybrać między dostępnością a silną SPÓJNOŚCIą kwaśną. Większość scenariuszy opartych na mikrousługach wymaga dostępności i wysokiej skalowalności w przeciwieństwie do silnej spójności. Aplikacje o znaczeniu krytycznym muszą pozostać w działaniu, a deweloperzy mogą obejść silną spójność przy użyciu technik do pracy z słabą lub bezprawną spójnością. Jest to podejście podejmowane przez większość architektur opartych na mikrousługach.

Ponadto w przypadku transakcji zatwierdzania w stylu KWASowym lub dwufazowym nie są one bezpośrednio związane z zasadami mikrousług. Większość baz danych NoSQL (takich jak Azure Cosmos DB, MongoDB itp.) nie obsługuje transakcji zatwierdzania dwuetapowego, typowych w scenariuszach dystrybuowanych baz danych. Jednak zachowanie spójności danych w ramach usług i baz danych jest niezbędne. To wyzwanie dotyczy również kwestii propagowania zmian w wielu mikrousługach, gdy pewne dane muszą być nadmiarowe, na przykład gdy trzeba mieć nazwę lub opis produktu w mikrousłudze wykazu i koszyku mikrousług.

Dobrym rozwiązaniem dla tego problemu jest użycie ostatecznej spójności między mikrousługami przegubowymi przy użyciu komunikacji opartej na zdarzeniach i systemu publikowania i subskrybowania. Te tematy zostały omówione w sekcji [asynchroniczna komunikacja oparta na zdarzeniach](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) w dalszej części tego przewodnika.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Wyzwanie \#4: jak projektować komunikację między granicami mikrousług

Komunikacja między granicami mikrousług jest rzeczywistym wyzwaniem. W tym kontekście komunikacja nie odnosi się do używanego protokołu (HTTP i REST, AMQP, Messaging itd.). Zamiast tego określa styl komunikacji, który powinien być używany, a zwłaszcza na to, jak to mikrousługi. W zależności od poziomu sprzęgu, gdy wystąpi awaria, wpływ tego błędu na system różni się znacznie.

W systemie rozproszonym, takim jak aplikacja oparta na mikrousługach, dzięki czemu wiele artefaktów porusza się wokół i z rozproszonymi usługami na wielu serwerach lub hostach, składniki zakończą się niepowodzeniem. Wystąpiły częściowe awarie i jeszcze większe przestoje, dlatego należy zaprojektować mikrousługi i komunikować się między nimi, biorąc pod uwagę typowe zagrożenia w tym typie rozproszonego systemu.

Popularnym podejściem jest implementowanie mikrousług opartych na protokole HTTP (REST), ze względu na ich prostotę. Podejście oparte na protokole HTTP jest doskonale akceptowalne; Ten problem jest związany z używaniem go. W przypadku korzystania z żądań i odpowiedzi HTTP tylko w celu współdziałania z mikrousługami z aplikacji klienckich lub bram interfejsu API jest to dokładne. Ale jeśli utworzysz długie łańcuchy synchronicznych wywołań HTTP na mikrousługach, komunikuje się w zależności od tego, czy mikrousługi były obiektami w aplikacji monolitycznej, aplikacja zostanie ostatecznie uruchomiona.

Załóżmy na przykład, że aplikacja kliencka wysyła wywołanie interfejsu API protokołu HTTP do pojedynczej mikrousługi, takiej jak mikrousługa porządkowania. Jeśli mikrousługa porządkowania w programie umożliwia wywoływanie dodatkowych mikrousług przy użyciu protokołu HTTP w ramach tego samego cyklu żądania/odpowiedzi, tworzysz łańcuch wywołań HTTP. Może to być rozsądnie uzasadnione. Istnieją jednak ważne kwestie, które należy wziąć pod uwagę podczas przechodzenia do tej ścieżki:

- Blokowanie i niska wydajność. Ze względu na synchroniczny charakter protokołu HTTP oryginalne żądanie nie otrzymuje odpowiedzi, dopóki nie zostaną zakończone wszystkie wewnętrzne wywołania HTTP. Załóżmy, że liczba tych wywołań rośnie znacznie i w tym samym czasie jedno z pośrednich wywołań HTTP do mikrousługi jest blokowane. Jest to wpływ na wydajność, a ogólna skalowalność będzie miała wykładniczy wpływ na wzrost liczby żądań HTTP.

- Mikrousługi sprzęgające przy użyciu protokołu HTTP. Mikrousługi biznesowe nie powinny być połączone z innymi mikrousługami biznesowymi. W idealnym przypadku nie należy wiedzieć o istnieniu innych mikrousług. Jeśli aplikacja korzysta z mikrousług sprzęgania, jak w przykładzie, osiągnięcie autonomii na mikrousług będzie niemal niemożliwe.

- Niepowodzenie w żadnej z mikrousług. W przypadku zaimplementowania łańcucha mikrousług połączonych przez wywołania HTTP, gdy dowolne mikrousługi nie powiedzie się (i ostatecznie nie będą działać), cały łańcuch mikrousług zakończy się niepowodzeniem. Systemy oparte na mikrousługach powinny być przeznaczone do dalszej pracy, a także w przypadku awarii częściowych. Nawet w przypadku implementowania logiki klienta, która używa ponowień w ramach funkcji wykładniczych wycofywania lub wyłączników, bardziej skomplikowane łańcuchy wywołań HTTP to bardziej skomplikowany sposób implementacji strategii niepowodzeń na podstawie protokołu HTTP.

W rzeczywistości, jeśli wewnętrzne mikrousługi komunikują się przez tworzenie łańcuchów żądań HTTP zgodnie z opisem, można zatwierdzić, że masz wbudowaną aplikację, ale jedną opartą na protokole HTTP między procesami.

W związku z tym w celu wymuszenia autonomii mikrousług i uzyskania lepszej odporności należy zminimalizować wykorzystanie łańcuchów komunikacji żądania/odpowiedzi między mikrousługami. Zaleca się używanie tylko asynchronicznej interakcji komunikacji między mikrousługą, przy użyciu asynchronicznej komunikacji komunikatów i zdarzeń albo za pomocą (asynchroniczne) sondowania HTTP niezależnie od oryginalnego żądania HTTP/ cykl odpowiedzi.

Korzystanie z komunikacji asynchronicznej jest wyjaśnione z dodatkowymi szczegółami w dalszej części tego przewodnika w sekcjach [asynchronicznej integracji mikrousług wymusza międzyusługową](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) i [asynchroniczną komunikację opartą na komunikatach](asynchronous-message-based-communication.md).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Cap theorem** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- @No__t **spójności ostatecznej**— 1
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- @No__t o **spójności danych**-1
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Fowlera Martin. CQRS (Command and Query Responsibility Segregation)**  \
  <https://martinfowler.com/bliki/CQRS.html>

- **Widok z materiałami** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles wiersz. Kwas a BASE: przesunięcie pH przetwarzania transakcji bazy danych** \
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **Kompensowanie transakcji** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **UDI Dahan. Składowe zorientowane na usługę** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[Poprzedni](logical-versus-physical-architecture.md)
>[dalej](identify-microservice-domain-model-boundaries.md)
