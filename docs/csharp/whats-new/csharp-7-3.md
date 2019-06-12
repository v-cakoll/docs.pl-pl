---
title: Co nowego w języku C# 7.3
description: Omówienie nowych funkcji w języku C# 7.3
ms.date: 05/16/2018
ms.openlocfilehash: aca5c1b82253c02eccf24af1e5c45d0203d0b1b8
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832711"
---
# <a name="whats-new-in-c-73"></a><span data-ttu-id="c4410-103">Co nowego w języku C# 7.3</span><span class="sxs-lookup"><span data-stu-id="c4410-103">What's new in C# 7.3</span></span>

<span data-ttu-id="c4410-104">Istnieją dwa główne motywy do wersji języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c4410-104">There are two main themes to the C# 7.3 release.</span></span> <span data-ttu-id="c4410-105">Jeden motyw zawiera funkcje, które umożliwiają bezpieczne kod był warto wiedzieć, jak niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="c4410-105">One theme provides features that enable safe code to be as performant as unsafe code.</span></span> <span data-ttu-id="c4410-106">Drugi motyw zawiera przyrostowe ulepszenia istniejących funkcji.</span><span class="sxs-lookup"><span data-stu-id="c4410-106">The second theme provides incremental improvements to existing features.</span></span> <span data-ttu-id="c4410-107">Ponadto w tej wersji dodano nowe opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c4410-107">In addition, new compiler options were added in this release.</span></span>

<span data-ttu-id="c4410-108">Następujące nowe funkcje obsługują motyw lepszą wydajność dla bezpiecznego kodu:</span><span class="sxs-lookup"><span data-stu-id="c4410-108">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="c4410-109">Można uzyskać dostęp do pól stałej bez przypinania.</span><span class="sxs-lookup"><span data-stu-id="c4410-109">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="c4410-110">Można ponownie przypisać `ref` zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="c4410-110">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="c4410-111">Możesz użyć inicjatory w `stackalloc` tablic.</span><span class="sxs-lookup"><span data-stu-id="c4410-111">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="c4410-112">Możesz użyć `fixed` instrukcje z dowolnego typu, który obsługuje wzorzec.</span><span class="sxs-lookup"><span data-stu-id="c4410-112">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="c4410-113">Możesz użyć dodatkowe ograniczenia ogólne.</span><span class="sxs-lookup"><span data-stu-id="c4410-113">You can use additional generic constraints.</span></span>

<span data-ttu-id="c4410-114">Wprowadzono następujące ulepszenia istniejących funkcji:</span><span class="sxs-lookup"><span data-stu-id="c4410-114">The following enhancements were made to existing features:</span></span>

- <span data-ttu-id="c4410-115">Możesz przetestować `==` i `!=` z typami spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c4410-115">You can test `==` and `!=` with tuple types.</span></span>
- <span data-ttu-id="c4410-116">Można używać zmiennych wyrażenia w większej liczby lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c4410-116">You can use expression variables in more locations.</span></span>
- <span data-ttu-id="c4410-117">Atrybuty mogą dołączyć do pola zapasowego właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c4410-117">You may attach attributes to the backing field of auto-implemented properties.</span></span>
- <span data-ttu-id="c4410-118">Metoda rozdzielczość w przypadku różnią się argumentów `in` została ulepszona.</span><span class="sxs-lookup"><span data-stu-id="c4410-118">Method resolution when arguments differ by `in` has been improved.</span></span>
- <span data-ttu-id="c4410-119">Rozpoznanie przeciążenia ma teraz mniejszą liczbę przypadków niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="c4410-119">Overload resolution now has fewer ambiguous cases.</span></span>

<span data-ttu-id="c4410-120">Nowe opcje kompilatora są:</span><span class="sxs-lookup"><span data-stu-id="c4410-120">The new compiler options are:</span></span>

