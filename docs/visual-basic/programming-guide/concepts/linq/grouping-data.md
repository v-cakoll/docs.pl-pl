---
title: Grupowanie danych (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f2e5c4c4713f1056f1eb2243f27e5acf0494542
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="c3d16-102">Grupowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3d16-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="c3d16-103">Grupowanie odwołuje się do operacji umieszczania danych w grupach, aby elementów w każdej grupie miały wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="c3d16-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="c3d16-104">Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="c3d16-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="c3d16-105">Klucz dla każdej grupy jest znak.</span><span class="sxs-lookup"><span data-stu-id="c3d16-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="c3d16-106">![Operacje grupowania LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="c3d16-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="c3d16-107">Metody operator standardowej kwerendy, które grupy elementów danych są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="c3d16-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3d16-108">Metody</span><span class="sxs-lookup"><span data-stu-id="c3d16-108">Methods</span></span>  
  
|<span data-ttu-id="c3d16-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="c3d16-109">Method Name</span></span>|<span data-ttu-id="c3d16-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c3d16-110">Description</span></span>|<span data-ttu-id="c3d16-111">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3d16-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c3d16-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="c3d16-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="c3d16-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="c3d16-113">GroupBy</span></span>|<span data-ttu-id="c3d16-114">Grupuje elementy, które mają wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="c3d16-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="c3d16-115">Każda grupa jest reprezentowana przez <xref:System.Linq.IGrouping%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c3d16-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c3d16-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="c3d16-116">ToLookup</span></span>|<span data-ttu-id="c3d16-117">Wstawia elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) oparte na funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="c3d16-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="c3d16-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="c3d16-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="c3d16-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="c3d16-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="c3d16-120">Poniższy przykład kodu wykorzystuje `Group By` klauzuli na liczby całkowite grupy na liście w zależności od tego, czy są one parzysta lub nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="c3d16-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3d16-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3d16-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="c3d16-122">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3d16-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="c3d16-123">Group By — klauzula</span><span class="sxs-lookup"><span data-stu-id="c3d16-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [<span data-ttu-id="c3d16-124">Porady: grupowanie plików według rozszerzenia (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3d16-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="c3d16-125">Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3d16-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
