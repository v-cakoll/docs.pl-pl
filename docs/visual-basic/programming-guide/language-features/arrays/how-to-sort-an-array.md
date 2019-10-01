---
title: 'Porady: sortowanie tablicy w Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700973"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="9fb55-102">Instrukcje: sortowanie tablicy w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fb55-102">How to: sort an array in Visual Basic</span></span>

<span data-ttu-id="9fb55-103">W tym artykule przedstawiono przykład sortowania tablicy ciągów w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9fb55-103">This article shows an example of how to sort an array of strings in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="9fb55-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9fb55-104">Example</span></span>

<span data-ttu-id="9fb55-105">Ten przykład deklaruje tablicę obiektów `String` o nazwie `zooAnimals`, wypełnia ją, a następnie sortuje ją alfabetycznie:</span><span class="sxs-lookup"><span data-stu-id="9fb55-105">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically:</span></span>
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a><span data-ttu-id="9fb55-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9fb55-106">Robust programming</span></span>

<span data-ttu-id="9fb55-107">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="9fb55-107">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="9fb55-108">Tablica jest pusta (Klasa <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9fb55-108">Array is empty (<xref:System.ArgumentNullException> class).</span></span>
- <span data-ttu-id="9fb55-109">Tablica jest wielowymiarowa (Klasa <xref:System.RankException>).</span><span class="sxs-lookup"><span data-stu-id="9fb55-109">Array is multidimensional (<xref:System.RankException> class).</span></span>
- <span data-ttu-id="9fb55-110">Co najmniej jeden element tablicy nie implementuje interfejsu <xref:System.IComparable> (Klasa <xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="9fb55-110">One or more elements of the array don't implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fb55-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fb55-111">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9fb55-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="9fb55-112">Arrays</span></span>](index.md)
- [<span data-ttu-id="9fb55-113">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="9fb55-113">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
- [<span data-ttu-id="9fb55-114">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="9fb55-114">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="9fb55-115">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9fb55-115">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
