---
title: 'How to: Sort An Array'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3fb9af8de0fc86075fdccd64506c855c1c720660
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351853"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="a0e91-102">How to: sort an array in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0e91-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="a0e91-103">This article shows an example of how to sort an array of strings in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a0e91-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="a0e91-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0e91-104">Example</span></span>

<span data-ttu-id="a0e91-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span><span class="sxs-lookup"><span data-stu-id="a0e91-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="a0e91-106">Robust programming</span><span class="sxs-lookup"><span data-stu-id="a0e91-106">Robust programming</span></span>

<span data-ttu-id="a0e91-107">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a0e91-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="a0e91-108">Array is empty (<xref:System.ArgumentNullException> class).</span><span class="sxs-lookup"><span data-stu-id="a0e91-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="a0e91-109">Array is multidimensional (<xref:System.RankException> class).</span><span class="sxs-lookup"><span data-stu-id="a0e91-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="a0e91-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span><span class="sxs-lookup"><span data-stu-id="a0e91-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0e91-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0e91-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a0e91-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="a0e91-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="a0e91-113">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="a0e91-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="a0e91-114">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="a0e91-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="a0e91-115">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a0e91-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
