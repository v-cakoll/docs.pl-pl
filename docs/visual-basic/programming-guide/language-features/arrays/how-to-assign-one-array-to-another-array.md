---
title: 'Instrukcje: Przypisywanie tablicy do innej tablicy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 834dad07ec1f4116aca72a184ccffc664d0a42ed
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835287"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="e8f83-102">Instrukcje: Przypisywanie tablicy do innej tablicy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8f83-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="e8f83-103">Ponieważ tablice są obiektami, będziesz ich używać w instrukcji przypisania, podobnie jak inne typy obiektów.</span><span class="sxs-lookup"><span data-stu-id="e8f83-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="e8f83-104">Zmienną tablicową mieści wskaźnik do danych stanowiące elementów tablicy i informacji Ranga i długość i przypisania kopiuje tylko ten wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="e8f83-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="e8f83-105">Aby przypisać jednej tablicy do innej tablicy</span><span class="sxs-lookup"><span data-stu-id="e8f83-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="e8f83-106">Upewnij się, że dwie tablice mają tę samą rangę (liczba wymiarów) i typy danych zgodne elementu.</span><span class="sxs-lookup"><span data-stu-id="e8f83-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="e8f83-107">Używać instrukcji przypisania standardowych można przypisać tablica źródłowa do tablicy docelowej.</span><span class="sxs-lookup"><span data-stu-id="e8f83-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="e8f83-108">Nie wykonuj obu nazwa tablicy za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="e8f83-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="e8f83-109">Podczas przypisywania tablicy do innej, obowiązują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="e8f83-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="e8f83-110">**Równe rangę.**</span><span class="sxs-lookup"><span data-stu-id="e8f83-110">**Equal Ranks.**</span></span> <span data-ttu-id="e8f83-111">Ranga tablicy docelowej (liczba wymiarów) musi być taka sama jak tablica źródłowa.</span><span class="sxs-lookup"><span data-stu-id="e8f83-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="e8f83-112">Podana rangę dwie tablice są równe, wymiary nie są równe.</span><span class="sxs-lookup"><span data-stu-id="e8f83-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="e8f83-113">Liczba elementów w określonym wymiarze, które można zmienić podczas przypisywania.</span><span class="sxs-lookup"><span data-stu-id="e8f83-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="e8f83-114">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="e8f83-114">**Element Types.**</span></span> <span data-ttu-id="e8f83-115">Musi mieć albo obu tablicach *odwołania do typu* elementów lub obu tablicach, musi mieć *typu wartości* elementów.</span><span class="sxs-lookup"><span data-stu-id="e8f83-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="e8f83-116">Aby uzyskać więcej informacji, zobacz [typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e8f83-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="e8f83-117">Jeśli elementy typu wartości obu tablicach, typów danych elementów musi być dokładnie takie same.</span><span class="sxs-lookup"><span data-stu-id="e8f83-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="e8f83-118">Jedynym wyjątkiem jest, którą można przypisać tablicę `Enum` elementów do tablicy typu podstawowego `Enum`.</span><span class="sxs-lookup"><span data-stu-id="e8f83-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="e8f83-119">Jeśli obu tablicach ma odwołanie do typu elementów, typ elementu źródłowego musi pochodzić od typu elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e8f83-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="e8f83-120">W przypadku dwóch tablic mają ten sam relację dziedziczenia jako ich elementy.</span><span class="sxs-lookup"><span data-stu-id="e8f83-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="e8f83-121">Jest to nazywane *Kowariancja tablicy*.</span><span class="sxs-lookup"><span data-stu-id="e8f83-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="e8f83-122">Kompilator zgłasza błąd, jeśli powyższe zasady są naruszone, na przykład jeśli typy danych nie są zgodne lub rangę są nierówne.</span><span class="sxs-lookup"><span data-stu-id="e8f83-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="e8f83-123">Możesz dodać obsługę błędów do kodu w taki sposób, aby upewnić się, że tablice są zgodne, przed podjęciem próby wykonania przypisania.</span><span class="sxs-lookup"><span data-stu-id="e8f83-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="e8f83-124">Można również użyć [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) — słowo kluczowe, jeśli chcesz uniknąć, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e8f83-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f83-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8f83-125">See also</span></span>

- [<span data-ttu-id="e8f83-126">Tablice</span><span class="sxs-lookup"><span data-stu-id="e8f83-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="e8f83-127">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="e8f83-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="e8f83-128">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e8f83-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="e8f83-129">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="e8f83-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
