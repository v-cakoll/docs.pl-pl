---
title: Co nowego w C# 7,3
description: Omówienie nowych funkcji w C# 7,3
ms.date: 05/16/2018
ms.openlocfilehash: ba4cea302d91b395e88940d087fcaed306920840
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204556"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="a89e0-103">Co nowego w C# 7,3</span><span class="sxs-lookup"><span data-stu-id="a89e0-103">What's new in C# 7.3</span></span>

<span data-ttu-id="a89e0-104">W C# wersji 7,3 istnieją dwa główne motywy.</span><span class="sxs-lookup"><span data-stu-id="a89e0-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="a89e0-105">Jeden motyw udostępnia funkcje, które umożliwiają bezpieczny kod, tak jak kod niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="a89e0-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="a89e0-106">Drugi motyw zawiera ulepszenia przyrostowe istniejących funkcji.</span><span class="sxs-lookup"><span data-stu-id="a89e0-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="a89e0-107">Ponadto w tej wersji dodano nowe opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a89e0-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="a89e0-108">Poniższe nowe funkcje obsługują motyw lepszej wydajności dla bezpiecznego kodu:</span><span class="sxs-lookup"><span data-stu-id="a89e0-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="a89e0-109">Można uzyskać dostęp do stałych pól bez przypinania.</span><span class="sxs-lookup"><span data-stu-id="a89e0-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="a89e0-110">Można zmienić przypisanie `ref` zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a89e0-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="a89e0-111">Inicjatorów można używać na `stackalloc` tablicach.</span><span class="sxs-lookup"><span data-stu-id="a89e0-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="a89e0-112">Instrukcji `fixed` można użyć dla dowolnego typu, który obsługuje wzorzec.</span><span class="sxs-lookup"><span data-stu-id="a89e0-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="a89e0-113">Można użyć dodatkowych ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="a89e0-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="a89e0-114">W istniejących funkcjach wprowadzono następujące ulepszenia:</span><span class="sxs-lookup"><span data-stu-id="a89e0-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="a89e0-115">Można testować `==` i `!=` z typami krotek.</span><span class="sxs-lookup"><span data-stu-id="a89e0-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="a89e0-116">Zmiennych wyrażeń można używać w większej liczbie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a89e0-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="a89e0-117">Możesz dołączyć atrybuty do pola zapasowego właściwości, które są implementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a89e0-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="a89e0-118">Ulepszono metodę rozpoznawania argumentów, które różnią się `in`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="a89e0-119">Rozwiązanie przeciążenia ma teraz mniej niejednoznaczne przypadki.</span><span class="sxs-lookup"><span data-stu-id="a89e0-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="a89e0-120">Nowe opcje kompilatora są następujące:</span><span class="sxs-lookup"><span data-stu-id="a89e0-120">The new compiler options are:</span></span>

