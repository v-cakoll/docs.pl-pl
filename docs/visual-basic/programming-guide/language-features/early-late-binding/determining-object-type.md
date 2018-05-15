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
ms.openlocfilehash: a9852998abeae67b2a0e9dc3ffc85318ce5045da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="583be-102">Określanie typu obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="583be-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="583be-103">Obiekt generyczny zmienne (czyli zmienne można zadeklarować jako `Object`) może przechowywać obiektów z dowolnej klasy.</span><span class="sxs-lookup"><span data-stu-id="583be-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="583be-104">Używając zmiennych typu `Object`, należy wykonać różne operacje, oparty na klasie obiektu; na przykład niektórych obiektów może nie obsługuje określonej właściwości lub metody.</span><span class="sxs-lookup"><span data-stu-id="583be-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="583be-105">Visual Basic udostępnia dwa sposoby kontrolowania, jakiego typu obiektu są przechowywane w zmiennej obiektu: `TypeName` funkcji i `TypeOf...Is` operatora.</span><span class="sxs-lookup"><span data-stu-id="583be-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="583be-106">Właściwość TypeName i TypeOf... Jest</span><span class="sxs-lookup"><span data-stu-id="583be-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="583be-107">`TypeName` Funkcja zwróci ciąg i jest najlepszym rozwiązaniem, gdy potrzebne do przechowywania lub wyświetlana nazwa klasy obiektu, jak pokazano w poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="583be-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 <span data-ttu-id="583be-108">`TypeOf...Is` Operator jest najlepszym wyborem do testowania typu obiektu, ponieważ jest znacznie szybsza niż porównanie ciągu równoważne przy użyciu `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="583be-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="583be-109">Poniższy fragment kodu używa `TypeOf...Is` w `If...Then...Else` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="583be-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 <span data-ttu-id="583be-110">Wyraz ostrożność jest termin tutaj.</span><span class="sxs-lookup"><span data-stu-id="583be-110">A word of caution is due here.</span></span> <span data-ttu-id="583be-111">`TypeOf...Is` Operator zwraca `True` Jeśli obiekt jest określonego typu lub pochodzi z konkretnego typu.</span><span class="sxs-lookup"><span data-stu-id="583be-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="583be-112">Prawie wszystkie czynności wykonywane za pomocą Visual Basic obejmuje obiekty, do których należą niektóre elementy nie mogą traktować jako obiekty, takie jak parametry i liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="583be-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="583be-113">Te obiekty pochodne i dziedziczy metody <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="583be-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="583be-114">Po upływie `Integer` ocenione z `Object`, `TypeOf...Is` operator zwraca `True`.</span><span class="sxs-lookup"><span data-stu-id="583be-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="583be-115">Poniższy przykład zgłasza, że parametr `InParam` jest zarówno `Object` i `Integer`:</span><span class="sxs-lookup"><span data-stu-id="583be-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 <span data-ttu-id="583be-116">W poniższym przykładzie użyto zarówno `TypeOf...Is` i `TypeName` można określić typu obiektu przekazana do niej w `Ctrl` argumentu.</span><span class="sxs-lookup"><span data-stu-id="583be-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="583be-117">`TestObject` Wywołań procedur `ShowType` z trzech różnych rodzajów formantów.</span><span class="sxs-lookup"><span data-stu-id="583be-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="583be-118">Aby uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="583be-118">To run the example</span></span>  
  
1.  <span data-ttu-id="583be-119">Utwórz nowy projekt aplikacji systemu Windows i Dodaj <xref:System.Windows.Forms.Button> kontroli, <xref:System.Windows.Forms.CheckBox> kontroli, a <xref:System.Windows.Forms.RadioButton> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="583be-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="583be-120">Po kliknięciu przycisku w formularzu wywołać `TestObject` procedury.</span><span class="sxs-lookup"><span data-stu-id="583be-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="583be-121">Dodaj następujący kod do formularza:</span><span class="sxs-lookup"><span data-stu-id="583be-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="583be-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="583be-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [<span data-ttu-id="583be-123">Wywoływanie właściwości lub metody za pomocą nazwy ciągu</span><span class="sxs-lookup"><span data-stu-id="583be-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [<span data-ttu-id="583be-124">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="583be-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="583be-125">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="583be-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="583be-126">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="583be-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="583be-127">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="583be-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
