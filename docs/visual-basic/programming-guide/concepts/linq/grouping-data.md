---
title: Grupowanie danych
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 6e84ccfbd6a2193ac5ab368d7526da2de29a3c47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353384"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="dd5aa-102">Grouping Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5aa-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="dd5aa-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="dd5aa-104">The following illustration shows the results of grouping a sequence of characters.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="dd5aa-105">The key for each group is the character.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-105">The key for each group is the character.</span></span>  
  
 ![Diagram that shows a LINQ Grouping operation.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="dd5aa-107">The standard query operator methods that group data elements are listed in the following section.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd5aa-108">Metody</span><span class="sxs-lookup"><span data-stu-id="dd5aa-108">Methods</span></span>  
  
|<span data-ttu-id="dd5aa-109">Method Name</span><span class="sxs-lookup"><span data-stu-id="dd5aa-109">Method Name</span></span>|<span data-ttu-id="dd5aa-110">Opis</span><span class="sxs-lookup"><span data-stu-id="dd5aa-110">Description</span></span>|<span data-ttu-id="dd5aa-111">Visual Basic Query Expression Syntax</span><span class="sxs-lookup"><span data-stu-id="dd5aa-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="dd5aa-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="dd5aa-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="dd5aa-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="dd5aa-113">GroupBy</span></span>|<span data-ttu-id="dd5aa-114">Groups elements that share a common attribute.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="dd5aa-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="dd5aa-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="dd5aa-116">ToLookup</span></span>|<span data-ttu-id="dd5aa-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="dd5aa-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="dd5aa-119">Query Expression Syntax Example</span><span class="sxs-lookup"><span data-stu-id="dd5aa-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="dd5aa-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span><span class="sxs-lookup"><span data-stu-id="dd5aa-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd5aa-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd5aa-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="dd5aa-122">Standard Query Operators Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5aa-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="dd5aa-123">Group By, klauzula</span><span class="sxs-lookup"><span data-stu-id="dd5aa-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="dd5aa-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5aa-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="dd5aa-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5aa-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
