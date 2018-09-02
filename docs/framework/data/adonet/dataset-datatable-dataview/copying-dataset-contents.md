---
title: Kopiowanie zawartości elementu DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: b85fb6ebf56b110330be121c87d2492b0cfac536
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401947"
---
# <a name="copying-dataset-contents"></a>Kopiowanie zawartości elementu DataSet
Można utworzyć kopię <xref:System.Data.DataSet> tak, aby pracować z danymi bez wywierania wpływu na oryginalnych danych lub pracy przy użyciu podzestawu danych z **zestawu danych**. Podczas kopiowania **DataSet**, możesz:  
  
-   Utworzyć dokładną kopię **zestawu danych**, w tym schematu, danych, informacje o stanie wiersza i wersje wiersza.  
  
-   Tworzenie **DataSet** zawiera schemat z istniejącej **zestawu danych**, ale tylko wiersze, które zostały zmodyfikowane. Zwracanie wszystkich wierszy, które zostały zmodyfikowane lub określić konkretną **właściwością DataRowState**. Aby uzyskać więcej informacji na temat stany wiersza zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Kopia schematu lub relacyjnej struktury **DataSet** tylko, bez kopiowania żadnych wierszy. Wiersze mogą być importowane do istniejącego <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTable.ImportRow%2A>.  
  
 Aby utworzyć dokładną kopię **zestawu danych** zawierającą zarówno schematu, jak i dane, użyj <xref:System.Data.DataSet.Copy%2A> metody **zestawu danych**. Poniższy przykład kodu pokazuje, jak utworzyć dokładną kopię **zestawu danych**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 Aby utworzyć kopię **zestawu danych** zawierającego schemat i tylko dane reprezentujące **dodano**, **zmodyfikowane**, lub **usunięte** wierszy, użyj <xref:System.Data.DataSet.GetChanges%2A> metody **zestawu danych**. Można również użyć **GetChanges —** zwracać tylko wiersze ze stanem określony wiersz, przekazując **właściwością DataRowState** wartości podczas wywoływania **GetChanges —**. Poniższy przykład kodu pokazuje sposób przekazywania **właściwością DataRowState** podczas wywoływania **GetChanges —**.  
  
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
  
 Aby utworzyć kopię **DataSet** zawiera tylko schemat, należy użyć <xref:System.Data.DataSet.Clone%2A> metody **zestawu danych**. Można również dodać istniejące wiersze do sklonowanego **DataSet** przy użyciu **ImportRow** metody **DataTable**. **ImportRow** dodaje dane, stan wiersza i informacje o wersji wierszy do określonej tabeli. Wartości w kolumnie są dodawane, tylko jeśli odpowiada nazwa kolumny i dane typ jest zgodny.  
  
 Poniższy przykład kodu tworzy klon **zestawu danych** , a następnie dodaje wiersze z oryginalnego **DataSet** do **klientów** tabelę **zestawu danych**  klonowania dla klientów, którym **tekst** kolumna ma wartość "Germany".  
  
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
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
