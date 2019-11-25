---
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351497"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="827ce-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="827ce-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="827ce-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span><span class="sxs-lookup"><span data-stu-id="827ce-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="827ce-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="827ce-104">Remarks</span></span>  
 <span data-ttu-id="827ce-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span><span class="sxs-lookup"><span data-stu-id="827ce-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="827ce-106">This saves the derived classes from having to redefine the common elements.</span><span class="sxs-lookup"><span data-stu-id="827ce-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="827ce-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span><span class="sxs-lookup"><span data-stu-id="827ce-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="827ce-108">In such a case, you want the consuming code to create objects only from the derived classes.</span><span class="sxs-lookup"><span data-stu-id="827ce-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="827ce-109">You use `MustInherit` on the base class to enforce this.</span><span class="sxs-lookup"><span data-stu-id="827ce-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="827ce-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span><span class="sxs-lookup"><span data-stu-id="827ce-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="827ce-111">You can define a base class and derive all these related classes from it.</span><span class="sxs-lookup"><span data-stu-id="827ce-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="827ce-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span><span class="sxs-lookup"><span data-stu-id="827ce-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="827ce-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span><span class="sxs-lookup"><span data-stu-id="827ce-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="827ce-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="827ce-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="827ce-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span><span class="sxs-lookup"><span data-stu-id="827ce-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="827ce-116">All value types derive from <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="827ce-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="827ce-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span><span class="sxs-lookup"><span data-stu-id="827ce-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="827ce-118">Rules</span><span class="sxs-lookup"><span data-stu-id="827ce-118">Rules</span></span>  
  
- <span data-ttu-id="827ce-119">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="827ce-119">**Declaration Context.**</span></span> <span data-ttu-id="827ce-120">You can use `MustInherit` only in a `Class` statement.</span><span class="sxs-lookup"><span data-stu-id="827ce-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="827ce-121">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="827ce-121">**Combined Modifiers.**</span></span> <span data-ttu-id="827ce-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="827ce-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="827ce-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="827ce-123">Example</span></span>  
 <span data-ttu-id="827ce-124">The following example illustrates both forced inheritance and forced overriding.</span><span class="sxs-lookup"><span data-stu-id="827ce-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="827ce-125">The base class `shape` defines a variable `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="827ce-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="827ce-126">The classes `circle` and `square` derive from `shape`.</span><span class="sxs-lookup"><span data-stu-id="827ce-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="827ce-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span><span class="sxs-lookup"><span data-stu-id="827ce-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="827ce-128">You can declare `shape1` and `shape2` to be of type `shape`.</span><span class="sxs-lookup"><span data-stu-id="827ce-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="827ce-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="827ce-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="827ce-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span><span class="sxs-lookup"><span data-stu-id="827ce-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="827ce-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span><span class="sxs-lookup"><span data-stu-id="827ce-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="827ce-132">Użycie</span><span class="sxs-lookup"><span data-stu-id="827ce-132">Usage</span></span>  
 <span data-ttu-id="827ce-133">The `MustInherit` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="827ce-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="827ce-134">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="827ce-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="827ce-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="827ce-135">See also</span></span>

- [<span data-ttu-id="827ce-136">Inherits, instrukcja</span><span class="sxs-lookup"><span data-stu-id="827ce-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="827ce-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="827ce-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="827ce-138">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="827ce-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="827ce-139">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="827ce-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
