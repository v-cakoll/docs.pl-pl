---
title: Problemy i rozwiązania do zarządzania danymi rozproszonych
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Problemy i rozwiązania do zarządzania danymi rozproszonych
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7d173133ab7c803c7ab48b39c50b02ee4f3b1721
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Problemy i rozwiązania do zarządzania danymi rozproszonych

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Żądanie \#1: sposób definiowania granice każdej mikrousługi

Definiowanie granic mikrousługi prawdopodobnie pierwszego wyzwania, które każda osoba, która wystąpi. Każdy mikrousługi należy autonomicznego ze wszystkimi korzyści i problemy, które wywołuje i każdego mikrousługi musi być częścią aplikacji. Jednak sposób można zidentyfikować te granice?

Najpierw należy się skoncentrować modeli domeny logiczne i dane dotyczące aplikacji. Należy spróbować ponownie zidentyfikować rozdzielonymi Wyspy danych i kontekstów w tej samej aplikacji. Każdy kontekst może mieć język biznesowej (warunki biznesowej). Konteksty należy określić i zarządzane niezależnie. Warunki i jednostek używane w tych różnych kontekstach mogą dźwiękowej podobne, ale może wykryć, czy dla danego kontekstu koncepcja firmy, z jednym jest używana w innym celu w innym kontekście, a nawet może mieć inną nazwę. Na przykład użytkownika mogą być określane jako użytkownik w kontekście tożsamości lub członkostwa odbiorcy w kontekście CRM, jako nabywców w kontekście porządkowania i tak dalej.