- <span data-ttu-id="c4410-121">`-publicsign` Aby włączyć, Otwórz źródło oprogramowania (OSS) podpisywanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="c4410-121">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="c4410-122">`-pathmap` Aby zapewnić mapowanie katalogi źródłowe.</span><span class="sxs-lookup"><span data-stu-id="c4410-122">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="c4410-123">W dalszej części tego artykułu zawiera szczegółowe informacje i łącza, aby dowiedzieć się więcej na temat ulepszenia.</span><span class="sxs-lookup"><span data-stu-id="c4410-123">The remainder of this article provides details and links to learn more about each of the improvements.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="c4410-124">Włączanie bardziej wydajne, bezpieczne kodu</span><span class="sxs-lookup"><span data-stu-id="c4410-124">Enabling more efficient safe code</span></span>

<span data-ttu-id="c4410-125">Można napisać kod C#, bezpiecznie wykonujący oraz niebezpieczny kod.</span><span class="sxs-lookup"><span data-stu-id="c4410-125">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="c4410-126">Bezpieczny kod pozwala uniknąć klasy błędów, takich jak przepełnienia buforu, wskaźniki stray i inne błędy dostępu do pamięci.</span><span class="sxs-lookup"><span data-stu-id="c4410-126">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="c4410-127">Te nowe funkcje rozszerzyć możliwości weryfikowalny kod bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="c4410-127">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="c4410-128">Dokładamy wszelkich starań, można zapisać więcej kodu przy użyciu bezpiecznych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="c4410-128">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="c4410-129">Te funkcje ułatwią.</span><span class="sxs-lookup"><span data-stu-id="c4410-129">These features make that easier.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="c4410-130">Indeksowanie `fixed` pola nie jest wymagane, przypinanie</span><span class="sxs-lookup"><span data-stu-id="c4410-130">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="c4410-131">Należy wziąć pod uwagę tej struktury:</span><span class="sxs-lookup"><span data-stu-id="c4410-131">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="c4410-132">We wcześniejszych wersjach języka C#, potrzebna do przypięcia zmienną dostęp do jednej z wartości całkowitych, które są częścią `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="c4410-132">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="c4410-133">Teraz, poniższy kod kompiluje się bez przypinanie zmiennej `p` w osobnym `fixed` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="c4410-133">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

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

