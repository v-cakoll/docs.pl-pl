---
title: Kopiowanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: de13e07eb5c19b8beffa724fec4a128c418a4fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151367"
---
# <a name="copying-dataset-contents"></a>Kopiowanie zawartości elementu DataSet
Można utworzyć kopię, <xref:System.Data.DataSet> aby można było pracować z danymi bez wpływu na oryginalne dane lub pracować z podzbiorem danych z **zestawu danych**. Podczas kopiowania **zestawu danych**można:  
  
- Utwórz dokładną kopię **zestawu danych,** w tym schemat, dane, informacje o stanie wiersza i wersje wierszy.  
  
- Utwórz **zestaw danych** zawierający schemat istniejącego zestawu **danych,** ale tylko wiersze, które zostały zmodyfikowane. Można zwrócić wszystkie wiersze, które zostały zmodyfikowane, lub określić określony **DataRowState**. Aby uzyskać więcej informacji o stanach wierszy, zobacz [Stany wierszy i Wersje wierszy](row-states-and-row-versions.md).  
  
- Skopiuj tylko schemat lub strukturę relacyjne **zestawu danych,** nie kopiując żadnych wierszy. Wiersze można zaimportować <xref:System.Data.DataTable> <xref:System.Data.DataTable.ImportRow%2A>do istniejącego za pomocą programu .  
  
 Aby utworzyć dokładną kopię **zestawu danych** zawierającego zarówno schemat, jak i dane, użyj <xref:System.Data.DataSet.Copy%2A> metody zestawu **danych**. W poniższym przykładzie kodu pokazano, jak utworzyć dokładną kopię **zestawu danych**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Aby utworzyć kopię **zestawu danych** zawierającego schemat i tylko dane reprezentujące wiersze **Dodane,** <xref:System.Data.DataSet.GetChanges%2A> **Zmodyfikowane**lub **Usunięte,** należy użyć metody zestawu **danych**. Za pomocą **funkcji GetChanges** można również zwrócić tylko wiersze z określonym stanem wiersza, przekazując wartość **DataRowState** podczas wywoływania **getchanges**. W poniższym przykładzie kodu pokazano, jak przekazać **DataRowState** podczas wywoływania **GetChanges**.  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 Aby utworzyć kopię **zestawu danych** zawierającego tylko schemat, należy użyć <xref:System.Data.DataSet.Clone%2A> metody zestawu **danych**. Można również dodać istniejące wiersze do sklonowanego **zestawu danych** przy użyciu metody **ImportRow** **tabeli DataTable**. **ImportRow** dodaje dane, stan wiersza i informacje o wersji wiersza do określonej tabeli. Wartości kolumn są dodawane tylko wtedy, gdy nazwa kolumny jest zgodna, a typ danych jest zgodny.  
  
 Poniższy przykład kodu tworzy klon **zestawu danych,** a następnie dodaje wiersze z oryginalnego **zestawu danych** do tabeli **Klienci** w pliku **DataSet** klon dla klientów, gdzie kolumna **CountryRegion** ma wartość "Niemcy".  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
