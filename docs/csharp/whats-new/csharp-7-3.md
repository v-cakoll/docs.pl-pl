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
# <a name="whats-new-in-c-73"></a><span data-ttu-id="456fd-103">Co nowego w Języku C# 7.3</span><span class="sxs-lookup"><span data-stu-id="456fd-103">What's new in C# 7.3</span></span>

<span data-ttu-id="456fd-104">Istnieją dwa główne tematy do wersji C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="456fd-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="456fd-105">Jeden motyw zawiera funkcje, które umożliwiają bezpiecznego kodu, aby być tak działającym jak niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="456fd-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="456fd-106">Drugi motyw zapewnia przyrostowe ulepszenia istniejących funkcji.</span><span class="sxs-lookup"><span data-stu-id="456fd-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="456fd-107">Ponadto w tej wersji dodano nowe opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="456fd-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="456fd-108">Następujące nowe funkcje obsługują temat lepszej wydajności bezpiecznego kodu:</span><span class="sxs-lookup"><span data-stu-id="456fd-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="456fd-109">Dostęp do stałych pól można uzyskać bez przypinania.</span><span class="sxs-lookup"><span data-stu-id="456fd-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="456fd-110">Można ponownie przypisać `ref` zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="456fd-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="456fd-111">Inicjatorów `stackalloc` można używać w tablicach.</span><span class="sxs-lookup"><span data-stu-id="456fd-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="456fd-112">Instrukcje można `fixed` używać z dowolnego typu, który obsługuje wzorzec.</span><span class="sxs-lookup"><span data-stu-id="456fd-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="456fd-113">Można użyć dodatkowych ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="456fd-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="456fd-114">Wprowadzono następujące ulepszenia istniejących funkcji:</span><span class="sxs-lookup"><span data-stu-id="456fd-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="456fd-115">Można `==` przetestować `!=` i z typami krotki.</span><span class="sxs-lookup"><span data-stu-id="456fd-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="456fd-116">Zmiennych wyrażeń można używać w większej liczbie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="456fd-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="456fd-117">Atrybuty można dołączyć do pola zapasowego właściwości implementowanych automatycznie.</span><span class="sxs-lookup"><span data-stu-id="456fd-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="456fd-118">Poprawiono rozpoznawanie `in` metod, gdy argumenty różnią się.</span><span class="sxs-lookup"><span data-stu-id="456fd-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="456fd-119">Rozdzielczość przeciążenia ma teraz mniej niejednoznacznych przypadków.</span><span class="sxs-lookup"><span data-stu-id="456fd-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="456fd-120">Nowe opcje kompilatora to:</span><span class="sxs-lookup"><span data-stu-id="456fd-120">The new compiler options are:</span></span>

- <span data-ttu-id="456fd-121">`-publicsign`, aby włączyć podpisywanie zestawów przez oprogramowanie Open Source (OSS).</span><span class="sxs-lookup"><span data-stu-id="456fd-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="456fd-122">`-pathmap`, aby zapewnić mapowanie dla katalogów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="456fd-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="456fd-123">W dalszej części tego artykułu zawiera szczegółowe informacje i łącza, aby dowiedzieć się więcej o każdej z ulepszeń.</span><span class="sxs-lookup"><span data-stu-id="456fd-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span> <span data-ttu-id="456fd-124">Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`</span><span class="sxs-lookup"><span data-stu-id="456fd-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="456fd-125">Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)</span><span class="sxs-lookup"><span data-stu-id="456fd-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="456fd-126">Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)</span><span class="sxs-lookup"><span data-stu-id="456fd-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="456fd-127">Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *próbek.*</span><span class="sxs-lookup"><span data-stu-id="456fd-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="456fd-128">Uruchom polecenie `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="456fd-128">Run `dotnet try`.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="456fd-129">Włączanie bardziej wydajnego bezpiecznego kodu</span><span class="sxs-lookup"><span data-stu-id="456fd-129">Enabling more efficient safe code</span></span>

