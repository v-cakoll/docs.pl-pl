---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 124262695f9333ce31c4097662688e0fe30f300d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969534"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="8c5d9-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c5d9-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="8c5d9-103">Określa, że klasa może być używana tylko jako klasa bazowa i że nie można utworzyć obiektu bezpośrednio z niej.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c5d9-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c5d9-104">Remarks</span></span>  
 <span data-ttu-id="8c5d9-105">Celem *klasy bazowej* (znany także jako *abstrakcyjna klasa*) polega na zdefiniowaniu funkcji, które są wspólne dla wszystkich klas, które są od niego pochodzi.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="8c5d9-106">Spowoduje to zapisanie klasy pochodne od konieczności przedefiniować wspólne elementy.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="8c5d9-107">W niektórych przypadkach wspólnej nie jest to kompletny, aby wprowadzić użytecznej obiektu, a każda klasa pochodna definiuje brakującej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="8c5d9-108">W takim przypadku należy kod konsumencki do tworzenia obiektów tylko z klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="8c5d9-109">Możesz użyć `MustInherit` w klasie bazowej do wyegzekwowania tego.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="8c5d9-110">Używanie innego `MustInherit` klasy jest ograniczenie zmienną do zestawu powiązanych klas.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="8c5d9-111">Można zdefiniować klasę bazową i pochodną te klasy pokrewne.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="8c5d9-112">Klasa bazowa trzeba podawać żadnych funkcji, które są wspólne dla wszystkich klas pochodnych, ale może służyć jako filtr do przypisywania wartości do zmiennych.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="8c5d9-113">Jeśli Twój kod konsumencki deklaruje zmienną jako klasa bazowa, Visual Basic umożliwia przypisywanie tylko obiekt z jednej z klas pochodnych do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="8c5d9-114">.NET Framework definiuje kilka `MustInherit` klas między nimi <xref:System.Array>, <xref:System.Enum>, i <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="8c5d9-115"><xref:System.ValueType> jest przykładem klasę bazową, która ogranicza zmienną.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="8c5d9-116">Wszystkie typy wartości wywodzą się z <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="8c5d9-117">Jeśli zadeklarujesz zmienną <xref:System.ValueType>, tylko typy wartości można przypisać do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8c5d9-118">reguły</span><span class="sxs-lookup"><span data-stu-id="8c5d9-118">Rules</span></span>  
  
-   <span data-ttu-id="8c5d9-119">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="8c5d9-119">**Declaration Context.**</span></span> <span data-ttu-id="8c5d9-120">Możesz użyć `MustInherit` tylko w `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="8c5d9-121">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="8c5d9-121">**Combined Modifiers.**</span></span> <span data-ttu-id="8c5d9-122">Nie można określić `MustInherit` wraz z `NotInheritable` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c5d9-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c5d9-123">Example</span></span>  
 <span data-ttu-id="8c5d9-124">Poniższy przykład ilustruje wymuszonego dziedziczenia i zastępowania wymuszone.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="8c5d9-125">Klasa bazowa `shape` definiuje zmienną `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="8c5d9-126">Klasy `circle` i `square` dziedziczyć `shape`.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="8c5d9-127">Dziedziczą definicji `acrossLine`, ale one należy zdefiniować funkcję `area` ponieważ to obliczenie jest inna dla każdego rodzaju kształtu.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="8c5d9-128">Można zadeklarować `shape1` i `shape2` typu `shape`.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="8c5d9-129">Jednak nie można utworzyć obiektu z `shape` ponieważ brakuje funkcjonalność funkcji `area` i jest oznaczony jako `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="8c5d9-130">Ponieważ są one zadeklarowane jako `shape`, zmienne `shape1` i `shape2` są ograniczone do obiektów z klas pochodnych `circle` i `square`.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="8c5d9-131">Visual Basic nie umożliwić przypisanie jakiegokolwiek innego obiektu do tych zmiennych, który zapewnia wysoki poziom bezpieczeństwa typu.</span><span class="sxs-lookup"><span data-stu-id="8c5d9-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="8c5d9-132">Użycie</span><span class="sxs-lookup"><span data-stu-id="8c5d9-132">Usage</span></span>  
 <span data-ttu-id="8c5d9-133">`MustInherit` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="8c5d9-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="8c5d9-134">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c5d9-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c5d9-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c5d9-135">See also</span></span>
- [<span data-ttu-id="8c5d9-136">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c5d9-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="8c5d9-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="8c5d9-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="8c5d9-138">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8c5d9-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="8c5d9-139">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="8c5d9-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
