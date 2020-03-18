---
title: Problemy i rozwiązania dotyczące rozproszonego zarządzania danymi
description: Dowiedz się, jakie są wyzwania i rozwiązania dla zarządzania danymi rozproszonymi w świecie mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: c30de24591d5a73fd34087f34a69e9c7ed54cd35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834457"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Problemy i rozwiązania dotyczące rozproszonego zarządzania danymi

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Wyzwanie \#1: Jak zdefiniować granice każdej mikrousługi

Definiowanie granic mikrousług jest prawdopodobnie pierwszym wyzwaniem, z którym każdy napotka. Każda mikrousługa musi być elementem aplikacji i każda mikrousługa powinna być autonomiczna ze wszystkimi korzyściami i wyzwaniami, które przekazuje. Ale jak rozpoznać te granice?

Najpierw należy skupić się na modelach domeny logicznej aplikacji i powiązanych danych. Spróbuj zidentyfikować oddzielone wyspy danych i różnych kontekstów w ramach tej samej aplikacji. Każdy kontekst może mieć inny język biznesowy (różne terminy biznesowe). Konteksty powinny być zdefiniowane i zarządzane niezależnie. Terminy i jednostki, które są używane w tych różnych kontekstach może brzmieć podobnie, ale można odkryć, że w określonym kontekście, koncepcji biznesowej z jednym jest używany do innego celu w innym kontekście, a nawet może mieć inną nazwę. Na przykład użytkownik może być określany jako użytkownik w kontekście tożsamości lub członkostwa, jako klient w kontekście CRM, jako kupujący w kontekście zamawiania i tak dalej.

Sposób identyfikowania granic między wieloma kontekstami aplikacji z inną domeną dla każdego kontekstu jest dokładnie taki, jak można zidentyfikować granice dla każdej mikrousługi biznesowej i jej powiązanego modelu domeny i danych. Zawsze należy zminimalizować sprzężenie między tymi mikrousługami. Ten przewodnik zawiera więcej szczegółów na temat tej identyfikacji i projektu modelu domeny w sekcji [Identyfikowanie granic modelu domeny dla każdej mikrousługi](identify-microservice-domain-model-boundaries.md) później.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Wyzwanie \#2: Jak tworzyć kwerendy, które pobierają dane z kilku mikrousług

Drugim wyzwaniem jest sposób implementowania zapytań, które pobierają dane z kilku mikrousług, unikając komunikacji chatty do mikrousług z aplikacji klienta zdalnego. Przykładem może być pojedynczy ekran z aplikacji mobilnej, który musi pokazać informacje o użytkowniku, który jest własnością mikrousług koszyka, katalogu i tożsamości użytkownika. Innym przykładem może być złożony raport obejmujący wiele tabel znajdujących się w wielu mikrousług. Właściwe rozwiązanie zależy od złożoności zapytań. Ale w każdym razie, będziesz potrzebować sposobu na agregowanie informacji, jeśli chcesz poprawić wydajność komunikacji systemu. Najpopularniejsze rozwiązania są następujące.

**Brama interfejsu API.** W przypadku prostej agregacji danych z wielu mikrousług, które są właścicielami różnych baz danych, zalecana metoda jest mikrousługą agregacji, znaną jako brama interfejsu API. Jednak należy zachować ostrożność podczas implementowania tego wzorca, ponieważ może to być punkt ssania w systemie i może naruszać zasadę autonomii mikrousług. Aby ograniczyć tę możliwość, można mieć wiele ukaranych bram interfejsu API, z których każda koncentruje się na pionowym "plasterku" lub obszarze biznesowym systemu. Wzorzec bramy interfejsu API jest wyjaśnione bardziej szczegółowo w [sekcji bramy interfejsu API](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) później.

**CQRS z tabelami kwerend/odczytów.** Innym rozwiązaniem do agregowania danych z wielu mikrousług jest [zmaterializowany widok wzorzec](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). W tym podejściu można wygenerować z wyprzedzeniem (przygotowanie danych nieznormalizowanych przed rzeczywistymi zapytaniami się zdarzyć), tabela tylko do odczytu z danymi, które są własnością wielu mikrousług. Tabela ma format dostosowany do potrzeb aplikacji klienckiej.

