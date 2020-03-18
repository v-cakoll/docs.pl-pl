---
title: Identyfikowanie ograniczeń modelu domeny dla poszczególnych mikrousług
description: Eksploruj istotę partycjonowania dużej aplikacji na mikrousługi w celu uzyskania architektury dźwięku.
ms.date: 09/20/2018
ms.openlocfilehash: 9c433066dd8e93dbb09b15e58c9c85617775723d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834413"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identyfikowanie granic modelu domeny dla każdej mikrousługi

Celem podczas identyfikowania granic modelu i rozmiar dla każdej mikrousługi nie jest, aby uzyskać do najbardziej szczegółowe separacji możliwe, mimo że należy dążyć do małych mikrousług, jeśli to możliwe. Zamiast tego twoim celem powinno być dotarcie do najbardziej znaczącej separacji opartej na wiedzy o domenie. Nacisk nie kładzie się na rozmiar, ale na możliwości biznesowe. Ponadto jeśli istnieje spójność jest potrzebna dla określonego obszaru aplikacji na podstawie dużej liczby zależności, co wskazuje na potrzebę pojedynczej mikrousługi, zbyt. Spójność jest sposobem, aby określić, jak rozdzielić lub grupować mikrousług. Ostatecznie podczas uzyskiwania większej wiedzy na temat domeny, należy dostosować rozmiar mikrousługi, iteracyjne. Znalezienie odpowiedniego rozmiaru nie jest procesem jednorazowym.

