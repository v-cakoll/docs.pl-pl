---
title: Korzystanie z konstruktorów — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 7c227b61c6d5b4ead00fced0dba046b90683fde1
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626415"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="52b2c-102">Używanie konstruktorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="52b2c-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="52b2c-103">Gdy tworzona jest [Klasa](../../language-reference/keywords/class.md) lub [Struktura](../../language-reference/builtin-types/struct.md) , jego Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="52b2c-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="52b2c-104">Konstruktory mają taką samą nazwę jak Klasa lub struktura i zazwyczaj inicjują elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="52b2c-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="52b2c-105">W poniższym przykładzie Klasa o nazwie `Taxi` jest definiowana przy użyciu prostego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="52b2c-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="52b2c-106">Ta klasa jest następnie tworzona przy użyciu operatora [New](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="52b2c-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="52b2c-107">Konstruktor `Taxi` jest wywoływany przez operatora `new` natychmiast po przydzieleniu pamięci dla nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="52b2c-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="52b2c-108">Konstruktor, który nie pobiera parametrów, jest nazywany *konstruktorem bez parametrów*.</span><span class="sxs-lookup"><span data-stu-id="52b2c-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="52b2c-109">Konstruktory bez parametrów są wywoływane za każdym razem, gdy obiekt jest skonkretyzowany przy użyciu operatora `new` i żadne argumenty nie są dostarczane do `new`.</span><span class="sxs-lookup"><span data-stu-id="52b2c-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="52b2c-110">Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="52b2c-111">O ile Klasa nie jest [statyczna](../../language-reference/keywords/static.md), klasy bez konstruktorów uzyskują publiczny Konstruktor bezparametrowy przez C# kompilator w celu włączenia tworzenia wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="52b2c-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="52b2c-112">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="52b2c-113">Można zapobiec tworzeniu wystąpienia klasy przez uczynienie konstruktora prywatnym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="52b2c-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="52b2c-114">Aby uzyskać więcej informacji, zobacz [prywatne konstruktory](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="52b2c-115">Konstruktory dla typów [struktur](../../language-reference/builtin-types/struct.md) przypominają konstruktory klas, ale `structs` nie może zawierać jawnego konstruktora bez parametrów, ponieważ jeden jest dostarczany automatycznie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="52b2c-115">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="52b2c-116">Ten konstruktor inicjuje każde pole w `struct` do [wartości domyślnej](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-116">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="52b2c-117">Jednak ten konstruktor bez parametrów jest wywoływany tylko wtedy, gdy `struct` jest tworzona przy użyciu `new`.</span><span class="sxs-lookup"><span data-stu-id="52b2c-117">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="52b2c-118">Na przykład, ten kod używa konstruktora bez parametrów dla <xref:System.Int32>, aby mieć pewność, że liczba całkowita została zainicjowana:</span><span class="sxs-lookup"><span data-stu-id="52b2c-118">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="52b2c-119">Poniższy kod powoduje jednak błąd kompilatora, ponieważ nie używa `new`i ponieważ próbuje użyć obiektu, który nie został zainicjowany:</span><span class="sxs-lookup"><span data-stu-id="52b2c-119">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="52b2c-120">Alternatywnie obiekty oparte na `structs` (w tym wszystkie wbudowane typy liczbowe) mogą być inicjowane lub przypisywane, a następnie używane jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="52b2c-120">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="52b2c-121">Wywołanie konstruktora bez parametrów dla typu wartości nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="52b2c-121">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="52b2c-122">Obie klasy i `structs` mogą definiować konstruktory przyjmujące parametry.</span><span class="sxs-lookup"><span data-stu-id="52b2c-122">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="52b2c-123">Konstruktory, które pobierają parametry, muszą być wywoływane za pomocą instrukcji `new` lub instrukcji [bazowej](../../language-reference/keywords/base.md) .</span><span class="sxs-lookup"><span data-stu-id="52b2c-123">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="52b2c-124">Klasy i `structs` mogą również definiować wiele konstruktorów, a żaden z nich nie jest wymagany do definiowania konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="52b2c-124">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="52b2c-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="52b2c-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="52b2c-126">Tę klasę można utworzyć przy użyciu jednej z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="52b2c-126">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="52b2c-127">Konstruktor może użyć słowa kluczowego `base` do wywołania konstruktora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="52b2c-127">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="52b2c-128">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="52b2c-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="52b2c-129">W tym przykładzie Konstruktor klasy bazowej jest wywoływany przed wykonaniem bloku dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="52b2c-129">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="52b2c-130">Słowo kluczowe `base` może być używane z parametrami lub bez nich.</span><span class="sxs-lookup"><span data-stu-id="52b2c-130">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="52b2c-131">Wszystkie parametry konstruktora mogą służyć jako parametry do `base`lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="52b2c-131">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="52b2c-132">Aby uzyskać więcej informacji, zobacz temat [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-132">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="52b2c-133">W klasie pochodnej, jeśli Konstruktor klasy bazowej nie jest jawnie wywoływany za pomocą słowa kluczowego `base`, Konstruktor bez parametrów, jeśli istnieje, jest wywoływana niejawnie.</span><span class="sxs-lookup"><span data-stu-id="52b2c-133">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="52b2c-134">Oznacza to, że następujące deklaracje konstruktora są efektywnie takie same:</span><span class="sxs-lookup"><span data-stu-id="52b2c-134">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="52b2c-135">Jeśli klasa bazowa nie oferuje konstruktora bez parametrów, Klasa pochodna musi jawnie wywołać konstruktora podstawowego przy użyciu `base`.</span><span class="sxs-lookup"><span data-stu-id="52b2c-135">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="52b2c-136">Konstruktor może wywołać innego konstruktora w tym samym obiekcie za pomocą słowa kluczowego [this](../../language-reference/keywords/this.md) .</span><span class="sxs-lookup"><span data-stu-id="52b2c-136">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="52b2c-137">Podobnie jak `base`, `this` może być używany z parametrami lub bez nich, a wszystkie parametry w Konstruktorze są dostępne jako parametry `this`lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="52b2c-137">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="52b2c-138">Na przykład Drugi Konstruktor w poprzednim przykładzie można napisać ponownie przy użyciu `this`:</span><span class="sxs-lookup"><span data-stu-id="52b2c-138">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="52b2c-139">Użycie słowa kluczowego `this` w poprzednim przykładzie powoduje, że ten konstruktor jest wywoływany:</span><span class="sxs-lookup"><span data-stu-id="52b2c-139">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="52b2c-140">Konstruktory mogą być oznaczone jako [publiczne](../../language-reference/keywords/public.md), [prywatne](../../language-reference/keywords/private.md), [chronione](../../language-reference/keywords/protected.md), [wewnętrzne](../../language-reference/keywords/internal.md), [chronione wewnętrznie](../../language-reference/keywords/protected-internal.md) lub [chronione prywatnie](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-140">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="52b2c-141">Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą tworzyć klasy.</span><span class="sxs-lookup"><span data-stu-id="52b2c-141">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="52b2c-142">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-142">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="52b2c-143">Konstruktor może być zadeklarowany jako statyczny za pomocą słowa kluczowego [static](../../language-reference/keywords/static.md) .</span><span class="sxs-lookup"><span data-stu-id="52b2c-143">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="52b2c-144">Konstruktory statyczne są wywoływane automatycznie, bezpośrednio przed uzyskaniem dostępu do dowolnych pól statycznych i są zwykle używane do inicjowania statycznych elementów członkowskich klas.</span><span class="sxs-lookup"><span data-stu-id="52b2c-144">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="52b2c-145">Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="52b2c-145">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="52b2c-146">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="52b2c-146">C# Language Specification</span></span>  

<span data-ttu-id="52b2c-147">Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](~/_csharplang/spec/classes.md#instance-constructors) i [konstruktory statyczne](~/_csharplang/spec/classes.md#static-constructors) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="52b2c-147">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="52b2c-148">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="52b2c-148">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="52b2c-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52b2c-149">See also</span></span>

- [<span data-ttu-id="52b2c-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="52b2c-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="52b2c-151">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="52b2c-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="52b2c-152">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="52b2c-152">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="52b2c-153">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="52b2c-153">Finalizers</span></span>](./destructors.md)
