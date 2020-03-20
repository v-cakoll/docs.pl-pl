---
title: Definiowanie kluczy podstawowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 159b23eb4ef5ca38ebce6e488080d315ec3be081
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151185"
---
# <a name="defining-primary-keys"></a>Definiowanie kluczy podstawowych
Tabela bazy danych często ma kolumnę lub grupę kolumn, która jednoznacznie identyfikuje każdy wiersz w tabeli. Ta kolumna identyfikującya lub grupa kolumn jest nazywana kluczem podstawowym.  
  
 Po zidentyfikowaniu <xref:System.Data.DataColumn> pojedynczego <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataTable>jako fora tabela <xref:System.Data.DataColumn.AllowDBNull%2A> automatycznie ustawia właściwość <xref:System.Data.DataColumn.Unique%2A> kolumny na **false,** a właściwość na **true**. W przypadku wielokolumnowych kluczy podstawowych tylko właściwość **AllowDBNull** jest automatycznie ustawiana na **false**.  
  
 **Właściwość PrimaryKey** <xref:System.Data.DataTable> a odbiera jako swoją wartość tablicę jednego lub więcej obiektów **DataColumn,** jak pokazano w poniższych przykładach. Pierwszy przykład definiuje pojedynczą kolumnę jako klucz podstawowy.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 Poniższy przykład definiuje dwie kolumny jako klucz podstawowy.  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataTable>
- [Definicja schematu elementu DataTable](datatable-schema-definition.md)
- [Elementy DataTable](datatables.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
