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
ms.openlocfilehash: e92e12908c89bb7a0bf385a2122b0c8f1eb8a6f7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581755"
---
# <a name="inherits-statement"></a><span data-ttu-id="29d6d-102">Inherits — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="29d6d-102">Inherits Statement</span></span>
<span data-ttu-id="29d6d-103">Powoduje, że bieżąca Klasa lub interfejs dziedziczy atrybuty, zmienne, właściwości, procedury i zdarzenia z innej klasy lub zestawu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="29d6d-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29d6d-104">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="29d6d-105">Części</span><span class="sxs-lookup"><span data-stu-id="29d6d-105">Parts</span></span>  
  
|<span data-ttu-id="29d6d-106">Termin</span><span class="sxs-lookup"><span data-stu-id="29d6d-106">Term</span></span>|<span data-ttu-id="29d6d-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="29d6d-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="29d6d-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="29d6d-108">Required.</span></span> <span data-ttu-id="29d6d-109">Nazwa klasy, z której pochodzi ta klasa.</span><span class="sxs-lookup"><span data-stu-id="29d6d-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="29d6d-110">—lub—</span><span class="sxs-lookup"><span data-stu-id="29d6d-110">-or-</span></span><br /><br /> <span data-ttu-id="29d6d-111">Nazwy interfejsów, z których pochodzi ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="29d6d-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="29d6d-112">Użyj przecinków, aby rozdzielić wiele nazw.</span><span class="sxs-lookup"><span data-stu-id="29d6d-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29d6d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29d6d-113">Remarks</span></span>  
 <span data-ttu-id="29d6d-114">Jeśli jest używana, instrukcja `Inherits` musi być pierwszym niepustym wierszem bez komentarza w definicji klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="29d6d-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="29d6d-115">Należy od razu przestrzegać instrukcji `Class` lub `Interface`.</span><span class="sxs-lookup"><span data-stu-id="29d6d-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="29d6d-116">@No__t_0 można użyć tylko w klasie lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="29d6d-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="29d6d-117">Oznacza to, że kontekst deklaracji dziedziczenia nie może być plikiem źródłowym, przestrzenią nazw, strukturą, modułem, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="29d6d-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="29d6d-118">Przepisy</span><span class="sxs-lookup"><span data-stu-id="29d6d-118">Rules</span></span>  
  
- <span data-ttu-id="29d6d-119">**Dziedziczenie klas.**</span><span class="sxs-lookup"><span data-stu-id="29d6d-119">**Class Inheritance.**</span></span> <span data-ttu-id="29d6d-120">Jeśli Klasa używa instrukcji `Inherits`, można określić tylko jedną klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="29d6d-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="29d6d-121">Klasa nie może dziedziczyć z klasy zagnieżdżonej w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="29d6d-121">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="29d6d-122">**Dziedziczenie interfejsu.**</span><span class="sxs-lookup"><span data-stu-id="29d6d-122">**Interface Inheritance.**</span></span> <span data-ttu-id="29d6d-123">Jeśli interfejs używa instrukcji `Inherits`, można określić jeden lub więcej interfejsów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="29d6d-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="29d6d-124">Można dziedziczyć z dwóch interfejsów, nawet jeśli każda z nich definiuje element członkowski o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="29d6d-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="29d6d-125">W takim przypadku kod implementujący musi używać kwalifikacji nazw, aby określić, który element członkowski jest wdrażany.</span><span class="sxs-lookup"><span data-stu-id="29d6d-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="29d6d-126">Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjnym poziomem dostępu.</span><span class="sxs-lookup"><span data-stu-id="29d6d-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="29d6d-127">Na przykład interfejs `Public` nie może dziedziczyć po interfejsie `Friend`.</span><span class="sxs-lookup"><span data-stu-id="29d6d-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="29d6d-128">Interfejs nie może dziedziczyć z interfejsu zagnieżdżonego w nim.</span><span class="sxs-lookup"><span data-stu-id="29d6d-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="29d6d-129">Przykładem dziedziczenia klasy w .NET Framework jest Klasa <xref:System.ArgumentException>, która dziedziczy z klasy <xref:System.SystemException>.</span><span class="sxs-lookup"><span data-stu-id="29d6d-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="29d6d-130">Dzięki temu <xref:System.ArgumentException> wszystkie wstępnie zdefiniowane właściwości i procedury wymagane przez wyjątki systemowe, takie jak Właściwość <xref:System.Exception.Message%2A> i Metoda <xref:System.Exception.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="29d6d-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="29d6d-131">Przykładem dziedziczenia interfejsów w .NET Framework jest interfejs <xref:System.Collections.ICollection>, który dziedziczy po interfejsie <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="29d6d-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="29d6d-132">Powoduje to, że <xref:System.Collections.ICollection> dziedziczyć definicję modułu wyliczającego wymaganego do przechodzenia do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="29d6d-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29d6d-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="29d6d-133">Example</span></span>  
 <span data-ttu-id="29d6d-134">Poniższy przykład używa instrukcji `Inherits`, aby pokazać, jak Klasa o nazwie `thisClass` może odziedziczyć wszystkie elementy członkowskie klasy bazowej o nazwie `anotherClass`.</span><span class="sxs-lookup"><span data-stu-id="29d6d-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="29d6d-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="29d6d-135">Example</span></span>  
 <span data-ttu-id="29d6d-136">Poniższy przykład pokazuje dziedziczenie wielu interfejsów.</span><span class="sxs-lookup"><span data-stu-id="29d6d-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="29d6d-137">Interfejs o nazwie `thisInterface` teraz zawiera wszystkie definicje w <xref:System.IComparable>, <xref:System.IDisposable> i <xref:System.IFormattable> interfejsy dziedziczone elementy członkowskie odpowiednio dla porównywania określonego typu dla dwóch obiektów, zwalniania przyznanych zasobów i wyrażania wartości obiekt jako `String`.</span><span class="sxs-lookup"><span data-stu-id="29d6d-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="29d6d-138">Klasa implementująca `thisInterface` musi implementować każdy element członkowski każdego z interfejsów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="29d6d-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d6d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29d6d-139">See also</span></span>

- [<span data-ttu-id="29d6d-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="29d6d-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="29d6d-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="29d6d-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="29d6d-142">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="29d6d-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="29d6d-143">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="29d6d-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="29d6d-144">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="29d6d-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
