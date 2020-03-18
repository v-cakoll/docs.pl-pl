---
title: Korzystanie z konstruktorów — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626415"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="d040b-102">Używanie konstruktorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d040b-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="d040b-103">Po utworzeniu [klasy](../../language-reference/keywords/class.md) lub [struktury,](../../language-reference/builtin-types/struct.md) jego konstruktor jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d040b-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="d040b-104">Konstruktorzy mają taką samą nazwę jak klasy lub struktury i zwykle inicjowania członków danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d040b-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="d040b-105">W poniższym przykładzie klasa `Taxi` o nazwie jest zdefiniowana przy użyciu prostego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d040b-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="d040b-106">Ta klasa jest następnie tworzone z [nowym](../../language-reference/operators/new-operator.md) operatorem.</span><span class="sxs-lookup"><span data-stu-id="d040b-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="d040b-107">Konstruktor `Taxi` jest wywoływany przez `new` operatora natychmiast po przydzielonym pamięci dla nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d040b-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="d040b-108">Konstruktor, który nie przyjmuje żadnych parametrów jest nazywany *konstruktorem bezparametrów*.</span><span class="sxs-lookup"><span data-stu-id="d040b-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="d040b-109">Konstruktory bezparametrów są wywoływane za każdym razem, `new` gdy obiekt jest tworzony `new`przy użyciu operatora i nie podano żadnych argumentów .</span><span class="sxs-lookup"><span data-stu-id="d040b-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="d040b-110">Aby uzyskać więcej informacji, zobacz [Konstruktora wystąpień](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="d040b-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="d040b-111">Chyba że klasa jest [statyczna](../../language-reference/keywords/static.md), klasy bez konstruktorów są podane konstruktora public parameterless przez kompilator C#, aby umożliwić wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="d040b-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="d040b-112">Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d040b-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="d040b-113">Można zapobiec klasy z wystąpienia przez co konstruktora prywatnych, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d040b-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="d040b-114">Aby uzyskać więcej informacji, zobacz [Konstruktory prywatne](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="d040b-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="d040b-115">Konstruktory dla typów [struktur](../../language-reference/builtin-types/struct.md) przypominają konstruktory klas, ale `structs` nie może zawierać jawny konstruktor bezparametrów, ponieważ jeden jest dostarczany automatycznie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d040b-115">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="d040b-116">Ten konstruktor inicjuje `struct` każde pole w [wartości domyślnej.](../../language-reference/builtin-types/default-values.md)</span><span class="sxs-lookup"><span data-stu-id="d040b-116">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="d040b-117">Jednak ten konstruktor bez parametrów `struct` jest wywoływany tylko `new`wtedy, gdy jest tworzony za pomocą .</span><span class="sxs-lookup"><span data-stu-id="d040b-117">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="d040b-118">Na przykład ten kod używa konstruktora bezparametrów dla <xref:System.Int32>, dzięki czemu masz pewność, że liczba całkowita jest inicjowana:</span><span class="sxs-lookup"><span data-stu-id="d040b-118">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="d040b-119">Poniższy kod powoduje jednak błąd kompilatora, `new`ponieważ nie używa , a ponieważ próbuje użyć obiektu, który nie został zainicjowany:</span><span class="sxs-lookup"><span data-stu-id="d040b-119">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="d040b-120">Alternatywnie obiekty oparte `structs` na (w tym wszystkie wbudowane typy liczbowe) mogą być inicjowane lub przypisywane, a następnie używane w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d040b-120">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="d040b-121">Tak więc wywołanie konstruktora bez parametrów dla typu wartości nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="d040b-121">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="d040b-122">Obie klasy `structs` i można zdefiniować konstruktory, które przyjmują parametry.</span><span class="sxs-lookup"><span data-stu-id="d040b-122">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="d040b-123">Konstruktory, które przyjmują parametry `new` muszą być wywoływane za pośrednictwem instrukcji lub [instrukcji podstawowej.](../../language-reference/keywords/base.md)</span><span class="sxs-lookup"><span data-stu-id="d040b-123">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="d040b-124">Klasy `structs` i można również zdefiniować wiele konstruktorów i nie jest wymagane do definiowania konstruktora bezparametrów.</span><span class="sxs-lookup"><span data-stu-id="d040b-124">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="d040b-125">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d040b-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="d040b-126">Tę klasę można utworzyć przy użyciu jednej z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d040b-126">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="d040b-127">Konstruktor można `base` użyć słowa kluczowego do wywołania konstruktora klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d040b-127">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="d040b-128">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d040b-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="d040b-129">W tym przykładzie konstruktora dla klasy podstawowej jest wywoływana przed blok dla konstruktora jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="d040b-129">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="d040b-130">Słowa `base` kluczowego można używać z parametrami lub bez.</span><span class="sxs-lookup"><span data-stu-id="d040b-130">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="d040b-131">Wszystkie parametry do konstruktora mogą być `base`używane jako parametry do , lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d040b-131">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="d040b-132">Aby uzyskać więcej informacji, zobacz [podstawa](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="d040b-132">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="d040b-133">W klasie pochodnej, jeśli konstruktor klasy podstawowej nie `base` jest wywoływany jawnie przy użyciu słowa kluczowego, konstruktor bezparametrów, jeśli istnieje, jest wywoływany niejawnie.</span><span class="sxs-lookup"><span data-stu-id="d040b-133">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="d040b-134">Oznacza to, że następujące deklaracje konstruktorów są skutecznie takie same:</span><span class="sxs-lookup"><span data-stu-id="d040b-134">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="d040b-135">Jeśli klasa podstawowa nie oferuje konstruktora bezparametrów, klasa pochodna musi jawne `base`wywołanie konstruktora podstawowego przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="d040b-135">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="d040b-136">Konstruktor może wywołać innego konstruktora w tym samym obiekcie przy użyciu [tego](../../language-reference/keywords/this.md) słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="d040b-136">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="d040b-137">Podobnie `base` `this` jak , może być używany z parametrami lub bez, a wszystkie `this`parametry w konstruktorze są dostępne jako parametry do , lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d040b-137">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="d040b-138">Na przykład drugi konstruktor w poprzednim przykładzie `this`można przepisać przy użyciu:</span><span class="sxs-lookup"><span data-stu-id="d040b-138">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="d040b-139">Użycie `this` słowa kluczowego w poprzednim przykładzie powoduje, że ten konstruktor ma być wywoływany:</span><span class="sxs-lookup"><span data-stu-id="d040b-139">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="d040b-140">Konstruktorzy mogą być oznaczani jako [publiczni,](../../language-reference/keywords/public.md) [prywatni, chronieni,](../../language-reference/keywords/protected.md) [private](../../language-reference/keywords/private.md) [wewnętrzni,](../../language-reference/keywords/internal.md) [chronieni wewnętrznie](../../language-reference/keywords/protected-internal.md) lub [prywatnie.](../../language-reference/keywords/private-protected.md)</span><span class="sxs-lookup"><span data-stu-id="d040b-140">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="d040b-141">Te modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą konstruować klasę.</span><span class="sxs-lookup"><span data-stu-id="d040b-141">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="d040b-142">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="d040b-142">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="d040b-143">Konstruktora można zadeklarować statyczne przy użyciu [statycznego](../../language-reference/keywords/static.md) słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="d040b-143">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="d040b-144">Konstruktory statyczne są wywoływane automatycznie, bezpośrednio przed dostępem do jakichkolwiek pól statycznych i są zwykle używane do inicjowania statycznych elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="d040b-144">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="d040b-145">Aby uzyskać więcej informacji, zobacz [Konstruktora statyczne](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="d040b-145">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d040b-146">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d040b-146">C# Language Specification</span></span>  

<span data-ttu-id="d040b-147">Aby uzyskać więcej informacji, zobacz [Konstruktory wystąpienia](~/_csharplang/spec/classes.md#instance-constructors) i [konstruktory statyczne](~/_csharplang/spec/classes.md#static-constructors) w [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)</span><span class="sxs-lookup"><span data-stu-id="d040b-147">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="d040b-148">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="d040b-148">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d040b-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d040b-149">See also</span></span>

- [<span data-ttu-id="d040b-150">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d040b-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d040b-151">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="d040b-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d040b-152">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d040b-152">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="d040b-153">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="d040b-153">Finalizers</span></span>](./destructors.md)
