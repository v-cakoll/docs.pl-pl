---
title: 'Porady: sortowanie tablicy w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f24c0625058dbd960411d5981b4e98e0e9422b99
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="d962c-102">Porady: sortowanie tablicy w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d962c-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="d962c-103">W tym przykładzie deklaruje tablicę `String` obiektów o nazwie `zooAnimals`, wypełnia go i następnie sortuje ją alfabetycznie.</span><span class="sxs-lookup"><span data-stu-id="d962c-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d962c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d962c-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d962c-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d962c-105">Compiling the Code</span></span>  
 <span data-ttu-id="d962c-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d962c-106">This example requires:</span></span>  
  
-   <span data-ttu-id="d962c-107">Dostęp do pliku Mscorlib.dll i <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d962c-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d962c-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d962c-108">Robust Programming</span></span>  
 <span data-ttu-id="d962c-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d962c-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d962c-110">Tablica jest pusta (<xref:System.ArgumentNullException> klasy)</span><span class="sxs-lookup"><span data-stu-id="d962c-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="d962c-111">Tablica jest wielowymiarowa (<xref:System.RankException> klasy)</span><span class="sxs-lookup"><span data-stu-id="d962c-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="d962c-112">Co najmniej jeden element w tablicy nie implementują <xref:System.IComparable> interfejsu (<xref:System.InvalidOperationException> klasy)</span><span class="sxs-lookup"><span data-stu-id="d962c-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d962c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d962c-113">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d962c-114">Tablice</span><span class="sxs-lookup"><span data-stu-id="d962c-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="d962c-115">Rozwiązywanie problemów związanych z tablicami</span><span class="sxs-lookup"><span data-stu-id="d962c-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="d962c-116">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="d962c-116">Collections</span></span>](../../concepts/collections.md)  
 [<span data-ttu-id="d962c-117">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d962c-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
