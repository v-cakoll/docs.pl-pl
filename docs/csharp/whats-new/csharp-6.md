---
title: Co nowego w języku C# 6 - Przewodnik po językach C#
description: Poznaj nowe funkcje w języku C# w wersji 6
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399393"
---
# <a name="whats-new-in-c-6"></a>Co nowego w C# 6

Wersja 6.0 języka C# zawierała wiele funkcji, które zwiększają produktywność deweloperów. Ogólny efekt tych funkcji jest, że piszesz bardziej zwięzły kod, który jest również bardziej czytelny. Składnia zawiera mniej ceremonii dla wielu typowych praktyk. Łatwiej jest zobaczyć intencję projektu z mniejszą ceremonią. Dobrze się poznaj te funkcje, a będziesz bardziej produktywny i napisz bardziej czytelny kod. Możesz skoncentrować się bardziej na swoich funkcjach niż na konstrukcjach języka.

W dalszej części tego artykułu zawiera omówienie każdej z tych funkcji, z linkiem do eksplorowania każdej funkcji. Można również eksplorować funkcje w [interaktywnej eksploracji w języku C# 6](../tutorials/exploration/csharp-6.yml) w sekcji samouczków.

## <a name="read-only-auto-properties"></a>Właściwości automatyczne tylko do odczytu

*Właściwości automatyczne tylko do odczytu* zapewniają bardziej zwięzłą składnię do tworzenia typów niezmiennych. Deklarujesz auto-właściwość tylko z get akcesor:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

I `FirstName` `LastName` właściwości można ustawić tylko w treści konstruktora tej samej klasy:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Próba ustawienia `LastName` w innej metodzie generuje błąd `CS0200` kompilacji:

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

Ta funkcja umożliwia obsługę języka true do tworzenia typów niezmienne i używa bardziej zwięzłe i wygodne składni auto-właściwości.

Jeśli dodanie tej składni nie powoduje usunięcia dostępnej metody, jest to [zmiana zgodna z binarną](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Inicjatory właściwości automatycznych

*Inicjatory właściwości* auto umożliwiają zadeklarowanie wartości początkowej właściwości auto jako części deklaracji właściwości.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

Element `Grades` członkowski jest inicjowany, gdzie jest zadeklarowany. To sprawia, że łatwiej wykonać inicjowanie dokładnie raz. Inicjowanie jest częścią deklaracji właściwości, co ułatwia zrównanie alokacji `Student` magazynu z interfejsem publicznym dla obiektów.

## <a name="expression-bodied-function-members"></a>Elementy członkowskie funkcji zabudowane wyrażeniem

Wiele członków, które piszesz są pojedyncze instrukcje, które mogą być pojedyncze wyrażenia. Zamiast tego napisz element członkowski zabudowany wyrażeniem. Działa dla metod i właściwości tylko do odczytu. Na przykład zastąpienie `ToString()` jest często świetnym kandydatem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Tej składni można również użyć dla właściwości tylko do odczytu:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Zmiana istniejącego elementu członkowskiego na element członkowski wyrażenia jest [zmianą zgodną z binarną.](version-update-considerations.md#binary-compatible-changes)

## <a name="using-static"></a>za pomocą statycznego

*Za pomocą statycznego* rozszerzenia umożliwia importowanie metod statycznych pojedynczej klasy. Określasz klasę, której używasz:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Nie <xref:System.Math> zawiera żadnych metod wystąpienia. Można również `using static` użyć do zaimportowania klasy metod statycznych dla klasy, która ma zarówno metody statyczne i wystąpienia. Jednym z najbardziej przydatnych <xref:System.String>przykładów jest:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Należy użyć w pełni kwalifikowanej `System.String` nazwy klasy, w instrukcji statycznego using.  Zamiast tego `string` nie można użyć słowa kluczowego.

Podczas importowania `static using` z instrukcji metody rozszerzenia są tylko w zakresie, gdy wywoływane przy użyciu składni wywołania metody rozszerzenia. Nie są one w zakresie, gdy wywoływana jako metoda statyczna. Często zobaczysz to w zapytaniach LINQ. Wzór LINQ można zaimportować, <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable>importując lub .

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Zazwyczaj należy wywołać metody rozszerzenia przy użyciu wyrażeń wywołania metody rozszerzenia. Dodanie nazwy klasy w rzadkich przypadkach, w których nazywasz je przy użyciu składni wywołania metody statycznej rozwiązuje niejednoznaczności.

Dyrektywa `static using` importuje również wszystkie typy zagnieżdżone. Można odwoływać się do wszystkich typów zagnieżdżonych bez kwalifikacji.

## <a name="null-conditional-operators"></a>Operatory warunkowe zerowe

*Operator warunkowy null* sprawia, że kontrole null znacznie łatwiejsze i płynne. Zastąp `.` `?.`dostęp do elementu członkowskiego na:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

W poprzednim przykładzie zmienna `first` jest `null` przypisywana, jeśli `null`obiekt person jest . W przeciwnym razie jest przypisywana `FirstName` wartość właściwości. Co najważniejsze, `?.` oznacza, że ten wiersz kodu `NullReferenceException` nie `person` generuje `null`jeśli zmienna jest . Zamiast tego, to zwarcia i zwraca `null`. Można również użyć null operator warunkowy dla dostępu do tablicy lub indeksatora. Zamień `[]` w `?[]` wyrażeniu indeksu.

Następujące wyrażenie zwraca `string`wartość , niezależnie `person`od wartości . Często używasz tej konstrukcji z operatorem *łączenia zerowego,* aby przypisać wartości domyślne, gdy jedną z właściwości jest `null`. Gdy wyrażenie zwarcia, `null` zwracana wartość jest wpisany, aby dopasować pełne wyrażenie.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Można również `?.` użyć do warunkowego wywołania metod. Najczęstszym zastosowaniem funkcji elementów członkowskich z operatorem warunkowym null jest `null`bezpiecznie wywołać delegatów (lub obsługi zdarzeń), które mogą być .  Zostanie wywołana metoda pełnomocnika `Invoke` przy `?.` użyciu operatora, aby uzyskać dostęp do elementu członkowskiego. Możesz zobaczyć przykład w artykule [wzorców delegata.](../delegates-patterns.md#handling-null-delegates)

Zasady `?.` operatora zapewniają, że lewa strona operatora jest oceniana tylko raz. Umożliwia wiele idiomów, w tym w poniższym przykładzie przy użyciu programów obsługi zdarzeń:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zapewnienie, że lewa strona jest oceniana tylko raz, umożliwia również użycie dowolnego wyrażenia, w tym wywołania metody, po lewej stronie`?.`

## <a name="string-interpolation"></a>Interpolacja ciągów

W przypadku języka C# 6 nowa funkcja [interpolacji ciągów](../language-reference/tokens/interpolated.md) umożliwia osadzanie wyrażeń w ciągu. Po prostu poprzedzaj ciąg z `$`i użyj wyrażeń między `{` i `}` zamiast ordinals:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

W tym przykładzie użyto właściwości wyrażenia podstawione. Można użyć dowolnego wyrażenia. Na przykład można obliczyć średnią punktową ucznia jako część interpolacji:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Poprzedni wiersz kodu formatuje wartość `Grades.Average()` jako liczbę zmiennoprzecinkową z dwoma miejscami dziesiętnym.

Często może być konieczne sformatowanie ciągu produkowane przy użyciu określonej kultury. Należy użyć faktu, że obiekt wytwarzany przez interpolację <xref:System.FormattableString?displayProperty=nameWithType>ciągu może być niejawnie konwertowany na . Wystąpienie <xref:System.FormattableString> zawiera ciąg formatu złożonego i wyniki oceny wyrażeń przed konwersją ich na ciągi. Użyj <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody, aby określić kulturę podczas formatowania ciągu. Poniższy przykład tworzy ciąg przy użyciu kultury niemiecki (de-DE). (Domyślnie kultura niemiecka używa znaku ',' dla separatora dziesiętnego i znaku '.' jako separatora tysięcy).

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Aby rozpocząć z interpolacji ciągów, zobacz [Interpolacji ciąg ów w języku c#](../tutorials/exploration/interpolated-strings.yml) interaktywny samouczek, [String interpolacji](../language-reference/tokens/interpolated.md) artykułu i [interpolacji ciąg w języku C#tutorial.](../tutorials/string-interpolation.md)

## <a name="exception-filters"></a>Filtry wyjątków

*Filtry wyjątków* są klauzule, które określają, kiedy należy zastosować danego catch klauzuli. Jeśli wyrażenie używane dla filtru `true`wyjątków jest oceniane , catch klauzula wykonuje swoje normalne przetwarzanie na wyjątek. Jeśli wyrażenie ocenia `false`, a `catch` następnie klauzula jest pomijana. Jednym z nich jest badanie informacji o `catch` wyjątku, aby ustalić, czy klauzula może przetworzyć wyjątek:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>Wyrażenie `nameof`

[Nameof](../language-reference/operators/nameof.md) wyrażenie oblicza nazwę symbolu. Jest to świetny sposób, aby narzędzia działały zawsze, gdy potrzebujesz nazwy zmiennej, właściwości lub pola członkowskiego. Jednym z najczęstszych `nameof` zastosowań jest podanie nazwy symbolu, który spowodował wyjątek:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Inne zastosowanie dotyczy aplikacji opartych na `INotifyPropertyChanged` języku XAML, które implementują interfejs:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Czekaj w blokach Catch i Finally

C# 5 miał kilka ograniczeń `await` wokół, gdzie można umieścić wyrażenia. Z C# 6, można `await` `catch` teraz `finally` używać w lub wyrażeń. Jest to najczęściej używane w scenariuszach rejestrowania:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Szczegóły implementacji `await` do `catch` dodawania obsługi wewnątrz i `finally` klauzule upewnij się, że zachowanie jest zgodne z zachowaniem kodu synchronicznego. Gdy kod wykonywany w lub `catch` `finally` zgłasza klauzuli, wykonanie szuka odpowiedniej `catch` klauzuli w następnym otaczającym bloku. Jeśli istnieje bieżący wyjątek, ten wyjątek zostanie utracony. To samo dzieje się z `catch` `finally` oczekiwanych wyrażeń i klauzule: odpowiedni `catch` jest wyszukiwany, a bieżący wyjątek, jeśli istnieje, zostanie utracony.  

> [!NOTE]
> To zachowanie jest powodem, dla `catch` którego `finally` zaleca się dokładne pisanie i klauzule, aby uniknąć wprowadzania nowych wyjątków.

## <a name="initialize-associative-collections-using-indexers"></a>Inicjuj kolekcje asocjacyjne przy użyciu indeksatorów

*Inicjatory indeksu* jest jedną z dwóch funkcji, które sprawiają, że inicjatory kolekcji bardziej spójne z użycia indeksu. We wcześniejszych wersjach języka C#, można użyć *inicjatorów kolekcji kolekcji* sekwencji styl, w tym <xref:System.Collections.Generic.Dictionary%602>, dodając nawiasy klamrowe wokół par kluczy i wartości:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Można ich używać <xref:System.Collections.Generic.Dictionary%602> z kolekcjami i `Add` innymi typami, w których metoda dostępna akceptuje więcej niż jeden argument. Nowa składnia obsługuje przypisanie przy użyciu indeksu do kolekcji:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Ta funkcja oznacza, że kontenery zestojowego mogą być inicjowane przy użyciu składni podobne ja w miejscu dla kontenerów sekwencji dla kilku wersji.

## <a name="extension-add-methods-in-collection-initializers"></a>Metody `Add` rozszerzenia w inicjatorach kolekcji

Inną funkcją, która ułatwia inicjowanie kolekcji jest możliwość `Add` użycia metody *rozszerzenia* dla metody. Ta funkcja została dodana dla parzystości z języka Visual Basic. Ta funkcja jest najbardziej przydatna, gdy masz niestandardową klasę kolekcji, która ma metodę o innej nazwie niż semantycznie dodawać nowe elementy.

## <a name="improved-overload-resolution"></a>Ulepszona rozdzielczość przeciążenia

Ta ostatnia funkcja to ta, której prawdopodobnie nie zauważysz. Istnieją konstrukcje, gdzie poprzednia wersja kompilatora C# może znaleźć niektóre wywołania metody obejmujące wyrażenia lambda niejednoznaczne. Należy wziąć pod uwagę tę metodę:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

We wcześniejszych wersjach języka C#wywołanie tej metody przy użyciu składni grupy metod zakończy się niepowodzeniem:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Wcześniejszy kompilator nie mógł poprawnie `Task.Run(Action)` `Task.Run(Func<Task>())`rozróżnić między i . W poprzednich wersjach należy użyć wyrażenia lambda jako argumentu:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Kompilator C# 6 poprawnie `Task.Run(Func<Task>())` określa, że jest lepszym wyborem.

### <a name="deterministic-compiler-output"></a>Deterministyczne dane wyjściowe kompilatora

Opcja `-deterministic` instruuje kompilator do tworzenia bajtów dla bajtów identyczny zestaw wyjściowy dla kolejnych kompilacji tych samych plików źródłowych.

Domyślnie każda kompilacja tworzy unikatowe dane wyjściowe na każdej kompilacji. Kompilator dodaje sygnaturę czasową i identyfikator GUID wygenerowany na podstawie liczb losowych. Ta opcja jest używana, jeśli chcesz porównać dane wyjściowe bajtów dla bajtów, aby zapewnić spójność między kompilacjami.

Aby uzyskać więcej informacji, zobacz [-deterministic kompilator a opcja](../language-reference/compiler-options/deterministic-compiler-option.md) artykułu.
