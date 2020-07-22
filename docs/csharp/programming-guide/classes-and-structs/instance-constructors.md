---
title: Konstruktory wystąpień — Przewodnik programowania w języku C#
description: Konstruktory wystąpień w języku C# Utwórz i zainicjuj wszystkie zmienne Członkowskie wystąpienia w przypadku użycia nowego wyrażenia do utworzenia obiektu klasy.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: d70e786446fb198afb4e0311757cacb65b706f47
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864205"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="b666d-103">Konstruktory wystąpień (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="b666d-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="b666d-104">Konstruktory wystąpień są używane do tworzenia i inicjowania wszelkich zmiennych składowych wystąpienia podczas używania [nowego](../../language-reference/operators/new-operator.md) wyrażenia do tworzenia obiektu [klasy](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="b666d-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="b666d-105">Aby zainicjować klasę [statyczną](../../language-reference/keywords/static.md) lub zmienne statyczne w klasie niestatycznej, należy zdefiniować Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="b666d-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="b666d-106">Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="b666d-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="b666d-107">Poniższy przykład pokazuje Konstruktor wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="b666d-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="b666d-108">Dla jasności Ta klasa zawiera pola publiczne.</span><span class="sxs-lookup"><span data-stu-id="b666d-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="b666d-109">Korzystanie z pól publicznych nie jest zalecanym sposobem programowania, ponieważ umożliwia jakąkolwiek metodę w dowolnym miejscu w programie bez ograniczeń i niezweryfikowany dostęp do wewnętrznych zadań roboczych obiektu.</span><span class="sxs-lookup"><span data-stu-id="b666d-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="b666d-110">Elementy członkowskie danych powinny być ogólnie prywatne i powinny być dostępne tylko za poorednictwem metod i właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="b666d-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="b666d-111">Ten konstruktor wystąpienia jest wywoływany za każdym razem, gdy `Coords` tworzony jest obiekt oparty na klasie.</span><span class="sxs-lookup"><span data-stu-id="b666d-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="b666d-112">Konstruktor podobny do tego, który nie przyjmuje argumentów, jest nazywany *konstruktorem bez parametrów*.</span><span class="sxs-lookup"><span data-stu-id="b666d-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="b666d-113">Jednak często przydatne jest zapewnienie dodatkowych konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="b666d-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="b666d-114">Na przykład możemy dodać konstruktora do `Coords` klasy, która umożliwia określenie wartości początkowych elementów członkowskich danych:</span><span class="sxs-lookup"><span data-stu-id="b666d-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="b666d-115">Pozwala to `Coords` na tworzenie obiektów z domyślnymi lub określonymi wartościami początkowymi, takimi jak:</span><span class="sxs-lookup"><span data-stu-id="b666d-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="b666d-116">Jeśli Klasa nie ma konstruktora, zostaje automatycznie wygenerowany Konstruktor bez parametrów, a wartości domyślne są używane do inicjowania pól obiektu.</span><span class="sxs-lookup"><span data-stu-id="b666d-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="b666d-117">Na przykład liczba [całkowita](../../language-reference/builtin-types/integral-numeric-types.md) jest inicjowana do wartości 0.</span><span class="sxs-lookup"><span data-stu-id="b666d-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="b666d-118">Aby uzyskać informacje na temat typów wartości domyślnych, zobacz [domyślne wartości typów języka C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="b666d-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="b666d-119">W związku z tym, ponieważ `Coords` Konstruktor bezparametrowy klasy inicjuje wszystkie elementy członkowskie danych jako zero, można go usunąć całkowicie bez zmiany sposobu działania klasy.</span><span class="sxs-lookup"><span data-stu-id="b666d-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="b666d-120">Kompletny przykład z użyciem wielu konstruktorów znajduje się w przykładzie 1 w dalszej części tego tematu, a przykład wygenerowanego automatycznie konstruktora jest dostępny w przykładzie 2.</span><span class="sxs-lookup"><span data-stu-id="b666d-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="b666d-121">Konstruktorów wystąpień można także używać do wywoływania konstruktorów wystąpień klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="b666d-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="b666d-122">Konstruktor klasy może wywoływać konstruktora klasy podstawowej za pomocą inicjatora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b666d-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="b666d-123">W tym przykładzie `Circle` Klasa przekazuje wartości reprezentujące promień i wysokość do konstruktora dostarczonego przez, `Shape` z którego pochodzi `Circle` .</span><span class="sxs-lookup"><span data-stu-id="b666d-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="b666d-124">Kompletny przykład korzystania z `Shape` i `Circle` pojawia się w tym temacie jako przykład 3.</span><span class="sxs-lookup"><span data-stu-id="b666d-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b666d-125">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="b666d-125">Example 1</span></span>  
 <span data-ttu-id="b666d-126">Poniższy przykład ilustruje klasę z dwoma konstruktorami klas, jeden bez argumentów i jeden z dwoma argumentami.</span><span class="sxs-lookup"><span data-stu-id="b666d-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="b666d-127">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="b666d-127">Example 2</span></span>  
 <span data-ttu-id="b666d-128">W tym przykładzie Klasa nie `Person` ma żadnych konstruktorów, w tym przypadku jest automatycznie dostarczany Konstruktor bez parametrów i pola są inicjowane do ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="b666d-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="b666d-129">Zwróć uwagę, że wartość domyślna `age` to `0` i wartość domyślna `name` to `null` .</span><span class="sxs-lookup"><span data-stu-id="b666d-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="b666d-130">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="b666d-130">Example 3</span></span>  
 <span data-ttu-id="b666d-131">Poniższy przykład ilustruje użycie inicjatora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="b666d-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="b666d-132">`Circle`Klasa pochodzi od klasy ogólnej `Shape` , a `Cylinder` Klasa pochodzi od `Circle` klasy.</span><span class="sxs-lookup"><span data-stu-id="b666d-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="b666d-133">Konstruktor dla każdej klasy pochodnej używa jej inicjatora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="b666d-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="b666d-134">Aby uzyskać więcej przykładów dotyczących wywoływania konstruktorów klasy bazowej, zobacz [Virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md)i [Base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="b666d-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b666d-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b666d-135">See also</span></span>

- [<span data-ttu-id="b666d-136">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b666d-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b666d-137">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="b666d-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b666d-138">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="b666d-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b666d-139">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="b666d-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="b666d-140">static</span><span class="sxs-lookup"><span data-stu-id="b666d-140">static</span></span>](../../language-reference/keywords/static.md)
