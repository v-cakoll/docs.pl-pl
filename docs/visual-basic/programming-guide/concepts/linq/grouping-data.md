---
title: Grupowanie danych
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 8996eee748489c596bc5adc32f53b6b39dbfc6ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398386"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="6285f-102">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6285f-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="6285f-103">Grupowanie odwołuje się do operacji umieszczania danych w grupach, tak aby elementy w każdej grupie miały wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="6285f-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="6285f-104">Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="6285f-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="6285f-105">Klucz dla każdej grupy jest znakiem.</span><span class="sxs-lookup"><span data-stu-id="6285f-105">The key for each group is the character.</span></span>  
  
 ![Diagram przedstawiający operację grupowania LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="6285f-107">Standardowe metody operatorów zapytań, które grupują elementy danych, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6285f-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6285f-108">Metody</span><span class="sxs-lookup"><span data-stu-id="6285f-108">Methods</span></span>  
  
|<span data-ttu-id="6285f-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="6285f-109">Method Name</span></span>|<span data-ttu-id="6285f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6285f-110">Description</span></span>|<span data-ttu-id="6285f-111">Składnia wyrażenia zapytania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6285f-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6285f-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="6285f-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="6285f-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="6285f-113">GroupBy</span></span>|<span data-ttu-id="6285f-114">Grupuje elementy, które mają wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="6285f-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="6285f-115">Każda grupa jest reprezentowana przez <xref:System.Linq.IGrouping%602> obiekt.</span><span class="sxs-lookup"><span data-stu-id="6285f-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6285f-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="6285f-116">ToLookup</span></span>|<span data-ttu-id="6285f-117">Wstawia elementy do <xref:System.Linq.Lookup%602> (słownik jeden-do-wielu) w oparciu o funkcję selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="6285f-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="6285f-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6285f-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="6285f-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="6285f-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="6285f-120">Poniższy przykład kodu używa `Group By` klauzuli do grupowania liczb całkowitych na liście zgodnie z tym, czy są one parzyste czy nieparzyste.</span><span class="sxs-lookup"><span data-stu-id="6285f-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6285f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6285f-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6285f-122">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6285f-122">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="6285f-123">Group By, klauzula</span><span class="sxs-lookup"><span data-stu-id="6285f-123">Group By Clause</span></span>](../../../language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="6285f-124">Instrukcje: grupowanie plików według rozszerzenia (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6285f-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="6285f-125">Instrukcje: dzielenie pliku na wiele plików przy użyciu grup (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6285f-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
