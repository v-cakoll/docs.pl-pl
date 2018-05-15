---
title: Przeciążone właściwości i metody (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: c0aa7c4a13e049045743044a98020a1aab2cf1a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="79146-102">Przeciążone właściwości i metody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79146-102">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="79146-103">Przeciążanie jest tworzenie więcej niż jednej procedury, wystąpienie konstruktora lub właściwości w klasie z tej samej nazwie, ale argument różnych typów.</span><span class="sxs-lookup"><span data-stu-id="79146-103">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>  
  
## <a name="overloading-usage"></a><span data-ttu-id="79146-104">Przeciążanie użycia</span><span class="sxs-lookup"><span data-stu-id="79146-104">Overloading usage</span></span>

 <span data-ttu-id="79146-105">Przeciążanie jest szczególnie przydatna w przypadku, gdy model obiektu mówią, że zostanie zastosowana identycznych nazw dla procedur, które działają na różnych typach danych.</span><span class="sxs-lookup"><span data-stu-id="79146-105">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="79146-106">Na przykład klasa służąca do wyświetlania kilku różnych typów danych może mieć `Display` procedur, które wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="79146-106">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>  
  
 [!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]
  
 <span data-ttu-id="79146-107">Bez przeładowania, będzie potrzebny do tworzenia unikatowych nazw dla każdej procedury, mimo że robią to samo, jak pokazano w następnym:</span><span class="sxs-lookup"><span data-stu-id="79146-107">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>  
  
 [!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]
  
 <span data-ttu-id="79146-108">Przeciążanie ułatwia używać właściwości lub metody, ponieważ umożliwia wybór typów danych, które mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="79146-108">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="79146-109">Na przykład przeciążone `Display` omówionych wcześniej można wywołać metody za pomocą dowolnego z następujących wierszy kodu:</span><span class="sxs-lookup"><span data-stu-id="79146-109">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>  
  
 [!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]
  
 <span data-ttu-id="79146-110">W czasie wykonywania Visual Basic wywołuje procedurę poprawne na podstawie typów danych parametrów, które określisz.</span><span class="sxs-lookup"><span data-stu-id="79146-110">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="79146-111">Przeciążanie reguły</span><span class="sxs-lookup"><span data-stu-id="79146-111">Overloading rules</span></span>

 <span data-ttu-id="79146-112">Przeciążonego elementu członkowskiego klasy można utworzyć przez dodanie dwóch lub więcej właściwości lub metody o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="79146-112">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="79146-113">Z wyjątkiem przeciążone elementy członkowskie pochodnej każdy przeciążonego elementu członkowskiego musi mieć listy różnych parametrów, a następujące elementy nie może pełnić funkcji różnego przeciążania właściwość lub procedura:</span><span class="sxs-lookup"><span data-stu-id="79146-113">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>  
  
-   <span data-ttu-id="79146-114">Modyfikatory, takich jak `ByVal` lub `ByRef`, które są stosowane do elementu członkowskiego lub parametrów elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="79146-114">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>  
  
-   <span data-ttu-id="79146-115">Nazwy parametrów</span><span class="sxs-lookup"><span data-stu-id="79146-115">Names of parameters</span></span>  
  
-   <span data-ttu-id="79146-116">Zwracane typy procedur</span><span class="sxs-lookup"><span data-stu-id="79146-116">Return types of procedures</span></span>  
  
 <span data-ttu-id="79146-117">`Overloads` — Słowo kluczowe jest opcjonalny w przypadku przeciążania, ale jeśli występują przeciążony używa elementu członkowskiego `Overloads` — słowo kluczowe, a następnie wszystkie inne przeciążone elementy członkowskie o tej samej nazwie należy także określić słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="79146-117">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>  
  
 <span data-ttu-id="79146-118">Klasy pochodne mogą przeciążania dziedziczonych członków z elementów członkowskich, które mają identyczne parametry i typy parametrów procesu nazywanego *przesłanianie według nazwy i podpisu*.</span><span class="sxs-lookup"><span data-stu-id="79146-118">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="79146-119">Jeśli `Overloads` — słowo kluczowe jest używana, gdy przesłanianie według nazwy i podpisu, implementacja klasy pochodnej elementu członkowskiego zamiast będzie używany do implementacji w klasie podstawowej, i inne przeciążenia dla tego elementu członkowskiego będą dostępne do wystąpień klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="79146-119">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>  
  
 <span data-ttu-id="79146-120">Jeśli `Overloads` — słowo kluczowe zostanie pominięty przeciążania dziedziczonego elementu członkowskiego z elementem członkowskim, który ma identyczne parametry i typy parametrów, a następnie przeładowanie jest nazywany *przesłanianie według nazwy*.</span><span class="sxs-lookup"><span data-stu-id="79146-120">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="79146-121">Przesłanianie według nazwy zastępuje implementacji dziedziczonego elementu członkowskiego, a także udostępnia inne przeciążenia jest niedostępny dla wystąpień klasy pochodnej i jego decedents.</span><span class="sxs-lookup"><span data-stu-id="79146-121">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>  
  
 <span data-ttu-id="79146-122">`Overloads` i `Shadows` Modyfikatory nie można używać z tej samej właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="79146-122">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="79146-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="79146-123">Example</span></span>

 <span data-ttu-id="79146-124">Poniższy przykład tworzy przeciążonych metod, które akceptują albo `String` lub `Decimal` reprezentację kwota dolara ($) i zwracany ciąg zawierający podatku.</span><span class="sxs-lookup"><span data-stu-id="79146-124">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>  
  
#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="79146-125">Aby użyć w tym przykładzie do utworzenia przeciążonej metody</span><span class="sxs-lookup"><span data-stu-id="79146-125">To use this example to create an overloaded method</span></span>
  
1.  <span data-ttu-id="79146-126">Otwórz nowy projekt i Dodaj klasę o nazwie `TaxClass`.</span><span class="sxs-lookup"><span data-stu-id="79146-126">Open a new project and add a class named `TaxClass`.</span></span>  
  
2.  <span data-ttu-id="79146-127">Dodaj następujący kod do `TaxClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="79146-127">Add the following code to the `TaxClass` class.</span></span>  
  
     [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]
  
3.  <span data-ttu-id="79146-128">Poniższej procedury można dodać do formularza.</span><span class="sxs-lookup"><span data-stu-id="79146-128">Add the following procedure to your form.</span></span>  
  
     [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]
  
4.  <span data-ttu-id="79146-129">Dodawanie przycisku do formularza i wywołanie `ShowTax` procedury z `Button1_Click` zdarzeń przycisku.</span><span class="sxs-lookup"><span data-stu-id="79146-129">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>  
  
5.  <span data-ttu-id="79146-130">Uruchom projekt i kliknij przycisk w formularzu do testowania przeciążone `ShowTax` procedury.</span><span class="sxs-lookup"><span data-stu-id="79146-130">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>  
  
 <span data-ttu-id="79146-131">W czasie wykonywania kompilator wybiera odpowiednią przeciążonej funkcji zgodny z parametrami używane.</span><span class="sxs-lookup"><span data-stu-id="79146-131">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="79146-132">Po kliknięciu przycisku przeciążona metoda jest wywoływana najpierw z `Price` parametr, który jest ciągiem i komunikat "cena jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="79146-132">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="79146-133">Podatek jest $5,12" jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="79146-133">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="79146-134">`TaxAmount` jest wywoływana z `Decimal` wartość po raz drugi i komunikat, "cena jest wartości dziesiętnej.</span><span class="sxs-lookup"><span data-stu-id="79146-134">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="79146-135">Podatek jest $5,12" jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="79146-135">Tax is $5.12" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79146-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79146-136">See also</span></span>

 [<span data-ttu-id="79146-137">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="79146-137">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="79146-138">Przesłanianie w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79146-138">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [<span data-ttu-id="79146-139">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="79146-139">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="79146-140">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="79146-140">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="79146-141">Shadows</span><span class="sxs-lookup"><span data-stu-id="79146-141">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="79146-142">ByVal</span><span class="sxs-lookup"><span data-stu-id="79146-142">ByVal</span></span>](../../../../visual-basic/language-reference/modifiers/byval.md)  
 [<span data-ttu-id="79146-143">ByRef</span><span class="sxs-lookup"><span data-stu-id="79146-143">ByRef</span></span>](../../../../visual-basic/language-reference/modifiers/byref.md)  
 [<span data-ttu-id="79146-144">Overloads</span><span class="sxs-lookup"><span data-stu-id="79146-144">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="79146-145">Shadows</span><span class="sxs-lookup"><span data-stu-id="79146-145">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
