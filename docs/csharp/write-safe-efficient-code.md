---
title: Zapisz bezpieczny i wydajny C# kod
description: Najnowsze ulepszenia C# języka umożliwiają pisanie możliwego do zweryfikowania bezpiecznego kodu, który został wcześniej powiązany z niebezpiecznym kodem.
ms.date: 10/23/2018
ms.custom: mvc
ms.openlocfilehash: 89a0bcf28c3c398865082e120ca9c16fe2c00651
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960841"
---
# <a name="write-safe-and-efficient-c-code"></a>Zapisz bezpieczny i wydajny C# kod

Nowe funkcje w C# programie umożliwiają pisanie zweryfikowanego bezpiecznego kodu z lepszą wydajnością. W przypadku starannej zastosowania tych technik mniejsza liczba scenariuszy wymaga niebezpiecznego kodu. Te funkcje ułatwiają Używanie odwołań do typów wartości jako argumentów metod i zwracanych metod. W przypadku bezpiecznego wykonywania tych technik minimalizuje kopiowanie typów wartości. Za pomocą typów wartości można zminimalizować liczbę alokacji i przebiegów elementów bezużytecznych.

Większość przykładowego kodu w tym artykule używa funkcji dodanych w C# 7,2. Aby korzystać z tych funkcji, należy skonfigurować projekt do korzystania C# z 7,2 lub nowszego. Aby uzyskać więcej informacji na temat ustawiania wersji językowej, zobacz [Konfigurowanie wersji językowej](language-reference/configure-language-version.md).

Ten artykuł koncentruje się na technikach związanych z wydajnym zarządzaniem zasobami. Jedną z korzyści w korzystaniu z typów wartości jest to, że często unikają alokacji sterty. Wadą jest to, że są one kopiowane przez wartość. Ten kompromis utrudnia optymalizację algorytmów, które działają w przypadku dużych ilości danych. Nowe funkcje językowe w C# 7,2 zapewniają mechanizmy, które umożliwiają bezpieczny wydajny kod przy użyciu odwołań do typów wartości. Korzystaj z tych funkcji, aby zminimalizować jednocześnie alokacje i operacje kopiowania. Ten artykuł zawiera informacje o tych nowych funkcjach.

Ten artykuł koncentruje się na następujących technikach zarządzania zasobami:

