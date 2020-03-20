---
title: Ograniczenia elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151289"
---
# <a name="datatable-constraints"></a>Ograniczenia elementu DataTable
Ograniczenia można użyć do wymuszenia ograniczeń <xref:System.Data.DataTable>dotyczących danych w programie , aby zachować integralność danych. Ograniczenie jest regułą automatyczną, zastosowaną do kolumny lub powiązanych kolumn, która określa przebieg akcji, gdy wartość wiersza jest w jakiś sposób zmieniona. Ograniczenia są wymuszane, `System.Data.DataSet.EnforceConstraints` <xref:System.Data.DataSet> gdy właściwość jest **true**. Przykład kodu, który pokazuje, `EnforceConstraints` jak ustawić <xref:System.Data.DataSet.EnforceConstraints%2A> właściwość, zobacz temat odwołania.  
  
 Istnieją dwa rodzaje ograniczeń w ADO.NET: <xref:System.Data.ForeignKeyConstraint> i . <xref:System.Data.UniqueConstraint> Domyślnie oba ograniczenia są tworzone automatycznie podczas tworzenia relacji między dwiema <xref:System.Data.DataRelation> lub więcej tabelami przez dodanie a do **zestawu danych**. Jednak można wyłączyć to zachowanie, określając **createConstraints** = **false** podczas tworzenia relacji.  
  
## <a name="foreignkeyconstraint"></a>Foreignkeyconstraint  
 **ForeignKeyConstraint** wymusza reguły dotyczące sposobu aktualizacji i usuwania powiązanych tabel są propagowane. Na przykład jeśli wartość w wierszu jednej tabeli jest aktualizowana lub usunięta, a ta sama wartość jest również używana w jednej lub kilku powiązanych tabelach, **ForeignKeyConstraint** określa, co się dzieje w powiązanych tabelach.  
  
 Właściwości <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> i **ForeignKeyConstraint** zdefiniować akcję, która ma zostać podjęta, gdy użytkownik próbuje usunąć lub zaktualizować wiersz w powiązanej tabeli. W poniższej tabeli opisano różne ustawienia dostępne dla **właściwości DeleteRule** i **UpdateRule** właściwości **ForeignKeyConstraint**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Kaskadowo**|Usuwanie lub aktualizowanie powiązanych wierszy.|  
|**Setnull**|Ustaw wartości w powiązanych wierszach na **DBNull**.|  
|**SetDefault (Domyślnie)**|Ustaw wartości w powiązanych wierszach na wartość domyślną.|  
|**Brak**|Nie podejmuj żadnych działań w powiązanych wierszach. Domyślnie włączone.|  
  
 A **ForeignKeyConstraint** można ograniczyć, a także propagować zmiany w powiązanych kolumn. W zależności od właściwości ustawionych dla **ForeignKeyConstraint** kolumny, jeśli **EnforceConstraints** właściwość **DataSet** jest **true**, wykonywanie niektórych operacji w wierszu nadrzędnym spowoduje wyjątek. Na przykład jeśli **DeleteRule** właściwość **ForeignKeyConstraint** jest **Brak**, wiersz nadrzędny nie można usunąć, jeśli ma żadnych wierszy podrzędnych.  
  
 Ograniczenie klucza obcego między pojedynczymi kolumnami lub między tablicą kolumn można utworzyć przy użyciu konstruktora **ForeignKeyConstraint.** Przekaż wynikowy **Obiekt ForeignKeyConstraint** do **Add** metody tabeli **Constraints** właściwości, która jest **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń **Add** metody **ConstraintCollection,** aby utworzyć **ForeignKeyConstraint**.  
  
 Podczas tworzenia **ForeignKeyConstraint**, można przekazać **DeleteRule** i **UpdateRule** wartości do konstruktora jako argumenty lub można ustawić je jako właściwości, jak w poniższym przykładzie (gdzie **Wartość DeleteRule** jest ustawiona na **Brak**).  
  
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
  
### <a name="acceptrejectrule"></a>Acceptrejectrule  
 Zmiany w wierszach można zaakceptować za pomocą **acceptChanges** metody lub anulować przy użyciu **RejectChanges** metody **DataSet**, **DataTable**lub **DataRow**. Gdy **zestaw danych** zawiera **foreignkeyconstraints**, wywoływanie **AcceptChanges** lub **RejectChanges** metody wymusza **AcceptRejectRule**. **AcceptRejectRule** właściwość **ForeignKeyConstraint** określa, które działania zostaną podjęte w wierszach podrzędnych, gdy **AcceptChanges** lub **RejectChanges** jest wywoływana w wierszu nadrzędnym.  
  
 W poniższej tabeli wymieniono dostępne ustawienia **reguły AcceptRejectRule**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Kaskadowo**|Akceptowanie lub odrzucanie zmian w wierszach podrzędnych.|  
|**Brak**|Nie podejmuj żadnych działań w wierszach podrzędnych. Domyślnie włączone.|  
  
### <a name="example"></a>Przykład  
 Poniższy przykład <xref:System.Data.ForeignKeyConstraint>tworzy , ustawia kilka jego <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>właściwości, w tym <xref:System.Data.ConstraintCollection> , <xref:System.Data.DataTable> i dodaje go do obiektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>Uniqueconstraint  
 **UniqueConstraint** obiektu, który może być przypisany do jednej kolumny lub do tablicy kolumn w **DataTable**, zapewnia, że wszystkie dane w określonej kolumnie lub kolumnach jest unikatowy dla każdego wiersza. Unikatowe ograniczenie dla kolumny lub tablicy kolumn można utworzyć za pomocą konstruktora **UniqueConstraint.** Przekaż wynikowy **UniqueConstraint** obiektu do **Add** metody tabeli **Constraints** właściwości, która jest **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń **Add** metody **ConstraintCollection,** aby utworzyć **UniqueConstraint**. Podczas tworzenia **UniqueConstraint** dla kolumny lub kolumn, można opcjonalnie określić, czy kolumna lub kolumny są kluczem podstawowym.  
  
 Można również utworzyć unikatowe ograniczenie dla kolumny, ustawiając **właściwość Unikatowa** kolumny na **true**. Alternatywnie ustawienie **Unique** właściwość pojedynczej kolumny na **false** usuwa wszelkie unikatowe ograniczenie, które mogą istnieć. Zdefiniowanie kolumny lub kolumn jako klucza podstawowego tabeli spowoduje automatyczne utworzenie unikatowego ograniczenia dla określonej kolumny lub kolumn. Jeśli usuniesz kolumnę z **Właściwości PrimaryKey** **datatable,** **UniqueConstraint** zostanie usunięty.  
  
 Poniższy przykład tworzy **UniqueConstraint** dla dwóch kolumn **DataTable**.  
  
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

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [Definicja schematu elementu DataTable](datatable-schema-definition.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
