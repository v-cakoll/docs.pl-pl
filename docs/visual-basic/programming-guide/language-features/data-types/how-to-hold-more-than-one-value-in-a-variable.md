---
title: 'Instrukcje: Utrzymywanie więcej niż jedną wartość w zmiennej (Visual Basic)'
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
ms.openlocfilehash: e2e1648ea508ecdd744adb8d2a4f7fdbc1e586c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332264"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="6d8fd-102">Instrukcje: Utrzymywanie więcej niż jedną wartość w zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d8fd-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="6d8fd-103">Zmienna zawiera więcej niż jedną wartość, jeśli zadeklarujesz będzie *złożonego typu danych*.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="6d8fd-104">[Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) zawierają klasy, tablic i struktur.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="6d8fd-105">Zmienną typu złożonych danych może zawierać kombinację podstawowe typy danych i innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="6d8fd-106">Struktury i klasy może zawierać kod, a także dane.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="6d8fd-107">Aby pomieścić więcej niż jedną wartość w zmiennej</span><span class="sxs-lookup"><span data-stu-id="6d8fd-107">To hold more than one value in a variable</span></span>  
  
1. <span data-ttu-id="6d8fd-108">Wyznaczyć, jakiego typu danych, którego chcesz użyć zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2. <span data-ttu-id="6d8fd-109">Jeśli typ złożony danych nie jest już zdefiniowany, zdefiniuj tak, aby użyć go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    -   <span data-ttu-id="6d8fd-110">Zdefiniuj strukturę z [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d8fd-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    -   <span data-ttu-id="6d8fd-111">Zdefiniuj tablicy o liczbie [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d8fd-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    -   <span data-ttu-id="6d8fd-112">Zdefiniuj klasę z [Class — instrukcja](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d8fd-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3. <span data-ttu-id="6d8fd-113">Deklarowanie zmiennej za pomocą `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-113">Declare your variable with a `Dim` statement.</span></span>  
  
4. <span data-ttu-id="6d8fd-114">Postępuj zgodnie z nazwą zmiennej `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-114">Follow the variable name with an `As` clause.</span></span>  
  
5. <span data-ttu-id="6d8fd-115">Postępuj zgodnie z `As` — słowo kluczowe o nazwie odpowiednich złożonych typów danych.</span><span class="sxs-lookup"><span data-stu-id="6d8fd-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d8fd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d8fd-116">See also</span></span>

- [<span data-ttu-id="6d8fd-117">Typy danych</span><span class="sxs-lookup"><span data-stu-id="6d8fd-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="6d8fd-118">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="6d8fd-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [<span data-ttu-id="6d8fd-119">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="6d8fd-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="6d8fd-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="6d8fd-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="6d8fd-121">Tablice</span><span class="sxs-lookup"><span data-stu-id="6d8fd-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="6d8fd-122">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="6d8fd-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="6d8fd-123">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="6d8fd-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
