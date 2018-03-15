---
title: "Typy wskaźników (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe7b926bdf9f662d25f2fe960b51fc8254b7aa3a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="64245-102">Typy wskaźników (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="64245-102">Pointer types (C# Programming Guide)</span></span>
<span data-ttu-id="64245-103">W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="64245-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="64245-104">Deklaracja typu wskaźnika ma jedną z następujących form:</span><span class="sxs-lookup"><span data-stu-id="64245-104">A pointer type declaration takes one of the following forms:</span></span>  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 <span data-ttu-id="64245-105">Dowolny z następujących typów może być typem wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="64245-105">Any of the following types may be a pointer type:</span></span>  
  
-   <span data-ttu-id="64245-106">[SByte —](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [ długie](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), [dziesiętną](../../../csharp/language-reference/keywords/decimal.md), lub [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="64245-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), or [bool](../../../csharp/language-reference/keywords/bool.md).</span></span>  
  
-   <span data-ttu-id="64245-107">Wszelkie [wyliczenia](../../../csharp/language-reference/keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="64245-107">Any [enum](../../../csharp/language-reference/keywords/enum.md) type.</span></span>  
  
-   <span data-ttu-id="64245-108">Dowolny typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="64245-108">Any pointer type.</span></span>  
  
-   <span data-ttu-id="64245-109">Dowolny typ struktury zdefiniowany przez użytkownika, który zawiera tylko pola niezarządzanych typów.</span><span class="sxs-lookup"><span data-stu-id="64245-109">Any user-defined struct type that contains fields of unmanaged types only.</span></span>  
  
 <span data-ttu-id="64245-110">Typy wskaźników dziedziczy [obiektu](../../../csharp/language-reference/keywords/object.md) i konwersji między typami wskaźników i `object`.</span><span class="sxs-lookup"><span data-stu-id="64245-110">Pointer types do not inherit from [object](../../../csharp/language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="64245-111">Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania.</span><span class="sxs-lookup"><span data-stu-id="64245-111">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="64245-112">Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="64245-112">However, you can convert between different pointer types and between pointer types and integral types.</span></span>  
  
 <span data-ttu-id="64245-113">W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (\*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="64245-113">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="64245-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="64245-114">For example:</span></span>  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 <span data-ttu-id="64245-115">Wskaźnik nie może wskazywać na odwołania lub do [struktury](../../../csharp/language-reference/keywords/struct.md) zawierający odwołań, ponieważ odwołanie do obiektu może być bezużytecznych nawet wtedy, gdy wskaźnik wskazuje go.</span><span class="sxs-lookup"><span data-stu-id="64245-115">A pointer cannot point to a reference or to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="64245-116">Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="64245-116">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>  
  
 <span data-ttu-id="64245-117">Wartość zmiennej wskaźnika typu `myType*` adres zmiennej typu `myType`.</span><span class="sxs-lookup"><span data-stu-id="64245-117">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="64245-118">Poniżej przedstawiono przykłady deklaracji typów wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="64245-118">The following are examples of pointer type declarations:</span></span>  
  
|<span data-ttu-id="64245-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="64245-119">Example</span></span>|<span data-ttu-id="64245-120">Opis</span><span class="sxs-lookup"><span data-stu-id="64245-120">Description</span></span>|  
|-------------|-----------------|  
|`int* p`|<span data-ttu-id="64245-121">`p` jest wskaźnik do wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="64245-121">`p` is a pointer to an integer.</span></span>|  
|`int** p`|<span data-ttu-id="64245-122">`p` jest wskaźnik na wskaźnik do wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="64245-122">`p` is a pointer to a pointer to an integer.</span></span>|  
|`int*[] p`|<span data-ttu-id="64245-123">`p` jest jednowymiarowej tablicy wskaźników do liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="64245-123">`p` is a single-dimensional array of pointers to integers.</span></span>|  
|`char* p`|<span data-ttu-id="64245-124">`p` jest wskaźnik do znaku.</span><span class="sxs-lookup"><span data-stu-id="64245-124">`p` is a pointer to a char.</span></span>|  
|`void* p`|<span data-ttu-id="64245-125">`p` jest wskaźnik do nieznanego typu.</span><span class="sxs-lookup"><span data-stu-id="64245-125">`p` is a pointer to an unknown type.</span></span>|  
  
 <span data-ttu-id="64245-126">Operatora pośredniego wskaźnika \* można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową.</span><span class="sxs-lookup"><span data-stu-id="64245-126">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="64245-127">Na przykład przeanalizujmy następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="64245-127">For example, consider the following declaration:</span></span>  
  
```  
int* myVariable;  
```  
  
 <span data-ttu-id="64245-128">Wyrażenie `*myVariable` oznacza `int` znaleziono pod adresem zawarte w zmiennej `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="64245-128">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>  
  
 <span data-ttu-id="64245-129">Istnieje kilka przykładów wskaźniki w tematach [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) i [konwersje wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="64245-129">There are several examples of pointers in the topics [fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span>  <span data-ttu-id="64245-130">W poniższym przykładzie przedstawiono potrzebę `unsafe` — słowo kluczowe i `fixed` instrukcji i jak zwiększać wskaźnik wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="64245-130">The following example shows the need for the `unsafe` keyword and the `fixed` statement, and how to increment an interior pointer.</span></span>  <span data-ttu-id="64245-131">Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="64245-131">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="64245-132">(Należy pamiętać o włączeniu niebezpieczny kod w **projektanta projektu**; wybierz **projektu**, **właściwości** menu, a następnie wybierz opcję **niebezpiecznego kodu** w **kompilacji** kartę.)</span><span class="sxs-lookup"><span data-stu-id="64245-132">(Remember to enable unsafe code in the **Project Designer**; choose **Project**, **Properties** on the menu bar, and then select **Allow unsafe code** in the **Build** tab.)</span></span>  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 <span data-ttu-id="64245-133">Nie można zastosować operator pośredni wskaźnik typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="64245-133">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="64245-134">Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="64245-134">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>  
  
 <span data-ttu-id="64245-135">Wskaźnik może być `null`.</span><span class="sxs-lookup"><span data-stu-id="64245-135">A pointer can be `null`.</span></span> <span data-ttu-id="64245-136">Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.</span><span class="sxs-lookup"><span data-stu-id="64245-136">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>  
  
 <span data-ttu-id="64245-137">Należy pamiętać, że przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="64245-137">Be aware that passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="64245-138">Należy wziąć pod uwagę metodę, która zwraca wskaźnik do zmiennej lokalnej za pośrednictwem `in`, `out` lub `ref` parametru lub w wyniku funkcji.</span><span class="sxs-lookup"><span data-stu-id="64245-138">Consider a method that returns a pointer to a local variable through an `in`, `out` or `ref` parameter or as the function result.</span></span> <span data-ttu-id="64245-139">Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.</span><span class="sxs-lookup"><span data-stu-id="64245-139">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>  
  
 <span data-ttu-id="64245-140">W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:</span><span class="sxs-lookup"><span data-stu-id="64245-140">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>  
  
|<span data-ttu-id="64245-141">Operator/instrukcja</span><span class="sxs-lookup"><span data-stu-id="64245-141">Operator/Statement</span></span>|<span data-ttu-id="64245-142">Zastosowanie</span><span class="sxs-lookup"><span data-stu-id="64245-142">Use</span></span>|  
|-------------------------|---------|  
|*|<span data-ttu-id="64245-143">Wykonuje operację wskaźnika pośredniego.</span><span class="sxs-lookup"><span data-stu-id="64245-143">Performs pointer indirection.</span></span>|  
|->|<span data-ttu-id="64245-144">Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="64245-144">Accesses a member of a struct through a pointer.</span></span>|  
|<span data-ttu-id="64245-145">[]</span><span class="sxs-lookup"><span data-stu-id="64245-145">[]</span></span>|<span data-ttu-id="64245-146">Indeksuje wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="64245-146">Indexes a pointer.</span></span>|  
|`&`|<span data-ttu-id="64245-147">Uzyskuje adres zmiennej.</span><span class="sxs-lookup"><span data-stu-id="64245-147">Obtains the address of a variable.</span></span>|  
|<span data-ttu-id="64245-148">++ oraz --</span><span class="sxs-lookup"><span data-stu-id="64245-148">++ and --</span></span>|<span data-ttu-id="64245-149">Zwiększa i zmniejsza wartość wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="64245-149">Increments and decrements pointers.</span></span>|  
|<span data-ttu-id="64245-150">+ oraz -</span><span class="sxs-lookup"><span data-stu-id="64245-150">+ and -</span></span>|<span data-ttu-id="64245-151">Wykonuje operacje arytmetyczne na wskaźniku.</span><span class="sxs-lookup"><span data-stu-id="64245-151">Performs pointer arithmetic.</span></span>|  
|<span data-ttu-id="64245-152">==,! =, \<, >, \<=, a > =</span><span class="sxs-lookup"><span data-stu-id="64245-152">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="64245-153">Porównuje wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="64245-153">Compares pointers.</span></span>|  
|`stackalloc`|<span data-ttu-id="64245-154">Przydziela pamięć na stosie.</span><span class="sxs-lookup"><span data-stu-id="64245-154">Allocates memory on the stack.</span></span>|  
|<span data-ttu-id="64245-155">`fixed` — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="64245-155">`fixed` statement</span></span>|<span data-ttu-id="64245-156">Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.</span><span class="sxs-lookup"><span data-stu-id="64245-156">Temporarily fixes a variable so that its address may be found.</span></span>|  
  
## <a name="c-language-specification"></a><span data-ttu-id="64245-157">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="64245-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64245-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64245-158">See Also</span></span>  
 [<span data-ttu-id="64245-159">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="64245-159">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="64245-160">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="64245-160">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="64245-161">Konwersje wskaźników</span><span class="sxs-lookup"><span data-stu-id="64245-161">Pointer Conversions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [<span data-ttu-id="64245-162">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="64245-162">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="64245-163">Typy</span><span class="sxs-lookup"><span data-stu-id="64245-163">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="64245-164">unsafe</span><span class="sxs-lookup"><span data-stu-id="64245-164">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="64245-165">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="64245-165">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="64245-166">stackalloc</span><span class="sxs-lookup"><span data-stu-id="64245-166">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)  
 [<span data-ttu-id="64245-167">Konwersja boxing i konwersja unboxing</span><span class="sxs-lookup"><span data-stu-id="64245-167">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
