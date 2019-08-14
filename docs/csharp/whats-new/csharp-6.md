---
title: Co nowego w C# 6- C# przewodniku
description: Poznaj nowe funkcje w C# wersji 6
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971382"
---
# <a name="whats-new-in-c-6"></a>Co nowego w C# 6

Wersja 6,0 systemu C# zawiera wiele funkcji, które zwiększają produktywność dla deweloperów. Ogólnym efektem tych funkcji jest pisanie bardziej zwięzłego kodu, który jest również bardziej czytelny. Składnia zawiera mniej procedury dla wielu typowych praktyk. Łatwiej jest zobaczyć cel projektowania z mniejszą procedury. Poznaj te funkcje również, aby zwiększyć produktywność i napisać bardziej czytelny kod. Możesz skoncentrować się na swoich funkcjach, niż w konstrukcjach języka.

Pozostała część tego artykułu zawiera omówienie każdej z tych funkcji z linkiem do eksplorowania każdej funkcji. Możesz również zapoznać się z funkcjami w [interaktywnej eksplorowaniu C# ](../tutorials/exploration/csharp-6.yml) w sekcji samouczki.

## <a name="read-only-auto-properties"></a>Autowłaściwości tylko do odczytu

*Właściwości autotylko do odczytu* zapewniają bardziej zwięzłą składnię do tworzenia niezmiennych typów. Właściwość autoproperty deklaruje się tylko przy użyciu metody dostępu get:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

Właściwości `FirstName` i`LastName` można ustawić tylko w treści konstruktora tej samej klasy:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Próba ustawienia `LastName` w innej metodzie spowoduje `CS0200` wygenerowanie błędu kompilacji:

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

Ta funkcja umożliwia obsługę języków w przypadku tworzenia niezmiennych typów i używa bardziej zwięzłej i wygodnej składni autowłaściwości.

Jeśli dodanie tej składni nie spowoduje usunięcia dostępnej metody, jest to [zgodna](version-update-considerations.md#binary-compatible-changes)z binarną zmianą.

## <a name="auto-property-initializers"></a>Inicjatory właściwości automatycznej

*Inicjatory właściwości automatycznie* umożliwiają deklarowanie wartości początkowej właściwości autoproperty jako części deklaracji właściwości.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

Element `Grades` członkowski jest inicjowany w miejscu, w którym został zadeklarowany. Dzięki temu można łatwiej wykonać inicjalizację dokładnie jeden raz. Inicjalizacja jest częścią deklaracji właściwości, dzięki czemu łatwiej jest zrównać alokację magazynu z interfejsem publicznym dla `Student` obiektów.

## <a name="expression-bodied-function-members"></a>Składowe funkcji w postaci wyrażeń

Wiele składowych, które piszesz, to pojedyncze instrukcje, które mogą być pojedynczymi wyrażeniami. Zamiast tego Napisz element członkowski z wyrażeniem. Działa w przypadku metod i właściwości tylko do odczytu. Na przykład przesłonięcie `ToString()` jest często doskonałym kandydatem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Tej składni można także użyć do właściwości tylko do odczytu:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Zmiana istniejącego elementu członkowskiego na wyrażenie składowane składowe jest [zgodną](version-update-considerations.md#binary-compatible-changes)z binarną zmianą.

## <a name="using-static"></a>Używanie static

*Użycie statycznego* rozszerzenia umożliwia importowanie metod statycznych pojedynczej klasy. Należy określić klasę, z której korzystasz:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> Nie zawiera żadnych metod wystąpienia. Można również użyć `using static` do zaimportowania metod statycznych klasy dla klasy, która ma zarówno metody statyczne, jak i wystąpienia. Jednym z najbardziej przydatnych przykładów jest <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Należy użyć `System.String` w pełni kwalifikowanej nazwy klasy w statycznej instrukcji using.  Nie można użyć `string` słowa kluczowego.

W przypadku zaimportowania z `static using` instrukcji metody rozszerzające są tylko w zakresie, gdy są wywoływane przy użyciu składni wywołania metody rozszerzenia. Nie są one w zakresie, gdy jest wywoływana jako metoda statyczna. Często są one widoczne w zapytaniach LINQ. Wzorzec LINQ można zaimportować przez <xref:System.Linq.Enumerable>zaimportowanie lub. <xref:System.Linq.Queryable>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Metody rozszerzające są zwykle wywoływane przy użyciu wyrażeń wywołania metody rozszerzenia. Dodanie nazwy klasy w rzadkim przypadku, gdy są one wywoływane przy użyciu składni wywołania metody statycznej, rozwiązuje niejednoznaczności.

`static using` Dyrektywa importuje również wszystkie typy zagnieżdżone. Można odwoływać się do wszelkich zagnieżdżonych typów bez kwalifikacji.

## <a name="null-conditional-operators"></a>Operatory warunkowe o wartości null

*Operator warunkowy o wartości null* sprawia, że sprawdzanie wartości null jest znacznie łatwiejsze i płynne. Zastąp element członkowski `.` dostępem `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

W poprzednim przykładzie zmienna `first` jest przypisywana `null` , jeśli obiektem jest `null`. W przeciwnym razie jest przypisana wartość `FirstName` właściwości. Co ważniejsze, `?.` oznacza, że ten wiersz kodu nie generuje elementu `NullReferenceException` , jeśli `person` zmienna jest `null`. Zamiast tego, krótkie obwody i zwraca `null`. Można również użyć operatora warunkowego null dla dostępu do tablicy lub indeksatora. Zamień `[]`nawwyrażeniuindeksu `?[]` .

Poniższe wyrażenie zwraca `string`, niezależnie od `person`wartości. Ta konstrukcja jest często używana z operatorem *łączenia wartości null* do przypisywania wartości domyślnych, gdy jedna `null`z właściwości jest. W przypadku krótkich obwodów `null` wyrażenia zwracana wartość jest wpisana w celu dopasowania pełnego wyrażenia.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Można również użyć `?.` do warunkowego wywoływania metod. Najbardziej typowym zastosowaniem funkcji Członkowskich z operatorem warunkowym null jest bezpieczne wywoływanie delegatów (lub obsługi zdarzeń), które `null`mogą być.  Wywołamy `Invoke` metodę delegata przy użyciu operatora, `?.` Aby uzyskać dostęp do elementu członkowskiego. W artykule dotyczącego [wzorców delegatów](../delegates-patterns.md#handling-null-delegates) można zobaczyć przykład.

Reguły `?.` operatora zapewniają, że lewa strona operatora jest szacowana tylko raz. Umożliwia ona wiele idiomy, w tym Poniższy przykład, przy użyciu obsługi zdarzeń:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Upewnienie się, że lewa strona jest szacowana tylko raz, również umożliwia użycie dowolnego wyrażenia, w tym wywołań metod, po lewej stronie`?.`

## <a name="string-interpolation"></a>Interpolacja ciągów

W C# przypadku opcji 6 Nowa funkcja [interpolacji ciągu](../language-reference/tokens/interpolated.md) umożliwia osadzanie wyrażeń w ciągu. Wystarczy wpisać ciąg z `$`wyrażeniami i używać wyrażeń między `{` i `}` zamiast liczb porządkowych:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

W tym przykładzie zastosowano właściwości przedstawionych wyrażeń. Możesz użyć dowolnego wyrażenia. Na przykład można obliczyć średnią punktu oceny studenta w ramach interpolacji:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczbę zmiennoprzecinkową z dwoma miejscami dziesiętnymi.

Często może zajść potrzeba sformatowania ciągu utworzonego przy użyciu określonej kultury. Możesz użyć faktu, że obiekt tworzony przez interpolację ciągu może być niejawnie konwertowany na <xref:System.FormattableString?displayProperty=nameWithType>. <xref:System.FormattableString> Wystąpienie zawiera ciąg formatu złożonego i wyniki oceny wyrażeń przed przekonwertowaniem ich na ciągi. <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> Użyj metody, aby określić kulturę podczas formatowania ciągu. Poniższy przykład generuje ciąg przy użyciu kultury niemieckiej (de-DE). (Domyślnie Kultura niemiecki używa znaku "," dla separatora dziesiętnego i znaku "." jako separatora tysięcy).

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Aby rozpocząć pracę z interpolacją ciągów, zobacz [Interpolacja ciągów C# w](../tutorials/exploration/interpolated-strings.yml) samouczku interaktywnym, artykuł [interpolacji ciągów](../language-reference/tokens/interpolated.md) i [Interpolacja ciągów w C# ](../tutorials/string-interpolation.md) samouczku.

## <a name="exception-filters"></a>Filtry wyjątków

*Filtry wyjątków* są klauzulami, które określają, kiedy należy zastosować daną klauzulę catch. Jeśli wyrażenie używane dla filtru wyjątków jest szacowane do `true`, klauzula catch wykonuje normalne przetwarzanie na wyjątek. Jeśli wyrażenie zwróci `false`wartość, `catch` klauzula jest pomijana. Jednym z nich jest badanie informacji o wyjątku, aby określić, czy `catch` klauzula może przetworzyć wyjątek:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof` Wyrażenie

Wyrażenie [nameof](../language-reference/operators/nameof.md) oblicza nazwę symbolu. Jest to świetny sposób, aby uzyskać dostęp do narzędzi, gdy potrzebna jest nazwa zmiennej, właściwości lub pola elementu członkowskiego. Jednym z najpopularniejszych użycia programu `nameof` jest podanie nazwy symbolu, który spowodował wyjątek:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Innym zastosowaniem jest używanie aplikacji opartych na języku XAML `INotifyPropertyChanged` , które implementują interfejs:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Await w blokach catch i finally

C#5 miało kilka ograniczeń, w których można `await` umieścić wyrażenia. Za C# pomocą 6 można teraz używać `await` wyrażeń in `catch` i. `finally` Jest to najczęściej używane w scenariuszach rejestrowania:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Szczegóły implementacji umożliwiające dodanie `await` obsługi wewnątrz `catch` i `finally` klauzule upewnij się, że zachowanie jest zgodne z zachowaniem kodu synchronicznego. Gdy kod wykonywany w `catch` klauzuli or `finally` zgłasza, wykonanie szuka odpowiedniej `catch` klauzuli w następnym otaczającym bloku. Jeśli wystąpił bieżący wyjątek, ten wyjątek zostanie utracony. Dzieje się tak samo w przypadku wyrażeń oczekujących `finally` w `catch` klauzulach i `catch` : odpowiednia wartość jest wyszukiwana, a obecny wyjątek, jeśli istnieje, zostanie utracony.  

> [!NOTE]
> To zachowanie jest przyczyną, że zaleca się pisanie `catch` i `finally` klauzule uważnie, aby uniknąć wprowadzania nowych wyjątków.

## <a name="initialize-associative-collections-using-indexers"></a>Inicjuj kolekcje asocjacyjne przy użyciu indeksatorów

*Inicjatory indeksów* to jedna z dwóch funkcji, które sprawiają, że Inicjatory kolekcji są bardziej spójne z użyciem indeksu. We wcześniejszych wersjach programu C#można było użyć *inicjatorów kolekcji* z kolekcjami stylów sekwencji, w <xref:System.Collections.Generic.Dictionary%602>tym, dodając nawiasy klamrowe wokół par klucz-wartość:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Można ich używać z <xref:System.Collections.Generic.Dictionary%602> kolekcjami i innymi typami, w których dostępna `Add` Metoda akceptuje więcej niż jeden argument. Nowa składnia obsługuje przypisanie przy użyciu indeksu do kolekcji:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Ta funkcja oznacza, że Kontenery asocjacyjne mogą być inicjowane przy użyciu składni podobnej do lokalizacji kontenerów sekwencji dla kilku wersji.

## <a name="extension-add-methods-in-collection-initializers"></a>Metody `Add` rozszerzające w inicjatorach kolekcji

Kolejną funkcją, która ułatwia inicjowanie kolekcji, jest możliwość użycia *metody rozszerzenia* dla `Add` metody. Ta funkcja została dodana do parzystości z Visual Basic. Ta funkcja jest najbardziej przydatna, gdy istnieje Klasa kolekcji niestandardowej, która ma metodę o innej nazwie do semantycznie Dodaj nowe elementy.

## <a name="improved-overload-resolution"></a>Ulepszone rozwiązanie przeciążania

Ta Ostatnia funkcja jest prawdopodobnie niezauważalna. Istnieją konstrukcje, w których Poprzednia wersja C# kompilatora mogła znaleźć pewne wywołania metody, które zawierają niejednoznaczne wyrażenia lambda. Rozważmy tę metodę:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

We wcześniejszych wersjach programu C#wywołanie tej metody przy użyciu składni grupy metod nie powiedzie się:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Wcześniejszy kompilator nie może rozróżnić `Task.Run(Action)` prawidłowo `Task.Run(Func<Task>())`między i. W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 kompilator prawidłowo określa, że `Task.Run(Func<Task>())` jest to lepszy wybór.

### <a name="deterministic-compiler-output"></a>Deterministyczne dane wyjściowe kompilatora

`-deterministic` Opcja instruuje kompilator, aby wytwarzał zestaw danych wyjściowych o identycznym bajcie dla kolejnych kompilacji tych samych plików źródłowych.

Domyślnie każda kompilacja generuje unikatowe dane wyjściowe dla każdej kompilacji. Kompilator dodaje sygnaturę czasową i identyfikator GUID generowany na podstawie liczb losowych. Użyj tej opcji, jeśli chcesz porównać dane wyjściowe bajty dla bajtów w celu zapewnienia spójności między kompilacjami.

Aby uzyskać więcej informacji, zobacz artykuł [Opcja kompilatora-deterministyczna](../language-reference/compiler-options/deterministic-compiler-option.md) .
