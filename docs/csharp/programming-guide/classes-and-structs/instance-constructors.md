---
title: Konstruktory instancji — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964738"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="31d9d-102">Konstruktory wystąpień (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="31d9d-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="31d9d-103">Konstruktory wystąpienia są używane do tworzenia i inicjowania zmiennych członkowskich wystąpienia, gdy nowe [wyrażenie](../../language-reference/operators/new-operator.md) służy do tworzenia obiektu [klasy](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="31d9d-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="31d9d-104">Aby zainicjować klasę [statyczną](../../language-reference/keywords/static.md) lub zmienne statyczne w klasie niestatycznej, należy zdefiniować konstruktora statycznego.</span><span class="sxs-lookup"><span data-stu-id="31d9d-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="31d9d-105">Aby uzyskać więcej informacji, zobacz [Konstruktora statyczne](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="31d9d-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="31d9d-106">W poniższym przykładzie przedstawiono konstruktora wystąpienia:</span><span class="sxs-lookup"><span data-stu-id="31d9d-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="31d9d-107">Dla jasności ta klasa zawiera pola publiczne.</span><span class="sxs-lookup"><span data-stu-id="31d9d-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="31d9d-108">Korzystanie z pól publicznych nie jest zalecaną praktyką programowania, ponieważ umożliwia dowolną metodę w dowolnym miejscu w programie nieograniczony i niezweryfikowany dostęp do wewnętrznego działania obiektu.</span><span class="sxs-lookup"><span data-stu-id="31d9d-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="31d9d-109">Elementy członkowskie danych zazwyczaj powinny być prywatne i powinny być dostępne tylko za pośrednictwem metod i właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="31d9d-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="31d9d-110">To wystąpienie konstruktora jest wywoływana `Coords` za każdym razem, gdy obiekt oparty na klasie jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="31d9d-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="31d9d-111">Konstruktora, jak ten, który nie przyjmuje żadnych argumentów, jest nazywany *konstruktorem bezparametrów*.</span><span class="sxs-lookup"><span data-stu-id="31d9d-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="31d9d-112">Jednak często jest przydatne, aby zapewnić dodatkowe konstruktory.</span><span class="sxs-lookup"><span data-stu-id="31d9d-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="31d9d-113">Na przykład możemy dodać konstruktora do `Coords` klasy, która pozwala nam określić początkowe wartości dla elementów członkowskich danych:</span><span class="sxs-lookup"><span data-stu-id="31d9d-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="31d9d-114">Dzięki `Coords` temu obiekty mogą być tworzone z domyślnymi lub określonymi wartościami początkowymi, takimi jak ten:</span><span class="sxs-lookup"><span data-stu-id="31d9d-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="31d9d-115">Jeśli klasa nie ma konstruktora, konstruktor bezparametrów jest generowany automatycznie, a wartości domyślne są używane do inicjowania pól obiektów.</span><span class="sxs-lookup"><span data-stu-id="31d9d-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="31d9d-116">Na przykład [int](../../language-reference/builtin-types/integral-numeric-types.md) jest inicjowany do 0.</span><span class="sxs-lookup"><span data-stu-id="31d9d-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="31d9d-117">Aby uzyskać informacje o wartościach domyślnych typu, zobacz [Wartości domyślne typów Języka C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="31d9d-117">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="31d9d-118">W związku `Coords` z tym ponieważ klasy konstruktora bez parametrów inicjuje wszystkie elementy członkowskie danych do zera, można usunąć całkowicie bez zmiany sposobu działania klasy.</span><span class="sxs-lookup"><span data-stu-id="31d9d-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="31d9d-119">Pełny przykład przy użyciu wielu konstruktorów znajduje się w przykładzie 1 w dalszej części tego tematu, a przykład automatycznie generowanekonstruktora znajduje się w przykładzie 2.</span><span class="sxs-lookup"><span data-stu-id="31d9d-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="31d9d-120">Konstruktorów wystąpienia można również wywołać konstruktory wystąpienia klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="31d9d-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="31d9d-121">Konstruktor klasy może wywołać konstruktora klasy podstawowej za pośrednictwem inicjatora, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="31d9d-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="31d9d-122">W tym przykładzie `Circle` klasa przekazuje wartości reprezentujące promień i `Shape` wysokość `Circle` do konstruktora dostarczonego przez którego pochodzi.</span><span class="sxs-lookup"><span data-stu-id="31d9d-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="31d9d-123">Pełny przykład `Shape` przy `Circle` użyciu i pojawia się w tym temacie jako przykład 3.</span><span class="sxs-lookup"><span data-stu-id="31d9d-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="31d9d-124">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="31d9d-124">Example 1</span></span>  
 <span data-ttu-id="31d9d-125">W poniższym przykładzie przedstawiono klasę z dwoma konstruktorami klas, jeden bez argumentów i jeden z dwoma argumentami.</span><span class="sxs-lookup"><span data-stu-id="31d9d-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="31d9d-126">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="31d9d-126">Example 2</span></span>  
 <span data-ttu-id="31d9d-127">W tym przykładzie `Person` klasa nie ma żadnych konstruktorów, w którym to przypadku konstruktor bezparametrów jest automatycznie dostarczany, a pola są inicjowane do ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="31d9d-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="31d9d-128">Należy zauważyć, że `age` `0` wartością domyślną `name` `null`jest i wartość domyślna jest .</span><span class="sxs-lookup"><span data-stu-id="31d9d-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="31d9d-129">Przykład 3</span><span class="sxs-lookup"><span data-stu-id="31d9d-129">Example 3</span></span>  
 <span data-ttu-id="31d9d-130">W poniższym przykładzie przedstawiono przy użyciu inicjatora klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="31d9d-130">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="31d9d-131">Klasa `Circle` jest pochodną klasy `Shape`ogólnej, `Cylinder` a klasa jest `Circle` pochodną klasy.</span><span class="sxs-lookup"><span data-stu-id="31d9d-131">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="31d9d-132">Konstruktor na każdej klasy pochodnej używa jego inicjatorklasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="31d9d-132">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="31d9d-133">Aby uzyskać więcej przykładów na wywoływanie konstruktorów klasy podstawowej, zobacz [wirtualne](../../language-reference/keywords/virtual.md), [zastąpić](../../language-reference/keywords/override.md)i [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="31d9d-133">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d9d-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31d9d-134">See also</span></span>

- [<span data-ttu-id="31d9d-135">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="31d9d-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="31d9d-136">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="31d9d-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="31d9d-137">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="31d9d-137">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="31d9d-138">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="31d9d-138">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="31d9d-139">Statyczne</span><span class="sxs-lookup"><span data-stu-id="31d9d-139">static</span></span>](../../language-reference/keywords/static.md)
