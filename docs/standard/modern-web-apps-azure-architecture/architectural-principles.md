---
title: Zasady dotyczące architektury
description: Projektowania nowoczesnych aplikacji sieci Web za pomocą platformy ASP.NET Core i platformy Azure | Zasady dotyczące architektury
author: ardalis
ms.author: wiwagn
ms.date: 02/16/2019
ms.openlocfilehash: 7d127476e37b9eefa9ddc13d26991145b6245b45
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442987"
---
# <a name="architectural-principles"></a>Zasady dotyczące architektury

> "Jeśli Konstruktorzy wbudowana budynki programistów sposób napisane programy, a następnie pierwszy woodpecker, dostarczonej wraz może zniszczyć civilization."  
> _\- Jan Weinberg_

Należy architektury i projektowania rozwiązania oparte na oprogramowaniu łatwość konserwacji na uwadze. Zasady przedstawione w tej sekcji pomocne kierunku decyzje architektoniczne, które będą powodować aplikacje zawsze przejrzyste i łatwego w utrzymaniu. Ogólnie rzecz biorąc te zasady przeprowadzi Cię do tworzenia aplikacji poza osobne składniki, które nie są ściśle powiązane z innymi częściami aplikacji, ale raczej komunikowania się poprzez jawne interfejsy lub systemami wiadomości.

## <a name="common-design-principles"></a>Wspólne zasady projektowania

### <a name="separation-of-concerns"></a>Separacji

Jest wiodącą zasadę podczas opracowywania **oddzielenie obaw**. Ta zasada potwierdza, powinny być oddzielone oprogramowania zależnie od rodzaju pracy, który wykonuje. Załóżmy na przykład, aplikacja, która zawiera logikę do identyfikowania warte zauważenia elementów do wyświetlenia dla użytkownika i takich pozycji, które formatuje w określony sposób, aby były lepiej widoczne. Zachowanie odpowiedzialny za wybierania elementów do formatu powinny być oddzielone od zachowania odpowiedzialny za formatowanie elementów, ponieważ te oddzielne wątpliwości, tylko przypadkowo powiązanych ze sobą.

Po architektonicznie aplikacje mogą być logicznie wbudowane do wykonania tej zasady, oddzielając zachowanie firm core od logiki interfejsu infrastruktury i użytkownika. W idealnym przypadku reguł biznesowych i logiki powinien znajdować się w osobnym projekcie nie powinna zależeć od innych projektów w aplikacji. Pozwala to zagwarantować, że model biznesowy jest łatwe do testowania i można rozwijać bez są ściśle powiązane szczegóły implementacji niskiego poziomu dostępu. Separacji kluczowa jest za użycie warstw w architekturach aplikacji.

### <a name="encapsulation"></a>Hermetyzacja protokołu

Różne części aplikacji należy używać **hermetyzacji** aby uwolnić ich z innych części aplikacji. Składniki aplikacji i warstwy powinno być możliwe dostosować ich wewnętrznej implementacji bez przerywania ich współpracowników, tak długo, jak zamówień zewnętrznych nie są naruszone. Polecenia COUNT_BIG hermetyzacji pomaga osiągnąć luźne powiązania i Modułowość projektów aplikacji, ponieważ obiekty i pakietów można zastąpić za pomocą alternatywnych implementacji tak długo, jak długo jest obsługiwany przez ten sam interfejs.

W klasach hermetyzacji uzyskuje się poprzez ograniczenie poza dostęp do tej klasy wewnętrzny stan. Jeśli zewnętrznego aktora chce, aby manipulować stan obiektu, go powinien zrobić za pomocą dobrze zdefiniowanych — funkcja (lub metoda ustawiająca właściwości), zamiast bezpośredniego dostępu do prywatnych stan obiektu. Podobnie składniki aplikacji i same aplikacje powinny ujawniać dobrze zdefiniowanych interfejsów dla swoich współpracowników do użycia zamiast zezwalać ich stan bezpośrednio modyfikować. Dzięki temu aplikacja wewnętrzną konstrukcją rozwój wraz z upływem czasu, nie martwiąc się, wykonanie tej tak spowoduje przerwanie współpracownikom, tak długo, jak zamówienia publiczne są obsługiwane.

### <a name="dependency-inversion"></a>Odwracanie zależności

Kierunek zależności w ramach aplikacji powinna mieć kierunek abstrakcji, nie szczegółów implementacji. Większość aplikacji są zapisywane w taki sposób, że zależności kompilacji przepływy w kierunku realizacji środowiska uruchomieniowego. To tworzy wykres zależności bezpośrednich. Oznacza to jeśli moduł A wywołuje funkcję w module B, które wywołuje funkcję w module języka C, a następnie w momencie czasu A kompilacji są zależne od B, która zależeć będzie od C, jak pokazano w rysunek 4-1.

