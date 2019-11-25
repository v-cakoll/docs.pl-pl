---
title: 'Porady: utrzymywanie więcej niż jednej wartości w zmiennej'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: d452fbf35f9d200348234b38c40f8636f0ec4b4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350022"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="7c7c9-102">Porady: utrzymywanie więcej niż jednej wartości w zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c7c9-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="7c7c9-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="7c7c9-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="7c7c9-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="7c7c9-106">Structures and classes can hold code as well as data.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="7c7c9-107">To hold more than one value in a variable</span><span class="sxs-lookup"><span data-stu-id="7c7c9-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="7c7c9-108">Determine what composite data type you want to use for your variable.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="7c7c9-109">If the composite data type is not already defined, define it so that your variable can use it.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="7c7c9-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7c7c9-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="7c7c9-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7c7c9-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="7c7c9-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7c7c9-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="7c7c9-113">Declare your variable with a `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="7c7c9-114">Follow the variable name with an `As` clause.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="7c7c9-115">Follow the `As` keyword with the name of the appropriate composite data type.</span><span class="sxs-lookup"><span data-stu-id="7c7c9-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c7c9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c7c9-116">See also</span></span>

- [<span data-ttu-id="7c7c9-117">Typy danych</span><span class="sxs-lookup"><span data-stu-id="7c7c9-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="7c7c9-118">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="7c7c9-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="7c7c9-119">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="7c7c9-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="7c7c9-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="7c7c9-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7c7c9-121">Tablice</span><span class="sxs-lookup"><span data-stu-id="7c7c9-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="7c7c9-122">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="7c7c9-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="7c7c9-123">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="7c7c9-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
