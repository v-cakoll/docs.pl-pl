---
title: Przeciążone właściwości i metody
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346086"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="a5c3e-102">Przeciążone właściwości i metody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5c3e-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="a5c3e-103">Przeciążenie jest tworzeniem więcej niż jednej procedury, konstruktora wystąpienia lub właściwości w klasie o tej samej nazwie, ale różnych typach argumentów.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="a5c3e-104">Przeciążenie użycia</span><span class="sxs-lookup"><span data-stu-id="a5c3e-104">Overloading usage</span></span>

<span data-ttu-id="a5c3e-105">Przeciążenie jest szczególnie przydatne, gdy model obiektów wskazuje, że są stosowane identyczne nazwy dla procedur, które działają na różnych typach danych.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="a5c3e-106">Na przykład Klasa, która może wyświetlać kilka różnych typów danych, może mieć `Display` procedury, które wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="a5c3e-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="a5c3e-107">Bez przeciążania należy utworzyć odrębne nazwy dla każdej procedury, nawet jeśli są one takie same, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="a5c3e-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="a5c3e-108">Przeciążanie ułatwia korzystanie z właściwości lub metod, ponieważ umożliwia wybór typów danych, które mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="a5c3e-109">Na przykład przeciążona metoda `Display` opisana wcześniej może być wywoływana z dowolnym z następujących wierszy kodu:</span><span class="sxs-lookup"><span data-stu-id="a5c3e-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="a5c3e-110">W czasie wykonywania Visual Basic wywołuje poprawną procedurę na podstawie typów danych parametrów, które określisz.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="a5c3e-111">Reguły przeciążania</span><span class="sxs-lookup"><span data-stu-id="a5c3e-111">Overloading rules</span></span>

 <span data-ttu-id="a5c3e-112">Tworzysz przeciążoną składową klasy przez dodanie dwóch lub więcej właściwości lub metod o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="a5c3e-113">Z wyjątkiem przeciążonych członków pochodnych każdy przeciążony element członkowski musi mieć różne listy parametrów, a następujące elementy nie mogą być używane jako funkcja odróżniająca podczas przeciążania właściwości lub procedury:</span><span class="sxs-lookup"><span data-stu-id="a5c3e-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="a5c3e-114">Modyfikatory, takie jak `ByVal` lub `ByRef`, które mają zastosowanie do elementu członkowskiego lub parametrów elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="a5c3e-115">Nazwy parametrów</span><span class="sxs-lookup"><span data-stu-id="a5c3e-115">Names of parameters</span></span>

- <span data-ttu-id="a5c3e-116">Zwracane typy procedur</span><span class="sxs-lookup"><span data-stu-id="a5c3e-116">Return types of procedures</span></span>

<span data-ttu-id="a5c3e-117">Słowo kluczowe `Overloads` jest opcjonalne podczas przeciążania, ale jeśli jakikolwiek przeciążony element członkowski używa słowa kluczowego `Overloads`, wówczas wszystkie inne przeciążone elementy członkowskie o tej samej nazwie muszą również określać to słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="a5c3e-118">Klasy pochodne mogą przeciążać dziedziczone elementy członkowskie z elementami członkowskimi, które mają identyczne parametry i typy parametrów, proces znany jako *przesłanianie przez nazwę i podpis*.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="a5c3e-119">Jeśli `Overloads` słowo kluczowe jest używane podczas przesłaniania według nazwy i podpisu, implementacja klasy pochodnej elementu członkowskiego zostanie użyta zamiast implementacji w klasie bazowej, a wszystkie pozostałe przeciążenia dla tego elementu członkowskiego będą dostępne dla wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="a5c3e-120">Jeśli słowo kluczowe `Overloads` zostanie pominięte podczas przeciążenia dziedziczonego elementu członkowskiego, który ma identyczne parametry i typy parametrów, Przeciążenie jest nazywane *przesłanianiem o nazwie*.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="a5c3e-121">Przesłanianie według nazwy zastępuje dziedziczone implementacje elementu członkowskiego i powoduje, że wszystkie pozostałe przeciążenia są niedostępne dla wystąpień klasy pochodnej i jej decedents.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="a5c3e-122">Modyfikatory `Overloads` i `Shadows` nie mogą być używane z tą samą właściwością lub metodą.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="a5c3e-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5c3e-123">Example</span></span>

<span data-ttu-id="a5c3e-124">Poniższy przykład tworzy przeciążone metody, które akceptują `String` lub `Decimal` reprezentację kwoty dolara i zwracają ciąg zawierający podatek sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="a5c3e-125">Aby użyć tego przykładu do utworzenia przeciążonej metody</span><span class="sxs-lookup"><span data-stu-id="a5c3e-125">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="a5c3e-126">Otwórz nowy projekt i Dodaj klasę o nazwie `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-126">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="a5c3e-127">Dodaj następujący kod do klasy `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-127">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="a5c3e-128">Dodaj następującą procedurę do formularza.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-128">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="a5c3e-129">Dodaj przycisk do formularza i Wywołaj procedurę `ShowTax` ze zdarzenia `Button1_Click` przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="a5c3e-130">Uruchom projekt i kliknij przycisk w formularzu, aby przetestować przeciążoną procedurę `ShowTax`.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="a5c3e-131">W czasie wykonywania kompilator wybiera odpowiednią przeciążoną funkcję zgodną z używanymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="a5c3e-132">Po kliknięciu przycisku przeciążona metoda jest wywoływana jako pierwsza z parametrem `Price`, który jest ciągiem i komunikatem "Price jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="a5c3e-133">Zostanie wyświetlony podatek $5,12.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="a5c3e-134">`TaxAmount` jest wywoływana z wartością `Decimal` po raz drugi i komunikatem "cena jest liczbą dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="a5c3e-135">Zostanie wyświetlony podatek $5,12.</span><span class="sxs-lookup"><span data-stu-id="a5c3e-135">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5c3e-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5c3e-136">See also</span></span>

- [<span data-ttu-id="a5c3e-137">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="a5c3e-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="a5c3e-138">Obserwowanie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5c3e-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="a5c3e-139">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a5c3e-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a5c3e-140">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="a5c3e-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="a5c3e-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="a5c3e-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="a5c3e-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="a5c3e-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)
- [<span data-ttu-id="a5c3e-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="a5c3e-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)
- [<span data-ttu-id="a5c3e-144">Overloads</span><span class="sxs-lookup"><span data-stu-id="a5c3e-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="a5c3e-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="a5c3e-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
