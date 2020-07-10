---
title: Co nowego w języku C# 7,3
description: Omówienie nowych funkcji w języku C# 7,3
ms.date: 05/16/2018
ms.openlocfilehash: cd8f554516fb5078d9d2ed1eec787f36e8f4c7a7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174760"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="82b07-103">Co nowego w języku C# 7,3</span><span class="sxs-lookup"><span data-stu-id="82b07-103">What's new in C# 7.3</span></span>

<span data-ttu-id="82b07-104">Istnieją dwa główne motywy w wersji C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="82b07-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="82b07-105">Jeden motyw udostępnia funkcje, które umożliwiają bezpieczny kod, tak jak kod niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="82b07-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="82b07-106">Drugi motyw zawiera ulepszenia przyrostowe istniejących funkcji.</span><span class="sxs-lookup"><span data-stu-id="82b07-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="82b07-107">Ponadto w tej wersji dodano nowe opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="82b07-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="82b07-108">Poniższe nowe funkcje obsługują motyw lepszej wydajności dla bezpiecznego kodu:</span><span class="sxs-lookup"><span data-stu-id="82b07-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="82b07-109">Można uzyskać dostęp do stałych pól bez przypinania.</span><span class="sxs-lookup"><span data-stu-id="82b07-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="82b07-110">Zmienne lokalne można przypisywać ponownie `ref` .</span><span class="sxs-lookup"><span data-stu-id="82b07-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="82b07-111">Inicjatorów można używać w `stackalloc` tablicach.</span><span class="sxs-lookup"><span data-stu-id="82b07-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="82b07-112">Można używać `fixed` instrukcji z dowolnym typem, który obsługuje wzorzec.</span><span class="sxs-lookup"><span data-stu-id="82b07-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="82b07-113">Można użyć dodatkowych ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="82b07-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="82b07-114">W istniejących funkcjach wprowadzono następujące ulepszenia:</span><span class="sxs-lookup"><span data-stu-id="82b07-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="82b07-115">Można testować `==` i `!=` z typami krotek.</span><span class="sxs-lookup"><span data-stu-id="82b07-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="82b07-116">Zmiennych wyrażeń można używać w większej liczbie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="82b07-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="82b07-117">Możesz dołączyć atrybuty do pola zapasowego właściwości, które są implementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="82b07-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="82b07-118">Ulepszono metodę rozdzielczości, gdy argumenty różnią się od `in` .</span><span class="sxs-lookup"><span data-stu-id="82b07-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="82b07-119">Rozwiązanie przeciążenia ma teraz mniej niejednoznaczne przypadki.</span><span class="sxs-lookup"><span data-stu-id="82b07-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="82b07-120">Nowe opcje kompilatora są następujące:</span><span class="sxs-lookup"><span data-stu-id="82b07-120">The new compiler options are:</span></span>