- Zadeklaruj [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) , aby wyrazić, że typ jest **niemodyfikowalny** i umożliwia kompilatorowi zapisywanie kopii przy użyciu parametrów [`in`](language-reference/keywords/in-parameter-modifier.md) .
- Jeśli typ nie może być niezmienny, zadeklaruj `struct` składowe `readonly`, aby wskazać, że element członkowski nie modyfikuje stanu.
- Użyj [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) zwracać, gdy wartość zwracana jest `struct` większa niż <xref:System.IntPtr.Size?displayProperty=nameWithType> i okres istnienia magazynu jest większy niż Metoda zwracająca wartość.
- Gdy rozmiar `readonly struct` jest większy niż <xref:System.IntPtr.Size?displayProperty=nameWithType>, należy przekazać go jako parametr `in` ze względu na wydajność.
- Nigdy nie przekazuj `struct` jako parametru `in`, chyba że jest zadeklarowany za pomocą modyfikatora `readonly` lub metoda wywołuje tylko `readonly` elementów członkowskich struktury. Naruszanie tych wskazówek może negatywnie wpłynąć na wydajność i może prowadzić do przesłaniania.
- Użyj [`ref struct`](language-reference/keywords/ref.md#ref-struct-types)lub `readonly ref struct`, takich jak <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> do pracy z pamięcią, jako sekwencji bajtów.

Te techniki wymuszają zrównoważenie dwóch konkurencyjnych celów w odniesieniu do **odwołań** i **wartości**. Zmienne, które są [typami odwołań](programming-guide/types/index.md#reference-types) , przechowują odwołanie do lokalizacji w pamięci. Zmienne [typu wartości](programming-guide/types/index.md#value-types) bezpośrednio zawierają ich wartości. Różnice te podkreślają kluczowe różnice, które są ważne w przypadku zarządzania zasobami pamięci. **Typy wartości** są zwykle kopiowane, gdy są przesyłane do metody lub zwracane z metody. To zachowanie obejmuje kopiowanie wartości `this` podczas wywoływania elementów członkowskich typu wartości. Koszt kopii jest związany z rozmiarem typu. **Typy odwołań** są przydzielane na zarządzanym stosie. Każdy nowy obiekt wymaga nowej alokacji, a następnie musi zostać odczytany. Obie te operacje są czasochłonne. Odwołanie jest kopiowane, gdy typ odwołania zostanie przekazana jako argument do metody lub zwrócony z metody.

W tym artykule przedstawiono przykładową koncepcję struktury punktu 3W w celu wyjaśnienia następujących zaleceń:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Różne przykłady używają różnych implementacji tego pojęcia.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Deklarowanie struktur tylko do odczytu dla niezmiennych typów wartości

Deklarowanie `struct` przy użyciu modyfikatora `readonly` informuje kompilator, że celem jest utworzenie niezmiennego typu. Kompilator wymusza tę decyzję projektową z następującymi regułami:

- Wszystkie elementy członkowskie pola muszą być `readonly`
- Wszystkie właściwości muszą być tylko do odczytu, z uwzględnieniem właściwości wdrożonych domyślnie.

Te dwie reguły są wystarczające, aby upewnić się, że żaden członek `readonly struct` nie modyfikuje stanu tej struktury. `struct` jest niezmienna. Strukturę `Point3D` można zdefiniować jako niezmienne struktury, jak pokazano w następującym przykładzie:

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

Postępuj zgodnie z tym zaleceniem za każdym razem, gdy zamierzasz utworzyć niezmienny typ wartości. Wszelkie ulepszenia wydajności są dodatkową korzyścią. `readonly struct` jasno wyraża zamiar projektowania.

## <a name="declare-readonly-members-when-a-struct-cant-be-immutable"></a>Zadeklaruj składowe tylko do odczytu, gdy struktura nie może być niezmienna

W C# 8,0 i nowszych, gdy typ struktury jest modyfikowalny, należy zadeklarować składowe, które nie powodują`readonly`mutacji. Na przykład poniżej przedstawiono modyfikowalną odmianę struktury punktu 3W:

```csharp
public struct Point3D
{
    public Point3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    private double _x;
    public double X 
    { 
        readonly get { return _x;}; 
        set { _x = value; }
    }
    
    private double _y;
    public double Y 
    { 
        readonly get { return _y;}; 
        set { _y = value; }
    }

    private double _z;
    public double Z 
    { 
        readonly get { return _z;}; 
        set { _z = value; }
    }

    public readonly double Distance => Math.Sqrt(X * X + Y * Y + Z * Z);

    public readonly override string ToString() => $"{X, Y, Z }";
}
```

Powyższy przykład pokazuje wiele lokalizacji, w których można zastosować modyfikator `readonly`: metody, właściwości i metod dostępu do właściwości. Jeśli używasz automatycznie wdrożonych właściwości, kompilator dodaje modyfikator `readonly` do metody dostępu `get` do odczytu i zapisu właściwości. Kompilator dodaje modyfikator `readonly` do automatycznie implementowanych deklaracji właściwości dla właściwości z tylko akcesorem `get`.

Dodanie modyfikatora `readonly` do elementów członkowskich, które nie są zgodne ze stanem, zapewnia dwie powiązane korzyści. Najpierw kompilator wymusza zamiar. Ten element członkowski nie może zmieniać stanu struktury ani nie może uzyskać dostępu do elementu członkowskiego, który nie jest również oznaczony `readonly`. Po drugie kompilator nie będzie tworzyć obronnych kopii parametrów `in` podczas uzyskiwania dostępu do `readonly` elementu członkowskiego. Kompilator może bezpiecznie wykonać tę optymalizację, ponieważ gwarantuje, że `struct` nie jest modyfikowany przez `readonly` składową.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Używaj instrukcji `ref readonly return` w przypadku dużych struktur, gdy jest to możliwe

Można zwrócić wartości przez odwołanie, gdy zwracana wartość nie jest lokalna dla zwracanej metody. Zwracanie przez odwołanie oznacza, że kopiowane jest tylko odwołanie, a nie strukturę. W poniższym przykładzie właściwość `Origin` nie może użyć powrotu `ref`, ponieważ zwracana wartość jest zmienną lokalną:

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

Jednak następująca Definicja właściwości może być zwracana przez odwołanie, ponieważ zwrócona wartość jest statyczną składową:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

Nie chcesz, aby wywołujący modyfikowali źródło, więc należy zwrócić wartość `readonly ref`:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

Zwrócenie `ref readonly` umożliwia zapisanie kopiowania większych struktur i zachowanie niezmienności wewnętrznych elementów członkowskich danych.

W odniesieniu do witryny wywołującej może być używana Właściwość `Origin` jako `readonly ref` lub jako wartość:

[!code-csharp[AssignRefReadonly](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Pierwsze przypisanie w poprzednim kodzie wykonuje kopię `Origin` stałej i przypisuje tę kopię. Drugi przypisuje odwołanie. Należy zauważyć, że modyfikator `readonly` musi być częścią deklaracji zmiennej. Nie można zmodyfikować odwołania, do którego się odwołuje. Próby wykonania tej operacji spowodują błąd czasu kompilacji.

Modyfikator `readonly` jest wymagany w deklaracji `originReference`.

Kompilator wymusza, aby obiekt wywołujący nie mógł zmodyfikować odwołania. Próbuje przypisać wartość bezpośrednio Wygeneruj błąd czasu kompilacji. Jednak kompilator nie może wiedzieć, czy jakakolwiek metoda członkowska modyfikuje stan struktury.
Aby upewnić się, że obiekt nie jest modyfikowany, kompilator tworzy kopie i wywołuje odwołania do elementów członkowskich przy użyciu tej kopii. Wszelkie modyfikacje dotyczą tej kopii.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Zastosuj modyfikator `in`, aby `readonly struct` parametry większe niż `System.IntPtr.Size`

Słowo kluczowe `in` uzupełnia istniejące `ref` i `out` słowa kluczowe, aby przekazywać argumenty przez odwołanie. Słowo kluczowe `in` określa przekazywanie argumentu przez odwołanie, ale wywołana metoda nie modyfikuje wartości.

To dodanie zapewnia pełen słownictwo do wyrażania zamiaru projektowania.
Typy wartości są kopiowane, gdy są przesyłane do wywołanej metody, jeśli nie określisz żadnego z następujących modyfikatorów w podpisie metody. Każdy z tych modyfikatorów określa, że zmienna jest przenoszona przez odwołanie, unikając kopiowania. Każdy modyfikator wyraża inny cel:

- `out`: Ta metoda ustawia wartość argumentu używanego jako ten parametr.
- `ref`: Ta metoda może ustawić wartość argumentu używanego jako ten parametr.
- `in`: Ta metoda nie modyfikuje wartości argumentu używanego jako ten parametr.

Dodaj modyfikator `in`, aby przekazać argument przez odwołanie i zadeklarować intencję projektowania do przekazywania argumentów przez odwołanie, aby uniknąć niepotrzebnego kopiowania. Nie zamierzasz modyfikować obiektu używanego jako ten argument.

To rozwiązanie często zwiększa wydajność dla typów wartości tylko do odczytu, które są większe niż <xref:System.IntPtr.Size?displayProperty=nameWithType>. Dla typów prostych (`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, `bool`i `enum` typów) , wszelkie potencjalne zyski wydajności są minimalne. W rzeczywistości wydajność może się pogorszyć za pomocą przekazywania informacji dla typów mniejszych niż <xref:System.IntPtr.Size?displayProperty=nameWithType>.

Poniższy kod przedstawia przykład metody, która oblicza odległość między dwoma punktami w przestrzeni 3D.

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Argumenty to dwie struktury, które każda z nich zawiera trzy podwojone. Podwójna wartość to 8 bajtów, więc każdy argument ma 24 bajty. Określając modyfikator `in`, należy przekazać 4-bajtowy lub 8-bajtowy odwołanie do tych argumentów, w zależności od architektury maszyny. Różnica w rozmiarze jest mała, ale jest dodawana, gdy aplikacja wywołuje tę metodę w ścisłej pętli używającej wielu różnych wartości.

Modyfikator `in` uzupełnia także `out` i `ref` w inny sposób. Nie można tworzyć przeciążeń metody, które różnią się tylko w obecności `in`, `out`lub `ref`. Te nowe reguły zwiększają takie samo zachowanie, które było zawsze zdefiniowane dla `out` i `ref` parametrów. Podobnie jak `out` i Modyfikatory `ref`, typy wartości nie są opakowane, ponieważ jest stosowany modyfikator `in`.

Modyfikator `in` może zostać zastosowany do każdego elementu członkowskiego, który pobiera parametry: metody, Delegaty, wyrażenia lambda, funkcje lokalne, indeksatory i operatory.

Inną funkcją `in` parametrów jest, że można użyć wartości literału lub stałych dla argumentu do `in` parametru. Ponadto, w przeciwieństwie do `ref` lub `out` parametru, nie trzeba stosować modyfikatora `in` w witrynie wywołania. Poniższy kod przedstawia dwa przykłady wywołania metody `CalculateDistance`. Pierwsze używa dwóch zmiennych lokalnych przekazaną przez odwołanie. Drugi zawiera zmienną tymczasową utworzoną w ramach wywołania metody.

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Istnieje kilka sposobów, w których kompilator wymusza charakter `in` tylko do odczytu.  Po pierwsze, wywołana metoda nie może bezpośrednio przypisywać do parametru `in`. Nie można bezpośrednio przypisać do żadnego pola `in` parametru, gdy ta wartość jest typu `struct`. Ponadto nie można przekazać `in` parametru do żadnej metody za pomocą modyfikatora `ref` lub `out`.
Te reguły mają zastosowanie do każdego pola `in` parametru, pod warunkiem, że pole jest typu `struct`, a parametr jest również typem `struct`. W rzeczywistości te reguły mają zastosowanie w przypadku wielu warstw dostępu do elementów członkowskich, pod warunkiem `structs`typy na wszystkich poziomach dostępu do elementów członkowskich.
Kompilator wymusza, że typy `struct` przekazane jako argumenty `in` i ich składowe `struct` są zmiennymi tylko do odczytu, gdy są używane jako argumenty innych metod.

Użycie parametrów `in` może uniknąć potencjalnych kosztów tworzenia kopii. Nie zmienia ona semantyki żadnego wywołania metody. W związku z tym nie trzeba określać modyfikatora `in` w witrynie wywołania. Pomijanie modyfikatora `in` w witrynie wywołania informuje kompilator, że może on wykonać kopię argumentu z następujących powodów:

- Istnieje niejawna konwersja, ale nie konwersja tożsamości z typu argumentu na typ parametru.
- Argument jest wyrażeniem, ale nie ma znanej zmiennej magazynu.
- Istnieje Przeciążenie, które różni się od obecności lub braku `in`. W takim przypadku Przeciążenie przez wartość jest lepszym dopasowaniem.

Te reguły są przydatne podczas aktualizowania istniejącego kodu w celu użycia argumentów odwołania tylko do odczytu. Wewnątrz metody wywoływanej można wywołać dowolną metodę wystąpienia używaną przez parametry wartości. W tych wystąpieniach zostanie utworzona kopia `in` parametru. Ponieważ kompilator może utworzyć zmienną tymczasową dla dowolnego parametru `in`, można także określić wartości domyślne dla dowolnego parametru `in`. Poniższy kod określa źródło (punkt 0, 0) jako wartość domyślną dla drugiego punktu:

[!code-csharp[InArgumentDefault](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Aby wymusić przekazywanie przez kompilator argumentów tylko do odczytu przez odwołanie, określ modyfikator `in` dla argumentów w miejscu wywołania, jak pokazano w poniższym kodzie:

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

To zachowanie ułatwia stosowanie parametrów `in` w czasie w dużych bazach kodu, w których możliwy jest wzrost wydajności. Aby najpierw dodać modyfikator `in` do podpisów metod. Następnie można dodać modyfikator `in` w lokacjach wywołań i utworzyć typy `readonly struct`, aby umożliwić kompilatorowi uniknięcie tworzenia w większej liczbie obronnych kopii `in` parametrów.

Wyznaczania parametru `in` można również użyć z typami referencyjnymi lub wartościami liczbowymi. Jednak korzyści w obu przypadkach są minimalne, o ile istnieją.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>Nigdy nie używaj niemodyfikowalnych struktur jako argumentu `in`

Opisane powyżej techniki wyjaśniają, jak uniknąć kopiowania przez zwracanie odwołań i przekazywanie wartości przez odwołanie. Techniki te działają najlepiej, gdy typy argumentów są zadeklarowane jako typy `readonly struct`. W przeciwnym razie kompilator musi utworzyć **kopie** w wielu sytuacjach, aby wymusić stałość wszystkich argumentów. Rozważmy poniższy przykład, który oblicza odległość punktu 3W od źródła:

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Struktura `Point3D` *nie* jest strukturą tylko do odczytu. W treści tej metody istnieje sześć różnych wywołań dostępu do właściwości. Przy pierwszej analizie można uważać, że te dostępy były bezpieczne. Po wykonaniu tej operacji metoda dostępu `get` nie powinna modyfikować stanu obiektu. Nie istnieje jednak reguła języka, która wymusza ten. Jest to tylko Wspólna konwencja. Każdy typ może zaimplementować metodę dostępu `get`, która zmodyfikowała stan wewnętrzny. Bez gwarancji języka kompilator musi utworzyć tymczasową kopię argumentu przed wywołaniem dowolnego elementu członkowskiego. Magazyn tymczasowy jest tworzony na stosie, wartości argumentu są kopiowane do magazynu tymczasowego, a wartość jest kopiowana do stosu dla każdego elementu członkowskiego jako argument `this`. W wielu sytuacjach te kopie mają szkodliwy wpływ na wydajność, ponieważ przekazywanie przez wartość jest szybsze niż odwołanie przekazywane przez tylko do odczytu, gdy typ argumentu nie jest `readonly struct`.

Zamiast tego, jeśli obliczenie odległości używa niezmiennej struktury, `ReadonlyPoint3D`, obiekty tymczasowe nie są potrzebne:

[!code-csharp[readonlyInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Kompilator generuje bardziej wydajny kod podczas wywoływania elementów członkowskich `readonly struct`: odwołanie `this`, zamiast kopii odbiornika, jest zawsze `in` parametrem przekazaną przez odwołanie do metody członkowskiej. Ta optymalizacja zapisuje kopiowanie w przypadku używania `readonly struct` jako argumentu `in`.

Nie należy przekazywać typu wartości null jako argumentu `in`. Typ <xref:System.Nullable%601> nie jest zadeklarowany jako struktura tylko do odczytu. Oznacza to, że kompilator musi generować kopie obronne dla każdego argumentu typu wartości null przekazaną do metody przy użyciu modyfikatora `in` w deklaracji parametru.

Możesz zobaczyć Przykładowy program, który demonstruje różnice w wydajności przy użyciu [Benchmark.NET](https://www.nuget.org/packages/BenchmarkDotNet/) w naszym [repozytorium przykładów](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) w witrynie GitHub. Porównuje przekazanie modyfikowalnej struktury przez wartość i przez odwołanie z przekazywaniem niezmiennej struktury przez wartość i przez odwołanie. Użycie niezmiennej struktury i przekazywanie przez odwołanie jest najszybsze.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Użyj typów `ref struct` do pracy z blokami lub pamięcią w pojedynczej klatce stosu

Pokrewna funkcja języka jest możliwość zadeklarować typ wartości, który musi być ograniczony do pojedynczej ramki stosu. To ograniczenie umożliwia kompilatorowi wykonywanie kilku optymalizacji. Podstawowa motywacja tej funkcji była <xref:System.Span%601> i powiązane struktury. Ulepszenia wydajności z tych ulepszeń zostaną osiągnięte przy użyciu nowych i zaktualizowanych interfejsów API platformy .NET, które używają typu <xref:System.Span%601>.

Podobne wymagania mogą pracować z pamięcią utworzoną przy użyciu [`stackalloc`](language-reference/operators/stackalloc.md) lub w przypadku korzystania z pamięci z interfejsów API międzyoperacyjności. Dla tych potrzeb można definiować własne typy `ref struct`.

## <a name="readonly-ref-struct-type"></a>Typ `readonly ref struct`

Deklarowanie struktury jako `readonly ref` łączy zalety i ograniczenia `ref struct` i deklaracji `readonly struct`. Pamięć używana przez zakres tylko do odczytu jest ograniczona do pojedynczej ramki stosu i nie można modyfikować pamięci używanej przez zakres tylko do odczytu.

## <a name="conclusions"></a>Wnioski

Użycie typów wartości minimalizuje liczbę operacji alokacji:

- Magazyn dla typów wartości jest przydzielony na stosy dla zmiennych lokalnych i argumentów metod.
- Magazyn dla typów wartości, które są elementami członkowskimi innych obiektów, jest przydzielany jako część tego obiektu, a nie jako oddzielna alokacja.
- Magazyn dla zwracanych wartości typu wartości jest przydzielony przez stos.

Kontrast, który ma typy referencyjne w tych samych sytuacjach:

- Magazyn dla typów referencyjnych to sterta przypisana do zmiennych lokalnych i argumentów metod. Odwołanie jest przechowywane na stosie.
- Magazyn dla typów referencyjnych, które są elementami członkowskimi innych obiektów, jest przypisywany osobno na stercie. Obiekt zawierający zawiera odwołanie.
- Magazyn dla zwracanych wartości typu referencyjnego to przydzieloną sterty. Odwołanie do tego magazynu jest przechowywane na stosie.

Minimalizacja alokacji obejmuje kompromisy. Kopiuj więcej pamięci, gdy rozmiar `struct` jest większy niż rozmiar odwołania. Odwołanie jest zwykle 64 bitów lub 32 bitów i zależy od procesora maszyny docelowej.

Te kompromisy mają zwykle minimalny wpływ na wydajność. Jednak w przypadku dużych struktur lub większych kolekcji zwiększa się wpływ na wydajność. Wpływ może być duży w przypadku ścisłych pętli i ścieżek dla programów.

Te ulepszenia C# języka są przeznaczone dla krytycznych algorytmów wydajności, w których Minimalizacja alokacji pamięci jest głównym czynnikiem w celu osiągnięcia wymaganej wydajności. Może się okazać, że nie używasz często tych funkcji w kodzie, który napiszesz. Jednak te ulepszenia zostały przyjęte w całym środowisku .NET. Ponieważ więcej i więcej interfejsów API korzystających z tych funkcji, zobaczysz wydajność aplikacji.

## <a name="see-also"></a>Zobacz także

- [ref — słowo kluczowe](language-reference/keywords/ref.md)
- [Wartości zwracane ref i zmienne lokalne ref](programming-guide/classes-and-structs/ref-returns.md)
