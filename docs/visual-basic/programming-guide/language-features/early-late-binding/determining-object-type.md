---
title: Określanie typu obiektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 5980549dd063b2c7d5c60ebd4e9762284c072009
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586621"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="110e6-102">Określanie typu obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="110e6-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="110e6-103">Obiekt generyczny zmienne (czyli zmienne został zadeklarowany jako `Object`) może zawierać obiekty z dowolnej klasy.</span><span class="sxs-lookup"><span data-stu-id="110e6-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="110e6-104">W przypadku używania zmiennych typu `Object`, konieczne może być różne akcje na podstawie klasy obiektu; na przykład niektóre obiekty mogą nie obsługiwać określoną właściwość lub metoda.</span><span class="sxs-lookup"><span data-stu-id="110e6-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="110e6-105">Visual Basic zapewnia dwa sposoby kontrolowania, jakiego typu obiektu jest przechowywany w zmiennej obiektu: `TypeName` funkcji i `TypeOf...Is` operatora.</span><span class="sxs-lookup"><span data-stu-id="110e6-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="110e6-106">TypeName, jak i TypeOf... Jest</span><span class="sxs-lookup"><span data-stu-id="110e6-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="110e6-107">`TypeName` Funkcja zwraca wartość typu ciąg i sprawdza się najlepiej, gdy należy zapisać lub wyświetlić nazwę klasy obiektu, jak pokazano na następujący fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="110e6-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 <span data-ttu-id="110e6-108">`TypeOf...Is` Operator jest najlepszym wyborem do testowania typu obiektu, ponieważ jest znacznie szybsze niż porównania ciągu równoważnego przy użyciu `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="110e6-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="110e6-109">Poniższy fragment kodu używa `TypeOf...Is` w ramach `If...Then...Else` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="110e6-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 <span data-ttu-id="110e6-110">W tym miejscu jest zaległe word ostrożności.</span><span class="sxs-lookup"><span data-stu-id="110e6-110">A word of caution is due here.</span></span> <span data-ttu-id="110e6-111">`TypeOf...Is` Operator zwraca `True` Jeśli obiekt jest określonego typu lub pochodzi z określonego typu.</span><span class="sxs-lookup"><span data-stu-id="110e6-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="110e6-112">Prawie wszystko, co zrobić za pomocą Visual Basic obejmuje obiekty, które zawierają jakieś elementy, które nie są zazwyczaj uważane za obiekty, takie jak ciągi i liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="110e6-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="110e6-113">Te obiekty są uzyskiwane z i odziedziczenie metody z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="110e6-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="110e6-114">Przy przekazywaniu `Integer` ocenione z `Object`, `TypeOf...Is` operator zwraca `True`.</span><span class="sxs-lookup"><span data-stu-id="110e6-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="110e6-115">Poniższy przykład informuje, że parametr `InParam` jest zarówno `Object` i `Integer`:</span><span class="sxs-lookup"><span data-stu-id="110e6-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 <span data-ttu-id="110e6-116">W poniższym przykładzie użyto obu `TypeOf...Is` i `TypeName` można ustalić typu obiektu, przekazana do niej w `Ctrl` argumentu.</span><span class="sxs-lookup"><span data-stu-id="110e6-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="110e6-117">`TestObject` Wywołania procedur `ShowType` z trzech różnych rodzajów formantów.</span><span class="sxs-lookup"><span data-stu-id="110e6-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="110e6-118">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="110e6-118">To run the example</span></span>  
  
1.  <span data-ttu-id="110e6-119">Utwórz nowy projekt aplikacji Windows i Dodaj <xref:System.Windows.Forms.Button> kontroli <xref:System.Windows.Forms.CheckBox> kontroli i <xref:System.Windows.Forms.RadioButton> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="110e6-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="110e6-120">Przy użyciu przycisku w formularzu, należy wywołać `TestObject` procedury.</span><span class="sxs-lookup"><span data-stu-id="110e6-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="110e6-121">Dodaj następujący kod do formularza:</span><span class="sxs-lookup"><span data-stu-id="110e6-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="110e6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="110e6-122">See also</span></span>
- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="110e6-123">Wywoływanie właściwości lub metody za pomocą nazwy ciągu</span><span class="sxs-lookup"><span data-stu-id="110e6-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="110e6-124">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="110e6-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="110e6-125">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="110e6-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="110e6-126">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="110e6-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="110e6-127">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="110e6-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
