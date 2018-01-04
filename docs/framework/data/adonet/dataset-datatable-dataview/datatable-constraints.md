---
title: Ograniczenia elementu DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3767467024d6c0d0dfbf1be8829d77ba3f7fa439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-constraints"></a>Ograniczenia elementu DataTable
Ograniczenia umożliwiają wymuszenie zastosowania ograniczenia dotyczące danych w <xref:System.Data.DataTable>, aby zapewnić integralność danych. Ograniczenie jest automatyczne reguły, kolumny lub powiązane kolumny określa sposób postępowania przypadku jakiś sposób zmiany wartości wiersza. Wymuszone są ograniczenia podczas `System.Data.DataSet.EnforceConstraints` właściwość <xref:System.Data.DataSet> jest **true**. Na przykład kodu, który pokazuje, jak ustawić `EnforceConstraints` właściwości, zobacz <xref:System.Data.DataSet.EnforceConstraints%2A> temat referencyjny.  
  
 Istnieją dwa rodzaje ograniczeń ADO.NET: <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint>. Domyślnie oba ograniczenia są tworzone automatycznie podczas tworzenia relacji między co najmniej dwie tabele, dodając <xref:System.Data.DataRelation> do **zestawu danych**. Jednak wyłączyć to zachowanie, określając **createConstraints** = **false** podczas tworzenia powiązania.  
  
## <a name="foreignkeyconstraint"></a>Element ForeignKeyConstraint  
 A **ForeignKeyConstraint** wymusza stosowanie reguł dotyczących sposobu propagacji aktualizacji i usunięć w tabelach pokrewnych. Na przykład, jeśli wartość w wierszu jedna tabela jest zaktualizowane lub usunięty i tej samej wartości jest również używana w jednej lub więcej powiązanych tabel **ForeignKeyConstraint** Określa, co się stanie w tabelach pokrewnych.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> i <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> właściwości **ForeignKeyConstraint** definiowania akcji do wykonania, kiedy użytkownik próbuje usunąć lub zaktualizować wiersza powiązanej tabeli. W poniższej tabeli opisano różne ustawienia dostępne dla **DeleteRule** i **elementu UpdateRule** właściwości **ForeignKeyConstraint**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Kaskadowo**|Usuń lub zaktualizuj powiązane wiersze.|  
|**SetNull**|Ustaw wartości w powiązane wiersze do **DBNull**.|  
|**SetDefault**|Ustaw wartości w powiązane wiersze do wartości domyślnej.|  
|**Brak**|Podejmij żadnej akcji na powiązane wiersze. Domyślnie włączone.|  
  
 A **ForeignKeyConstraint** można ograniczyć, również są propagowane, zmiany powiązane kolumny. W zależności od właściwości ustawione dla **ForeignKeyConstraint** kolumny, jeśli **EnforceConstraints** właściwość **DataSet** jest **true**, wykonywania pewnych operacji na wierszu nadrzędny spowoduje powstanie Wystąpił wyjątek. Na przykład jeśli **DeleteRule** właściwość **ForeignKeyConstraint** jest **Brak**, nie można usunąć wiersza nadrzędnego, jeśli ma ona żadnych wierszy podrzędnych.  
  
 Można utworzyć ograniczenia klucza obcego między jednej kolumny lub tablica kolumn za pomocą **ForeignKeyConstraint** konstruktora. Przekaż powstałe w ten sposób **ForeignKeyConstraint** do obiektu **Dodaj** metody tabeli **ograniczenia** właściwość, która jest **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń **Dodaj** metody **ConstraintCollection** utworzyć **ForeignKeyConstraint**.  
  
 Podczas tworzenia **ForeignKeyConstraint**, można przekazać **DeleteRule** i **elementu UpdateRule** wartości do konstruktora jako argumenty, lub można ustawić je jako właściwości jako następujący przykład (gdzie **DeleteRule** ma wartość **Brak**).  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 Zmiany wiersze mogą być akceptowane przy użyciu **AcceptChanges** metody lub używając anulowane **RejectChanges** metody **DataSet**, **DataTable**, lub **DataRow**. Gdy **DataSet** zawiera **ForeignKeyConstraints**, wywoływanie **AcceptChanges** lub **RejectChanges** metody wymusza  **AcceptRejectRule**. **AcceptRejectRule** właściwość **ForeignKeyConstraint** Określa, jakie działania zostaną wykonane w elemencie podrzędnym wiersze, kiedy **AcceptChanges** lub  **RejectChanges** jest wywoływana w wierszu nadrzędnej.  
  
 W poniższej tabeli wymieniono dostępne ustawienia **AcceptRejectRule**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Kaskadowo**|Zaakceptuj lub Odrzuć zmiany do wierszy podrzędnych.|  
|**Brak**|Nie zająć się wierszy podrzędnych. Domyślnie włączone.|  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.ForeignKeyConstraint>, ustawia niektóre jego właściwości, w tym <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>i dodaje go do <xref:System.Data.ConstraintCollection> z <xref:System.Data.DataTable> obiektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint** obiektu, który można przypisać do jednej kolumny lub tablica kolumn w **DataTable**, zapewnia, że wszystkie dane w określonej kolumnie lub kolumnach są unikatowe w każdym wierszu. Ograniczenia unique dla kolumny lub tablica kolumn można utworzyć przy użyciu **UniqueConstraint** konstruktora. Przekaż powstałe w ten sposób **UniqueConstraint** do obiektu **Dodaj** metody tabeli **ograniczenia** właściwość, która jest **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń **Dodaj** metody **ConstraintCollection** utworzyć **UniqueConstraint**. Podczas tworzenia **UniqueConstraint** dla kolumny lub kolumn, można opcjonalnie określić kolumny lub kolumn, czy klucz podstawowy.  
  
 Można również utworzyć ograniczenia unique dla kolumny, ustawiając **Unique** właściwości kolumny do **true**. Możesz też ustawienie **Unique** właściwości pojedynczej kolumny do **false** usuwa unikatowego ograniczenia, które mogą istnieć. Definiowanie kolumny lub kolumn jako klucz podstawowy dla tabeli automatycznie spowoduje utworzenie unikatowego ograniczenia dla określonej kolumny lub kolumn. Usunięcie kolumny z **PrimaryKey** właściwość **DataTable**, **UniqueConstraint** zostanie usunięta.  
  
 Poniższy przykład tworzy **UniqueConstraint** 2 kolumny **DataTable**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
