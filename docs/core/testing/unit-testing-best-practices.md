---
title: Najważniejsze wskazówki dotyczące pisania testów jednostkowych
description: Zapoznaj się z najlepszymi rozwiązaniami dotyczącymi pisania testów jednostkowych, które mają jakość kodu napędowego i odporność projektów .NET Core i .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 586373381bcb18384cbf29bb2ca2bd220a2b2d3d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240964"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>Najlepsze rozwiązania dotyczące testowania jednostkowego z .NET Core i .NET Standard

Istnieje wiele korzyści z pisania testów jednostkowych; pomagają w regresji, dostarczają dokumentację i ułatwiają dobry projekt. Jednak trudne do odczytania i kruche testy jednostkowe mogą siać spustoszenie w bazie kodu. W tym artykule opisano niektóre najlepsze rozwiązania dotyczące projektowania testów jednostkowych dla projektów .NET Core i .NET Standard.

W tym przewodniku dowiesz się o najlepszych praktykach podczas pisania testów jednostkowych, aby testy były odporne i łatwe do zrozumienia.

[John Reese](https://reese.dev) ze specjalnymi podziękowaniami dla [Roya Osherove'a](https://osherove.com/)

## <a name="why-unit-test"></a>Dlaczego test jednostkowy?

### <a name="less-time-performing-functional-tests"></a>Krótszy czas wykonywania testów funkcjonalnych
Testy funkcjonalne są drogie. Zazwyczaj obejmują one otwarcie aplikacji i wykonanie serii kroków, które ty (lub ktoś inny), należy wykonać w celu zweryfikowania oczekiwanego zachowania. Kroki te mogą nie zawsze być znane testerowi, co oznacza, że będą musieli dotrzeć do kogoś bardziej kompetentnego w okolicy w celu przeprowadzenia testu. Samo testowanie może potrwać kilka sekund dla trywialnych zmian lub minut dla większych zmian. Wreszcie, proces ten musi być powtórzony dla każdej zmiany, które można wprowadzić w systemie.

Testy jednostkowe, z drugiej strony, wziąć milisekund, mogą być uruchamiane po naciśnięciu przycisku i nie koniecznie wymagają żadnej wiedzy na temat systemu w ogóle. To, czy test zda lub nie, zależy od biegacza testowego, a nie jednostki.

### <a name="protection-against-regression"></a>Ochrona przed regresją
Wady regresji są wady, które są wprowadzane po wprowadzeniu zmiany do aplikacji. Testerzy często testują nie tylko swoją nową funkcję, ale także funkcje, które istniały wcześniej, aby sprawdzić, czy wcześniej zaimplementowane funkcje nadal działają zgodnie z oczekiwaniami.

W przypadku testowania jednostkowego można ponownie uruchomić cały zestaw testów po każdej kompilacji lub nawet po zmianie wiersza kodu. Daje pewność, że nowy kod nie może złamać istniejące funkcje.

### <a name="executable-documentation"></a>Dokumentacja wykonywalna
Nie zawsze może być oczywiste, co dana metoda robi lub jak zachowuje się biorąc pod uwagę pewne dane wejściowe. Możesz zadać sobie pytanie: Jak zachowuje się ta metoda, jeśli przekażę jej pusty ciąg? Null?

Jeśli masz zestaw dobrze nazwanych testów jednostkowych, każdy test powinien być w stanie jasno wyjaśnić oczekiwane dane wyjściowe dla danego wejścia. Ponadto powinien być w stanie sprawdzić, czy rzeczywiście działa.

### <a name="less-coupled-code"></a>Mniej sprzężeny kod
Gdy kod jest ściśle sprzężeny, może być trudne do testu jednostkowego. Bez tworzenia testów jednostkowych dla kodu, który piszesz, sprzężenia mogą być mniej widoczne.

Pisanie testów dla kodu będzie naturalnie oddzielić kod, ponieważ byłoby trudniejsze do przetestowania w przeciwnym razie.

## <a name="characteristics-of-a-good-unit-test"></a>Charakterystyka dobrego testu jednostkowego

- **Szybko**. Nie rzadko zdarza się, że dojrzałe projekty mają tysiące testów jednostkowych. Testy jednostkowe powinny zająć bardzo mało czasu. Milisekund.
- **Izolowane**. Testy jednostkowe są autonomiczne, można uruchomić w izolacji i nie mają zależności od czynników zewnętrznych, takich jak system plików lub bazy danych.
- **Powtarzalne**. Uruchomienie testu jednostkowego powinno być zgodne z jego wynikami, oznacza to, że zawsze zwraca ten sam wynik, jeśli nie zmienisz niczego między przebiegami.
- **Samokontrolowanie**. Test powinien być w stanie automatycznie wykryć, czy przeszedł lub nie powiodło się bez interakcji człowieka.
- **Terminowo**. Test jednostkowy nie powinien trwać nieproporcjonalnie długo, aby napisać w porównaniu do testowanego kodu. Jeśli znajdziesz testowania kodu przy dużej ilości czasu w porównaniu do pisania kodu, należy wziąć pod uwagę projekt, który jest bardziej sprawdzalne.

## <a name="lets-speak-the-same-language"></a>Mówmy tym samym językiem
Termin *mock* jest niestety bardzo nadużywane, gdy mówimy o testach. Następujące definiuje najczęstsze typy *podróbek* podczas pisania testów jednostkowych:

*Fałszywe* — podróbka to ogólny termin, który może służyć do opisywania wycinka lub makiety obiektu. Czy jest to skrót lub makiety zależy od kontekstu, w którym jest używany. Innymi słowy, fałszywy może być zalążek lub makiety.

*Makieta* — makieta obiektu jest fałszywy obiekt w systemie, który decyduje, czy test jednostkowy przeszedł lub nie. Makieta zaczyna się jako fake, dopóki nie zostanie dotwierdzona przeciwko.

*Stub* — skrótowy jest kontrolowanym zamiennikiem istniejącej zależności (lub współpracownika) w systemie. Za pomocą skrótu, można przetestować kod bez zajmowania się zależności bezpośrednio. Domyślnie fałszywy zaczyna się jako skrót.

Należy wziąć pod uwagę następujący fragment kodu:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Byłby to przykład wycinka jest określany jako makieta. W tym przypadku jest to wycinek. Właśnie przechodzisz w Zakonie jako środek, aby `Purchase` móc tworzyć wystąpienia (system w teście). Nazwa `MockOrder` jest również bardzo mylące, ponieważ znowu, kolejność nie jest makieta.

Lepszym podejściem byłoby

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Zmieniając nazwę klasy na `FakeOrder`, zrobiłeś klasy o wiele bardziej ogólne, klasa może służyć jako makiety lub wycinka. W zależności od tego, co jest lepsze dla przypadku testowego. W powyższym `FakeOrder` przykładzie jest używany jako wycinek. Nie używasz `FakeOrder` w żadnym kształcie lub formie podczas asertywny. `FakeOrder`właśnie został przekazany `Purchase` do klasy, aby spełnić wymagania konstruktora.

Aby użyć go jako makiety, można zrobić coś takiego

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

W takim przypadku sprawdzasz właściwość na Fake (twierdząc przeciwko niemu), więc w `mockOrder` powyższym fragmencie kodu, jest mock.

> [!IMPORTANT]
> Ważne jest, aby ta terminologia była poprawna. Jeśli wywołasz wycinki "makiety", inni deweloperzy będą wprowadzać fałszywe założenia dotyczące intencji.

Najważniejszą rzeczą do zapamiętania o makiety kontra wycinki jest to, że makiety są jak wycinki, ale twierdzą, przeciwko makiety obiektu, podczas gdy nie twierdzą przeciwko wycinka.

## <a name="best-practices"></a>Najlepsze rozwiązania

### <a name="naming-your-tests"></a>Nadawanie nazw testom
Nazwa testu powinna składać się z trzech części:

- Nazwa testowanej metody.
- Scenariusz, w którym jest testowany.
- Oczekiwane zachowanie, gdy scenariusz jest wywoływany.

#### <a name="why"></a>Dlaczego?

- Standardy nazewnictwa są ważne, ponieważ jawnie wyrażają intencję testu.

Testy są czymś więcej niż tylko upewnienie się, że kod działa, ale również zawierają dokumentację. Wystarczy spojrzeć na zestaw testów jednostkowych, powinieneś być w stanie wywnioskować zachowanie kodu, nawet nie patrząc na sam kod. Ponadto po niepowodzeniu testów można zobaczyć dokładnie, które scenariusze nie spełniają twoich oczekiwań.

#### <a name="bad"></a>Źle:
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Organizowanie testów
**Rozmieść, Działaj, Potwierdzaj** jest typowym wzorcem podczas testowania jednostek. Jak sama nazwa wskazuje, składa się z trzech głównych działań:

- *Rozmieść* obiekty, tworząc je i konfigurując w razie potrzeby.
- *Działaj* na obiekcie.
- *Twierdzą,* że coś jest zgodnie z oczekiwaniami.

#### <a name="why"></a>Dlaczego?

- Wyraźnie oddziela to, co jest testowane od *kroków aranżacji* *i potwierdzenia.*
- Mniejsza szansa na połączenie twierdzeń z kodem "Act".

Czytelność jest jednym z najważniejszych aspektów podczas pisania testu. Oddzielenie każdej z tych akcji w ramach testu wyraźnie wyróżnić zależności wymagane do wywołania kodu, jak kod jest wywoływany i co próbujesz potwierdzić. Chociaż może być możliwe, aby połączyć niektóre kroki i zmniejszyć rozmiar testu, głównym celem jest, aby test tak czytelny, jak to możliwe.

#### <a name="bad"></a>Źle:
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Napisz minimalnie przechodzące testy
Dane wejściowe, które mają być używane w teście jednostkowym powinny być najprostsze z możliwych w celu sprawdzenia zachowania, które są obecnie testujące.

#### <a name="why"></a>Dlaczego?

- Testy stają się bardziej odporne na przyszłe zmiany w bazie kodu.
- Bliżej do testowania zachowania nad implementacją.

Testy, które zawierają więcej informacji niż wymagane do zdaniu testu mają większe szanse na wprowadzenie błędów do testu i może sprawić, że intencja testu mniej jasne. Podczas pisania testów chcesz skupić się na zachowaniu. Ustawianie dodatkowych właściwości w modelach lub używanie wartości niezerowych, gdy nie jest to wymagane, tylko umniejsza to, co próbujesz udowodnić.

#### <a name="bad"></a>Źle:
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Unikaj magicznych strun
Nazewnictwo zmiennych w testach jednostkowych jest równie ważne, jeśli nie ważniejsze, niż nazewnictwo zmiennych w kodzie produkcyjnym. Testy jednostkowe nie powinny zawierać magicznych ciągów.

#### <a name="why"></a>Dlaczego?

- Zapobiega konieczności czytelnika testu do sprawdzenia kodu produkcji, aby dowiedzieć się, co sprawia, że wartość jest wyjątkowa.
- Wyraźnie pokazuje, co próbujesz *udowodnić,* a nie *próbujesz osiągnąć*.

Magiczne struny mogą powodować zamieszanie dla czytelnika testów. Jeśli ciąg wygląda nietypowe, mogą się zastanawiać, dlaczego pewna wartość została wybrana dla parametru lub wartości zwracanej. Może to prowadzić ich do bliższego przyjrzenia się szczegółom implementacji, a nie skupić się na teście.

> [!TIP]
> Podczas pisania testów, należy dążyć do wyrażenia jak najwięcej intencji, jak to możliwe. W przypadku magicznych ciągów dobrym podejściem jest przypisywanie tych wartości do stałych.

#### <a name="bad"></a>Źle:
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Unikaj logiki w testach
Podczas pisania testów jednostkowych należy unikać ręcznego `if` `while`łączenia `for` `switch`ciągów i warunków logicznych, takich jak , , , , itp.

#### <a name="why"></a>Dlaczego?

- Mniejsza szansa na wprowadzenie błędu wewnątrz testów.
- Skoncentruj się na wyniku końcowym, a nie na szczegółach implementacji.

Po wprowadzeniu logiki do zestawu testów, szansa wprowadzenia błędu do niego znacznie wzrasta. Ostatnie miejsce, w którym chcesz znaleźć błąd, znajduje się w pakiecie testowym. Powinieneś mieć wysoki poziom pewności, że twoje testy działają, w przeciwnym razie nie będziesz im ufać. Testy, którym nie ufasz, nie zapewniają żadnej wartości. Gdy test nie powiedzie się, chcesz mieć poczucie, że coś jest rzeczywiście nie tak z kodem i że nie można go zignorować.

> [!TIP]
> Jeśli logika w teście wydaje się nieunikniona, należy rozważyć podzielenie testu na dwa lub więcej różnych testów.

#### <a name="bad"></a>Źle:
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Preferuj metody pomocnika do konfiguracji i rozdarcia
Jeśli potrzebujesz podobnego obiektu lub stanu dla testów, wolisz metodę pomocnika niż wykorzystanie atrybutów Setup i Teardown, jeśli istnieją.

#### <a name="why"></a>Dlaczego?

- Mniej zamieszania podczas czytania testów, ponieważ cały kod jest widoczny z poziomu każdego testu.
- Mniejsze szanse na ustawienie zbyt dużo lub zbyt mało dla danego testu.
- Mniejsza szansa na udostępnianie stanu między testami, który tworzy niepożądane zależności między nimi.

W ramach testowania `Setup` jednostkowego jest wywoływana przed każdym testem jednostkowym w pakiecie testów. Podczas gdy niektórzy mogą zobaczyć to jako przydatne narzędzie, to zazwyczaj kończy się prowadzi do nadęty i trudne do odczytania testów. Każdy test będzie zazwyczaj mieć różne wymagania w celu uruchomienia testu. Niestety, `Setup` zmusza do korzystania z dokładnie tych samych wymagań dla każdego testu.

> [!NOTE]
> xUnit usunął zarówno SetUp i TearDown w wersji 2.x

#### <a name="bad"></a>Źle:
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Unikaj wielu twierdzeń
Podczas pisania testów, spróbuj dołączyć tylko jeden Assert na test. Typowe podejścia do używania tylko jednego potwierdzenia obejmują:

- Utwórz oddzielny test dla każdego potwierdzenia.
- Użyj sparametryzowanych testów.

#### <a name="why"></a>Dlaczego?

- Jeśli jeden Assert nie powiedzie się, kolejne Asserts nie będą oceniane.
- Zapewnia, że nie są potwierdzające wiele przypadków w testach.
- Daje cały obraz, dlaczego testy nie powiodą się.

Podczas wprowadzania wielu potwierdza w przypadku testowym, nie jest gwarantowane, że wszystkie potwierdzenia zostaną wykonane. W większości platform testowania jednostek, gdy potwierdzenie nie powiedzie się w teście jednostkowym, testy postępowania są automatycznie uważane za niepowiedzę. Może to być mylące, ponieważ funkcja, która faktycznie działa, będzie wyświetlana jako nieudana.

> [!NOTE]
> Typowym wyjątkiem od tej reguły jest podczas powoływania się na obiekt. W takim przypadku jest ogólnie dopuszczalne mieć wiele dotuje względem każdej właściwości, aby upewnić się, że obiekt jest w stanie, który oczekujesz, że w.

#### <a name="bad"></a>Źle:
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Sprawdzanie poprawności metod prywatnych według metod publicznych testów jednostkowych
W większości przypadków nie powinno być potrzeby testowania metody prywatnej. Metody prywatne są szczegółem implementacji. Można myśleć o tym w ten sposób: metody prywatne nigdy nie istnieją w izolacji. W pewnym momencie będzie metoda publiczna, która wywołuje metodę prywatną w ramach jej implementacji. To, na czym należy dbać, to efekt końcowy metody publicznej, która wywołuje ją w sposób prywatny.

Rozważmy następujący przypadek

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

Pierwszą reakcją może być rozpoczęcie `TrimInput` pisania testu, ponieważ chcesz upewnić się, że metoda działa zgodnie z oczekiwaniami. Jednak jest całkowicie możliwe, `ParseLogLine` że `sanitizedInput` manipuluje w taki sposób, że `TrimInput` nie można oczekiwać, renderowania test przed bezużyteczne.

Prawdziwy test powinien być przeprowadzony przeciwko `ParseLogLine` metodzie publicznej, ponieważ to jest to, na czym ostatecznie powinieneś dbać.

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

Z tego punktu widzenia, jeśli widzisz metodę prywatną, znajdź metodę publiczną i napisz testy przeciwko tej metodzie. Tylko dlatego, że metoda prywatna zwraca oczekiwany wynik, nie oznacza, że system, który ostatecznie wywołuje metodę prywatną używa wynik poprawnie.

### <a name="stub-static-references"></a>Stub odniesienia statyczne
Jedną z zasad badania jednostkowego jest to, że musi on mieć pełną kontrolę nad badanym systemem. Może to być problematyczne, gdy kod produkcyjny zawiera `DateTime.Now`wywołania odwołań statycznych (np. ). Należy wziąć pod uwagę następujący kod

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Jak ten kod może być ewentualnie testowane jednostki? Możesz spróbować takiego podejścia, jak

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

Niestety, szybko zdasz sobie sprawę, że istnieje kilka problemów z testami.

- Jeśli zestaw testów zostanie uruchomiony we wtorek, drugi test zakończy się powodzeniem, ale pierwszy test zakończy się niepowodzeniem.
- Jeśli zestaw testów jest uruchamiany w dowolnym innym dniu, pierwszy test zakończy się powodzeniem, ale drugi test zakończy się niepowodzeniem.

Aby rozwiązać te problemy, musisz wprowadzić *szew* do kodu produkcyjnego. Jednym z podejść jest zawijanie kodu, który należy kontrolować w interfejsie i mieć kod produkcyjny zależy od tego interfejsu.

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Twój zestaw testów stanie się teraz

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

Teraz zestaw testów ma `DateTime.Now` pełną kontrolę nad i może wycinek dowolnej wartości podczas wywoływania do metody.
