---
title: ReadOnly
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
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351279"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="434dd-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="434dd-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="434dd-103">Specifies that a variable or property can be read but not written.</span><span class="sxs-lookup"><span data-stu-id="434dd-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="434dd-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="434dd-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="434dd-105">Rules</span><span class="sxs-lookup"><span data-stu-id="434dd-105">Rules</span></span>

- <span data-ttu-id="434dd-106">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="434dd-106">**Declaration Context.**</span></span> <span data-ttu-id="434dd-107">You can use `ReadOnly` only at module level.</span><span class="sxs-lookup"><span data-stu-id="434dd-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="434dd-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span><span class="sxs-lookup"><span data-stu-id="434dd-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="434dd-109">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="434dd-109">**Combined Modifiers.**</span></span> <span data-ttu-id="434dd-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="434dd-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="434dd-111">**Assigning a Value.**</span><span class="sxs-lookup"><span data-stu-id="434dd-111">**Assigning a Value.**</span></span> <span data-ttu-id="434dd-112">Code consuming a `ReadOnly` property cannot set its value.</span><span class="sxs-lookup"><span data-stu-id="434dd-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="434dd-113">But code that has access to the underlying storage can assign or change the value at any time.</span><span class="sxs-lookup"><span data-stu-id="434dd-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="434dd-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span><span class="sxs-lookup"><span data-stu-id="434dd-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="434dd-115">When to Use a ReadOnly Variable</span><span class="sxs-lookup"><span data-stu-id="434dd-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="434dd-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span><span class="sxs-lookup"><span data-stu-id="434dd-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="434dd-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span><span class="sxs-lookup"><span data-stu-id="434dd-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="434dd-118">You might not even know the value at compile time.</span><span class="sxs-lookup"><span data-stu-id="434dd-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="434dd-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span><span class="sxs-lookup"><span data-stu-id="434dd-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="434dd-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="434dd-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="434dd-121">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="434dd-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="434dd-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span><span class="sxs-lookup"><span data-stu-id="434dd-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="434dd-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span><span class="sxs-lookup"><span data-stu-id="434dd-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="434dd-124">However, you can change the values of one or more of the array members.</span><span class="sxs-lookup"><span data-stu-id="434dd-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="434dd-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span><span class="sxs-lookup"><span data-stu-id="434dd-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="434dd-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span><span class="sxs-lookup"><span data-stu-id="434dd-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="434dd-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="434dd-127">Example</span></span>

<span data-ttu-id="434dd-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span><span class="sxs-lookup"><span data-stu-id="434dd-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="434dd-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span><span class="sxs-lookup"><span data-stu-id="434dd-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="434dd-130">However, the property is `Public`, and any code that can access the class can read the property.</span><span class="sxs-lookup"><span data-stu-id="434dd-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="434dd-131">The `ReadOnly` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="434dd-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="434dd-132">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="434dd-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="434dd-133">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="434dd-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="434dd-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="434dd-134">See also</span></span>

- [<span data-ttu-id="434dd-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="434dd-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="434dd-136">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="434dd-136">Keywords</span></span>](../keywords/index.md)
