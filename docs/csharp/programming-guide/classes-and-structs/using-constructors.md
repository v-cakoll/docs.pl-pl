---
title: Używanie konstruktorów (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: b19676b2549bbb54af7fb1d72ff0e98352c61383
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529023"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="70040-102">Używanie konstruktorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="70040-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="70040-103">Gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzone, jego konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="70040-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="70040-104">Konstruktory mają taką samą nazwę jak klasy lub struktury, a zwykle inicjują członków danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="70040-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="70040-105">W poniższym przykładzie klasę o nazwie `Taxi` jest zdefiniowana za pomocą prostego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="70040-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="70040-106">Ta klasa jest następnie utworzone za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="70040-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="70040-107">`Taxi` Konstruktor jest wywoływany przez `new` operator natychmiast po pamięci zarezerwowanej dla nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="70040-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 <span data-ttu-id="70040-108">Wywoływany jest konstruktor, który nie przyjmuje żadnych parametrów *domyślnego konstruktora*.</span><span class="sxs-lookup"><span data-stu-id="70040-108">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="70040-109">Konstruktory domyślne są wywoływane zawsze wtedy, gdy jest tworzone wystąpienie obiektu za pomocą `new` operatora i żadne argumenty, które zostały udostępnione firmie `new`.</span><span class="sxs-lookup"><span data-stu-id="70040-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="70040-110">Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="70040-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="70040-111">Chyba, że klasa jest [statyczne](../../../csharp/language-reference/keywords/static.md), klasy bez konstruktory są podane publicznego konstruktora domyślnego przez kompilator języka C# w celu umożliwienia tworzenia wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="70040-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="70040-112">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="70040-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="70040-113">Klasę można zapobiec uruchamianiu przez Konstruktor prywatny, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="70040-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 <span data-ttu-id="70040-114">Aby uzyskać więcej informacji, zobacz [konstruktory prywatne](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="70040-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="70040-115">Konstruktory [struktury](../../../csharp/language-reference/keywords/struct.md) typy przypominają Konstruktory klasy, ale `structs` nie może zawierać jawne domyślnego konstruktora, ponieważ zostało ono określone automatycznie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="70040-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="70040-116">Ten konstruktor inicjuje wszystkie pola w `struct` do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="70040-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="70040-117">Aby uzyskać więcej informacji, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="70040-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="70040-118">Jednak to domyślny konstruktor jest wywoływana tylko jeśli `struct` jest utworzone za pomocą `new`.</span><span class="sxs-lookup"><span data-stu-id="70040-118">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="70040-119">Na przykład, ten kod używa domyślnego konstruktora dla <xref:System.Int32>, dzięki czemu są pewność, że liczba całkowita jest zainicjowany:</span><span class="sxs-lookup"><span data-stu-id="70040-119">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="70040-120">Poniższy kod, jednak powoduje błąd kompilatora, ponieważ nie używa `new`, a ponieważ próbuje użyć obiektu, który nie został zainicjowany:</span><span class="sxs-lookup"><span data-stu-id="70040-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="70040-121">Alternatywnie, na podstawie obiektów `structs` (w tym wbudowane typy liczbowe) mogą zostać zainicjowane lub przypisane i następnie jest używany jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="70040-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="70040-122">Dlatego wywołanie domyślnego konstruktora dla typu wartości nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="70040-122">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="70040-123">Obie klasy i `structs` mogą definiować konstruktorów, które przyjmują parametry.</span><span class="sxs-lookup"><span data-stu-id="70040-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="70040-124">Konstruktory, które przyjmują parametry musi zostać wywołana przez `new` instrukcji lub [podstawowy](../../../csharp/language-reference/keywords/base.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="70040-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="70040-125">Klasy i `structs` można również zdefiniować wiele konstruktorów i nie jest wymagany do zdefiniowania domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="70040-125">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="70040-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="70040-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 <span data-ttu-id="70040-127">Ta klasa można utworzyć przy użyciu jednej z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="70040-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 <span data-ttu-id="70040-128">Można użyć konstruktora `base` słowo kluczowe, aby wywołać konstruktora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="70040-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="70040-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="70040-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 <span data-ttu-id="70040-130">W tym przykładzie konstruktora dla klasy bazowej jest wywoływana przed wykonaniem bloku dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="70040-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="70040-131">`base` — Słowo kluczowe może być używany z bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="70040-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="70040-132">Wszelkie parametry konstruktora może służyć jako parametry `base`, lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="70040-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="70040-133">Aby uzyskać więcej informacji, zobacz [podstawowy](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="70040-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="70040-134">W klasie pochodnej, jeśli Konstruktor klasy bazowej nie jest jawnie wywoływana przy użyciu `base` — słowo kluczowe, Konstruktor domyślny, jeśli istnieje, jest wywoływana niejawnie.</span><span class="sxs-lookup"><span data-stu-id="70040-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="70040-135">Oznacza to, że następujące deklaracje Konstruktor jest praktycznie taki sam:</span><span class="sxs-lookup"><span data-stu-id="70040-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 <span data-ttu-id="70040-136">Jeśli klasa bazowa nie oferuje domyślnego konstruktora, klasy pochodnej musi utworzyć jawnym wywołaniem konstruktora bazowego przy użyciu `base`.</span><span class="sxs-lookup"><span data-stu-id="70040-136">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="70040-137">Konstruktor może wywołać innego konstruktora w ten sam obiekt przy użyciu [to](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="70040-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="70040-138">Podobnie jak `base`, `this` może być używany z lub bez parametrów i parametrów w Konstruktorze są dostępne jako parametry `this`, lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="70040-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="70040-139">Na przykład, drugi Konstruktor w poprzednim przykładzie może zostać przepisany z użyciem `this`:</span><span class="sxs-lookup"><span data-stu-id="70040-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 <span data-ttu-id="70040-140">Korzystanie z `this` — słowo kluczowe w poprzednim przykładzie powoduje, że ten konstruktor do wywołania:</span><span class="sxs-lookup"><span data-stu-id="70040-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 <span data-ttu-id="70040-141">Konstruktory może być oznaczona jako [publicznych](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md)lub [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="70040-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="70040-142">Następujące modyfikatory dostępu definiują, jak użytkownicy klasy można skonstruować klasy.</span><span class="sxs-lookup"><span data-stu-id="70040-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="70040-143">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md). </span><span class="sxs-lookup"><span data-stu-id="70040-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="70040-144">Konstruktor mogą być deklarowane statycznych przy użyciu [statyczne](../../../csharp/language-reference/keywords/static.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="70040-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="70040-145">Konstruktory statyczne są nazywane automatycznie, bezpośrednio przed wykonaniem dowolnego pola statyczne są dostępne i są zazwyczaj używane do zainicjowania statyczni członkowie klas.</span><span class="sxs-lookup"><span data-stu-id="70040-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="70040-146">Aby uzyskać więcej informacji, zobacz [konstruktorów statycznych](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="70040-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="70040-147">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="70040-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70040-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70040-148">See Also</span></span>

- [<span data-ttu-id="70040-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="70040-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="70040-150">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="70040-150">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="70040-151">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="70040-151">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="70040-152">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="70040-152">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
