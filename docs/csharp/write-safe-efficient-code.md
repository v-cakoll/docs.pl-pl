---
title: Pisanie bezpiecznego i wydajnego kodu C#
description: Ostatnie ulepszenia języka C# umożliwiają pisanie weryfikowalny kod bezpieczny, który wydajność wcześniej skojarzone z niebezpiecznym kodem.
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 365320fef5a2f9cd123086c1baed9a786ede9f05
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345078"
---
# <a name="write-safe-and-efficient-c-code"></a>Pisanie bezpiecznego i wydajnego kodu C#

Nowe funkcje w języku C# umożliwiają pisanie weryfikowalny bezpieczny kod z lepszą wydajność. Jeśli starannie zastosujesz te techniki, mniej scenariuszy wymaga niebezpiecznego kodu. Te funkcje ułatwiają używanie odwołań do typów wartości jako argumentów metody i zwracanych metod. Po wykonaniu bezpiecznie, techniki te zminimalizować kopiowanie typów wartości. Za pomocą typów wartości, można zminimalizować liczbę alokacji i wyrzucania elementów bezużytecznych przechodzi.

Wiele przykładowego kodu w tym artykule używa funkcji dodanych w języku C# 7.2. Aby korzystać z tych funkcji, należy skonfigurować projekt do używania języka C# 7.2 lub nowszego. Aby uzyskać więcej informacji na temat ustawiania wersji [językowej, zobacz konfigurowanie wersji językowej](language-reference/configure-language-version.md).

W tym artykule skupiono się na technikach efektywnego zarządzania zasobami. Jedną z zalet przy użyciu typów wartości jest to, że często unikają alokacji sterty. Wadą jest to, że są one kopiowane przez wartość. Ten kompromis utrudnia optymalizację algorytmów, które działają na dużych ilościach danych. Nowe funkcje języka w języku C# 7.2 zapewniają mechanizmy, które umożliwiają bezpieczne wydajny kod przy użyciu odwołań do typów wartości. Użyj tych funkcji mądrze, aby zminimalizować zarówno alokacji i operacji kopiowania. W tym artykule omówiono te nowe funkcje.

W tym artykule skupiono się na następujących technikach zarządzania zasobami:

- Zadeklaruj a [`readonly struct`](language-reference/builtin-types/struct.md#readonly-struct) wyrazić, że typ jest **niezmienny**. Dzięki temu kompilator może zapisywać [`in`](language-reference/keywords/in-parameter-modifier.md) kopie obronne podczas korzystania z parametrów.
- Jeśli typ nie może być niezmienne, zadeklarować `struct` członków, `readonly` aby wskazać, że element członkowski nie modyfikuje stanu.
- Użyj [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) zwracanego, gdy zwracana wartość jest `struct` większa niż <xref:System.IntPtr.Size?displayProperty=nameWithType> i okres istnienia magazynu jest większy niż metoda zwracająca wartość.
- Gdy rozmiar a `readonly struct` jest <xref:System.IntPtr.Size?displayProperty=nameWithType>większy niż , należy `in` przekazać go jako parametr ze względu na wydajność.
- Nigdy nie `struct` przekazuje `in` jako parametr, chyba `readonly` że jest zadeklarowany `readonly` za pomocą modyfikatora lub metoda wywołuje tylko członków struktury. Naruszenie tych wskazówek może negatywnie wpłynąć na wydajność i może prowadzić do niejasnego zachowania.
- Użyj [`ref struct`](language-reference/keywords/ref.md#ref-struct-types), lub `readonly ref struct` takiego <xref:System.Span%601> <xref:System.ReadOnlySpan%601> typu lub do pracy z pamięcią jako sekwencji bajtów.

Techniki te zmuszają do zrównoważenia dwóch konkurencyjnych celów w odniesieniu do **odniesień** i **wartości.** Zmienne, które są [typami odwołań,](programming-guide/types/index.md#reference-types) przechowują odwołanie do lokalizacji w pamięci. Zmienne, które są [typami wartości](programming-guide/types/index.md#value-types) bezpośrednio zawierają ich wartość. Różnice te podkreślają kluczowe różnice, które są ważne dla zarządzania zasobami pamięci. **Typy wartości** są zazwyczaj kopiowane po przekazaniu do metody lub zwrócone z metody. To zachowanie obejmuje kopiowanie `this` wartości podczas wywoływania elementów członkowskich typu wartości. Koszt kopii jest powiązany z rozmiarem typu. **Typy odwołań** są przydzielane na zarządzanym stosie. Każdy nowy obiekt wymaga nowej alokacji, a następnie musi zostać odzyskany. Obie te operacje zająć trochę czasu. Odwołanie jest kopiowane, gdy typ odwołania jest przekazywany jako argument do metody lub zwracany z metody.

W tym artykule użyto następującego przykładowego pojęcia struktury 3D-point, aby wyjaśnić te zalecenia:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Różne przykłady używają różnych implementacji tej koncepcji.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Deklarowanie struktur tylko do odczytu dla niezmiennych typów wartości

Deklarowanie `struct` przy `readonly` użyciu modyfikatora informuje kompilator, że intencją jest utworzenie typu niezmienne. Kompilator wymusza tę decyzję o projekcie z następującymi regułami:

- Wszyscy członkowie terenu muszą być`readonly`
- Wszystkie właściwości muszą być tylko do odczytu, w tym właściwości automatycznie zaimplementowane.

Te dwie reguły są wystarczające, `readonly struct` aby upewnić się, że żaden członek zmienia stan tej struktury. Jest `struct` niezmienny. Struktura `Point3D` może być zdefiniowana jako niezmienna struktura, jak pokazano w poniższym przykładzie:

```csharp
readonly public struct ReadonlyPoint3D
{
    public ReadonlyPoint3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    public double X { get; }
    public double Y { get; }
    public double Z { get; }
}
```

Postępuj zgodnie z tym zaleceniem, gdy intencją projektu jest utworzenie niezmiennego typu wartości. Wszelkie ulepszenia wydajności są dodatkową korzyścią. Wyraźnie `readonly struct` wyraża swój zamiar projektu.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Deklarowanie tylko do odczytu członków, gdy nie można niezmiennie być niezmienną strukturą

W języku C# 8.0 i nowszych, gdy typ struktury jest modyfikowalna, należy zadeklarować członków, które nie powodują `readonly`mutacji. Należy wziąć pod uwagę inną aplikację, która wymaga struktury punktów 3D, ale musi obsługiwać zmienność. Następująca wersja struktury punktów 3D `readonly` dodaje modyfikator tylko do tych elementów członkowskich, które nie modyfikują struktury. Postępuj zgodnie z tym przykładem, gdy projekt musi obsługiwać modyfikacje struktury przez niektórych członków, ale nadal chcesz korzyści z wymuszania tylko na niektórych elementach członkowskich:

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        _x = x;
        _y = y;
        _z = z;
    }

    private double _x;
    public double X
    {
        readonly get => _x;
        set => _x = value;
    }

    private double _y;
    public double Y
    {
        readonly get => _y;
        set => _y = value;
    }

    private double _z;
    public double Z
    {
        readonly get => _z;
        set => _z = value;
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X}, {Y}, {Z}";
}
```

W poprzednim przykładzie przedstawiono wiele lokalizacji, `readonly` w których można zastosować modyfikator: metody, właściwości i akcesory właściwości. Jeśli używasz właściwości automatycznie implementowane, kompilator dodaje `readonly` `get` modyfikator do akcesora dla właściwości odczytu i zapisu. Kompilator dodaje `readonly` modyfikator do automatycznie implementowanych deklaracji właściwości dla `get` właściwości tylko akcesor.

Dodanie `readonly` modyfikatora do elementów członkowskich, które nie mutują stanu zapewnia dwie powiązane korzyści. Po pierwsze kompilator wymusza intencji. Ten element członkowski nie może mutować stanu struktury ani nie może uzyskać `readonly`dostępu do elementu członkowskiego, który nie jest również oznaczony. Po drugie kompilator nie utworzy `in` kopii obronnych `readonly` parametrów podczas uzyskiwania dostępu do elementu członkowskiego. Kompilator można dokonać tej optymalizacji bezpiecznie, ponieważ gwarantuje, że nie `struct` jest modyfikowany przez element członkowski. `readonly`

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Jeśli `ref readonly return` to możliwe, używaj instrukcji dla dużych struktur

Wartości można zwracać przez odwołanie, gdy zwracana wartość nie jest lokalna dla metody zwracającej. Zwracanie przez odwołanie oznacza, że kopiowane jest tylko odwołanie, a nie struktura. W poniższym przykładzie `Origin` właściwość nie `ref` może użyć zwrotu, ponieważ zwracana wartość jest zmienną lokalną:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Jednak następująca definicja właściwości mogą być zwracane przez odwołanie, ponieważ zwracana wartość jest elementem statycznym:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Nie chcesz, aby osoby wywołujące modyfikujące początek układu `ref readonly`współrzędnych, więc należy zwrócić wartość przez:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Powrót `ref readonly` umożliwia zapisanie kopiowania większych struktur i zachowanie niezmienności wewnętrznych elementów członkowskich danych.

W miejscu wywołania dzwoniący dokonują `Origin` wyboru, `ref readonly` aby użyć właściwości jako lub jako wartości:

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Pierwsze przypisanie w poprzednim kodzie tworzy `Origin` kopię stałej i przypisuje tę kopię. Drugi przypisuje odwołanie. Należy zauważyć, że `readonly` modyfikator musi być częścią deklaracji zmiennej. Odwołanie, do którego się odnosi, nie może być modyfikowane. Próby w tym celu powodują błąd w czasie kompilacji.

Modyfikator `readonly` jest wymagany w `originReference`deklaracji .

Kompilator wymusza, że wywołujący nie można zmodyfikować odwołania. Próbuje przypisać wartość bezpośrednio wygenerować błąd w czasie kompilacji. Jednak kompilator nie może wiedzieć, czy dowolna metoda elementu członkowskiego modyfikuje stan struktury.
Aby upewnić się, że obiekt nie jest modyfikowany, kompilator tworzy kopię i wywołuje odwołania do elementów członkowskich przy użyciu tej kopii. Wszelkie modyfikacje są do tej kopii obronnej.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Zastosuj `in` modyfikator `readonly struct` do parametrów większych niż`System.IntPtr.Size`

Słowo `in` kluczowe uzupełnia `ref` `out` istniejące i słowa kluczowe, aby przekazać argumenty przez odwołanie. Słowo `in` kluczowe określa przekazywanie argumentu przez odwołanie, ale wywołana metoda nie modyfikuje wartości.

Ten dodatek zapewnia pełne słownictwo, aby wyrazić swoje intencje projektowe.
Typy wartości są kopiowane po przekazaniu do metody wywoływanej, gdy nie określisz żadnego z następujących modyfikatorów w podpisie metody. Każdy z tych modyfikatorów określa, że zmienna jest przekazywana przez odwołanie, unikając kopiowania. Każdy modyfikator wyraża inny zamiar:

- `out`: Ta metoda ustawia wartość argumentu używanego jako ten parametr.
- `ref`: Ta metoda może ustawić wartość argumentu użytego jako ten parametr.
- `in`: Ta metoda nie modyfikuje wartości argumentu użytego jako ten parametr.

Dodaj `in` modyfikator, aby przekazać argument przez odwołanie i zadeklarować zamiar projektu przekazać argumenty przez odwołanie, aby uniknąć niepotrzebnego kopiowania. Nie zamierzasz modyfikować obiektu używanego jako ten argument.

Praktyka ta często poprawia wydajność dla typów wartości <xref:System.IntPtr.Size?displayProperty=nameWithType>odczytu, które są większe niż . W przypadku`sbyte`typów `byte` `short`prostych `ushort` `int`( `uint` `long`, `ulong` `char`, `float` `double`, `decimal` `bool`, `enum` , , , , , , i , i , i typy), wszelkie potencjalne przyrosty wydajności są minimalne. W rzeczywistości wydajność może ulec pogorszeniu przy użyciu funkcji <xref:System.IntPtr.Size?displayProperty=nameWithType>pass-by-reference dla typów mniejszych niż .

Poniższy kod przedstawia przykład metody, która oblicza odległość między dwoma punktami w przestrzeni 3D.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Argumenty są dwie struktury, które zawierają trzy podwaja. Double jest 8 bajtów, więc każdy argument jest 24 bajtów. Określając `in` modyfikator, należy przekazać 4-bajtowe lub 8-bajtowe odwołanie do tych argumentów, w zależności od architektury maszyny. Różnica w rozmiarze jest mała, ale sumuje się, gdy aplikacja wywołuje tę metodę w wąskiej pętli przy użyciu wielu różnych wartości.

Modyfikator `in` `out` uzupełnia `ref` i w inny sposób, jak również. Nie można utworzyć przeciążenia metody, które różnią się `in` `out`tylko `ref`w obecności , lub . Te nowe reguły rozszerzają to `out` samo `ref` zachowanie, które zawsze było zdefiniowane dla i parametry. Podobnie `out` jak `ref` modyfikatory i typy wartości `in` nie są zapakowane, ponieważ modyfikator jest stosowany.

Modyfikator `in` może być stosowany do dowolnego elementu członkowskiego, który przyjmuje parametry: metody, delegatów, lambdas, funkcje lokalne, indeksatory, operatory.

Inną cechą parametrów `in` jest użycie wartości literału lub `in` stałych dla argumentu do parametru. Ponadto, w `ref` `out` przeciwieństwie do lub parametru, `in` nie trzeba stosować modyfikator w witrynie wywołania. Poniższy kod pokazuje dwa przykłady `CalculateDistance` wywoływania metody. Pierwszy używa dwóch zmiennych lokalnych przekazanych przez odwołanie. Drugi zawiera zmienną tymczasową utworzoną jako część wywołania metody.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Istnieje kilka sposobów, w którym kompilator wymusza `in` charakter tylko do odczytu argumentu.  Przede wszystkim wywołana metoda nie może bezpośrednio `in` przypisać do parametru. Nie można bezpośrednio przypisać do żadnego `in` pola parametru, `struct` gdy ta wartość jest typem. Ponadto nie można przekazać parametr `in` do żadnej metody `ref` `out` przy użyciu lub modyfikatora.
Reguły te mają zastosowanie `in` do dowolnego pola `struct` parametru, pod warunkiem, że pole jest typem, a parametr jest również typem. `struct` W rzeczywistości te reguły mają zastosowanie do wielu warstw dostępu do `structs`elementów członkowskich, pod warunkiem, że typy na wszystkich poziomach dostępu do elementów członkowskich są .
Kompilator wymusza, `struct` `in` że typy przekazywane jako argumenty i ich `struct` elementy członkowskie są zmienne tylko do odczytu, gdy są używane jako argumenty do innych metod.

Zastosowanie parametrów `in` może uniknąć potencjalnych kosztów wydajności tworzenia kopii. Nie zmienia semantyki żadnych wywołań metody. W związku z tym nie trzeba `in` określać modyfikator w witrynie wywołania. Pominięcie modyfikatora `in` w witrynie wywołania informuje kompilator, że jest dozwolone, aby wykonać kopię argumentu z następujących powodów:

- Istnieje konwersja niejawna, ale nie konwersja tożsamości z typu argumentu do typu parametru.
- Argument jest wyrażeniem, ale nie ma znanej zmiennej magazynu.
- Istnieje przeciążenie, które różni się obecnością lub brakiem `in`pliku . W takim przypadku przeciążenie według wartości jest lepsze dopasowanie.

Te reguły są przydatne podczas aktualizowania istniejącego kodu w celu użycia argumentów odwołania tylko do odczytu. Wewnątrz metody wywoływane można wywołać dowolną metodę wystąpienia, która używa przez parametry wartości. W tych przypadkach tworzona `in` jest kopia parametru. Ponieważ kompilator może utworzyć zmienną tymczasową dla dowolnego `in` parametru, można również określić wartości domyślne dla dowolnego `in` parametru. Poniższy kod określa początek (punkt 0,0) jako wartość domyślną dla drugiego punktu:

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Aby wymusić kompilator do przekazywania argumentów `in` tylko do odczytu przez odwołanie, należy określić modyfikator argumentów w witrynie wywołania, jak pokazano w poniższym kodzie:

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

To zachowanie ułatwia przyjęcie `in` parametrów w czasie w dużych baz kodu, gdzie wzrost wydajności są możliwe. Najpierw dodajesz `in` modyfikator do podpisów metod. Następnie można dodać `in` modyfikator w witrynach wywołań i utworzyć `readonly struct` typy, aby `in` włączyć kompilator, aby uniknąć tworzenia kopii obronnych parametrów w większej liczbie lokalizacji.

Oznaczenie `in` parametru może być również używane z typami odniesienia lub wartościami liczbowymi. Jednak korzyści w obu przypadkach są minimalne, jeśli w ogóle.

## <a name="avoid-mutable-structs-as-an-in-argument"></a>Unikaj modyfikowalnych struktur `in` jako argumentu

Techniki opisane powyżej wyjaśniają, jak uniknąć kopii, zwracając odwołania i przekazując wartości przez odniesienie. Te techniki działają najlepiej, gdy typy argumentów są zadeklarowane jako `readonly struct` typy. W przeciwnym razie kompilator musi utworzyć **kopie obronne** w wielu sytuacjach, aby wymusić readonly-ness żadnych argumentów. Rozważmy następujący przykład, który oblicza odległość punktu 3D od początku układu współrzędnych:

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Struktura `Point3D` *nie* jest tylko do odczytu struktury. Istnieje sześć różnych wywołań dostępu do właściwości w treści tej metody. Przy pierwszym badaniu, można było pomyśleć, że te dostępy były bezpieczne. Po tym `get` wszystkim akcesor nie należy modyfikować stan obiektu. Ale nie ma reguły językowej, która to wymusza. To tylko wspólna konwencja. Każdy typ można `get` zaimplementować akcesor, który zmodyfikował stan wewnętrzny. Bez gwarancji niektórych języków kompilator musi utworzyć tymczasową kopię argumentu `readonly` przed wywołaniem dowolnego elementu członkowskiego nie oznaczone modyfikatorem. Magazyn tymczasowy jest tworzony na stosie, wartości argumentu są kopiowane do magazynu tymczasowego, a wartość jest `this` kopiowana do stosu dla każdego elementu członkowskiego jako argument. W wielu sytuacjach te kopie szkodzą wydajności na tyle, że przekazywanie przez wartość jest szybsze niż `readonly struct` przekazywanie przez odczyt tylko odwołanie, gdy typ argumentu nie jest a, a metoda wywołuje członków, które nie są oznaczone. `readonly` Jeśli zaznaczysz wszystkie metody, które nie `readonly`modyfikują stanu struktury jako , kompilator może bezpiecznie określić, że stan struktury nie jest modyfikowany, a kopia obronna nie jest potrzebna.

Zamiast tego, jeśli obliczanie odległości używa niezmiennej `ReadonlyPoint3D`struktury, obiekty tymczasowe nie są potrzebne:

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Kompilator generuje bardziej wydajny kod podczas `readonly struct`wywoływania członków : Odwołanie, `this` zamiast kopii odbiornika, jest zawsze parametrem przekazywanym `in` przez odwołanie do metody elementu członkowskiego. Ta optymalizacja zapisuje kopiowanie, gdy używasz `readonly struct` jako argumentu. `in`

Nie należy przekazywać typu wartości nullable jako `in` argument. Typ <xref:System.Nullable%601> nie jest zadeklarowany jako struktura tylko do odczytu. Oznacza to, że kompilator musi generować kopie obronne dla dowolnego `in` nullable argument typu wartości przekazywane do metody przy użyciu modyfikatora w deklaracji parametru.

Możesz zobaczyć przykładowy program, który pokazuje różnice w wydajności przy użyciu [BenchmarkDotNet](https://www.nuget.org/packages/BenchmarkDotNet/) w naszym [repozytorium przykładów](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) w usłudze GitHub. Porównuje przekazywanie modyfikowalne struktury przez wartość i przez odwołanie z przekazywania niezmienne struktury przez wartość i przez odwołanie. Użycie niezmiennej struktury i przekazywania przez odwołanie jest najszybsze.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Używanie `ref struct` typów do pracy z blokami lub pamięcią na jednej ramce stosu

Powiązana funkcja języka jest możliwość deklarowania typu wartości, które muszą być ograniczone do pojedynczej ramki stosu. To ograniczenie umożliwia kompilatorowi dokonać kilku optymalizacji. Główną motywacją dla <xref:System.Span%601> tej funkcji były i powiązane struktury. Ulepszenia wydajności można uzyskać za pomocą nowych i zaktualizowanych interfejsów API platformy <xref:System.Span%601> .NET, które korzystają z tego typu.

Mogą mieć podobne wymagania pracy z [`stackalloc`](language-reference/operators/stackalloc.md) pamięcią utworzoną przy użyciu lub podczas korzystania z pamięci z interfejsów API międzyop. Można zdefiniować `ref struct` własne typy dla tych potrzeb.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct`Typu

Deklarowanie struktury jako `readonly ref` łączy korzyści i ograniczenia `ref struct` `readonly struct` i deklaracje. Pamięć używana przez readonly span jest ograniczona do jednej ramki stosu, a pamięć używana przez readonly span nie może być modyfikowana.

## <a name="conclusions"></a>Wnioski

Za pomocą typów wartości minimalizuje liczbę operacji alokacji:

- Magazyn dla typów wartości jest stos przydzielony dla zmiennych lokalnych i argumentów metody.
- Magazyn dla typów wartości, które są członkami innych obiektów jest przydzielany jako część tego obiektu, a nie jako oddzielna alokacja.
- Magazyn dla wartości zwracanej typu wartości jest przydzielany stos.

Kontrast, że z typami odwołań w tych samych sytuacjach:

- Magazyn dla typów odwołań są przydzielane sterty dla zmiennych lokalnych i argumentów metody. Odwołanie jest przechowywane na stosie.
- Magazyn dla typów odwołań, które są członkami innych obiektów są oddzielnie przydzielane na stosie. Obiekt zawierający przechowuje odwołanie.
- Magazyn dla wartości zwracanej typu referencyjnego jest przydzielany na stercie. Odwołanie do tego magazynu jest przechowywany na stosie.

Minimalizowanie alokacji wiąże się z kompromisami. Skopiuj więcej pamięci, gdy rozmiar `struct` jest większy niż rozmiar odwołania. Odwołanie jest zazwyczaj 64 bitów lub 32 bitów i zależy od procesora komputera docelowego.

Te kompromisy zazwyczaj mają minimalny wpływ na wydajność. Jednak w przypadku dużych struktur lub większych kolekcji zwiększa się wpływ na wydajność. Wpływ może być duży w ciasnych pętlach i gorących ścieżkach dla programów.

Te ulepszenia języka C# są przeznaczone do algorytmów o krytycznym znaczeniu dla wydajności, gdzie minimalizowanie alokacji pamięci jest głównym czynnikiem w osiągnięciu niezbędnej wydajności. Może się okazać, że często nie używasz tych funkcji w kodzie, który piszesz. Jednak te ulepszenia zostały przyjęte w całej .NET. Ponieważ coraz więcej interfejsów API korzysta z tych funkcji, zobaczysz, że wydajność aplikacji zostanie ulepszona.

## <a name="see-also"></a>Zobacz też

- [słowo kluczowe ref](language-reference/keywords/ref.md)
- [Wartości zwracane ref i zmienne lokalne ref](programming-guide/classes-and-structs/ref-returns.md)