<span data-ttu-id="456fd-130">Powinno być w stanie napisać kod C# bezpiecznie, który wykonuje, jak również niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="456fd-130">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="456fd-131">Bezpieczny kod pozwala uniknąć klas błędów, takich jak przekroczenia buforu, wskaźniki bezpańskich i inne błędy dostępu do pamięci.</span><span class="sxs-lookup"><span data-stu-id="456fd-131">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="456fd-132">Te nowe funkcje rozszerzają możliwości weryfikowalnego bezpiecznego kodu.</span><span class="sxs-lookup"><span data-stu-id="456fd-132">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="456fd-133">Staraj się napisać więcej kodu przy użyciu bezpiecznych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="456fd-133">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="456fd-134">Te funkcje sprawiają, że łatwiej.</span><span class="sxs-lookup"><span data-stu-id="456fd-134">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="456fd-135">Pola `fixed` indeksowania nie wymagają przypinania</span><span class="sxs-lookup"><span data-stu-id="456fd-135">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="456fd-136">Rozważmy tę strukturę:</span><span class="sxs-lookup"><span data-stu-id="456fd-136">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="456fd-137">We wcześniejszych wersjach języka C#, trzeba było przypiąć zmienną, `myFixedField`aby uzyskać dostęp do jednej z liczb całkowitych, które są częścią programu .</span><span class="sxs-lookup"><span data-stu-id="456fd-137">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="456fd-138">Teraz poniższy kod kompiluje bez `p` przypinania zmiennej wewnątrz oddzielnej `fixed` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="456fd-138">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="456fd-139">Zmienna `p` uzyskuje dostęp `myFixedField`do jednego elementu w programie .</span><span class="sxs-lookup"><span data-stu-id="456fd-139">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="456fd-140">Nie trzeba deklarować oddzielnej `int*` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="456fd-140">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="456fd-141">Należy pamiętać, że `unsafe` nadal potrzebujesz kontekstu.</span><span class="sxs-lookup"><span data-stu-id="456fd-141">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="456fd-142">We wcześniejszych wersjach języka C#należy zadeklarować drugi stały wskaźnik:</span><span class="sxs-lookup"><span data-stu-id="456fd-142">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="456fd-143">Aby uzyskać więcej informacji, [ `fixed` ](../language-reference/keywords/fixed-statement.md)zobacz artykuł na instrukcji .</span><span class="sxs-lookup"><span data-stu-id="456fd-143">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="456fd-144">`ref`zmienne lokalne mogą być ponownie przypisywane</span><span class="sxs-lookup"><span data-stu-id="456fd-144">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="456fd-145">Teraz `ref` mieszkańcy mogą być ponownie przypisane do odwoływania się do różnych wystąpień po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="456fd-145">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="456fd-146">Następujący kod teraz kompiluje:</span><span class="sxs-lookup"><span data-stu-id="456fd-146">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="456fd-147">Aby uzyskać więcej informacji, zobacz artykuł na [`foreach`](../language-reference/keywords/foreach-in.md) [ `ref` temat zwrotów i `ref` mieszkańców](../programming-guide/classes-and-structs/ref-returns.md)oraz artykuł na temat .</span><span class="sxs-lookup"><span data-stu-id="456fd-147">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="456fd-148">`stackalloc`tablice obsługują inicjatory</span><span class="sxs-lookup"><span data-stu-id="456fd-148">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="456fd-149">Można było określić wartości elementów w tablicy podczas inicjowania:</span><span class="sxs-lookup"><span data-stu-id="456fd-149">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="456fd-150">Teraz tę samą składnię można zastosować do `stackalloc`tablic zadeklarowanych za pomocą:</span><span class="sxs-lookup"><span data-stu-id="456fd-150">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="456fd-151">Aby uzyskać więcej informacji, zobacz artykuł [ `stackalloc` operatora.](../language-reference/operators/stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="456fd-151">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="456fd-152">Więcej typów `fixed` obsługuje instrukcję</span><span class="sxs-lookup"><span data-stu-id="456fd-152">More types support the `fixed` statement</span></span>

<span data-ttu-id="456fd-153">Instrukcja `fixed` obsługiwane ograniczony zestaw typów.</span><span class="sxs-lookup"><span data-stu-id="456fd-153">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="456fd-154">Począwszy od języka C# 7.3, każdy typ, który `GetPinnableReference()` zawiera metodę, która zwraca lub `ref T` `ref readonly T` może być `fixed`.</span><span class="sxs-lookup"><span data-stu-id="456fd-154">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="456fd-155">Dodanie tej funkcji `fixed` oznacza, <xref:System.Span%601?displayProperty=nameWithType> że można używać z typami pokrewnymi i pokrewnymi.</span><span class="sxs-lookup"><span data-stu-id="456fd-155">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="456fd-156">Aby uzyskać więcej informacji, zobacz artykuł [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md) w odwołaniu do języka.</span><span class="sxs-lookup"><span data-stu-id="456fd-156">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="456fd-157">Rozszerzone ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="456fd-157">Enhanced generic constraints</span></span>

