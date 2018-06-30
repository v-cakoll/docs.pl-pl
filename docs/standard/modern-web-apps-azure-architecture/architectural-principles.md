---
title: Zasady architektury
description: Projektowania nowoczesnych aplikacji sieci Web platformy ASP.NET Core i Azure | Zasady architektury
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: 4ee14b128d3b83fd446352bb6f78afc08fb38c52
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105862"
---
# <a name="architectural-principles"></a>Zasady architektury

> "Jeśli konstruktorów wbudowana budynków programistów sposób zapisano programy, a następnie woodpecker pierwszy, dostarczonej wraz z spowodowałoby zniszczenie cywilizacji."  
> _\- Jan Weinberg_

## <a name="summary"></a>Podsumowanie

Należy zaprojektować i projektowania rozwiązań w zakresie oprogramowania z utrzymanie pamiętać. Zasady opisane w tej sekcji pomocne kierunku architektury decyzje, które będą powodować czystą, łatwy w obsłudze aplikacji. Ogólnie rzecz biorąc te zasady przeprowadzi Cię do tworzenia aplikacji poza odrębny składników, które nie są ściśle powiązane do innych części aplikacji, ale raczej komunikują się za pośrednictwem jawne interfejsy lub systemami wiadomości.

## <a name="common-design-principles"></a>Wspólne zasady projektowania

### <a name="separation-of-concerns"></a>Separacji

Jest wiodącą zasadę podczas opracowywania **separacji dotyczy**. Ta zasada potwierdza, powinny być oddzielone oprogramowania zależności od rodzaju pracy, którą wykonuje. Załóżmy na przykład, aplikacji, która zawiera logikę do identyfikacji warte wymienienia elementów do wyświetlenia dla użytkownika, a które formatuje w określony sposób, aby były bardziej widoczne takie elementy. Zachowanie odpowiedzialny za wybierania elementów do formatu powinny być przechowywane oddzielnie od zachowania odpowiedzialny za formatowania elementów, ponieważ są one oddzielne zagadnienia są tylko przypadkowo ze sobą powiązane.

Pod względem architektury aplikacje mogą być logicznie wbudowane do wykonania tej zasady oddzielając zachowanie firm core z infrastruktury i użytkownika logikę interfejsu. W idealnym przypadku reguł biznesowych i logiki powinien znajdować się w oddzielnych projektu, który nie należy uwzględniać inne projekty w aplikacji. Pomaga to zapewnić, że modelu biznesowego jest prosty do testowania i można rozwijać bez są ściśle powiązane szczegóły implementacji niskiego poziomu. Separacji kluczowa jest za korzystanie z warstw w architekturach aplikacji.

### <a name="encapsulation"></a>Hermetyzacja protokołu

Różne części aplikacji należy używać **hermetyzacji** aby ochronić ich z innymi częściami aplikacji. Składniki aplikacji i warstwach powinno być możliwe dostosowanie ich wewnętrznej implementacji bez przerywania ich współpracownicy, dopóki nie naruszenia zamówień zewnętrznych. Właściwe korzystanie z hermetyzacji pomaga osiągnąć luźne powiązanie i Modułowość projektów aplikacji, ponieważ obiekty i pakietów można zastąpić alternatywnych implementacji tak długo, jak ten sam interfejs jest obsługiwany.

W klasach hermetyzacji uzyskuje się poprzez ograniczenie poza dostęp do wewnętrzny stan klasy. Jeśli poza aktora chce manipulowania stan obiektu, go należy to zrobić za pośrednictwem funkcji dobrze zdefiniowany (lub metoda ustawiająca właściwości), zamiast bezpośredniego dostępu do prywatnego stan obiektu. Podobnie składniki aplikacji i same aplikacje powinny ujawniać dobrze zdefiniowanych interfejsów dla swoich współpracowników do użycia zamiast stosowanie ich stanie można zmodyfikować bezpośrednio. Dzięki temu aplikacja — projekt wewnętrzny podlegać ewolucji w czasie, nie martwiąc się, że to tak spowoduje przerwanie współpracownikom, tak długo, jak zamówień publicznych, które są obsługiwane.

### <a name="dependency-inversion"></a>Odwracanie zależności

Kierunek zależności aplikacji powinna być w kierunku abstrakcji, nie szczegóły implementacji. Większość aplikacji są zapisywane w taki sposób, że zależności kompilacji przepływów w kierunku wykonywania środowiska wykonawczego. To tworzy wykres zależności bezpośrednich. Oznacza to jeśli moduł A wywołań w funkcji w module B, które wywołuje funkcję w module C, a następnie w momencie czasu A kompilacji są zależne od B, który będzie zależeć od C, jak pokazano w rysunek 4-1.

![](./media/image4-1.png)

