---
title: Korzystanie z konstruktorów — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: faab6ac57629db11c60ee5b563ea95ebb90016dd
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964359"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="88694-102">Używanie konstruktorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="88694-102">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="88694-103">Gdy tworzona jest [Klasa](../../language-reference/keywords/class.md) lub [Struktura](../../language-reference/keywords/struct.md) , jego Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="88694-103">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="88694-104">Konstruktory mają taką samą nazwę jak Klasa lub struktura i zazwyczaj inicjują elementy członkowskie danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="88694-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="88694-105">W poniższym przykładzie Klasa o nazwie `Taxi` jest definiowana przy użyciu prostego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="88694-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="88694-106">Ta klasa jest następnie tworzona przy użyciu operatora [New](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="88694-106">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="88694-107">Konstruktor `Taxi` jest wywoływany przez operatora `new` natychmiast po przydzieleniu pamięci dla nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="88694-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="88694-108">Konstruktor, który nie pobiera parametrów, jest nazywany *konstruktorem bez parametrów*.</span><span class="sxs-lookup"><span data-stu-id="88694-108">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="88694-109">Konstruktory bez parametrów są wywoływane za każdym razem, gdy obiekt jest skonkretyzowany przy użyciu operatora `new` i żadne argumenty nie są dostarczane do `new`.</span><span class="sxs-lookup"><span data-stu-id="88694-109">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="88694-110">Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="88694-110">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="88694-111">O ile Klasa nie jest [statyczna](../../language-reference/keywords/static.md), klasy bez konstruktorów uzyskują publiczny Konstruktor bezparametrowy przez C# kompilator w celu włączenia tworzenia wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="88694-111">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="88694-112">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="88694-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="88694-113">Można zapobiec tworzeniu wystąpienia klasy przez uczynienie konstruktora prywatnym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="88694-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="88694-114">Aby uzyskać więcej informacji, zobacz [prywatne konstruktory](./private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="88694-114">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="88694-115">Konstruktory dla typów [struktur](../../language-reference/keywords/struct.md) przypominają konstruktory klas, ale `structs` nie może zawierać jawnego konstruktora bez parametrów, ponieważ jeden jest dostarczany automatycznie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="88694-115">Constructors for [struct](../../language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="88694-116">Ten konstruktor inicjuje każde pole w `struct` do [wartości domyślnej](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="88694-116">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="88694-117">Jednak ten konstruktor bez parametrów jest wywoływany tylko wtedy, gdy `struct` jest tworzona przy użyciu `new`.</span><span class="sxs-lookup"><span data-stu-id="88694-117">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="88694-118">Na przykład, ten kod używa konstruktora bez parametrów dla <xref:System.Int32>, aby mieć pewność, że liczba całkowita została zainicjowana:</span><span class="sxs-lookup"><span data-stu-id="88694-118">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="88694-119">Poniższy kod powoduje jednak błąd kompilatora, ponieważ nie używa `new`i ponieważ próbuje użyć obiektu, który nie został zainicjowany:</span><span class="sxs-lookup"><span data-stu-id="88694-119">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="88694-120">Alternatywnie obiekty oparte na `structs` (w tym wszystkie wbudowane typy liczbowe) mogą być inicjowane lub przypisywane, a następnie używane jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="88694-120">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="88694-121">Wywołanie konstruktora bez parametrów dla typu wartości nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="88694-121">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="88694-122">Obie klasy i `structs` mogą definiować konstruktory przyjmujące parametry.</span><span class="sxs-lookup"><span data-stu-id="88694-122">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="88694-123">Konstruktory, które pobierają parametry, muszą być wywoływane za pomocą instrukcji `new` lub instrukcji [bazowej](../../language-reference/keywords/base.md) .</span><span class="sxs-lookup"><span data-stu-id="88694-123">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="88694-124">Klasy i `structs` mogą również definiować wiele konstruktorów, a żaden z nich nie jest wymagany do definiowania konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="88694-124">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="88694-125">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="88694-125">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="88694-126">Tę klasę można utworzyć przy użyciu jednej z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="88694-126">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="88694-127">Konstruktor może użyć słowa kluczowego `base` do wywołania konstruktora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="88694-127">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="88694-128">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="88694-128">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="88694-129">W tym przykładzie Konstruktor klasy bazowej jest wywoływany przed wykonaniem bloku dla konstruktora.</span><span class="sxs-lookup"><span data-stu-id="88694-129">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="88694-130">Słowo kluczowe `base` może być używane z parametrami lub bez nich.</span><span class="sxs-lookup"><span data-stu-id="88694-130">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="88694-131">Wszystkie parametry konstruktora mogą służyć jako parametry do `base`lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="88694-131">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="88694-132">Aby uzyskać więcej informacji, zobacz temat [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="88694-132">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="88694-133">W klasie pochodnej, jeśli Konstruktor klasy bazowej nie jest jawnie wywoływany za pomocą słowa kluczowego `base`, Konstruktor bez parametrów, jeśli istnieje, jest wywoływana niejawnie.</span><span class="sxs-lookup"><span data-stu-id="88694-133">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="88694-134">Oznacza to, że następujące deklaracje konstruktora są efektywnie takie same:</span><span class="sxs-lookup"><span data-stu-id="88694-134">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="88694-135">Jeśli klasa bazowa nie oferuje konstruktora bez parametrów, Klasa pochodna musi jawnie wywołać konstruktora podstawowego przy użyciu `base`.</span><span class="sxs-lookup"><span data-stu-id="88694-135">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="88694-136">Konstruktor może wywołać innego konstruktora w tym samym obiekcie za pomocą słowa kluczowego [this](../../language-reference/keywords/this.md) .</span><span class="sxs-lookup"><span data-stu-id="88694-136">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="88694-137">Podobnie jak `base`, `this` może być używany z parametrami lub bez nich, a wszystkie parametry w Konstruktorze są dostępne jako parametry `this`lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="88694-137">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="88694-138">Na przykład Drugi Konstruktor w poprzednim przykładzie można napisać ponownie przy użyciu `this`:</span><span class="sxs-lookup"><span data-stu-id="88694-138">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="88694-139">Użycie słowa kluczowego `this` w poprzednim przykładzie powoduje, że ten konstruktor jest wywoływany:</span><span class="sxs-lookup"><span data-stu-id="88694-139">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="88694-140">Konstruktory mogą być oznaczone jako [publiczne](../../language-reference/keywords/public.md), [prywatne](../../language-reference/keywords/private.md), [chronione](../../language-reference/keywords/protected.md), [wewnętrzne](../../language-reference/keywords/internal.md), [chronione wewnętrznie](../../language-reference/keywords/protected-internal.md) lub [chronione prywatnie](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="88694-140">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="88694-141">Te Modyfikatory dostępu definiują sposób, w jaki użytkownicy klasy mogą tworzyć klasy.</span><span class="sxs-lookup"><span data-stu-id="88694-141">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="88694-142">Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="88694-142">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="88694-143">Konstruktor może być zadeklarowany jako statyczny za pomocą słowa kluczowego [static](../../language-reference/keywords/static.md) .</span><span class="sxs-lookup"><span data-stu-id="88694-143">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="88694-144">Konstruktory statyczne są wywoływane automatycznie, bezpośrednio przed uzyskaniem dostępu do dowolnych pól statycznych i są zwykle używane do inicjowania statycznych elementów członkowskich klas.</span><span class="sxs-lookup"><span data-stu-id="88694-144">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="88694-145">Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="88694-145">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="88694-146">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="88694-146">C# Language Specification</span></span>  

<span data-ttu-id="88694-147">Aby uzyskać więcej informacji, zobacz [konstruktory wystąpień](~/_csharplang/spec/classes.md#instance-constructors) i [konstruktory statyczne](~/_csharplang/spec/classes.md#static-constructors) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="88694-147">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="88694-148">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="88694-148">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="88694-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88694-149">See also</span></span>

- [<span data-ttu-id="88694-150">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="88694-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88694-151">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="88694-151">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="88694-152">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="88694-152">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="88694-153">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="88694-153">Finalizers</span></span>](./destructors.md)
