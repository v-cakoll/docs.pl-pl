---
title: Zapis w bezpieczny i skuteczny C# kodu
description: Najnowsze ulepszenia C# języka umożliwiają pisanie weryfikowalny kod bezpieczny, że wydajność była poprzednio skojarzona z niebezpieczny kod.
ms.date: 10/23/2018
ms.custom: mvc
ms.openlocfilehash: c5505f69a4706ef0f631c82e075e422cb8e13885
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50043116"
---
# <a name="write-safe-and-efficient-c-code"></a>Zapis w bezpieczny i skuteczny C# kodu #

Nowe funkcje w C# umożliwiają pisanie weryfikowalny kod bezpieczny lepszą wydajność. Jeśli zastosujesz dokładnie te techniki, mniej scenariusze wymagają niebezpieczny kod. Te funkcje ułatwiają użyć odwołania do typów wartości jako metoda argumenty i zwraca metoda. Po zakończeniu bezpiecznie tych technik zminimalizować kopiowania typów wartości. Korzystając z typów wartości, można zminimalizować liczbę alokacji i przekazuje kolekcji wyrzucania elementów.

Duża część przykładowego kodu w tym artykule używa funkcji dodanych w C# 7.2. Aby korzystać z tych funkcji, należy skonfigurować projekt do C# 7.2 lub nowsza. Aby uzyskać więcej informacji na temat ustawiania wersji języka, zobacz [skonfigurować wersję językową](language-reference/configure-language-version.md).

Ten artykuł koncentruje się na temat metod do zarządzania zasobami wydajne. Jedną z zalet przy użyciu typów wartości jest, aby uniknąć często alokacji sterty. Wadą jest to zostaną skopiowane przez wartość. To kosztem utrudnienie Optymalizowanie algorytmów, które działają na dużych ilości danych. Nowy język funkcje w C# 7.2 zapewniają mechanizmy, które umożliwiają bezpieczne wydajność kodu przy użyciu odwołań do typów wartości. Należy uważnie używać tych funkcji do minimum zarówno alokacji i operacje kopiowania. W tym artykule przeanalizowano tych nowych funkcji.

Ten artykuł koncentruje się na następujących technik zarządzania zasobów:

