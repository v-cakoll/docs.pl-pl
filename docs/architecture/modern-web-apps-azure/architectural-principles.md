---
title: Zasady dotyczące architektury
description: Architekt nowoczesne aplikacje internetowe z ASP.NET Core i Azure | Zasady architektury
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: ffc890bf8cd6b07bd70d8fc7b2b8cfeaf474ae35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450274"
---
# <a name="architectural-principles"></a>Zasady dotyczące architektury

> "Gdyby budowniczowie budowali budynki tak, jak programiści pisali programy, to pierwszy dzięcioł, który przyszedł, zniszczyłby cywilizację."  
> _\-Gerald Weinberg_

Należy architekti i projektowania rozwiązań programowych z myślą o łatwości konserwacji. Zasady opisane w tej sekcji mogą pomóc w poprowadzeniu cię w kierunku decyzji architektonicznych, które spowodują czyste, możliwe do utrzymania aplikacje. Ogólnie rzecz biorąc te zasady poprowadzi Cię w kierunku tworzenia aplikacji z dyskretnych składników, które nie są ściśle powiązane z innymi częściami aplikacji, ale raczej komunikować się za pośrednictwem jawnych interfejsów lub systemów obsługi wiadomości.

## <a name="common-design-principles"></a>Wspólne zasady projektowania

### <a name="separation-of-concerns"></a>Rozdzielenie obaw

Zasadą przewodnią przy opracowywaniu jest **separacja obaw**. Zasada ta stanowi, że oprogramowanie powinno być oddzielone w oparciu o rodzaje pracy, którą wykonuje. Na przykład należy wziąć pod uwagę aplikację, która zawiera logikę do identyfikowania godnych uwagi elementów do wyświetlenia użytkownikowi i który formatuje takie elementy w określony sposób, aby uczynić je bardziej zauważalne. Zachowanie odpowiedzialne za wybór elementów do formatowania powinny być oddzielone od zachowania odpowiedzialnego za formatowanie elementów, ponieważ są to oddzielne problemy, które są przypadkowo powiązane ze sobą.

Architektonicznie aplikacje mogą być logicznie skonstruowane, aby postępować zgodnie z tą zasadą, oddzielając podstawowe zachowanie biznesowe od logiki infrastruktury i interfejsu użytkownika. W idealnym przypadku reguły biznesowe i logika powinny znajdować się w oddzielnym projekcie, który nie powinien zależeć od innych projektów w aplikacji. Pomaga to zapewnić, że model biznesowy jest łatwy do przetestowania i może ewoluować bez ścisłego sprzężenia z szczegółami implementacji niskiego poziomu. Oddzielenie problemów jest kluczowym czynnikiem za korzystanie z warstw w architekturach aplikacji.

### <a name="encapsulation"></a>Hermetyzacja

Różne części aplikacji powinny używać **hermetyzacji,** aby odizolować je od innych części aplikacji. Składniki aplikacji i warstwy powinny być w stanie dostosować ich wewnętrznej implementacji bez przerywania ich współpracowników tak długo, jak kontrakty zewnętrzne nie są naruszane. Prawidłowe stosowanie hermetyzacji pomaga osiągnąć luźne sprzężenie i modułowość w projektach aplikacji, ponieważ obiekty i pakiety można zastąpić alternatywnymi implementacjami, o ile ten sam interfejs jest utrzymywany.

W klasach hermetyzacji jest osiągana przez ograniczenie dostępu z zewnątrz do stanu wewnętrznego klasy. Jeśli podmiot zewnętrzny chce manipulować stanem obiektu, powinien to zrobić za pośrednictwem dobrze zdefiniowanej funkcji (lub metody ustawiania właściwości), zamiast mieć bezpośredni dostęp do stanu prywatnego obiektu. Podobnie składniki aplikacji i same aplikacje powinny uwidaczniać dobrze zdefiniowane interfejsy dla swoich współpracowników do użycia, a nie pozwalając ich stan do bezpośredniej modyfikacji. Dzięki temu wewnętrzny projekt aplikacji ewoluuje wraz z urazem, nie martwiąc się, że spowoduje to przerwanie współpracy, o ile umowy publiczne zostaną utrzymane.

### <a name="dependency-inversion"></a>Odwrócenie zależności

Kierunek zależności w aplikacji powinien być w kierunku abstrakcji, a nie szczegóły implementacji. Większość aplikacji są zapisywane w taki sposób, że zależność w czasie kompilacji przepływy w kierunku wykonywania wykonawczego. Spowoduje to wygenerowanie wykresu zależności bezpośredniej. Oznacza to, że jeśli moduł A wywołuje funkcję w module B, która wywołuje funkcję w module C, a następnie w czasie kompilacji A będzie zależeć od B, który będzie zależeć od C, jak pokazano na rysunku 4-1.

