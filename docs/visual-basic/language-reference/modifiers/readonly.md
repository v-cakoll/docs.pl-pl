---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: e2957bf49292dfcafab8e78f4b997247c34ad279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="c3ba1-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3ba1-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="c3ba1-103">Określa, że zmienna lub właściwość mogą być odczytywane, ale nie są zapisywane.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3ba1-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3ba1-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c3ba1-105">Reguły</span><span class="sxs-lookup"><span data-stu-id="c3ba1-105">Rules</span></span>  
  
-   <span data-ttu-id="c3ba1-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="c3ba1-106">**Declaration Context.**</span></span> <span data-ttu-id="c3ba1-107">Można użyć `ReadOnly` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="c3ba1-108">Oznacza to, że w kontekście deklaracji `ReadOnly` elementu musi być klasą, strukturą lub modułu i nie może być plik źródłowy, przestrzeni nazw lub procedury.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="c3ba1-109">**Łączna modyfikatorów.**</span><span class="sxs-lookup"><span data-stu-id="c3ba1-109">**Combined Modifiers.**</span></span> <span data-ttu-id="c3ba1-110">Nie można określić `ReadOnly` razem z `Static` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="c3ba1-111">**Przypisywanie wartości.**</span><span class="sxs-lookup"><span data-stu-id="c3ba1-111">**Assigning a Value.**</span></span> <span data-ttu-id="c3ba1-112">Korzystanie z kodu `ReadOnly` właściwości nie można ustawić jej wartości.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="c3ba1-113">Jednak kod, który ma dostęp do powiązany magazyn można przypisać lub zmień wartość w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="c3ba1-114">Można przypisać wartości do `ReadOnly` zmiennej tylko w jego deklaracji lub w konstruktorze klasy lub struktury, w którym jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="c3ba1-115">Kiedy należy użyć zmiennej tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c3ba1-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="c3ba1-116">Istnieją sytuacje, w których nie można użyć [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md) Aby zadeklarować i przypisać wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="c3ba1-117">Na przykład `Const` instrukcja nie może zaakceptować typu danych, którego chcesz przypisać lub nie można obliczyć wartość w czasie kompilacji z wyrażeniem stałym.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="c3ba1-118">Możesz nawet nie wiedzieć, wartość w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="c3ba1-119">W takich przypadkach można użyć `ReadOnly` zmienną do przechowywania wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3ba1-120">Jeśli typ danych zmiennej jest typem referencyjnym, takich jak tablica lub wystąpienia klasy, nawet jeśli jest samej zmiennej można zmienić jej elementów członkowskich `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="c3ba1-121">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="c3ba1-122">Podczas inicjowania tablicy wskazywana przez `characterArray()` blokad "x", "y" i "z".</span><span class="sxs-lookup"><span data-stu-id="c3ba1-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="c3ba1-123">Ponieważ zmiennej `characterArray` jest `ReadOnly`, jego wartość nie można zmienić po jego inicjowania; będący, nowej tablicy nie można przypisać do niej.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="c3ba1-124">Można jednak zmienić wartości co najmniej jeden z elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="c3ba1-125">Po wywołaniu procedury `changeArrayElement`, tablicy wskazywana przez `characterArray()` blokad "x", "M" i "z".</span><span class="sxs-lookup"><span data-stu-id="c3ba1-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="c3ba1-126">Należy pamiętać, że jest to podobne do deklarowaniu parametru procedury należy [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), który uniemożliwia zmianę z samym argumentem wywołania procedury, ale pozwala zmienić jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3ba1-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3ba1-127">Example</span></span>  
 <span data-ttu-id="c3ba1-128">W poniższym przykładzie zdefiniowano `ReadOnly` właściwości data, na którym został dzierżawione pracownika.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="c3ba1-129">Magazynów klas właściwość wartość wewnętrznie jako `Private` kodu zmiennej i tylko wewnątrz klasy można zmienić tę wartość.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="c3ba1-130">Właściwość jest jednak `Public`, i kodu, który można uzyskać dostępu do klasy mogą odczytać właściwości.</span><span class="sxs-lookup"><span data-stu-id="c3ba1-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 <span data-ttu-id="c3ba1-131">`ReadOnly` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="c3ba1-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c3ba1-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c3ba1-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="c3ba1-133">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c3ba1-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3ba1-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3ba1-134">See Also</span></span>  
 [<span data-ttu-id="c3ba1-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="c3ba1-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="c3ba1-136">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c3ba1-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
