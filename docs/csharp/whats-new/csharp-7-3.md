---
title: Co nowego w C# 7,3
description: Omówienie nowych funkcji w C# 7,3
ms.date: 05/16/2018
ms.openlocfilehash: ca53073db1b61300186a483001f79bf0caa79169
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433525"
---
# <a name="whats-new-in-c-73"></a>Co nowego w C# 7,3

W C# wersji 7,3 istnieją dwa główne motywy. Jeden motyw udostępnia funkcje, które umożliwiają bezpieczny kod, tak jak kod niebezpieczny. Drugi motyw zawiera ulepszenia przyrostowe istniejących funkcji. Ponadto w tej wersji dodano nowe opcje kompilatora.

Poniższe nowe funkcje obsługują motyw lepszej wydajności dla bezpiecznego kodu:

- Można uzyskać dostęp do stałych pól bez przypinania.
- Zmienne lokalne można przypisywać ponownie `ref` .
- Inicjatorów można używać w `stackalloc` tablicach.
- Można używać `fixed` instrukcji z dowolnym typem, który obsługuje wzorzec.
- Można użyć dodatkowych ograniczeń ogólnych.

W istniejących funkcjach wprowadzono następujące ulepszenia:

- Można testować `==` i `!=` z typami krotek.
- Zmiennych wyrażeń można używać w większej liczbie lokalizacji.
- Możesz dołączyć atrybuty do pola zapasowego właściwości, które są implementowane automatycznie.
- Ulepszono metodę rozdzielczości, gdy `in` argumenty różnią się od.
- Rozwiązanie przeciążenia ma teraz mniej niejednoznaczne przypadki.

Nowe opcje kompilatora są następujące:

- `-publicsign`Aby włączyć podpisywanie zestawów przez oprogramowanie typu Open Source (OSS).
- `-pathmap`w celu zapewnienia mapowania dla katalogów źródłowych.

Pozostała część tego artykułu zawiera szczegółowe informacje i linki, aby dowiedzieć się więcej na temat poszczególnych ulepszeń. Te funkcje można eksplorować w środowisku za pomocą `dotnet try` narzędzia globalnego:

1. Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .
1. Uruchom `dotnet try`.

## <a name="enabling-more-efficient-safe-code"></a>Włączanie bardziej wydajnego bezpiecznego kodu

Powinien być w stanie bezpiecznie napisać C# kod, który wykonuje, a także kod niebezpieczny. Bezpieczny kod unika klas błędów, takich jak przekroczenia buforu, nieużywane wskaźniki i inne błędy dostępu do pamięci. Te nowe funkcje rozszerzają możliwości zweryfikowania bezpiecznego kodu. Staraj się pisać więcej kodu przy użyciu bezpiecznych konstrukcji. Te funkcje ułatwiają to.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Pola `fixed` indeksowania nie wymagają przypinania

Rozważmy tę strukturę:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

We wcześniejszych wersjach programu C#wymagało przypinania zmiennej w celu uzyskania dostępu do jednej z liczb całkowitych, które są `myFixedField`częścią. Teraz Poniższy kod kompiluje bez przypinania zmiennej `p` wewnątrz oddzielnej `fixed` instrukcji:

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

