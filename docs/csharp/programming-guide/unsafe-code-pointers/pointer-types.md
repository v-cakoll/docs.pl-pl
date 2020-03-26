---
title: Typy wskaźników — przewodnik po programowaniu języka C#
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7bbfa6b2238458d3248da830cf9d6ac36551b431
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507038"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="85aa7-102">Typy wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="85aa7-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="85aa7-103">W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="85aa7-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="85aa7-104">Deklaracja typu wskaźnika ma jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="85aa7-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="85aa7-105">Typ określony przed `*` typem wskaźnika nazywa **się typem referencyjnym**.</span><span class="sxs-lookup"><span data-stu-id="85aa7-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="85aa7-106">Tylko [typ niezarządzany](../../language-reference/builtin-types/unmanaged-types.md) może być typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="85aa7-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="85aa7-107">Typy wskaźników nie dziedziczą z [obiektu](../../language-reference/builtin-types/reference-types.md) i `object`między typami wskaźników nie istnieją konwersje.</span><span class="sxs-lookup"><span data-stu-id="85aa7-107">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="85aa7-108">Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania.</span><span class="sxs-lookup"><span data-stu-id="85aa7-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="85aa7-109">Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="85aa7-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="85aa7-110">W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (\*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="85aa7-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="85aa7-111">Przykład:</span><span class="sxs-lookup"><span data-stu-id="85aa7-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="85aa7-112">Wskaźnik nie może wskazywać na odwołanie lub [struktury,](../../language-reference/builtin-types/struct.md) która zawiera odwołania, ponieważ odwołanie do obiektu może być śmieci zbierane, nawet jeśli wskaźnik jest skierowany do niego.</span><span class="sxs-lookup"><span data-stu-id="85aa7-112">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="85aa7-113">Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="85aa7-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="85aa7-114">Wartość zmiennej wskaźnika `myType*` typu jest adresem zmiennej `myType`typu .</span><span class="sxs-lookup"><span data-stu-id="85aa7-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="85aa7-115">Poniżej przedstawiono przykłady deklaracji typów wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="85aa7-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="85aa7-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="85aa7-116">Example</span></span>|<span data-ttu-id="85aa7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="85aa7-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="85aa7-118">`p`jest wskaźnikiem do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="85aa7-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="85aa7-119">`p`jest wskaźnikiem do wskaźnika do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="85aa7-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="85aa7-120">`p`jest jednowymiarową tablicą wskaźników do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="85aa7-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="85aa7-121">`p`jest wskaźnikiem do char.</span><span class="sxs-lookup"><span data-stu-id="85aa7-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="85aa7-122">`p`jest wskaźnikiem do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="85aa7-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="85aa7-123">Operatora pośredniego wskaźnika \* można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową.</span><span class="sxs-lookup"><span data-stu-id="85aa7-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="85aa7-124">Na przykład przeanalizujmy następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="85aa7-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="85aa7-125">Wyrażenie `*myVariable` oznacza zmienną `int` znalezioną pod adresem `myVariable`zawartym w programie .</span><span class="sxs-lookup"><span data-stu-id="85aa7-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="85aa7-126">Istnieje kilka przykładów wskaźników w tematach [stałych konwersji instrukcji](../../language-reference/keywords/fixed-statement.md) i [wskaźnika](./pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="85aa7-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="85aa7-127">W poniższym `unsafe` przykładzie użyto słowa kluczowego i `fixed` instrukcji i pokazano, jak zwiększać wskaźnik wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="85aa7-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="85aa7-128">Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="85aa7-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="85aa7-129">Te przykłady muszą być skompilowane z zestawem opcji [kompilatora -unsafe.](../../language-reference/compiler-options/unsafe-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="85aa7-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="85aa7-130">Nie można zastosować operatora pośredniego do `void*`wskaźnika typu .</span><span class="sxs-lookup"><span data-stu-id="85aa7-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="85aa7-131">Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="85aa7-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="85aa7-132">Wskaźnik może `null`być .</span><span class="sxs-lookup"><span data-stu-id="85aa7-132">A pointer can be `null`.</span></span> <span data-ttu-id="85aa7-133">Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.</span><span class="sxs-lookup"><span data-stu-id="85aa7-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="85aa7-134">Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="85aa7-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="85aa7-135">Należy wziąć pod uwagę metodę, która `in`zwraca `out`wskaźnik `ref` do zmiennej lokalnej za pośrednictwem , lub parametru lub jako wynik funkcji.</span><span class="sxs-lookup"><span data-stu-id="85aa7-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="85aa7-136">Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.</span><span class="sxs-lookup"><span data-stu-id="85aa7-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="85aa7-137">W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:</span><span class="sxs-lookup"><span data-stu-id="85aa7-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="85aa7-138">Operator/instrukcja</span><span class="sxs-lookup"><span data-stu-id="85aa7-138">Operator/Statement</span></span>|<span data-ttu-id="85aa7-139">Użycie</span><span class="sxs-lookup"><span data-stu-id="85aa7-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="85aa7-140">Wykonuje operację wskaźnika pośredniego.</span><span class="sxs-lookup"><span data-stu-id="85aa7-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="85aa7-141">Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="85aa7-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="85aa7-142">Indeksuje wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="85aa7-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="85aa7-143">Uzyskuje adres zmiennej.</span><span class="sxs-lookup"><span data-stu-id="85aa7-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="85aa7-144">`++` i `--`</span><span class="sxs-lookup"><span data-stu-id="85aa7-144">`++` and `--`</span></span>|<span data-ttu-id="85aa7-145">Zwiększa i zmniejsza wartość wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="85aa7-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="85aa7-146">`+` i `-`</span><span class="sxs-lookup"><span data-stu-id="85aa7-146">`+` and `-`</span></span>|<span data-ttu-id="85aa7-147">Wykonuje operacje arytmetyczne na wskaźniku.</span><span class="sxs-lookup"><span data-stu-id="85aa7-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="85aa7-148">`==`, `!=` `<`, `>` `<=`, , i`>=`</span><span class="sxs-lookup"><span data-stu-id="85aa7-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="85aa7-149">Porównuje wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="85aa7-149">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="85aa7-150">Przydziela pamięć na stosie.</span><span class="sxs-lookup"><span data-stu-id="85aa7-150">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="85aa7-151">`fixed`Instrukcja</span><span class="sxs-lookup"><span data-stu-id="85aa7-151">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="85aa7-152">Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.</span><span class="sxs-lookup"><span data-stu-id="85aa7-152">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="85aa7-153">Aby uzyskać więcej informacji na temat operatorów powiązanych ze [wskaźnikiem, zobacz Operatory powiązane ze wskaźnikiem](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="85aa7-153">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="85aa7-154">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="85aa7-154">C# language specification</span></span>

<span data-ttu-id="85aa7-155">Aby uzyskać więcej informacji, zobacz sekcję [Typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [specyfikacji języka języka języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="85aa7-155">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85aa7-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85aa7-156">See also</span></span>

- [<span data-ttu-id="85aa7-157">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="85aa7-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="85aa7-158">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="85aa7-158">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="85aa7-159">Konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="85aa7-159">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="85aa7-160">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="85aa7-160">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="85aa7-161">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="85aa7-161">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="85aa7-162">unsafe</span><span class="sxs-lookup"><span data-stu-id="85aa7-162">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
