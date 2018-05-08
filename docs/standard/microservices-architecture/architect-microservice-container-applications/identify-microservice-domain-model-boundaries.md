---
title: Identyfikowanie granice modelu domeny dla każdego mikrousługi
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Identyfikowanie granice modelu domeny dla każdego mikrousługi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b11d2838539b8ddbe21bcfcb77845a10e466c760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Zidentyfikuj granice modelu domeny dla każdego mikrousługi

Celem podczas identyfikowania granice modelu i rozmiaru dla każdego mikrousługi jest nie uzyskać dostęp do najbardziej szczegółowego separacji to możliwe, chociaż należy zwykle kierunku małych mikrousług Jeśli to możliwe. Zamiast tego celem powinno być na uzyskanie dostępu do najbardziej znaczący separacji, kierując się swoją wiedzą domeny. Nacisk nie znajduje się na rozmiar, ale zamiast tego na możliwości biznesowe. Ponadto w przypadku zwykłego spójności wymagane dla niektórych części aplikacji oparte na dużą liczbę zależności, wskazujący potrzebę pojedynczego mikrousługi, zbyt. Spójności jest do identyfikowania sposobu Rozdziel lub mikrousług razem z grupy. Ostatecznie podczas gdy możesz uzyskać więcej informacji na temat domeny, powinno się zaadaptować rozmiar Twojej mikrousługi wielokrotnie powtarzane. Znajdowanie właściwego rozmiaru nie jest procesem jednorazowej.