**Rysunek 4-1.** Wykres zależności bezpośrednich.

Zastosowanie zasady odwracanie zależności umożliwia A może wywołać metody abstrakcji, która implementuje B, umożliwiając a wywołania B w czasie wykonywania, ale b zależeć interfejs sterowane przez A w czasie kompilacji (w związku z tym *odwracanie* Typowy kompilacji zależności). W czasie wykonywania przepływ wykonania programu nie zostanie zmienione, ale wprowadzenie interfejsy oznacza, że łatwo można podłączyć różnych implementacji tych interfejsów.

![](./media/image4-2.png)

**Rysunek 4-2.** Wykres zależności odwrócony.

**Odwracanie zależności** jest kluczowym elementem tworzenia luźno połączonych aplikacji, ponieważ szczegóły implementacji mogą być zapisywane są zależne od i wdrożenie nowszej abstrakcje poziomu, a nie odwrotnie. Wynikowa aplikacje są w związku z tym testować, moduły i łatwy w obsłudze. Rozwiązanie polegające na *iniekcji zależności* jest możliwe dzięki zgodnie z zasadą odwracanie zależności.

### <a name="explicit-dependencies"></a>Jawne zależności

**Klasy i metody jawnie należy włączyć wszystkie brać obiekty, które są im niezbędne do poprawnego działania.** Konstruktory klas możliwość klas zidentyfikować elementy, które są im potrzebne, aby mogła być w nieprawidłowym stanie i działać prawidłowo. Po zdefiniowaniu klasy, która konstruowane i o nazwie, ale który będzie działać tylko prawidłowo w przypadku niektórych składników infrastruktury lub globalnych w miejscu tych klas są *nieuczciwych* z klientów. Kontrakt konstruktora informuje klienta, który wymaga tylko określone czynności (prawdopodobnie pusta, jeśli klasa jest tylko za pomocą konstruktora domyślnego), ale, a następnie w czasie wykonywania, który okaże się obiekt naprawdę prawdopodobnie potrzebował coś innego.

Wykonując zasady jawne zależności z klasy i metody są uczciwymi z klientów o to, czego szukają prawidłowego działania. Dzięki temu kodu więcej pomocniczy i kodowania umów bardziej przyjazny dla użytkownika, ponieważ użytkownicy będą zaufania, który tak długo, jak udostępniają one, co jest wymagane w formularzu metodę lub parametrami konstruktora, obiekty, które pracują z będą zachowywać się poprawnie w czasie wykonywania.

### <a name="single-responsibility"></a>Pojedynczy odpowiedzialności

Zasady odpowiedzialności pojedynczego dotyczy obiektowego, ale również mogą być uważane za podobne do separacji zasady architektury. Stany go, że obiekty muszą mieć tylko jeden odpowiedzialność i powinny mieć tylko jedną z przyczyn można zmienić. Tylko sytuacji, w której należy zmienić obiekt jest w szczególności jeśli musisz zaktualizować sposób, w której wykonuje jej odpowiedzialność jeden. Po tej zasady pozwala tworzyć więcej luźno połączonych i moduły systemów, ponieważ wiele rodzajów nowe zachowanie może być zaimplementowany jako nowe klasy, a nie przez dodanie dodatkowych odpowiedzialność na istniejących klas. Dodanie nowych klas jest bezpieczniejsze niż zmiana istniejących klas, ponieważ żaden kod jeszcze zależy od nowych klas.

W aplikacji wbudowanymi firma Microsoft może dotyczyć zasady pojedynczego odpowiedzialność na wysokim poziomie warstw w aplikacji. Odpowiedzialność prezentacji może pozostawać w projekcie interfejsu użytkownika, podczas dostępu do danych odpowiedzialność powinny być przechowywane w ramach projektu infrastruktury. Logika biznesowa powinna być przechowywana w core projekt aplikacji, których można łatwo przetestować i można rozwijać, niezależnie od innych obowiązków.

Podczas tej zasady jest stosowany do architektury aplikacji i Przekierowanie do punktu końcowego logiczne, otrzymasz mikrousług. Danego mikrousługi powinien mieć pojedynczy odpowiedzialności. Jeśli chcesz rozszerzyć zachowanie systemu, zazwyczaj lepiej jest to zrobić przez dodanie dodatkowych mikrousług, a nie przez dodanie odpowiedzialność do istniejącego.

