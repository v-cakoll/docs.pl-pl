---
title: Kopiowanie zawartości zestawu danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: bee91a6406fd48894580ce6223a5682dbadab380
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757297"
---
# <a name="copying-dataset-contents"></a>Kopiowanie zawartości zestawu danych
Można utworzyć kopię <xref:System.Data.DataSet> tak, aby pracować z danymi bez wpływu na oryginalnych danych lub pracy z podzbiorem danych z **zestawu danych**. Podczas kopiowania **DataSet**, można wykonywać następujące czynności:  
  
-   Utwórz dokładną kopię **zestawu danych**, w tym schematu, danych, informacje o stanie wiersza i wersje wiersza.  
  
-   Utwórz **zestawu danych** zawierający schemat istniejących **zestawu danych**, ale tylko wiersze, które zostały zmodyfikowane. Zwracanie wszystkich wierszy, które zostały zmodyfikowane lub określić **właściwością DataRowState**. Aby uzyskać więcej informacji na temat stany wiersza, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Kopia schematu lub relacyjne struktury **zestawu danych** , bez kopiowania jakiekolwiek wiersze. Wiersze mogą być importowane do istniejącego <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Aby utworzyć dokładną kopię **DataSet** zawierającą zarówno schematu, jak i dane, użyj <xref:System.Data.DataSet.Copy%2A> metody **zestawu danych**. W poniższym przykładzie przedstawiono sposób tworzenia dokładną kopię **zestawu danych**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Aby utworzyć kopię **zestawu danych** zawierającą schemat i tylko dane reprezentujące **Added**, **zmodyfikowane**, lub **usunięte** wierszy, użyj <xref:System.Data.DataSet.GetChanges%2A> metody **zestawu danych**. Można również użyć **GetChanges** do zwrócenia tylko wiersze ze stanem określony wiersz przez przekazanie **właściwością DataRowState** wartości podczas wywoływania metody **GetChanges**. Poniższy przykład kodu pokazuje sposób przekazywania **właściwością DataRowState** podczas wywoływania metody **GetChanges**.  
  
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
  
 Aby utworzyć kopię **DataSet** zawiera tylko schemat, należy użyć <xref:System.Data.DataSet.Clone%2A> metody **zestawu danych**. Możesz także dodać istniejące wiersze na sklonowanym **DataSet** przy użyciu **ImportRow** metody **DataTable**. **ImportRow** dodaje dane, wiersz stanu oraz informacje o wersji wierszy do określonej tabeli. Wartości w kolumnach są dodawane, tylko jeśli nazwa kolumny odpowiada i dane typ jest zgodny.  
  
 Poniższy przykład kodu tworzy Sklonowanie **zestawu danych** , a następnie dodaje wiersze z oryginalnego **DataSet** do **klientów** w tabeli **zestawu danych**  klonowania dla klientów, którym **Ustawieniem CountryRegion** kolumna ma wartość "Niemcy".  
  
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
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
