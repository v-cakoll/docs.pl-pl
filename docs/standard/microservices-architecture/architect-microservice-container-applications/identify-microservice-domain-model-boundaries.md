---
title: Identyfikowanie ograniczeń modelu domeny dla poszczególnych mikrousług
description: Zapoznaj się z essence partycjonowania dużych aplikacji na mikrousługi do osiągnięcia architektury dźwięku.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 9142c5abbbd3839caac377876ba54258cdf916b4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152503"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identyfikowanie ograniczeń modelu domeny dla poszczególnych mikrousług

Mimo, że należy zwykle kierunku małych mikrousług, jeśli jest to możliwe, aby uzyskać dostęp do najbardziej szczegółowego separacji jest to możliwe, nie jest celem identyfikowanie ograniczeń modelu i rozmiar dla poszczególnych mikrousług. Zamiast tego celem powinno być, aby uzyskać dostęp do najbardziej istotnych oddzielenie kierować swojej wiedzy specjalistycznej. Szczególnym nie ma rozmiar, ale zamiast tego możliwości biznesowych. Ponadto w przypadku zwykłego spójności potrzebne dla obszaru aplikacji oparte na dużą liczbę zależności wskazująca potrzebę pojedynczych mikrousług za. Spójności jest do identyfikowania sposobu Rozdziel lub mikrousług razem w grupy. Ostatecznie Chociaż możesz uzyskać więcej informacji o domenie, powinno się zaadaptować rozmiar Twojej mikrousług iteracyjne. Znajdowanie wielkości nie jest procesem jednorazowej.

