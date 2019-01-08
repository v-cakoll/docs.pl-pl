---
title: Co nowego w języku C# 6 — Przewodnik po języku C#
description: Dowiedz się, nowych funkcji w języku C# w wersji 6
ms.date: 12/12/2018
ms.openlocfilehash: d7e3392412ad6f01cd150e31cec43aa99c42b437
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084683"
---
# <a name="whats-new-in-c-6"></a>Co nowego w języku C# 6

Wersja 6.0 C# zawiera wiele funkcji, które zwiększają produktywność dla deweloperów. Ogólny efekt tych funkcji jest pisania bardziej zwięzły widok kodu, który jest również bardziej czytelne. Składnia zawiera mniej procedury dla wielu typowych rozwiązań. Jest łatwiej zobaczyć założenia projektowe z mniej procedury. Dowiedz się również, te funkcje i zostanie mu bardziej wydajnej pracy i napisać bardziej czytelny kod. Możesz skoncentrować się więcej na temat Twojej funkcji niż w konstrukcji języka.

W pozostałej części tego artykułu zawiera omówienie każdego z tych funkcji, za pomocą łącza, aby zapoznać się z każdej funkcji. Możesz też zapoznać się z funkcjami w [interaktywny samouczek dotyczący C# 6](../tutorials/exploration/csharp-6.yml) w sekcji samouczków.

## <a name="read-only-auto-properties"></a>Auto właściwości tylko do odczytu

*Tylko do odczytu właściwości automatyczne* zapewniają bardziej zwięzły widok składnię, aby utworzyć typy niezmienne. Właściwość automatyczną deklarowana za pomocą tylko akcesor pobierania:

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

Ta funkcja umożliwia obsługę języka true Tworzenie typów niezmienne i używa składni właściwości automatycznej bardziej zwięzłe i wygodne.

Jeśli dodanie tej składni nie powoduje usunięcia dostępnej metody, to [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Inicjatory właściwości automatycznej

*Właściwości automatyczne* umożliwiają deklarowanie początkowa wartość auto właściwością jako część deklaracji właściwości.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Elementu członkowskiego jest inicjowany, którym jest zdeklarowana. Który sprawia, że łatwiej wykonać inicjowania dokładnie jeden raz. Inicjowanie jest częścią deklaracji właściwości, dzięki czemu łatwiej jest równoważne Alokacja magazynu za pomocą interfejsu publicznego dla `Student` obiektów.

## <a name="expression-bodied-function-members"></a>Elementy członkowskie z wyrażeniem w treści funkcji

Wiele elementów członkowskich, które należy zapisać są pojedynczej instrukcji, które mogą być pojedynczego wyrażenia. Zamiast niego zapisu elementu członkowskiego z wyrażeniem w treści. Działa w przypadku metod i właściwości tylko do odczytu. Na przykład zastępowania metody `ToString()` często jest doskonałym kandydatem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Dla właściwości tylko do odczytu, można również użyć następującej składni:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Zmienianie istniejącego elementu członkowskiego do elementu członkowskiego zabudowanego wyrażenie jest [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).

## <a name="using-static"></a>Przy użyciu statycznej

*Przy użyciu statycznej* ulepszenie umożliwia importowanie metod statycznych w tej samej klasy. Należy określić klasę, którą używasz:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> Nie zawiera żadnych metod wystąpienia. Można również użyć `using static` można zaimportować metody statyczne klasy dla klasy, która ma statycznych i metod wystąpienia. Jednym z najbardziej przydatnych przykładów jest <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Należy użyć w pełni kwalifikowaną nazwę klasy, `System.String` w statycznych przy użyciu instrukcji.  Nie można użyć `string` słowa kluczowego zamiast tego.

Po zaimportowaniu z `static using` instrukcji, metody rozszerzające są tylko w zakresie, gdy wywoływany przy użyciu składni wywołania metody rozszerzenia. Nie są one w zakresie wywołanego jako metoda statyczna. Często zobaczysz następujący w kwerendach LINQ. Możesz zaimportować wzorzec LINQ, importując <xref:System.Linq.Enumerable>, lub <xref:System.Linq.Queryable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Zwykle wywołują metody rozszerzenia za pomocą wyrażenia wywołania metody rozszerzenia. Dodawanie nazwy klasy w rzadkich przypadkach, gdzie ich wywoływania przy użyciu wywołania metody statycznej składni usuwa niejednoznaczności.

`static using` Dyrektywy również importuje wszystkie typy zagnieżdżone. Wszelkie zagnieżdżone typy bez kwalifikacji można się odwoływać.

## <a name="null-conditional-operators"></a>Operatory warunkowe null

*Operatora warunkowego wartości null* sprawia, że sprawdzenia wartości null znacznie łatwiejsze i płynny. Zastąp dostęp do elementu członkowskiego `.` z `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

W poprzednim przykładzie, zmienna `first` przypisano `null` przypadku obiektu osoba `null`. W przeciwnym razie jest przypisywana wartość `FirstName` właściwości. Co najważniejsze `?.` oznacza, że ten wiersz kodu nie generuje `NullReferenceException` Jeśli `person` zmienna jest `null`. Zamiast tego należy short-circuits i zwraca `null`. Umożliwia także null operatora warunkowego dostępu do tablicy i indeksatora. Zastąp `[]` z `?[]` w wyrażeniu indeksu.

Poniższe wyrażenie zwraca `string`, niezależnie od tego, wartości `person`. Często używają tej konstrukcji z *łączenie wartości null* operatora, aby przypisać domyślnej wartości, gdy jedna z właściwości jest `null`. Gdy wyrażenie short-circuits, `null` wartość zwracana jest wpisany pasuje pełnego wyrażenia.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Można również użyć `?.` do warunkowo wywołania metody. Najczęściej używane funkcje Członkowskie za pomocą operatora warunkowego wartości null jest bezpiecznie wywoływać delegatów (lub programy obsługi zdarzeń), może być `null`.  Wywołasz pełnomocnika `Invoke` przy użyciu metody `?.` operatora dostępu do elementu członkowskiego. Widać w przykładzie [delegować wzorców](../delegates-patterns.md#handling-null-delegates) artykułu.

Reguły `?.` operatora, upewnij się, że po lewej stronie operatora jest oceniane tylko raz. Umożliwia ona wiele idiomy, w tym w poniższym przykładzie przy użyciu programów obsługi zdarzeń:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zapewnienie, że po lewej stronie jest oceniane tylko raz, umożliwi to również użyć dowolnego wyrażenia, w tym wywołania metody, z lewej strony `?.`

## <a name="string-interpolation"></a>Interpolacja ciągów

Za pomocą C# 6, nowe [Interpolacja ciągów](../language-reference/tokens/interpolated.md) funkcja umożliwia osadzanie wyrażeń w ciągu. Po prostu poprzedzony ciąg z `$`i używać wyrażeń między `{` i `}` zamiast liczby porządkowe:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

W tym przykładzie użyto właściwości podstawione wyrażeń. Można użyć dowolnego wyrażenia. Na przykład można obliczyć Średnia ocen studenta w ramach interpolacji:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczba zmiennoprzecinkowa z dwóch miejsc po przecinku.

Często należy sformatować ciąg powstały, używając określonej kultury. Możesz użyć fakt, że obiekt utworzony przez Interpolacja ciągów, które mogą być niejawnie konwertowane na <xref:System.FormattableString?displayProperty=nameWithType>. <xref:System.FormattableString> Wystąpienie zawiera ciąg formatu złożonego oraz wynikiem oceny wyrażenia przed rozpoczęciem konwertowania ich na ciągi. Użyj <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodę, aby określić kulturę, gdy ciąg formatowania. Poniższy przykład tworzy ciąg przy użyciu kultury niemiecki (de-DE). (Domyślnie niemieckiego kultura używa znaku ',' jako separatora dziesiętnego i "." znaków jako separatora.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Aby rozpocząć pracę z Interpolacja ciągów, zobacz [interpolacji w ciągu C# ](../tutorials/intro-to-csharp/interpolated-strings.yml) interaktywnego samouczka [Interpolacja ciągów](../language-reference/tokens/interpolated.md) artykułu, a [Interpolacja w C# ](../tutorials/string-interpolation.md) samouczka.

## <a name="exception-filters"></a>Filtry wyjątków

*Filtry wyjątków* są klauzule określające stosowania klauzuli catch danego. Jeśli w wyrażeniu użytym dla filtru wyjątku daje w wyniku `true`, klauzuli "catch" wykonuje jej normalne przetwarzanie po wystąpieniu wyjątku. Jeśli wyrażenie ma `false`, a następnie `catch` klauzula jest pomijany. Jednym z zastosowań jest zbadanie informacje o wyjątku, aby określić, czy `catch` klauzuli może przetwarzać wyjątek:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof` Wyrażenia

`nameof` Wyrażenie ma nazwę symbolu. Jest doskonałym sposobem na narzędzia do pracy w każdym przypadku, gdy potrzebna jest nazwa zmiennej, właściwość lub pole elementu członkowskiego. Jedną z najbardziej typowych używa `nameof` ma na celu dostarczenie nazwa symbolu, który spowodował wyjątek:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Innym zastosowaniem jest z aplikacji opartych na XAML, które implementują `INotifyPropertyChanged` interfejsu:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Await w Catch i Finally blokuje

C# 5 ma również kilka ograniczeń wokół gdzie można umieścić `await` wyrażenia. Za pomocą C# 6, można teraz używać `await` w `catch` lub `finally` wyrażenia. Jest to najczęściej używana w scenariuszach logowania:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Szczegóły implementacji, aby dodać `await` obsługi w `catch` i `finally` klauzule upewnij się, że zachowanie jest zgodne z zachowaniem dla kodu synchronicznego. Gdy kod jest wykonywany w `catch` lub `finally` klauzuli zgłasza wyjątek, wykonanie szuka odpowiedniej `catch` klauzuli w następnym bloku otaczającego. Jeśli było bieżący wyjątek, ten wyjątek zostanie utracony. W tym celu za pomocą wyrażeń oczekiwane w `catch` i `finally` klauzule: odpowiedniej `catch` są wyszukiwane i bieżący wyjątek, jeśli istnieje, zostanie utracony.  

> [!NOTE]
> To zachowanie jest przyczyna, zaleca się zapisać `catch` i `finally` klauzule dokładnie, aby uniknąć wprowadzenia nowych wyjątków.

## <a name="initialize-associative-collections-using-indexers"></a>Inicjowanie asocjacyjnych kolekcji przy użyciu indeksatorów

*Inicjatory indeksów* to jedna z dwóch funkcji, które inicjatory kolekcji bardziej spójny z użyciem indeksu. We wcześniejszych wersjach programu C#, można użyć *inicjatory kolekcji* z kolekcji stylów sekwencji, w tym <xref:System.Collections.Generic.Dictionary%602>, przez dodawanie nawiasów klamrowych otaczających klucz i wartość pary:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Możesz używać ich z <xref:System.Collections.Generic.Dictionary%602> kolekcje i inne typy miejsce dostępne `Add` metoda przyjmuje więcej niż jeden argument. Nowa składnia obsługuje przypisanie do kolekcji przy użyciu indeksu:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Tej funkcji oznacza, że kontenery asocjacyjne mogą być inicjowane przy użyciu składni podobnej do wprowadzonych w miejscu na potrzeby kontenerów sekwencji dla kilku wersji.

## <a name="extension-add-methods-in-collection-initializers"></a>Rozszerzenie `Add` metody inicjatory kolekcji

Kolejną funkcją, który ułatwia inicjowanie kolekcji jest możliwość używania *— metoda rozszerzenia* dla `Add` metody. Ta funkcja została dodana przez parzystość za pomocą Visual Basic. Ta funkcja jest najbardziej użyteczna, gdy masz klasę kolekcji niestandardowej, który ma metodę o innej nazwie do semantycznie dodawania nowych elementów.

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