Zastanów się nad czymś w rodzaju ekranu aplikacji mobilnej. Jeśli masz jedną bazę danych, można połączyć dane dla tego ekranu przy użyciu kwerendy SQL, która wykonuje złożone sprzężenie obejmujące wiele tabel. Jednak gdy masz wiele baz danych, a każda baza danych jest własnością innej mikrousługi, nie można zbadać tych baz danych i utworzyć sprzężenie SQL. Złożone zapytanie staje się wyzwaniem. Można rozwiązać ten wymóg przy użyciu podejścia CQRS — można utworzyć nieznormalizowaną tabelę w innej bazie danych, która jest używana tylko dla zapytań. Tabela może być zaprojektowana specjalnie dla danych potrzebnych do złożonej kwerendy, z relacją jeden-do-jednego między polami potrzebnymi na ekranie aplikacji a kolumnami w tabeli kwerend. Może to również służyć do celów sprawozdawczych.

Takie podejście nie tylko rozwiązuje oryginalny problem (jak zapytanie i przyłączyć się między mikrousług), ale również znacznie zwiększa wydajność w porównaniu ze złożonym sprzężenia, ponieważ masz już dane, które wymaga aplikacji w tabeli kwerend. Oczywiście przy użyciu polecenia i zapytań odpowiedzialności segregacji (CQRS) z zapytań/odczytów tabel oznacza dodatkowe prace programistyczne i trzeba będzie objąć spójność ostateczną. Niemniej jednak wymagania dotyczące wydajności i wysokiej skalowalności w [scenariuszach współpracy](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (lub scenariuszy konkurencyjnych, w zależności od punktu widzenia) są, gdzie należy zastosować CQRS z wielu baz danych.

**"Zimne dane" w centralnych bazach danych.** W przypadku złożonych raportów i zapytań, które mogą nie wymagać danych w czasie rzeczywistym, typowym podejściem jest eksportowanie "gorących danych" (danych transakcyjnych z mikrousług) jako "zimnych danych" do dużych baz danych, które są używane tylko do raportowania. Ten centralny system bazy danych może być systemem opartym na dużych zbiorach danych, takim jak Hadoop, magazynem danych, takim jak oparty na usłudze Azure SQL Data Warehouse, lub nawet pojedynczą bazą danych SQL, która jest używana tylko dla raportów (jeśli rozmiar nie będzie problemem).

Należy pamiętać, że ta scentralizowana baza danych będzie używana tylko dla zapytań i raportów, które nie wymagają danych w czasie rzeczywistym. Oryginalne aktualizacje i transakcje, jako źródło prawdy, muszą znajdować się w danych mikrousług. Sposób synchronizacji danych będzie albo przy użyciu komunikacji opartej na zdarzeniach (omówione w następnych sekcjach) lub przy użyciu innych narzędzi importu/eksportu infrastruktury bazy danych. Jeśli używasz komunikacji opartej na zdarzeniach, ten proces integracji będzie podobny do sposobu propagowania danych, jak opisano wcześniej dla tabel kwerend CQRS.

Jednak jeśli projekt aplikacji obejmuje stale agregowania informacji z wielu mikrousług dla złożonych zapytań, może to być objawem złego projektu - mikrousługi powinny być tak izolowane, jak to możliwe z innych mikrousług. (Wyklucza to raporty/analizy, które zawsze powinny używać centralnych baz danych na zimno). Mając ten problem często może być przyczyną scalania mikrousług. Należy zrównoważyć autonomię ewolucji i wdrażania każdej mikrousługi z silnymi zależnościami, spójnością i agregacją danych.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Wyzwanie \#3: Jak osiągnąć spójność w wielu mikrousługach

Jak wspomniano wcześniej, dane należące do każdej mikrousługi jest prywatny do tej mikrousługi i można uzyskać dostęp tylko przy użyciu interfejsu API mikrousług. W związku z tym przedstawione wyzwanie polega na implementacji procesów biznesowych end-to-end przy zachowaniu spójności w wielu mikrousług.

Aby przeanalizować ten problem, przyjrzyjmy się przykładowi z [aplikacji referencyjnej eShopOnContainers](https://aka.ms/eshoponcontainers). Mikrousługi katalogu przechowuje informacje o wszystkich produktów, w tym ceny produktu. Mikrousługi koszyka zarządza czasowych danych o produktach, które użytkownicy są dodawane do koszyków, który zawiera cenę towarów w momencie ich dodania do koszyka. Gdy cena produktu jest aktualizowana w katalogu, cena ta powinna być również aktualizowana w aktywnych koszykach, które przechowują ten sam produkt, a także system powinien prawdopodobnie ostrzec użytkownika, mówiąc, że cena określonego towaru uległa zmianie od czasu dodania go do koszyka.

W hipotetycznej monolitycznej wersji tej aplikacji, gdy cena zmienia się w tabeli produktów, podsystem katalogu może po prostu użyć transakcji ACID do aktualizacji bieżącej ceny w tabeli Koszyk.

Jednak w aplikacji opartej na mikrousługach tabele Produkt i koszyk są własnością odpowiednich mikrousług. Żadna mikrousługa nie powinna nigdy zawierać tabel/magazynu należących do innej mikrousługi we własnych transakcjach, nawet w zapytaniach bezpośrednich, jak pokazano na rysunku 4-9.

![Diagram pokazujący, że nie można udostępnić danych bazy danych mikrousług.](./media/distributed-data-management/indepentent-microservice-databases.png)

**Rysunek 4-9**. Mikrousługi nie mogą bezpośrednio uzyskać dostępu do tabeli w innej mikrousługi

Mikrousługi katalogu nie należy aktualizować tabeli koszyka bezpośrednio, ponieważ tabela Koszyk jest własnością mikrousługi koszyka. Aby zaktualizować mikrousługi koszyka, mikrousługi katalogu należy użyć spójności ostatecznej prawdopodobnie na podstawie komunikacji asynchronicznej, takich jak zdarzenia integracji (komunikaty i komunikacji opartej na zdarzeniach). W ten sposób aplikacja referencyjna [eShopOnContainers](https://aka.ms/eshoponcontainers) wykonuje ten typ spójności w mikrousługach.

Jak stwierdzono w [orędzie WPR](https://en.wikipedia.org/wiki/CAP_theorem), należy wybrać między dostępnością a silną konsystencją ACID. Większość scenariuszy opartych na mikrousługach wymaga dostępności i wysokiej skalowalności, w przeciwieństwie do silnej spójności. Aplikacje o znaczeniu krytycznym muszą pozostać uruchomione, a deweloperzy mogą obejść silną spójność przy użyciu technik pracy ze słabą lub ostateczną spójnością. Jest to podejście przyjęte przez większość architektur opartych na mikrousługach.

Ponadto acid-style lub dwufazowe transakcje zatwierdzania nie są tylko w stosunku do zasad mikrousług; większość baz danych NoSQL (takich jak Azure Cosmos DB, MongoDB itp.) nie obsługuje dwufazowych transakcji zatwierdzania, typowych w scenariuszach rozproszonych baz danych. Jednak utrzymanie spójności danych między usługami i bazami danych jest niezbędne. To wyzwanie jest również związane z pytaniem, jak propagować zmiany w wielu mikrousług, gdy niektóre dane muszą być nadmiarowe — na przykład, gdy trzeba mieć nazwę produktu lub opis w mikrousługi katalogu i koszyka mikrousługi.

Dobrym rozwiązaniem tego problemu jest użycie spójności ostatecznej między mikrousługami wyrażonymi za pośrednictwem komunikacji opartej na zdarzeniach i systemu publikowania i subskrybowania. Te tematy są omówione w sekcji [Asynchroniczne komunikacji opartej na zdarzeniach](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) w dalszej części tego przewodnika.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Wyzwanie \#4: Jak zaprojektować komunikację ponad granicami mikrousług

Komunikowanie się między granicami mikrousług jest prawdziwym wyzwaniem. W tym kontekście komunikacja nie odnosi się do jakiego protokołu, którego należy użyć (HTTP i REST, AMQP, wiadomości i tak dalej). Zamiast tego dotyczy stylu komunikacji, którego należy użyć, a zwłaszcza, jak powiązane mikrousług powinny być. W zależności od poziomu sprzężenia, gdy wystąpi awaria, wpływ tej awarii na system będzie się znacznie różnić.

W systemie rozproszonym, takim jak aplikacja oparta na mikrousługach, z tak wieloma artefaktami przemieszczających się i z rozproszonymi usługami na wielu serwerach lub hostach, składniki po pewnym czasie zawiodą. Wystąpi częściowa awaria i nawet większe awarie, dlatego należy zaprojektować mikrousługi i komunikację między nimi, biorąc pod uwagę typowe zagrożenia w tym typie systemu rozproszonego.

Popularnym podejściem jest zaimplementowanie mikrousług opartych na HTTP (REST) ze względu na ich prostotę. Podejście oparte na HTTP jest całkowicie dopuszczalne; problem w tym miejscu jest związany ze tym, jak go używać. Jeśli używasz żądań HTTP i odpowiedzi tylko do interakcji z mikrousług z aplikacji klienckich lub bram interfejsu API, to dobrze. Ale jeśli utworzysz długie łańcuchy synchronicznych wywołań HTTP między mikrousługami, komunikując się przez ich granice, tak jakby mikrousługi były obiektami w aplikacji monolitycznej, aplikacja po pewnym czasie napotka problemy.

Na przykład wyobraź sobie, że aplikacja kliencka sprawia, że wywołanie interfejsu API HTTP do poszczególnych mikrousług, takich jak mikrousługi zamawiania. Jeśli mikrousługi zamawiania z kolei wywołuje dodatkowe mikrousług przy użyciu protokołu HTTP w ramach tego samego cyklu żądania/odpowiedzi, tworzysz łańcuch wywołań HTTP. Początkowo może to brzmieć rozsądnie. Istnieją jednak ważne kwestie, które należy wziąć pod uwagę podczas przechodzenia tą ścieżką:

- Blokowanie i niska wydajność. Ze względu na synchroniczny charakter HTTP, oryginalne żądanie nie otrzymuje odpowiedzi, dopóki wszystkie wewnętrzne wywołania HTTP są zakończone. Wyobraź sobie, że liczba tych wywołań znacznie wzrasta i w tym samym czasie jeden z pośrednich wywołań HTTP do mikrousługi jest zablokowany. W rezultacie ma to wpływ na wydajność, a ogólna skalowalność będzie wykładniczo naruszona wraz ze wzrostem dodatkowych żądań HTTP.

- Sprzężenie mikrousług z HTTP. Mikrousługi biznesowe nie powinny być powiązane z innymi mikrousługami biznesowymi. W idealnym przypadku nie powinny "wiedzieć" o istnieniu innych mikrousług. Jeśli aplikacja opiera się na mikrousług sprzęgających, jak w przykładzie, osiągnięcie autonomii na mikrousługi będzie prawie niemożliwe.

- Błąd w jednej mikrousługi. Jeśli zaimplementowano łańcuch mikrousług połączonych wywołaniami HTTP, gdy którykolwiek z mikrousług nie powiedzie się (i ostatecznie zakończy się niepowodzeniem) cały łańcuch mikrousług zakończy się niepowodzeniem. System oparty na mikrousługach powinny być zaprojektowane tak, aby kontynuować pracę, jak to możliwe podczas częściowych awarii. Nawet jeśli implementujesz logikę klienta, która używa ponownych prób z wykładniczymi mechanizmami wycofywania lub wyłącznika, tym bardziej złożone są łańcuchy wywołań HTTP, tym bardziej złożone jest implementowanie strategii awarii opartej na http.

W rzeczywistości jeśli wewnętrzne mikrousługi komunikują się, tworząc łańcuchy żądań HTTP zgodnie z opisem, można argumentować, że masz aplikację monolityczną, ale na podstawie protokołu HTTP między procesami zamiast mechanizmów komunikacji wewnątrzprocesu.

W związku z tym w celu wymuszenia autonomii mikrousług i mają lepszą odporność, należy zminimalizować użycie łańcuchów komunikatu żądania/odpowiedzi w mikrousługach. Zaleca się, aby używać tylko interakcji asynchronicznej do komunikacji między mikrousługami, za pomocą komunikacji asynchronicznej opartej na komunikatach i zdarzeniach lub przy użyciu (asynchronicznego) sondowania HTTP niezależnie od oryginalnego cyklu żądania/odpowiedzi HTTP.

Korzystanie z komunikacji asynchronicznej wyjaśniono z dodatkowych szczegółów w dalszej części tego przewodnika w sekcjach [integracji mikrousług asynchronicznych wymusza autonomii mikrousługi](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) i [komunikacji opartej na komunikatach asynchronicznych](asynchronous-message-based-communication.md).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **WPR – powszewierzenie** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- **Spójność ostateczna** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Podkład spójności danych** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Martin Fowler. CQRS (segregacja odpowiedzialności za polecenia i kwerendy)** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Widok zmaterializowany** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles Row. ACID vs. BASE: Przesunięcie pH przetwarzania transakcji bazy danych** \
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **Transakcja kompensacyjna** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **Udi Dahan. Skład zorientowany na usługi** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[Poprzedni](logical-versus-physical-architecture.md)
>[następny](identify-microservice-domain-model-boundaries.md)
