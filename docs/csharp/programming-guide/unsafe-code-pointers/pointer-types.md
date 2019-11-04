---
title: Typy wskaźnika — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: b9b9f145f8f2d945fa06d53efa89f5754766963f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423126"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="68f7c-102">Typy wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="68f7c-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="68f7c-103">W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="68f7c-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="68f7c-104">Deklaracja typu wskaźnika ma jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="68f7c-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="68f7c-105">Typ określony przed `*` w typie wskaźnika jest nazywany **typem referent**.</span><span class="sxs-lookup"><span data-stu-id="68f7c-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="68f7c-106">Tylko [Typ niezarządzany](../../language-reference/builtin-types/unmanaged-types.md) może być typem referent.</span><span class="sxs-lookup"><span data-stu-id="68f7c-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="68f7c-107">Typy wskaźnika nie dziedziczą z [obiektu](../../language-reference/builtin-types/reference-types.md) i nie istnieją konwersje między typami wskaźnika a `object`.</span><span class="sxs-lookup"><span data-stu-id="68f7c-107">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="68f7c-108">Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania.</span><span class="sxs-lookup"><span data-stu-id="68f7c-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="68f7c-109">Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="68f7c-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="68f7c-110">W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (\*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="68f7c-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="68f7c-111">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="68f7c-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="68f7c-112">Wskaźnik nie może wskazywać odwołania lub [struktury](../../language-reference/keywords/struct.md) , która zawiera odwołania, ponieważ odwołanie do obiektu może być odzyskiwane nawet wtedy, gdy wskaźnik wskazuje go.</span><span class="sxs-lookup"><span data-stu-id="68f7c-112">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="68f7c-113">Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="68f7c-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="68f7c-114">Wartość zmiennej wskaźnika typu `myType*` jest adresem zmiennej typu `myType`.</span><span class="sxs-lookup"><span data-stu-id="68f7c-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="68f7c-115">Poniżej przedstawiono przykłady deklaracji typów wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="68f7c-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="68f7c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="68f7c-116">Example</span></span>|<span data-ttu-id="68f7c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="68f7c-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="68f7c-118">`p` jest wskaźnikiem do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="68f7c-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="68f7c-119">`p` jest wskaźnikiem do wskaźnika do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="68f7c-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="68f7c-120">`p` to Jednowymiarowa tablica wskaźników do liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="68f7c-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="68f7c-121">`p` jest wskaźnikiem do znaku.</span><span class="sxs-lookup"><span data-stu-id="68f7c-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="68f7c-122">`p` jest wskaźnikiem do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="68f7c-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="68f7c-123">Operatora pośredniego wskaźnika \* można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową.</span><span class="sxs-lookup"><span data-stu-id="68f7c-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="68f7c-124">Na przykład przeanalizujmy następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="68f7c-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="68f7c-125">Wyrażenie `*myVariable` oznacza zmienną `int` znalezioną pod adresem zawartym w `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="68f7c-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="68f7c-126">Kilka przykładów wskaźników znajduje się w tematach [stałych instrukcja](../../language-reference/keywords/fixed-statement.md) i [konwersje wskaźnika](./pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="68f7c-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="68f7c-127">Poniższy przykład używa słowa kluczowego `unsafe` i instrukcji `fixed` i pokazuje, jak zwiększyć wewnętrzny wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="68f7c-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="68f7c-128">Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="68f7c-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="68f7c-129">Te przykłady muszą zostać skompilowane przy użyciu [-niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) zestawu opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="68f7c-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="68f7c-130">Nie można zastosować operatora pośredni do wskaźnika typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="68f7c-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="68f7c-131">Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="68f7c-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="68f7c-132">Wskaźnik może być `null`.</span><span class="sxs-lookup"><span data-stu-id="68f7c-132">A pointer can be `null`.</span></span> <span data-ttu-id="68f7c-133">Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.</span><span class="sxs-lookup"><span data-stu-id="68f7c-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="68f7c-134">Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="68f7c-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="68f7c-135">Rozważmy metodę, która zwraca wskaźnik do zmiennej lokalnej za pomocą `in`, `out`lub parametru `ref` lub jako wynik funkcji.</span><span class="sxs-lookup"><span data-stu-id="68f7c-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="68f7c-136">Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.</span><span class="sxs-lookup"><span data-stu-id="68f7c-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="68f7c-137">W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:</span><span class="sxs-lookup"><span data-stu-id="68f7c-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="68f7c-138">Operator/instrukcja</span><span class="sxs-lookup"><span data-stu-id="68f7c-138">Operator/Statement</span></span>|<span data-ttu-id="68f7c-139">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="68f7c-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="68f7c-140">Wykonuje operację wskaźnika pośredniego.</span><span class="sxs-lookup"><span data-stu-id="68f7c-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="68f7c-141">Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="68f7c-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="68f7c-142">Indeksuje wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="68f7c-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="68f7c-143">Uzyskuje adres zmiennej.</span><span class="sxs-lookup"><span data-stu-id="68f7c-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="68f7c-144">`++` i `--`</span><span class="sxs-lookup"><span data-stu-id="68f7c-144">`++` and `--`</span></span>|<span data-ttu-id="68f7c-145">Zwiększa i zmniejsza wartość wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="68f7c-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="68f7c-146">`+` i `-`</span><span class="sxs-lookup"><span data-stu-id="68f7c-146">`+` and `-`</span></span>|<span data-ttu-id="68f7c-147">Wykonuje operacje arytmetyczne na wskaźniku.</span><span class="sxs-lookup"><span data-stu-id="68f7c-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="68f7c-148">`==`, `!=`, `<`, `>`, `<=`i `>=`</span><span class="sxs-lookup"><span data-stu-id="68f7c-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="68f7c-149">Porównuje wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="68f7c-149">Compares pointers.</span></span>|
|[<span data-ttu-id="68f7c-150">operator `stackalloc`</span><span class="sxs-lookup"><span data-stu-id="68f7c-150">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="68f7c-151">Przydziela pamięć na stosie.</span><span class="sxs-lookup"><span data-stu-id="68f7c-151">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="68f7c-152">Instrukcja `fixed`</span><span class="sxs-lookup"><span data-stu-id="68f7c-152">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="68f7c-153">Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.</span><span class="sxs-lookup"><span data-stu-id="68f7c-153">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="68f7c-154">Aby uzyskać więcej informacji na temat operatorów powiązanych ze wskaźnikiem, zobacz temat [Operatory powiązane z wskaźnikiem](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="68f7c-154">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="68f7c-155">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="68f7c-155">C# language specification</span></span>

<span data-ttu-id="68f7c-156">Aby uzyskać więcej informacji, zobacz sekcję [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="68f7c-156">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="68f7c-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68f7c-157">See also</span></span>

- [<span data-ttu-id="68f7c-158">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="68f7c-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="68f7c-159">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="68f7c-159">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="68f7c-160">Konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="68f7c-160">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="68f7c-161">Typy</span><span class="sxs-lookup"><span data-stu-id="68f7c-161">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="68f7c-162">unsafe</span><span class="sxs-lookup"><span data-stu-id="68f7c-162">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
