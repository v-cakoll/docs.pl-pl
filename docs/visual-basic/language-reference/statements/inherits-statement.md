---
title: Inherits — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 4a98ada39a04730b46f40fe139e72d1855d9b067
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739506"
---
# <a name="inherits-statement"></a><span data-ttu-id="2165e-102">Inherits — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="2165e-102">Inherits Statement</span></span>
<span data-ttu-id="2165e-103">Powoduje, że bieżącą klasę lub interfejs dziedziczy atrybuty, zmiennych, właściwości, procedur i zdarzeń z innej klasy lub zestawu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2165e-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2165e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2165e-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="2165e-105">Części</span><span class="sxs-lookup"><span data-stu-id="2165e-105">Parts</span></span>  
  
|<span data-ttu-id="2165e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="2165e-106">Term</span></span>|<span data-ttu-id="2165e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="2165e-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="2165e-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="2165e-108">Required.</span></span> <span data-ttu-id="2165e-109">Nazwa klasy, z której pochodzi ta klasa.</span><span class="sxs-lookup"><span data-stu-id="2165e-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="2165e-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="2165e-110">-or-</span></span><br /><br /> <span data-ttu-id="2165e-111">Nazwy interfejsów, z których pochodzi ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="2165e-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="2165e-112">Użyj przecinków do oddzielenia wielu nazw.</span><span class="sxs-lookup"><span data-stu-id="2165e-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2165e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2165e-113">Remarks</span></span>  
 <span data-ttu-id="2165e-114">Jeśli używane, `Inherits` instrukcja musi być pierwszy wiersz nie jest pusty, bez komentarza w definicji klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2165e-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="2165e-115">Należy natychmiast wykonać `Class` lub `Interface` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2165e-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="2165e-116">Możesz użyć `Inherits` tylko w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="2165e-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="2165e-117">Oznacza to, że kontekst deklaracji dla dziedziczenia nie może być plik źródłowy, przestrzeń nazw, struktury, moduł, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="2165e-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2165e-118">reguły</span><span class="sxs-lookup"><span data-stu-id="2165e-118">Rules</span></span>  
  
-   <span data-ttu-id="2165e-119">**Dziedziczenie klas.**</span><span class="sxs-lookup"><span data-stu-id="2165e-119">**Class Inheritance.**</span></span> <span data-ttu-id="2165e-120">Jeśli korzysta z klasy `Inherits` instrukcji, można określić tylko jedną klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="2165e-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="2165e-121">Klasa nie może też dziedziczyć z klasy w niej zagnieżdżonej.</span><span class="sxs-lookup"><span data-stu-id="2165e-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="2165e-122">**Interfejs dziedziczenia.**</span><span class="sxs-lookup"><span data-stu-id="2165e-122">**Interface Inheritance.**</span></span> <span data-ttu-id="2165e-123">Jeśli korzysta z interfejsu `Inherits` instrukcji, można określić jeden lub więcej podstawowych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2165e-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="2165e-124">Dwa interfejsy mogą dziedziczyć, nawet wtedy, gdy każda definiują element członkowski o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2165e-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="2165e-125">Jeśli to zrobisz, więc w kodzie implementującym musi być określona elementu członkowskiego, który implementuje kwantyfikacja nazwy.</span><span class="sxs-lookup"><span data-stu-id="2165e-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="2165e-126">Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjny poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="2165e-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="2165e-127">Na przykład `Public` interfejs nie może dziedziczyć `Friend` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2165e-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="2165e-128">Interfejs nie może dziedziczyć z interfejsu w nim zagnieżdżony.</span><span class="sxs-lookup"><span data-stu-id="2165e-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="2165e-129">Na przykład dziedziczenia klas w programie .NET Framework <xref:System.ArgumentException> klasy, która dziedziczy po elemencie <xref:System.SystemException> klasy.</span><span class="sxs-lookup"><span data-stu-id="2165e-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="2165e-130">Dzięki temu można <xref:System.ArgumentException> wszystkich wstępnie zdefiniowanych właściwości i procedur wymaganych przez wyjątki systemowe, takie jak <xref:System.Exception.Message%2A> właściwości i <xref:System.Exception.ToString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2165e-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="2165e-131">Na przykład dziedziczenia interfejsu w programie .NET Framework <xref:System.Collections.ICollection> interfejs, który dziedziczy z <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2165e-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="2165e-132">Powoduje to, że <xref:System.Collections.ICollection> dziedziczenia definicji enumerator musieli przemierzają kolekcję.</span><span class="sxs-lookup"><span data-stu-id="2165e-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2165e-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="2165e-133">Example</span></span>  
 <span data-ttu-id="2165e-134">W poniższym przykładzie użyto `Inherits` instrukcję, aby pokazać, jak klasę o nazwie `thisClass` może dziedziczyć wszystkie elementy członkowskie klasa bazowa o nazwie `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="2165e-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="2165e-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="2165e-135">Example</span></span>  
 <span data-ttu-id="2165e-136">Poniższy przykład pokazuje dziedziczenie z wielu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2165e-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 <span data-ttu-id="2165e-137">Interfejs o nazwie `thisInterface` zawiera teraz wszystkie definicje w <xref:System.IComparable>, <xref:System.IDisposable>, i <xref:System.IFormattable> interfejsów dziedziczone elementy Członkowskie zapewniają odpowiednio specyficznych dla typu porównanie dwóch obiektów, zwalniając przydzielone zasoby oraz wartość obiektu jako `String`.</span><span class="sxs-lookup"><span data-stu-id="2165e-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="2165e-138">Klasa, która implementuje `thisInterface` musi implementować każdy członek każdy interfejs podstawowy.</span><span class="sxs-lookup"><span data-stu-id="2165e-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2165e-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2165e-139">See Also</span></span>  
 [<span data-ttu-id="2165e-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="2165e-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="2165e-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="2165e-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="2165e-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="2165e-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="2165e-143">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="2165e-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="2165e-144">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2165e-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
