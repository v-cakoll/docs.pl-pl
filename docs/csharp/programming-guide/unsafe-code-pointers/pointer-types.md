---
title: Typy wskaźników - C# Programming Guide
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 028497bbeae26ded126ba4d7ce459a6a85e0bcb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724047"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="11659-102">Typy wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="11659-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="11659-103">W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="11659-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="11659-104">Deklaracja typu wskaźnika ma jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="11659-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="11659-105">Typ określony przed `*` w wskaźnik typu jest nazywana **typu Obiekt obsługujący**.</span><span class="sxs-lookup"><span data-stu-id="11659-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="11659-106">Dowolne z następujących typów może być typem obiekt obsługujący:</span><span class="sxs-lookup"><span data-stu-id="11659-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="11659-107">Dowolnego typu całkowitoliczbowego: [sbyte](../../language-reference/keywords/sbyte.md), [bajtów](../../language-reference/keywords/byte.md), [krótki](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [długie](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="11659-107">Any integral type: [sbyte](../../language-reference/keywords/sbyte.md), [byte](../../language-reference/keywords/byte.md), [short](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [long](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).</span></span>
- <span data-ttu-id="11659-108">Wszystkie typy zmiennoprzecinkowe: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="11659-108">Any floating-point type: [float](../../language-reference/keywords/float.md), [double](../../language-reference/keywords/double.md).</span></span>
- <span data-ttu-id="11659-109">[CHAR](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="11659-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="11659-110">[wartość logiczna](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="11659-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="11659-111">[dziesiętna](../../language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="11659-111">[decimal](../../language-reference/keywords/decimal.md).</span></span>
- <span data-ttu-id="11659-112">Wszelkie [wyliczenia](../../language-reference/keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="11659-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="11659-113">Dowolny typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="11659-113">Any pointer type.</span></span> <span data-ttu-id="11659-114">Dzięki temu wyrażenia takie jak `void**`.</span><span class="sxs-lookup"><span data-stu-id="11659-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="11659-115">Dowolny typ struktury zdefiniowany przez użytkownika, który zawiera tylko pola niezarządzanych typów.</span><span class="sxs-lookup"><span data-stu-id="11659-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="11659-116">Typy wskaźnika nie dziedziczą [obiektu](../../language-reference/keywords/object.md) i nie występują konwersje między typami wskaźnika a `object`.</span><span class="sxs-lookup"><span data-stu-id="11659-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="11659-117">Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania.</span><span class="sxs-lookup"><span data-stu-id="11659-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="11659-118">Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="11659-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="11659-119">W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (\*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="11659-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="11659-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="11659-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="11659-121">Wskaźnik nie może wskazywać odwołania ani do [struktury](../../language-reference/keywords/struct.md) zawierającej odwołania, ponieważ odwołanie do obiektu może zostać usunięte nawet wtedy, gdy jest wskazywane przez wskaźnik do niego.</span><span class="sxs-lookup"><span data-stu-id="11659-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="11659-122">Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="11659-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="11659-123">Wartość zmiennej wskaźnika typu `myType*` to adres zmiennej typu `myType`.</span><span class="sxs-lookup"><span data-stu-id="11659-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="11659-124">Poniżej przedstawiono przykłady deklaracji typów wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="11659-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="11659-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="11659-125">Example</span></span>|<span data-ttu-id="11659-126">Opis</span><span class="sxs-lookup"><span data-stu-id="11659-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="11659-127">`p` to wskaźnik do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="11659-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="11659-128">`p` to wskaźnik do wskaźnika do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="11659-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="11659-129">`p` to Jednowymiarowa tablica wskaźników do liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="11659-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="11659-130">`p` jest wskaźnik do znaku.</span><span class="sxs-lookup"><span data-stu-id="11659-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="11659-131">`p` to wskaźnik do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="11659-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="11659-132">Operatora pośredniego wskaźnika \* można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową.</span><span class="sxs-lookup"><span data-stu-id="11659-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="11659-133">Na przykład przeanalizujmy następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="11659-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="11659-134">Wyrażenie `*myVariable` oznacza `int` znaleziono pod adresem zawartym w zmiennej `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="11659-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="11659-135">Istnieje kilka przykładów wskaźników można znaleźć w tematach [fixed Statement](../../language-reference/keywords/fixed-statement.md) i [konwersje wskaźników](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="11659-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="11659-136">W poniższym przykładzie użyto `unsafe` — słowo kluczowe i `fixed` instrukcji i pokazuje, jak zwiększyć wartość wskaźnika wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="11659-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="11659-137">Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="11659-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="11659-138">Przykłady te muszą być skompilowane z [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) zestaw opcji kompilatora.</span><span class="sxs-lookup"><span data-stu-id="11659-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="11659-139">Nie można zastosować operatora pośredniego do wskaźnika typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="11659-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="11659-140">Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="11659-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="11659-141">Wskaźnik może mieć `null`.</span><span class="sxs-lookup"><span data-stu-id="11659-141">A pointer can be `null`.</span></span> <span data-ttu-id="11659-142">Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.</span><span class="sxs-lookup"><span data-stu-id="11659-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="11659-143">Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="11659-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="11659-144">Należy wziąć pod uwagę metodę, która zwraca wskaźnik do zmiennej lokalnej za pośrednictwem `in`, `out`, lub `ref` parametru lub jako wynik funkcji.</span><span class="sxs-lookup"><span data-stu-id="11659-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="11659-145">Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.</span><span class="sxs-lookup"><span data-stu-id="11659-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="11659-146">W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:</span><span class="sxs-lookup"><span data-stu-id="11659-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="11659-147">Operator/instrukcja</span><span class="sxs-lookup"><span data-stu-id="11659-147">Operator/Statement</span></span>|<span data-ttu-id="11659-148">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="11659-148">Use</span></span>|
|-------------------------|---------|
|*|<span data-ttu-id="11659-149">Wykonuje operację wskaźnika pośredniego.</span><span class="sxs-lookup"><span data-stu-id="11659-149">Performs pointer indirection.</span></span>|
|->|<span data-ttu-id="11659-150">Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="11659-150">Accesses a member of a struct through a pointer.</span></span>|
|<span data-ttu-id="11659-151">[]</span><span class="sxs-lookup"><span data-stu-id="11659-151">[]</span></span>|<span data-ttu-id="11659-152">Indeksuje wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="11659-152">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="11659-153">Uzyskuje adres zmiennej.</span><span class="sxs-lookup"><span data-stu-id="11659-153">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="11659-154">++ oraz --</span><span class="sxs-lookup"><span data-stu-id="11659-154">++ and --</span></span>|<span data-ttu-id="11659-155">Zwiększa i zmniejsza wartość wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="11659-155">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="11659-156">+ oraz -</span><span class="sxs-lookup"><span data-stu-id="11659-156">+ and -</span></span>|<span data-ttu-id="11659-157">Wykonuje operacje arytmetyczne na wskaźniku.</span><span class="sxs-lookup"><span data-stu-id="11659-157">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="11659-158">==,! =, \<, >, \<= i > =</span><span class="sxs-lookup"><span data-stu-id="11659-158">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="11659-159">Porównuje wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="11659-159">Compares pointers.</span></span>|
|`stackalloc`|<span data-ttu-id="11659-160">Przydziela pamięć na stosie.</span><span class="sxs-lookup"><span data-stu-id="11659-160">Allocates memory on the stack.</span></span>|
|<span data-ttu-id="11659-161">`fixed` Instrukcja</span><span class="sxs-lookup"><span data-stu-id="11659-161">`fixed` statement</span></span>|<span data-ttu-id="11659-162">Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.</span><span class="sxs-lookup"><span data-stu-id="11659-162">Temporarily fixes a variable so that its address may be found.</span></span>|

## <a name="c-language-specification"></a><span data-ttu-id="11659-163">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11659-163">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="11659-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11659-164">See also</span></span>

- [<span data-ttu-id="11659-165">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="11659-165">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="11659-166">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="11659-166">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="11659-167">Konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="11659-167">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="11659-168">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="11659-168">Pointer Expressions</span></span>](pointer-expressions.md)
- [<span data-ttu-id="11659-169">Typy</span><span class="sxs-lookup"><span data-stu-id="11659-169">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="11659-170">unsafe</span><span class="sxs-lookup"><span data-stu-id="11659-170">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="11659-171">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="11659-171">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="11659-172">stackalloc</span><span class="sxs-lookup"><span data-stu-id="11659-172">stackalloc</span></span>](../../language-reference/keywords/stackalloc.md)
- [<span data-ttu-id="11659-173">Konwersja boxing i konwersja unboxing</span><span class="sxs-lookup"><span data-stu-id="11659-173">Boxing and Unboxing</span></span>](../types/boxing-and-unboxing.md)