![](./media/image4-1.png)

**Rysunek 4-1.** Wykres zależności bezpośrednich.

Stosowanie zasady czystego odwrócenie zależności pozwala na wywoływanie metod na klasą abstrakcyjną, która implementuje B, umożliwiając a wywołanie B w czasie wykonywania, ale b była zależna od interfejsu kontrolowane przez element w czasie kompilacji (w związku z tym, *odwracanie* Typowe kompilacji zależności). W czasie wykonywania przepływem wykonania programu nie jest zmieniany, ale wprowadzenie interfejsów oznacza, że różne implementacje tych interfejsów można łatwo podłączyć.

![](./media/image4-2.png)

**Rysunek 4-2.** Wykres zależności odwrócony.

**Odwracanie zależności** jest kluczowym elementem tworzenia aplikacji luźno powiązane, ponieważ szczegóły implementacji mogą być zapisywane są zależne od do zaimplementowania wyższym poziomie abstrakcji, a nie odwrotnie. Wynikowy aplikacje są w wyniku zakresie testować, moduły i łatwego w utrzymaniu. Praktyka *wstrzykiwanie zależności* jest możliwe dzięki zgodnie z zasadą odwrócenie zależności.

### <a name="explicit-dependencies"></a>Jawne zależności

**Klasy i metody jawnie wymagać współpracujących obiekty, które są im potrzebne, aby działać poprawnie.** Konstruktory klasy zapewnienia możliwości dla klas zidentyfikować elementy, które są im potrzebne, aby mieć prawidłowy stan i działać prawidłowo. Po zdefiniowaniu klasy, która skonstruowany oraz o nazwie, ale które będzie działać tylko prawidłowo w przypadku niektórych składników administratorem globalnym lub infrastruktury w miejscu, w ramach tych zajęć są *nieuczciwych* za pomocą swoich klientów. Kontrakt konstruktora o tym, że klienta, który wymaga tylko określone czynności (prawdopodobnie pusta, jeśli klasa jest po prostu przy użyciu domyślnego konstruktora), ale, a następnie w czasie wykonywania, który okazuje się obiekt rzeczywiście potrzebujesz czegoś innego.

Postępując zgodnie z zasadą jawne zależności, metod i klas są uczciwe za pomocą swoich klientów o to, czego potrzebują do działania. To sprawia, że Twój kod więcej pomocniczy i kodowania kontraktów bardziej przyjazny dla użytkownika, ponieważ użytkownicy będą ufać, że tak długo, jak długo stanowią, co jest wymagane w formularzu metodę lub parametry konstruktora, obiekty, które działają z będzie działać. poprawnie w czasie wykonywania.

### <a name="single-responsibility"></a>Pojedynczej odpowiedzialności

Zasada pojedynczej odpowiedzialności ma zastosowanie do projektu, obiektowy, ale również może być traktowany jako zasady architektury, podobnie jak separacji zagadnień. Stwierdza, że obiekty powinny mieć tylko jeden odpowiedzialności i powinny mieć tylko jedną z przyczyn można zmienić. W szczególności jedyną sytuacją, w którym należy zmieniać obiekt jest taki sposób, w którym wykonuje swoją odpowiedzialność co muszą zostać zaktualizowane. Po tej zasady pozwala tworzyć bardziej luźno połączonych, i moduły systemów, ponieważ wiele rodzajów nowe zachowanie można zaimplementować jako nowe klasy, a nie przez dodanie dodatkowych odpowiedzialność za istniejących klas. Dodawanie nowych klas jest bezpieczniejsze niż zmiana istniejących klas, ponieważ brak kodu, ale zależy od nowych klas.

W aplikacji monolitycznej możemy zastosować zasady pojedynczej odpowiedzialności na wysokim poziomie do warstw w aplikacji. Odpowiedzialność prezentacji może pozostawać w projekt interfejsu użytkownika, podczas dostępu do danych odpowiedzialność powinny być przechowywane w ramach projektu infrastruktury. Logika biznesowa powinna być ograniczona w projekcie podstawowych aplikacji, którym można łatwo przetestować i może się rozwijać, niezależnie od innych obowiązków.

Jeśli zasada ta jest stosowane do architektury aplikacji i podjęte w celu jego logicznym punktem końcowym, uzyskasz dostęp mikrousług. Mikrousługi danego powinien mieć jeden obszar odpowiedzialności. Jeśli chcesz rozszerzyć zachowania systemu, jest zazwyczaj lepiej to zrobić, dodając dodatkowe mikrousług, a nie przez dodanie odpowiedzialność za istniejącą grupę.

