---
title: Kopiowanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: d8a7762c4ec5d650295ca0626180285723549051
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786515"
---
# <a name="copying-dataset-contents"></a>Kopiowanie zawartości elementu DataSet
Można utworzyć kopię <xref:System.Data.DataSet> programu, aby można było korzystać z danych bez wpływania na oryginalne dane, lub pracy z podzbiorem danych z **elementu DataSet**. Podczas kopiowania **zestawu danych**można:  
  
- Utwórz dokładną kopię **zestawu danych**, włącznie z schematem, danymi, informacjami o stanie wiersza i wersjami wierszy.  
  
- Utwórz **zestaw danych** , który zawiera schemat istniejącego **zestawu danych**, ale tylko wiersze, które zostały zmodyfikowane. Można zwrócić wszystkie wiersze, które zostały zmodyfikowane, lub określić określony **DataRowState**. Aby uzyskać więcej informacji na temat stanów wiersza, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).  
  
- Skopiuj schemat lub strukturę relacyjną tylko **zestawu danych** , bez kopiowania żadnych wierszy. Wiersze można importować do istniejącej <xref:System.Data.DataTable> funkcji using. <xref:System.Data.DataTable.ImportRow%2A>  
  
 Aby utworzyć dokładną kopię **zestawu danych** , który zawiera schemat i dane, użyj <xref:System.Data.DataSet.Copy%2A> metody **zestawu danych**. Poniższy przykład kodu pokazuje, jak utworzyć dokładną kopię **zestawu danych**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Aby utworzyć kopię **zestawu danych** , który zawiera schemat i tylko dane reprezentujące **dodane**, **zmodyfikowane**lub **usunięte** wiersze, użyj <xref:System.Data.DataSet.GetChanges%2A> metody **zestawu danych**. Można również użyć metody **Getchangs** , aby zwrócić tylko wiersze z określonym stanem wiersza przez przekazanie wartości **DataRowState** podczas wywoływania metody **GetChanges**. Poniższy przykład kodu pokazuje, jak przekazać **DataRowState** podczas wywoływania metody **GetChanges**.  
  
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
  
 Aby utworzyć kopię **zestawu danych** , który zawiera tylko schemat, użyj <xref:System.Data.DataSet.Clone%2A> metody **zestawu danych**. Istnieje również możliwość dodania istniejących wierszy do sklonowanego **zestawu danych** przy użyciu metody **ImportRow** **tabeli DataTable**. **ImportRow** dodaje informacje o stanie wiersza i wersji wiersza do określonej tabeli. Wartości kolumn są dodawane tylko wtedy, gdy nazwa kolumny jest zgodna i typ danych jest zgodny.  
  
 Poniższy przykład kodu tworzy klon **zestawu danych** , a następnie dodaje wiersze z oryginalnego **zestawu** danych do tabeli **Customers** w sklonowanym **zestawie danych** dla klientów, których kolumna **CountryRegion** ma wartość "Niemcy" ".  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Elementy DataSet, DataTable i DataView](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
