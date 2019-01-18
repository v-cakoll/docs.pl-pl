---
title: Konwersje rzutowania i typ - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 8753e977007e46ea4227c8c0072671a2e9298645
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362135"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="bf480-102">Konwersje rzutowania i typ (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="bf480-102">Casting and type conversions (C# Programming Guide)</span></span>

<span data-ttu-id="bf480-103">Ponieważ C# to typowany statycznie w czasie kompilacji, po zadeklarowaniu zmiennej, nie można ponownie zadeklarować lub przypisaną wartością innego typu, chyba że tego typu jest niejawnie konwertowany na typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="bf480-103">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or assigned a value of another type unless that type is implicitly convertible to the variable's type.</span></span> <span data-ttu-id="bf480-104">Na przykład `string` nie może być niejawnie konwertowane na `int`.</span><span class="sxs-lookup"><span data-stu-id="bf480-104">For example, the `string` cannot be implicitly converted to `int`.</span></span> <span data-ttu-id="bf480-105">W związku z tym, gdy Deklarujesz `i` jako `int`, nie można przypisać ciąg "Hello", co ilustruje poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="bf480-105">Therefore, after you declare `i` as an `int`, you cannot assign the string "Hello" to it, as the following code shows:</span></span>
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 <span data-ttu-id="bf480-106">Jednak czasami może być konieczne Kopiowanie wartości do zmiennej lub metoda parametr innego typu.</span><span class="sxs-lookup"><span data-stu-id="bf480-106">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="bf480-107">Na przykład, Niewykluczone, że zmienna typu Liczba całkowita, który chcesz przekazać do metody, w której parametr jest wpisana jako `double`.</span><span class="sxs-lookup"><span data-stu-id="bf480-107">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="bf480-108">Można też przypisać zmiennej klasy do zmiennej typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bf480-108">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="bf480-109">Te rodzaje operacji są nazywane *konwersje typów*.</span><span class="sxs-lookup"><span data-stu-id="bf480-109">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="bf480-110">W języku C# należy wykonać następujące rodzaje konwersje:</span><span class="sxs-lookup"><span data-stu-id="bf480-110">In C#, you can perform the following kinds of conversions:</span></span>  
  
-   <span data-ttu-id="bf480-111">**Niejawne konwersje**: Nie specjalnej składni jest wymagana, ponieważ konwersja jest bezpiecznym typem, a żadne dane nie zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="bf480-111">**Implicit conversions**: No special syntax is required because the conversion is type safe and no data will be lost.</span></span> <span data-ttu-id="bf480-112">Przykłady obejmują konwersji z mniejszych na większych typów całkowitych i konwersje z klasy podstawowej w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="bf480-112">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>  
  
-   <span data-ttu-id="bf480-113">**Konwersje jawne (rzutowania)**: Konwersje jawne wymaga operatora rzutowania.</span><span class="sxs-lookup"><span data-stu-id="bf480-113">**Explicit conversions (casts)**: Explicit conversions require a cast operator.</span></span> <span data-ttu-id="bf480-114">Rzutowanie jest wymagane, gdy informacji może zostać utracone podczas konwersji, lub gdy Konwersja może się nie powieść z innych przyczyn.</span><span class="sxs-lookup"><span data-stu-id="bf480-114">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span>  <span data-ttu-id="bf480-115">Typowe przykłady obejmują numerycznej konwersji do typu, który ma mniejszą dokładność i mniejszy zakres i konwersja wystąpienia klasy bazowej do klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="bf480-115">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>  
  
