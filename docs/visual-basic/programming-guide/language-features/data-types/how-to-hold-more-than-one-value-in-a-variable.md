---
title: 'Instrukcje: Utrzymywanie więcej niż jednej wartości w zmiennej'
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
ms.openlocfilehash: 399c5909ee6988f96bcc85260b0401f3bd18a0f2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393899"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="1e1c5-102">Porady: utrzymywanie więcej niż jednej wartości w zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e1c5-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="1e1c5-103">Zmienna zawiera więcej niż jedną wartość, jeśli deklaruje ją jako *złożony typ danych*.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="1e1c5-104">[Złożone typy danych](composite-data-types.md) obejmują struktury, tablice i klasy.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-104">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="1e1c5-105">Zmienna złożonego typu danych może zawierać kombinację podstawowych typów danych i innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="1e1c5-106">Struktury i klasy mogą przechowywać kod oraz dane.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-106">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="1e1c5-107">Aby przechowywać więcej niż jedną wartość w zmiennej</span><span class="sxs-lookup"><span data-stu-id="1e1c5-107">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="1e1c5-108">Określ typ danych złożonych, który ma być używany dla zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-108">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="1e1c5-109">Jeśli złożony typ danych nie jest jeszcze zdefiniowany, zdefiniuj go tak, aby zmienna mogła z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="1e1c5-110">Zdefiniuj strukturę przy użyciu [instrukcji struktury](../../../language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e1c5-110">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="1e1c5-111">Zdefiniuj tablicę z [instrukcją Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e1c5-111">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="1e1c5-112">Zdefiniuj klasę z [instrukcją klasy](../../../language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1e1c5-112">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="1e1c5-113">Zadeklaruj zmienną za pomocą `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-113">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="1e1c5-114">Postępuj według nazwy zmiennej z `As` klauzulą.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-114">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="1e1c5-115">Użyj `As` słowa kluczowego z nazwą odpowiedniego złożonego typu danych.</span><span class="sxs-lookup"><span data-stu-id="1e1c5-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e1c5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e1c5-116">See also</span></span>

- [<span data-ttu-id="1e1c5-117">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1e1c5-117">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="1e1c5-118">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="1e1c5-118">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="1e1c5-119">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="1e1c5-119">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="1e1c5-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="1e1c5-120">Structures</span></span>](structures.md)
- [<span data-ttu-id="1e1c5-121">Tablice</span><span class="sxs-lookup"><span data-stu-id="1e1c5-121">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="1e1c5-122">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="1e1c5-122">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="1e1c5-123">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="1e1c5-123">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