<span data-ttu-id="c4410-134">Zmienna `p` uzyskuje dostęp do jednego elementu `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="c4410-134">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="c4410-135">Nie trzeba deklarować oddzielnego `int*` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c4410-135">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="c4410-136">Należy zauważyć, że w dalszym ciągu konieczny `unsafe` kontekstu.</span><span class="sxs-lookup"><span data-stu-id="c4410-136">Note that you still need an `unsafe` context.</span></span> <span data-ttu-id="c4410-137">We wcześniejszych wersjach języka C# należy zadeklarować wskaźnik drugiego stały:</span><span class="sxs-lookup"><span data-stu-id="c4410-137">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

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

<span data-ttu-id="c4410-138">Aby uzyskać więcej informacji, zobacz artykuł [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c4410-138">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="ref-local-variables-may-be-reassigned"></a><span data-ttu-id="c4410-139">`ref` Zmienne lokalne może zostać ponownie przypisane</span><span class="sxs-lookup"><span data-stu-id="c4410-139">`ref` local variables may be reassigned</span></span>

<span data-ttu-id="c4410-140">Teraz `ref` lokalne może zostać ponownie przypisane do odwoływania się do innego wystąpienia zostały już zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="c4410-140">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="c4410-141">Poniższy kod powoduje kompilację:</span><span class="sxs-lookup"><span data-stu-id="c4410-141">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="c4410-142">Aby uzyskać więcej informacji, zobacz artykuł [ `ref` zwraca i `ref` lokalne](../programming-guide/classes-and-structs/ref-returns.md)oraz artykuł dotyczący [ `foreach` ](../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="c4410-142">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="c4410-143">`stackalloc` tablice obsługują inicjatorów</span><span class="sxs-lookup"><span data-stu-id="c4410-143">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="c4410-144">Dotąd istniała określ wartości dla elementów w tablicy, podczas jego inicjowania:</span><span class="sxs-lookup"><span data-stu-id="c4410-144">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="c4410-145">Teraz takiej samej składni można zastosować do tablic, które są zadeklarowane za pomocą `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="c4410-145">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="c4410-146">Aby uzyskać więcej informacji, zobacz [ `stackalloc` operator](../language-reference/operators/stackalloc.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="c4410-146">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="c4410-147">Obsługuje większą liczbę typów `fixed` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="c4410-147">More types support the `fixed` statement</span></span>

<span data-ttu-id="c4410-148">`fixed` Instrukcja obsługiwana ograniczony zestaw typów.</span><span class="sxs-lookup"><span data-stu-id="c4410-148">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="c4410-149">Począwszy od C# 7.3, dowolny typ, który zawiera `GetPinnableReference()` metodę, która zwraca `ref T` lub `ref readonly T` może być `fixed`.</span><span class="sxs-lookup"><span data-stu-id="c4410-149">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="c4410-150">Dodanie tej funkcji oznacza, że `fixed` mogą być używane z <xref:System.Span%601?displayProperty=nameWithType> i typów pokrewnych.</span><span class="sxs-lookup"><span data-stu-id="c4410-150">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="c4410-151">Aby uzyskać więcej informacji, zobacz [ `fixed` instrukcji](../language-reference/keywords/fixed-statement.md) artykułu w dokumentacji języka.</span><span class="sxs-lookup"><span data-stu-id="c4410-151">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="c4410-152">Rozszerzone ograniczenia ogólne</span><span class="sxs-lookup"><span data-stu-id="c4410-152">Enhanced generic constraints</span></span>

<span data-ttu-id="c4410-153">Teraz można określić typ <xref:System.Enum?displayProperty=nameWithType> lub <xref:System.Delegate?displayProperty=nameWithType> jako klasa bazowa ograniczeń dla parametru typu.</span><span class="sxs-lookup"><span data-stu-id="c4410-153">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="c4410-154">Można również użyć nowej `unmanaged` ograniczenie, aby określić, że parametr typu musi być **niezarządzany typ**.</span><span class="sxs-lookup"><span data-stu-id="c4410-154">You can also use the new `unmanaged` constraint, to specify that a type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="c4410-155">**Niezarządzany typ** to typ, który nie jest typem odwołania i nie zawiera żadnych typu odwołania na każdym poziomie zagnieżdżania.</span><span class="sxs-lookup"><span data-stu-id="c4410-155">An **unmanaged type** is a type that isn't a reference type and doesn't contain any reference type at any level of nesting.</span></span>

<span data-ttu-id="c4410-156">Aby uzyskać więcej informacji, zobacz artykuły na [ `where` ograniczenia ogólne](../language-reference/keywords/where-generic-type-constraint.md) i [ograniczenia dotyczące parametrów typu](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c4410-156">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="c4410-157">Dodanie tych warunków ograniczających do istniejących typów jest [niezgodna zmiana](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="c4410-157">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="c4410-158">Zamknięte typy rodzajowe mogą już nie spełnia te nowe ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="c4410-158">Closed generic types may no longer meet these new constraints.</span></span>

## <a name="make-existing-features-better"></a><span data-ttu-id="c4410-159">Ulepszyć istniejące funkcje</span><span class="sxs-lookup"><span data-stu-id="c4410-159">Make existing features better</span></span>

<span data-ttu-id="c4410-160">Drugi motyw zawiera ulepszenia funkcji w języku.</span><span class="sxs-lookup"><span data-stu-id="c4410-160">The second theme provides improvements to features in the language.</span></span> <span data-ttu-id="c4410-161">Te funkcje Zwiększ produktywność, podczas zapisywania C#.</span><span class="sxs-lookup"><span data-stu-id="c4410-161">These features improve productivity when writing C#.</span></span>

### <a name="tuples-support--and-"></a><span data-ttu-id="c4410-162">Obsługuje krotek `==` i `!=`</span><span class="sxs-lookup"><span data-stu-id="c4410-162">Tuples support `==` and `!=`</span></span>

<span data-ttu-id="c4410-163">C# spójna kolekcja znajdująca się typy obsługują teraz `==` i `!=`.</span><span class="sxs-lookup"><span data-stu-id="c4410-163">The C# tuple types now support `==` and `!=`.</span></span> <span data-ttu-id="c4410-164">Aby uzyskać więcej informacji, zobacz obejmujący sekcję [równości](../tuples.md#equality-and-tuples) w artykule na [krotek](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="c4410-164">For more information, see the section covering [equality](../tuples.md#equality-and-tuples) in the article on [tuples](../tuples.md).</span></span>

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a><span data-ttu-id="c4410-165">Dołącz atrybuty do pola zapasowego właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="c4410-165">Attach attributes to the backing fields for auto-implemented properties</span></span>

<span data-ttu-id="c4410-166">Ta składnia jest teraz obsługiwane:</span><span class="sxs-lookup"><span data-stu-id="c4410-166">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="c4410-167">Ten atrybut `SomeThingAboutFieldAttribute` jest stosowany do pola pomocniczego wygenerowanego przez kompilator dla `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="c4410-167">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="c4410-168">Aby uzyskać więcej informacji, zobacz [atrybuty](../programming-guide/concepts/attributes/index.md) w Podręczniku programowania C#.</span><span class="sxs-lookup"><span data-stu-id="c4410-168">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

### <a name="in-method-overload-resolution-tiebreaker"></a><span data-ttu-id="c4410-169">`in` tiebreaker rozdzielczość przeciążenia metody</span><span class="sxs-lookup"><span data-stu-id="c4410-169">`in` method overload resolution tiebreaker</span></span>

<span data-ttu-id="c4410-170">Gdy `in` dodano modyfikator argument, te dwie metody mogłoby spowodować niejednoznaczność:</span><span class="sxs-lookup"><span data-stu-id="c4410-170">When the `in` argument modifier was added, these two methods would cause an ambiguity:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="c4410-171">Teraz przez wartość (najpierw w poprzednim przykładzie) przeciążenie jest lepsze niż w wersji odniesienia tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="c4410-171">Now, the by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="c4410-172">Aby wywołać wersję z argument odwołania tylko do odczytu, należy dołączyć `in` modyfikator podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="c4410-172">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

> [!NOTE]
> <span data-ttu-id="c4410-173">Było to wdrożone jako naprawienia błędu.</span><span class="sxs-lookup"><span data-stu-id="c4410-173">This was implemented as a bug fix.</span></span> <span data-ttu-id="c4410-174">To nie jest już jest niejednoznaczny nawet w przypadku wersji językowej ustawiona na "7.2".</span><span class="sxs-lookup"><span data-stu-id="c4410-174">This no longer is ambiguous even with the language version set to "7.2".</span></span>

<span data-ttu-id="c4410-175">Aby uzyskać więcej informacji, zobacz artykuł [ `in` modyfikator parametru](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="c4410-175">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="extend-expression-variables-in-initializers"></a><span data-ttu-id="c4410-176">Rozszerzanie zmiennych wyrażenia w inicjatorach</span><span class="sxs-lookup"><span data-stu-id="c4410-176">Extend expression variables in initializers</span></span>

<span data-ttu-id="c4410-177">Dodano w języku C# 7.0, aby zezwolić na składnię `out` deklaracje zmiennej został rozszerzony do uwzględnienia inicjatorów pola, właściwości, inicjatory konstruktora, a klauzul zapytania.</span><span class="sxs-lookup"><span data-stu-id="c4410-177">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="c4410-178">Umożliwia stosowanie kodu, takich jak na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c4410-178">It enables code such as the following example:</span></span>

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

### <a name="improved-overload-candidates"></a><span data-ttu-id="c4410-179">Ulepszone kandydujące metody rozwiązywania przeciążenia</span><span class="sxs-lookup"><span data-stu-id="c4410-179">Improved overload candidates</span></span>

<span data-ttu-id="c4410-180">W każdej wersji reguł rozwiązywania przeciążenia zaktualizowani adres sytuacjom, w których niejednoznacznego wywołania metod mają "oczywistym" wyborem.</span><span class="sxs-lookup"><span data-stu-id="c4410-180">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="c4410-181">W tej wersji dodano trzy nowe reguły, aby ułatwić kompilatora wybierz oczywistym wyborem:</span><span class="sxs-lookup"><span data-stu-id="c4410-181">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="c4410-182">Podczas grupy metod zawiera wystąpienie i statyczne elementy członkowskie, kompilator odrzuca składowych wystąpienia, jeśli metoda została wywołana bez odbiornika wystąpienia lub kontekstu.</span><span class="sxs-lookup"><span data-stu-id="c4410-182">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="c4410-183">Kompilator odrzuca statycznych elementów członkowskich, jeśli metoda została wywołana z odbiornikiem wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c4410-183">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="c4410-184">Gdy nie ma żadnych odbiorcy, kompilator zawiera tylko statyczne elementy członkowskie w ramach kontekstu statycznego, w przeciwnym razie statycznych i elementów członkowskich wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c4410-184">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="c4410-185">Odbiornik ambiguously to wystąpienie lub typu, kompilator zawiera zarówno.</span><span class="sxs-lookup"><span data-stu-id="c4410-185">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="c4410-186">Kontekstu statycznego, gdy ukrytego `this` odbiorcy wystąpienia nie można użyć, zawiera treść elementów członkowskich, gdzie nie `this` jest zdefiniowany, takie jak statyczne elementy członkowskie, a także miejsc, gdzie `this` nie można użyć, takie jak inicjatorów pola i Inicjatory konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c4410-186">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="c4410-187">Jeśli grupa metoda zawiera niektóre metody rodzajowe, której argumenty typu nie spełnia ich ograniczenia, te elementy członkowskie są usuwane z zestawu Release candidate.</span><span class="sxs-lookup"><span data-stu-id="c4410-187">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="c4410-188">Dla metody konwersji z grupy metody Release candidate, którego typem zwracanym nie zgodny z pełnomocnika Zwróć typ są usuwane z zestawu.</span><span class="sxs-lookup"><span data-stu-id="c4410-188">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="c4410-189">Tylko zauważysz tej zmiany, ponieważ można znaleźć mniej błędów kompilatora przeciążenia metody niejednoznaczne po upewnieniu się, która metoda jest lepsza.</span><span class="sxs-lookup"><span data-stu-id="c4410-189">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="c4410-190">Nowe opcje kompilatora</span><span class="sxs-lookup"><span data-stu-id="c4410-190">New compiler options</span></span>

<span data-ttu-id="c4410-191">Nowe opcje kompilatora obsługuje nową kompilację i scenariuszy DevOps dla programów C#.</span><span class="sxs-lookup"><span data-stu-id="c4410-191">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="c4410-192">Publiczne lub podpisywania "Open Source"</span><span class="sxs-lookup"><span data-stu-id="c4410-192">Public or Open Source signing</span></span>

<span data-ttu-id="c4410-193">`-publicsign` — Opcja kompilatora instruuje kompilator, aby podpisać zestaw za pomocą klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="c4410-193">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="c4410-194">Zestaw jest oznaczony jako podpisany, ale podpis jest pobierana z kluczem publicznym.</span><span class="sxs-lookup"><span data-stu-id="c4410-194">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="c4410-195">Ta opcja umożliwia tworzenie zestawów podpisanych z projektów typu open source za pomocą klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="c4410-195">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="c4410-196">Aby uzyskać więcej informacji, zobacz [— opcja kompilatora - publicsign](../language-reference/compiler-options/publicsign-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="c4410-196">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="c4410-197">elemencie pathmap</span><span class="sxs-lookup"><span data-stu-id="c4410-197">pathmap</span></span>

<span data-ttu-id="c4410-198">`-pathmap` — Opcja kompilatora instruuje kompilator, aby zastąpić ścieżkami źródłowymi w środowisku kompilacji ze ścieżkami źródłowymi zamapowany.</span><span class="sxs-lookup"><span data-stu-id="c4410-198">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="c4410-199">`-pathmap` Opcja kontroluje ścieżki źródłowej, napisane przez kompilator dla plików PDB lub do <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c4410-199">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="c4410-200">Aby uzyskać więcej informacji, zobacz [elemencie pathmap — opcja kompilatora](../language-reference/compiler-options/pathmap-compiler-option.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="c4410-200">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
