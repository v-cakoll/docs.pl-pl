---
title: Co nowego w Języku C# 7.3
description: Przegląd nowych funkcji w języku C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204556"
---
# <a name="whats-new-in-c-73"></a>Co nowego w Języku C# 7.3

Istnieją dwa główne tematy do wersji C# 7.3. Jeden motyw zawiera funkcje, które umożliwiają bezpiecznego kodu, aby być tak działającym jak niebezpieczny kod. Drugi motyw zapewnia przyrostowe ulepszenia istniejących funkcji. Ponadto w tej wersji dodano nowe opcje kompilatora.

Następujące nowe funkcje obsługują temat lepszej wydajności bezpiecznego kodu:

- Dostęp do stałych pól można uzyskać bez przypinania.
- Można ponownie przypisać `ref` zmienne lokalne.
- Inicjatorów `stackalloc` można używać w tablicach.
- Instrukcje można `fixed` używać z dowolnego typu, który obsługuje wzorzec.
- Można użyć dodatkowych ograniczeń ogólnych.

Wprowadzono następujące ulepszenia istniejących funkcji:

- Można `==` przetestować `!=` i z typami krotki.
- Zmiennych wyrażeń można używać w większej liczbie lokalizacji.
- Atrybuty można dołączyć do pola zapasowego właściwości implementowanych automatycznie.
- Poprawiono rozpoznawanie `in` metod, gdy argumenty różnią się.
- Rozdzielczość przeciążenia ma teraz mniej niejednoznacznych przypadków.

Nowe opcje kompilatora to:

- `-publicsign`, aby włączyć podpisywanie zestawów przez oprogramowanie Open Source (OSS).
- `-pathmap`, aby zapewnić mapowanie dla katalogów źródłowych.

W dalszej części tego artykułu zawiera szczegółowe informacje i łącza, aby dowiedzieć się więcej o każdej z ulepszeń. Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`

1. Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *próbek.*
1. Uruchom polecenie `dotnet try`.

## <a name="enabling-more-efficient-safe-code"></a>Włączanie bardziej wydajnego bezpiecznego kodu

Powinno być w stanie napisać kod C# bezpiecznie, który wykonuje, jak również niebezpieczny kod. Bezpieczny kod pozwala uniknąć klas błędów, takich jak przekroczenia buforu, wskaźniki bezpańskich i inne błędy dostępu do pamięci. Te nowe funkcje rozszerzają możliwości weryfikowalnego bezpiecznego kodu. Staraj się napisać więcej kodu przy użyciu bezpiecznych konstrukcji. Te funkcje sprawiają, że łatwiej.

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>Pola `fixed` indeksowania nie wymagają przypinania

Rozważmy tę strukturę:

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

We wcześniejszych wersjach języka C#, trzeba było przypiąć zmienną, `myFixedField`aby uzyskać dostęp do jednej z liczb całkowitych, które są częścią programu . Teraz poniższy kod kompiluje bez `p` przypinania zmiennej wewnątrz oddzielnej `fixed` instrukcji:

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

Zmienna `p` uzyskuje dostęp `myFixedField`do jednego elementu w programie . Nie trzeba deklarować oddzielnej `int*` zmiennej. Należy pamiętać, że `unsafe` nadal potrzebujesz kontekstu. We wcześniejszych wersjach języka C#należy zadeklarować drugi stały wskaźnik:

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

Aby uzyskać więcej informacji, [ `fixed` ](../language-reference/keywords/fixed-statement.md)zobacz artykuł na instrukcji .

### <a name="ref-local-variables-may-be-reassigned"></a>`ref`zmienne lokalne mogą być ponownie przypisywane

Teraz `ref` mieszkańcy mogą być ponownie przypisane do odwoływania się do różnych wystąpień po zainicjowaniu. Następujący kod teraz kompiluje:

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

Aby uzyskać więcej informacji, zobacz artykuł na [`foreach`](../language-reference/keywords/foreach-in.md) [ `ref` temat zwrotów i `ref` mieszkańców](../programming-guide/classes-and-structs/ref-returns.md)oraz artykuł na temat .

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc`tablice obsługują inicjatory

Można było określić wartości elementów w tablicy podczas inicjowania:

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

Teraz tę samą składnię można zastosować do `stackalloc`tablic zadeklarowanych za pomocą:

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

Aby uzyskać więcej informacji, zobacz artykuł [ `stackalloc` operatora.](../language-reference/operators/stackalloc.md)

### <a name="more-types-support-the-fixed-statement"></a>Więcej typów `fixed` obsługuje instrukcję

Instrukcja `fixed` obsługiwane ograniczony zestaw typów. Począwszy od języka C# 7.3, każdy typ, który `GetPinnableReference()` zawiera metodę, która zwraca lub `ref T` `ref readonly T` może być `fixed`. Dodanie tej funkcji `fixed` oznacza, <xref:System.Span%601?displayProperty=nameWithType> że można używać z typami pokrewnymi i pokrewnymi.

Aby uzyskać więcej informacji, zobacz artykuł [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md) w odwołaniu do języka.

### <a name="enhanced-generic-constraints"></a>Rozszerzone ograniczenia ogólne

Teraz można określić <xref:System.Enum?displayProperty=nameWithType> typ <xref:System.Delegate?displayProperty=nameWithType> lub jako ograniczenia klasy podstawowej dla parametru typu.

Można również użyć `unmanaged` nowego ograniczenia, aby określić, że parametr typu musi być [typem niepodlegającym](../language-reference/builtin-types/unmanaged-types.md)null.

