---
title: Grupowanie danych
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 9a4011b77f91ff241d23f7aeca95925a1e170483
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266823"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="3b1f3-102">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b1f3-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="3b1f3-103">Grupowanie odnosi się do operacji umieszczania danych w grupach, tak aby elementy w każdej grupie współużytkują wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="3b1f3-104">Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="3b1f3-105">Kluczem dla każdej grupy jest znak.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-105">The key for each group is the character.</span></span>  
  
 ![Diagram, który pokazuje operację grupowania LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="3b1f3-107">Standardowe metody operatora kwerendy, które grupują elementy danych są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b1f3-108">Metody</span><span class="sxs-lookup"><span data-stu-id="3b1f3-108">Methods</span></span>  
  
|<span data-ttu-id="3b1f3-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="3b1f3-109">Method Name</span></span>|<span data-ttu-id="3b1f3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3b1f3-110">Description</span></span>|<span data-ttu-id="3b1f3-111">Składnia wyrażenia kwerendy wizualnej podstawowej</span><span class="sxs-lookup"><span data-stu-id="3b1f3-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3b1f3-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="3b1f3-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3b1f3-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="3b1f3-113">GroupBy</span></span>|<span data-ttu-id="3b1f3-114">Grupuje elementy, które mają wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="3b1f3-115">Każda grupa jest reprezentowana przez obiekt. <xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="3b1f3-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3b1f3-116">Tolookup</span><span class="sxs-lookup"><span data-stu-id="3b1f3-116">ToLookup</span></span>|<span data-ttu-id="3b1f3-117">Wstawia elementy <xref:System.Linq.Lookup%602> do (słownika jeden do wielu) na podstawie funkcji selektora klawiszy.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="3b1f3-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="3b1f3-119">Przykład składni wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="3b1f3-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="3b1f3-120">Poniższy przykład kodu `Group By` używa klauzuli do grupowania danych całkowitych na liście w zależności od tego, czy są one równe czy nieparzyste.</span><span class="sxs-lookup"><span data-stu-id="3b1f3-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b1f3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b1f3-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3b1f3-122">Omówienie standardowych operatorów zapytań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b1f3-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="3b1f3-123">Group By, klauzula</span><span class="sxs-lookup"><span data-stu-id="3b1f3-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="3b1f3-124">Jak: Grupowanie plików według rozszerzenia (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b1f3-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="3b1f3-125">Jak: Dzielenie pliku na wiele plików przy użyciu grup (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b1f3-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
