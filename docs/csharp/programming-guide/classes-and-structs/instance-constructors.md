---
title: Konstruktory wystąpień C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964738"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="80f4e-102">Konstruktory wystąpień (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="80f4e-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="80f4e-103">Konstruktory wystąpień są używane do tworzenia i inicjowania wszelkich zmiennych składowych wystąpienia podczas używania [nowego](../../language-reference/operators/new-operator.md) wyrażenia do tworzenia obiektu [klasy](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="80f4e-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="80f4e-104">Aby zainicjować klasę [statyczną](../../language-reference/keywords/static.md) lub zmienne statyczne w klasie niestatycznej, należy zdefiniować Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="80f4e-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="80f4e-105">Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="80f4e-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="80f4e-106">Poniższy przykład pokazuje Konstruktor wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="80f4e-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="80f4e-107">Dla jasności Ta klasa zawiera pola publiczne.</span><span class="sxs-lookup"><span data-stu-id="80f4e-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="80f4e-108">Korzystanie z pól publicznych nie jest zalecanym sposobem programowania, ponieważ umożliwia jakąkolwiek metodę w dowolnym miejscu w programie bez ograniczeń i niezweryfikowany dostęp do wewnętrznych zadań roboczych obiektu.</span><span class="sxs-lookup"><span data-stu-id="80f4e-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="80f4e-109">Elementy członkowskie danych powinny być ogólnie prywatne i powinny być dostępne tylko za poorednictwem metod i właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="80f4e-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="80f4e-110">Ten konstruktor wystąpienia jest wywoływany za każdym razem, gdy tworzony jest obiekt oparty na klasie `Coords`.</span><span class="sxs-lookup"><span data-stu-id="80f4e-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="80f4e-111">Konstruktor podobny do tego, który nie przyjmuje argumentów, jest nazywany *konstruktorem bez parametrów*.</span><span class="sxs-lookup"><span data-stu-id="80f4e-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="80f4e-112">Jednak często przydatne jest zapewnienie dodatkowych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="80f4e-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="80f4e-113">Na przykład możemy dodać konstruktora do klasy `Coords`, która umożliwia określenie wartości początkowych elementów członkowskich danych:</span><span class="sxs-lookup"><span data-stu-id="80f4e-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="80f4e-114">Pozwala to na tworzenie `Coords` obiektów z domyślnymi lub określonymi wartościami początkowymi, takimi jak:</span><span class="sxs-lookup"><span data-stu-id="80f4e-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="80f4e-115">Jeśli Klasa nie ma konstruktora, zostaje automatycznie wygenerowany Konstruktor bez parametrów, a wartości domyślne są używane do inicjowania pól obiektu.</span><span class="sxs-lookup"><span data-stu-id="80f4e-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="80f4e-116">Na przykład liczba [całkowita](../../language-reference/builtin-types/integral-numeric-types.md) jest inicjowana do wartości 0.</span><span class="sxs-lookup"><span data-stu-id="80f4e-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="80f4e-117">Aby uzyskać informacje o typach wartości domyślnych, zobacz [domyślne wartości C# typów](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="80f4e-117">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="80f4e-118">W związku z tym, ponieważ Konstruktor bez parametrów klasy `Coords` inicjuje wszystkie elementy członkowskie danych jako zero, można go usunąć całkowicie bez zmiany sposobu działania klasy.</span><span class="sxs-lookup"><span data-stu-id="80f4e-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="80f4e-119">Kompletny przykład z użyciem wielu konstruktorów znajduje się w przykładzie 1 w dalszej części tego tematu, a przykład wygenerowanego automatycznie konstruktora jest dostępny w przykładzie 2.</span><span class="sxs-lookup"><span data-stu-id="80f4e-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="80f4e-120">Konstruktorów wystąpień można także używać do wywoływania konstruktorów wystąpień klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="80f4e-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="80f4e-121">Konstruktor klasy może wywoływać konstruktora klasy podstawowej za pomocą inicjatora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="80f4e-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="80f4e-122">W tym przykładzie Klasa `Circle` przekazuje wartości reprezentujące promień i wysokość do konstruktora dostarczonego przez `Shape`, z którego `Circle` pochodzi.</span><span class="sxs-lookup"><span data-stu-id="80f4e-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="80f4e-123">Pełny przykład przy użyciu `Shape` i `Circle` pojawia się w tym temacie jako przykład 3.</span><span class="sxs-lookup"><span data-stu-id="80f4e-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="80f4e-124">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="80f4e-124">Example 1</span></span>  
 <span data-ttu-id="80f4e-125">Poniższy przykład ilustruje klasę z dwoma konstruktorami klas, jeden bez argumentów i jeden z dwoma argumentami.</span><span class="sxs-lookup"><span data-stu-id="80f4e-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="80f4e-126">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="80f4e-126">Example 2</span></span>  
 <span data-ttu-id="80f4e-127">W tym przykładzie Klasa `Person` nie ma żadnych konstruktorów, w tym przypadku jest automatycznie dostarczany Konstruktor bez parametrów i pola są inicjowane do ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="80f4e-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="80f4e-128">Zwróć uwagę, że wartość domyślna `age` jest `0` i wartość domyślna `name` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="80f4e-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="80f4e-129">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="80f4e-129">Example 3</span></span>  
 <span data-ttu-id="80f4e-130">Poniższy przykład ilustruje użycie inicjatora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="80f4e-130">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="80f4e-131">Klasa `Circle` jest pochodną klasy ogólnej `Shape`, a Klasa `Cylinder` jest pochodną klasy `Circle`.</span><span class="sxs-lookup"><span data-stu-id="80f4e-131">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="80f4e-132">Konstruktor dla każdej klasy pochodnej używa jej inicjatora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="80f4e-132">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="80f4e-133">Aby uzyskać więcej przykładów dotyczących wywoływania konstruktorów klasy bazowej, zobacz [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)i [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="80f4e-133">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f4e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80f4e-134">See also</span></span>

- [<span data-ttu-id="80f4e-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="80f4e-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="80f4e-136">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="80f4e-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="80f4e-137">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="80f4e-137">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="80f4e-138">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="80f4e-138">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="80f4e-139">static</span><span class="sxs-lookup"><span data-stu-id="80f4e-139">static</span></span>](../../language-reference/keywords/static.md)