- <span data-ttu-id="82b07-121">`-publicsign`Aby włączyć podpisywanie zestawów przez oprogramowanie typu Open Source (OSS).</span><span class="sxs-lookup"><span data-stu-id="82b07-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="82b07-122">`-pathmap`w celu zapewnienia mapowania dla katalogów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="82b07-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="82b07-123">Pozostała część tego artykułu zawiera szczegółowe informacje i linki, aby dowiedzieć się więcej na temat poszczególnych ulepszeń.</span><span class="sxs-lookup"><span data-stu-id="82b07-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="82b07-124">Te funkcje można eksplorować w środowisku za pomocą `dotnet try` Narzędzia globalnego:</span><span class="sxs-lookup"><span data-stu-id="82b07-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="82b07-125">Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="82b07-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="82b07-126">Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="82b07-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="82b07-127">Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="82b07-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="82b07-128">Uruchom polecenie `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="82b07-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="82b07-129">Włączanie bardziej wydajnego bezpiecznego kodu</span><span class="sxs-lookup"><span data-stu-id="82b07-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="82b07-130">Należy mieć możliwość bezpiecznego pisania kodu w języku C#, który wykonuje, a także kod niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="82b07-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="82b07-131">Bezpieczny kod unika klas błędów, takich jak przekroczenia buforu, nieużywane wskaźniki i inne błędy dostępu do pamięci.</span><span class="sxs-lookup"><span data-stu-id="82b07-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="82b07-132">Te nowe funkcje rozszerzają możliwości zweryfikowania bezpiecznego kodu.</span><span class="sxs-lookup"><span data-stu-id="82b07-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="82b07-133">Staraj się pisać więcej kodu przy użyciu bezpiecznych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="82b07-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="82b07-134">Te funkcje ułatwiają to.</span><span class="sxs-lookup"><span data-stu-id="82b07-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="82b07-135">Pola indeksowania nie `fixed` wymagają przypinania</span><span class="sxs-lookup"><span data-stu-id="82b07-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="82b07-136">Rozważmy tę strukturę:</span><span class="sxs-lookup"><span data-stu-id="82b07-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="82b07-137">We wcześniejszych wersjach języka C# wymagało przypinania zmiennej w celu uzyskania dostępu do jednej z liczb całkowitych, które są częścią `myFixedField` .</span><span class="sxs-lookup"><span data-stu-id="82b07-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="82b07-138">Teraz Poniższy kod kompiluje bez przypinania zmiennej `p` wewnątrz oddzielnej `fixed` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="82b07-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="82b07-139">Zmienna `p` uzyskuje dostęp do jednego elementu w `myFixedField` .</span><span class="sxs-lookup"><span data-stu-id="82b07-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="82b07-140">Nie musisz deklarować odrębnej `int*` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="82b07-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="82b07-141">Pamiętaj, że nadal potrzebujesz `unsafe` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="82b07-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="82b07-142">We wcześniejszych wersjach języka C# należy zadeklarować drugi stały wskaźnik:</span><span class="sxs-lookup"><span data-stu-id="82b07-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="82b07-143">Aby uzyskać więcej informacji, zobacz artykuł na temat [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="82b07-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="82b07-144">`ref`zmienne lokalne mogą zostać ponownie przypisane</span><span class="sxs-lookup"><span data-stu-id="82b07-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="82b07-145">Teraz elementy `ref` lokalne mogą zostać ponownie przypisane, aby odwoływać się do różnych wystąpień po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="82b07-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="82b07-146">Poniższy kod jest teraz kompilowany:</span><span class="sxs-lookup"><span data-stu-id="82b07-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="82b07-147">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [ `ref` zwrotów i elementów `ref` lokalnych](../programming-guide/classes-and-structs/ref-returns.md)oraz artykuł w artykule [`foreach`](../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="82b07-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="82b07-148">`stackalloc`Tablice obsługują inicjatory</span><span class="sxs-lookup"><span data-stu-id="82b07-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="82b07-149">Po zainicjowaniu można określić wartości dla elementów w tablicy:</span><span class="sxs-lookup"><span data-stu-id="82b07-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="82b07-150">Teraz tę samą składnię można zastosować do tablic, które są zadeklarowane za pomocą `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="82b07-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="82b07-151">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [ `stackalloc` operatorów](../language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="82b07-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="82b07-152">Więcej typów obsługuje `fixed` instrukcja</span><span class="sxs-lookup"><span data-stu-id="82b07-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="82b07-153">`fixed`Instrukcja obsługuje ograniczony zestaw typów.</span><span class="sxs-lookup"><span data-stu-id="82b07-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="82b07-154">Począwszy od języka C# 7,3, dowolnego typu, który zawiera `GetPinnableReference()` metodę zwracającą `ref T` lub `ref readonly T` może być `fixed` .</span><span class="sxs-lookup"><span data-stu-id="82b07-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="82b07-155">Dodanie tej funkcji oznacza, że `fixed` mogą być używane z <xref:System.Span%601?displayProperty=nameWithType> i powiązane typy.</span><span class="sxs-lookup"><span data-stu-id="82b07-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="82b07-156">Aby uzyskać więcej informacji, zobacz artykuł [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md) w dokumentacji języka.</span><span class="sxs-lookup"><span data-stu-id="82b07-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="82b07-157">Ulepszone ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="82b07-157">Enhanced generic constraints</span></span>

