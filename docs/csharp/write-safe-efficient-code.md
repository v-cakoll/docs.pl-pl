---
title: Napisz bezpieczny i wydajny kod Języka C#
description: Najnowsze ulepszenia języka C# umożliwiają napisanie weryfikowalnego bezpiecznego kodu, który wcześniej skojarzony z niebezpiecznym kodem został skojarzony z niebezpiecznym kodem.
ms.date: 10/23/2018
ms.technology: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: d4a7916b80e15c7f00fa0a7da213ed0593e0959d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239979"
---
# <a name="write-safe-and-efficient-c-code"></a>Napisz bezpieczny i wydajny kod Języka C#

Nowe funkcje w języku C# umożliwiają pisanie weryfikowalnego bezpiecznego kodu z lepszą wydajnością. Jeśli starannie zastosować te techniki, mniej scenariuszy wymagają niebezpiecznego kodu. Te funkcje ułatwiają używanie odwołań do typów wartości jako argumentów metody i zwracanych metod. Po wykonaniu bezpiecznie, techniki te zminimalizować kopiowanie typów wartości. Za pomocą typów wartości, można zminimalizować liczbę alokacji i przebiegów wyrzucania elementów bezużytecznych.

Wiele z przykładowego kodu w tym artykule używa funkcji dodanych w języku C# 7.2. Aby korzystać z tych funkcji, należy skonfigurować projekt do używania języka C# 7.2 lub nowszego. Aby uzyskać więcej informacji na temat ustawiania wersji językowej, zobacz [konfigurowanie wersji językowej](language-reference/configure-language-version.md).

W tym artykule skupiono się na technikach efektywnego zarządzania zasobami. Jedną z zalet przy użyciu typów wartości jest to, że często unikają alokacji sterty. Wadą jest to, że są one kopiowane według wartości. Ten kompromis utrudnia optymalizację algorytmów, które działają na dużych ilościach danych. Nowe funkcje języka w języku C# 7.2 zapewniają mechanizmy, które umożliwiają bezpieczne efektywne kodu przy użyciu odwołań do typów wartości. Użyj tych funkcji mądrze, aby zminimalizować zarówno alokacji i operacji kopiowania. W tym artykule omówiono te nowe funkcje.

W tym artykule skupiono się na następujących technikach zarządzania zasobami:

