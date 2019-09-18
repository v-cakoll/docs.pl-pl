---
title: 'Instrukcje: Zablokuj więcej niż jedną wartość w zmiennej (Visual Basic)'
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
ms.openlocfilehash: 8d07a34a98303f9d220dba0a3c955120b421340e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054197"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="f9823-102">Instrukcje: Zablokuj więcej niż jedną wartość w zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9823-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="f9823-103">Zmienna zawiera więcej niż jedną wartość, jeśli deklaruje ją jako *złożony typ danych*.</span><span class="sxs-lookup"><span data-stu-id="f9823-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="f9823-104">[Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) obejmują struktury, tablice i klasy.</span><span class="sxs-lookup"><span data-stu-id="f9823-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="f9823-105">Zmienna złożonego typu danych może zawierać kombinację podstawowych typów danych i innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="f9823-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="f9823-106">Struktury i klasy mogą przechowywać kod oraz dane.</span><span class="sxs-lookup"><span data-stu-id="f9823-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="f9823-107">Aby przechowywać więcej niż jedną wartość w zmiennej</span><span class="sxs-lookup"><span data-stu-id="f9823-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="f9823-108">Określ typ danych złożonych, który ma być używany dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f9823-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="f9823-109">Jeśli złożony typ danych nie jest jeszcze zdefiniowany, zdefiniuj go tak, aby zmienna mogła z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="f9823-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="f9823-110">Zdefiniuj strukturę przy użyciu [instrukcji struktury](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f9823-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="f9823-111">Zdefiniuj tablicę z [instrukcją Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f9823-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="f9823-112">Zdefiniuj klasę z [instrukcją klasy](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f9823-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="f9823-113">Zadeklaruj zmienną za pomocą `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f9823-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="f9823-114">Postępuj według nazwy zmiennej z `As` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="f9823-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="f9823-115">`As` Użyj słowa kluczowego z nazwą odpowiedniego złożonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="f9823-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9823-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9823-116">See also</span></span>

- [<span data-ttu-id="f9823-117">Typy danych</span><span class="sxs-lookup"><span data-stu-id="f9823-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f9823-118">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="f9823-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="f9823-119">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="f9823-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="f9823-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="f9823-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f9823-121">Tablice</span><span class="sxs-lookup"><span data-stu-id="f9823-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="f9823-122">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="f9823-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="f9823-123">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="f9823-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
