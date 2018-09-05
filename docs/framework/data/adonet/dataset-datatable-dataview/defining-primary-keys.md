---
title: Definiowanie kluczy podstawowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: aecd16357857dca7393eac879159c916d8cf8ac7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520221"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="53bb7-102">Definiowanie kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="53bb7-102">Defining Primary Keys</span></span>
<span data-ttu-id="53bb7-103">Tabela bazy danych ma często kolumny lub grupy kolumn, który unikatowo identyfikuje każdy wiersz w tabeli.</span><span class="sxs-lookup"><span data-stu-id="53bb7-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="53bb7-104">Ta identyfikujące kolumny lub grupy kolumn nosi nazwę klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="53bb7-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="53bb7-105">Po określeniu jednej <xref:System.Data.DataColumn> jako <xref:System.Data.DataTable.PrimaryKey%2A> dla <xref:System.Data.DataTable>, tabeli automatycznie ustawia <xref:System.Data.DataColumn.AllowDBNull%2A> właściwości kolumny, która ma **false** i <xref:System.Data.DataColumn.Unique%2A> właściwości  **wartość true,**.</span><span class="sxs-lookup"><span data-stu-id="53bb7-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="53bb7-106">Wiele kolumn kluczy podstawowych, tylko **AllowDBNull** zostaje automatycznie ustalona **false**.</span><span class="sxs-lookup"><span data-stu-id="53bb7-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="53bb7-107">**PrimaryKey** właściwość <xref:System.Data.DataTable> odbiera jako jego wartość tablicę co najmniej jeden **DataColumn** obiekty, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="53bb7-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="53bb7-108">Pierwszy przykład definiuje jedną kolumnę jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="53bb7-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="53bb7-109">W poniższym przykładzie zdefiniowano dwie kolumny jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="53bb7-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53bb7-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53bb7-110">See Also</span></span>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="53bb7-111">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="53bb7-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="53bb7-112">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="53bb7-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="53bb7-113">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="53bb7-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
