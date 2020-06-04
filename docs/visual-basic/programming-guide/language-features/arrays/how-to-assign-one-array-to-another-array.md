---
title: 'Porady: przypisywanie tablicy do innej tablicy'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413082"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="cb280-102">Porady: przypisywanie tablicy do innej tablicy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb280-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="cb280-103">Ponieważ tablice są obiektami, można ich używać w instrukcjach przypisania, takich jak inne typy obiektów.</span><span class="sxs-lookup"><span data-stu-id="cb280-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="cb280-104">Zmienna tablicowa zawiera wskaźnik do danych tworzących elementy tablicy oraz informacje o rangi i długości, a przypisanie kopiuje tylko ten wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="cb280-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="cb280-105">Aby przypisać jedną tablicę do innej tablicy</span><span class="sxs-lookup"><span data-stu-id="cb280-105">To assign one array to another array</span></span>

1. <span data-ttu-id="cb280-106">Upewnij się, że dwie tablice mają taką samą rangę (liczbę wymiarów), jak i zgodne typy danych elementów.</span><span class="sxs-lookup"><span data-stu-id="cb280-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="cb280-107">Użyj standardowej instrukcji przypisania, aby przypisać tablicę źródłową do tablicy docelowej.</span><span class="sxs-lookup"><span data-stu-id="cb280-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="cb280-108">Nie Obserwuj żadnej nazwy tablicy z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="cb280-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="cb280-109">Po przypisaniu jednej tablicy do innej obowiązują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="cb280-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="cb280-110">**Równe Range.**</span><span class="sxs-lookup"><span data-stu-id="cb280-110">**Equal Ranks.**</span></span> <span data-ttu-id="cb280-111">Ranga (liczba wymiarów) tablicy docelowej musi być taka sama jak w przypadku tablicy źródłowej.</span><span class="sxs-lookup"><span data-stu-id="cb280-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="cb280-112">Jeśli Range dwóch tablic są równe, wymiary nie muszą być równe.</span><span class="sxs-lookup"><span data-stu-id="cb280-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="cb280-113">Liczba elementów w danym wymiarze może ulec zmianie podczas przypisywania.</span><span class="sxs-lookup"><span data-stu-id="cb280-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="cb280-114">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="cb280-114">**Element Types.**</span></span> <span data-ttu-id="cb280-115">Obie tablice muszą mieć elementy *typu referencyjnego* lub obie tablice muszą mieć elementy *typu wartości* .</span><span class="sxs-lookup"><span data-stu-id="cb280-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="cb280-116">Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](../data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="cb280-116">For more information, see [Value Types and Reference Types](../data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="cb280-117">Jeśli obie tablice mają elementy typu wartości, typy danych elementu muszą być dokładnie takie same.</span><span class="sxs-lookup"><span data-stu-id="cb280-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="cb280-118">Jedynym wyjątkiem jest to, że można przypisać tablicę `Enum` elementów do tablicy typu podstawowego tego elementu `Enum` .</span><span class="sxs-lookup"><span data-stu-id="cb280-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="cb280-119">Jeśli obie tablice mają elementy typu referencyjnego, typ elementu źródłowego musi pochodzić od typu elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="cb280-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="cb280-120">W takim przypadku dwie tablice mają taką samą relację dziedziczenia jak ich elementy.</span><span class="sxs-lookup"><span data-stu-id="cb280-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="cb280-121">Jest to nazywane *kowariancją tablicową*.</span><span class="sxs-lookup"><span data-stu-id="cb280-121">This is called *array covariance*.</span></span>

<span data-ttu-id="cb280-122">Kompilator zgłasza błąd, jeśli powyższe reguły zostały naruszone, na przykład jeśli typy danych nie są zgodne lub Range nie są równe.</span><span class="sxs-lookup"><span data-stu-id="cb280-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="cb280-123">Można dodać obsługę błędów do kodu, aby upewnić się, że tablice są zgodne przed próbą przypisania.</span><span class="sxs-lookup"><span data-stu-id="cb280-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="cb280-124">Możesz również użyć słowa kluczowego [operatora TryCast](../../../language-reference/operators/trycast-operator.md) , jeśli chcesz uniknąć zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cb280-124">You can also use the [TryCast Operator](../../../language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb280-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb280-125">See also</span></span>

- [<span data-ttu-id="cb280-126">Tablice</span><span class="sxs-lookup"><span data-stu-id="cb280-126">Arrays</span></span>](index.md)
- [<span data-ttu-id="cb280-127">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="cb280-127">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="cb280-128">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cb280-128">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="cb280-129">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="cb280-129">Array Conversions</span></span>](../data-types/array-conversions.md)