[Sam Newman](https://samnewman.io/), uznany promotor mikrousług i autor książki [Building Microservices](https://samnewman.io/books/building_microservices/), podkreśla, że należy zaprojektować mikrousług na podstawie wzorca ograniczonego kontekstu (BC) (część projektu opartego na domenie), jak wprowadzono wcześniej. Czasami bc może składać się z kilku usług fizycznych, ale nie odwrotnie.

Model domeny z określonymi jednostkami domeny ma zastosowanie w obrębie konkretnego bc lub mikrousługi. Bc ogranicza możliwość stosowania modelu domeny i daje członkom zespołu deweloperów jasne i wspólne zrozumienie tego, co musi być spójność i co może być rozwijany niezależnie. Są to te same cele dla mikrousług.

Innym narzędziem, które informuje o wyborze projektu jest [prawo Conwaya,](https://en.wikipedia.org/wiki/Conway%27s_law)które stanowi, że aplikacja będzie odzwierciedlać granice społeczne organizacji, która go wyprodukowała. Ale czasami jest odwrotnie - organizacja firmy jest tworzona przez oprogramowanie. Być może trzeba odwrócić prawo Conway i budować granice tak, jak chcesz, aby firma została zorganizowana, opierając się w kierunku doradztwa procesowego.

Aby zidentyfikować ograniczone konteksty, można użyć wzorca DDD o nazwie [wzorzec mapowania kontekstu](https://www.infoq.com/articles/ddd-contextmapping). Za pomocą mapowania kontekstu można zidentyfikować różne konteksty w aplikacji i ich granice. Często ma inny kontekst i granicę dla każdego małego podsystemu, na przykład. Mapa kontekstowa jest sposobem definiowania i jawnego określania tych granic między domenami. Bc jest autonomiczny i zawiera szczegóły pojedynczej domeny - szczegóły, takie jak jednostki domeny- i definiuje umowy integracji z innymi bc. Jest to podobne do definicji mikrousługi: jest autonomiczny, implementuje niektóre możliwości domeny i musi zapewnić interfejsy. Dlatego mapowanie kontekstu i wzorzec kontekstu ograniczone są dobre podejścia do identyfikowania granic modelu domeny mikrousług.

Podczas projektowania dużej aplikacji zobaczysz, jak można pofragmentować jej model domeny — ekspert domeny z domeny katalogu będzie na przykład nazywał jednostki w domenach wykazu i zapasów niż ekspert domeny wysyłkowej. Lub jednostka domeny użytkownika może być różny pod względem wielkości i liczby atrybutów w kontaktach z ekspertem CRM, który chce przechowywać każdy szczegół o kliencie niż dla eksperta domeny zamawiania, który potrzebuje tylko częściowe dane o kliencie. Bardzo trudno jest rozróżnić wszystkie terminy domen we wszystkich domenach związanych z dużą aplikacją. Ale najważniejsze jest to, że nie powinieneś próbować jednoczyć terminów. Zamiast tego zaakceptuj różnice i bogactwo zapewniane przez każdą domenę. Jeśli spróbujesz mieć ujednoliconą bazę danych dla całej aplikacji, próby jednolitego słownictwa będą niewygodne i nie będą brzmieć dobrze dla żadnego z wielu ekspertów domeny. W związku z tym kontrolerów domeny (zaimplementowane jako mikrousług) pomoże Ci wyjaśnić, gdzie można użyć niektórych terminów domeny i gdzie trzeba podzielić system i utworzyć dodatkowe kontrolery bcs z różnych domen.

Będziesz wiedzieć, że masz odpowiednie granice i rozmiary każdego bc i modelu domeny, jeśli masz kilka silnych relacji między modelami domeny i zwykle nie trzeba scalać informacje z wielu modeli domenpodczas wykonywania typowych operacji aplikacji .

Być może najlepszą odpowiedzią na pytanie, jak duży powinien być model domeny dla każdej mikrousługi, jest następujący: powinien mieć autonomiczny bc, tak izolowany, jak to możliwe, który umożliwia pracę bez konieczności ciągłego przełączania się do innych kontekstów (inne modeli mikrousług). Na rysunku 4-10, można zobaczyć, jak wiele mikrousług (wiele kontrolerów bcs) każdy ma swój własny model i jak ich jednostki mogą być zdefiniowane, w zależności od określonych wymagań dla każdej z domen zidentyfikowanych w aplikacji.

![Diagram przedstawiający jednostki w kilku granicach modelu.](./media/identify-microservice-domain-model-boundaries/identify-entities-microservice-model-boundries.png)

**Rysunek 4-10**. Identyfikowanie jednostek i granic modelu mikrousług

Rysunek 4–10 przedstawia przykładowy scenariusz związany z systemem zarządzania konferencjami online. Ta sama jednostka jest wyświetlana jako "Użytkownicy", "Kupujący", "Płatnicy" i "Klienci" w zależności od ograniczonego kontekstu. Zidentyfikowano kilka kontrolerów bcs, które mogą być implementowane jako mikrousług, na podstawie domen, które eksperci domeny zdefiniowane dla Ciebie. Jak widać istnieją jednostki, które są obecne tylko w jednym modelu mikrousługi, takich jak płatności w mikrousługi płatności. Będą one łatwe do wdrożenia.

Jednak może również mieć jednostki, które mają inny kształt, ale mają tę samą tożsamość w wielu modelach domeny z wielu mikrousług. Na przykład User jednostka jest identyfikowana w mikrousługi zarządzania konferencjami. Ten sam użytkownik, o tej samej tożsamości, jest jednym o nazwie Kupujący w mikrousługi zamawiania lub jeden o nazwie Płatnik w mikrousługi płatności, a nawet jeden o nazwie Klienta w mikrousłudze obsługi klienta. Dzieje się tak, ponieważ w zależności od [wszechobecnego języka,](https://martinfowler.com/bliki/UbiquitousLanguage.html) z których korzysta każdy ekspert domeny, użytkownik może mieć inną perspektywę nawet z różnymi atrybutami. Jednostka użytkownika w modelu mikrousługi o nazwie Conferences Management może mieć większość swoich atrybutów danych osobowych. Jednak ten sam użytkownik w kształcie płatnika w mikrousługi Płatności lub w kształcie Klienta w mikrousług obsługi klienta może nie potrzebować tej samej listy atrybutów.

Podobne podejście przedstawiono na rysunku 4-11.

![Diagram przedstawiający sposób rozkładu modelu danych na wiele modeli domen.](./media/identify-microservice-domain-model-boundaries/decompose-traditional-data-models.png)

**Rysunek 4-11**. Rozkładanie tradycyjnych modeli danych na wiele modeli domen

Podczas rozkładu tradycyjnego modelu danych między kontekstami ograniczonymi, można mieć różne jednostki, które mają tę samą tożsamość (kupujący jest również użytkownikiem) z różnymi atrybutami w każdym kontekście ograniczonym. Można zobaczyć, jak użytkownik jest obecny w modelu mikrousługi Zarządzanie konferencjami jako user jednostki i jest również obecny w postaci jednostki Kupujący w mikrousługi cen, z alternatywnych atrybutów lub szczegółów dotyczących użytkownika, gdy jest to rzeczywiście nabywcy. Każda mikrousługa lub BC może nie potrzebować wszystkich danych związanych z user jednostki, tylko część z nich, w zależności od problemu do rozwiązania lub kontekstu. Na przykład w modelu mikrousługi cen nie trzeba adres lub nazwę użytkownika, tylko identyfikator (jako tożsamość) i stan, które będą miały wpływ na rabaty podczas wyceny miejsc na kupującego.

Encja Seat ma taką samą nazwę, ale różne atrybuty w każdym modelu domeny. Seat udostępnia jednak tożsamość na podstawie tego samego identyfikatora, tak jak ma to miejsce w przypadku Użytkownika i Kupującego.

Zasadniczo istnieje wspólna koncepcja użytkownika, która istnieje w wielu usługach (domenach), które współużytkują tożsamość tego użytkownika. Jednak w każdym modelu domeny mogą istnieć dodatkowe lub różne szczegóły dotyczące encji użytkownika. W związku z tym musi istnieć sposób mapowania jednostki użytkownika z jednej domeny (mikrousługi) do innej.

Istnieje kilka korzyści, aby nie udostępniać tej samej jednostki użytkownika z taką samą liczbą atrybutów w różnych domenach. Jedną z zalet jest zmniejszenie powielania, dzięki czemu modele mikrousług nie mają żadnych danych, które nie są potrzebne. Inną korzyścią jest posiadanie mikrousługi wzorcowej, która jest właścicielem określonego typu danych na jednostkę, dzięki czemu aktualizacje i zapytania dla tego typu danych są napędzane tylko przez tę mikrousługę.

>[!div class="step-by-step"]
>[Poprzedni](distributed-data-management.md)
>[następny](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
