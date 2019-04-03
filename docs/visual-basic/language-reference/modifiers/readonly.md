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
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825394"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="f59b2-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f59b2-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="f59b2-103">Określa, że zmiennej lub właściwości mogą być odczytywane, ale nie jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="f59b2-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f59b2-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f59b2-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f59b2-105">reguły</span><span class="sxs-lookup"><span data-stu-id="f59b2-105">Rules</span></span>  
  
-   <span data-ttu-id="f59b2-106">**Kontekst deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="f59b2-106">**Declaration Context.**</span></span> <span data-ttu-id="f59b2-107">Możesz użyć `ReadOnly` tylko na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="f59b2-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="f59b2-108">Oznacza to, że kontekst deklaracji `ReadOnly` elementu musi być klasy, struktury lub modułu, a nie może być plikiem źródłowym, przestrzeń nazw lub procedury.</span><span class="sxs-lookup"><span data-stu-id="f59b2-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="f59b2-109">**Modyfikatory połączone.**</span><span class="sxs-lookup"><span data-stu-id="f59b2-109">**Combined Modifiers.**</span></span> <span data-ttu-id="f59b2-110">Nie można określić `ReadOnly` wraz z `Static` w tej samej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f59b2-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="f59b2-111">**Przypisywanie wartości.**</span><span class="sxs-lookup"><span data-stu-id="f59b2-111">**Assigning a Value.**</span></span> <span data-ttu-id="f59b2-112">Korzystanie z kodu `ReadOnly` właściwości nie można ustawić jej wartość.</span><span class="sxs-lookup"><span data-stu-id="f59b2-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="f59b2-113">Jednak kod, który ma dostęp do podstawowej magazynu można przypisać lub zmień wartość w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="f59b2-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="f59b2-114">Można przypisać wartości do `ReadOnly` zmiennych, tylko w jego deklaracji lub w konstruktorze klasy lub struktury, w którym jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="f59b2-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="f59b2-115">Kiedy należy używać zmiennej tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f59b2-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="f59b2-116">Istnieją sytuacje, w których nie można użyć [instrukcja Const](../../../visual-basic/language-reference/statements/const-statement.md) zadeklarować i przypisać wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="f59b2-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="f59b2-117">Na przykład `Const` instrukcji, nie może zaakceptować typu danych, którą chcesz przypisać lub mogą być gotowy do obliczenia wartości w czasie kompilacji z wyrażeniem stałym.</span><span class="sxs-lookup"><span data-stu-id="f59b2-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="f59b2-118">Możesz nawet nie wiedzieć, wartość w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f59b2-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="f59b2-119">W takich przypadkach można użyć `ReadOnly` zmienną do przechowywania wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="f59b2-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f59b2-120">Jeśli typ danych zmiennej jest typem referencyjnym, takich jak tablica lub wystąpienia klasy, jej członków można zmienić, nawet jeśli sama zmienna jest `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="f59b2-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="f59b2-121">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="f59b2-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="f59b2-122">Podczas inicjowania tablicy, wskazywana przez `characterArray()` przechowuje "x", "y" i "z".</span><span class="sxs-lookup"><span data-stu-id="f59b2-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="f59b2-123">Ponieważ zmienna `characterArray` jest `ReadOnly`, jego wartość nie można zmienić po jego zainicjowaniu; będącego, nowej tablicy nie można przypisać do niej.</span><span class="sxs-lookup"><span data-stu-id="f59b2-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="f59b2-124">Można jednak zmienić wartości co najmniej jednego elementy członkowskie tablicy.</span><span class="sxs-lookup"><span data-stu-id="f59b2-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="f59b2-125">Po wywołaniu do procedury `changeArrayElement`, tablicy wskazywany przez `characterArray()` przechowuje "x", "M" i "z".</span><span class="sxs-lookup"><span data-stu-id="f59b2-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="f59b2-126">Należy pamiętać, że jest to podobne do deklarowania parametr procedury, aby być [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), które uniemożliwia zmianę z samym argumentem wywoływania procedury, ale pozwala zmienić jej członków.</span><span class="sxs-lookup"><span data-stu-id="f59b2-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f59b2-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f59b2-127">Example</span></span>  
 <span data-ttu-id="f59b2-128">W poniższym przykładzie zdefiniowano `ReadOnly` właściwości daty, na którym został zatrudniony pracownika.</span><span class="sxs-lookup"><span data-stu-id="f59b2-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="f59b2-129">Magazyny klasy wartość wewnętrznie jako `Private` zmiennej, a tylko kod wewnątrz klasy może zmienić tę wartość.</span><span class="sxs-lookup"><span data-stu-id="f59b2-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="f59b2-130">Jednak właściwość jest `Public`, i wszelki kod, który mogą uzyskiwać dostęp do tej klasy może być odczytana właściwość.</span><span class="sxs-lookup"><span data-stu-id="f59b2-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="f59b2-131">`ReadOnly` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="f59b2-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f59b2-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f59b2-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="f59b2-133">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="f59b2-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f59b2-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f59b2-134">See also</span></span>

- [<span data-ttu-id="f59b2-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="f59b2-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="f59b2-136">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f59b2-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
