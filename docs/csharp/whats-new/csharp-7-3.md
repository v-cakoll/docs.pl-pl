---
title: Nowości w języku C# 7.3
description: Omówienie nowych funkcji w języku C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: 96aa0290299755c00cbc698297661bd847ed4221
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948501"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="89d55-103">Nowości w języku C# 7.3</span><span class="sxs-lookup"><span data-stu-id="89d55-103">What's new in C# 7.3</span></span>

<span data-ttu-id="89d55-104">Istnieją dwa główne kompozycje do wersji 7.3 C#.</span><span class="sxs-lookup"><span data-stu-id="89d55-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="89d55-105">Jeden motyw zawiera funkcje, które umożliwiają bezpieczne kodu jako wydajności jako niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="89d55-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="89d55-106">Drugi motyw zawiera przyrostowe ulepszenia istniejących funkcji.</span><span class="sxs-lookup"><span data-stu-id="89d55-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="89d55-107">Ponadto nowe opcje kompilatora zostały dodane w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="89d55-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="89d55-108">Następujące nowe funkcje obsługę motywu lepszą wydajność bezpiecznego kodu:</span><span class="sxs-lookup"><span data-stu-id="89d55-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="89d55-109">Dostępne pola stałej bez przypinania.</span><span class="sxs-lookup"><span data-stu-id="89d55-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="89d55-110">Można ponownie przypisać `ref` zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="89d55-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="89d55-111">Możesz użyć inicjatory w `stackalloc` tablic.</span><span class="sxs-lookup"><span data-stu-id="89d55-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="89d55-112">Można użyć `fixed` instrukcji z dowolnego typu, który obsługuje wzorca.</span><span class="sxs-lookup"><span data-stu-id="89d55-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="89d55-113">Można użyć dodatkowych ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="89d55-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="89d55-114">Wprowadzono następujące ulepszenia istniejących funkcji:</span><span class="sxs-lookup"><span data-stu-id="89d55-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="89d55-115">Możesz przetestować `==` i `!=` z typami spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="89d55-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="89d55-116">Można używać zmiennych wyrażenie więcej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="89d55-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="89d55-117">Atrybuty może dołączyć do pola zapasowy właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="89d55-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="89d55-118">Metoda rozdzielczość w przypadku różnią się argumentów `in` została ulepszona.</span><span class="sxs-lookup"><span data-stu-id="89d55-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="89d55-119">Rozpoznanie przeciążenia ma mniejszą liczbę przypadków niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="89d55-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="89d55-120">Dostępne są nowe opcje kompilatora:</span><span class="sxs-lookup"><span data-stu-id="89d55-120">The new compiler options are:</span></span>

- <span data-ttu-id="89d55-121">`-publicsign` Aby włączyć, otwórz źródła oprogramowania wyszczególnione podpisywanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="89d55-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="89d55-122">`-pathmap` Aby zapewnić mapowania dla katalogów źródła.</span><span class="sxs-lookup"><span data-stu-id="89d55-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="89d55-123">W dalszej części tego artykułu zawiera informacje i linki, aby dowiedzieć się więcej na temat ulepszeń.</span><span class="sxs-lookup"><span data-stu-id="89d55-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-performant-safe-code"></a><span data-ttu-id="89d55-124">Włączanie więcej wydajność bezpiecznego kodu.</span><span class="sxs-lookup"><span data-stu-id="89d55-124">Enabling more performant safe code</span></span>