- Zadeklarować, [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) aby wyrazić, że typ jest **niezmienny** i [`in`](language-reference/keywords/in-parameter-modifier.md) umożliwia kompilatorowi, aby zapisać kopie podczas korzystania z parametrów.
- Jeśli typ nie może być niezmienny, zadeklarować `struct` członków, `readonly` aby wskazać, że element członkowski nie modyfikuje stan.
- Użyj [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) return, gdy wartość `struct` zwracana <xref:System.IntPtr.Size?displayProperty=nameWithType> jest większa niż i okres istnienia magazynu jest większa niż metoda zwracana wartość.
- Gdy rozmiar a `readonly struct` jest <xref:System.IntPtr.Size?displayProperty=nameWithType>większy niż , należy `in` przekazać go jako parametr ze względu na wydajność.
- Nigdy nie `struct` przekazać jako parametr, `in` chyba `readonly` że jest zadeklarowany `readonly` za pomocą modyfikatora lub metoda wywołuje tylko członków struktury. Naruszenie tych wskazówek może negatywnie wpłynąć na wydajność i może prowadzić do niejasnego zachowania.
- Użyj [`ref struct`](language-reference/keywords/ref.md#ref-struct-types), lub `readonly ref struct` takich <xref:System.Span%601> <xref:System.ReadOnlySpan%601> lub do pracy z pamięcią jako sekwencji bajtów.

Techniki te zmuszają do zrównoważenia dwóch konkurencyjnych celów w odniesieniu do **odniesień** i **wartości.** Zmienne, które są [typami odwołań,](programming-guide/types/index.md#reference-types) mają odwołanie do lokalizacji w pamięci. Zmienne, które są [typami wartości](programming-guide/types/index.md#value-types) bezpośrednio zawierają ich wartość. Różnice te podkreślają kluczowe różnice, które są ważne dla zarządzania zasobami pamięci. **Typy wartości** są zazwyczaj kopiowane po przekazaniu do metody lub zwracane z metody. To zachowanie obejmuje kopiowanie `this` wartości podczas wywoływania członków typu wartości. Koszt kopii jest powiązany z rozmiarem typu. **Typy odwołań** są przydzielane na zarządzanym stosie. Każdy nowy obiekt wymaga nowej alokacji, a następnie muszą zostać odzyskane. Obie te operacje zajmują trochę czasu. Odwołanie jest kopiowane, gdy typ odwołania jest przekazywany jako argument do metody lub zwracany z metody.

W tym artykule użyto następującego przykładowego pojęcia struktury punktu 3D, aby wyjaśnić następujące zalecenia:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Różne przykłady używają różnych implementacji tej koncepcji.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Deklarowanie struktur tylko do odczytu dla typów wartości niezmienne

Deklarowanie `struct` przy `readonly` użyciu modyfikatora informuje kompilator, że zamiarem jest utworzenie typu niezmienne. Kompilator wymusza tę decyzję projektową z następującymi regułami:

- Wszyscy członkowie pola muszą być`readonly`
- Wszystkie właściwości muszą być tylko do odczytu, w tym właściwości implementowane automatycznie.

Te dwie zasady są wystarczające, aby `readonly struct` zapewnić, że żaden członek struktury nie modyfikuje stanu tej struktury. Jest `struct` niezmienny. Struktura `Point3D` może być zdefiniowana jako niezmienna struktura, jak pokazano w poniższym przykładzie:

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

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Deklarowanie tylko do odczytu członków, gdy struktura nie może być niezmienna

W języku C# 8.0 i nowszych, gdy typ struktury jest zmienny, `readonly`należy zadeklarować członków, które nie powodują mutacji . Na przykład, oto zmienna odmiana struktury punktów 3D:

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

W poprzednim przykładzie przedstawiono wiele lokalizacji, w `readonly` których można zastosować modyfikator: metody, właściwości i akcesory właściwości. Jeśli używasz właściwości autoimplementowane, kompilator `readonly` dodaje modyfikator do akcesora `get` dla właściwości odczytu i zapisu. Kompilator `readonly` dodaje modyfikator do deklaracji właściwości zaimplementowane `get` automatycznie dla właściwości tylko z akcesorem.

Dodanie `readonly` modyfikatora do elementów członkowskich, które nie mutują stanu zapewnia dwie powiązane korzyści. Po pierwsze kompilator wymusza intencji. Ten element członkowski nie może mutować stanu struktury ani uzyskiwać dostępu `readonly`do elementu członkowskiego, który nie jest również oznaczony. Po drugie kompilator nie utworzy `in` defensywnych kopii `readonly` parametrów podczas uzyskiwania dostępu do elementu członkowskiego. Kompilator może bezpiecznie dokonać tej `struct` optymalizacji, ponieważ `readonly` gwarantuje, że nie jest modyfikowany przez element członkowski.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>W `ref readonly return` miarę możliwości używaj instrukcji dla dużych konstrukcji

Wartości można zwrócić przez odwołanie, gdy zwracana wartość nie jest lokalna dla metody zwracanej. Zwracanie przez odwołanie oznacza, że kopiowane jest tylko odwołanie, a nie struktura. W poniższym przykładzie `Origin` właściwość nie można `ref` użyć return, ponieważ zwracana wartość jest zmienna lokalna:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Jednak następująca definicja właściwości mogą być zwracane przez odwołanie, ponieważ zwracana wartość jest statyczny element członkowski:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Nie chcesz, aby obiekty wywołujące modyfikujące pochodzenie, `ref readonly`więc należy zwrócić wartość przez:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Zwracanie `ref readonly` umożliwia zapisywanie kopiowania większych struktur i zachowanie niezmienności wewnętrznych elementów członkowskich danych.

W witrynie wywołania obiekty wywołujące dokonać `Origin` wyboru, `ref readonly` aby użyć właściwości jako lub jako wartość:

[!code-csharp[AssignRefReadonly](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Pierwsze przypisanie w poprzednim kodzie tworzy `Origin` kopię stałej i przypisuje tę kopię. Drugi przypisuje odwołanie. Należy zauważyć, że `readonly` modyfikator musi być częścią deklaracji zmiennej. Nie można modyfikować odwołania, do którego się odnosi. Próby w ten sposób spowodować błąd w czasie kompilacji.

Modyfikator `readonly` jest wymagany w `originReference`deklaracji .

Kompilator wymusza, że obiekt wywołujący nie można zmodyfikować odwołanie. Próbuje przypisać wartość bezpośrednio wygenerować błąd czasu kompilacji. Jednak kompilator nie może wiedzieć, czy każda metoda elementu członkowskiego modyfikuje stan struktury.
Aby upewnić się, że obiekt nie jest modyfikowany, kompilator tworzy kopię i wywołuje odwołania do elementów członkowskich przy użyciu tej kopii. Wszelkie modyfikacje są do tej kopii obronnej.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Stosowanie `in` modyfikatora do `readonly struct` parametrów większych niż`System.IntPtr.Size`

Słowo `in` kluczowe uzupełnia `ref` istniejące `out` i słowa kluczowe, aby przekazać argumenty przez odwołanie. Słowo `in` kluczowe określa przekazywanie argumentu przez odwołanie, ale wywoływana metoda nie modyfikuje wartości.

Dodatek ten zapewnia pełne słownictwo, aby wyrazić swój zamiar projektu.
Typy wartości są kopiowane po przekazaniu do metody wywoływanej, gdy nie określisz żadnego z następujących modyfikatorów w podpisie metody. Każdy z tych modyfikatorów określa, że zmienna jest przekazywana przez odwołanie, unikając kopii. Każdy modyfikator wyraża inną intencję:

- `out`: Ta metoda ustawia wartość argumentu używanego jako ten parametr.
- `ref`: Ta metoda może ustawić wartość argumentu używanego jako ten parametr.
- `in`: Ta metoda nie modyfikuje wartości argumentu używanego jako ten parametr.

Dodaj `in` modyfikator przekazać argument przez odwołanie i zadeklarować zamiar projektu do przekazywania argumentów przez odwołanie, aby uniknąć niepotrzebnego kopiowania. Nie zamierzasz modyfikować obiektu używanego jako ten argument.

Ta praktyka często zwiększa wydajność dla typów wartości <xref:System.IntPtr.Size?displayProperty=nameWithType>tylko do odczytu, które są większe niż . W przypadku`sbyte`typów `byte` `short`prostych `ushort` `int`( `uint` `long`, `ulong` `char`, `float` `double`, `decimal` `bool`, `enum` , , , i , i typów), wszelkie potencjalne zyski są minimalne. W rzeczywistości wydajność może ulec pogorszeniu przy użyciu pass-by-odwołania dla typów mniejszych niż <xref:System.IntPtr.Size?displayProperty=nameWithType>.

Poniższy kod przedstawia przykład metody, która oblicza odległość między dwoma punktami w przestrzeni 3D.

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Argumenty są dwie struktury, które każda zawiera trzy podwaja. Podwójne jest 8 bajtów, więc każdy argument jest 24 bajtów. Określając `in` modyfikator, należy przekazać odwołanie 4 bajtów lub 8-bajtowych do tych argumentów, w zależności od architektury komputera. Różnica w rozmiarze jest mała, ale sumuje się, gdy aplikacja wywołuje tę metodę w ścisłej pętli przy użyciu wielu różnych wartości.

Modyfikator `in` `out` uzupełnia `ref` i w inny sposób, jak również. Nie można utworzyć przeciążenia metody, które różnią `in`się `out`tylko `ref`obecnością , lub . Te nowe reguły rozszerzają to samo zachowanie, które zawsze były zdefiniowane dla `out` i `ref` parametry. Podobnie `out` jak `ref` modyfikatory, typy wartości nie `in` są zapakowane, ponieważ modyfikator jest stosowany.

Modyfikator `in` może być stosowany do dowolnego elementu członkowskiego, który przyjmuje parametry: metody, delegatów, lambdas, funkcje lokalne, indeksatory, operatory.

Inną cechą `in` parametrów jest to, że można użyć wartości `in` literału lub stałych dla argumentu do parametru. Ponadto, w `ref` `out` przeciwieństwie do lub parametru, `in` nie trzeba stosować modyfikator w witrynie wywołania. Poniższy kod przedstawia dwa przykłady wywoływania `CalculateDistance` metody. Pierwszy używa dwóch zmiennych lokalnych przekazywanych przez odwołanie. Drugi zawiera zmienną tymczasową utworzoną w ramach wywołania metody.

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Istnieje kilka sposobów, w których kompilator wymusza `in` charakter tylko do odczytu argumentu.  Przede wszystkim wywoływana metoda nie może bezpośrednio `in` przypisać do parametru. Nie można bezpośrednio przypisać do żadnego `in` pola parametru, `struct` gdy ta wartość jest typem. Ponadto nie można przekazać `in` parametr do dowolnej `ref` metody `out` za pomocą lub modyfikatora.
Reguły te mają zastosowanie `in` do dowolnego pola parametru, pod warunkiem, że pole jest typem, `struct` a parametr jest również typem. `struct` W rzeczywistości reguły te mają zastosowanie do wielu warstw dostępu do elementów `structs`członkowskich, pod warunkiem, że typy na wszystkich poziomach dostępu do elementów członkowskich są .
Kompilator wymusza, `struct` że `in` typy `struct` przekazywane jako argumenty i ich elementy członkowskie są zmienne tylko do odczytu, gdy są używane jako argumenty do innych metod.

Zastosowanie `in` parametrów może uniknąć potencjalnych kosztów wydajności tworzenia kopii. Nie zmienia semantyki żadnego wywołania metody. W związku z tym nie `in` trzeba określić modyfikatora w witrynie wywołania. Pominięcie `in` modyfikatora w witrynie wywołania informuje kompilator, że jest dozwolone, aby kopię argumentu z następujących powodów:

- Istnieje niejawna konwersja, ale nie konwersja tożsamości z typu argumentu do typu parametru.
- Argument jest wyrażeniem, ale nie ma znanej zmiennej magazynu.
- Istnieje przeciążenie, które różni się `in`obecnością lub brakiem . W takim przypadku przeciążenie według wartości jest lepsze dopasowanie.

Reguły te są przydatne podczas aktualizowania istniejącego kodu do używania argumentów odwołania tylko do odczytu. Wewnątrz metody o nazwie, można wywołać dowolną metodę wystąpienia, która używa przez parametry wartości. W takich przypadkach tworzona jest `in` kopia parametru. Ponieważ kompilator może utworzyć `in` zmienną tymczasową dla dowolnego `in` parametru, można również określić wartości domyślne dla dowolnego parametru. Poniższy kod określa początek (punkt 0,0) jako wartość domyślną dla drugiego punktu:

[!code-csharp[InArgumentDefault](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Aby wymusić kompilator do przekazywania argumentów `in` tylko do odczytu przez odwołanie, należy określić modyfikator na argumenty w witrynie wywołania, jak pokazano w następującym kodzie:

[!code-csharp[UseInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

To zachowanie ułatwia przyjmowanie `in` parametrów w czasie w dużych bazach kodu, gdzie możliwe są przyrosty wydajności. Najpierw dodaj `in` modyfikator do podpisów metody. Następnie można dodać `in` modyfikator w `readonly struct` witrynach wywołań i tworzyć typy, `in` aby włączyć kompilator, aby uniknąć tworzenia kopii obronnych parametrów w większej liczbie lokalizacji.

Oznaczenia `in` parametru mogą być również używane z typami odwołań lub wartościami liczbowymi. Jednak korzyści w obu przypadkach są minimalne, jeśli w ogóle.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>Nigdy nie używaj zmiennych `in` struktur jak w argumencie

Techniki opisane powyżej wyjaśniają, jak uniknąć kopii, zwracając odwołania i przekazując wartości przez odwołanie. Techniki te działają najlepiej, gdy `readonly struct` typy argumentów są zadeklarowane jako typy. W przeciwnym razie kompilator musi utworzyć **kopie obronne** w wielu sytuacjach, aby wymusić readonly-ness wszelkich argumentów. Rozważmy następujący przykład, który oblicza odległość punktu 3D od początku układu współrzędnych:

[!code-csharp[InArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Struktura `Point3D` *nie* jest strukturą tylko do odczytu. Istnieje sześć różnych wywołań dostępu do właściwości w treści tej metody. Przy pierwszym badaniu, być może myślałeś, że te dostępy były bezpieczne. Po tym `get` wszystkim akcesor nie należy modyfikować stan obiektu. Ale nie ma reguły języka, która by to wymuszała. To tylko wspólna konwencja. Każdy typ może `get` zaimplementować akcesor, który zmodyfikował stan wewnętrzny. Bez gwarancji języka kompilator musi utworzyć tymczasową kopię argumentu przed wywołaniem dowolnego elementu członkowskiego. Magazyn tymczasowy jest tworzony na stosie, wartości argumentu są kopiowane do magazynu tymczasowego, a `this` wartość jest kopiowana do stosu dla każdego dostępu do elementu członkowskiego jako argument. W wielu sytuacjach te kopie szkody wydajności wystarczy, że pass-by-value jest szybszy niż pass-by-readonly-odwołania, gdy typ argumentu `readonly struct`nie jest .

Zamiast tego, jeśli obliczenia odległości używa niezmienne struktury, `ReadonlyPoint3D`, obiekty tymczasowe nie są potrzebne:

[!code-csharp[readonlyInArgument](../../samples/snippets/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Kompilator generuje bardziej wydajny kod podczas `readonly struct`wywoływania elementów członkowskich: Odwołanie, `this` zamiast kopii `in` odbiornika, jest zawsze parametr emanowany przez odwołanie do metody członkowskiej. Ta optymalizacja zapisuje kopiowanie `readonly struct` podczas `in` używania jako argumentu.

Nie należy przekazywać typu wartości `in` nulljako argument. Typ <xref:System.Nullable%601> nie jest zadeklarowany jako struktura tylko do odczytu. Oznacza to, że kompilator musi wygenerować kopie obronne dla `in` dowolnego argumentu typu wartości nullable przekazany do metody przy użyciu modyfikatora w deklaracji parametru.

Możesz zobaczyć przykładowy program, który demonstruje różnice w wydajności przy użyciu [BenchmarkDotNet](https://www.nuget.org/packages/BenchmarkDotNet/) w naszym [repozytorium przykładów w usg.](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) Porównuje przekazywanie zmiennej struktury według wartości i przez odwołanie z przekazywaniem niezmiennej struktury przez wartość i przez odwołanie. Użycie niezmiennej struktury i przebiegu przez odwołanie jest najszybsze.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Używanie `ref struct` typów do pracy z blokami lub pamięcią na pojedynczej klatce stosu

Funkcja języka pokrewnego jest możliwość deklarowania typu wartości, który musi być ograniczony do pojedynczej ramki stosu. To ograniczenie umożliwia kompilatorowi, aby kilka optymalizacji. Główną motywacją dla <xref:System.Span%601> tej funkcji były i powiązane struktury. Uchylisz ulepszenia wydajności wynikające z tych ulepszeń przy użyciu nowych <xref:System.Span%601> i zaktualizowanych interfejsów API .NET, które korzystają z tego typu.

Mogą wystąpić podobne wymagania dotyczące pracy [`stackalloc`](language-reference/operators/stackalloc.md) z pamięcią utworzoną przy użyciu lub podczas korzystania z pamięci z interfejsów API międzysystemowych. Można zdefiniować własne `ref struct` typy dla tych potrzeb.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct`Typu

Deklarowanie struktury jako `readonly ref` łączy w sobie `ref struct` korzyści `readonly struct` i ograniczenia i deklaracje. Pamięć używana przez zakres tylko do odczytu jest ograniczona do pojedynczej ramki stosu, a pamięć używana przez zakres tylko do odczytu nie może być modyfikowana.

## <a name="conclusions"></a>Wnioski

Użycie typów wartości minimalizuje liczbę operacji alokacji:

- Magazyn dla typów wartości jest stos przydzielone dla zmiennych lokalnych i argumentów metody.
- Magazyn dla typów wartości, które są członkami innych obiektów jest przydzielany jako część tego obiektu, a nie jako oddzielna alokacja.
- Magazyn dla wartości zwracanych typu wartości jest przydzielany przez stos.

Kontrast, że z typami odwołań w tych samych sytuacjach:

- Magazyn dla typów odwołań są sterty przydzielone dla zmiennych lokalnych i argumentów metody. Odwołanie jest przechowywane na stosie.
- Magazyn dla typów odwołań, które są członkami innych obiektów są oddzielnie przydzielane na stercie. Obiekt zawierający przechowuje odwołanie.
- Magazyn dla wartości zwracanych typu odwołania jest przydzielany sterty. Odwołanie do tego magazynu jest przechowywany na stosie.

Minimalizacja przydziałów wiąże się z kompromisami. Skopiuj więcej pamięci, gdy rozmiar `struct` jest większy niż rozmiar odwołania. Odwołanie jest zazwyczaj 64 bitów lub 32 bitów i zależy od procesora CPU komputera docelowego.

Te kompromisy mają na ogół minimalny wpływ na wydajność. Jednak w przypadku dużych struktur lub większych kolekcji zwiększa się wpływ na wydajność. Wpływ może być duży w ciasnych pętlach i gorących ścieżkach dla programów.

Te ulepszenia języka C# są przeznaczone do algorytmów o krytycznym znaczeniu dla wydajności, gdzie minimalizowanie alokacji pamięci jest głównym czynnikiem w osiąganiu niezbędnej wydajności. Może się okazać, że często nie używasz tych funkcji w kodzie, który piszesz. Jednak te ulepszenia zostały przyjęte w całej .NET. Ponieważ coraz więcej interfejsów API korzysta z tych funkcji, zobaczysz poprawę wydajności aplikacji.

## <a name="see-also"></a>Zobacz też

- [ref — słowo kluczowe](language-reference/keywords/ref.md)
- [Wartości zwracane ref i zmienne lokalne ref](programming-guide/classes-and-structs/ref-returns.md)