- <span data-ttu-id="a89e0-121">`-publicsign`, aby włączyć podpisywanie zestawów przez oprogramowanie typu Open Source (OSS).</span><span class="sxs-lookup"><span data-stu-id="a89e0-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="a89e0-122">`-pathmap` w celu zapewnienia mapowania katalogów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="a89e0-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="a89e0-123">Pozostała część tego artykułu zawiera szczegółowe informacje i linki, aby dowiedzieć się więcej na temat poszczególnych ulepszeń.</span><span class="sxs-lookup"><span data-stu-id="a89e0-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="a89e0-124">Te funkcje można eksplorować w środowisku za pomocą narzędzia globalnego `dotnet try`:</span><span class="sxs-lookup"><span data-stu-id="a89e0-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="a89e0-125">Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="a89e0-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="a89e0-126">Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="a89e0-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="a89e0-127">Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="a89e0-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="a89e0-128">Uruchom `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="a89e0-129">Włączanie bardziej wydajnego bezpiecznego kodu</span><span class="sxs-lookup"><span data-stu-id="a89e0-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="a89e0-130">Powinien być w stanie bezpiecznie napisać C# kod, który wykonuje, a także kod niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="a89e0-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="a89e0-131">Bezpieczny kod unika klas błędów, takich jak przekroczenia buforu, nieużywane wskaźniki i inne błędy dostępu do pamięci.</span><span class="sxs-lookup"><span data-stu-id="a89e0-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="a89e0-132">Te nowe funkcje rozszerzają możliwości zweryfikowania bezpiecznego kodu.</span><span class="sxs-lookup"><span data-stu-id="a89e0-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="a89e0-133">Staraj się pisać więcej kodu przy użyciu bezpiecznych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="a89e0-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="a89e0-134">Te funkcje ułatwiają to.</span><span class="sxs-lookup"><span data-stu-id="a89e0-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="a89e0-135">Indeksowanie pól `fixed` nie wymaga przypinania</span><span class="sxs-lookup"><span data-stu-id="a89e0-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="a89e0-136">Rozważmy tę strukturę:</span><span class="sxs-lookup"><span data-stu-id="a89e0-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="a89e0-137">We wcześniejszych wersjach programu C#wymagało przypinania zmiennej w celu uzyskania dostępu do jednej z liczb całkowitych, które są częścią `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="a89e0-138">Teraz Poniższy kod kompiluje bez przypinania zmiennej `p` wewnątrz oddzielnej instrukcji `fixed`:</span><span class="sxs-lookup"><span data-stu-id="a89e0-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="a89e0-139">Zmienna `p` uzyskuje dostęp do jednego elementu w `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="a89e0-140">Nie musisz deklarować oddzielnej zmiennej `int*`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="a89e0-141">Pamiętaj, że nadal potrzebujesz kontekstu `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="a89e0-142">We wcześniejszych wersjach programu C#należy zadeklarować drugi stały wskaźnik:</span><span class="sxs-lookup"><span data-stu-id="a89e0-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="a89e0-143">Aby uzyskać więcej informacji, zobacz artykuł w [instrukcji`fixed`](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a89e0-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="a89e0-144">`ref` zmienne lokalne mogą zostać ponownie przypisane</span><span class="sxs-lookup"><span data-stu-id="a89e0-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="a89e0-145">Teraz `ref` lokalne mogą zostać ponownie przypisane, aby odwoływać się do różnych wystąpień po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="a89e0-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="a89e0-146">Poniższy kod jest teraz kompilowany:</span><span class="sxs-lookup"><span data-stu-id="a89e0-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="a89e0-147">Aby uzyskać więcej informacji, zobacz artykuł na temat [`ref` zwraca i `ref` lokalnych](../programming-guide/classes-and-structs/ref-returns.md)i artykułu w [`foreach`](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="a89e0-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="a89e0-148">Tablice `stackalloc` obsługują inicjatory</span><span class="sxs-lookup"><span data-stu-id="a89e0-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="a89e0-149">Po zainicjowaniu można określić wartości dla elementów w tablicy:</span><span class="sxs-lookup"><span data-stu-id="a89e0-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="a89e0-150">Teraz tę samą składnię można zastosować do tablic, które są zadeklarowane za pomocą `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="a89e0-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="a89e0-151">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [operatorów`stackalloc`](../language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="a89e0-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="a89e0-152">Więcej typów obsługuje instrukcję `fixed`</span><span class="sxs-lookup"><span data-stu-id="a89e0-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="a89e0-153">Instrukcja `fixed` obsługuje ograniczony zestaw typów.</span><span class="sxs-lookup"><span data-stu-id="a89e0-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="a89e0-154">Począwszy od C# 7,3, może być `fixed`dowolnego typu, który zawiera metodę `GetPinnableReference()`, która zwraca `ref T` lub `ref readonly T`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="a89e0-155">Dodanie tej funkcji oznacza, że `fixed` mogą być używane z <xref:System.Span%601?displayProperty=nameWithType> i powiązane typy.</span><span class="sxs-lookup"><span data-stu-id="a89e0-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="a89e0-156">Aby uzyskać więcej informacji, zobacz artykuł [`fixed` instrukcji](../language-reference/keywords/fixed-statement.md) w dokumentacji języka.</span><span class="sxs-lookup"><span data-stu-id="a89e0-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="a89e0-157">Ulepszone ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="a89e0-157">Enhanced generic constraints</span></span>

