---
title: Identyfikowanie granic modelu domeny dla każdej mikrousługi
description: Zapoznaj się z istotą partycjonowania dużej aplikacji do mikrousług w celu osiągnięcia architektury dźwiękowej.
ms.date: 09/20/2018
ms.openlocfilehash: 9c433066dd8e93dbb09b15e58c9c85617775723d
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834413"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Określ granice modelu domeny dla każdej mikrousługi

Celem określania granic i rozmiaru modelu dla każdej mikrousługi nie jest uzyskanie bardziej szczegółowego rozdzielenia, chociaż jest to możliwe w przypadku małych mikrousług. Zamiast tego należy zapoznać się z najważniejszym rozdzieleniem podanym przez wiedzę o domenie. Ten nacisk nie jest rozmiarem, ale zamiast możliwości biznesowe. Ponadto, jeśli istnieje wyraźna spójność dla pewnego obszaru aplikacji w oparciu o dużą liczbę zależności, która wskazuje potrzebę tylko jednego mikrousługi. Spójność to sposób, aby określić, jak należy rozdzielić lub zgrupować wspólnie mikrousługi. Ostatecznie, podczas gdy uzyskasz więcej informacji na temat domeny, należy dostosować rozmiar mikrousługi, iteracyjnie. Znalezienie odpowiedniego rozmiaru nie jest procesem z jednym zrzutem.

