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
ms.openlocfilehash: 5d88a01f90bc91a88229d19aa2368f8c71075b2f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404502"
---
# <a name="inherits-statement"></a><span data-ttu-id="d1546-102">Inherits — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="d1546-102">Inherits Statement</span></span>
<span data-ttu-id="d1546-103">Powoduje, że bieżąca Klasa lub interfejs dziedziczy atrybuty, zmienne, właściwości, procedury i zdarzenia z innej klasy lub zestawu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d1546-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1546-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1546-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="d1546-105">Części</span><span class="sxs-lookup"><span data-stu-id="d1546-105">Parts</span></span>  
  
|<span data-ttu-id="d1546-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d1546-106">Term</span></span>|<span data-ttu-id="d1546-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d1546-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="d1546-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="d1546-108">Required.</span></span> <span data-ttu-id="d1546-109">Nazwa klasy, z której pochodzi ta klasa.</span><span class="sxs-lookup"><span data-stu-id="d1546-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="d1546-110">-lub-</span><span class="sxs-lookup"><span data-stu-id="d1546-110">-or-</span></span><br /><br /> <span data-ttu-id="d1546-111">Nazwy interfejsów, z których pochodzi ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="d1546-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="d1546-112">Użyj przecinków, aby rozdzielić wiele nazw.</span><span class="sxs-lookup"><span data-stu-id="d1546-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1546-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1546-113">Remarks</span></span>  
 <span data-ttu-id="d1546-114">Jeśli jest używana, `Inherits` instrukcja musi być pierwszym niepustym wierszem bez komentarza w definicji klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d1546-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="d1546-115">Należy od razu przestrzegać `Class` instrukcji or `Interface` .</span><span class="sxs-lookup"><span data-stu-id="d1546-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="d1546-116">Można używać `Inherits` tylko w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="d1546-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="d1546-117">Oznacza to, że kontekst deklaracji dziedziczenia nie może być plikiem źródłowym, przestrzenią nazw, strukturą, modułem, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="d1546-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d1546-118">Reguły</span><span class="sxs-lookup"><span data-stu-id="d1546-118">Rules</span></span>  
  
- <span data-ttu-id="d1546-119">**Dziedziczenie klas.**</span><span class="sxs-lookup"><span data-stu-id="d1546-119">**Class Inheritance.**</span></span> <span data-ttu-id="d1546-120">Jeśli Klasa używa `Inherits` instrukcji, można określić tylko jedną klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="d1546-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="d1546-121">Klasa nie może dziedziczyć z klasy zagnieżdżonej w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="d1546-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="d1546-122">**Dziedziczenie interfejsu.**</span><span class="sxs-lookup"><span data-stu-id="d1546-122">**Interface Inheritance.**</span></span> <span data-ttu-id="d1546-123">Jeśli interfejs używa `Inherits` instrukcji, można określić jeden lub więcej interfejsów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="d1546-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="d1546-124">Można dziedziczyć z dwóch interfejsów, nawet jeśli każda z nich definiuje element członkowski o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d1546-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="d1546-125">W takim przypadku kod implementujący musi używać kwalifikacji nazw, aby określić, który element członkowski jest wdrażany.</span><span class="sxs-lookup"><span data-stu-id="d1546-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="d1546-126">Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjnym poziomem dostępu.</span><span class="sxs-lookup"><span data-stu-id="d1546-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="d1546-127">Na przykład `Public` interfejs nie może dziedziczyć z `Friend` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d1546-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="d1546-128">Interfejs nie może dziedziczyć z interfejsu zagnieżdżonego w nim.</span><span class="sxs-lookup"><span data-stu-id="d1546-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="d1546-129">Przykładem dziedziczenia klasy w .NET Framework jest <xref:System.ArgumentException> Klasa, która dziedziczy z <xref:System.SystemException> klasy.</span><span class="sxs-lookup"><span data-stu-id="d1546-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="d1546-130">Zapewnia to <xref:System.ArgumentException> wszystkie wstępnie zdefiniowane właściwości i procedury wymagane przez wyjątki systemowe, takie jak <xref:System.Exception.Message%2A> Właściwość i <xref:System.Exception.ToString%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="d1546-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="d1546-131">Przykładem dziedziczenia interfejsów w .NET Framework jest <xref:System.Collections.ICollection> interfejs, który dziedziczy z <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d1546-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="d1546-132">Powoduje to <xref:System.Collections.ICollection> dziedziczenie definicji modułu wyliczającego wymaganego do przechodzenia do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d1546-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1546-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1546-133">Example</span></span>  
 <span data-ttu-id="d1546-134">Poniższy przykład używa instrukcji, `Inherits` Aby pokazać, jak Klasa o nazwie `thisClass` może dziedziczyć wszystkich elementów członkowskich klasy bazowej o nazwie `anotherClass` .</span><span class="sxs-lookup"><span data-stu-id="d1546-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="d1546-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1546-135">Example</span></span>  
 <span data-ttu-id="d1546-136">Poniższy przykład pokazuje dziedziczenie wielu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d1546-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="d1546-137">Interfejs o nazwie `thisInterface` teraz zawiera wszystkie definicje w <xref:System.IComparable> , <xref:System.IDisposable> i <xref:System.IFormattable> interfejsy dziedziczonych elementów członkowskich odpowiednio dla porównywania typów dwóch obiektów, zwalniania przyznanych zasobów i wyrażania wartości obiektu jako `String` .</span><span class="sxs-lookup"><span data-stu-id="d1546-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="d1546-138">Klasa implementująca `thisInterface` musi implementować każdy element członkowski każdego interfejsu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="d1546-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1546-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1546-139">See also</span></span>

- [<span data-ttu-id="d1546-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="d1546-140">MustInherit</span></span>](../modifiers/mustinherit.md)
- [<span data-ttu-id="d1546-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="d1546-141">NotInheritable</span></span>](../modifiers/notinheritable.md)
- [<span data-ttu-id="d1546-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="d1546-142">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="d1546-143">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="d1546-143">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="d1546-144">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1546-144">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