[Sam Newman](https://samnewman.io/), rozpoznawanym promotor mikrousług oraz autora książki [Mikrousług budynku](https://samnewman.io/books/building_microservices/), wyróżnia się, że należy projektować Twojej mikrousług wzorca kontekstu ograniczone (BC) (część z oparte na domenie projekt), jak wprowadzone wcześniej. Czasami BC może składać się z kilku usług fizycznej, ale nie odwrotnie.

Model domeny z określonej domeny jednostek ma zastosowanie w konkretnych BC lub mikrousługi. BC rozgranicza stosowania modelu domeny i deweloperów zapewnia przejrzyste i udostępnionych zrozumienia co musi być spójna i jakie mogą być opracowane niezależnie członków zespołu. Są to te same cele dla mikrousług.

Innego narzędzia, które informują wybór projektu jest [Conway w prawo](https://en.wikipedia.org/wiki/Conway%27s_law), które stwierdza, że aplikacja będzie odzwierciedlać społecznościowych granic organizacji, który go utworzył. Czasami przeciwieństwem ma wartość true, ale — organizacji firmy jest tworzony przez oprogramowanie. Aby wycofać Conway w prawo i tworzenie granic sposobu, w firmie, aby uporządkowane, może być konieczne leaning kierunku konsultacji procesów biznesowych.

Aby zidentyfikować ograniczonego kontekstów, jest wzorzec DDD, który może służyć do to [mapowania kontekście wzorca](https://www.infoq.com/articles/ddd-contextmapping). Z kontekstu mapowania należy zidentyfikować różnych kontekstów w aplikacji i ich granic. Jest to często mają różne kontekstu i granic dla każdego podsystemu mały, na przykład. Mapa kontekstu jest sposób definiowania i dokonać jawnej tych granic między domenami. BC jest serwer autonomiczny i zawiera szczegóły pojedynczej domeny — szczegółowe informacje, takie jak jednostek domeny — i definiuje integracji umowy z innych usług łączności biznesowej. Jest to podobne do definicji mikrousługi: jest serwer autonomiczny, implementuje niektórych możliwości domeny i przekazuje interfejsów. Jest to, dlaczego mapowania kontekstu i wzorzec ograniczone kontekstu są dobrym podejścia do identyfikacji użytkownika mikrousług granice modelu domeny.

Podczas projektowania dużej aplikacji, zobaczysz, jak jego model domeny może pofragmentowany — ekspert domeny w domenie katalogu zostanie nazwy jednostek inaczej w domenie katalogu i spisu od ekspertów, domeny wysyłania dla wystąpienia. Lub jednostką domeny użytkownika może różnić się rozmiarem i liczby atrybutów podczas pracy nad CRM ekspertów, kto chce przechowywać co szczegółowych informacji dotyczących klientów niż dla porządkowania ekspert domeny, który wymaga tylko częściowe dane dotyczące klienta. Jest bardzo trudne do odróżniania wszystkie warunki domeny we wszystkich domenach, które są powiązane z dużej aplikacji. Jednak najbardziej ważne jest, że użytkownik nie należy próbować ujednolicenie postanowienia; Zamiast tego należy zaakceptować różnice i siłę pochodzącymi z każdej domeny. Jeśli spróbujesz ujednoliconego bazy danych dla całej aplikacji prób ujednoliconego słownictwa będzie nieodpowiednich i nie dźwięk w prawo do dowolnego z wieloma ekspertami domeny. W związku z tym usług łączności biznesowej (zaimplementowane jako mikrousług) pomoże Ci wyjaśnienie, których można użyć określonych warunków domeny i gdzie należy podzielić systemu i utworzyć dodatkowe usług łączności biznesowej z innej domeny.

Oznacza to, że masz prawa granic i rozmiary każdego BC i modelu domeny jeśli masz kilka silne relacje między modelami domeny i wykonaniu nie zawsze muszą być scalone informacje z wielu modeli domeny podczas wykonywania Typowa aplikacja operacje.

Prawdopodobnie najlepsze odpowiedź na pytanie, jak duże powinny być modelu domeny dla każdego mikrousługi są następujące: powinien mieć BC autonomicznych, jak izolowanym, jak to możliwe, który umożliwia pracę bez konieczności przełączania stale do innych kontekstach (inne modele mikrousługi firmy). Rysunek 4-10 można zobaczyć jak wiele mikrousług (wiele usług łączności biznesowej) każdego mają własne modelu i sposób ich jednostek można zdefiniować, w zależności od określone wymagania dotyczące każdej z domen zidentyfikowanych w aplikacji.

![](./media/image10.png)

**Rysunek 4-10**. Identyfikowanie jednostek i granice modelu mikrousługi

Rysunek 4-10 przedstawiono przykładowy scenariusz związane z system zarządzania konferencji w trybie online. Zidentyfikowano kilka usług łączności biznesowej, które można implementować jako mikrousług, na podstawie domen, które ekspertów domeny zdefiniowane dla użytkownika. Jak widać, istnieją jednostki, które znajdują się tylko w modelu pojedynczego mikrousługi, takich jak płatności w mikrousługi płatności. Te będą łatwa do wdrożenia.

Jednak może być również jednostek, które mają różne kształtu, ale być współużytkowane przez wiele modeli domeny z wielu mikrousług tej samej tożsamości. Na przykład jednostki użytkownika zostanie zidentyfikowana w mikrousługi konferencji zarządzania. Tego samego użytkownika o tej samej tożsamości jest elementem o nazwie kupujący w mikrousługi porządkowanie lub elementem o nazwie płatnika w mikrousługi płatności, a nawet jednego o nazwie klienta mikrousługi obsługi klienta. Wynika to z faktu, w zależności od [powszechny języka](https://martinfowler.com/bliki/UbiquitousLanguage.html) czy używa ekspert każdej domeny, użytkownik może mieć inną perspektywę nawet z różnymi atrybutami. Jednostki użytkownika w modelu mikrousługi o nazwie konferencji zarządzania może być najbardziej jego atrybuty danych osobowych. Jednak tego samego użytkownika w kształcie płatnika mikrousługi płatności lub kształt odbiorcy mikrousługi obsługi klienta nie może być konieczne tę samą listę atrybutów.

Podejście podobne przedstawiono w rysunek 4-11.

![](./media/image11.png)

**Rysunek 4-11**. Decomposing modeli tradycyjnych danych do wielu modeli domeny

Widać, jak użytkownik znajduje się w modelu mikrousługi zarządzania konferencji jako jednostki użytkownika i występuje również w postaci obiektu nabywców mikrousługi cennik, alternatywne atrybuty lub szczegóły użytkownika, gdy jest rzeczywiście kupujący. Każdy mikrousługi lub BC nie może być konieczne wszystkie dane związane z jednostki użytkownika, tylko część, w zależności od problem do rozwiązania lub kontekście. Na przykład w modelu mikrousługi cennik, nie trzeba adres lub identyfikator użytkownika, wystarczy identyfikator (jako tożsamość) i stan, który będzie mieć wpływ na rabaty, gdy cennik miejsc na nabywców.

Jednostka stanowisko ma taką samą nazwę, ale różnych atrybutów w każdym modelu domeny. Jednak stanowisko udostępnia tożsamości oparte na tym samym identyfikatorze jak się dzieje z użytkownika i nabywców.

Zasadniczo jest udostępniony koncepcji użytkownika, który istnieje w wielu usług (w domenach), których udostępnianie tożsamości danego użytkownika. Jednak w każdym modelu domeny może być dodatkowych lub innych szczegółów dotyczących jednostki użytkownika. W związku z tym musi istnieć mapują jednostki użytkownika z jednej domeny (mikrousługi) do innego.

Istnieje wiele zalet nie współużytkowanie tej samej jednostki użytkownika z taką samą liczbę atrybutów między domenami. Korzyścią jest ograniczenie duplikatów, dzięki czemu modele mikrousługi nie mają żadnych danych, która nie ma potrzeby. Kolejna korzyść związana występują mikrousługi wzorca, który jest właścicielem określonego typu danych na jednostkę tak, aby aktualizacje i zapytania dla tego typu danych pojawiają się tylko przy tym mikrousługi.


>[!div class="step-by-step"]
[Poprzednie] (distributed-data-management.md) [dalej] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