<span data-ttu-id="89d55-125">Można napisać kod C#, bezpiecznie wykonująca oraz niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="89d55-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="89d55-126">Bezpieczne kodu pozwala uniknąć klasy błędów, takich jak przepełnienia buforu, wskaźniki stray i inne błędy dostępu do pamięci.</span><span class="sxs-lookup"><span data-stu-id="89d55-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="89d55-127">Te nowe funkcje rozszerzyć możliwości zweryfikowania kodu bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="89d55-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="89d55-128">Starań, aby zapisać więcej kodu przy użyciu konstrukcji bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="89d55-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="89d55-129">Te funkcje upewnij, że łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="89d55-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="89d55-130">Indeksowanie `fixed` pól nie wymaga przypinanie</span><span class="sxs-lookup"><span data-stu-id="89d55-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="89d55-131">Należy wziąć pod uwagę tej struktury:</span><span class="sxs-lookup"><span data-stu-id="89d55-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="89d55-132">We wcześniejszych wersjach języka C#, trzeba przypiąć zmiennej dostęp do jednej z liczb całkowitych, które są częścią `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="89d55-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="89d55-133">Poniższy kod kompiluje się teraz w kontekście bezpiecznego:</span><span class="sxs-lookup"><span data-stu-id="89d55-133">Now, the following code compiles in a safe context:</span></span>

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

<span data-ttu-id="89d55-134">Zmienna `p` uzyskuje dostęp do jednego elementu `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="89d55-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="89d55-135">Nie należy deklarować oddzielnej `int*` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="89d55-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="89d55-136">Należy pamiętać, że nadal potrzebujesz `unsafe` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="89d55-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="89d55-137">We wcześniejszych wersjach języka C# należy zadeklarować drugi stałej wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="89d55-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="89d55-138">Aby uzyskać więcej informacji, zobacz artykuł na [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="89d55-138">Fore more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="89d55-139">`ref` Zmienne lokalne mogą zostać przypisane na nowo</span><span class="sxs-lookup"><span data-stu-id="89d55-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="89d55-140">Teraz `ref` zmienne lokalne mogą zostać przypisany odwoływać się do innego wystąpienia zostały już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="89d55-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="89d55-141">Poniższy kod tworzy jedynie:</span><span class="sxs-lookup"><span data-stu-id="89d55-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="89d55-142">Aby uzyskać więcej informacji, zobacz artykuł na [ `ref` zwraca i `ref` zmiennych lokalnych](../programming-guide/classes-and-structs/ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="89d55-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="89d55-143">`stackalloc` tablice obsługują inicjatory</span><span class="sxs-lookup"><span data-stu-id="89d55-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="89d55-144">Flaguje do określania wartości dla elementów w tablicy, gdy należy zainicjować:</span><span class="sxs-lookup"><span data-stu-id="89d55-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="89d55-145">Teraz, można zastosować tej samej składni do tablic zadeklarowanych z `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="89d55-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="89d55-146">Aby uzyskać więcej informacji, zobacz [ `stackalloc` instrukcji](../language-reference/keywords/stackalloc.md) artykułu w language reference.</span><span class="sxs-lookup"><span data-stu-id="89d55-146">For more information, see the [`stackalloc` statement](../language-reference/keywords/stackalloc.md) article in the language reference.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="89d55-147">Obsługuje większą liczbę typów `fixed` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="89d55-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="89d55-148">`fixed` Ograniczony zestaw typów obsługuje tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="89d55-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="89d55-149">Począwszy od C# 7.3, dowolnego typu, który zawiera `GetPinnableReference()` metodę zwracającą `ref T` lub `ref readonly T` może być `fixed`.</span><span class="sxs-lookup"><span data-stu-id="89d55-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="89d55-150">Dodanie tej funkcji oznacza, że `fixed` mogą być używane z <xref:System.Span%601?displayProperty=nameWithType> i powiązanych typów.</span><span class="sxs-lookup"><span data-stu-id="89d55-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="89d55-151">Aby uzyskać więcej informacji, zobacz [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md) artykułu w language reference.</span><span class="sxs-lookup"><span data-stu-id="89d55-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="89d55-152">Rozszerzone ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="89d55-152">Enhanced generic constraints</span></span>