[Sam Newmana](https://samnewman.io/), rozpoznany podwyższanie poziomu mikrousług i autor [tworzenia mikrousług](https://samnewman.io/books/building_microservices/)w książce, oznacza, że należy zaprojektować mikrousługi na podstawie wzorca ograniczone kontekstu (BC) (część projektu opartego na domenie), jak to zostało wprowadzone. wyżej. Czasami może składać się z kilku usług fizycznych, ale nie odwrotnie.

Model domeny z określonymi jednostkami domeny ma zastosowanie w ramach konkretnej BC lub mikrousług. Funkcja BC ogranicza możliwość zastosowania modelu domeny i zapewnia członkom zespołu deweloperów jasne i wspólne zrozumienie, co musi być spójne i co może być opracowane niezależnie. Są to te same cele dla mikrousług.

Innym narzędziem, które informuje o wyborze projektu, jest [Conways](https://en.wikipedia.org/wiki/Conway%27s_law), który stwierdza, że aplikacja będzie odzwierciedlać granice społecznościowe organizacji, która go wygenerowała. Jednak czasami przeciwieństwem jest wartość true — organizacja firmy jest tworzona przez oprogramowanie. Może być konieczne odwrócenie prawa Conways i skompilowanie granic w taki sposób, w jaki ma być zorganizowana firma, a tym samym do konsultacji między procesami biznesowymi.

Aby zidentyfikować konteksty ograniczone, można użyć deseniu DDD o nazwie [wzorzec mapowania kontekstu](https://www.infoq.com/articles/ddd-contextmapping). Mapowanie kontekstu pozwala identyfikować różne konteksty w aplikacji i ich granice. Często istnieją różne konteksty i granice dla każdego małego podsystemu, na przykład. Mapowanie kontekstu jest sposobem definiowania i określania jawnych granic między domenami. BC jest autonomiczna i zawiera szczegółowe informacje o pojedynczej domenie — szczegóły, takie jak jednostki domeny i definiuje kontrakty integracji z innymi usługami łączności biznesowej. Jest to podobne do definicji mikrousługi: jest autonomiczna, implementuje pewne możliwości domeny i musi udostępniać interfejsy. Dzieje się tak dlatego, że mapowanie kontekstu i powiązane wzorce kontekstu są dobrym podejściem do identyfikowania granic modelu domeny mikrousług.

Podczas projektowania dużej aplikacji zobaczysz, jak jej model domeny może być pofragmentowany — ekspert domeny z domeny wykazu będzie określać jednostki jako inaczej w katalogu i domenach spisu niż na przykład dla eksperta domeny wysyłki. Lub jednostka domeny użytkownika może być różna od rozmiaru i liczby atrybutów podczas pracy z ekspertem programu CRM, który chce przechowywać wszystkie szczegółowe informacje o kliencie, niż w przypadku podmiotu zamawiającego domeny, który po prostu potrzebuje danych częściowych dotyczących klienta. Bardzo trudno jest odróżnić wszystkie warunki domeny dla wszystkich domen związanych z dużą aplikacją. Jednak najważniejsze jest, że nie należy próbować ujednolicić warunków. Zamiast tego należy zaakceptować różnice i rozbudowaność zapewnioną przez poszczególne domeny. Jeśli spróbujesz korzystać z ujednoliconej bazy danych dla całej aplikacji, próby w ujednoliconym słownictwie będą niewygodna i nie będą miały dostępu bezpośrednio do żadnego z wielu ekspertów domeny. W związku z tym usługa BCs (zaimplementowana jako mikrousługi) pomoże w wyjaśnieniu, gdzie można używać pewnych warunków domeny i gdzie należy podzielić system i utworzyć dodatkowe usługi łączności biznesowej z różnymi domenami.

Wiadomo, że masz odpowiednie granice i rozmiary każdego modelu BC i domeny, jeśli masz kilka silnych relacji między modelami domen i nie musisz zwykle scalać informacji z wielu modeli domen podczas wykonywania typowych operacji aplikacji .

Prawdopodobnie najlepszą odpowiedzią na pytanie, jak duży model domeny dla każdej mikrousługi powinien być następujący: powinien mieć autonomiczną metodę BC, jak to możliwe, która pozwala na działanie bez konieczności ciągłego przełączania się do innych kontekstów (innych modele mikrousług). Na rysunku 4-10 można zobaczyć, jak wiele mikrousług (wiele BCs) ma własny model i jak można definiować ich jednostki, w zależności od określonych wymagań dla każdej z określonych domen w aplikacji.

![Diagram przedstawiający jednostki w kilku granicach modeli.](./media/identify-microservice-domain-model-boundaries/identify-entities-microservice-model-boundries.png)

**Rysunek 4-10**. Identyfikowanie jednostek i granic modelu mikrousług

Rysunek 4-10 ilustruje przykładowy scenariusz związany z systemem zarządzania konferencją online. Ta sama jednostka jest wyświetlana jako "Users", "Kupcs", "Payers" i "Customers" w zależności od kontekstu ograniczonego. Zidentyfikowano kilka usług BCs, które mogą być zaimplementowane jako mikrousługi, na podstawie domen zdefiniowanych dla Ciebie przez ekspertów domeny. Jak widać, istnieją jednostki, które znajdują się tylko w jednym modelu mikrousług, np. w przypadku płatności w mikrousłudze. Ich wdrożenie będzie łatwe.

Można jednak również mieć jednostki o innym kształcie, ale współużytkować tę samą tożsamość w modelach wielu domen z wielu mikrousług. Na przykład jednostka użytkownika jest identyfikowana w mikrousłudze konferencji do zarządzania. Ten sam użytkownik, o tej samej tożsamości, jest jednym z nazwanymi kupującymi w mikrousłudze porządkowania lub jeden nazwany płatnika w mikrousłudze płatniczej, a nawet jeden nazwany klient w mikrousłudze klienta. Wynika to z faktu, że w zależności od [języka powszechnie](https://martinfowler.com/bliki/UbiquitousLanguage.html) używanego przez każdego eksperta domeny użytkownik może mieć inną perspektywę nawet z innymi atrybutami. Jednostka użytkownika w modelu mikrousług o nazwie Zarządzanie konferencjami może mieć większość prywatnych atrybutów danych. Jednak ten sam użytkownik w kształcie płatnika w płatności mikrousług lub w kształcie klienta w usłudze mikrousług klienta może nie potrzebować tej samej listy atrybutów.

Podobne podejście przedstawiono na rysunku 4-11.

![Diagram przedstawiający sposób rozdzielania modelu danych na wiele modeli domen.](./media/identify-microservice-domain-model-boundaries/decompose-traditional-data-models.png)

**Rysunek 4-11**. Tworzenie tradycyjnych modeli danych w wielu modelach domen

Podczas deredagowania tradycyjnego modelu danych między ograniczonymi kontekstami można mieć różne jednostki, które współużytkują tę samą tożsamość (jest to również użytkownik) z innymi atrybutami w każdym związanym kontekście. Aby zobaczyć, jak użytkownik jest obecny w modelu mikrousług zarządzania konferencjami jako podmiot użytkownika i jest również obecny w formie jednostki kupca w mikrousłudze cenowej, z alternatywnymi atrybutami lub szczegółami dotyczącymi użytkownika, gdy jest on rzeczywiście nabywcą. Każda mikrousługa lub BC może nie potrzebować wszystkich danych związanych z jednostką użytkownika, w zależności od problemu do rozwiązania lub kontekstu. Na przykład w modelu mikrousług cenowych nie jest potrzebny adres ani nazwa użytkownika, tylko identyfikator (tożsamość) i stan, które będą miały wpływ na rabaty w przypadku, gdy ceny są dostępne dla każdego nabywcy.

Jednostka stanowiska ma taką samą nazwę, ale różne atrybuty w każdym modelu domeny. Jednak stanowisko ma tożsamość na podstawie tego samego identyfikatora, co dzieje się z użytkownikami i nabywcą.

Zasadniczo istnieje współdzielona koncepcja użytkownika, która istnieje w wielu usługach (domenach), które współużytkują tożsamość tego użytkownika. Jednak w każdym modelu domeny mogą istnieć dodatkowe lub inne szczegóły dotyczące jednostki użytkownika. W związku z tym musi być sposobem na mapowanie jednostki użytkownika z jednej domeny (mikrousługi) na inną.

Istnieje kilka korzyści, aby nie współużytkować tej samej jednostki użytkownika z tą samą liczbą atrybutów w różnych domenach. Jedną z korzyści jest zredukowanie poziomu duplikowania, dzięki czemu modele mikrousług nie mają żadnych niepotrzebnych danych. Kolejną zaletą jest posiadanie mikrousługi, która jest właścicielem pewnego typu danych na jednostkę, tak aby aktualizacje i zapytania dla tego typu danych były sterowane tylko przez tę mikrousługę.

>[!div class="step-by-step"]
>[Poprzedni](distributed-data-management.md)
>[dalej](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
