---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d384986e42ee69a0f425c1590599aa2c82bc856
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="e760d-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e760d-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="e760d-103">Określa, że klasa może być używana tylko jako klasa bazowa i że nie można utworzyć obiektu bezpośrednio z niej.</span><span class="sxs-lookup"><span data-stu-id="e760d-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e760d-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e760d-104">Remarks</span></span>  
 <span data-ttu-id="e760d-105">Celem *klasa podstawowa* (znanej także jako *klasy abstrakcyjnej*) jest określenie funkcje, które są wspólne dla wszystkich klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="e760d-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="e760d-106">Spowoduje to zapisanie klasy pochodnej z konieczności ponownego zdefiniowania wspólne elementy.</span><span class="sxs-lookup"><span data-stu-id="e760d-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="e760d-107">W niektórych przypadkach wspólnej nie jest to pełny, aby używać obiektu, a każda klasa pochodna definiuje brakującej funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="e760d-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="e760d-108">W takim przypadku ma zostać odbierającą do tworzenia obiektów tylko z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="e760d-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="e760d-109">Możesz użyć `MustInherit` w klasie podstawowej tego wymusić.</span><span class="sxs-lookup"><span data-stu-id="e760d-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="e760d-110">Użycie innego `MustInherit` klasy jest ograniczenie zmienną do zestawu powiązanymi klasami.</span><span class="sxs-lookup"><span data-stu-id="e760d-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="e760d-111">Można zdefiniować klasę podstawową i pochodną te klasy pokrewne.</span><span class="sxs-lookup"><span data-stu-id="e760d-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="e760d-112">Klasa podstawowa nie trzeba podać żadnej funkcji, które są wspólne dla wszystkich klas pochodnych, ale może służyć jako filtr dla przypisywanie wartości do zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e760d-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="e760d-113">Jeśli odbierającą kod deklaruje zmienną jako klasę podstawową, Visual Basic umożliwia przypisanie tylko obiekt z jednej z klas pochodnych do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e760d-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="e760d-114">.NET Framework definiuje kilka `MustInherit` klas między nimi <xref:System.Array>, <xref:System.Enum>, i <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="e760d-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="e760d-115"><xref:System.ValueType>jest to przykład klasy podstawowej, która ogranicza zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e760d-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="e760d-116">Wszystkie typy wartości pochodzi od <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="e760d-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="e760d-117">Deklarowanie zmiennej jako <xref:System.ValueType>, tylko typy wartości można przypisać do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e760d-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e760d-118">Reguły</span><span class="sxs-lookup"><span data-stu-id="e760d-118">Rules</span></span>  
  
-   <span data-ttu-id="e760d-119">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="e760d-119">**Declaration Context.**</span></span> <span data-ttu-id="e760d-120">Można użyć `MustInherit` tylko w `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e760d-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="e760d-121">**Łączna modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="e760d-121">**Combined Modifiers.**</span></span> <span data-ttu-id="e760d-122">Nie można określić `MustInherit` razem z `NotInheritable` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e760d-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e760d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="e760d-123">Example</span></span>  
 <span data-ttu-id="e760d-124">W poniższym przykładzie przedstawiono wymuszone dziedziczenia i zastępowanie wymuszone.</span><span class="sxs-lookup"><span data-stu-id="e760d-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="e760d-125">Klasa podstawowa `shape` definiuje zmienną `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="e760d-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="e760d-126">Klasy `circle` i `square` pochodzi od `shape`.</span><span class="sxs-lookup"><span data-stu-id="e760d-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="e760d-127">Dziedziczą definicji `acrossLine`, ale zdefiniować funkcję `area` to obliczenie różni się dla każdego rodzaju kształtu.</span><span class="sxs-lookup"><span data-stu-id="e760d-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 <span data-ttu-id="e760d-128">Można zadeklarować `shape1` i `shape2` typu `shape`.</span><span class="sxs-lookup"><span data-stu-id="e760d-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="e760d-129">Jednak nie można utworzyć obiektu z `shape` ponieważ brakuje w nim funkcje funkcji `area` i jest oznaczony jako `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="e760d-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="e760d-130">Ponieważ zostały zgłoszone jako `shape`, zmienne `shape1` i `shape2` są ograniczone do obiektów z klasy pochodnej `circle` i `square`.</span><span class="sxs-lookup"><span data-stu-id="e760d-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="e760d-131">Visual Basic nie umożliwiają przypisywanie drugi obiekt do tych zmiennych zapewniający wysokiego poziomu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e760d-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e760d-132">Użycie</span><span class="sxs-lookup"><span data-stu-id="e760d-132">Usage</span></span>  
 <span data-ttu-id="e760d-133">`MustInherit` Modyfikatora można używać w tym kontekście:</span><span class="sxs-lookup"><span data-stu-id="e760d-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="e760d-134">Class — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e760d-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e760d-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e760d-135">See Also</span></span>  
 [<span data-ttu-id="e760d-136">Inherits — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e760d-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="e760d-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="e760d-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="e760d-138">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e760d-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="e760d-139">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="e760d-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