<span data-ttu-id="89d55-153">Teraz można określić typ <xref:System.Enum?displayProperty=nameWithType> lub <xref:System.Delegate?displayProperty=nameWithType> jako klasa podstawowa ograniczenia dla parametru typu.</span><span class="sxs-lookup"><span data-stu-id="89d55-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="89d55-154">Można również użyć nowej `unmanaged` ograniczenie, aby określić, że musi być parametrem typu **niezarządzany typ**.</span><span class="sxs-lookup"><span data-stu-id="89d55-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="89d55-155">**Niezarządzany typ** jest typ, który nie jest typem referencyjnym i nie zawiera żadnego typu odwołania na dowolnym poziomie zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="89d55-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="89d55-156">Aby uzyskać więcej informacji, zobacz artykuły w [ `where` ograniczenia ogólne](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczenia dotyczące parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="89d55-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="89d55-157">Ulepszać istniejących funkcji</span><span class="sxs-lookup"><span data-stu-id="89d55-157">Make existing features better</span></span>

<span data-ttu-id="89d55-158">Drugi motyw zawiera ulepszenia funkcji w tym języku.</span><span class="sxs-lookup"><span data-stu-id="89d55-158">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="89d55-159">Te funkcje zwiększenie produktywności podczas pisania C#.</span><span class="sxs-lookup"><span data-stu-id="89d55-159">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="89d55-160">Obsługuje krotek `==` i `!=`</span><span class="sxs-lookup"><span data-stu-id="89d55-160">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="89d55-161">Teraz obsługiwane typy krotki C# `==` i `!=`.</span><span class="sxs-lookup"><span data-stu-id="89d55-161">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="89d55-162">Aby uzyskać więcej informacji, zobacz sekcja obejmujący [równości](../tuples.md#equality-and-tuples) w artykule na [krotek](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="89d55-162">Fore more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="89d55-163">Dołącz atrybuty do pola zapasowego dla właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="89d55-163">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="89d55-164">Ta składnia jest teraz obsługiwana:</span><span class="sxs-lookup"><span data-stu-id="89d55-164">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="89d55-165">Atrybut `SomeThingAboutFieldAttribute` jest stosowany do wygenerowanego przez kompilator pole zapasowe dla `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="89d55-165">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="89d55-166">Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w Podręczniku programowania C#.</span><span class="sxs-lookup"><span data-stu-id="89d55-166">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="89d55-167">`in` tiebreaker rozpoznawanie przeciążenia — metoda</span><span class="sxs-lookup"><span data-stu-id="89d55-167">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="89d55-168">Gdy `in` modyfikator argument został dodany, te dwie metody spowodowałoby niejednoznaczności:</span><span class="sxs-lookup"><span data-stu-id="89d55-168">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="89d55-169">Teraz przez wartość (najpierw w poprzednim przykładzie) jest lepszym rozwiązaniem niż przeciążenie przez wersję odwołania tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="89d55-169">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="89d55-170">Aby wywołać wersji z argumentem odwołania tylko do odczytu, należy uwzględnić `in` modyfikator podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="89d55-170">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="89d55-171">To zostało zaimplementowane jako poprawkę.</span><span class="sxs-lookup"><span data-stu-id="89d55-171">This was implemented as a bug fix.</span></span> <span data-ttu-id="89d55-172">To już jest niejednoznaczny nawet w przypadku wersji językowej ustawioną wartość "7.2".</span><span class="sxs-lookup"><span data-stu-id="89d55-172">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="89d55-173">Aby uzyskać więcej informacji, zobacz artykuł na [ `in` modyfikator parametru](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="89d55-173">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="89d55-174">Rozszerzanie zmiennych wyrażenie w inicjatory</span><span class="sxs-lookup"><span data-stu-id="89d55-174">Extend expression variables in initializers</span></span>

<span data-ttu-id="89d55-175">Dodano w języku C# w wersji 7.0 umożliwia składnię `out` do uwzględnienia inicjatorów pola, właściwości inicjatory, inicjatory konstruktora, a zapytanie z klauzulami został rozszerzony deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="89d55-175">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="89d55-176">Umożliwia ona kodu na przykład w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="89d55-176">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="89d55-177">Ulepszone przeciążenie kandydujące</span><span class="sxs-lookup"><span data-stu-id="89d55-177">Improved overload candidates</span></span>