Sposób identyfikacji granicę między wielu kontekstów aplikacji z innej domeny dla każdego kontekstu jest dokładnie, jak rozpoznać granice dla każdej mikrousługi biznesowych i jej powiązane danych i modelu domeny. Zawsze próba zminimalizować sprzężenia między tymi mikrousług. W tym przewodniku przechodzi w stan więcej szczegółów dotyczących tego projektu modelu identyfikacji i domeny w sekcji [identyfikujące model domeny granice dla każdej mikrousługi](#identifying-domain-model-boundaries-for-each-microservice) później.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Żądanie \#2: jak tworzyć zapytania, które służą do pobierania danych z kilku mikrousług

Drugi wyzwaniem jest implementowania kwerendy pobierające dane z kilku mikrousług, unikając do mikrousług chatty komunikacji z klientami zdalnymi aplikacji. Przykładem może być jednym ekranie z aplikacji mobilnej, który wymaga, aby wyświetlić informacje o użytkowniku, którego właścicielem jest koszyka, katalogu i mikrousług tożsamości użytkownika. Innym przykładem może być złożonego raportu obejmujące wiele tabel znajdujących się w wielu mikrousług. Odpowiednim rozwiązaniem jest zależna od złożoności kwerend. Jednak w każdym przypadku należy sposób agregują informacje, aby zwiększyć wydajność w komunikacji systemu. Najbardziej popularnych rozwiązań są następujące.

**Interfejs API bramy**. Agregacji proste danych z wielu mikrousług, którego właścicielem różnych baz danych Zalecanym podejściem jest mikrousługi agregacji, określany jako bramę interfejsu API. Jednak należy zachować ostrożność implementacja tego wzorca, ponieważ w systemie może być punktem urządzenie rozruchowe, a może naruszyć zasady Autonomia mikrousługi. Aby uniknąć tej możliwości, może mieć wielu bram interfejsu API dopasowanymi grzywną każdego jeden koncentrujących się na pionowym "fragment" lub obszar działalności systemu. Wzorzec bramy interfejsu API jest co omówiono bardziej szczegółowo w sekcji Używanie interfejsu API bramy później.

**CQRS z tabelami zapytania/odczyty**. Innym rozwiązaniem do agregowania danych z wielu mikrousług jest [Zmaterializowany widok wzorca](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). W takie podejście, należy wygenerować, wcześniej (przygotowanie nieznormalizowany danych, przed stanie rzeczywiste zapytań), tylko do odczytu tabelę z danymi, którego właścicielem jest wiele mikrousług. Tabela ma format dostosowane do potrzeb aplikacji klienckiej.

Należy wziąć pod uwagę przypominać ekranu dla aplikacji mobilnej. Jeśli masz pojedynczej bazy danych, użytkownik może pobierać razem danych dla tego ekranu przy użyciu zapytania SQL, który wykonuje sprzężenie złożonych obejmujące wiele tabel. Jednak jeśli masz wiele baz danych, a każda baza danych jest własnością innego mikrousługi, nie można kwerendy tych baz danych i tworzenie sprzężenia SQL. Złożone kwerendy staje się żądanie. Można rozwiązać wymaganie podejście CQRS — tworzenie nieznormalizowany tabeli w innej bazy danych, która jest używana tylko dla zapytania. Tabela może być zaprojektowana specjalnie z myślą o danych potrzebnych do złożonego zapytania, z relacją między polami wymaganej przez ekranu aplikacji i kolumn w tabeli zapytania. Można go również służyć do celów raportowania.

Takie podejście nie tylko rozwiązuje problem oryginalnego (jak zapytań i sprzężenia między mikrousług); zwiększa również wydajności znacznie w porównaniu z złożonych sprzężenia, ponieważ masz już dane, które są wymagane przez aplikację w tabeli zapytania. Oczywiście przy użyciu polecenia i podział odpowiedzialności kwerendy (CQRS) z zapytania/odczyty tabel oznacza dodatkowe prace i konieczne będzie obejmować spójność ostateczna. Niemniej jednak wymagania dotyczące wydajności i skalowalności wysokiej w [współpracy scenariusze](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (lub konkurencyjnych scenariuszy, w zależności od punktu widzenia) jest, gdzie należy zastosować CQRS z wieloma bazami danych.

**"Zimnych danych" w bazach danych centralnej**. Złożonych raportów i zapytań, które nie mogą wymagać danych w czasie rzeczywistym typowym podejściem jest wyeksportowanie Twojej "gorących danych" (danych transakcyjnych z mikrousług) jako "zimnych danych" w dużych baz danych, które są używane tylko do raportowania. Tego systemu centralnej bazie danych może być danych Big Data systemu, takich jak Hadoop, Magazyn danych podobny do opartych na magazyn danych SQL Azure lub nawet jednej bazy danych SQL używane tylko dla raportów (Jeśli rozmiar nie będzie problemu).

Należy pamiętać, że ta scentralizowanej bazie danych mają być używane tylko do kwerendy i raporty, które nie są dane w czasie rzeczywistym. Oryginalne aktualizacje i transakcje jako źródła PRAWDA, muszą być danych mikrousług. Sposób może synchronizować dane będą za pomocą komunikacji sterowane zdarzeniami (opisane w kolejnych sekcjach) lub przy użyciu innych narzędzi importu/eksportu infrastruktury bazy danych. Jeśli użytkownik korzysta z komunikacji sterowane zdarzeniami, ten proces integracji będzie podobny do sposób propagację danych zgodnie z wcześniejszym opisem dla CQRS badania tabel.

Jednak jeśli projektu aplikacji obejmuje stale agregowanie informacji z wielu mikrousług złożonych zapytań, może być objawem zły projektu — mikrousługi należy jako izolowanych, jak to możliwe z innych mikrousług. (Wyklucza raporty/analytics, która zawsze powinna być używana danych chłodni centralnej bazy danych). Ten problem często może być powodem do scalenia mikrousług. Musisz autonomię rozwoju i wdrażania każdej mikrousługi z silną zależności, spójność i agregacja danych.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Żądanie \#3: jak w celu ujednolicenia wielu mikrousług

Jak wspomniano wcześniej, danych należących do każdego mikrousługi jest oznaczony jako prywatny tego mikrousługi i można uzyskać tylko za pomocą jego mikrousługi interfejsu API. Dlatego żądanie przedstawiony jest implementowania procesów biznesowych na trasie przy zachowaniu spójności między wieloma mikrousług.

Aby analizować ten problem, Przyjrzyjmy się przykładem z [eShopOnContainers odwołania aplikacji](http://aka.ms/eshoponcontainers). Mikrousługi katalogu przechowuje informacje o wszystkich produktów, w tym ich poziomu podstawowego. Mikrousługi porządkowanie zarządza zleceń i należy sprawdzić nową kolejność nie przekracza dostępne katalogu podstawowego produktu. (Lub scenariusza mogą dotyczyć logikę, która obsługuje produkty wycofane.) Hipotetyczny wbudowanymi wersji tej aplikacji porządkowania podsystemu można po prostu użyć transakcji ACID do sprawdzania dostępności zasobów, tworzenia kolejności w tabeli poleceń i aktualizacji dostępnych zasobów w tabeli Produkty.

Jednak w aplikacji oparte na mikrousług tabeli kolejności i produktu są własnością ich odpowiednich mikrousług. Nie mikrousługi kiedykolwiek powinna zawierać baz danych należących do innego mikrousługi w tej samej transakcji lub kwerend, jak pokazano w rysunek 4-9.

![](./media/image9.PNG)

**Rysunek 4-9**. Mikrousługi bezpośrednio nie może uzyskać dostępu do tabeli w innym mikrousługi

Mikrousługi porządkowanie powinien nie zaktualizować tabeli produkty bezpośrednio, ponieważ w tabeli Produkty jest własnością mikrousługi katalogu. Aby dokonać aktualizacji mikrousługi katalogu, mikrousługi porządkowanie należy używać tylko komunikacji asynchronicznej, takich jak zdarzenia integracji (wiadomości i komunikacji oparte na zdarzeniu). Jest to sposób [eShopOnContainers](http://aka.ms/eshoponcontainers) odwołania aplikacji wykonuje ten typ aktualizacji.

Podane przez [Newtona zakończenia](https://en.wikipedia.org/wiki/CAP_theorem), musisz wybrać między dostępności i ACID wysoki poziom spójności. Większość scenariuszy opartych na mikrousługi wymaga dostępności i wysoką skalowalność, w przeciwieństwie do wysoki poziom spójności. Kluczowych aplikacji musi znajdować się, a następnie uruchomiona i deweloperów można obejść wysoki poziom spójności za pomocą techniki do pracy z słabych lub ostatecznego spójności. To podejście przez większość architektury mikrousługi na podstawie.

Ponadto kwasu stylu lub dwufazowe zatwierdzanie transakcji nie są tylko względem mikrousług zasad. Większość bazy danych NoSQL (np. Azure DB rozwiązania Cosmos bazy danych MongoDB, itp.) nie obsługują dwufazowe zatwierdzanie transakcji. Jednak zachowanie danych spójności między usługami i baz danych jest niezbędne. Ten problem również jest powiązany z zapytania sposobu Propaguj zmiany do wszystkich mikrousług wielu w przypadku niektórych danych musi być nadmiarowe — na przykład, gdy musisz mieć nazwy lub opisu mikrousługi katalogu i koszyka produktu mikrousługi.

Dobre rozwiązanie tego problemu jest Użyj spójność ostateczna między mikrousług przegubowe za pośrednictwem komunikacji sterowane zdarzeniami i systemem publikowania i subskrybowania. Te tematy w sekcji [komunikacji asynchronicznej sterowane zdarzeniami](#async_event_driven_communication) dalszej części tego przewodnika.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Żądanie \#4: sposób projektowania komunikacji między granicami mikrousługi

Granice komunikacji za pośrednictwem mikrousługi jest rzeczywistym wyzwaniem. W tym kontekście komunikacji nie odwołuje się który protokół powinien używać (HTTP i REST, protokołu AMQP obsługi wiadomości i tak dalej). Zamiast tego adresów styl komunikacji należy używać, i jak sprzężonego z mikrousług powinno się. W zależności od poziomu sprzężenia gdy wystąpi błąd, wpływ awarii w systemie różni się znacząco.

W Rozproszony system, takich jak mikrousług aplikacji sieci, z tylu artefakty przenoszenia i usługi rozproszone między wiele serwerów lub hostów nie zostanie ostatecznie składników. Niepowodzenie częściowe i awarie jeszcze większym nastąpi, więc należy projektować Twojej mikrousług i komunikację między nimi biorąc pod uwagę ryzyko typowe w tym typie Rozproszony system.

Popularne podejście jest zaimplementowanie HTTP (REST) — na podstawie mikrousług ze względu na prostotę ich. Podejście oparte na protokole HTTP jest dopuszczalne doskonale; w tym miejscu problem jest związany sposobu ich używania. Jeśli używasz żądań i odpowiedzi HTTP tylko w celu interakcji z Twojej mikrousług z aplikacji klienckich lub bram interfejsu API, który jest poprawne. Ale jeśli tworzysz długie łańcuchy synchroniczne wywołania HTTP między mikrousług komunikacji za pośrednictwem ich granic tak, jakby mikrousług był obiektów w aplikacji wbudowanymi aplikacji zostanie ostatecznie wystąpiły problemy.

Na przykład załóżmy, że aplikacja kliencka wykonuje wywołanie interfejsu API HTTP poszczególnych mikrousługi jak mikrousługi porządkowanie. Mikrousługi porządkowanie z kolei wywołuje dodatkowe cykl mikrousług przy użyciu protokołu HTTP w ramach tego samego żądania/odpowiedzi, tworzenia łańcucha wywołań HTTP. Może być brzmi uzasadnione początkowo. Istnieją jednak ważne kwestie do rozważenia podczas przechodzenia w dół tej ścieżki:

-   Blokowania i niskiej wydajności. Ze względu na specyfikę synchroniczne HTTP oryginalne żądanie nie otrzyma odpowiedź, zakończenie wszystkich wewnętrzny połączeń HTTP. Załóżmy, jeśli liczba tych wywołań znacznie zwiększa i w tym samym czasie, jedną HTTP pośredniego wywołania do mikrousługi jest zablokowana. Wynik jest to wpływ na wydajność, czy wykładniczo wpłynie ogólnej skalowalności jako dodatkowe zwiększenie żądania HTTP.

-   Sprzężenia mikrousług protokołu HTTP. Mikrousług biznesowych nie powinny być połączone z mikrousług innych firm. Najlepiej, jeśli ich nie "informacje" o istnienie innych mikrousług. Jeśli aplikacja opiera się na sprzężenia mikrousług, jak pokazano w przykładzie, uzyskanie Autonomia na mikrousługi będzie niemożliwe.

-   Błąd w żadnych jeden mikrousługi. Jeśli zaimplementowano łańcucha mikrousług połączone połączenia HTTP, gdy dowolne mikrousług nie powiedzie się (i ostatecznie zakończy się niepowodzeniem) całego łańcucha mikrousług zakończy się niepowodzeniem. Systemu mikrousługi należy tak zaprojektować, aby kontynuować pracę oraz możliwości podczas częściowej awarii. Nawet w przypadku implementowania logiki klienta, która używa ponownych prób z wykładniczego wycofywania lub mechanizmy wyłącznika więcej łańcuchów wywołania złożone HTTP są bardziej złożone jest zaimplementować strategię błędu HTTP w oparciu.

W rzeczywistości Jeśli Twoje wewnętrzny mikrousług komunikują się przez utworzenie łańcucha żądań HTTP, zgodnie z opisem, go może być utrzymywał, czy masz wbudowanymi aplikacji, ale oparty na HTTP między procesami zamiast mechanizmy komunikacji intraprocess.

W związku z tym aby wymusić Autonomia mikrousługi i mieć większą elastyczność, należy zminimalizować użycie łańcucha żądań i odpowiedzi komunikacji między mikrousług. Zaleca się używać tylko asynchroniczne interakcji dla komunikacji między mikrousługi za pomocą komunikacji asynchronicznej wiadomości - i oparty na zdarzeniach lub sondowania HTTP niezależnie od oryginalnej cyklu żądań i odpowiedzi HTTP.

Użycie komunikacji asynchronicznej jest wyjaśnione w dokumencie o dodatkowe informacje w dalszej części tego przewodnika w sekcjach [integracji asynchroniczne mikrousługi wymusza Autonomia w mikrousługi](#asynchronous-microservice-integration-enforce-microservices-autonomy) i [asynchronicznym Komunikacja oparta na komunikat](#asynchronous-message-based-communication).

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Zakończenie Newtona**
    [*https://en.wikipedia.org/wiki/CAP\_Newtona*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Spójność ostateczna**
    [*https://en.wikipedia.org/wiki/Eventual\_spójności*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Elementarz spójność danych**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Pole Fowler. CQRS (polecenia i podział odpowiedzialności zapytania)**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Zmaterializowanym widoku**
    [*https://docs.microsoft.com/azure/architecture/patterns/materialized-view*](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

-   **Charlesa wiersza. ACID vs. PODSTAWOWA: Ciąg Shifting przetwarzania transakcji bazy danych**
    [*http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/*](http://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/)

-   **Kompensowanie transakcji**
    [*https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction*](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

-   **Udi Dahan. Kompozycja zorientowane na usługę**
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)


>[!div class="step-by-step"]
[Poprzednie] (logiczne i fizycznych architecture.md) [dalej] (zidentyfikować mikrousługi domeny — model-boundaries.md)
