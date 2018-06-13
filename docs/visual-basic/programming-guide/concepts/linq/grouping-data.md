---
title: Grupowanie danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: e2732c91dfff65ebb86ef45296ba369c3073a8f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644202"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="72e53-102">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72e53-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="72e53-103">Grupowanie odwołuje się do operacji umieszczania danych w grupach, aby elementów w każdej grupie miały wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="72e53-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="72e53-104">Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="72e53-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="72e53-105">Klucz dla każdej grupy jest znak.</span><span class="sxs-lookup"><span data-stu-id="72e53-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="72e53-106">![Operacje grupowania LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="72e53-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="72e53-107">Metody operator standardowej kwerendy, które grupy elementów danych są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="72e53-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72e53-108">Metody</span><span class="sxs-lookup"><span data-stu-id="72e53-108">Methods</span></span>  
  
|<span data-ttu-id="72e53-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="72e53-109">Method Name</span></span>|<span data-ttu-id="72e53-110">Opis</span><span class="sxs-lookup"><span data-stu-id="72e53-110">Description</span></span>|<span data-ttu-id="72e53-111">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72e53-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="72e53-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="72e53-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="72e53-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="72e53-113">GroupBy</span></span>|<span data-ttu-id="72e53-114">Grupuje elementy, które mają wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="72e53-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="72e53-115">Każda grupa jest reprezentowana przez <xref:System.Linq.IGrouping%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="72e53-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="72e53-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="72e53-116">ToLookup</span></span>|<span data-ttu-id="72e53-117">Wstawia elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) oparte na funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="72e53-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="72e53-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="72e53-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="72e53-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="72e53-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="72e53-120">Poniższy przykład kodu wykorzystuje `Group By` klauzuli na liczby całkowite grupy na liście w zależności od tego, czy są one parzysta lub nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="72e53-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72e53-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72e53-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="72e53-122">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72e53-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="72e53-123">Group By, klauzula</span><span class="sxs-lookup"><span data-stu-id="72e53-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [<span data-ttu-id="72e53-124">Porady: grupowanie plików według rozszerzenia (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72e53-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="72e53-125">Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72e53-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
