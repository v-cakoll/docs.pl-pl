---
title: Nowości w języku C# 7.3
description: Omówienie nowych funkcji w języku C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 1d1aca2564c26315cf8b3af60a863ea3c70fd385
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827101"
---
# <a name="whats-new-in-c-73"></a>Nowości w języku C# 7.3

Istnieją dwa główne kompozycje do wersji 7.3 C#. Jeden motyw zawiera funkcje, które umożliwiają bezpieczne kodu jako wydajności jako niebezpieczny kod. Drugi motyw zawiera przyrostowe ulepszenia istniejących funkcji. Ponadto nowe opcje kompilatora zostały dodane w tej wersji.

Następujące nowe funkcje obsługę motywu lepszą wydajność bezpiecznego kodu:

- Dostępne pola stałej bez przypinania.
- Można ponownie przypisać `ref` zmiennych lokalnych.
- Możesz użyć inicjatory w `stackalloc` tablic.
- Można użyć `fixed` instrukcji z dowolnego typu, który obsługuje wzorca.
- Można użyć dodatkowych ograniczeń ogólnych.

Wprowadzono następujące ulepszenia istniejących funkcji:

- Możesz przetestować `==` i `!=` z typami spójnej kolekcji.
- Można używać zmiennych wyrażenie więcej lokalizacji.
- Atrybuty może dołączyć do pola zapasowy właściwości zaimplementowane automatycznie.
- Metoda rozdzielczość w przypadku różnią się argumentów `in` została ulepszona.
- Rozpoznanie przeciążenia ma mniejszą liczbę przypadków niejednoznaczne.

Dostępne są nowe opcje kompilatora:

- `-publicsign` Aby włączyć, otwórz źródła oprogramowania wyszczególnione podpisywanie zestawów.
- `-pathmap` Aby zapewnić mapowania dla katalogów źródła.

W dalszej części tego artykułu zawiera informacje i linki, aby dowiedzieć się więcej na temat ulepszeń.

## <a name="enabling-more-performant-safe-code"></a>Włączanie więcej wydajność bezpiecznego kodu.

Można napisać kod C#, bezpiecznie wykonująca oraz niebezpieczny kod. Bezpieczne kodu pozwala uniknąć klasy błędów, takich jak przepełnienia buforu, wskaźniki stray i inne błędy dostępu do pamięci. Te nowe funkcje rozszerzyć możliwości zweryfikowania kodu bezpieczne. Starań, aby zapisać więcej kodu przy użyciu konstrukcji bezpieczne. Te funkcje upewnij, że łatwiejsze.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Indeksowanie `fixed` pól nie wymaga przypinanie

Należy wziąć pod uwagę tej struktury:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

We wcześniejszych wersjach języka C#, trzeba przypiąć zmiennej dostęp do jednej z liczb całkowitych, które są częścią `myFixedField`. Poniższy kod kompiluje się teraz w kontekście bezpiecznego:

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

Zmienna `p` uzyskuje dostęp do jednego elementu `myFixedField`. Nie należy deklarować oddzielnej `int*` zmiennej. Należy pamiętać, że nadal potrzebujesz `unsafe` kontekstu. We wcześniejszych wersjach języka C# należy zadeklarować drugi stałej wskaźnika:

```csharp
class C
{
    static S s = new S();

    public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

Aby uzyskać więcej informacji, zobacz artykuł na [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` Zmienne lokalne mogą zostać przypisane na nowo

