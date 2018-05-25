---
title: Nowości w języku C# 6 - przewodnik C#
description: Dowiedz się nowych funkcji w języku C# w wersji 6
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: c23d4f45441451fbf8a2ad2f939bdb1ed6144154
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="whats-new-in-c-6"></a>Nowości w języku C# 6

6.0 wersji języka C# zawiera wiele funkcji, które zwiększają wydajność dla deweloperów. Funkcje w tej wersji:

* [Tylko do odczytu właściwości Auto](#read-only-auto-properties):
    - Można tworzyć tylko do odczytu auto właściwości, które można ustawić tylko w przypadku konstruktorów.
* [Inicjatory Auto właściwością](#auto-property-initializers):
    - Można pisać wyrażenia inicjowania, aby ustawić początkowej wartości auto właściwością.
* [Elementy członkowskie zabudowanych wyrażenia funkcji](#expression-bodied-function-members):
    - Można tworzyć za pomocą wyrażenia lambda metody jednego wiersza.
* [przy użyciu statycznego](#using-static):
    - Wszystkie metody jednej klasy można zaimportować do bieżącej przestrzeni nazw.
* [Null — operatory warunkowe](#null-conditional-operators):
    - Zwięźle i bezpiecznie dostępnych elementów członkowskich obiektu podczas nadal sprawdzania wartości null z operatora warunkowego wartości null.
* [Ciąg interpolacji](#string-interpolation):
    - Ciąg formatowania wyrażenia za pomocą wbudowanego wyrażeń zamiast argumenty pozycyjne może zapisywać.
* [Filtry wyjątków](#exception-filters):
    - Można przechwycić wyrażenia na podstawie właściwości wyjątek lub inny stan programu. 
* [nameof wyrażenia](#nameof-expressions):
    - Możesz pozwolić, aby wygenerować reprezentacji ciągu symbole kompilatora.
* [await w catch i finally blokuje](#await-in-catch-and-finally-blocks):
    - Można użyć `await` wyrażenia w lokalizacjach, które je wcześniej niedozwolone.
* [Indeks inicjatory](#index-initializers):
    - Można tworzyć wyrażenia inicjowania asocjacyjnej kontenerów, a także kontenery sekwencji.
* [Metody rozszerzenia dla inicjatory kolekcji](#extension-add-methods-in-collection-initializers):
    - Inicjatory kolekcji można oparte na metodach dostępne rozszerzenia, oprócz metod elementu członkowskiego.
* [Rozpoznanie przeciążenia ulepszone](#improved-overload-resolution):
    - Niektóre konstrukcje wygenerowanych wcześniej wywołania metody niejednoznaczne teraz rozpoznawane poprawnie.

Ogólny efekt tych funkcji jest który zapisu bardziej zwięzły kod, który jest również bardziej czytelne. Składnia zawiera mniej procedury dla wielu typowych rozwiązań. Możliwe jest łatwiejsze Zobacz celem projektu z mniej procedury. Informacje te funkcje także i będzie bardziej wydajnej pracy, pisania czytelność kodu i bardziej skoncentrować się na Twoje podstawowe funkcje niż w konstrukcji języka.

W pozostałej części tego tematu zawiera szczegółowe informacje na każdym z tych funkcji.

## <a name="auto-property-enhancements"></a>Ulepszenia Auto-właściwością 

Składnia automatycznie implementowanych właściwości (zwykle nazywane "właściwości auto") wprowadzone łatwość tworzenia właściwości, które ma prosty get i set metod dostępu:

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

Jednak ta składnia proste ograniczony rodzaje projektów, które można obsługiwać przy użyciu właściwości auto. C# 6 zwiększa możliwości właściwości auto, dzięki czemu można ich używać w scenariuszach więcej. Nie musisz przełączyć na pełniejsze składnia deklarowanie i operowanie nimi pole zapasowe ręcznie często.

Nowej składni adresów scenariusze dla właściwości tylko do odczytu i Inicjowanie zmiennej magazynu za auto właściwością.

### <a name="read-only-auto-properties"></a>Auto właściwości tylko do odczytu

*Tylko do odczytu właściwości auto* zapewniają bardziej zwięzły składni do tworzenia typów niezmienialny. Najbardziej Ci można modyfikować typów we wcześniejszych wersjach języka C# to zadeklarować ustawiające prywatnych:

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
Przy użyciu tej składni, kompilator nie upewnij się, że typ naprawdę nie można modyfikować. Wymusza tylko który `FirstName` i `LastName` z kodu poza klasy nie są modyfikowane właściwości.

Tylko do odczytu właściwości automatycznie włączyć true zachowania tylko do odczytu. Auto właściwością został zadeklarowany za pomocą dostępu get:

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

Ta funkcja umożliwia obsługę języka wartość true, tworzenie typów niezmienne i przy użyciu składni auto właściwością zwięzły i bardziej wygodne.

### <a name="auto-property-initializers"></a>Inicjatory Auto właściwością

*Inicjatory Auto-właściwością* można zadeklarować jako część deklaracji właściwości początkowej wartości dla właściwości auto.  We wcześniejszych wersjach te właściwości musi mieć metody ustawiające i należy użyć tej metody ustawiającej można zainicjować magazynu danych używana przez pole zapasowe. Należy wziąć pod uwagę tej klasy dla użytkowników domowych, zawierający nazwę i listę klas studenta:

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
Wraz z rozwojem tej klasy, może zawierać inne konstruktorów. Każdy Konstruktor musi zainicjować tego pola lub będą powodować błędy.

C# 6 umożliwia przypisanie wartości początkowej dla miejsca używanego przez auto właściwością w deklaracji właściwości automatycznej:

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Element członkowski został zainicjowany, którym jest zadeklarowany. Który ułatwia zainicjować dokładnie raz. Inicjowanie jest częścią deklaracja właściwości, co ułatwia są równoważne Alokacja magazynu z interfejs publiczny dla `Student` obiektów.

Inicjatory właściwości można użyć właściwości odczytu/zapisu, jak również właściwości tylko do odczytu, jak pokazano tutaj.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>Elementy członkowskie zabudowanych wyrażenie — funkcja

Treść wiele elementów członkowskich, które możemy zapisać składają się z tylko jedną instrukcję, który może być reprezentowany jako wyrażenia. Można zmniejszyć tego składni pisząc zamiast tego elementu członkowskiego zabudowanych wyrażenia. Działa metody i właściwości tylko do odczytu. Na przykład zastępująca `ToString()` często jest doskonałym kandydatem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Można także użyć zabudowanych wyrażenia elementów członkowskich właściwości tylko do odczytu:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a>przy użyciu statycznego

*Przy użyciu statycznego* ulepszenie umożliwia importowanie metod statycznych tej samej klasy. Wcześniej `using` instrukcji zaimportowane wszystkie typy w przestrzeni nazw. 

Często używamy metody statyczne klasy w całym naszego kodu. Wielokrotnie wpisanie nazwy klasy mogą przesłaniać znaczenie kodu. Typowym przykładem jest podczas zapisywania klasy, które wielu obliczeń liczbowych.
Kod będzie wyściełana <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> i inne wywołania do różnych metod w <xref:System.Math> klasy. Nowe `using static` składni ułatwia tych klas znacznie czyszczący do odczytu. Należy określić klasę, którego używasz:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Teraz, można użyć dowolnej metody statycznej w <xref:System.Math> klasy bez kwalifikowanie <xref:System.Math> klasy. <xref:System.Math> Klasa jest przypadek użycia doskonały dla tej funkcji, ponieważ nie zawiera żadnych metod wystąpienia. Można również użyć `using static` klasy statycznej metody klasy, która ma obu statyczna importu do metody wystąpienia. Jednym z najbardziej przydatne przykłady jest <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Należy użyć nazwy FQDN klasy `System.String` w statycznego za pomocą instrukcji. Nie można użyć `string` słowa kluczowego zamiast tego. 

Można teraz wywołać metody statyczne zdefiniowane w <xref:System.String> klasy bez kwalifikowanie tych metod jako elementy członkowskie tej klasy:

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` Funkcji i rozszerzenie metody interakcji w sposób i niektórych reguł, które w szczególności adresu tych interakcji zawarte w projekcie języka. Celem jest, aby zminimalizować ryzyko wszelkie istotne zmiany w istniejących codebases, tym należy do Ciebie.

Metody rozszerzenia są tylko w zakresie wywołanego przy użyciu składni wywołanie metody rozszerzenia nie wywołanego jako metoda statyczna.
Często pojawi się to w zapytaniach LINQ. Można importować wzorzec LINQ, importując <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Zostaną zaimportowane wszystkie metody w <xref:System.Linq.Enumerable> klasy.
Metody rozszerzenia są jednak tylko w zakresie wywołanego jako metody rozszerzenia. Nie są w zakresie, jeśli są one nazywane przy użyciu składni metody statycznej:

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Ta decyzja jest ponieważ metody rozszerzenia są zwykle nazywane przy użyciu wyrażenia wywołania metody rozszerzenia. W rzadkich przypadkach, gdy są wywoływane przy użyciu metody statycznej wywołania składni jest, aby usunąć niejednoznaczność.
Wymaganie nazwę klasy w ramach wywołania prawdopodobnie rozsądnego.

Istnieje jedna funkcja ostatniego `static using`. `static using` Dyrektywy również importuje wszystkie typy zagnieżdżone. Który umożliwia wskazanie żadnych zagnieżdżonych typów bez kwalifikacji.

## <a name="null-conditional-operators"></a>Operatory warunkowe null

Wartości zerowe skomplikować kodu. Należy sprawdzić co dostępu do zmiennych, aby upewnić się, nie są usunięcia odwołania `null`. *Null operator warunkowy* sprawia, że te testy znacznie łatwiejsze i płynnych.

Po prostu zastąpić dostęp do elementu członkowskiego `.` z `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

W powyższym przykładzie zmienna `first` przypisano `null` Jeśli obiekt osoby jest `null`. W przeciwnym razie zostanie przypisana wartość `FirstName` właściwości. Przede wszystkim `?.` oznacza, że ten wiersz kodu nie generuje `NullReferenceException` podczas `person` zmienna jest `null`. Zamiast tego short-circuits i tworzy `null`.

Ponadto pamiętać, że wyrażenie zwraca `string`, niezależnie od wartości `person`.
W przypadku krótkich circuiting `null` wartość zwracana jest wpisana do dopasowania pełnego wyrażenia.

Często służą ta konstrukcja z *null łączenie* operator można przypisać wartości domyślne, jeśli jedna z właściwości są `null`:

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Argument operacji po stronie prawej z `?.` operator nie jest ograniczona do właściwości lub pól.
Można również użyć do warunkowo wywołania metody. Najczęściej używane funkcje elementów członkowskich o wartości null operator warunkowy jest można bezpiecznie wywołać delegatów (lub procedury obsługi zdarzeń) może to być `null`.  Można to zrobić przez wywołanie metody delegata `Invoke` przy użyciu metody `?.` operator może uzyskać dostępu do elementu członkowskiego. Widać w przykładzie  
[Delegowanie wzorce](../delegates-patterns.md#handling-null-delegates) tematu.

Zasady `?.` operator upewnij się, że po lewej stronie operatora jest oceniane tylko raz. Ważne jest i umożliwia wielu idioms, w tym przykładzie przy użyciu programów obsługi zdarzeń. Zacznijmy od użycia programu obsługi zdarzeń. W poprzednich wersjach języka C# zostałby zachęca do pisania kodu, jak to:

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

To preferowany nad prostsze składni:

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> Powyższy przykład wprowadza wyścigu. `SomethingHappened` Zdarzenia może mieć subskrybentów po zaznaczeniu tej opcji przed `null`, i tych subskrybentów mógł zostać usunięty przed zdarzenie jest wywoływane. Spowodowałoby <xref:System.NullReferenceException> zostanie wygenerowany.

W tej drugiej wersji `SomethingHappened` obsługi zdarzeń może mieć wartości null podczas testowania, ale jeśli inny kod usuwa obsługi, nadal możliwe wartości null podczas wywoływania obsługi zdarzeń.

Kompilator generuje kod dla `?.` operator, który zapewnia po lewej stronie (`this.SomethingHappened`) z `?.` wyrażenie jest obliczane raz, a wynik jest buforowany:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zapewnienie, że po lewej stronie jest oceniane tylko raz umożliwia również użyć dowolnego wyrażenia, w tym wywołania metody, po lewej stronie `?.` nawet jeśli te efekty uboczne, są one oceniane raz, więc efekty uboczne wystąpić tylko raz. Można wyświetlić na przykład w naszej zawartości [zdarzenia](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Ciąg interpolacji

C# 6 zawiera nowej składni do tworzenia ciągów z ciągu formatu i wyrażeń, które są obliczane, aby utworzyć inne wartości ciągu.

Zazwyczaj potrzebne do użycia parametrów pozycyjnych w metodzie, takie jak `string.Format`:

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

C# 6 nowe [ciągu interpolacji](../language-reference/tokens/interpolated.md) funkcja umożliwia osadzanie wyrażeń w ciągu formatu. Po prostu poprzedzony ciąg z `$`:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

W tym przykładzie początkowej użyto wyrażenia właściwości podstawione wyrażeń. Można rozwinąć w tej składni, aby użyć dowolnego wyrażenia. Na przykład można obliczyć Średnia ocen studenta jako część interpolacji:

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

Uruchomione w poprzednim przykładzie, czy stwierdzisz, że w danych wyjściowych `Grades.Average()` może mieć więcej miejsc dziesiętnych, niż chcesz. Składnia ciągu interpolacji obsługuje wszystkie w formacie ciągów dostępne przy użyciu metod formatowania wcześniej. Możesz dodać ciągów formatu w nawiasach klamrowych. Dodaj `:` po wyrażeniu formatowania:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczba zmiennoprzecinkowa z dwóch miejsc po przecinku.

`:` Zawsze jest interpretowany jako separator wyrażeniu formatowania ciągu formatu. Może to powodować problemy, gdy używa wyrażenia `:` w inny sposób, na przykład operator warunkowy:

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

W powyższym przykładzie `:` jest analizowana jako początku ciąg formatu nie jest częścią operator warunkowy. We wszystkich przypadkach, gdy tak się stanie należy ująć wyrażenia w nawiasach, aby wymusić kompilatora, aby zinterpretować wyrażenia, jak zamierzasz:

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Nie ma ograniczenia wyrażeń, które można umieścić w nawiasach klamrowych. Można wykonywać złożonych zapytań LINQ w ciągu interpolowanym można przeprowadzić obliczenia i wyświetlić wyniki:

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

W tym przykładzie widać, czy można zagnieżdżać interpolacji wyrażeniem wewnątrz innego interpolacji wyrażeniem. W tym przykładzie jest bardzo prawdopodobne, bardziej złożone niż byłaby wskazana w kodzie produkcyjnym.
Zamiast jest opisowy szerokości funkcji. Dowolne wyrażenie C# można umieścić między nawiasami klamrowymi ciągu interpolowanym.

### <a name="string-interpolation-and-specific-cultures"></a>Ciąg interpolacji i określone kultury

Wszystkie przykłady w poprzedniej sekcji formatu ciągi, przy użyciu bieżącej kultury i języka na komputerze gdzie kod jest wykonywany. Często konieczne może być ciąg utworzony, używając określonej kultury formatu.
Robić, które używają fakt, że obiekt utworzony przez interpolacji ciągu można niejawnie przekonwertować <xref:System.FormattableString>.

<xref:System.FormattableString> Wystąpienie zawiera ciąg formatu oraz wynikiem obliczenia wyrażenia przed ich konwertowanie na ciągi. Można użyć metod publicznych klasy <xref:System.FormattableString> do określenia kultury podczas formatowania ciągu. Na przykład poniższy przykład tworzy ciąg przy użyciu kultury niemieckim. (Separator dziesiętny używa znaku ',' i '.' znak jako separatora.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Aby uzyskać więcej informacji, zobacz [ciągu interpolacji](../language-reference/tokens/interpolated.md) tematu.

## <a name="exception-filters"></a>Filtry wyjątków

Kolejną nową funkcją w C# 6 jest *filtry wyjątków*. Filtry wyjątków są klauzule określające stosowania klauzuli catch danego.
Jeśli w wyrażeniu użytym dla filtru wyjątku daje w wyniku `true`, w klauzuli catch wykonuje jego normalnego przetwarzania z powodu wyjątku. Jeśli wyrażenie ma `false`, a następnie `catch` klauzuli zostanie pominięta.

Zapoznaj się z informacjami o wyjątku, aby ustalić, czy jest jedno użycie `catch` klauzuli może przetwarzać wyjątek:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

Kod wygenerowany przez filtry wyjątków zapewnia lepsze informacje o wyjątek zgłoszony i nie jest przetwarzane. Przed dodaniem filtry wyjątków dla języka, należy utworzyć kod podobne do poniższych:

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

Punkt, w którym wyjątku zmiany między te dwa przykłady.
W poprzednim kodzie, gdzie `throw` jest używana klauzula, analiza śledzenia stosu ani badania zrzuty awaryjne wyświetli, czy wyjątek został zgłoszony z `throw` instrukcji w klauzuli catch. Obiekt wyjątku rzeczywiste będzie zawierać oryginalnego stos wywołań, ale wszystkie inne informacje o zmiennych w stosie wywołań między tym punkcie throw i lokalizację punktu początkowego throw zostało utracone. 

Natomiast który o przetwarzaniu kod przy użyciu filtru wyjątków: daje w wyniku wyrażenia filtru wyjątków `false`. W związku z tym wykonywania nigdy nie przechodzi `catch` klauzuli. Ponieważ `catch` klauzuli nie wykonuj, odwijanie stosu nie ma miejsce. Czy oznacza, że oryginalne throw lokalizacji są zachowywane na potrzeby debugowania działań, które nastąpi później.

Zawsze, gdy należy ocenić pola lub właściwości wyjątek, zdejmując to zadanie wyłącznie typ wyjątku, użyj filtru wyjątków, aby zachować więcej informacji o debugowaniu.

Inny, zalecane wzorca zawierającego filtry wyjątków jest używane do rejestrowania procedury. To użycie korzysta również sposób, w której punkt Zgłoś wyjątek jest zachowywane podczas daje w wyniku filtra wyjątku `false`.

Metoda rejestrowania będą metody, którego argument jest wyjątek, który bezwarunkowo zwraca `false`:

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Zawsze, gdy chcesz rejestrować wyjątek, możesz dodać klauzuli catch i tej metody można użyć jako filtru wyjątków:

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

Wyjątki są przechwytywane nigdy, ponieważ `LogException` metoda zawsze zwraca `false`. Tego filtru wyjątków zawsze wartość FAŁSZ oznacza, że umieszczenie tej obsługi rejestrowania przed wszystkie inne programy obsługi wyjątków:

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

Powyższy przykład prezentuje ważne aspektu filtrów wyjątków.
Filtry wyjątków umożliwić scenariuszy, w których bardziej ogólne klauzuli catch wyjątku może pojawić się przed co bardziej szczegółowe. Istnieje również możliwość mają ten sam typ wyjątku, są wyświetlane w wielu klauzule catch:

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Inny wzorzec zalecane zapobiega klauzule catch przetwarzania wyjątki, gdy jest dołączony debuger. Ta technika pozwala na uruchamianie aplikacji z debugera i zatrzymuje wykonywanie, gdy jest zgłaszany wyjątek.

W kodzie należy dodać filtra wyjątku, aby każdy kod odzyskiwania wykonuje tylko wtedy, gdy nie jest dołączony debuger:

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Po dodaniu to w kodzie, należy ustawić debuger można przerwać w przypadku wszystkich nieobsługiwanych wyjątków. Uruchom program w debugerze i debuger dzieli się po każdej zmianie `PerformFailingOperation()` zgłasza `RecoverableException`.
Debuger dzieli programu, ponieważ w klauzuli catch nie będzie można wykonać z powodu filtru wyjątków zwracającego wartość false.

## <a name="nameof-expressions"></a>`nameof` Wyrażenia

`nameof` Wyrażenie ma nazwę symbolu. Jest to dobry sposób na Pobierz narzędzia Praca zawsze, gdy potrzebna jest nazwa zmienną, właściwością lub polem członka.

Jedną z najbardziej typowych używa `nameof` jest zapewnienie nazwa symbolu, który spowodował wyjątek:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Użyj innego jest z aplikacjami na podstawie języka XAML, które implementuje `INotifyPropertyChanged` interfejsu:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

Zaletą używania `nameof` operator przez ciąg stałej jest dokładnie symbolu, narzędzia. Jeśli używasz narzędzia do refaktoryzacji Aby zmienić nazwę symbolu, go spowoduje zmianę nazwy w `nameof` wyrażenia. Ciągi o stałej nie ma tego korzyści. Wypróbuj ją samodzielnie w edytorze Ulubione: Zmień nazwę zmiennej, a także wszystkie `nameof` również zaktualizuje wyrażenia.

`nameof` Wyrażenie zwraca niekwalifikowana nazwa argumentu (`LastName` w poprzednich przykładach) nawet wtedy, gdy używasz w pełni kwalifikowana nazwa argumentu:

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

To `nameof` wyrażenie daje `FirstName`, a nie `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>Await w Catch i Finally blokuje

C# 5 ma kilka ograniczeń wokół lokalizację można `await` wyrażenia.
Jednym z tych została usunięta w języku C# 6. Można teraz używać `await` w `catch` lub `finally` wyrażenia. 

Dodanie await wyrażenia w catch i finally bloki może wydawać się skomplikować, jak te są przetwarzane. Dodajmy przykład omówimy sposobu wyświetlania. W dowolnej metody asynchronicznej, można użyć wyrażenia await w klauzuli finally.

C# 6 można również zdefiniować oczekiwania w wyrażeniach catch. To jest najczęściej używana w scenariuszach rejestrowania:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Szczegóły implementacji dodawania `await` obsługuje wewnątrz `catch` i `finally` klauzule zapewnia, że zachowanie jest zgodne z zachowaniem synchroniczne kodu. Jeśli kod wykonywany w `catch` lub `finally` klauzuli zgłasza wyjątek, wykonanie szuka odpowiedniej `catch` klauzuli w następnym bloku otaczającego. Wystąpił wyjątek bieżący, ten wyjątek zostanie utracone. W tym celu z Oczekiwano wyrażenia w `catch` i `finally` klauzule: odpowiedniej `catch` jest wyszukiwany i bieżący wyjątek, jeśli istnieje, zostanie utracony.  

> [!NOTE]
> To zachowanie jest powód, zaleca się zapisu `catch` i `finally` klauzule dokładnie, aby uniknąć wprowadzenia nowych wyjątków.

## <a name="index-initializers"></a>Inicjatory indeksu

*Inicjatory indeksu* jest jednym z dwóch funkcje inicjatory kolekcji bardziej spójny z użyciem indeksu. We wcześniejszych wersjach języka C#, można użyć *inicjatory kolekcji* tylko z kolekcjami styl sekwencji, w tym <xref:System.Collections.Generic.Dictionary%602> przez dodanie nawiasów klamrowych otaczających pary kluczy i wartości:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

Teraz można używać ich z <xref:System.Collections.Generic.Dictionary%602> kolekcje i podobnych typów. Nowej składni obsługuje przypisanie do kolekcji przy użyciu indeksu:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Ta funkcja oznacza, że asocjacyjnej kontenery mogą być inicjowane przy użyciu składni podobnej do została co w przypadku sekwencji kontenery różne wersje.

## <a name="extension-add-methods-in-collection-initializers"></a>Rozszerzenie `Add` metod w inicjatory kolekcji

Inny funkcja, która ułatwia inicjowania kolekcji jest możliwość używania *— metoda rozszerzenia* dla `Add` metody. Ta funkcja została dodana do parzystości za pomocą Visual Basic. 

Funkcja jest najbardziej przydatna w przypadku klasy niestandardowej kolekcji, która ma metodę o innej nazwie do semantycznie dodawania nowych elementów.

Rozważmy na przykład kolekcja studentów w następujący sposób:

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` Metoda dodaje studenta. Ale nie będzie zgodna z `Add` wzorca.
W poprzednich wersjach języka C#, nie można użyć inicjatory kolekcji z `Enrollment` obiektu:

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

Teraz możesz, ale tylko wtedy, gdy tworzenie metodę rozszerzenia, która mapuje `Add` do `Enroll`:

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

Czynności przy użyciu tej funkcji ma mapowania dowolnej metody dodaje elementy kolekcji do metody o nazwie `Add` tworząc metody rozszerzenia.

## <a name="improved-overload-resolution"></a>Rozpoznanie przeciążenia ulepszone

Ta funkcja ostatniego jest jeden, który prawdopodobnie nie będzie zauważyć. Znaleziono konstrukcje poprzedniej wersji kompilatora C# mogą mieć wykryto niektóre wywołania metody obejmujące wyrażenia lambda jest niejednoznaczna. Tej metody należy wziąć pod uwagę:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

We wcześniejszych wersjach języka C# wywołanie tej metody, przy użyciu składni grupy — metoda nie powiedzie się:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
Wcześniej kompilatora nie można prawidłowo między rozróżnienia `Task.Run(Action)` i `Task.Run(Func<Task>())`. W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Kompilator języka C# 6 poprawnie określi, że `Task.Run(Func<Task>())` jest lepszym rozwiązaniem.
