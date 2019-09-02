---
title: Ograniczenia elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 68b99e834428261d59c5fb27277b24eb0f6e77e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205049"
---
# <a name="datatable-constraints"></a>Ograniczenia elementu DataTable
Możesz użyć ograniczeń <xref:System.Data.DataTable>, aby wymusić ograniczenia dotyczące danych w, aby zachować integralność danych. Ograniczenie jest automatyczną regułą stosowaną do kolumny lub powiązanych kolumn, która określa przebieg akcji, gdy wartość wiersza jest zmieniana. Ograniczenia są wymuszane, `System.Data.DataSet.EnforceConstraints` gdy właściwość <xref:System.Data.DataSet> ma **wartość true**. Przykładowy kod, który pokazuje, jak ustawić `EnforceConstraints` właściwość, można znaleźć w <xref:System.Data.DataSet.EnforceConstraints%2A> temacie Reference.  
  
 Istnieją dwa rodzaje ograniczeń w ADO.NET: <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint>i. Domyślnie oba ograniczenia są tworzone automatycznie podczas tworzenia relacji między dwiema lub wieloma tabelami przez dodanie <xref:System.Data.DataRelation> do **zestawu danych**. Takie zachowanie można jednak wyłączyć, określając wartość w polu Wyłącz **ograniczenia** = **false** podczas tworzenia relacji.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 **Element ForeignKeyConstraint** wymusza reguły dotyczące sposobu propagacji aktualizacji i usunięć do powiązanych tabel. Na przykład, jeśli wartość w wierszu jednej tabeli jest aktualizowana lub usuwana, a ta sama wartość jest również używana w co najmniej jednej pokrewnych tabelach, **element ForeignKeyConstraint** określa, co się dzieje w tabelach pokrewnych.  
  
 Właściwości <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> i <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> **element ForeignKeyConstraint** definiują akcję do wykonania, gdy użytkownik próbuje usunąć lub zaktualizować wiersz w powiązanej tabeli. W poniższej tabeli opisano różne ustawienia dostępne dla właściwości **DeleteRule** i **UpdateRule** **element ForeignKeyConstraint**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Cascade**|Usuń lub zaktualizuj powiązane wiersze.|  
|**SetNull**|Ustaw wartości w powiązanych wierszach na wartość **DBNull**.|  
|**SetDefault**|Ustaw wartości domyślne w powiązanych wierszach.|  
|**Brak**|Nie podejmuj żadnych działań w odniesieniu do powiązanych wierszy. Domyślnie włączone.|  
  
 **Element ForeignKeyConstraint** może ograniczyć, a także propagowanie zmian w powiązanych kolumnach. W zależności od właściwości ustawionych dla **element ForeignKeyConstraint** kolumny, jeśli właściwość **EnforceConstraints** **zestawu danych** ma **wartość true**, wykonanie niektórych operacji w wierszu nadrzędnym spowoduje wyjątek. Na przykład jeśli właściwość **DeleteRule** elementu **element ForeignKeyConstraint** ma **wartość None**, nie można usunąć wiersza nadrzędnego, jeśli ma on wszystkie wiersze podrzędne.  
  
 Można utworzyć ograniczenie klucza obcego między pojedynczymi kolumnami lub między tablicami kolumn za pomocą konstruktora **element ForeignKeyConstraint** . Przekaż otrzymany obiekt **element ForeignKeyConstraint** do metody **Add** właściwości **ograniczenia** tabeli, która jest elementem **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń metody **Add** obiektu ConstraintCollection , aby utworzyć **element ForeignKeyConstraint**.  
  
 Podczas tworzenia elementu **element ForeignKeyConstraint**można przekazać wartości **DeleteRule** i **UpdateRule** do konstruktora jako argumenty lub ustawić je jako właściwości, tak jak w poniższym przykładzie (gdzie wartość **DeleteRule** jest ustawiona na  **Brak**).  
  
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
 Zmiany w wierszach można zaakceptować przy użyciu **metody AcceptChanges** lub anulowane przy użyciu **metody RejectChanges** **zestawu danych**, **DataTable**lub **DataRow**. Gdy **zestaw danych** zawiera **ForeignKeyConstraints**, wywoływanie metod **AcceptChanges** lub **RejectChanges** wymusza **AcceptRejectRule**. Właściwość **AcceptRejectRule** **element ForeignKeyConstraint** określa, która akcja zostanie podjęta w wierszach podrzędnych w przypadku wywołania metody **AcceptChanges** lub **RejectChanges** w wierszu nadrzędnym.  
  
 W poniższej tabeli wymieniono dostępne ustawienia dla **AcceptRejectRule**.  
  
|Ustawienie reguły|Opis|  
|------------------|-----------------|  
|**Cascade**|Akceptowanie lub odrzucanie zmian w wierszach podrzędnych.|  
|**Brak**|Nie podejmuj żadnych działań w wierszach podrzędnych. Domyślnie włączone.|  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.ForeignKeyConstraint>, ustawia kilka jego właściwości, w <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>tym <xref:System.Data.ConstraintCollection> i dodaje <xref:System.Data.DataTable> go do obiektu.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 Obiekt **UniqueConstraint** , który można przypisać do pojedynczej kolumny lub do tablicy kolumn w **tabeli DataTable**, zapewnia, że wszystkie dane w określonej kolumnie lub kolumnach są unikatowe dla każdego wiersza. Można utworzyć unikatowe ograniczenie dla kolumny lub tablicy kolumn za pomocą konstruktora **UniqueConstraint** . Przekaż otrzymany obiekt **UniqueConstraint** do metody **Add** właściwości **ograniczenia** tabeli, która jest elementem **ConstraintCollection**. Można również przekazać argumenty konstruktora do kilku przeciążeń metody **Add** obiektu ConstraintCollection , aby utworzyć **UniqueConstraint**. Podczas tworzenia **UniqueConstraint** dla kolumny lub kolumn można opcjonalnie określić, czy kolumna lub kolumny są kluczem podstawowym.  
  
 Możesz również utworzyć unikatowe ograniczenie dla kolumny, ustawiając właściwość **Unique** kolumny na **wartość true**. Alternatywnie, ustawienie właściwości **Unique** pojedynczej kolumny na **false** usuwa wszelkie unikatowe ograniczenia, które mogą istnieć. Definiowanie kolumny lub kolumn jako klucza podstawowego dla tabeli spowoduje automatyczne utworzenie unikatowego ograniczenia dla określonej kolumny lub kolumny. Jeśli usuniesz kolumnę z właściwości PrimaryKey **elementu DataTable**, **UniqueConstraint** zostanie usunięta.  
  
 Poniższy przykład tworzy **UniqueConstraint** dla dwóch kolumn tabeli **DataTable**.  
  
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
- [Definicja schematu elementu DataTable](datatable-schema-definition.md)
- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
