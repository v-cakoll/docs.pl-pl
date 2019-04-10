---
title: Najlepsze rozwiązania dotyczące pisania testów jednostkowych
description: Poznaj najlepsze rozwiązania dotyczące pisania testów jednostkowych, które Dbaj o jakość kodu i odporności dla projektów .NET Core i .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: 7f4699b5277c5feeac4d9116ac85e096247aa748
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427451"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>Najlepsze rozwiązania przy użyciu platformy .NET Core i .NET Standard testy jednostkowe

Istnieje wiele korzyści, do pisania testów jednostkowych; pomagają przy użyciu regresji, zapewniają dostęp do dokumentacji i ułatwienia dobrego projektowania. Jednak testy jednostkowe trudne do odczytu i kruchy można spustoszyć bazy kodu. W tym artykule opisano najlepsze rozwiązania dotyczące projektowania testów jednostkowych dla projektów .NET Core i .NET Standard.

W tym przewodniku dowiesz się najważniejsze wskazówki podczas pisania testów jednostkowych, aby zachować testów, odporne i łatwe do zrozumienia.

Przez [John Reese](https://reese.dev) ze specjalnymi dzięki [Roy Osherove](https://osherove.com/)

## <a name="why-unit-test"></a>Dlaczego test jednostkowy?

### <a name="less-time-performing-functional-tests"></a>Mniej czasu na wykonywanie testów funkcjonalnych
Testy funkcjonalne są kosztowne. Są na ogół podczas otwierania aplikacji, a następnie wykonanie serii czynności, które użytkownik (lub kogoś innego), należy wykonać, aby można było zweryfikować oczekiwane zachowanie. Te kroki nie zawsze być znane do testera, co oznacza, że konieczne będzie skontaktowanie się z ktoś większą wiedzę w obszarze w celu przeprowadzenia badania. Testowanie sam może potrwać sekund proste zmiany lub minut w celu większe zmiany. Ponadto ten proces należy powtórzyć dla każdej zmiany wprowadzone w systemie.

Testy jednostkowe, z drugiej strony ręcznie, zająć milisekund, mogą być uruchamiane naciśnięciem przycisku i nie muszą mieć żadnej wiedzy w dużych systemu. Określa, czy test kończy się pomyślnie lub nie powiedzie się, zależy od narzędzia test runner nie osoby.

### <a name="protection-against-regression"></a>Ochrona przed regresji
Regresja wady są wady, które są wprowadzone podczas wprowadzania zmian do aplikacji. Powszechne jest wprowadzanie dla testerów, nie tylko testowania ich nowych funkcji, ale także funkcje, które istniało wcześniej w celu sprawdzenia, które było wcześniej zaimplementowane funkcje nadal działają zgodnie z oczekiwaniami.

Za pomocą testów jednostkowych jest możliwe ponowne uruchamianie usługi cały zestaw testów po każdej kompilacji, lub nawet w przypadku, po zmianie wiersza kodu. Co daje pewność, że nowy kod nie mogą przerwać działania istniejących funkcji.

### <a name="executable-documentation"></a>Dokumentacja pliku wykonywalnego
Go może nie zawsze jest oczywiste działanie konkretną metodę lub jego zachowania podany niektórych danych wejściowych. Może zadać sobie: Jak zachowują się ta metoda jeśli mogę przekazać pusty ciąg? Wartość null?

W przypadku zestawu testów jednostkowych dobrze nazwane każdy test powinien móc wyjaśniają oczekiwanych danych wyjściowych dla danego składnika. Ponadto powinno być możliwe sprawdzić, czy rzeczywiście działa.

### <a name="less-coupled-code"></a>Mniej sprzężonych kodu
Gdy kod jest ściśle powiązane, może być trudne do testów jednostkowych. Bez tworzenia testów jednostkowych dla kodu, który właśnie piszesz, sprzężenia mogą być mniej jasne.

Pisanie testów dla kodu naturalnie będzie rozdzielenie kodu, ponieważ może być trudniejsze do testowania, w przeciwnym razie.

## <a name="characteristics-of-a-good-unit-test"></a>Charakterystyki testu jednostkowego dobre
- **Szybkie**. Nie jest niczym niezwykłym dojrzała projektów, które mają kilka tysięcy testów jednostkowych. Testy jednostkowe powinno zająć bardzo mało czasu do uruchomienia. Liczba milisekund.
- **Izolowane**. Testy jednostkowe są autonomiczne, mogą być uruchamiane w izolacji i mieć żadnych zależności na wszelkich zewnętrznych czynników, takich jak system plików lub bazy danych.
- **Powtarzalne**. Uruchamianie testów jednostkowych powinny być zgodne z jego wyniki, oznacza to, zawsze zwraca ten sam wynik, jeśli nie należy zmieniać niczego Between przebiegów.
- **Sprawdzanie własnym**. Test powinien móc automatycznie wykryć, czy przekazywany ani nie powiodła się bez interwencji człowieka.
- **Czas**. Test jednostkowy nie powinna przyjmować zapisu w porównaniu do testowany kod jest nieproporcjonalnie dużo czasu. Jeśli okaże się, testowanie kodu, biorąc dużą ilość czasu w porównaniu do pisania kodu, należy wziąć pod uwagę projekt, który jest bardziej sprawdzalnego działa zgodnie.

## <a name="lets-speak-the-same-language"></a>Teraz używać tego samego języka
Termin *testowanie* jest Niestety bardzo użyte w przypadku testowania. Następujące definiuje najbardziej powszechne typy *elementów sztucznych* podczas pisania testów jednostkowych:

*Sztuczne* -sfałszowana to ogólny termin określający, który może służyć do opisu odcinek lub makiety obiektu. Czy jest on odcinek czy pozorny zależy od kontekstu, w którym jest używany. Dlatego oznacza to, sfałszowana można odcinek lub pozorny.

*Testowanie* -makiety obiektu jest obiektem sztuczne w systemie, który decyduje, czy test jednostkowy został zakończony powodzeniem lub niepowodzeniem. Pozorny rozpoczyna się jako sfałszowana do momentu jej przeciwko.

*Klasy zastępczej* — odcinek jest musi zastąpić istniejące zależności (lub współpracownika) w systemie. Za pomocą odcinek, można testować kod bez konieczności wnikania zależnością bezpośrednio. Domyślnie sfałszowana rozpoczyna się jako wejściowy.

Rozważmy następujący fragment kodu:

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Jest to przykład wycinka są określane jako pozorny. W tym przypadku jest to wycinka. Po prostu przechodząc w kolejności, co oznacza, że aby można było utworzyć wystąpienia `Purchase` (system w trakcie testu). Nazwa `MockOrder` jest również bardzo mylące, ponieważ ponownie, kolejność nie jest pozorny.

Lepszym rozwiązaniem byłoby

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Zmieniając nazwę klasy, która ma `FakeOrder`, wprowadzono klasy o wiele bardziej ogólnym, klasa może służyć jako pozorny ani klas zastępczych. Obowiązuje lepszym miejscem dla przypadku testowego. W powyższym przykładzie `FakeOrder` służy jako wejściowy. Nie używasz `FakeOrder` w dowolnej formie podczas assert. `FakeOrder` po prostu została przekazana do `Purchase` klasy w celu spełnienia wymagań konstruktora.

Aby użyć go jako pozorny, możesz to zrobić coś takiego

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

W takim przypadku podczas sprawdzania właściwość sfałszowana (potwierdzające przed nim), więc w powyższym fragmencie kodu `mockOrder` jest pozorny.

> [!IMPORTANT]
> Należy uzyskać prawidłowy terminologię. Wywołanie usługi wycinków "mocks" inni deweloperzy mają wartość false zakładają zgodne z zamiarami użytkownika.

Główny jest, aby pamiętać mocks i wycinków jest mocks przypominają wycinków, że asercja względem makiety obiektu, natomiast nie wystąpiło zapewnienie względem wycinka.

## <a name="best-practices"></a>Najlepsze rozwiązania

### <a name="naming-your-tests"></a>Nadawanie nazw testów
Nazwa testu powinien składać się z trzech części:
- Nazwa metody poddawana testom.
- Scenariusz, w którym jest testowana.
- Oczekiwane zachowanie po wywołaniu tego scenariusza.

#### <a name="why"></a>Dlaczego?
- Standardy nazewnictwa są ważne, ponieważ one jawnie express celem testu.

Testy są więcej niż tylko upewniając się, Twój kod działa, ale oferują też dokumentacji. Po prostu patrząc pakietów testów jednostkowych, można rozpoznać zachowania kodu bez nawet spojrzenie na sam kod. Ponadto gdy testy nie powiodą się, możesz zobaczyć dokładnie scenariuszy, do których nie spełniają Twoich oczekiwań.

#### <a name="bad"></a>Zły:
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Rozmieszczanie testów
**Rozmieść, działania, Asercja** pojawia się często wzorca, gdy testy jednostkowe. Jak wskazuje nazwa, składa się z trzech głównych czynności:
- *Rozmieść* obiektów, tworzenia i konfigurowania zgodnie z potrzebami.
- *ACT* na obiekcie.
- *Asercja* , coś, co jest zgodne z oczekiwaniami.

#### <a name="why"></a>Dlaczego?
- Wyraźnie oddziela jest poddawana testom z *Rozmieść* i *asercja* kroki.
- Mniej szansę intermix potwierdzenia z kodem "Act".

Czytelność jest jednym z najważniejszych aspektów, podczas zapisywania testu. Oddzielając każdy z tych akcji w ramach testu wyraźnie wyróżnić zależności wymagane do wywołania w kodzie, jak kod jest wywoływana i próbujesz potwierdzenia. Może być możliwe, aby połączyć kilka kroków i zmniejszyć rozmiar testu, podstawowym celem jest zapewnienie testu jako do odczytu, jak to możliwe.

#### <a name="bad"></a>Zły:
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Pisanie minimalny zestaw testów przekazywanie
Dane wejściowe do użycia w test jednostkowy powinna być najprostsza możliwa, aby sprawdzić zachowanie, które obecnie testujesz.

#### <a name="why"></a>Dlaczego?
- Testy stają się bardziej odporne na przyszłe zmiany w bazie kodu.
- Im bliżej testowania implementacji zachowania.

Testy, które zawierają więcej informacji, niż jest to wymagane do przekazania testu wyższe prawdopodobieństwo wprowadzenie błędów do testu i może być celem mniej wyczyść test. Podczas pisania testów chcesz skupić się na zachowaniu. Ustawianie właściwości dodatkowych modeli lub przy użyciu wartości różna od zera, gdy nie jest wymagany, źle wpływa tylko na próbujesz potwierdzić.

#### <a name="bad"></a>Zły:
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Należy unikać magic ciągów
Nazwy zmiennych w jednostce testów to jako ważne, jeśli nie ważniejsza, nazw zmiennych w kodzie produkcyjnym. Testy jednostkowe nie powinna zawierać ciągi magic.

#### <a name="why"></a>Dlaczego?
- Eliminuje konieczność Sprawdzanie kodu produkcyjnego, aby ustalić, co sprawia, że wartość specjalne dla czytnika testu.
- Wyraźnie pokazuje, co ma być realizowany *udowodnić, że* zamiast próbowania *osiągnąć*.

Ciągi Magic może nie być jasne do czytnika testów. Jeśli ciąg wygląda niezwykłe, mogą dowiedzieć się, dlaczego określoną wartość został wybrany dla parametru lub zwróć wartość. Może to prowadzić do Przyjrzyj się bliżej szczegóły implementacji, a nie skoncentrować się na testowej.

> [!TIP] 
> Podczas pisania testów, należy dążyć do express tyle przeznaczenie, jak to możliwe. W przypadku ciągów magic dobra metoda jest można przypisać te wartości na stałe.

#### <a name="bad"></a>Zły:
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Należy unikać logiki w testach
Podczas zapisywania jednostkowe, testy Unikaj łączenia ciągów ręczne i logiczne warunków, takich jak `if`, `while`, `for`, `switch`itp.

#### <a name="why"></a>Dlaczego?
- Mniej masz szansę, aby wprowadzić usterkę w testach.
- Skup się na wynik końcowy, a nie szczegóły implementacji.

Po wprowadzeniu logiki w pakiecie testowym znacznie zwiększa ryzyko wprowadzenia usterkę do niego. Ostatnie miejsce, które chcesz znaleźć usterkę znajduje się w pakiecie testowym. Powinny mieć pewność, że testy pracy wysokiego poziomu, w przeciwnym razie zostanie ufasz je. Testy, które nie ufasz, nie oferuje żadnej wartości. Gdy test zakończy się niepowodzeniem, chcesz mieć sens, czy jest coś, co faktycznie problem z kodem i że nie może być ignorowane.

> [!TIP]
> Jeśli logika w teście nieuniknione, należy rozważyć rozdzielenie test na co najmniej dwóch różnych badań.

#### <a name="bad"></a>Zły:
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Preferuj metody pomocnika do instalacji i usuwania
Podobne obiektu lub stanu są wymagane dla testów, najpierw metody pomocnika niż korzystanie z atrybutów instalacji i usuwania, jeśli istnieją.

#### <a name="why"></a>Dlaczego?
- Mniej błąd podczas odczytywania testów, ponieważ cały kod nie jest widoczny w ramach każdego testu.
- Mniejsze ryzyko Definiowanie zbyt dużej lub zbyt mały dla danego testu.
- Mniejsze ryzyko udostępnianie stanu między testami, które tworzy niechcianych zależności między nimi.

W jednostce testowanie struktur, `Setup` jest wywoływana przed test każdej jednostki w pakiecie testowym. Podczas gdy niektóre może zobaczyć jako przydatne narzędzie, zazwyczaj kończy się prowadzące do przeglądarek i trudne do odczytania testów. Zwykle obejmuje różne wymagania, aby uruchomić test działanie każdego testu. Niestety `Setup` wymusza przy użyciu dokładnie te same wymagania dla każdego testu.

> [!NOTE] 
> xUnit usunęła instalacji i usuwania, począwszy od wersji 2.x

#### <a name="bad"></a>Zły:
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Należy unikać wiele asercji
Podczas pisania testów, spróbuj obejmujący tylko jednego potwierdzenia dla testu. Typowe sposoby użycia tylko jednej assert, obejmują:
- Utwórz oddzielne testu dla każdego potwierdzenia.
- Użyć sparametryzowanych testów.

#### <a name="why"></a>Dlaczego?
- Jeśli jeden Asercja nie powiedzie się, nie zostanie ono ocenione kolejnych potwierdzenia.
- Gwarantuje, że nie są potwierdzające wiele przypadków, w testach.
- Zawiera cały obraz tego, dlaczego testy kończą się niepowodzeniem. 

W przypadku wprowadzenia wielu potwierdza do przypadku testowego, go nie masz gwarancję, że wszystkie z deklaracji rozkazujących będzie można wykonać. W większości struktur testowania jednostek po potwierdzenie nie powiedzie się podczas testów jednostkowych, testów postępowania są automatycznie uznawane za zakończonych niepowodzeniem. Może to być mylące, ponieważ funkcje, które rzeczywiście działa, będą wyświetlane jako niepowodzenie.

> [!NOTE]
> Typowe wyjątkiem od tej reguły jest potwierdzające względem obiektu. W tym przypadku jest ogół dopuszczalne mieć wielu deklaracji rozkazujących dla każdej właściwości, aby upewnić się, obiekt jest w stanie się on w oczekiwany.

#### <a name="bad"></a>Zły:
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Lepsze:
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Sprawdzanie poprawności metody prywatne przez metody publiczne testy jednostkowe
W większości przypadków nie należy, aby przetestować metody prywatnej. Metody prywatne są szczegółowo opisuje implementacja. Można traktować je w ten sposób: metody prywatne nigdy nie istnieje w izolacji. W pewnym momencie będzie to mieć publiczną metodę umożliwiający dostęp do Internetu, który wywołuje metody prywatnej jako część jego implementacja. Co zadbać o to wynik końcowy metodę publiczną, która wywołuje jeden prywatny. 

Należy wziąć pod uwagę następujący przypadek

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

Pierwszy reakcję może być do rozpoczęcia pisania test `TrimInput` ponieważ chcesz upewnić się, że metoda działa zgodnie z oczekiwaniami. Jednak jest całkowicie możliwe, `ParseLogLine` manipuluje `sanitizedInput` w taki sposób, który nie będzie, renderowanie Testuj pod względem `TrimInput` bezużyteczny. 

Test rzeczywisty ma być przeprowadzane względem publicznej metody mające połączenie z Internetem `ParseLogLine` ponieważ jest to, co powinno ostatecznie interesujące Cię. 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

Z tego punktu widzenia Jeśli widzisz metody prywatnej, Znajdź publicznej metody i pisania testów względem tej metody. Po prostu, ponieważ jest to metoda prywatna zwraca oczekiwany wynik, nie znaczy, że system, który wywołuje na końcu metody prywatnej używa wynik poprawnie.

### <a name="stub-static-references"></a>Klasy zastępczej odwołań statycznych
Jest jedną z zasad testu jednostkowego, musi mieć pełną kontrolę nad systemie poddawanym testowi. Może to być problematyczne, gdy w kodzie produkcyjnym obejmuje wywołania do odwołań statycznych (np. `DateTime.Now`). Rozważmy poniższy kod

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

Jak ten kod prawdopodobnie można jednostki testowane? Możesz spróbować podejście takich jak

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

Niestety będzie szybkie tworzenie, istnieje kilka problemów dotyczących testów. 

- Jeśli zestaw testów jest uruchamiana we wtorek, drugi test zostanie przekazany, ale pierwszy test zakończy się niepowodzeniem.
- Jeżeli zestaw testów jest wykonywany w innych dniu, pierwszy test zostanie przekazany, ale drugi test zakończy się niepowodzeniem.

Aby rozwiązać te problemy, konieczne będzie wprowadzenie *szwu* w kodzie produkcyjnym. Jest jednym z podejść do zawijania kodu, które należy kontrolować w interfejsie i kodzie produkcyjnym, zależą od tego interfejsu.

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

Stanie się w pakiecie testowym

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

Teraz zestaw testów ma pełną kontrolę nad `DateTime.Now` i można zastąpić klasą zastępczą dowolnej wartości podczas wywoływania metody.
