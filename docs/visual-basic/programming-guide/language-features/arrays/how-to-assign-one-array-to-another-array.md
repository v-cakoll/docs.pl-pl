---
title: 'Porady: przypisywanie tablicy do innej tablicy'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: be5337e36c2cc7ad9f9b32182b8575ac66bb4a50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351889"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a><span data-ttu-id="9a1e8-102">Porady: przypisywanie tablicy do innej tablicy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a1e8-102">How to: Assign One Array to Another Array (Visual Basic)</span></span>

<span data-ttu-id="9a1e8-103">Because arrays are objects, you can use them in assignment statements like other object types.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-103">Because arrays are objects, you can use them in assignment statements like other object types.</span></span> <span data-ttu-id="9a1e8-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-104">An array variable holds a pointer to the data constituting the array elements and the rank and length information, and an assignment copies only this pointer.</span></span>

### <a name="to-assign-one-array-to-another-array"></a><span data-ttu-id="9a1e8-105">To assign one array to another array</span><span class="sxs-lookup"><span data-stu-id="9a1e8-105">To assign one array to another array</span></span>

1. <span data-ttu-id="9a1e8-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-106">Ensure that the two arrays have the same rank (number of dimensions) and compatible element data types.</span></span>

2. <span data-ttu-id="9a1e8-107">Use a standard assignment statement to assign the source array to the destination array.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-107">Use a standard assignment statement to assign the source array to the destination array.</span></span> <span data-ttu-id="9a1e8-108">Do not follow either array name with parentheses.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-108">Do not follow either array name with parentheses.</span></span>

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

<span data-ttu-id="9a1e8-109">When you assign one array to another, the following rules apply:</span><span class="sxs-lookup"><span data-stu-id="9a1e8-109">When you assign one array to another, the following rules apply:</span></span>

- <span data-ttu-id="9a1e8-110">**Equal Ranks.**</span><span class="sxs-lookup"><span data-stu-id="9a1e8-110">**Equal Ranks.**</span></span> <span data-ttu-id="9a1e8-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-111">The rank (number of dimensions) of the destination array must be the same as that of the source array.</span></span>

  <span data-ttu-id="9a1e8-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-112">Provided the ranks of the two arrays are equal, the dimensions do not need to be equal.</span></span> <span data-ttu-id="9a1e8-113">The number of elements in a given dimension can change during assignment.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-113">The number of elements in a given dimension can change during assignment.</span></span>

- <span data-ttu-id="9a1e8-114">**Element Types.**</span><span class="sxs-lookup"><span data-stu-id="9a1e8-114">**Element Types.**</span></span> <span data-ttu-id="9a1e8-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-115">Either both arrays must have *reference type* elements or both arrays must have *value type* elements.</span></span> <span data-ttu-id="9a1e8-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="9a1e8-116">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>

  - <span data-ttu-id="9a1e8-117">If both arrays have value type elements, the element data types must be exactly the same.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-117">If both arrays have value type elements, the element data types must be exactly the same.</span></span> <span data-ttu-id="9a1e8-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-118">The only exception to this is that you can assign an array of `Enum` elements to an array of the base type of that `Enum`.</span></span>

  - <span data-ttu-id="9a1e8-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-119">If both arrays have reference type elements, the source element type must derive from the destination element type.</span></span> <span data-ttu-id="9a1e8-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-120">When this is the case, the two arrays have the same inheritance relationship as their elements.</span></span> <span data-ttu-id="9a1e8-121">This is called *array covariance*.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-121">This is called *array covariance*.</span></span>

<span data-ttu-id="9a1e8-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-122">The compiler reports an error if the above rules are violated, for example if the data types are not compatible or the ranks are unequal.</span></span> <span data-ttu-id="9a1e8-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-123">You can add error handling to your code to make sure that the arrays are compatible before attempting an assignment.</span></span> <span data-ttu-id="9a1e8-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span><span class="sxs-lookup"><span data-stu-id="9a1e8-124">You can also use the [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md) keyword if you want to avoid throwing an exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a1e8-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a1e8-125">See also</span></span>

- [<span data-ttu-id="9a1e8-126">Tablice</span><span class="sxs-lookup"><span data-stu-id="9a1e8-126">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9a1e8-127">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="9a1e8-127">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="9a1e8-128">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9a1e8-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="9a1e8-129">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="9a1e8-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