[Dowiedz się więcej na temat architektury mikrousług](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Nie powtarzaj samodzielnie (PRÓBNEGO)

Aplikację należy unikać, określając zachowanie związane z określonym pojęcie w wielu miejscach, jak jest to częste źródło błędy. W pewnym momencie zmiany w wymaganiach wymaga zmianę tego zachowania oraz prawdopodobieństwo, że co najmniej jedno wystąpienie zachowanie zakończy się niepowodzeniem, należy zaktualizować spowoduje niespójne zachowanie systemu.

Zamiast duplikowania logiki, należy hermetyzować w konstrukcji programowania. Ustaw konstruowania pojedynczego urzędu za pośrednictwem tego zachowania, a także mieć innych części aplikacji, która wymaga użycia tego zachowania nową konstrukcję.

> [!NOTE]
> Należy unikać powiązanie ze sobą zachowanie tylko przypadkowo powtarzających się. Na przykład po prostu, ponieważ dwie różne stałe zarówno mają taką samą wartość, nie oznacza powinien mieć tylko jedną stałą, jeśli koncepcyjnie one odwoływaniu się do różnych rzeczy.

### <a name="persistence-ignorance"></a>Nieznajomości trwałości

**Trwałość nieznajomości** (PI), który odnosi się do typów, które mają zostać utrwalona, którego kod jest jednak wpływu na wybór technologii trwałości. Typy na platformie .NET są czasami określane jako zwykłych starych obiektów CLR (POCOs), ponieważ nie ma potrzeby dziedziczą z konkretnej klasy bazowej lub implementacji konkretnego interfejsu. Nieznajomości trwałości jest przydatne, ponieważ zezwala ona na ten sam model biznesowy w celu jego utrwalenia na wiele sposobów, oferując dodatkową elastyczność na potrzeby aplikacji. Opcje trwałości mogą ulec zmianie wraz z upływem czasu od technologii jedną bazę danych do innego, lub dodatkowych metod trwałości mogą być wymagane, oprócz niezależnie od uruchomienia za pomocą aplikacji (na przykład za pomocą pamięci podręcznej redis Cache lub Azure DocumentDb, w uzupełnieniu do relacyjna baza danych).

Niektóre przykłady naruszenie tej zasady obejmują:

- Wymagane klasy bazowej.

- Implementacja wymaganego interfejsu.

- Klasy jest odpowiedzialny za zapisywanie samodzielnie (na przykład wzorzec aktywnym rekordzie).

- Wymagane domyślnego konstruktora.

- Właściwości wymagających virtual — słowo kluczowe.

- Specyficzne dla trwałości wymaganych atrybutów.

Wymóg, że klasy nie ma żadnej z powyższych funkcje lub zachowania dodaje sprzężenia między tymi typami w celu jego utrwalenia i wybór technologii trwałości, powodując trudniejsze do przyjęcia nowych strategii dostępu do danych w przyszłości.

### <a name="bounded-contexts"></a>Ograniczone konteksty

**Ograniczone konteksty** są centralnej wzorzec driven projektu. Umożliwiają realizowanie złożoności w dużych aplikacji lub organizacje przez podzielenie go na osobne moduły pojęć. Każdy moduł koncepcyjny reprezentuje kontekst, który jest oddzielony od innych kontekstach (z tego powodu ograniczonego) oraz można rozwijać niezależnie. Poszczególnych kontekstach najlepiej należy wybrać własne nazwy pojęcia znajdujący się w nim, a powinien mieć wyłączny dostęp do własnego magazynu.

Co najmniej poszczególnych aplikacjach sieci web należy dążyć do mieć własne kontekstach z własny magazyn stanów trwałych dla swojego modelu biznesowego, a nie z innych aplikacji do udostępniania bazy danych. Między ograniczone konteksty odbywa się za pośrednictwem interfejsów programistycznych, a nie za pomocą udostępnionej bazy danych, który pozwala na logiki biznesowej i zdarzenia, aby móc umieścić w odpowiedzi na zmiany, które mają miejsce. Ograniczone konteksty mapy ściśle do mikrousług, które również najlepiej są implementowane jako własnych indywidualnych ograniczone konteksty.

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Wzorce projektowe oparte na języku JAVA: Zasady](https://java-design-patterns.com/principles/)
* [Ograniczony kontekst](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Poprzednie](choose-between-traditional-web-and-single-page-apps.md)
>[dalej](common-web-application-architectures.md)
