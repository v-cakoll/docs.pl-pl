---
title: Co nowego w języku C# 7.3
description: Omówienie nowych funkcji w języku C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 570da53059242c0242609ddcba5cb23f1728aa9f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873803"
---
# <a name="whats-new-in-c-73"></a>Co nowego w języku C# 7.3

Istnieją dwa główne motywy do wersji języka C# 7.3. Jeden motyw zawiera funkcje, które umożliwiają bezpieczne kod był warto wiedzieć, jak niebezpieczny kod. Drugi motyw zawiera przyrostowe ulepszenia istniejących funkcji. Ponadto w tej wersji dodano nowe opcje kompilatora.

Następujące nowe funkcje obsługują motyw lepszą wydajność dla bezpiecznego kodu:

- Można uzyskać dostęp do pól stałej bez przypinania.
- Można ponownie przypisać `ref` zmiennych lokalnych.
- Możesz użyć inicjatory w `stackalloc` tablic.
- Możesz użyć `fixed` instrukcje z dowolnego typu, który obsługuje wzorzec.
- Możesz użyć dodatkowe ograniczenia ogólne.

Wprowadzono następujące ulepszenia istniejących funkcji:

- Możesz przetestować `==` i `!=` z typami spójnej kolekcji.
- Można używać zmiennych wyrażenia w większej liczby lokalizacji.
- Atrybuty mogą dołączyć do pola zapasowego właściwości zaimplementowane automatycznie.
- Metoda rozdzielczość w przypadku różnią się argumentów `in` została ulepszona.
- Rozpoznanie przeciążenia ma teraz mniejszą liczbę przypadków niejednoznaczne.

Nowe opcje kompilatora są:

- `-publicsign` Aby włączyć, Otwórz źródło oprogramowania (OSS) podpisywanie zestawów.
- `-pathmap` Aby zapewnić mapowanie katalogi źródłowe.

W dalszej części tego artykułu zawiera szczegółowe informacje i łącza, aby dowiedzieć się więcej na temat ulepszenia.

## <a name="enabling-more-efficient-safe-code"></a>Włączanie bardziej wydajne, bezpieczne kodu

Można napisać kod C#, bezpiecznie wykonujący oraz niebezpieczny kod. Bezpieczny kod pozwala uniknąć klasy błędów, takich jak przepełnienia buforu, wskaźniki stray i inne błędy dostępu do pamięci. Te nowe funkcje rozszerzyć możliwości weryfikowalny kod bezpieczny. Dokładamy wszelkich starań, można zapisać więcej kodu przy użyciu bezpiecznych konstrukcji. Te funkcje ułatwią.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Indeksowanie `fixed` pola nie jest wymagane, przypinanie

Należy wziąć pod uwagę tej struktury:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

We wcześniejszych wersjach języka C#, potrzebna do przypięcia zmienną dostęp do jednej z wartości całkowitych, które są częścią `myFixedField`. Poniższy kod kompiluje się teraz w kontekście bezpiecznego:

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

Zmienna `p` uzyskuje dostęp do jednego elementu `myFixedField`. Nie trzeba deklarować oddzielnego `int*` zmiennej. Należy zauważyć, że w dalszym ciągu konieczny `unsafe` kontekstu. We wcześniejszych wersjach języka C# należy zadeklarować wskaźnik drugiego stały:

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

Aby uzyskać więcej informacji, zobacz artykuł [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md).

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` Zmienne lokalne może zostać ponownie przypisane

Teraz `ref` lokalne może zostać ponownie przypisane do odwoływania się do innego wystąpienia zostały już zainicjowane. Poniższy kod powoduje kompilację:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Aby uzyskać więcej informacji, zobacz artykuł [ `ref` zwraca i `ref` lokalne](../programming-guide/classes-and-structs/ref-returns.md)oraz artykuł dotyczący [ `foreach` ](../language-reference/keywords/foreach-in.md).

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` tablice obsługują inicjatorów

Dotąd istniała określ wartości dla elementów w tablicy, podczas jego inicjowania:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Teraz takiej samej składni można zastosować do tablic, które są zadeklarowane za pomocą `stackalloc`:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Aby uzyskać więcej informacji, zobacz [ `stackalloc` instrukcji](../language-reference/keywords/stackalloc.md) artykułu w dokumentacji języka.

### <a name="more-types-support-the-fixed-statement"></a>Obsługuje większą liczbę typów `fixed` — instrukcja

`fixed` Instrukcja obsługiwana ograniczony zestaw typów. Począwszy od C# 7.3, dowolny typ, który zawiera `GetPinnableReference()` metodę, która zwraca `ref T` lub `ref readonly T` może być `fixed`. Dodanie tej funkcji oznacza, że `fixed` mogą być używane z <xref:System.Span%601?displayProperty=nameWithType> i typów pokrewnych.

Aby uzyskać więcej informacji, zobacz [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md) artykułu w dokumentacji języka.

### <a name="enhanced-generic-constraints"></a>Rozszerzone ograniczenia ogólne

Teraz można określić typ <xref:System.Enum?displayProperty=nameWithType> lub <xref:System.Delegate?displayProperty=nameWithType> jako klasa bazowa ograniczeń dla parametru typu.

Można również użyć nowej `unmanaged` ograniczenie, aby określić, że parametr typu musi być **niezarządzany typ**. **Niezarządzany typ** to typ, który nie jest typem odwołania i nie zawiera żadnych typu odwołania na każdym poziomie zagnieżdżania.