<span data-ttu-id="456fd-158">Teraz można określić <xref:System.Enum?displayProperty=nameWithType> typ <xref:System.Delegate?displayProperty=nameWithType> lub jako ograniczenia klasy podstawowej dla parametru typu.</span><span class="sxs-lookup"><span data-stu-id="456fd-158">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="456fd-159">Można również użyć `unmanaged` nowego ograniczenia, aby określić, że parametr typu musi być [typem niepodlegającym](../language-reference/builtin-types/unmanaged-types.md)null.</span><span class="sxs-lookup"><span data-stu-id="456fd-159">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="456fd-160">Aby uzyskać więcej informacji, zobacz artykuły dotyczące [ `where` ogólnych ograniczeń](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczeń parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="456fd-160">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="456fd-161">Dodanie tych ograniczeń do istniejących typów jest [niezgodną zmianą](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="456fd-161">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="456fd-162">Zamknięte typy ogólne mogą już nie spełniać tych nowych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="456fd-162">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="456fd-163">Ulepszanie istniejących funkcji</span><span class="sxs-lookup"><span data-stu-id="456fd-163">Make existing features better</span></span>

<span data-ttu-id="456fd-164">Drugi motyw zawiera ulepszenia funkcji w języku.</span><span class="sxs-lookup"><span data-stu-id="456fd-164">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="456fd-165">Te funkcje zwiększają produktywność podczas pisania języka C#.</span><span class="sxs-lookup"><span data-stu-id="456fd-165">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="456fd-166">Obsługa `==` krotek i`!=`</span><span class="sxs-lookup"><span data-stu-id="456fd-166">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="456fd-167">Typy krotki Języka `==` C# obsługują teraz i `!=`.</span><span class="sxs-lookup"><span data-stu-id="456fd-167">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="456fd-168">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [równości](../tuples.md#equality-and-tuples) w artykule na [krotek](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="456fd-168">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="456fd-169">Dołączanie atrybutów do pól zapasowych dla właściwości implementowanych automatycznie</span><span class="sxs-lookup"><span data-stu-id="456fd-169">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="456fd-170">Ta składnia jest teraz obsługiwana:</span><span class="sxs-lookup"><span data-stu-id="456fd-170">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="456fd-171">Atrybut `SomeThingAboutFieldAttribute` jest stosowany do kompilatora `SomeProperty`wygenerowanego pola zapasowego dla .</span><span class="sxs-lookup"><span data-stu-id="456fd-171">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="456fd-172">Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w przewodniku programowania C#.</span><span class="sxs-lookup"><span data-stu-id="456fd-172">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="456fd-173">`in`metoda przeciążenia rozdzielczość tiebreaker</span><span class="sxs-lookup"><span data-stu-id="456fd-173">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="456fd-174">Po `in` dodaniu modyfikatorargumentu te dwie metody mogą spowodować niejednoznaczność:</span><span class="sxs-lookup"><span data-stu-id="456fd-174">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="456fd-175">Teraz według wartości (pierwszy w poprzednim przykładzie) przeciążenie jest lepsze niż przez readonly wersji referencyjnej.</span><span class="sxs-lookup"><span data-stu-id="456fd-175">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="456fd-176">Aby wywołać wersję z argumentem odwołania tylko `in` do odczytu, należy dołączyć modyfikator podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="456fd-176">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="456fd-177">Zostało to zaimplementowane jako poprawka błędu.</span><span class="sxs-lookup"><span data-stu-id="456fd-177">This was implemented as a bug fix.</span></span> <span data-ttu-id="456fd-178">Nie jest to już dwuznaczne, nawet w wersji językowej ustawionej na "7.2".</span><span class="sxs-lookup"><span data-stu-id="456fd-178">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="456fd-179">Aby uzyskać więcej informacji, zobacz artykuł na [ `in` modyfikator parametrów](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="456fd-179">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="456fd-180">Rozszerzanie zmiennych wyrażenia w inicjatorach</span><span class="sxs-lookup"><span data-stu-id="456fd-180">Extend expression variables in initializers</span></span>

<span data-ttu-id="456fd-181">Składnia dodana w języku C# 7.0, aby umożliwić `out` deklaracje zmiennych została rozszerzona o inicjatory pól, inicjatory właściwości, inicjatory konstruktorów i klauzule kwerendy.</span><span class="sxs-lookup"><span data-stu-id="456fd-181">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="456fd-182">Umożliwia kod, taki jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="456fd-182">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="456fd-183">Ulepszone kandydujące metody rozwiązywania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="456fd-183">Improved overload candidates</span></span>

<span data-ttu-id="456fd-184">W każdej wersji reguły rozpoznawania przeciążenia są aktualizowane w celu rozwiązania sytuacji, w których wywołania metod niejednoznacznych mają wybór "oczywisty".</span><span class="sxs-lookup"><span data-stu-id="456fd-184">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="456fd-185">W tej wersji dodano trzy nowe reguły, które pomogą kompilatorowi wybrać oczywisty wybór:</span><span class="sxs-lookup"><span data-stu-id="456fd-185">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="456fd-186">Gdy grupa metod zawiera zarówno wystąpienia, jak i statyczne elementy członkowskie, kompilator odrzuca elementy członkowskie wystąpienia, jeśli metoda została wywołana bez odbiornika wystąpienia lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="456fd-186">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="456fd-187">Kompilator odrzuca elementy członkowskie statyczne, jeśli metoda została wywołana za pomocą odbiornika wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="456fd-187">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="456fd-188">Gdy nie ma odbiornika, kompilator zawiera tylko elementy statyczne w kontekście statycznym, w przeciwnym razie zarówno statyczne i wystąpienia elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="456fd-188">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="456fd-189">Gdy odbiornik jest niejednoznacznie wystąpienie lub typ, kompilator zawiera zarówno.</span><span class="sxs-lookup"><span data-stu-id="456fd-189">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="456fd-190">Kontekst statyczny, `this` w którym nie można użyć niejawnego `this` odbiornika wystąpienia, obejmuje treść elementów członkowskich, w których nie jest zdefiniowany, takich jak statycznych elementów członkowskich, a także miejsca, w których `this` nie można użyć, takich jak inicjatory pola i inicjatory konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="456fd-190">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="456fd-191">Gdy grupa metod zawiera niektóre metody ogólne, których argumenty typu nie spełniają ich ograniczeń, te elementy członkowskie są usuwane z zestawu kandydatów.</span><span class="sxs-lookup"><span data-stu-id="456fd-191">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="456fd-192">W przypadku konwersji grupy metod metody, których typ zwracany nie jest zgodny z typem zwracanym pełnomocnika, są usuwane z zestawu.</span><span class="sxs-lookup"><span data-stu-id="456fd-192">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="456fd-193">Zauważysz tylko tę zmianę, ponieważ znajdziesz mniej błędów kompilatora dla przeciążenia metody niejednoznaczne, gdy masz pewność, która metoda jest lepsza.</span><span class="sxs-lookup"><span data-stu-id="456fd-193">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="456fd-194">Nowe opcje kompilatora</span><span class="sxs-lookup"><span data-stu-id="456fd-194">New compiler options</span></span>

<span data-ttu-id="456fd-195">Nowe opcje kompilatora obsługują nowe scenariusze kompilacji i DevOps dla programów Języka C#.</span><span class="sxs-lookup"><span data-stu-id="456fd-195">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="456fd-196">Podpisywanie publiczne lub open source</span><span class="sxs-lookup"><span data-stu-id="456fd-196">Public or Open Source signing</span></span>

<span data-ttu-id="456fd-197">Opcja `-publicsign` kompilatora instruuje kompilatordo podpisania zestawu przy użyciu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="456fd-197">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="456fd-198">Zestaw jest oznaczony jako podpisany, ale podpis jest pobierany z klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="456fd-198">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="456fd-199">Ta opcja umożliwia tworzenie podpisanych zestawów z projektów open source przy użyciu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="456fd-199">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="456fd-200">Aby uzyskać więcej informacji, zobacz [-publicsign kompilator a opcja](../language-reference/compiler-options/publicsign-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="456fd-200">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="456fd-201">mapa ścieżki</span><span class="sxs-lookup"><span data-stu-id="456fd-201">pathmap</span></span>

<span data-ttu-id="456fd-202">Opcja `-pathmap` kompilatora instruuje kompilator, aby zastąpić ścieżki źródłowe ze środowiska kompilacji z mapowanych ścieżek źródłowych.</span><span class="sxs-lookup"><span data-stu-id="456fd-202">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="456fd-203">Opcja `-pathmap` steruje ścieżką źródłową zapisaną przez kompilator do plików PDB lub dla <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>pliku .</span><span class="sxs-lookup"><span data-stu-id="456fd-203">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="456fd-204">Aby uzyskać więcej informacji, zobacz [-pathmap kompilator a](../language-reference/compiler-options/pathmap-compiler-option.md) opcja artykułu.</span><span class="sxs-lookup"><span data-stu-id="456fd-204">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