<span data-ttu-id="a89e0-158">Teraz można określić typ <xref:System.Enum?displayProperty=nameWithType> lub <xref:System.Delegate?displayProperty=nameWithType> jako ograniczenia klasy bazowej dla parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a89e0-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="a89e0-159">Można również użyć nowego ograniczenia `unmanaged`, aby określić, że parametr typu musi być [typem niezarządzanym](../language-reference/builtin-types/unmanaged-types.md)null.</span><span class="sxs-lookup"><span data-stu-id="a89e0-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="a89e0-160">Aby uzyskać więcej informacji, zobacz artykuły dotyczące [`where` ograniczeń ogólnych](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczeń dla parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a89e0-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="a89e0-161">Dodanie tych ograniczeń do istniejących typów jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="a89e0-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="a89e0-162">Zamknięte typy ogólne nie mogą już odpowiadać tym nowym ograniczeniom.</span><span class="sxs-lookup"><span data-stu-id="a89e0-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="a89e0-163">Ulepszanie istniejących funkcji</span><span class="sxs-lookup"><span data-stu-id="a89e0-163">Make existing features better</span></span>

<span data-ttu-id="a89e0-164">Drugi motyw zawiera ulepszenia funkcji w języku.</span><span class="sxs-lookup"><span data-stu-id="a89e0-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="a89e0-165">Te funkcje zwiększają produktywność C#podczas pisania.</span><span class="sxs-lookup"><span data-stu-id="a89e0-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="a89e0-166">Krotki obsługują `==` i `!=`</span><span class="sxs-lookup"><span data-stu-id="a89e0-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="a89e0-167">Typy C# krotek obsługują teraz `==` i `!=`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="a89e0-168">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [równości](../tuples.md#equality-and-tuples) w artykule na temat [krotek](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="a89e0-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="a89e0-169">Dołącz atrybuty do pól zapasowych dla automatycznie implementowanych właściwości</span><span class="sxs-lookup"><span data-stu-id="a89e0-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="a89e0-170">Ta składnia jest teraz obsługiwana:</span><span class="sxs-lookup"><span data-stu-id="a89e0-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="a89e0-171">Atrybut `SomeThingAboutFieldAttribute` jest stosowany do pola zapasowego wygenerowanego przez kompilator dla `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="a89e0-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="a89e0-172">Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w C# przewodniku programowania.</span><span class="sxs-lookup"><span data-stu-id="a89e0-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="a89e0-173">wczesnego `in` przeciążania metody</span><span class="sxs-lookup"><span data-stu-id="a89e0-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="a89e0-174">Po dodaniu modyfikatora argumentu `in`, te dwie metody spowodują niejednoznaczność:</span><span class="sxs-lookup"><span data-stu-id="a89e0-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="a89e0-175">Teraz Przeciążenie wartości (najpierw w poprzednim przykładzie) przeciążenia jest lepsze niż wersja odwołania do tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="a89e0-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="a89e0-176">Aby wywołać wersję z argumentem odwołania tylko do odczytu, należy uwzględnić modyfikator `in` podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="a89e0-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="a89e0-177">Ta implementacja została zaimplementowana jako Poprawka błędu.</span><span class="sxs-lookup"><span data-stu-id="a89e0-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="a89e0-178">To nie jest już niejednoznaczne nawet w przypadku wersji językowej ustawionej na "7,2".</span><span class="sxs-lookup"><span data-stu-id="a89e0-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="a89e0-179">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [modyfikatora parametru`in`](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="a89e0-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="a89e0-180">Rozszerzone zmienne wyrażeń w inicjatorach</span><span class="sxs-lookup"><span data-stu-id="a89e0-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="a89e0-181">Składnia dodana w C# 7,0 zezwalająca na `out` deklaracji zmiennych została rozszerzona w celu uwzględnienia inicjatorów pól, inicjatorów właściwości, inicjatorów konstruktora i klauzul zapytania.</span><span class="sxs-lookup"><span data-stu-id="a89e0-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="a89e0-182">Umożliwia to wykonywanie kodu, takiego jak Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="a89e0-182">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="a89e0-183">Ulepszone kandydujące metody rozwiązywania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="a89e0-183">Improved overload candidates</span></span>

<span data-ttu-id="a89e0-184">W każdej wersji reguły rozpoznawania przeciążenia zostały zaktualizowane w celu rozwiązania sytuacji, w których niejednoznaczne wywołania metod mają oczywisty wybór.</span><span class="sxs-lookup"><span data-stu-id="a89e0-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="a89e0-185">W tej wersji dodano trzy nowe reguły, które ułatwiają wybór oczywisty przez kompilator:</span><span class="sxs-lookup"><span data-stu-id="a89e0-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="a89e0-186">Gdy grupa metod zawiera zarówno wystąpienie, jak i statyczne elementy członkowskie, kompilator odrzuca elementy członkowskie wystąpienia, jeśli metoda została wywołana bez odbiorcy wystąpienia lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a89e0-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="a89e0-187">Kompilator odrzuca statyczne elementy członkowskie, jeśli metoda została wywołana z odbiornikiem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a89e0-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="a89e0-188">Gdy nie ma odbiornika, kompilator zawiera tylko statyczne elementy członkowskie w kontekście statycznym, w przeciwnym razie elementy członkowskie statyczne i wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a89e0-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="a89e0-189">Gdy odbiorca jest niejednoznacznie wystąpieniem lub typem, kompilator zawiera oba te elementy.</span><span class="sxs-lookup"><span data-stu-id="a89e0-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="a89e0-190">Statyczny kontekst, w którym niejawny odbiornik `this` wystąpienia nie może być używany, zawiera treść elementów członkowskich, w których nie zdefiniowano `this`, takich jak statyczne elementy członkowskie, a także miejsc, w których nie można używać `this`, takich jak inicjatory pól i konstruktory.</span><span class="sxs-lookup"><span data-stu-id="a89e0-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="a89e0-191">Gdy grupa metod zawiera kilka metod ogólnych, których argumenty typu nie spełniają ograniczeń, te elementy członkowskie są usuwane z zestawu kandydatów.</span><span class="sxs-lookup"><span data-stu-id="a89e0-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="a89e0-192">Dla konwersji grup metod, metody kandydujące, których typ zwracany nie jest zgodny z typem zwracanym delegata, są usuwane z zestawu.</span><span class="sxs-lookup"><span data-stu-id="a89e0-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="a89e0-193">Ta zmiana zostanie wykorzystana tylko dlatego, że w przypadku niejednoznacznych przeciążeń metod znajdziesz mniej błędów kompilatora, gdy masz pewność, która metoda jest lepsza.</span><span class="sxs-lookup"><span data-stu-id="a89e0-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="a89e0-194">Nowe opcje kompilatora</span><span class="sxs-lookup"><span data-stu-id="a89e0-194">New compiler options</span></span>

<span data-ttu-id="a89e0-195">Nowe opcje kompilatora obsługują nowe scenariusze kompilacji i DevOps dla C# programów.</span><span class="sxs-lookup"><span data-stu-id="a89e0-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="a89e0-196">Podpisywanie publiczne lub Open Source</span><span class="sxs-lookup"><span data-stu-id="a89e0-196">Public or Open Source signing</span></span>

<span data-ttu-id="a89e0-197">Opcja kompilatora `-publicsign` instruuje kompilator do podpisania zestawu przy użyciu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a89e0-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="a89e0-198">Zestaw jest oznaczony jako podpisany, ale podpis jest pobierany z klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a89e0-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="a89e0-199">Ta opcja umożliwia tworzenie podpisanych zestawów z projektów typu "open source" przy użyciu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="a89e0-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="a89e0-200">Aby uzyskać więcej informacji, zobacz [publicsign opcji kompilatora](../language-reference/compiler-options/publicsign-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="a89e0-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="a89e0-201">elemencie pathmap</span><span class="sxs-lookup"><span data-stu-id="a89e0-201">pathmap</span></span>

<span data-ttu-id="a89e0-202">Opcja kompilatora `-pathmap` instruuje kompilator, aby zamieniać ścieżki źródłowe ze środowiska kompilacji z zamapowanymi ścieżkami źródłowymi.</span><span class="sxs-lookup"><span data-stu-id="a89e0-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="a89e0-203">Opcja `-pathmap` steruje ścieżką źródłową zapisaną przez kompilator do plików PDB lub <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a89e0-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="a89e0-204">Aby uzyskać więcej informacji, zobacz [elemencie pathmap opcji kompilatora](../language-reference/compiler-options/pathmap-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="a89e0-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
