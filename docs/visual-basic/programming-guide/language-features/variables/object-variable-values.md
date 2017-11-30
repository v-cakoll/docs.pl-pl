---
title: "Wartości zmiennej obiektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccab22920923500a2332db2372e52813c890e5e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="a2caf-102">Wartości zmiennej obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2caf-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="a2caf-103">Zmienna [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) mogą odwoływać się do danych dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="a2caf-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="a2caf-104">Wartości są przechowywane w `Object` zmiennej jest przechowywany w innym miejscu w pamięci, gdy samej zmiennej zawiera wskaźnik do danych.</span><span class="sxs-lookup"><span data-stu-id="a2caf-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="a2caf-105">Funkcje klasyfikatora obiektu</span><span class="sxs-lookup"><span data-stu-id="a2caf-105">Object Classifier Functions</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a2caf-106">udostępnia funkcje, które zwracają informacje o tym, co `Object` zmienna odwołuje się do, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a2caf-106"> supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a2caf-107">Funkcja</span><span class="sxs-lookup"><span data-stu-id="a2caf-107">Function</span></span>|<span data-ttu-id="a2caf-108">Zwraca wartość PRAWDA, jeśli odnosi się zmienna obiektu</span><span class="sxs-lookup"><span data-stu-id="a2caf-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="a2caf-109">Tablica wartości, a nie pojedynczą wartość</span><span class="sxs-lookup"><span data-stu-id="a2caf-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="a2caf-110">A [Date — typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md) wartość lub ciąg, który może zostać zinterpretowany jako wartość daty i godziny</span><span class="sxs-lookup"><span data-stu-id="a2caf-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="a2caf-111">Obiekt typu <xref:System.DBNull>, reprezentuje brakujące lub nieistniejącą dane</span><span class="sxs-lookup"><span data-stu-id="a2caf-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="a2caf-112">Obiekt wyjątku, który jest pochodną<xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="a2caf-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="a2caf-113">[Nic](../../../../visual-basic/language-reference/nothing.md), oznacza to, obiekt nie jest aktualnie przypisany do zmiennej</span><span class="sxs-lookup"><span data-stu-id="a2caf-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="a2caf-114">Liczba lub ciąg, który może zostać zinterpretowany jako liczba</span><span class="sxs-lookup"><span data-stu-id="a2caf-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="a2caf-115">Typ odwołania (na przykład ciąg, tablicy, delegata lub typ klasy)</span><span class="sxs-lookup"><span data-stu-id="a2caf-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="a2caf-116">Funkcje te można użyć w celu uniknięcia przesyłania nieprawidłową wartość do operacji lub procedury.</span><span class="sxs-lookup"><span data-stu-id="a2caf-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="a2caf-117">TypeOf — Operator</span><span class="sxs-lookup"><span data-stu-id="a2caf-117">TypeOf Operator</span></span>  
 <span data-ttu-id="a2caf-118">Można również użyć [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) ustalenie, czy obecnie odnosi się zmienna obiektu określonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="a2caf-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="a2caf-119">`TypeOf`... `Is` wyrażenie ma `True` typu run-time operandu jest pochodną lub implementuje określonego typu.</span><span class="sxs-lookup"><span data-stu-id="a2caf-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="a2caf-120">W poniższym przykładzie użyto `TypeOf` na zmienne obiektów odwołujących się do typów wartości i odwołania.</span><span class="sxs-lookup"><span data-stu-id="a2caf-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="a2caf-121">Powyższy przykład zapisuje następujące wiersze do **debugowania** okno:</span><span class="sxs-lookup"><span data-stu-id="a2caf-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="a2caf-122">Zmienna obiektu `num` odnosi się do danych typu `Integer`, i `frm` odwołuje się do obiektu klasy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="a2caf-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="a2caf-123">Tablice obiektów</span><span class="sxs-lookup"><span data-stu-id="a2caf-123">Object Arrays</span></span>  
 <span data-ttu-id="a2caf-124">Można zadeklarować i użyj tablicy `Object` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="a2caf-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="a2caf-125">Jest to przydatne, gdy potrzebne do obsługi różnych typów danych i klas obiektów.</span><span class="sxs-lookup"><span data-stu-id="a2caf-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="a2caf-126">Wszystkie elementy w tablicy muszą mieć ten sam zadeklarowany typ danych.</span><span class="sxs-lookup"><span data-stu-id="a2caf-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="a2caf-127">Deklarowanie tego typu danych jako `Object` pozwala przechowywać obiekty i klasy wystąpień równolegle z innymi typami danych w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a2caf-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2caf-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2caf-128">See Also</span></span>  
 [<span data-ttu-id="a2caf-129">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="a2caf-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="a2caf-130">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="a2caf-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="a2caf-131">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="a2caf-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="a2caf-132">Porady: odwoływanie się do bieżącego wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="a2caf-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="a2caf-133">Porady: wyznaczyć, jakiego typu odnosi się zmienna obiektu</span><span class="sxs-lookup"><span data-stu-id="a2caf-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [<span data-ttu-id="a2caf-134">Porady: Określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="a2caf-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="a2caf-135">Porady: Określanie, czy dwa obiekty są identyczne</span><span class="sxs-lookup"><span data-stu-id="a2caf-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [<span data-ttu-id="a2caf-136">Typy danych</span><span class="sxs-lookup"><span data-stu-id="a2caf-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