![Wykres zależności bezpośredniej](./media/image4-1.png)

**Rysunek 4-1.** Wykres zależności bezpośredniej.

Zastosowanie zasady inwersji zależności umożliwia A wywołanie metod abstrakcji, które implementuje B, umożliwiając A wywołanie B w czasie wykonywania, ale dla B zależy od interfejsu kontrolowanego przez A w czasie kompilacji *(w* związku z tym odwrócenie typowej zależności w czasie kompilacji). W czasie wykonywania przepływu wykonywania programu pozostaje niezmieniona, ale wprowadzenie interfejsów oznacza, że różne implementacje tych interfejsów można łatwo podłączyć.

![Wykres odwróconej zależności](./media/image4-2.png)

**Rysunek 4-2.** Odwrócony wykres zależności.

**Inwersja zależności** jest kluczową częścią tworzenia luźno powiązanych aplikacji, ponieważ szczegóły implementacji mogą być zapisywane w zależności i implementacji abstrakcji wyższego poziomu, a nie na odwrót. Powstałe aplikacje są bardziej sprawdzalne, modułowe i możliwe do utrzymania w wyniku. Praktyka *wstrzykiwania zależności* jest możliwe poprzez przestrzeganie zasady inwersji zależności.

### <a name="explicit-dependencies"></a>Jawne zależności

**Metody i klasy powinny jawnie wymagać wszelkich współpracujących obiektów, których potrzebują, aby działać poprawnie.** Konstruktory klas zapewniają możliwość dla klas, aby zidentyfikować rzeczy, których potrzebują, aby być w prawidłowym stanie i działać poprawnie. Jeśli zdefiniujesz klasy, które mogą być konstruowane i wywoływane, ale będzie działać poprawnie tylko wtedy, gdy pewne składniki globalne lub infrastruktury są w miejscu, te klasy są *nieuczciwe* z ich klientów. Kontrakt konstruktora mówi klientowi, że potrzebuje tylko określonych rzeczy (prawdopodobnie nic, jeśli klasa jest po prostu przy użyciu konstruktora bezparametrów), ale następnie w czasie wykonywania okazuje się, że obiekt naprawdę potrzebował czegoś innego.

Postępując zgodnie z zasadą jawne zależności, klas i metod są uczciwi ze swoimi klientami o tym, czego potrzebują, aby funkcjonować. Dzięki temu kod jest bardziej samodokumentujący, a kontrakty kodowania są bardziej przyjazne dla użytkownika, ponieważ użytkownicy będą mieli pewność, że tak długo, jak zapewniają to, co jest wymagane w postaci parametrów metody lub konstruktora, obiekty, z którymi pracują, będą się zachowywać poprawnie w czasie wykonywania.

### <a name="single-responsibility"></a>Pojedyncza odpowiedzialność

Zasada jednolitej odpowiedzialności ma zastosowanie do projektowania obiektowego, ale może być również uważana za zasadę architektoniczną podobną do rozdziału obaw. Stwierdza się w nim, że przedmioty powinny ponoszą tylko jedną odpowiedzialność i że powinny mieć tylko jeden powód do zmiany. W szczególności jedyną sytuacją, w której obiekt powinien ulec zmianie, jest, jeśli sposób, w jaki wykonuje swoją jedną odpowiedzialność, musi zostać zaktualizowany. Zgodnie z tą zasadą pomaga produkować bardziej luźno sprzężone i modułowe systemy, ponieważ wiele rodzajów nowych zachowań można zaimplementować jako nowe klasy, a nie przez dodanie dodatkowej odpowiedzialności do istniejących klas. Dodawanie nowych klas jest zawsze bezpieczniejsze niż zmiana istniejących klas, ponieważ żaden kod nie zależy jeszcze od nowych klas.

W monolitycznym zastosowaniu możemy zastosować zasadę pojedynczej odpowiedzialności na wysokim poziomie do warstw w aplikacji. Odpowiedzialność za prezentację powinna pozostać w projekcie interfejsu i usług, podczas gdy odpowiedzialność za dostęp do danych powinna być utrzymywana w projekcie infrastruktury. Logika biznesowa powinna być przechowywana w projekcie podstawowym aplikacji, gdzie można go łatwo przetestować i ewoluować niezależnie od innych obowiązków.

