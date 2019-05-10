---
title: 'Instrukcje: Sortowanie tablicy w języku Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 3c701d1b65d31315ba931cca729e465ba7d766b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620877"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="961e9-102">Instrukcje: Sortowanie tablicy w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="961e9-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="961e9-103">Ten przykład deklaruje tablicę `String` obiektów o nazwie `zooAnimals`, wypełnia ją i następnie sortuje ją alfabetycznie.</span><span class="sxs-lookup"><span data-stu-id="961e9-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="961e9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="961e9-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="961e9-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="961e9-105">Compiling the Code</span></span>  
 <span data-ttu-id="961e9-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="961e9-106">This example requires:</span></span>  
  
- <span data-ttu-id="961e9-107">Dostęp do biblioteki Mscorlib.dll i <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="961e9-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="961e9-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="961e9-108">Robust Programming</span></span>  
 <span data-ttu-id="961e9-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="961e9-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="961e9-110">Tablica jest pusta (<xref:System.ArgumentNullException> klasy)</span><span class="sxs-lookup"><span data-stu-id="961e9-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
- <span data-ttu-id="961e9-111">Tablica ma charakter wielowymiarowy (<xref:System.RankException> klasy)</span><span class="sxs-lookup"><span data-stu-id="961e9-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
- <span data-ttu-id="961e9-112">Nie należy implementować jeden lub więcej elementów tablicy <xref:System.IComparable> interfejsu (<xref:System.InvalidOperationException> klasy)</span><span class="sxs-lookup"><span data-stu-id="961e9-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="961e9-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="961e9-113">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [<span data-ttu-id="961e9-114">Tablice</span><span class="sxs-lookup"><span data-stu-id="961e9-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="961e9-115">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="961e9-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [<span data-ttu-id="961e9-116">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="961e9-116">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="961e9-117">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="961e9-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
