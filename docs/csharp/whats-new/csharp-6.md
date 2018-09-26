---
title: Co nowego w języku C# 6 — Przewodnik po języku C#
description: Dowiedz się, nowych funkcji w języku C# w wersji 6
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f6f953eacc935d38cc7d45173109c96c52a5e2f3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208188"
---
# <a name="whats-new-in-c-6"></a>Co nowego w języku C# 6

Wersja 6.0 C# zawiera wiele funkcji, które zwiększają produktywność dla deweloperów. Funkcje w tej wersji:

* [Tylko do odczytu właściwości automatyczne](#read-only-auto-properties):
    - Można tworzyć tylko do odczytu właściwości automatyczne, które można ustawić tylko w konstruktorach.
* [Właściwości automatyczne](#auto-property-initializers):
    - Można napisać inicjalizacji wyrażenia, aby ustawić wartość początkową auto właściwością.
* [Elementy członkowskie z wyrażeniem w treści funkcji](#expression-bodied-function-members):
    - Umożliwia tworzenie metod jednej linii za pomocą wyrażenia lambda.
* [przy użyciu statycznej](#using-static):
    - Wszystkie metody klasy pojedynczej można zaimportować do bieżącej przestrzeni nazw.
* [Null — operatorów warunkowych](#null-conditional-operators):
    - Możesz można zwięźle i bezpiecznie uzyskiwać dostęp do elementów członkowskich obiektu nadal trwa sprawdzanie dostępności o wartości null za pomocą operatora warunkowego wartości null.
* [Interpolacja ciągów](#string-interpolation):
    - Możesz zapisać ciąg formatowania wyrażeń za pomocą wbudowanego wyrażeń, zamiast argumentów pozycyjnych.
* [Filtry wyjątków](#exception-filters):
    - Możesz przechwytywać wyrażenia na podstawie właściwości wyjątku lub inny stan programu. 
* [Wyrażenie nameof](#nameof-expressions):
    - Można pozwolić kompilatorowi Generowanie ciągów reprezentujących symboli.
* [await w catch i finally blokuje](#await-in-catch-and-finally-blocks):
    - Możesz użyć `await` wyrażeń w lokalizacjach, które wcześniej niedopuszczalne je.
* [Inicjatory indeksów](#index-initializers):
    - Można tworzyć wyrażenia inicjowania dla kontenerów asocjacyjnych, a także kontenery sekwencji.
* [Metody rozszerzenia dla inicjatory kolekcji](#extension-add-methods-in-collection-initializers):
    - Inicjatory kolekcji może polegać na metody dostępne rozszerzenia, oprócz metod elementu członkowskiego.
* [Ulepszona funkcja rozpoznawania przeciążeń](#improved-overload-resolution):
    - Poprawnie rozpoznać niektórych konstrukcji, które poprzednio wygenerowanym teraz wywołania metody niejednoznaczne.
* [`deterministic` — Opcja kompilatora](#deterministic-compiler-output):
    - Opcja kompilatora deterministyczne gwarantuje, że kolejne kompilacje tego samego źródła generują ten sam wynik w binarnym.

Ogólny efekt tych funkcji jest pisania bardziej zwięzły widok kodu, który jest również bardziej czytelne. Składnia zawiera mniej procedury dla wielu typowych rozwiązań. Jest łatwiej zobaczyć założenia projektowe z mniej procedury. Dowiedz się również, te funkcje i zostanie mu bardziej wydajnej pracy, pisanie czytelność kodu i bardziej skupić się na swoje podstawowe funkcje niż w konstrukcji języka.

W pozostałej części tego tematu zawiera szczegółowe informacje dotyczące każdej z tych funkcji.

## <a name="auto-property-enhancements"></a>Ulepszenia właściwości automatycznej

Składnia automatycznie implementowanych właściwości (zwykle określane jako "auto właściwości") wprowadzone bardzo łatwo jest tworzyć właściwości, które było proste get i ustaw metody dostępu:

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

Jednak to prosta składnia ograniczony rodzaje projektów, które można obsługiwać przy użyciu właściwości auto. C# 6 zwiększa możliwości właściwości automatyczne, dzięki czemu można ich używać w dalszych scenariuszach. Nie trzeba będzie wrócić na bardziej szczegółowy składni deklarowania i manipulowanie pole zapasowe ręcznie tak często.

Nowa składnia jest przeznaczona dla scenariuszy dla właściwości tylko do odczytu i Inicjowanie zmiennej magazynu za auto właściwością.

### <a name="read-only-auto-properties"></a>Auto właściwości tylko do odczytu

*Tylko do odczytu właściwości automatyczne* zapewniają bardziej zwięzły widok składnię, aby utworzyć typy niezmienne. Najbardziej który można pobrać typów niezmienne we wcześniejszych wersjach języka C# został do deklarowania metod ustawiających prywatnych:

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
Przy użyciu tej składni, kompilator nie upewnij się, że typ naprawdę niezmienne. Wymusza tylko który `FirstName` i `LastName` właściwości nie są modyfikowane z dowolnego kodu spoza klasy.

Tylko do odczytu właściwości automatyczne włączanie true zachowanie tylko do odczytu. Właściwość automatyczną deklarowana za pomocą tylko akcesor pobierania:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` i `LastName` właściwości można ustawić tylko w treści konstruktora:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Ustawiany `LastName` w innej metody generuje `CS0200` błąd kompilacji:

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

Ta funkcja umożliwia obsługę języka wartość true, aby tworzenie typów niezmienne i za pomocą składni właściwości automatycznej bardziej zwięzłe i wygodne.

Jeśli dodanie tej składni nie nie powoduje usunięcia dostępnej metody, [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).

### <a name="auto-property-initializers"></a>Inicjatory właściwości automatycznej

*Właściwości automatyczne* umożliwiają deklarowanie początkowa wartość auto właściwością jako część deklaracji właściwości.  We wcześniejszych wersjach te właściwości musi mieć metody ustawiające i trzeba użyć tej metody ustawiającej można zainicjować magazynu danych, używane przez pola pomocniczego. Dla uczniów lub studentów, zawierający nazwę i listę ocen studentów, należy wziąć pod uwagę tej klasy:

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
Wraz z rozwojem tej klasy może zawierać innych konstruktorów. Każdy konstruktora musi zainicjować tego pola lub będą powodować błędy.

C# 6, można przypisać wartość początkową dla miejsca używanego przez auto właściwością w deklaracji właściwości automatycznej:

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Elementu członkowskiego jest inicjowany, którym jest zdeklarowana. Który sprawia, że łatwiej wykonać inicjowania dokładnie jeden raz. Inicjowanie jest częścią deklaracji właściwości, dzięki czemu łatwiej jest równoważne Alokacja magazynu za pomocą interfejsu publicznego dla `Student` obiektów.

Właściwości można za pomocą właściwości odczytu/zapisu, a także właściwości tylko do odczytu, jak pokazano poniżej.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>Elementy członkowskie z wyrażeniem w treści funkcji

Treść wiele elementów członkowskich, które napiszemy składają się z tylko jedną instrukcję, która może być reprezentowany jako wyrażenie. Można zmniejszyć tej składni, pisząc zamiast tego elementu członkowskiego z wyrażeniem w treści. Działa w przypadku metod i właściwości tylko do odczytu. Na przykład zastępowania metody `ToString()` często jest doskonałym kandydatem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Elementy członkowskie z wyrażeniem można również użyć właściwości tylko do odczytu:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Zmienianie istniejącego elementu członkowskiego do elementu członkowskiego zabudowanego wyrażenie jest [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).


## <a name="using-static"></a>Przy użyciu statycznej

*Przy użyciu statycznej* ulepszenie umożliwia importowanie metod statycznych w tej samej klasy. Wcześniej `using` zestawienie zaimportowane wszystkie typy w przestrzeni nazw. 

Często używamy metody statyczne klasy w naszym kodzie. Wielokrotnie wpisanie nazwy klasy mogą zasłaniać znaczenie kodu. Typowym przykładem jest, kiedy piszesz klas, które wykonują wiele obliczeń numerycznych.
Twój kod będzie wyściełana <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> i innych wywołań do różnych metod w <xref:System.Math> klasy. Nowy `using static` składni wprowadzać tych klas znacznie bardziej przejrzyste do odczytu. Należy określić klasę, którą używasz:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Teraz można użyć dowolnej metody statycznej w <xref:System.Math> klasy bez kwalifikowania <xref:System.Math> klasy. <xref:System.Math> Klasa jest przypadek użycia doskonałe dla tej funkcji, ponieważ nie zawiera żadnych metod wystąpienia. Można również użyć `using static` można zaimportować metody statyczne klasy dla klasy, która ma statycznych i metod wystąpienia. Jednym z najbardziej przydatnych przykładów jest <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Należy użyć w pełni kwalifikowaną nazwę klasy, `System.String` w statycznych przy użyciu instrukcji. Nie można użyć `string` słowa kluczowego zamiast tego. 

Teraz można wywołać metody statyczne zdefiniowane w <xref:System.String> klasy bez kwalifikowania tych metod jako elementy członkowskie tej klasy:

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` Funkcji i rozszerzenie metod wchodzić w interakcje w różny sposób, a projekt języka uwzględniane niektórych reguł, które w szczególności rozwiązują tych interakcji. Celem jest, aby zminimalizować prawdopodobieństwo wszelkie istotne zmiany w istniejących ścieżek bazowych kodów, tym Twoich.

Metody rozszerzenia są tylko w zakresie, gdy wywoływany przy użyciu składni wywołania metody rozszerzenia nie wywołanego jako metoda statyczna.
Często zobaczysz następujący w kwerendach LINQ. Możesz zaimportować wzorzec LINQ, importując <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

To importuje wszystkie metody w <xref:System.Linq.Enumerable> klasy.
Metody rozszerzenia są jednak tylko w zakresie wywołanego jako metody rozszerzenia. Nie ma ich w zakresie jeśli są one wezwane przy użyciu składni metody statycznej:

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Ta decyzja jest, ponieważ metody rozszerzenia są zwykle nazywane przy użyciu wyrażenia wywołania metody rozszerzenia. W rzadkich przypadkach, w których są wywoływane przy użyciu statycznej metody należy wywołać składnia jest rozstrzyganie niejednoznaczności.
Wymaganie nazwę klasy jako część wywołania wygląda poddanie.

Istnieje jedna funkcja ostatnie `static using`. `static using` Dyrektywy również importuje wszystkie typy zagnieżdżone. Która pozwala odwoływać się do żadnych zagnieżdżonych typów bez kwalifikacji.

## <a name="null-conditional-operators"></a>Operatory warunkowe null

Wartości null skomplikować kodu. Należy sprawdzić każdy dostęp do zmiennych, aby upewnić się, nie wyłuskujesz `null`. *Operatora warunkowego wartości null* sprawia, że tych sprawdzeń znacznie łatwiejsze i płynny.

Zwykłe zamienienie przez dostęp do elementu członkowskiego `.` z `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

W poprzednim przykładzie, zmienna `first` przypisano `null` przypadku obiektu osoba `null`. W przeciwnym razie, pobiera przypisaną wartość `FirstName` właściwości. Co najważniejsze `?.` oznacza, że nie generuje ten wiersz kodu `NullReferenceException` podczas `person` zmienna jest `null`. Zamiast tego short-circuits i tworzy `null`.

Warto również zauważyć, że to wyrażenie zwraca `string`, niezależnie od tego, wartości `person`.
W przypadku krótkich circuiting `null` wartość zwracana jest wpisany pasuje pełnego wyrażenia.

Często możesz użyć tej konstrukcji z *łączenie wartości null* operator można przypisać wartości domyślne, gdy jedna z właściwości `null`:

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Po prawej stronie operandu po stronie `?.` operator nie jest ograniczona do właściwości lub pola.
Można również użyć do warunkowo wywołania metody. Najczęściej używane funkcje Członkowskie za pomocą operatora warunkowego wartości null jest bezpiecznie wywoływać delegatów (lub programy obsługi zdarzeń), może być `null`.  Możesz to zrobić przez wywołanie metody delegata `Invoke` przy użyciu metody `?.` operatora dostępu do elementu członkowskiego. Widać w przykładzie  
[Delegowanie wzorców](../delegates-patterns.md#handling-null-delegates) tematu.

Reguły `?.` operatora, upewnij się, że po lewej stronie operatora jest oceniane tylko raz. To jest ważne i umożliwia wielu idiomy, w tym przykładzie za pomocą procedury obsługi zdarzeń. Zacznijmy od użycia programu obsługi zdarzeń. W poprzednich wersjach języka C# zostałby zachęca do pisania kodu, takich jak to:

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

Jest to preferowany nad prostsze składni:

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> Poprzedni przykład wprowadza sytuacji wyścigu. `SomethingHappened` Zdarzenia może mieć subskrybentów po zaznaczeniu tej opcji przed `null`, i tych subskrybentów mógł zostać usunięty, zanim zdarzenie jest wywoływane. Spowodowałoby <xref:System.NullReferenceException> zostanie wygenerowany.

W tej drugiej wersji `SomethingHappened` programu obsługi zdarzeń może mieć wartości null podczas testowania, ale jeśli inny kod usuwa program obsługi, może nadal być null wywołanego programu obsługi zdarzeń.

Kompilator generuje kod dla `?.` operatora, które gwarantuje, że po lewej stronie (`this.SomethingHappened`) z `?.` wyrażenie jest wykonywane tylko raz, a wynik jest buforowany:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zapewnienie, że po lewej stronie jest oceniane tylko raz, umożliwi to również użyć dowolnego wyrażenia, w tym wywołań metod w lewej części `?.` nawet jeśli te efekty uboczne, ocenia się je jeden raz, więc efekty uboczne wystąpić tylko raz. Przykładem w naszej zawartości można wyświetlić na [zdarzenia](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Interpolacja ciągów

C# 6 zawiera nową składnię do redagowania ciągi z ciągiem formatu i wyrażenia, które są obliczane, aby utworzyć inne wartości typu ciąg.

Tradycyjnie, trzeba było używać parametry pozycyjne w metodzie, takie jak `string.Format`:

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

Za pomocą języka C# 6 nowe [Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcji umożliwia osadzanie wyrażeń w ciągu formatu. Po prostu poprzedzony ciąg z `$`:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

W tym przykładzie początkowej użyto wyrażenia właściwości podstawione wyrażeń. Możesz rozwinąć na tej składni, aby użyć dowolnego wyrażenia. Na przykład można obliczyć Średnia ocen studenta w ramach interpolacji:

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

Uruchomione w poprzednim przykładzie, może stwierdzisz, że dane wyjściowe `Grades.Average()` może mieć więcej miejsc dziesiętnych niż chcesz. Składnia interpolacji ciągu obsługuje format ciągów dostępne za pomocą metod formatowania wcześniej. Możesz dodać ciągów formatu w nawiasach klamrowych. Dodaj `:` następujące wyrażenie które ma format:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczba zmiennoprzecinkowa z dwóch miejsc po przecinku.

`:` Zawsze jest interpretowany jako separator wyrażeń formatowana i ciąg formatu. Gdy używa wyrażenie może prowadzić do problemów `:` w inny sposób, na przykład operator warunkowy:

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

W powyższym przykładzie `:` jest analizowany jako początek ciągu formatu nie należą do operatora warunkowego. We wszystkich przypadkach, w którym dzieje się tak można otoczyć wyrażenia z nawiasami, aby wymusić na kompilatorze interpretowanie wyrażenia, ponieważ planowane:

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Nie ma żadnych ograniczeń wyrażenia, które można umieścić między nawiasami klamrowymi. Można wykonać złożonego zapytania LINQ, wewnątrz ciągu interpolowanego do wykonywania obliczeń i wyświetlić wynik:

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

W tym przykładzie widać, że można zagnieżdżać wyrażenia interpolacji ciągu wewnątrz innego wyrażenia interpolacji ciągu. W tym przykładzie jest bardzo prawdopodobne, bardziej złożone niż może pojawić się w kodzie produkcyjnym.
Jest to raczej przedstawiają szeroki zakres funkcji. Dowolne wyrażenie języka C# mogą być umieszczone między nawiasami klamrowymi ciągu interpolowanym.

### <a name="string-interpolation-and-specific-cultures"></a>Interpolacja ciągów i określonych kultur

Wszystkie przykłady, które są wyświetlane w poprzedniej sekcji Formatowanie ciągów przy użyciu bieżącej kultury i języka na komputerze gdzie kod jest wykonywany. Często potrzebne formatującej ciąg powstały, używając określonej kultury.
Aby zrobić, użyj fakt, że obiekt utworzony przez Interpolacja ciągów, które mogą być niejawnie konwertowane na <xref:System.FormattableString>.

<xref:System.FormattableString> Wystąpienie zawiera ciąg formatu oraz wynikiem oceny wyrażenia przed rozpoczęciem konwertowania ich na ciągi. Możesz użyć metody publiczne <xref:System.FormattableString> do określania kulturę, gdy ciąg formatowania. Na przykład poniższy przykład tworzy ciąg przy użyciu kultury niemieckim. (Używa znaku ',' jako separatora dziesiętnego i "." znaków jako separatora.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Aby uzyskać więcej informacji, zobacz [Interpolacja ciągów](../language-reference/tokens/interpolated.md) tematu.

## <a name="exception-filters"></a>Filtry wyjątków

Kolejną nową funkcją w C# 6 jest *filtry wyjątków*. Filtry wyjątków są klauzule określające stosowania klauzuli catch danego.
Jeśli w wyrażeniu użytym dla filtru wyjątku daje w wyniku `true`, klauzuli "catch" wykonuje jej normalne przetwarzanie po wystąpieniu wyjątku. Jeśli wyrażenie ma `false`, a następnie `catch` klauzula jest pomijany.

Jednym z zastosowań jest zbadanie informacje o wyjątku, aby określić, czy `catch` klauzuli może przetwarzać wyjątek:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

Kod wygenerowany przez filtry wyjątków zapewnia pełniejsze informacje na temat wyjątek zgłoszony i nie jest przetwarzane. Zanim filtry wyjątków zostały dodane do języka, będziesz potrzebować do pisania kodu, jak pokazano poniżej:

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

Punkt, w którym wyjątek jest zgłaszany zmiany między dwa poniższe przykłady.
W poprzednim kodzie, gdzie `throw` jest używana klauzula, analizy śladu stosu ani badania zrzuty awaryjne pokaże, że wyjątek `throw` instrukcji w klauzuli "catch". Obiekt faktyczny wyjątek będzie zawierać oryginalnego stos wywołań, ale wszystkie inne informacje o żadnych zmiennych w stosie wywołań między tym punktem throw i lokalizacja punktu początkowego throw zostało utracone. 

Natomiast, za pomocą przetwarzaniu kod przy użyciu filtra wyjątku: wyrażenie filtru wyjątków, które daje w wyniku `false`. W związku z tym, wykonanie nigdy nie przechodzi `catch` klauzuli. Ponieważ `catch` klauzula nie jest wykonywane, nie wykonywania operacji odwijania stosu odbywa się. Czy oznacza, że oryginalna throw lokalizacji są zachowywane w debugowania działań, które nastąpi później.

Zawsze, gdy należy ocenić pól lub właściwości wyjątku, zamiast polegania wyłącznie na typ wyjątku, użyj filtru wyjątków, aby zachować więcej informacji o debugowaniu.

Inny zalecany wzorzec z filtry wyjątków jest używane do rejestrowania procedury. Użycie tych korzysta też sposób, w której punkt throw wyjątku jest zachowywane podczas daje w wyniku filtra wyjątku `false`.

Metoda rejestrowania będzie metodą, którego argument jest wyjątek, który bezwarunkowo zwraca `false`:

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Zawsze wtedy, gdy chcesz rejestrować wyjątek, można dodać klauzulę catch i użycie tej metody jako filtru wyjątków:

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

Wyjątki są przechwytywane nigdy, ponieważ `LogException` metoda zawsze zwraca `false`. Z filtrem wyjątku zawsze wartość false oznacza, że można umieszczać w tym obsługi rejestrowania przed wszystkie inne programy obsługi wyjątków:

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

Poprzedni przykład prezentuje bardzo ważne reguł filtry wyjątków.
Filtry wyjątków włączyć scenariusze, w których bardziej ogólnej klauzuli catch wyjątku może następować przed elementem bardziej konkretny akcelerator. Użytkownik może również mieć taki sam typ wyjątku, są wyświetlane w wielu klauzule catch:

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Inny zalecany wzorzec zapobiega klauzule catch przetwarzania wyjątki, gdy jest dołączony debuger. Ta technika pozwala na uruchamianie aplikacji za pomocą debugera i zatrzymać wykonywanie, gdy wyjątek jest zgłaszany.

W kodzie należy dodać filtra wyjątku, aby każdy kod odzyskiwania jest wykonywany tylko wtedy, gdy nie jest dołączony debuger:

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Po dodaniu w kodzie, należy ustawić swoje debuger przerywa przy wszystkich wyjątkach nieobsługiwanych. Uruchom program w debugerze i debuger przerywa zawsze, gdy `PerformFailingOperation()` zgłasza `RecoverableException`.
Debuger przerywa programu, ponieważ w klauzuli "catch" nie można wykonać z powodu filtru wyjątków zwraca wartość false.

## <a name="nameof-expressions"></a>`nameof` Wyrażenia

`nameof` Wyrażenie ma nazwę symbolu. Jest doskonałym sposobem na narzędzia do pracy w każdym przypadku, gdy potrzebna jest nazwa zmiennej, właściwość lub pole elementu członkowskiego.

Jedną z najbardziej typowych używa `nameof` ma na celu dostarczenie nazwa symbolu, który spowodował wyjątek:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Innym zastosowaniem jest przy użyciu XAML na podstawie aplikacji, które implementują `INotifyPropertyChanged` interfejsu:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

Zaletą korzystania z `nameof` operator za pośrednictwem stałym ciągiem jest zrozumieć symbol narzędzia. Jeśli używasz narzędzia do refaktoryzacji można zmienić nazwy symbolu go spowoduje zmianę nazwy w `nameof` wyrażenia. Stałe ciągów nie mają tej zalety. Spróbuj napisać kod w ulubionym edytorze: zmiana nazwy zmiennej, a także wszystkie `nameof` wyrażenia zostaną również zaktualizowane.

`nameof` Wyrażenie powoduje niekwalifikowana nazwa argumentu (`LastName` w poprzednich przykładach) nawet w przypadku używania w pełni kwalifikowana nazwa argumentu:

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

To `nameof` tworzy wyrażenie `FirstName`, a nie `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>Await w Catch i Finally blokuje

C# 5 ma również kilka ograniczeń wokół gdzie można umieścić `await` wyrażenia.
Jeden z nich zostało usunięte w języku C# 6. Teraz możesz używać `await` w `catch` lub `finally` wyrażenia. 

Dodanie wyrażeń await w catch i finally bloków może wydawać się skomplikować, jak te są przetwarzane. Dodajmy przykład w celu omówienia, to wygląd. W dowolnej metody asynchronicznej, można użyć wyrażenia await w klauzuli finally.

Przy użyciu języka C# 6 można również zdefiniować oczekiwania w wyrażeniach catch. Jest to najczęściej używana w scenariuszach logowania:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Szczegóły implementacji, aby dodać `await` obsługi w `catch` i `finally` klauzule gwarantuje, że zachowanie jest zgodne z zachowaniem dla kodu synchronicznego. Gdy kod jest wykonywany w `catch` lub `finally` klauzuli zgłasza wyjątek, wykonanie szuka odpowiedniej `catch` klauzuli w następnym bloku otaczającego. Jeśli było bieżący wyjątek, ten wyjątek zostanie utracony. W tym celu za pomocą wyrażeń oczekiwane w `catch` i `finally` klauzule: odpowiedniej `catch` są wyszukiwane i bieżący wyjątek, jeśli istnieje, zostanie utracony.  

> [!NOTE]
> To zachowanie jest przyczyna, zaleca się zapisać `catch` i `finally` klauzule dokładnie, aby uniknąć wprowadzenia nowych wyjątków.

## <a name="index-initializers"></a>Inicjatory indeksów

*Inicjatory indeksów* to jedna z dwóch funkcji, które inicjatory kolekcji bardziej spójny z użyciem indeksu. We wcześniejszych wersjach języka C#, można użyć *inicjatory kolekcji* tylko z kolekcji stylów sekwencji, w tym <xref:System.Collections.Generic.Dictionary%602> , dodając nawiasów klamrowych otaczających par kluczy i wartości:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

Teraz można użyć ich z <xref:System.Collections.Generic.Dictionary%602> kolekcji i podobnych typów. Nowa składnia obsługuje przypisanie do kolekcji przy użyciu indeksu:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Tej funkcji oznacza, że kontenery asocjacyjne mogą być inicjowane przy użyciu składni podobnej do wprowadzonych w miejscu na potrzeby kontenerów sekwencji dla kilku wersji.

## <a name="extension-add-methods-in-collection-initializers"></a>Rozszerzenie `Add` metody inicjatory kolekcji

Kolejną funkcją, który ułatwia inicjowanie kolekcji jest możliwość używania *— metoda rozszerzenia* dla `Add` metody. Ta funkcja została dodana przez parzystość za pomocą Visual Basic. 

Ta funkcja jest najbardziej użyteczna, gdy masz klasę kolekcji niestandardowej, który ma metodę o innej nazwie do semantycznie dodawania nowych elementów.

Na przykład należy wziąć pod uwagę kolekcję studentów w następujący sposób:

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` Metoda dodaje studenta. Ale nie należy wykonać `Add` wzorca.
W poprzednich wersjach języka C#, nie można użyć inicjatory kolekcji za pomocą `Enrollment` obiektu:

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

Teraz możesz, ale tylko wtedy, gdy tworzysz metodę rozszerzenia, która mapuje `Add` do `Enroll`:

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

Co robisz za pomocą tej funkcji jest do mapowania dowolnej metody dodaje elementy do kolekcji z metodą o nazwie `Add` , tworząc metodą rozszerzenia.

## <a name="improved-overload-resolution"></a>Rozpoznanie przeciążenia ulepszone

Funkcja ta ostatnia jest jeden, który prawdopodobnie nie będą zauważyć. Wystąpiły konstrukcje poprzedniej wersji kompilatora języka C# może mieć wykryto niektóre wywołania metody obejmujące wyrażenia lambda jest niejednoznaczny. Należy wziąć pod uwagę tę metodę:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

We wcześniejszych wersjach języka C# wywołanie tej metody, przy użyciu składni metody grupy może zakończyć się niepowodzeniem:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
Wcześniej kompilator nie można odróżnić prawidłowo między `Task.Run(Action)` i `Task.Run(Func<Task>())`. W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Kompilator języka C# 6 poprawnie ustali, że `Task.Run(Func<Task>())` jest lepszym rozwiązaniem.

### <a name="deterministic-compiler-output"></a>Dane wyjściowe kompilatora deterministyczna

`-deterministic` Opcji powoduje, że kompilator generuje zestaw identycznych danych wyjściowych dla bajt dla kolejnych kompilacje tych samych plików źródłowych.

Domyślnie każdy kompilacji tworzy unikatowe dane wyjściowe w każdej kompilacji. Kompilator dodaje sygnaturę czasową i identyfikator GUID generowany na podstawie liczby losowe. Użyj tej opcji, jeśli chcesz porównać dla bajt danych wyjściowych, aby upewnić się, że zostało skompilowane zachowania spójności w.

Aby uzyskać więcej informacji, zobacz [— opcja kompilatora deterministyczne](../language-reference/compiler-options/deterministic-compiler-option.md) artykułu.
