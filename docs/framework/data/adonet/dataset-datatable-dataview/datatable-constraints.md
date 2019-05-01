---
title: Ograniczenia elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 254f486fa19d8af30759d9a9fd6642a1a40e82a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034362"
---
# <a name="datatable-constraints"></a>Ograniczenia elementu DataTable
Ograniczenia służy do wymuszania ograniczeń dotyczących danych w <xref:System.Data.DataTable>, w celu zachowania integralności danych. Ograniczenie jest reguła automatycznego stosowane kolumny lub powiązanych kolumn, który określa sposobu działania przypadku jakiś sposób zmiany wartości wiersza. Ograniczenia są wymuszane podczas `System.Data.DataSet.EnforceConstraints` właściwość <xref:System.Data.DataSet> jest **true**. Dla przykładu kodu, który pokazuje, jak ustawić `EnforceConstraints` właściwości, zobacz <xref:System.Data.DataSet.EnforceConstraints%2A> temat referencyjny.  
  
 Istnieją dwa rodzaje ograniczeń ADO.NET: <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint>. Domyślnie oba ograniczenia są tworzone automatycznie podczas tworzenia relacji między co najmniej dwóch tabel, dodając <xref:System.Data.DataRelation> do **zestawu danych**. Jednak to zachowanie można wyłączyć, określając **createConstraints** = **false** podczas tworzenia powiązania.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **ForeignKeyConstraint** wymusza reguły określające, jak są propagowane aktualizacji i usuwania w tabelach pokrewnych. Na przykład, jeśli wartości w wierszu jedna tabela zostanie zaktualizowany lub usunięty i tej samej wartości jest również używane w jednej lub więcej powiązanych tabel **ForeignKeyConstraint** Określa, co się dzieje w tabelach pokrewnych.  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> i <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> właściwości **ForeignKeyConstraint** zdefiniuj akcję do wykonania, kiedy użytkownik próbuje usunąć lub zaktualizować wiersza w powiązanej tabeli. W poniższej tabeli opisano różne ustawienia dostępne dla **DeleteRule** i **elementu UpdateRule** właściwości **ForeignKeyConstraint**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Kaskadowe**|Usuń lub zaktualizuj powiązane wiersze.|  
|**SetNull**|Ustaw wartości w powiązanych wierszy do **DBNull**.|  
|**SetDefault**|Ustaw wartości w powiązane wiersze do wartości domyślnej.|  
|**Brak**|Podejmuj żadnych działań powiązane wiersze. Domyślnie włączone.|  
  
 A **ForeignKeyConstraint** można ograniczyć, również są propagowane, zmiany powiązane kolumny. W zależności od właściwości ustawionej dla **ForeignKeyConstraint** kolumny, jeśli **EnforceConstraints** właściwość **DataSet** jest **true**, wykonywania pewnych operacji na wiersza nadrzędnego wynikiem będzie wyjątek. Na przykład jeśli **DeleteRule** właściwość **ForeignKeyConstraint** jest **Brak**, nie można usunąć wiersza nadrzędnego, jeśli ma on wszystkie wiersze podrzędne.  
  
 Można utworzyć ograniczenia klucza obcego między pojedynczej kolumny lub tablica kolumn przy użyciu **ForeignKeyConstraint** konstruktora. Przekaż wynikowy **ForeignKeyConstraint** obiekt **Dodaj** tabelę metod **ograniczenia** właściwość, która jest **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń **Dodaj** metody **ConstraintCollection** utworzyć **ForeignKeyConstraint**.  
  
 Podczas tworzenia **ForeignKeyConstraint**, można przekazać **DeleteRule** i **elementu UpdateRule** wartości do konstruktora jako argumenty lub można je ustawić jako właściwości, jak w programie następujący przykład (gdzie **DeleteRule** wartość jest równa **Brak**).  
  
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
 Można zaakceptować zmiany do wierszy przy użyciu **AcceptChanges** metody lub anulowano przy użyciu **RejectChanges** metody **zestawu danych**, **DataTable**, lub **DataRow**. Gdy **DataSet** zawiera **ForeignKeyConstraints**, powinny być przekazywane wywołującemu **AcceptChanges** lub **RejectChanges** metody wymusza  **AcceptRejectRule**. **AcceptRejectRule** właściwość **ForeignKeyConstraint** Określa akcję, która zostaną wykonane w elemencie podrzędnym wiersze, gdy **AcceptChanges** lub  **RejectChanges** jest wywoływana w wiersza nadrzędnego.  
  
 W poniższej tabeli wymieniono dostępne ustawienia **AcceptRejectRule**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Kaskadowe**|Zaakceptuj lub Odrzuć zmiany wiersze podrzędne.|  
|**Brak**|Podejmować żadnej akcji na wiersze podrzędne. Domyślnie włączone.|  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.ForeignKeyConstraint>, ustawia niektóre jego właściwości, w tym <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>i dodaje go do <xref:System.Data.ConstraintCollection> z <xref:System.Data.DataTable> obiektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint** obiektu, który można przypisać do jednej kolumny lub tablica kolumn w **DataTable**, zapewnia, że wszystkie dane w określonej kolumnie lub kolumnach jest unikatowa na wiersz. Można utworzyć unikatowego ograniczenia, kolumny lub tablicy kolumn przy użyciu **UniqueConstraint** konstruktora. Przekaż wynikowy **UniqueConstraint** obiekt **Dodaj** tabelę metod **ograniczenia** właściwość, która jest **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń **Dodaj** metody **ConstraintCollection** utworzyć **UniqueConstraint**. Podczas tworzenia **UniqueConstraint** dla kolumny lub kolumn, można opcjonalnie określić czy kolumnie lub kolumnach są kluczem podstawowym.  
  
 Możesz również utworzyć unikatowego ograniczenia dla kolumny, ustawiając **unikatowe** właściwości kolumny, która ma **true**. Alternatywnie ustawienie **unikatowe** właściwości jednej kolumnie w celu **false** usuwa unikatowego ograniczenia, które mogą istnieć. Definiowanie kolumny lub kolumn jako klucz podstawowy dla tabeli automatycznie utworzy unikatowego ograniczenia dla określonej kolumny lub kolumn. Jeśli usuniesz kolumny z **PrimaryKey** właściwość **DataTable**, **UniqueConstraint** zostanie usunięty.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