Teraz `ref` zmienne lokalne mogą zostać przypisany odwoływać się do innego wystąpienia zostały już zainicjowane. Poniższy kod tworzy jedynie:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Aby uzyskać więcej informacji, zobacz artykuł na [ `ref` zwraca i `ref` zmiennych lokalnych](../programming-guide/classes-and-structs/ref-returns.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` tablice obsługują inicjatory

Flaguje do określania wartości dla elementów w tablicy, gdy należy zainicjować:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Teraz, można zastosować tej samej składni do tablic zadeklarowanych z `stackalloc`:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Aby uzyskać więcej informacji, zobacz [ `stackalloc` instrukcji](../language-reference/keywords/stackalloc.md) artykułu w language reference.

### <a name="more-types-support-the-fixed-statement"></a>Obsługuje większą liczbę typów `fixed` — instrukcja

`fixed` Ograniczony zestaw typów obsługuje tej instrukcji. Począwszy od C# 7.3, dowolnego typu, który zawiera `GetPinnableReference()` metodę zwracającą `ref T` lub `ref readonly T` może być `fixed`. Dodanie tej funkcji oznacza, że `fixed` mogą być używane z <xref:System.Span%601?displayProperty=nameWithType> i powiązanych typów.

Aby uzyskać więcej informacji, zobacz [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md) artykułu w language reference.

### <a name="enhanced-generic-constraints"></a>Rozszerzone ograniczenia ogólne

Teraz można określić typ <xref:System.Enum?displayProperty=nameWithType> lub <xref:System.Delegate?displayProperty=nameWithType> jako klasa podstawowa ograniczenia dla parametru typu.

Można również użyć nowej `unmanaged` ograniczenie, aby określić, że musi być parametrem typu **niezarządzany typ**. **Niezarządzany typ** jest typ, który nie jest typem referencyjnym i nie zawiera żadnego typu odwołania na dowolnym poziomie zagnieżdżenia.

Aby uzyskać więcej informacji, zobacz artykuły w [ `where` ograniczenia ogólne](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczenia dotyczące parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="make-existing-features-better"></a>Ulepszać istniejących funkcji

Drugi motyw zawiera ulepszenia funkcji w tym języku. Te funkcje zwiększenie produktywności podczas pisania C#.

### <a name="tuples-support--and-"></a>Obsługuje krotek `==` i `!=`

Teraz obsługiwane typy krotki C# `==` i `!=`. Aby uzyskać więcej informacji, zobacz sekcja obejmujący [równości](../tuples.md#equality-and-tuples) w artykule na [krotek](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Dołącz atrybuty do pola zapasowego dla właściwości zaimplementowane automatycznie

Ta składnia jest teraz obsługiwana:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Atrybut `SomeThingAboutFieldAttribute` jest stosowany do wygenerowanego przez kompilator pole zapasowe dla `SomeProperty`. Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w Podręczniku programowania C#.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` tiebreaker rozpoznawanie przeciążenia — metoda

Gdy `in` modyfikator argument został dodany, te dwie metody spowodowałoby niejednoznaczności:

```csharp
static void M(S arg);
static void M(in S arg);
```

Teraz przez wartość (najpierw w poprzednim przykładzie) jest lepszym rozwiązaniem niż przeciążenie przez wersję odwołania tylko do odczytu. Aby wywołać wersji z argumentem odwołania tylko do odczytu, należy uwzględnić `in` modyfikator podczas wywoływania metody.

> [!NOTE]
> To zostało zaimplementowane jako poprawkę. To już jest niejednoznaczny nawet w przypadku wersji językowej ustawioną wartość "7.2".

Aby uzyskać więcej informacji, zobacz artykuł na [ `in` modyfikator parametru](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozszerzanie zmiennych wyrażenie w inicjatory

Dodano w języku C# w wersji 7.0 umożliwia składnię `out` do uwzględnienia inicjatorów pola, właściwości inicjatory, inicjatory konstruktora, a zapytanie z klauzulami został rozszerzony deklaracji zmiennych. Umożliwia ona kodu na przykład w poniższym przykładzie:

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
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>Ulepszone przeciążenie kandydujące

W każdej wersji reguł rozwiązywania przeciążenia zostać zaktualizowane do sytuacji adres, gdzie niejednoznaczne wywołania metod mają "oczywiste" choice. Ta wersja dodaje pomocy kompilatora oczywiste wyboru pobranie trzech nowych reguł:

1. Gdy grupa metod zawiera wystąpienie i statyczne elementy członkowskie, kompilator odrzuca elementów członkowskich wystąpienia metody został wywołany bez wystąpienie odbiornika lub kontekstu. Kompilator odrzuca statyczne elementy członkowskie, jeśli metoda została wywołana z odbiornikiem wystąpienia. Gdy nie ma żadnych odbiornik, kompilator zawiera tylko statyczne elementy członkowskie w kontekstu statycznego, w przeciwnym razie obu statyczna i wystąpienia elementów członkowskich. Odbiornik ambiguously jest wystąpień lub typu, kompilator obejmuje zarówno. Kontekstu statycznego, jeśli niejawne `this` odbiornika wystąpienia nie można użyć, zawiera treść elementów członkowskich, jeśli nie `this` jest zdefiniowany, takie jak statyczne elementy członkowskie, a także miejsc, gdzie `this` nie można użyć, takich jak inicjatorów pola i Inicjatory konstruktora.
1. Jeśli grupa metod zawiera niektóre metody ogólne, którego argumenty typu nie spełniają ich ograniczenia, tych elementów członkowskich są usuwane z zestawu kandydata.
1. Dla metody konwersji grupy metod których typ zwracany nie zgodny z delegata zwracać typu są usuwane z zestawu.

Ta zmiana można zauważyć tylko, ponieważ można znaleźć mniej błędy kompilatora przeciążenia metody niejednoznaczne po upewnieniu się, która metoda jest lepszym rozwiązaniem.

## <a name="new-compiler-options"></a>Nowe opcje kompilatora

Nowe opcje kompilatora obsługują nową kompilację i scenariuszy opracowywania oprogramowania dla programów C#.

### <a name="public-or-open-source-signing"></a>Publicznego lub typu Open Source podpisywania

`-publicsign` — Opcja kompilatora instruuje kompilator, aby podpisać zestawu za pomocą klucza publicznego. Zestaw jest oznaczony jako podpisany, ale sygnatura jest pobierana z kluczem publicznym. Ta opcja umożliwia tworzenie podpisanych zestawów z projektów open source za pomocą klucza publicznego.

Aby uzyskać więcej informacji, zobacz [— opcja kompilatora - publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) artykułu.

### <a name="pathmap"></a>pathmap

`-pathmap` — Opcja kompilatora instruuje kompilator, aby zastąpić ścieżki źródłowej ze środowiska kompilacji źródła zamapowanej ścieżki. `-pathmap` Opcja steruje napisane przez kompilator do plików PDB lub dla ścieżki źródłowej <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Aby uzyskać więcej informacji, zobacz [— opcja kompilatora - pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) artykułu.