<span data-ttu-id="89d55-178">W każdej wersji reguł rozwiązywania przeciążenia zostać zaktualizowane do sytuacji adres, gdzie niejednoznaczne wywołania metod mają "oczywiste" choice.</span><span class="sxs-lookup"><span data-stu-id="89d55-178">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="89d55-179">Ta wersja dodaje pomocy kompilatora oczywiste wyboru pobranie trzech nowych reguł:</span><span class="sxs-lookup"><span data-stu-id="89d55-179">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="89d55-180">Gdy grupa metod zawiera wystąpienie i statyczne elementy członkowskie, kompilator odrzuca elementów członkowskich wystąpienia metody został wywołany bez wystąpienie odbiornika lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="89d55-180">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="89d55-181">Kompilator odrzuca statyczne elementy członkowskie, jeśli metoda została wywołana z odbiornikiem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="89d55-181">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="89d55-182">Gdy nie ma żadnych odbiornik, kompilator zawiera tylko statyczne elementy członkowskie w kontekstu statycznego, w przeciwnym razie obu statyczna i wystąpienia elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="89d55-182">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="89d55-183">Odbiornik ambiguously jest wystąpień lub typu, kompilator obejmuje zarówno.</span><span class="sxs-lookup"><span data-stu-id="89d55-183">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="89d55-184">Kontekstu statycznego, jeśli niejawne `this` odbiornika wystąpienia nie można użyć, zawiera treść elementów członkowskich, jeśli nie `this` jest zdefiniowany, takie jak statyczne elementy członkowskie, a także miejsc, gdzie `this` nie można użyć, takich jak inicjatorów pola i Inicjatory konstruktora.</span><span class="sxs-lookup"><span data-stu-id="89d55-184">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="89d55-185">Jeśli grupa metod zawiera niektóre metody ogólne, którego argumenty typu nie spełniają ich ograniczenia, tych elementów członkowskich są usuwane z zestawu kandydata.</span><span class="sxs-lookup"><span data-stu-id="89d55-185">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="89d55-186">Dla metody konwersji grupy metod których typ zwracany nie zgodny z delegata zwracać typu są usuwane z zestawu.</span><span class="sxs-lookup"><span data-stu-id="89d55-186">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="89d55-187">Ta zmiana można zauważyć tylko, ponieważ można znaleźć mniej błędy kompilatora przeciążenia metody niejednoznaczne po upewnieniu się, która metoda jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="89d55-187">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="89d55-188">Nowe opcje kompilatora</span><span class="sxs-lookup"><span data-stu-id="89d55-188">New compiler options</span></span>

<span data-ttu-id="89d55-189">Nowe opcje kompilatora obsługują nową kompilację i scenariuszy opracowywania oprogramowania dla programów C#.</span><span class="sxs-lookup"><span data-stu-id="89d55-189">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="89d55-190">Publicznego lub typu Open Source podpisywania</span><span class="sxs-lookup"><span data-stu-id="89d55-190">Public or Open Source signing</span></span>

<span data-ttu-id="89d55-191">`-publicsign` — Opcja kompilatora instruuje kompilator, aby podpisać zestawu za pomocą klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="89d55-191">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="89d55-192">Zestaw jest oznaczony jako podpisany, ale sygnatura jest pobierana z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="89d55-192">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="89d55-193">Ta opcja umożliwia tworzenie podpisanych zestawów z projektów open source za pomocą klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="89d55-193">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="89d55-194">Aby uzyskać więcej informacji, zobacz [— opcja kompilatora - publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="89d55-194">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="89d55-195">pathmap</span><span class="sxs-lookup"><span data-stu-id="89d55-195">pathmap</span></span>

<span data-ttu-id="89d55-196">`-pathmap` — Opcja kompilatora instruuje kompilator, aby zastąpić ścieżki źródłowej ze środowiska kompilacji źródła zamapowanej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="89d55-196">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="89d55-197">`-pathmap` Opcja steruje napisane przez kompilator do plików PDB lub dla ścieżki źródłowej <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="89d55-197">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="89d55-198">Aby uzyskać więcej informacji, zobacz [— opcja kompilatora - pathmap](../language-reference/compiler-options/pathmap-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="89d55-198">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