Aby uzyskać więcej informacji, zobacz artykuły dotyczące [ `where` ogólnych ograniczeń](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczeń parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).

Dodanie tych ograniczeń do istniejących typów jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes). Zamknięte typy ogólne mogą już nie spełniać tych nowych ograniczeń.

## <a name="make-existing-features-better"></a>Ulepszanie istniejących funkcji

Drugi motyw zawiera ulepszenia funkcji w języku. Te funkcje zwiększają produktywność podczas pisania języka C#.

### <a name="tuples-support--and-"></a>Obsługa `==` krotek i`!=`

Typy krotki Języka `==` C# obsługują teraz i `!=`. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [równości](../tuples.md#equality-and-tuples) w artykule na [krotek](../tuples.md).

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>Dołączanie atrybutów do pól zapasowych dla właściwości implementowanych automatycznie

Ta składnia jest teraz obsługiwana:

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

Atrybut `SomeThingAboutFieldAttribute` jest stosowany do kompilatora `SomeProperty`wygenerowanego pola zapasowego dla . Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w przewodniku programowania C#.

### <a name="in-method-overload-resolution-tiebreaker"></a>`in`metoda przeciążenia rozdzielczość tiebreaker

Po `in` dodaniu modyfikatorargumentu te dwie metody mogą spowodować niejednoznaczność:

```csharp
static void M(S arg);
static void M(in S arg);
```

Teraz według wartości (pierwszy w poprzednim przykładzie) przeciążenie jest lepsze niż przez readonly wersji referencyjnej. Aby wywołać wersję z argumentem odwołania tylko `in` do odczytu, należy dołączyć modyfikator podczas wywoływania metody.

> [!NOTE]
> Zostało to zaimplementowane jako poprawka błędu. Nie jest to już dwuznaczne, nawet w wersji językowej ustawionej na "7.2".

Aby uzyskać więcej informacji, zobacz artykuł na [ `in` modyfikator parametrów](../language-reference/keywords/in-parameter-modifier.md).

### <a name="extend-expression-variables-in-initializers"></a>Rozszerzanie zmiennych wyrażenia w inicjatorach

Składnia dodana w języku C# 7.0, aby umożliwić `out` deklaracje zmiennych została rozszerzona o inicjatory pól, inicjatory właściwości, inicjatory konstruktorów i klauzule kwerendy. Umożliwia kod, taki jak w poniższym przykładzie:

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

W każdej wersji reguły rozpoznawania przeciążenia są aktualizowane w celu rozwiązania sytuacji, w których wywołania metod niejednoznacznych mają wybór "oczywisty". W tej wersji dodano trzy nowe reguły, które pomogą kompilatorowi wybrać oczywisty wybór:

1. Gdy grupa metod zawiera zarówno wystąpienia, jak i statyczne elementy członkowskie, kompilator odrzuca elementy członkowskie wystąpienia, jeśli metoda została wywołana bez odbiornika wystąpienia lub kontekstu. Kompilator odrzuca elementy członkowskie statyczne, jeśli metoda została wywołana za pomocą odbiornika wystąpienia. Gdy nie ma odbiornika, kompilator zawiera tylko elementy statyczne w kontekście statycznym, w przeciwnym razie zarówno statyczne i wystąpienia elementów członkowskich. Gdy odbiornik jest niejednoznacznie wystąpienie lub typ, kompilator zawiera zarówno. Kontekst statyczny, `this` w którym nie można użyć niejawnego `this` odbiornika wystąpienia, obejmuje treść elementów członkowskich, w których nie jest zdefiniowany, takich jak statycznych elementów członkowskich, a także miejsca, w których `this` nie można użyć, takich jak inicjatory pola i inicjatory konstruktorów.
1. Gdy grupa metod zawiera niektóre metody ogólne, których argumenty typu nie spełniają ich ograniczeń, te elementy członkowskie są usuwane z zestawu kandydatów.
1. W przypadku konwersji grupy metod metody, których typ zwracany nie jest zgodny z typem zwracanym pełnomocnika, są usuwane z zestawu.

Zauważysz tylko tę zmianę, ponieważ znajdziesz mniej błędów kompilatora dla przeciążenia metody niejednoznaczne, gdy masz pewność, która metoda jest lepsza.

## <a name="new-compiler-options"></a>Nowe opcje kompilatora

Nowe opcje kompilatora obsługują nowe scenariusze kompilacji i DevOps dla programów Języka C#.

### <a name="public-or-open-source-signing"></a>Podpisywanie publiczne lub open source

Opcja `-publicsign` kompilatora instruuje kompilatordo podpisania zestawu przy użyciu klucza publicznego. Zestaw jest oznaczony jako podpisany, ale podpis jest pobierany z klucza publicznego. Ta opcja umożliwia tworzenie podpisanych zestawów z projektów open source przy użyciu klucza publicznego.

Aby uzyskać więcej informacji, zobacz [-publicsign kompilator a opcja](../language-reference/compiler-options/publicsign-compiler-option.md) artykułu.

### <a name="pathmap"></a>mapa ścieżki

Opcja `-pathmap` kompilatora instruuje kompilator, aby zastąpić ścieżki źródłowe ze środowiska kompilacji z mapowanych ścieżek źródłowych. Opcja `-pathmap` steruje ścieżką źródłową zapisaną przez kompilator do plików PDB lub dla <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>pliku .

Aby uzyskać więcej informacji, zobacz [-pathmap kompilator a](../language-reference/compiler-options/pathmap-compiler-option.md) opcja artykułu.