Zmienna `p` uzyskuje dostęp do jednego elementu `myFixedField`w. Nie musisz deklarować odrębnej `int*` zmiennej. Pamiętaj, że nadal potrzebujesz `unsafe` kontekstu. We wcześniejszych wersjach programu C#należy zadeklarować drugi stały wskaźnik:

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Aby uzyskać więcej informacji, zobacz artykuł na temat [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref`zmienne lokalne mogą zostać ponownie przypisane

Teraz elementy `ref` lokalne mogą zostać ponownie przypisane, aby odwoływać się do różnych wystąpień po zainicjowaniu. Poniższy kod jest teraz kompilowany:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Aby uzyskać więcej informacji, zobacz artykuł dotyczący [ `ref` zwrotów i `ref` elementów lokalnych](../programming-guide/classes-and-structs/ref-returns.md)oraz artykuł w [`foreach`](../language-reference/keywords/foreach-in.md)artykule.

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc`Tablice obsługują inicjatory

Po zainicjowaniu można określić wartości dla elementów w tablicy:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Teraz tę samą składnię można zastosować do tablic, które są zadeklarowane `stackalloc`za pomocą:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Aby uzyskać więcej informacji, zobacz [ `stackalloc` ](../language-reference/operators/stackalloc.md) artykuł dotyczący operatorów.

### <a name="more-types-support-the-fixed-statement"></a>Więcej typów obsługuje `fixed` instrukcja

`fixed` Instrukcja obsługuje ograniczony zestaw typów. Począwszy od C# 7,3, dowolny typ, który zawiera `GetPinnableReference()` `ref T` metodę zwracającą lub `ref readonly T` może być `fixed`. Dodanie tej funkcji oznacza, `fixed` że mogą być używane <xref:System.Span%601?displayProperty=nameWithType> z i powiązane typy.

Aby uzyskać więcej informacji, zobacz [ `fixed` artykuł instrukcji](../language-reference/keywords/fixed-statement.md) w dokumentacji języka.

### <a name="enhanced-generic-constraints"></a>Ulepszone ograniczenia ogólne

Teraz można określić typ <xref:System.Enum?displayProperty=nameWithType> lub <xref:System.Delegate?displayProperty=nameWithType> jako ograniczenia klasy bazowej dla parametru typu.

Można również użyć nowego `unmanaged` ograniczenia, aby określić, że parametr typu musi być typem niezarządzanym. [](../language-reference/builtin-types/unmanaged-types.md)

Aby uzyskać więcej informacji, zobacz artykuły dotyczące [ `where` ograniczeń ogólnych](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczeń dla parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).

Dodanie tych ograniczeń do istniejących typów jest niezgodną [zmianą](version-update-considerations.md#incompatible-changes). Zamknięte typy ogólne nie mogą już odpowiadać tym nowym ograniczeniom.

## <a name="make-existing-features-better"></a>Ulepszanie istniejących funkcji

Drugi motyw zawiera ulepszenia funkcji w języku. Te funkcje zwiększają produktywność C#podczas pisania.

### <a name="tuples-support--and-"></a>Krotki obsługują `==` i`!=`

Typy C# krotek obsługują `==` teraz i `!=`. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [równości](../tuples.md#equality-and-tuples) w artykule na temat [krotek](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Dołącz atrybuty do pól zapasowych dla automatycznie implementowanych właściwości

Ta składnia jest teraz obsługiwana:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Ten atrybut `SomeThingAboutFieldAttribute` jest stosowany do pola zapasowego wygenerowanego `SomeProperty`przez kompilator dla. Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w C# przewodniku programowania.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in`wczesnego przeciążania metody

Po dodaniu modyfikatora argumentu te dwie metody spowodują niejednoznaczność: `in`

```csharp
static void M(S arg);
static void M(in S arg);
```

Teraz Przeciążenie wartości (najpierw w poprzednim przykładzie) przeciążenia jest lepsze niż wersja odwołania do tylko do odczytu. Aby wywołać wersję z argumentem odwołania tylko do odczytu, należy dołączyć `in` modyfikator podczas wywoływania metody.

> [!NOTE]
> Ta implementacja została zaimplementowana jako Poprawka błędu. To nie jest już niejednoznaczne nawet w przypadku wersji językowej ustawionej na "7,2".

Aby uzyskać więcej informacji, zobacz artykuł dotyczący [ `in` modyfikatora parametru](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozszerzone zmienne wyrażeń w inicjatorach

Składnia dodana w C# 7,0 umożliwia `out` przełączenie deklaracji zmiennych w taki sposób, aby zawierały inicjatory pól, inicjatory właściwości, inicjatory konstruktorów i klauzule zapytań. Umożliwia to wykonywanie kodu, takiego jak Poniższy przykład:

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>Ulepszone kandydujące metody rozwiązywania przeciążenia

W każdej wersji reguły rozpoznawania przeciążenia zostały zaktualizowane w celu rozwiązania sytuacji, w których niejednoznaczne wywołania metod mają oczywisty wybór. W tej wersji dodano trzy nowe reguły, które ułatwiają wybór oczywisty przez kompilator:

1. Gdy grupa metod zawiera zarówno wystąpienie, jak i statyczne elementy członkowskie, kompilator odrzuca elementy członkowskie wystąpienia, jeśli metoda została wywołana bez odbiorcy wystąpienia lub kontekstu. Kompilator odrzuca statyczne elementy członkowskie, jeśli metoda została wywołana z odbiornikiem wystąpienia. Gdy nie ma odbiornika, kompilator zawiera tylko statyczne elementy członkowskie w kontekście statycznym, w przeciwnym razie elementy członkowskie statyczne i wystąpienia. Gdy odbiorca jest niejednoznacznie wystąpieniem lub typem, kompilator zawiera oba te elementy. Statyczny kontekst, w którym niejawny `this` odbiornik wystąpienia nie może być używany, zawiera treść członków, gdzie nie `this` jest zdefiniowany, takich jak statyczne elementy członkowskie, a także `this` miejsca, w których nie można ich używać, takich jak inicjatory pola i Konstruktor-inicjatory.
1. Gdy grupa metod zawiera kilka metod ogólnych, których argumenty typu nie spełniają ograniczeń, te elementy członkowskie są usuwane z zestawu kandydatów.
1. Dla konwersji grup metod, metody kandydujące, których typ zwracany nie jest zgodny z typem zwracanym delegata, są usuwane z zestawu.

Ta zmiana zostanie wykorzystana tylko dlatego, że w przypadku niejednoznacznych przeciążeń metod znajdziesz mniej błędów kompilatora, gdy masz pewność, która metoda jest lepsza.

## <a name="new-compiler-options"></a>Nowe opcje kompilatora

Nowe opcje kompilatora obsługują nowe scenariusze kompilacji i DevOps dla C# programów.

### <a name="public-or-open-source-signing"></a>Podpisywanie publiczne lub Open Source

Opcja `-publicsign` kompilatora instruuje kompilator do podpisania zestawu przy użyciu klucza publicznego. Zestaw jest oznaczony jako podpisany, ale podpis jest pobierany z klucza publicznego. Ta opcja umożliwia tworzenie podpisanych zestawów z projektów typu "open source" przy użyciu klucza publicznego.

Aby uzyskać więcej informacji, zobacz [publicsign opcji kompilatora](../language-reference/compiler-options/publicsign-compiler-option.md) .

### <a name="pathmap"></a>elemencie pathmap

Opcja `-pathmap` kompilatora instruuje kompilator, aby zamieniać ścieżki źródłowe ze środowiska kompilacji z zamapowanymi ścieżkami źródłowymi. Opcja steruje ścieżką źródłową zapisaną przez kompilator do plików PDB lub <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>dla. `-pathmap`

Aby uzyskać więcej informacji, zobacz [elemencie pathmap opcji kompilatora](../language-reference/compiler-options/pathmap-compiler-option.md) .
