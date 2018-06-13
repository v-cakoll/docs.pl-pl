---
title: Inherits — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 43a8aa4e9e04ee035cb52e9f829de13e5c022217
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604344"
---
# <a name="inherits-statement"></a><span data-ttu-id="9bd46-102">Inherits — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="9bd46-102">Inherits Statement</span></span>
<span data-ttu-id="9bd46-103">Powoduje, że klasy lub interfejsu dziedziczenie atrybutów, zmiennych, właściwości, procedur i zdarzeń z innej klasy lub zestawu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9bd46-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bd46-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="9bd46-105">Części</span><span class="sxs-lookup"><span data-stu-id="9bd46-105">Parts</span></span>  
  
|<span data-ttu-id="9bd46-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9bd46-106">Term</span></span>|<span data-ttu-id="9bd46-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9bd46-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="9bd46-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9bd46-108">Required.</span></span> <span data-ttu-id="9bd46-109">Nazwa klasy, z której pochodzi ta klasa.</span><span class="sxs-lookup"><span data-stu-id="9bd46-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="9bd46-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="9bd46-110">-or-</span></span><br /><br /> <span data-ttu-id="9bd46-111">Nazwy interfejsów, spośród których pochodzi ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="9bd46-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="9bd46-112">Użyj przecinków do oddzielania wielu nazw.</span><span class="sxs-lookup"><span data-stu-id="9bd46-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd46-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bd46-113">Remarks</span></span>  
 <span data-ttu-id="9bd46-114">Jeśli używana, `Inherits` instrukcji musi być pierwszym wierszem niepustą, komentarza-w definicji klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9bd46-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="9bd46-115">Należy natychmiast wykonać `Class` lub `Interface` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9bd46-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="9bd46-116">Można użyć `Inherits` tylko w klasie lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="9bd46-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="9bd46-117">Oznacza to, że w kontekście deklaracja dziedziczenia nie może być plik źródłowy, przestrzeni nazw, struktury, modułu, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="9bd46-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9bd46-118">Reguły</span><span class="sxs-lookup"><span data-stu-id="9bd46-118">Rules</span></span>  
  
-   <span data-ttu-id="9bd46-119">**Dziedziczenie klas.**</span><span class="sxs-lookup"><span data-stu-id="9bd46-119">**Class Inheritance.**</span></span> <span data-ttu-id="9bd46-120">Jeśli używa klasy `Inherits` instrukcji, można określić tylko jedną klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="9bd46-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="9bd46-121">Klasa nie dziedziczy z klasy w nim zagnieżdżony.</span><span class="sxs-lookup"><span data-stu-id="9bd46-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="9bd46-122">**Interfejs dziedziczenia.**</span><span class="sxs-lookup"><span data-stu-id="9bd46-122">**Interface Inheritance.**</span></span> <span data-ttu-id="9bd46-123">Jeśli używa interfejsu `Inherits` instrukcji, można określić co najmniej jeden interfejsach podstawowych.</span><span class="sxs-lookup"><span data-stu-id="9bd46-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="9bd46-124">Może dziedziczyć z dwóch interfejsów, nawet jeśli ich zdefiniować element członkowski o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9bd46-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="9bd46-125">Jeśli to zrobisz, więc implementującej kodu musi umożliwia określenie, który element członkowski implementuje kwantyfikacja nazwy.</span><span class="sxs-lookup"><span data-stu-id="9bd46-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="9bd46-126">Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjne poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="9bd46-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="9bd46-127">Na przykład `Public` interfejsu nie może dziedziczyć z `Friend` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9bd46-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="9bd46-128">Interfejs nie może dziedziczyć z interfejsu w nim zagnieżdżony.</span><span class="sxs-lookup"><span data-stu-id="9bd46-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="9bd46-129">Na przykład dziedziczenia klas w programie .NET Framework <xref:System.ArgumentException> klasy, która dziedziczy <xref:System.SystemException> klasy.</span><span class="sxs-lookup"><span data-stu-id="9bd46-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="9bd46-130">Zapewnia to do <xref:System.ArgumentException> wszystkich wstępnie zdefiniowanych właściwości i procedur wymaganych przez wyjątki systemu, takich jak <xref:System.Exception.Message%2A> właściwości i <xref:System.Exception.ToString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9bd46-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="9bd46-131">Na przykład z dziedziczenia interfejsu w programie .NET Framework <xref:System.Collections.ICollection> interfejs, który dziedziczy <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9bd46-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="9bd46-132">Powoduje to <xref:System.Collections.ICollection> dziedziczenia definicji modułu wyliczającego wymagane do przechodzenia kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9bd46-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd46-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bd46-133">Example</span></span>  
 <span data-ttu-id="9bd46-134">W poniższym przykładzie użyto `Inherits` instrukcji, aby pokazać, jak klasa o nazwie `thisClass` może dziedziczyć wszystkich elementów członkowskich klasy podstawowej o nazwie `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="9bd46-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9bd46-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bd46-135">Example</span></span>  
 <span data-ttu-id="9bd46-136">W poniższym przykładzie przedstawiono dziedziczenia wiele interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9bd46-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 <span data-ttu-id="9bd46-137">Interfejs o nazwie `thisInterface` teraz obejmuje wszystkie definicje w <xref:System.IComparable>, <xref:System.IDisposable>, i <xref:System.IFormattable> dziedziczone elementy Członkowskie przekaże odpowiednio do określonego typu porównania dwóch obiektów wydanie interfejsy przydzielone zasoby oraz wartości obiektu jako `String`.</span><span class="sxs-lookup"><span data-stu-id="9bd46-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="9bd46-138">Klasa, która implementuje `thisInterface` musi implementować każdy element członkowski każdy interfejs podstawowy.</span><span class="sxs-lookup"><span data-stu-id="9bd46-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd46-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bd46-139">See Also</span></span>  
 [<span data-ttu-id="9bd46-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="9bd46-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="9bd46-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="9bd46-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="9bd46-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="9bd46-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="9bd46-143">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="9bd46-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="9bd46-144">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9bd46-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
