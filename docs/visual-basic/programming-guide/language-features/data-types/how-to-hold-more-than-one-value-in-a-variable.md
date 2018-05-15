---
title: 'Porady: utrzymywanie więcej niż jednej wartości w zmiennej (Visual Basic)'
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
ms.openlocfilehash: 783c75ed4577831b7ca444870c97063e8a057346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="e5409-102">Porady: utrzymywanie więcej niż jednej wartości w zmiennej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5409-102">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>
<span data-ttu-id="e5409-103">Zmienna posiada więcej niż jedną wartość zadeklarowana za *złożonego typu danych*.</span><span class="sxs-lookup"><span data-stu-id="e5409-103">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>  
  
 <span data-ttu-id="e5409-104">[Złożone typy danych](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) obejmują struktur, tablic i klasy.</span><span class="sxs-lookup"><span data-stu-id="e5409-104">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="e5409-105">Zmienna typu złożonego danych może zawierać kombinację podstawowe typy danych i innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="e5409-105">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="e5409-106">Struktury i klasy może zawierać kod, a także dane.</span><span class="sxs-lookup"><span data-stu-id="e5409-106">Structures and classes can hold code as well as data.</span></span>  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="e5409-107">Aby przechowywać więcej niż jedną wartość w zmiennej</span><span class="sxs-lookup"><span data-stu-id="e5409-107">To hold more than one value in a variable</span></span>  
  
1.  <span data-ttu-id="e5409-108">Wyznaczyć, jakiego typu danych, którego chcesz użyć dla zmiennej użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e5409-108">Determine what composite data type you want to use for your variable.</span></span>  
  
2.  <span data-ttu-id="e5409-109">Jeśli typ danych nie jest już zdefiniowana, należy zdefiniować go tak, aby użyć go do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e5409-109">If the composite data type is not already defined, define it so that your variable can use it.</span></span>  
  
    -   <span data-ttu-id="e5409-110">Zdefiniuj struktury z [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5409-110">Define a structure with a [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
    -   <span data-ttu-id="e5409-111">Zdefiniuj tablicy o [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5409-111">Define an array with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
    -   <span data-ttu-id="e5409-112">Definiowanie klasy, z [Class — instrukcja](../../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5409-112">Define a class with a [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
3.  <span data-ttu-id="e5409-113">Deklarowanie zmiennej użytkownika z `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e5409-113">Declare your variable with a `Dim` statement.</span></span>  
  
4.  <span data-ttu-id="e5409-114">Po nazwie zmiennej `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e5409-114">Follow the variable name with an `As` clause.</span></span>  
  
5.  <span data-ttu-id="e5409-115">Wykonaj `As` — słowo kluczowe z nazwą typu złożonego danych.</span><span class="sxs-lookup"><span data-stu-id="e5409-115">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5409-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5409-116">See Also</span></span>  
 [<span data-ttu-id="e5409-117">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e5409-117">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="e5409-118">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="e5409-118">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="e5409-119">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="e5409-119">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="e5409-120">Struktury</span><span class="sxs-lookup"><span data-stu-id="e5409-120">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="e5409-121">Tablice</span><span class="sxs-lookup"><span data-stu-id="e5409-121">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="e5409-122">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="e5409-122">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="e5409-123">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="e5409-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
