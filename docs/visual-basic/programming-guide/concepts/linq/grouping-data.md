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
# <a name="grouping-data-visual-basic"></a>Grupowanie danych (Visual Basic)
Grupowanie odnosi się do operacji umieszczania danych w grupach, tak aby elementy w każdej grupie współużytkują wspólny atrybut.  
  
 Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków. Kluczem dla każdej grupy jest znak.  
  
 ![Diagram, który pokazuje operację grupowania LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 Standardowe metody operatora kwerendy, które grupują elementy danych są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażenia kwerendy wizualnej podstawowej|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Grupuje elementy, które mają wspólny atrybut. Każda grupa jest reprezentowana przez obiekt. <xref:System.Linq.IGrouping%602>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|Tolookup|Wstawia elementy <xref:System.Linq.Lookup%602> do (słownika jeden do wielu) na podstawie funkcji selektora klawiszy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia kwerendy  
 Poniższy przykład kodu `Group By` używa klauzuli do grupowania danych całkowitych na liście w zależności od tego, czy są one równe czy nieparzyste.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Omówienie standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Group By, klauzula](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [Jak: Grupowanie plików według rozszerzenia (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [Jak: Dzielenie pliku na wiele plików przy użyciu grup (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
