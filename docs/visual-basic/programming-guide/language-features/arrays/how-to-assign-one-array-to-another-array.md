---
title: 'Porady: przypisywanie tablicy do innej tablicy (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="e7087-102">Porady: przypisywanie tablicy do innej tablicy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7087-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>
<span data-ttu-id="e7087-103">Ponieważ tablic są obiektami, można używać ich w instrukcji przypisania, podobnie jak inne typy obiektów.</span><span class="sxs-lookup"><span data-stu-id="e7087-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="e7087-104">Zmienną tablicową zawiera wskaźnik do stanowiące elementów tablicy i informacje o randze i długość danych, i przypisania kopiuje tylko ten wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="e7087-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>  
  
### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="e7087-105">Aby przypisywanie tablicy do innej tablicy</span><span class="sxs-lookup"><span data-stu-id="e7087-105">To assign one array to another array</span></span>  
  
1.  <span data-ttu-id="e7087-106">Upewnij się, że dwóch tablic mają taką samą rangę (liczba wymiarów) i element niezgodne typy danych.</span><span class="sxs-lookup"><span data-stu-id="e7087-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>  
  
2.  <span data-ttu-id="e7087-107">Użyj instrukcji przypisania standardowych można przypisać tablicy źródłowej do tablicy docelowej.</span><span class="sxs-lookup"><span data-stu-id="e7087-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="e7087-108">Nie wykonuj albo nazwa tablicy w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="e7087-108">Do not follow either array name with parentheses.</span></span>  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 <span data-ttu-id="e7087-109">Po przypisaniu tablicy do innej, obowiązują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="e7087-109">When you assign one array to another, the following rules apply:</span></span>  
  
-   <span data-ttu-id="e7087-110">**Taki sam rangi.**</span><span class="sxs-lookup"><span data-stu-id="e7087-110">**Equal Ranks.**</span></span> <span data-ttu-id="e7087-111">(Liczba wymiarów) rangę tablicy docelowej musi być taka sama jak tablicy źródłowej.</span><span class="sxs-lookup"><span data-stu-id="e7087-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>  
  
     <span data-ttu-id="e7087-112">Zakładając, że rangi dwóch tablic są takie same, wymiary nie są równe.</span><span class="sxs-lookup"><span data-stu-id="e7087-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="e7087-113">Liczba elementów w określonym wymiarze można zmienić podczas przypisywania.</span><span class="sxs-lookup"><span data-stu-id="e7087-113">The number of elements in a given dimension can change during assignment.</span></span>  
  
-   <span data-ttu-id="e7087-114">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="e7087-114">**Element Types.**</span></span> <span data-ttu-id="e7087-115">Musi mieć albo obu tablice *zawierają odwołania do typu* elementy lub obu tablic musi mieć *typu wartości* elementów.</span><span class="sxs-lookup"><span data-stu-id="e7087-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="e7087-116">Aby uzyskać więcej informacji, zobacz [typów wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e7087-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
    -   <span data-ttu-id="e7087-117">Jeśli oba tablice elementów typu wartości, typy elementów danych muszą być dokładnie takie same.</span><span class="sxs-lookup"><span data-stu-id="e7087-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="e7087-118">Jedynym wyjątkiem jest przypisanie tablicę `Enum` elementów do tablicy typu podstawowego `Enum`.</span><span class="sxs-lookup"><span data-stu-id="e7087-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>  
  
    -   <span data-ttu-id="e7087-119">Jeśli obydwie tablice elementów Typ odwołania, typu elementu źródłowego musi pochodzić od typu elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e7087-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="e7087-120">W przypadku dwóch tablic mieć tej samej relacji dziedziczenia jako ich elementów.</span><span class="sxs-lookup"><span data-stu-id="e7087-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="e7087-121">Ta metoda jest wywoływana *Kowariancja tablicy*.</span><span class="sxs-lookup"><span data-stu-id="e7087-121">This is called *array covariance*.</span></span>  
  
 <span data-ttu-id="e7087-122">Kompilator zgłasza błąd, jeśli powyższe zasady naruszenia, na przykład jeśli typy danych są niezgodne lub rangę nie są równe.</span><span class="sxs-lookup"><span data-stu-id="e7087-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="e7087-123">Możesz dodać obsługę błędów do swój kod, aby upewnić się, że tablice są zgodne, przed podjęciem próby wykonania przypisania.</span><span class="sxs-lookup"><span data-stu-id="e7087-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="e7087-124">Można również użyć [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) — słowo kluczowe, jeśli chcesz uniknąć generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e7087-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7087-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7087-125">See Also</span></span>  
 [<span data-ttu-id="e7087-126">Tablice</span><span class="sxs-lookup"><span data-stu-id="e7087-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="e7087-127">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="e7087-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="e7087-128">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e7087-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="e7087-129">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="e7087-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
