---
title: Definiowanie kluczy podstawowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 21d63aa33e20019f8392b81fb69881296a52cb26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="defining-primary-keys"></a><span data-ttu-id="a860a-102">Definiowanie kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="a860a-102">Defining Primary Keys</span></span>
<span data-ttu-id="a860a-103">Tabela bazy danych ma często kolumny lub grupy kolumn, który unikatowo identyfikuje każdego wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a860a-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="a860a-104">Identyfikowania tej kolumny lub grupy kolumn nosi nazwę klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a860a-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="a860a-105">Po zidentyfikowaniu pojedynczy <xref:System.Data.DataColumn> jako <xref:System.Data.DataTable.PrimaryKey%2A> dla <xref:System.Data.DataTable>, tabeli automatycznie ustawia <xref:System.Data.DataColumn.AllowDBNull%2A> właściwości kolumny do **false** i <xref:System.Data.DataColumn.Unique%2A> właściwości  **wartość true,**.</span><span class="sxs-lookup"><span data-stu-id="a860a-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="a860a-106">Wiele kolumn kluczy podstawowych, tylko **AllowDBNull** jest automatycznie ustawiana właściwość **false**.</span><span class="sxs-lookup"><span data-stu-id="a860a-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="a860a-107">**PrimaryKey** właściwość <xref:System.Data.DataTable> odbiera jako wartość tablicę co najmniej jeden **DataColumn** obiekty, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="a860a-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="a860a-108">Pierwszym przykładzie definiuje pojedynczą kolumnę jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a860a-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="a860a-109">W poniższym przykładzie zdefiniowano dwie kolumny jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a860a-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a860a-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a860a-110">See Also</span></span>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="a860a-111">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="a860a-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="a860a-112">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="a860a-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="a860a-113">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="a860a-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