<span data-ttu-id="82b07-158">Teraz można określić typ <xref:System.Enum?displayProperty=nameWithType> lub <xref:System.Delegate?displayProperty=nameWithType> jako ograniczenia klasy bazowej dla parametru typu.</span><span class="sxs-lookup"><span data-stu-id="82b07-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="82b07-159">Można również użyć nowego `unmanaged` ograniczenia, aby określić, że parametr typu musi być [typem niezarządzanym](../language-reference/builtin-types/unmanaged-types.md)null.</span><span class="sxs-lookup"><span data-stu-id="82b07-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="82b07-160">Aby uzyskać więcej informacji, zobacz artykuły dotyczące [ `where` ograniczeń ogólnych](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczeń dla parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="82b07-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="82b07-161">Dodanie tych ograniczeń do istniejących typów jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="82b07-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="82b07-162">Zamknięte typy ogólne nie mogą już odpowiadać tym nowym ograniczeniom.</span><span class="sxs-lookup"><span data-stu-id="82b07-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="82b07-163">Ulepszanie istniejących funkcji</span><span class="sxs-lookup"><span data-stu-id="82b07-163">Make existing features better</span></span>

<span data-ttu-id="82b07-164">Drugi motyw zawiera ulepszenia funkcji w języku.</span><span class="sxs-lookup"><span data-stu-id="82b07-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="82b07-165">Te funkcje zwiększają produktywność podczas pisania języka C#.</span><span class="sxs-lookup"><span data-stu-id="82b07-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="82b07-166">Krotki obsługują `==` i`!=`</span><span class="sxs-lookup"><span data-stu-id="82b07-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="82b07-167">Typy krotek języka C# teraz obsługują `==` i `!=` .</span><span class="sxs-lookup"><span data-stu-id="82b07-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="82b07-168">Aby uzyskać więcej informacji, zobacz sekcję [równość krotki](../language-reference/builtin-types/value-tuples.md#tuple-equality) w artykule [typy krotek](../language-reference/builtin-types/value-tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="82b07-168">For more information, see the [Tuple equality](../language-reference/builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="82b07-169">Dołącz atrybuty do pól zapasowych dla automatycznie implementowanych właściwości</span><span class="sxs-lookup"><span data-stu-id="82b07-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="82b07-170">Ta składnia jest teraz obsługiwana:</span><span class="sxs-lookup"><span data-stu-id="82b07-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="82b07-171">Ten atrybut `SomeThingAboutFieldAttribute` jest stosowany do pola zapasowego wygenerowanego przez kompilator dla `SomeProperty` .</span><span class="sxs-lookup"><span data-stu-id="82b07-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="82b07-172">Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w Przewodnik programowania w języku C#.</span><span class="sxs-lookup"><span data-stu-id="82b07-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="82b07-173">`in`wczesnego przeciążania metody</span><span class="sxs-lookup"><span data-stu-id="82b07-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="82b07-174">Po `in` dodaniu modyfikatora argumentu te dwie metody spowodują niejednoznaczność:</span><span class="sxs-lookup"><span data-stu-id="82b07-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="82b07-175">Teraz Przeciążenie wartości (najpierw w poprzednim przykładzie) przeciążenia jest lepsze niż wersja odwołania do tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="82b07-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="82b07-176">Aby wywołać wersję z argumentem odwołania tylko do odczytu, należy dołączyć `in` modyfikator podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="82b07-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="82b07-177">Ta implementacja została zaimplementowana jako Poprawka błędu.</span><span class="sxs-lookup"><span data-stu-id="82b07-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="82b07-178">To nie jest już niejednoznaczne nawet w przypadku wersji językowej ustawionej na "7,2".</span><span class="sxs-lookup"><span data-stu-id="82b07-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="82b07-179">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [ `in` modyfikatora parametru](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="82b07-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="82b07-180">Rozszerzone zmienne wyrażeń w inicjatorach</span><span class="sxs-lookup"><span data-stu-id="82b07-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="82b07-181">Składnia dodana w języku C# 7,0 do zezwalania na `out` deklaracje zmiennych w celu uwzględnienia inicjatorów pól, inicjatorów właściwości, inicjatorów konstruktora i klauzul zapytania.</span><span class="sxs-lookup"><span data-stu-id="82b07-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="82b07-182">Umożliwia to wykonywanie kodu, takiego jak Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="82b07-182">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="82b07-183">Ulepszone kandydujące metody rozwiązywania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="82b07-183">Improved overload candidates</span></span>

<span data-ttu-id="82b07-184">W każdej wersji reguły rozpoznawania przeciążenia zostały zaktualizowane w celu rozwiązania sytuacji, w których niejednoznaczne wywołania metod mają oczywisty wybór.</span><span class="sxs-lookup"><span data-stu-id="82b07-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="82b07-185">W tej wersji dodano trzy nowe reguły, które ułatwiają wybór oczywisty przez kompilator:</span><span class="sxs-lookup"><span data-stu-id="82b07-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="82b07-186">Gdy grupa metod zawiera zarówno wystąpienie, jak i statyczne elementy członkowskie, kompilator odrzuca elementy członkowskie wystąpienia, jeśli metoda została wywołana bez odbiorcy wystąpienia lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="82b07-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="82b07-187">Kompilator odrzuca statyczne elementy członkowskie, jeśli metoda została wywołana z odbiornikiem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="82b07-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="82b07-188">Gdy nie ma odbiornika, kompilator zawiera tylko statyczne elementy członkowskie w kontekście statycznym, w przeciwnym razie elementy członkowskie statyczne i wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="82b07-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="82b07-189">Gdy odbiorca jest niejednoznacznie wystąpieniem lub typem, kompilator zawiera oba te elementy.</span><span class="sxs-lookup"><span data-stu-id="82b07-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="82b07-190">Statyczny kontekst, w którym niejawny `this` odbiornik wystąpienia nie może być używany, zawiera treść elementów członkowskich, gdzie nie `this` jest zdefiniowana, takich jak statyczne elementy członkowskie, a także miejsca, w których `this` nie można ich używać, takich jak inicjatory pól i konstruktory.</span><span class="sxs-lookup"><span data-stu-id="82b07-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="82b07-191">Gdy grupa metod zawiera kilka metod ogólnych, których argumenty typu nie spełniają ograniczeń, te elementy członkowskie są usuwane z zestawu kandydatów.</span><span class="sxs-lookup"><span data-stu-id="82b07-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="82b07-192">Dla konwersji grup metod, metody kandydujące, których typ zwracany nie jest zgodny z typem zwracanym delegata, są usuwane z zestawu.</span><span class="sxs-lookup"><span data-stu-id="82b07-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="82b07-193">Ta zmiana zostanie wykorzystana tylko dlatego, że w przypadku niejednoznacznych przeciążeń metod znajdziesz mniej błędów kompilatora, gdy masz pewność, która metoda jest lepsza.</span><span class="sxs-lookup"><span data-stu-id="82b07-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="82b07-194">Nowe opcje kompilatora</span><span class="sxs-lookup"><span data-stu-id="82b07-194">New compiler options</span></span>

<span data-ttu-id="82b07-195">Nowe opcje kompilatora obsługują nowe scenariusze kompilacji i DevOps dla programów w języku C#.</span><span class="sxs-lookup"><span data-stu-id="82b07-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="82b07-196">Podpisywanie publiczne lub Open Source</span><span class="sxs-lookup"><span data-stu-id="82b07-196">Public or Open Source signing</span></span>

<span data-ttu-id="82b07-197">`-publicsign`Opcja kompilatora instruuje kompilator do podpisania zestawu przy użyciu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="82b07-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="82b07-198">Zestaw jest oznaczony jako podpisany, ale podpis jest pobierany z klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="82b07-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="82b07-199">Ta opcja umożliwia tworzenie podpisanych zestawów z projektów typu "open source" przy użyciu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="82b07-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="82b07-200">Aby uzyskać więcej informacji, zobacz [publicsign opcji kompilatora](../language-reference/compiler-options/publicsign-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="82b07-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="82b07-201">elemencie pathmap</span><span class="sxs-lookup"><span data-stu-id="82b07-201">pathmap</span></span>

<span data-ttu-id="82b07-202">`-pathmap`Opcja kompilatora instruuje kompilator, aby zamieniać ścieżki źródłowe ze środowiska kompilacji z zamapowanymi ścieżkami źródłowymi.</span><span class="sxs-lookup"><span data-stu-id="82b07-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="82b07-203">`-pathmap`Opcja steruje ścieżką źródłową zapisaną przez kompilator do plików PDB lub dla <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> .</span><span class="sxs-lookup"><span data-stu-id="82b07-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="82b07-204">Aby uzyskać więcej informacji, zobacz [elemencie pathmap opcji kompilatora](../language-reference/compiler-options/pathmap-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="82b07-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