Gdy ta zasada jest stosowana do architektury aplikacji i podjęte do logicznego punktu końcowego, otrzymasz mikrousług. Danej mikrousługi powinny mieć jedną odpowiedzialność. Jeśli trzeba rozszerzyć zachowanie systemu, zwykle lepiej to zrobić przez dodanie dodatkowych mikrousług, a nie przez dodanie odpowiedzialności do istniejącego.

[Dowiedz się więcej o architekturze mikrousług](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Nie powtarzaj się (DRY)

Aplikacja powinna unikać określania zachowania związanego z określonym pojęciem w wielu miejscach, ponieważ jest to częste źródło błędów. W pewnym momencie zmiana wymagań będzie wymagać zmiany tego zachowania i prawdopodobieństwo, że co najmniej jedno wystąpienie zachowania nie zostanie zaktualizowane spowoduje niespójne zachowanie systemu.

Zamiast powielania logiki, hermetyzować go w konstrukcji programowania. Należy wykonać tę konstrukcję pojedynczego uprawnienia nad tym zachowaniem i mieć dowolną inną część aplikacji, która wymaga tego zachowania użyć nowej konstrukcji.

> [!NOTE]
> Należy unikać wiązania razem zachowanie, które jest tylko przypadkowo powtarzalne. Na przykład tylko dlatego, że dwie różne stałe mają tę samą wartość, nie oznacza to, że powinieneś mieć tylko jedną stałą, jeśli koncepcyjnie odnoszą się do różnych rzeczy.

### <a name="persistence-ignorance"></a>Niewiedza o trwałości

**Nieznajomość trwałości** (PI) odnosi się do typów, które muszą być utrwaliłe, ale których kod nie ma wpływu na wybór technologii trwałości. Takie typy w .NET są czasami określane jako zwykły starych obiektów CLR (POC), ponieważ nie trzeba dziedziczyć z określonej klasy podstawowej lub implementować określonego interfejsu. Nieznajomość trwałości jest cenne, ponieważ pozwala na ten sam model biznesowy, które mają być utrwalić na wiele sposobów, oferując dodatkową elastyczność do aplikacji. Opcje trwałości może się zmieniać wraz z uchwycenia, z jednej technologii bazy danych do innej lub dodatkowe formy trwałości może być wymagane oprócz niezależnie od aplikacji rozpoczęte z (na przykład przy użyciu pamięci podręcznej Redis lub usługi Azure Cosmos DB oprócz relacyjnej bazy danych).

Oto kilka przykładów naruszeń tej zasady:

- Wymagana klasa podstawowa.

- Wymagana implementacja interfejsu.

- Klasy odpowiedzialne za zapisywanie się (takie jak wzorzec rekordu aktywnego).

- Wymagany konstruktor bezparametrów.

- Właściwości wymagające wirtualnego słowa kluczowego.

- Atrybuty wymagane do swoistego dla trwałości.

Wymóg, że klasy mają dowolną z powyższych funkcji lub zachowań dodaje sprzężenia między typami, które mają być utrwalić i wybór technologii trwałości, co utrudnia przyjęcie nowych strategii dostępu do danych w przyszłości.

### <a name="bounded-contexts"></a>Ograniczone konteksty

**Ograniczone konteksty** są centralnym wzorcem w projekcie opartym na domenie. Zapewniają one sposób radzenia sobie ze złożonością w dużych aplikacjach lub organizacjach, rozbijając ją na oddzielne moduły koncepcyjne. Każdy moduł koncepcyjny reprezentuje kontekst, który jest oddzielony od innych kontekstów (stąd, ograniczone) i może ewoluować niezależnie. Każdy ograniczony kontekst powinien idealnie mieć swobodę wyboru własnych nazw dla pojęć w nim i powinien mieć wyłączny dostęp do własnego magazynu trwałości.

Co najmniej poszczególnych aplikacji sieci web należy dążyć do własnego kontekstu ograniczone, z własnego magazynu trwałości dla ich modelu biznesowego, a nie udostępnianie bazy danych z innymi aplikacjami. Komunikacja między kontekstami ograniczonymi odbywa się za pośrednictwem interfejsów programowych, a nie za pośrednictwem udostępnionej bazy danych, co pozwala na logikę biznesową i zdarzenia, które mają miejsce w odpowiedzi na zmiany, które mają miejsce. Ograniczone konteksty map ściśle do mikrousług, które również są idealnie zaimplementowane jako własne indywidualne ograniczone konteksty.

## <a name="additional-resources"></a>Zasoby dodatkowe

- [Wzory projektowania JAVA: Zasady](https://java-design-patterns.com/principles/)
- [Ograniczony kontekst](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Poprzedni](choose-between-traditional-web-and-single-page-apps.md)
>[następny](common-web-application-architectures.md)