- Zadeklaruj [ `readonly struct` ](language-reference/keywords/readonly.md#readonly-struct-example) programu express, że typ jest **niezmienialnych** i umożliwia kompilatorowi Zapisuj kopie w przypadku korzystania z [ `in` ](language-reference/keywords/in-parameter-modifier.md) parametrów.
- Użyj [ `ref readonly` ](language-reference/keywords/ref.md#reference-return-values) zwrócenia, jeśli wartość zwracana to `struct` większy niż <xref:System.IntPtr.Size?displayProperty=nameWithType> i okresu istnienia pamięci masowej jest większa niż metoda zwracania wartości.
- Gdy rozmiar `readonly struct` jest większy niż <xref:System.IntPtr.Size?displayProperty=nameWithType>, należy przekazać go jako `in` parametr ze względu na wydajność.
- Nigdy nie przekazać `struct` jako `in` parametr o ile nie jest zadeklarowana za pomocą `readonly` modyfikator ponieważ może negatywnie wpłynąć na wydajność i może prowadzić do zasłoniętej zachowania.
- Użyj [ `ref struct` ](language-reference/keywords/ref.md#ref-struct-types), lub `readonly ref struct` takich jak <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> do pracy z pamięcią za pomocą sekwencji bajtów.

Te techniki wymusić równoważyć dwóch celów konkurencyjnych w odniesieniu do **odwołania** i **wartości**. Zmienne, które są [typy odwołań](programming-guide/types/index.md#reference-types) utrzymywanie odwołania do lokalizacji w pamięci. Zmienne, które są [typy wartości](programming-guide/types/index.md#value-types) bezpośrednio zawierać ich wartości. Te różnice wyróżnienie podstawowe różnice, które są ważne na potrzeby zarządzania zasobami pamięci. **Typy wartości** zwykle są kopiowane, gdy przekazywane do metody lub zwrócone z metody. To zachowanie obejmuje kopiowanie wartości `this` podczas wywoływania elementów członkowskich typu wartości. Koszt kopii jest powiązana z rozmiaru typu. **Typy odwołań** są przydzielane na zarządzanym stosie. Każdy nowy obiekt wymaga nowej alokacji, a następnie należy odzyskać. Oba te operacje trwają czasu. Odwołanie jest kopiowane, gdy typ odwołania jest przekazywany jako argument do metody lub zwrócone z metody.

W tym artykule używa następujących koncepcji przykład struktury punktu 3W, aby wyjaśnić te zalecenia:

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

Różne przykłady używają różne implementacje tę koncepcję.

## <a name="declare-readonly-structs-for-immutable-value-types"></a>Zadeklaruj struktur tylko do odczytu dla typów wartości niezmienialnych

Deklarowanie `struct` przy użyciu `readonly` modyfikator informuje kompilator, zgodne z zamiarami użytkownika jest utworzenie typu niezmienne. Kompilator wymusza tej decyzji projektowych, z następującymi regułami:

- Wszystkie elementy członkowskie pola musi być `readonly`
- Wszystkie właściwości muszą być tylko do odczytu, w tym właściwości zaimplementowane automatycznie.

Te dwie reguły są wystarczające, aby upewnić się, że żaden członek `readonly struct` modyfikuje stan tej struktury. `struct` Można modyfikować. `Point3D` Strukturę można zdefiniować jako niezmienialny struktury, jak pokazano w poniższym przykładzie:

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

Zawsze wtedy, gdy zgodną z planem projektu w celu utworzenia typu wartości niezmienne, postępuj zgodnie z tego zalecenia. Jakie ulepszenia wydajności są dodatkowe korzyści. `readonly struct` Wyraźnie wyraża zgodną z planem projektu.

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>Użyj `ref readonly return` instrukcji dla dużych struktur, gdy jest to możliwe

Może zwracać wartości przez odwołanie, kiedy wartość zwracana nie jest lokalnym zwracanych metody. Zwracanie przez odwołanie oznacza, że kopiowane jest tylko odwołanie, nie struktury. W poniższym przykładzie `Origin` właściwości nie można użyć `ref` zwrócić, ponieważ wartość zwracana jest zmienna lokalna:

```csharp
public Point3D Origin {get;} => new Point3D(0,0,0);
```

Jednak następującą definicję właściwości mogą być zwrócone przez odwołanie, ponieważ zwrócona wartość jest składową statyczną:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin { get; } => ref origin;

    // other members removed for space
}
```

Nie chcesz, aby modyfikowanie pochodzenia, dzięki czemu powinna zwrócić wartość przez obiekty wywołujące `readonly ref`:

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public ref readonly Point3D Origin { get; } => ref origin;

    // other members removed for space
}
```

Zwracanie przez `readonly ref` umożliwia zapisywanie, kopiowanie większych struktur i zachować niezmienności członkowie danych wewnętrznych.

W witrynie wywołania obiektów wywołujących wprowadzić decyzja o korzystaniu z `Origin` właściwość jako `readonly ref` lub jako wartość:

[!code-csharp[AssignRefReadonly](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

Pierwsze przypisanie w poprzednim kodzie tworzy kopię `Origin` stałych i przypisuje kopiujących. Drugi przypisuje odwołania. Należy zauważyć, że `readonly` modyfikator musi być częścią deklaracja zmiennej. Nie można zmodyfikować odwołania, do którego się odwołuje. Próba wykonania tej czynności powoduje błąd kompilacji.

`readonly` Modyfikator jest wymagany w deklaracji `originReference`.

Kompilator wymusza to, że obiekt wywołujący nie można zmodyfikować odwołania. Podejmowana jest próba przypisania wartości bezpośrednio wygenerować błąd kompilacji. Jednak kompilator nie wiadomo, jeśli metoda dowolnego elementu członkowskiego modyfikuje stan struktury.
Aby upewnić się, że obiekt nie jest modyfikowana, kompilator tworzy kopię i wywołuje element członkowski odwołań za pomocą tej kopii. Wszystkie modyfikacje są tym kopia obronna.

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>Zastosuj `in` modyfikatora `readonly struct` parametry większe niż `System.IntPtr.Size`

`in` — Słowo kluczowe uzupełniają istniejące `ref` i `out` słów kluczowych, aby przekazywać argumentów przez odwołanie. `in` — Słowo kluczowe Określa, przekazywanie argumentu przez odwołanie, ale wywoływanej metody nie modyfikuje wartości.

To dodawanie zapewnia pełną słownictwa wyrażenia zgodną z planem projektu.
Typy wartości są kopiowane, gdy przekazywane do metody o nazwie, jeśli nie określisz dowolną z następujących modyfikatorów w podpisie metody. Każda z tych modyfikatorów Określa, czy zmienna jest przekazywana przez odwołanie, unikając kopiowania. Każdy modyfikator wyraża innego zamiaru:

- `out`: Ta metoda ustawia wartość argumentu jako parametr.
- `ref`: Ta metoda może ustawić wartość argumentu jako parametr.
- `in`: Ta metoda nie modyfikuje wartość argumentu jako parametr.

Dodaj `in` modyfikator do przekazywania argumentu przez odwołanie i Zadeklaruj swoje założenia projektowe, aby przekazywać argumentów przez odwołanie, aby uniknąć niepotrzebnego kopiowania. Nie zamierzasz zmodyfikować obiekt używany w roli tego argumentu. Poniższy kod przedstawia przykład metody, które oblicza odległość między dwoma punktami w przestrzeni 3D.

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

Argumenty są dwie struktury, że każdy zawiera trzech liczb typu Double. Wartość o podwójnej precyzji jest 8 bajtów, dzięki czemu każdy argument jest 24 bajty. Określając `in` modyfikatora, należy przekazać 4-bajtowych lub 8-bajtowych odwołania do tych argumentów, w zależności od architektury komputera. Różnica w rozmiarze jest mała, ale dodaje, gdy Twoja aplikacja wywołuje tę metodę w pętli za pomocą wielu różnych wartości.

`in` Uzupełniające modyfikator `out` i `ref` w inny sposób, jak również. Nie można utworzyć przeciążenia metody, które różnią się tylko w obecności właściwości `in`, `out`, lub `ref`. Te nowe reguły rozszerzyć takie samo zachowanie, które zawsze miały zostały zdefiniowane dla `out` i `ref` parametrów. Podobnie jak `out` i `ref` modyfikatorów, typy wartości nie są zapakowany, ponieważ `in` modyfikator jest stosowany.

`in` Modyfikator mogą być stosowane do wszystkich elementów członkowskich, która przyjmuje parametry: metod delegatów, wyrażeń lambda, funkcji lokalnych, indeksatory, operatorów.

Kolejną funkcją `in` parametry są może używać wartości literałów lub stałe w jako argumentu do `in` parametru. Ponadto, w odróżnieniu od `ref` lub `out` parametru, nie trzeba zastosować `in` modyfikator w witrynie wywołania. Poniższy kod pokazuje dwa przykłady wywoływania `CalculateDistance` metody. Pierwszy używa dwóch zmiennych lokalnych, przekazywany przez odwołanie. Drugi zawiera zmienną tymczasową utworzonych jako część wywołania metody.

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

Istnieje kilka sposobów, w których kompilator wymusza tylko do odczytu rodzaj `in` argumentu.  Po pierwsze, wywoływanej metody nie można przypisać bezpośrednio do `in` parametru. Bezpośrednio nie można przypisać do dowolnego pola `in` parametr, gdy ta wartość jest `struct` typu. Ponadto nie można przekazać `in` parametr przy użyciu dowolnej metody `ref` lub `out` modyfikator.
Te reguły mają zastosowanie do dowolnego pola `in` parametru podane, pole jest `struct` typu, a parametr jest również `struct` typu. W rzeczywistości te reguły stosuje się na wiele warstw dostępu do elementu członkowskiego, pod warunkiem typy na wszystkich poziomach dostępu do elementu członkowskiego `structs`.
Kompilator wymusza, który `struct` typy przekazane jako `in` argumentów i ich `struct` elementy członkowskie są zmienne tylko do odczytu, gdy jest używana jako argumenty do innych metod.

Korzystanie z `in` parametrów można uniknąć potencjalnych kosztów wydajności tworzenia kopii. Go nie zmienia semantykę każde wywołanie metody. W związku z tym, nie trzeba określić `in` modyfikator w witrynie wywołania. Pominięcie `in` modyfikator w witrynie wywołania informuje kompilator, mogą być kopię argumentu z następujących powodów:

- Istnieje niejawna konwersja, ale nie tożsamość konwersję z typu argumentu z typem parametru.
- Argument jest wyrażeniem, ale nie ma zmienną znanych magazynu.
- Istnieje przeciążenie różni się obecności lub braku `in`. W takim przypadku według wartości przeciążenia ma lepsze dopasowanie.

Reguły te są przydatne w przypadku aktualizowania istniejącego kodu do argumenty odwołania tylko do odczytu. Wewnątrz metody o nazwie możesz wywołać dowolnej metody wystąpienia, która używa parametrów wielowartościowych. W tych przypadkach kopię `in` utworzeniu parametru. Ponieważ kompilator może utworzyć zmienną tymczasową dla każdego `in` parametru, można również określić wartości domyślnych dla każdej `in` parametru. Poniższy kod określa pochodzenia (punkt 0,0) jako wartość domyślna dla drugi punkt:

[!code-csharp[InArgumentDefault](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

Aby wymusić na kompilatorze argument tylko do odczytu jest przekazywany przez odwołanie, należy określić `in` modyfikator dla argumentów w witrynie wywołania, jak pokazano w poniższym kodzie:

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

To zachowanie ułatwia przyjęcie `in` parametrów wraz z upływem czasu w dużych bazach kodu, gdzie możliwe są wzrost wydajności. Możesz dodać `in` modyfikatora podpisy metod pierwszy. Następnie należy dodać `in` modyfikator na wywołania i utworzyć `readonly struct` typy umożliwiające kompilatorowi unikanie tworzenia kopii obrony `in` parametrów w większej liczby lokalizacji.

`in` Nazwy parametru może również służyć za pomocą typów referencyjnych lub wartości liczbowych. Jednak korzyści w obu przypadkach są minimalne, jeśli istnieje.

## <a name="never-use-mutable-structs-as-in-in-argument"></a>Nigdy nie używaj mutable struktur, podobnie jak w `in` argumentu

Opisane powyżej metody wyjaśniają, jak uniknąć kopii, zwracając odwołań i przekazanie wartości przez odwołanie. Techniki te działają najlepiej, jeśli typy argumentów są deklarowane jako `readonly struct` typów. W przeciwnym razie kompilator musi utworzyć **obrony kopie** w wielu sytuacjach, aby wymusić tylko do odczytu ness żadnych argumentów. Rozważmy następujący przykład, który oblicza odległość punkt 3D ze źródła:

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

`Point3D` Struktura jest *nie* struktury tylko do odczytu. Istnieje sześć wywołań dostęp do różnych właściwości w treści tej metody. Na pierwszego badania może mieć umieszczenie tych dostępach są bezpieczne. Gdy wszystkie `get` akcesor nie należy modyfikować stan obiektu. Ale nie ma żadnej reguły języka, który wymusza. Jest typową Konwencją. Można wdrożyć dowolny typ `get` dostępu, który zmodyfikował stan wewnętrzny. Bez gwarancji niektóre języka kompilatora należy utworzyć tymczasowej kopii argument przed wywołaniem dowolnego elementu członkowskiego. Magazyn tymczasowy jest tworzone na stosie, wartości argumentu są kopiowane do tymczasowego przechowywania i wartość jest kopiowany do stosu dla każdego dostępu do elementu członkowskiego jako `this` argumentu. W wielu sytuacjach te kopie negatywnie wpłynąć na wydajność, tyle że przekazać przez wartość jest szybsze niż — dostęp próbny, tylko do odczytu odwołanie gdy typ argumentu jest `readonly struct`.

Zamiast tego, jeśli obliczeń odległość używa struktury niezmienne `ReadonlyPoint3D`, obiekty tymczasowe nie są potrzebne:

[!code-csharp[readonlyInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

Kompilator generuje kod bardziej efektywne, gdy wywołujesz członkowie `readonly struct`: `this` odwołanie, zamiast kopii receiver, jest zawsze `in` parametr przekazywany przez odwołanie do elementu członkowskiego. Tego rodzaju optymalizacji zapisywanie, kopiowanie, gdy używasz `readonly struct` jako `in` argumentu.

Możesz zobaczyć program przykładu, który ilustruje różnice wydajności przy użyciu [Benchmark.net](https://www.nuget.org/packages/BenchmarkDotNet/) w naszym [repozytorium przykładów](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark) w witrynie GitHub. Porównuje się sukcesem, struktura mutable według wartości i według odwołania przekazywanie struktury niezmienne według wartości i według odwołania. Korzystanie z niezmiennego struktury i — dostęp próbny przez odwołanie jest najszybszy.

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>Użyj `ref struct` typy do pracy z bloków lub pamięci na ramce stosu

Funkcja języka powiązane jest zdolność do deklarowania typu wartości, które muszą być ograniczone do ramki stosu. To ograniczenie włącza kompilator udostępnia kilka optymalizacji. Główną motywacją do tej funkcji został <xref:System.Span%601> i pokrewne struktury. Osiągniesz poprawa wydajności wynikająca ze te rozszerzenia funkcjonalności za pomocą nowych i zaktualizowanych interfejsów API platformy .NET, które używanie <xref:System.Span%601> typu.

Masz podobnych wymaganiach dotyczących pracy z pamięcią utworzone za pomocą [ `stackalloc` ](language-reference/keywords/stackalloc.md) lub w przypadku używania pamięci za pomocą międzyoperacyjnych interfejsów API. Definiowanie swoich własnych `ref struct` typy dla tych wymagań.

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` Typ

Deklarowanie struktury jako `readonly ref` łączy korzyści i ograniczeń dotyczących `ref struct` i `readonly struct` deklaracji. Pamięć używana przez zakres tylko do odczytu jest ograniczony do ramki stosu i pamięci używanej przez zakres tylko do odczytu nie mogą być modyfikowane.

## <a name="conclusions"></a>Wnioski

Używanie typów wartości minimalizuje liczbę operacji alokacji:

- Magazyn dla typów wartości jest na stosie dla zmiennych lokalnych i argumenty metody.
- Magazyn dla typów wartości, które należą do innych obiektów jest przydzielany w ramach tego obiektu, nie jako osobne alokacji.
- Magazyn dla typu wartości zwracać wartości jest na stosie.

Kontrast wpisywany z odwołaniem w tej samej sytuacji:

- Magazyn dla typów referencyjnych są sterty przydzielonej dla zmiennych lokalnych i argumenty metody. Odwołania są przechowywane w stosie.
- Magazyn dla typów odwołań, które należą do innych obiektów oddzielnie są przydzielane na stosie. Obiekt zawierający przechowuje odwołania.
- Magazyn dla typu wartości zwracać wartości jest sterty przydzielonej. Odwołanie do tego magazynu są przechowywane w stosie.

Minimalizacja alokacji jest powiązana z stosowania kompromisów. Skopiuj większej ilości pamięci podczas rozmiar `struct` jest większy niż rozmiar odwołania. Odwołanie jest zwykle 64-bitowy lub 32-bitowy i zależy od Procesora komputera docelowego.

Tych kompromisów ogólnie ma wpływ na wydajność minimalny. Jednak dla dużych struktur lub większych kolekcji, zwiększa negatywny wpływ na wydajność. Wpływ mogą być duże w ścisłej pętli i ścieżek krytycznych dla programów.

Te ulepszenia C# języka są przeznaczone dla algorytmów krytyczne wydajności w przypadku, gdy minimalizując alokacji pamięci jest czynnikiem w osiąganiu niezbędne wydajności. Może się okazać, że nie są często używane funkcje te w kodzie, którą piszesz. Jednak te ulepszenia zostały przyjęte w całej platformy .NET. Ponieważ coraz więcej interfejsy API korzystać z tych funkcji, zobaczysz wydajności aplikacji, zwiększyć.
