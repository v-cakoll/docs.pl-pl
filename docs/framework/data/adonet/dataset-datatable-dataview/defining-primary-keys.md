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
# <a name="defining-primary-keys"></a><span data-ttu-id="b4be3-102">Definiowanie kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="b4be3-102">Defining Primary Keys</span></span>
<span data-ttu-id="b4be3-103">Tabela bazy danych często ma kolumnę lub grupę kolumn, która jednoznacznie identyfikuje każdy wiersz w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b4be3-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="b4be3-104">Ta kolumna identyfikującya lub grupa kolumn jest nazywana kluczem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="b4be3-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="b4be3-105">Po zidentyfikowaniu <xref:System.Data.DataColumn> pojedynczego <xref:System.Data.DataTable.PrimaryKey%2A> <xref:System.Data.DataTable>jako fora tabela <xref:System.Data.DataColumn.AllowDBNull%2A> automatycznie ustawia właściwość <xref:System.Data.DataColumn.Unique%2A> kolumny na **false,** a właściwość na **true**.</span><span class="sxs-lookup"><span data-stu-id="b4be3-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="b4be3-106">W przypadku wielokolumnowych kluczy podstawowych tylko właściwość **AllowDBNull** jest automatycznie ustawiana na **false**.</span><span class="sxs-lookup"><span data-stu-id="b4be3-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="b4be3-107">**Właściwość PrimaryKey** <xref:System.Data.DataTable> a odbiera jako swoją wartość tablicę jednego lub więcej obiektów **DataColumn,** jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="b4be3-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="b4be3-108">Pierwszy przykład definiuje pojedynczą kolumnę jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="b4be3-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="b4be3-109">Poniższy przykład definiuje dwie kolumny jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="b4be3-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b4be3-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4be3-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="b4be3-111">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="b4be3-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="b4be3-112">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="b4be3-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="b4be3-113">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b4be3-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
