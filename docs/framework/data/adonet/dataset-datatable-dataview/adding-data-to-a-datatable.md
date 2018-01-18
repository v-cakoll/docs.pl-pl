---
title: Dodawanie danych do elementu DataTable
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
ms.assetid: d6aa8474-7bde-48f7-949d-20dc38a1625b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 29ba4a62b2c896e4ce5fa01929307ee82753495f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="adding-data-to-a-datatable"></a>Dodawanie danych do elementu DataTable
Po utworzeniu <xref:System.Data.DataTable> i zdefiniować jego struktury, przy użyciu kolumn i ograniczeń, można dodać nowe wiersze danych do tabeli. Aby dodać nowy wiersz, należy zadeklarować nowej zmiennej jako typ <xref:System.Data.DataRow>. Nowy **DataRow** obiekt jest zwracany w przypadku wywołania <xref:System.Data.DataTable.NewRow%2A> metody. **DataTable** tworzy następnie **DataRow** obiekt na podstawie struktury tabeli, zgodnie z definicją w <xref:System.Data.DataColumnCollection>.  
  
 Poniższy przykład przedstawia sposób tworzenia nowego wiersza przez wywołanie metody **NewRow** metody.  
  
```vb  
Dim workRow As DataRow = workTable.NewRow()  
```  
  
```csharp  
DataRow workRow = workTable.NewRow();  
```  
  
 Następnie można manipulować, korzystając nowo dodany wiersz za pomocą indeksu lub nazwa kolumny, jak pokazano w poniższym przykładzie.  
  
```vb  
workRow("CustLName") = "Smith"  
workRow(1) = "Smith"  
```  
  
```csharp  
workRow["CustLName"] = "Smith";  
workRow[1] = "Smith";  
```  
  
 Po wstawieniu danych do nowego wiersza **Dodaj** metoda jest używana do dodania do wiersza <xref:System.Data.DataRowCollection>, pokazano w poniższym kodzie.  
  
```vb  
workTable.Rows.Add(workRow)  
```  
  
```csharp  
workTable.Rows.Add(workRow);  
```  
  
 Możesz także wywołać **Dodaj** metodę, aby dodać nowy wiersz przekazując w tablicy wartości wpisanych jako <xref:System.Object>, jak pokazano w poniższym przykładzie.  
  
```vb  
workTable.Rows.Add(new Object() {1, "Smith"})  
```  
  
```csharp  
workTable.Rows.Add(new Object[] {1, "Smith"});  
```  
  
 Przekazanie tablicy wartości wpisanych jako **obiektu**, do **Dodaj** — metoda tworzy nowy wiersz w tabeli i ustawia jej wartości w kolumnach wartości w tablicy object. Należy pamiętać, sekwencyjnie zgodne wartości w tablicy kolumn, na podstawie kolejności, w którym są wyświetlane w tabeli.  
  
 W poniższym przykładzie dodano 10 wierszy do nowo utworzony **klientów** tabeli.  
  
```vb  
Dim workRow As DataRow  
Dim i As Integer  
  
For i = 0 To 9  
  workRow = workTable.NewRow()  
  workRow(0) = i  
  workRow(1) = "CustName" & I.ToString()  
  workTable.Rows.Add(workRow)  
Next  
```  
  
```csharp  
DataRow workRow;  
  
for (int i = 0; i <= 9; i++)   
{  
  workRow = workTable.NewRow();  
  workRow[0] = i;  
  workRow[1] = "CustName" + i.ToString();  
  workTable.Rows.Add(workRow);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
