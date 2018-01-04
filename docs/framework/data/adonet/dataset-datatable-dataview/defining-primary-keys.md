---
title: Definiowanie kluczy podstawowych
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
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dffced0e3d8cd28699d41ea6bb286e3d59f16bb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="defining-primary-keys"></a>Definiowanie kluczy podstawowych
Tabela bazy danych ma często kolumny lub grupy kolumn, który unikatowo identyfikuje każdego wiersza w tabeli. Identyfikowania tej kolumny lub grupy kolumn nosi nazwę klucza podstawowego.  
  
 Po zidentyfikowaniu pojedynczy <xref:System.Data.DataColumn> jako <xref:System.Data.DataTable.PrimaryKey%2A> dla <xref:System.Data.DataTable>, tabeli automatycznie ustawia <xref:System.Data.DataColumn.AllowDBNull%2A> właściwości kolumny do **false** i <xref:System.Data.DataColumn.Unique%2A> właściwości  **wartość true,**. Wiele kolumn kluczy podstawowych, tylko **AllowDBNull** jest automatycznie ustawiana właściwość **false**.  
  
 **PrimaryKey** właściwość <xref:System.Data.DataTable> odbiera jako wartość tablicę co najmniej jeden **DataColumn** obiekty, jak pokazano w poniższych przykładach. Pierwszym przykładzie definiuje pojedynczą kolumnę jako klucz podstawowy.  
  
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
  
 W poniższym przykładzie zdefiniowano dwie kolumny jako klucz podstawowy.  
  
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
 <xref:System.Data.DataTable>  
 [Definicja schematu elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