Aby uzyskać więcej informacji, zobacz artykuły na [ `where` ograniczenia ogólne](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczenia dotyczące parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).

Dodanie tych warunków ograniczających do istniejących typów jest [niezgodna zmiana](version-update-considerations.md#incompatible-changes). Zamknięte typy rodzajowe mogą już nie spełnia te nowe ograniczenia.

## <a name="make-existing-features-better"></a>Ulepszyć istniejące funkcje

Drugi motyw zawiera ulepszenia funkcji w języku. Te funkcje Zwiększ produktywność, podczas zapisywania C#.

### <a name="tuples-support--and-"></a>Obsługuje krotek `==` i `!=`

C# spójna kolekcja znajdująca się typy obsługują teraz `==` i `!=`. Aby uzyskać więcej informacji, zobacz obejmujący sekcję [równości](../tuples.md#equality-and-tuples) w artykule na [krotek](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Dołącz atrybuty do pola zapasowego właściwości zaimplementowane automatycznie

Ta składnia jest teraz obsługiwane:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Ten atrybut `SomeThingAboutFieldAttribute` jest stosowany do pola pomocniczego wygenerowanego przez kompilator dla `SomeProperty`. Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w Podręczniku programowania C#.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` tiebreaker rozdzielczość przeciążenia metody

Gdy `in` dodano modyfikator argument, te dwie metody mogłoby spowodować niejednoznaczność:

```csharp
static void M(S arg);
static void M(in S arg);
```

Teraz przez wartość (najpierw w poprzednim przykładzie) przeciążenie jest lepsze niż w wersji odniesienia tylko do odczytu. Aby wywołać wersję z argument odwołania tylko do odczytu, należy dołączyć `in` modyfikator podczas wywoływania metody.

> [!NOTE]
> Było to wdrożone jako naprawienia błędu. To nie jest już jest niejednoznaczny nawet w przypadku wersji językowej ustawiona na "7.2".

Aby uzyskać więcej informacji, zobacz artykuł [ `in` modyfikator parametru](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozszerzanie zmiennych wyrażenia w inicjatorach

Dodano w języku C# 7.0, aby zezwolić na składnię `out` deklaracje zmiennej został rozszerzony do uwzględnienia inicjatorów pola, właściwości, inicjatory konstruktora, a klauzul zapytania. Umożliwia stosowanie kodu, takich jak na poniższym przykładzie:

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

### <a name="improved-overload-candidates"></a>Kandydujące dla przeciążenia ulepszone

W każdej wersji reguł rozwiązywania przeciążenia zaktualizowani adres sytuacjom, w których niejednoznacznego wywołania metod mają "oczywistym" wyborem. W tej wersji dodano trzy nowe reguły, aby ułatwić kompilatora wybierz oczywistym wyborem:

1. Podczas grupy metod zawiera wystąpienie i statyczne elementy członkowskie, kompilator odrzuca składowych wystąpienia, jeśli metoda została wywołana bez odbiornika wystąpienia lub kontekstu. Kompilator odrzuca statycznych elementów członkowskich, jeśli metoda została wywołana z odbiornikiem wystąpienia. Gdy nie ma żadnych odbiorcy, kompilator zawiera tylko statyczne elementy członkowskie w ramach kontekstu statycznego, w przeciwnym razie statycznych i elementów członkowskich wystąpienia. Odbiornik ambiguously to wystąpienie lub typu, kompilator zawiera zarówno. Kontekstu statycznego, gdy ukrytego `this` odbiorcy wystąpienia nie można użyć, zawiera treść elementów członkowskich, gdzie nie `this` jest zdefiniowany, takie jak statyczne elementy członkowskie, a także miejsc, gdzie `this` nie można użyć, takie jak inicjatorów pola i Inicjatory konstruktora.
1. Jeśli grupa metoda zawiera niektóre metody rodzajowe, której argumenty typu nie spełnia ich ograniczenia, te elementy członkowskie są usuwane z zestawu Release candidate.
1. Dla metody konwersji z grupy metody Release candidate, którego typem zwracanym nie zgodny z pełnomocnika Zwróć typ są usuwane z zestawu.

Tylko zauważysz tej zmiany, ponieważ można znaleźć mniej błędów kompilatora przeciążenia metody niejednoznaczne po upewnieniu się, która metoda jest lepsza.

## <a name="new-compiler-options"></a>Nowe opcje kompilatora

Nowe opcje kompilatora obsługuje nową kompilację i scenariuszy DevOps dla programów C#.

### <a name="public-or-open-source-signing"></a>Publiczne lub podpisywania "Open Source"

`-publicsign` — Opcja kompilatora instruuje kompilator, aby podpisać zestaw za pomocą klucza publicznego. Zestaw jest oznaczony jako podpisany, ale podpis jest pobierana z kluczem publicznym. Ta opcja umożliwia tworzenie zestawów podpisanych z projektów typu open source za pomocą klucza publicznego.

Aby uzyskać więcej informacji, zobacz [— opcja kompilatora - publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) artykułu.

### <a name="pathmap"></a>elemencie pathmap

`-pathmap` — Opcja kompilatora instruuje kompilator, aby zastąpić ścieżkami źródłowymi w środowisku kompilacji ze ścieżkami źródłowymi zamapowany. `-pathmap` Opcja kontroluje ścieżki źródłowej, napisane przez kompilator dla plików PDB lub do <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.

Aby uzyskać więcej informacji, zobacz [elemencie pathmap — opcja kompilatora](../language-reference/compiler-options/pathmap-compiler-option.md) artykułu.