[Newmana](https://samnewman.io/), rozpoznawanym promoter mikrousług i autora książki [tworzenie Mikrousług](https://samnewman.io/books/building_microservices/), wyróżnia się, że należy projektować mikrousługi na podstawie ograniczonego kontekstu (BC) wzorca (część opartego na domenach projektu), jak wprowadzone wcześniej. Czasami BC może składać się z kilku usług fizycznych, ale nie odwrotnie.

Model domeny przy użyciu jednostek z konkretnej domeny ma zastosowanie w konkretnych BC lub mikrousług. BC rozgranicza stosowania modelu domeny, a członkowie zespołu deweloperów zapewnia, czytelne i udostępnione znajomości co muszą być spójne i jakie mogą być tworzone niezależnie. Są to te same cele mikrousług.

Inne narzędzie, które informują uzasadnienie wyboru tych elementów jest [prawo Conway'a](https://en.wikipedia.org/wiki/Conway%27s_law), które stwierdza, że aplikacja będzie odzwierciedlać granice społecznościowych organizacji, który go. Jednak czasami przeciwieństwo obowiązuje — organizacja w firmie, jest tworzona przez oprogramowanie. Konieczne może być wycofać prawo Conway'a i tworzenie granic w sposób firmy, które mają być organizowane leaning kierunku konsultacji procesów biznesowych.

Aby zidentyfikować ograniczone konteksty, możesz użyć wzorzec DDD, o nazwie [mapowanie kontekstu wzorzec](https://www.infoq.com/articles/ddd-contextmapping). Kontekst mapowania należy zidentyfikować różnych kontekstach w aplikacji i ich granice. Jest to często mają inny kontekst i granic dla każdego podsystemu mały, na przykład. Mapa kontekstu jest sposób definiowania i jawne te granice między domenami. BC to autonomiczne i zawiera szczegółowe informacje z jednej domeny — szczegóły, takie jak jednostki domeny — i definiuje umów integracji z innych usług łączności biznesowej. Jest to podobne do definicji mikrousługi: To autonomiczne, implementuje niektórych możliwości domeny i przekazuje interfejsów. Jest to, dlaczego kontekst mapowania i wzorzec ograniczony kontekst są dobre podejścia do identyfikowania granice modelu domeny mikrousługi.

Podczas projektowania dużych aplikacji, zobaczysz, jak fragmentacji swój model domeny — eksperta domeny z domeny katalogu będzie nazwa jednostki inaczej w katalogu i spisu domeny niż domena wysyłki, ekspertów, na przykład. Lub może być innego rozmiaru i liczby atrybutów jednostki domeny użytkownika, podczas pracy z CRM ekspertów, kto chce przechowywać szczegóły każdego zdarzenia o kliencie niż dla szeregowania eksperta domeny, który potrzebuje tylko częściowe dane dotyczące klienta. Jest to bardzo trudne do odróżniania wszystkie terminy domeny we wszystkich domenach, które są związane z dużych aplikacji. Ale najbardziej ważne jest, że nie powinna próbować ujednolicenie warunki. Zamiast tego należy zaakceptować różnice i złożonością zawartym w każdej domenie. Jeśli zostanie podjęta próba zostały ujednolicony bazy danych dla całej aplikacji, próby ujednoliconego słownictwa będzie niewygodna i nie będzie dźwięk w prawo do dowolnego z wielu eksperci domeny. W związku z tym usług łączności biznesowej (zaimplementowane jako mikrousługi) pomoże Ci aby wyjaśnić, którym może korzystać z niektórych terminów domeny i gdzie należy podzielić system i utworzyć dodatkowe usług łączności biznesowej z różnymi domenami.

Będziesz wiedzieć, że masz prawo granic i rozmiarów każdego BC i modelu domeny, jeśli masz kilka silne relacje między modeli domeny i wykonaj w nie zawsze konieczne do scalenia informacji z różnych modeli domeny, podczas wykonywania operacji w typowej aplikacji .

Może być najlepszą odpowiedź na pytanie, jak duże powinny być modelu domeny dla poszczególnych mikrousług jest następująca: powinien mieć BC autonomicznych, jak izolowane, jak to możliwe, która pozwala na pracę bez konieczności stale przechodzenia do innych kontekstach, (inne modele w mikrousługach). Na rysunku 4-10, możesz zobaczyć jak wiele mikrousług (wiele usług łączności biznesowej) każdego ma swoje własne modelu i sposób ich jednostek można zdefiniować, w zależności od określonych wymagań dla każdej z domen określonych w aplikacji.

![Jednostki w kilku modelu granic (ograniczone konteksty), gdzie tej samej jednostki, jest wyświetlany jako "Użytkownicy", "Kupujący", "Podatników" i "Klienci" w zależności od ograniczony kontekst](./media/image10.png)

**Rysunek 4 – 10**. Identyfikowanie jednostek i granice modelu mikrousług

Rysunek 4 – 10 przedstawia przykładowy scenariusz związane z systemu zarządzania konferencjami online. Zidentyfikowaliśmy kilka usług łączności biznesowej, które można zaimplementować jako mikrousługi, na podstawie domen, zdefiniowane przez ekspertów z konkretnych dziedzin dla Ciebie. Jak widać, że istnieją jednostek, które znajdują się tylko w modelu pojedynczych mikrousług, takich jak płatności w mikrousługach płatności. Te będą łatwe do wdrożenia.

Jednak może również być jednostek, które dysponują innego kształtu, ale udostępnianie tej samej tożsamości w wielu modeli domeny z wielu mikrousług. Na przykład jednostka użytkownika jest identyfikowane w mikrousługach zarządzania konferencjami. Tego samego użytkownika z tą samą tożsamością jest jeden o nazwie kupujący w mikrousługach porządkowanie, co najmniej jeden o nazwie płatnika w mikrousługach płatności, a nawet jednego o nazwie klienta mikrousług działem obsługi klienta. Jest to spowodowane w zależności od [wszechobecne języka](https://martinfowler.com/bliki/UbiquitousLanguage.html) , korzysta z każdego eksperta domeny, użytkownik może mieć różne perspektywy, nawet w przypadku różnych atrybutów. Jednostka użytkownika w modelu mikrousług, o nazwie zarządzania konferencjami może być najbardziej jego atrybuty danych osobowych. Jednak że tego samego użytkownika w kształcie płatnika w mikrousługach płatności lub w kształcie klienta w mikrousługach działem obsługi klienta nie może być konieczne taką listą atrybutów.

Podejście podobne zilustrowano w rysunek 4 – 11.

![Podczas podzielenie modelu tradycyjnym danych między ograniczone konteksty, możesz mieć różnych obiektów, które mają taką samą tożsamość (kupujący jest również użytkownikiem) z różnymi atrybutami w poszczególnych kontekstach.](./media/image11.png)

**Rysunek 4 – 11**. Podzielenie modeli tradycyjnych danych wielu modeli domeny

Zobaczysz, jak użytkownik znajduje się w modelu mikrousług zarządzania konferencjami jako jednostki użytkownika i również znajduje się w formularzu jednostki nabywcy w mikrousługach ceny, za pomocą alternatywnej atrybutów lub szczegółowe informacje o użytkowniku, gdy jest ona rzeczywiście kupujący. Każda mikrousługa lub BC nie może być konieczne wszystkie dane powiązane z jednostką użytkownika, po prostu część, w zależności od problemu do rozwiązania lub w kontekście. Na przykład w modelu mikrousług cen, nie trzeba adres lub nazwę użytkownika, po prostu identyfikator (jako tożsamość) i stan, który będzie miało wpływ na rabaty, gdy ceny stanowisk na kupujący.

Jednostki stanowisko ma taką samą nazwę, ale różnych atrybutów w każdym modelu domeny. Jednak stanowisko udostępnia tożsamości, w oparciu o takim samym Identyfikatorem, jak to się dzieje z użytkowników i kupujący.

Zasadniczo jest udostępniony koncepcji użytkownika, który znajduje się w wielu usług (domeny), których udostępnianie tożsamości danego użytkownika. Ale w każdym modelu domeny może być dodatkowym lub innym szczegóły jednostki użytkownika. W związku z tym musi istnieć sposób mapowania jednostki użytkownika z jednej domeny (mikrousług) do innego.

Istnieje wiele korzyści związanych z nie udostępnianie tej samej jednostki użytkownika z taką samą liczbę atrybutów między domenami. Jedną z zalet jest zmniejszenie duplikatów, tak aby mikrousług modele nie masz żadnych danych, która nie ma potrzeby. Kolejną korzyścią występują wzorca mikrousług, który jest właścicielem określonego typu danych na jednostkę, aby aktualizacje i zapytania dla tego typu danych, które są sterowane tylko przez tego mikrousług.

>[!div class="step-by-step"]
>[Poprzednie](distributed-data-management.md)
>[dalej](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)