-   <span data-ttu-id="bf480-116">**Konwersje zdefiniowane przez użytkownika**: Konwersje zdefiniowane przez użytkownika są wykonywane przez specjalne metody, które można zdefiniować umożliwia jawne i niejawne konwersje między typami niestandardowych, które nie mają relacji — Klasa pochodna klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="bf480-116">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="bf480-117">Aby uzyskać więcej informacji, zobacz [operatory konwersji](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="bf480-117">For more information, see [Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>  
  
-   <span data-ttu-id="bf480-118">**Konwersje z klas pomocniczych**: Do konwersji między typami niezgodnych, takich jak liczby całkowite i <xref:System.DateTime?displayProperty=nameWithType> obiektów, lub ciągów szesnastkowych i tablice typu byte, możesz użyć <xref:System.BitConverter?displayProperty=nameWithType> klasy <xref:System.Convert?displayProperty=nameWithType> klasy i `Parse` metod typu liczbowego wbudowanych typów, takich jak <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bf480-118">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=nameWithType> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=nameWithType> class, the <xref:System.Convert?displayProperty=nameWithType> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bf480-119">Aby uzyskać więcej informacji, zobacz [jak: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: Konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), i [jak: Konwertowanie ciągów szesnastkowych, które typy liczbowe](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="bf480-119">For more information, see [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), and [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="bf480-120">Niejawne konwersje</span><span class="sxs-lookup"><span data-stu-id="bf480-120">Implicit conversions</span></span>

 <span data-ttu-id="bf480-121">Dla wbudowanych typów liczbowych można wprowadzić niejawną konwersję, gdy wartość ma być przechowywany można dopasować do zmiennej bez są obcięte lub zaokrąglony.</span><span class="sxs-lookup"><span data-stu-id="bf480-121">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="bf480-122">Na przykład zmienna typu [długie](../../../csharp/language-reference/keywords/long.md) (64-bitowa liczba całkowita) można przechowywać wszystkie wartości [int](../../../csharp/language-reference/keywords/int.md) (32-bitowa liczba całkowita) można przechowywać.</span><span class="sxs-lookup"><span data-stu-id="bf480-122">For example, a variable of type [long](../../../csharp/language-reference/keywords/long.md) (64-bit integer) can store any value that an [int](../../../csharp/language-reference/keywords/int.md) (32-bit integer) can store.</span></span> <span data-ttu-id="bf480-123">W poniższym przykładzie, kompilator niejawnie konwertuje wartość `num` po prawej stronie na typ `long` przed przypisaniem go do `bigNum`.</span><span class="sxs-lookup"><span data-stu-id="bf480-123">In the following example, the compiler implicitly converts the value of `num` on the right to a type `long` before assigning it to `bigNum`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 <span data-ttu-id="bf480-124">Aby uzyskać pełną listę wszystkich niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="bf480-124">For a complete list of all implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="bf480-125">Dla typów odwołań istnieje niejawna konwersja zawsze z klasy do jednej z jego bezpośredniej lub pośredniej klasy bazowej lub interfejsów.</span><span class="sxs-lookup"><span data-stu-id="bf480-125">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="bf480-126">Nie specjalnej składni jest konieczne, ponieważ klasa pochodna zawsze zawiera wszystkie elementy członkowskie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="bf480-126">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a><span data-ttu-id="bf480-127">Konwersje jawne</span><span class="sxs-lookup"><span data-stu-id="bf480-127">Explicit conversions</span></span>

 <span data-ttu-id="bf480-128">Jednakże, jeśli konwersja nie może być nawiązywane bez ryzyka utraty informacji, kompilator wymaga jednak wykonania jawnej konwersji, która jest wywoływana *rzutowania*.</span><span class="sxs-lookup"><span data-stu-id="bf480-128">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="bf480-129">Rzutowanie jest sposób jawnie informowania kompilator zamierzasz wprowadzić konwersji i że masz świadomość, może dojść do utraty danych.</span><span class="sxs-lookup"><span data-stu-id="bf480-129">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur.</span></span> <span data-ttu-id="bf480-130">Aby wykonać rzutowanie, należy określić typ, który jest Rzutowanie na w nawiasach wartość lub zmienną, które ma zostać przekonwertowany.</span><span class="sxs-lookup"><span data-stu-id="bf480-130">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="bf480-131">Poniższy program rzutowania [double](../../../csharp/language-reference/keywords/double.md) do [int](../../../csharp/language-reference/keywords/int.md). Program nie zostanie skompilowany bez rzutowania.</span><span class="sxs-lookup"><span data-stu-id="bf480-131">The following program casts a [double](../../../csharp/language-reference/keywords/double.md) to an [int](../../../csharp/language-reference/keywords/int.md). The program will not compile without the cast.</span></span>  
  
 [!code-csharp[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 <span data-ttu-id="bf480-132">Aby uzyskać listę jawnych konwersji liczbowych, które mogą zobaczyć [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="bf480-132">For a list of the explicit numeric conversions that are allowed, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="bf480-133">Dla typów odwołań jawnego rzutowania jest wymagany, jeśli chcesz przekonwertować typ pochodny od typu podstawowego:</span><span class="sxs-lookup"><span data-stu-id="bf480-133">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 <span data-ttu-id="bf480-134">Operacji rzutowania między typami odwołań nie zmienia typu środowiska wykonawczego obiektu bazowego; zmienia tylko typ wartości, który jest używany jako odwołanie do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="bf480-134">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="bf480-135">Aby uzyskać więcej informacji, zobacz [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="bf480-135">For more information, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="bf480-136">Wyjątki konwersji typu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="bf480-136">Type conversion exceptions at run time</span></span>

 <span data-ttu-id="bf480-137">W niektórych konwersji typu odwołania kompilator nie może określić, czy rzutowania będzie nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="bf480-137">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="bf480-138">Istnieje możliwość dla operacji rzutowania, skompilowany poprawnie Niepowodzenie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bf480-138">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="bf480-139">Jak pokazano w poniższym przykładzie, typ rzutowania spowoduje kończy się niepowodzeniem w czasie wykonywania <xref:System.InvalidCastException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="bf480-139">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>  
  
 [!code-csharp[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 <span data-ttu-id="bf480-140">C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatorów umożliwiających testowanie zgodności przed wykonaniem faktycznie rzutowania.</span><span class="sxs-lookup"><span data-stu-id="bf480-140">C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="bf480-141">Aby uzyskać więcej informacji, zobacz [jak: Bezpieczne rzutowanie za pomocą dopasowywania do wzorca, jak i operatory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span><span class="sxs-lookup"><span data-stu-id="bf480-141">For more information, see [How to: Safely cast using pattern matching, as and is Operators](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bf480-142">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bf480-142">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="bf480-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf480-143">See also</span></span>

- [<span data-ttu-id="bf480-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bf480-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bf480-145">Typy</span><span class="sxs-lookup"><span data-stu-id="bf480-145">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="bf480-146">(), operator</span><span class="sxs-lookup"><span data-stu-id="bf480-146">() Operator</span></span>](../../../csharp/language-reference/operators/invocation-operator.md)  
- [<span data-ttu-id="bf480-147">explicit</span><span class="sxs-lookup"><span data-stu-id="bf480-147">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
- [<span data-ttu-id="bf480-148">implicit</span><span class="sxs-lookup"><span data-stu-id="bf480-148">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
- [<span data-ttu-id="bf480-149">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="bf480-149">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [<span data-ttu-id="bf480-150">Konwersja uogólnionych typów</span><span class="sxs-lookup"><span data-stu-id="bf480-150">Generalized Type Conversion</span></span>](https://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)  
- [<span data-ttu-id="bf480-151">Konwersja typu wyeksportowanego</span><span class="sxs-lookup"><span data-stu-id="bf480-151">Exported Type Conversion</span></span>](https://msdn.microsoft.com/library/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)  
- [<span data-ttu-id="bf480-152">Instrukcje: Konwertowanie ciągu na liczbę</span><span class="sxs-lookup"><span data-stu-id="bf480-152">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