[Dowiedz się więcej o architekturze mikrousług](http://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Nie powtarzaj samodzielnie (suchej)

Aplikacji należy unikać, określając zachowanie związane z określonym koncepcji w kilku miejscach, jak jest to często źródła błędów. W pewnym momencie zmiany wymagań dotyczących wymaga zmiany tego zachowania oraz prawdopodobieństwo, że co najmniej jedno wystąpienie zachowania zakończy się niepowodzeniem, należy zaktualizować spowoduje niespójne działanie systemu.

Zamiast duplikowania logiki, hermetyzować go w konstrukcji programowania. Uczyń tę konstruowania pojedynczego urzędu za pośrednictwem tego zachowania, i mieć dowolną część aplikacji, która wymaga użycia tego zachowania nową konstrukcję.

> [!NOTE]
> Unikaj powiązanie ze sobą zachowanie tylko przypadkowo powtarzających się. Na przykład wyłącznie z powodu dwóch różnych stałe zarówno mają taką samą wartość, która nie oznacza powinien mieć tylko jedną stałą, jeśli koncepcyjnie odnoszą się różne.

### <a name="persistence-ignorance"></a>Nieznajomości trwałości

**Trwałość nieznajomości** (PI) odwołuje się do typów, które mają zostać utrwalony, którego kod jest poza zasięgiem Wybór technologii trwałości. Takie typy w programie .NET są czasami określane jako zwykły stare obiekty CLR (POCOs), ponieważ nie muszą dziedziczyć konkretnej klasy podstawowej ani nie implementuje danego interfejsu. Nieznajomości trwałości jest przydatne, ponieważ zezwala ona na ten sam model firm utrwalenia na wiele sposobów, oferty dodatkowa elastyczność w aplikacji. Opcji trwałości mogą ulec zmianie w czasie z technologii jedną bazę danych do innego, lub dodatkowych metod trwałości mogą być wymagane, oprócz niezależnie od uruchomienia z aplikacji (na przykład przy użyciu pamięci podręcznej Redis lub usługi Azure DocumentDb oprócz relacyjna baza danych).

Przykładem naruszenia tej zasady obejmują:

-   Wymagane klasy podstawowej

-   Implementacji wymaganego interfejsu

-   Klasy odpowiedzialne za zapisywanie się (na przykład wzorzec aktywnym rekordzie)

-   Wymagane domyślnego konstruktora

-   Właściwości wymagających virtual — słowo kluczowe

-   Specyficzne dla trwałości wymaganych atrybutów.

To wymaganie, że klasy nie ma żadnej z powyższych funkcji lub zachowania dodaje sprzężenia między typami utrwalenia i wybór technologii trwałości, co utrudnia przyjęcie nowych strategii dostępu do danych w przyszłości.

### <a name="bounded-contexts"></a>Konteksty ograniczonego

**Ograniczone kontekstów** są centralnej wzorzec projektowania Domain-Driven. Umożliwiają realizowanie złożoności w dużych aplikacji lub organizacje przez podzielenie go na oddzielnych modułów koncepcyjnego. Każdy moduł koncepcyjnej następnie reprezentuje kontekst, który jest oddzielona od innych kontekstach (w związku z tym ograniczone) i można rozwijać niezależnie. Każdy kontekst ograniczonego w idealnym przypadku należy wybrać własne nazwy dla pojęcia znajdujące się w nim, a powinien mieć wyłącznego dostępu do magazynu trwałości.

Co najmniej aplikacji sieci web poszczególnych powinien starań, aby mieć własne ograniczonego kontekstu, za pomocą ich własnych magazynu trwałości dla swojego modelu biznesowego, a nie z innych aplikacji do udostępniania bazy danych. Komunikacja między kontekstami ograniczonego następuje za pośrednictwem interfejsów programistycznych, a nie za pomocą udostępnionej bazy danych, dzięki czemu do obsługi logiki biznesowej i zdarzenia podjęcie umieścić w odpowiedzi na zmiany, które mają miejsce. Ściśle ograniczone kontekstów mapy do mikrousług, który również w idealnym przypadku są zaimplementowane jako własne poszczególnych kontekstów ograniczone.

> ### <a name="references--modern-web-applications"></a>Odwołania — nowoczesnych aplikacji sieci Web
> - **Separacji**  
> <http://deviq.com/separation-of-concerns/>
> - **Hermetyzacja protokołu** <http://deviq.com/encapsulation/>
> - **Zasada odwracanie zależności**  
> <http://deviq.com/dependency-inversion-principle/>
> - **Zasada jawne zależności**  
> <http://deviq.com/explicit-dependencies-principle/>
> - **Nie powtarzaj samodzielnie**  
> <http://deviq.com/don-t-repeat-yourself/>
> - **Nieznajomości trwałości**  
> <http://deviq.com/persistence-ignorance/>
> - **Kontekst ograniczonego**  
> <https://martinfowler.com/bliki/BoundedContext.html>

> [!div class="step-by-step"]
[Poprzednie](choose-between-traditional-web-and-single-page-apps.md)
[dalej](common-web-application-architectures.md)
