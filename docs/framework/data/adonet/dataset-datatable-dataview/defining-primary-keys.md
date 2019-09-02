---
title: Definiowanie kluczy podstawowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: dbfd8a8b207c0da9403ac1f8ab36557c4abe383b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204911"
---
# <a name="defining-primary-keys"></a><span data-ttu-id="644a4-102">Definiowanie kluczy podstawowych</span><span class="sxs-lookup"><span data-stu-id="644a4-102">Defining Primary Keys</span></span>
<span data-ttu-id="644a4-103">Tabela bazy danych ma zwykle kolumnę lub grupę kolumn, która jednoznacznie identyfikuje każdy wiersz w tabeli.</span><span class="sxs-lookup"><span data-stu-id="644a4-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="644a4-104">Ta kolumna identyfikująca lub grupa kolumn jest nazywana kluczem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="644a4-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="644a4-105">Po zidentyfikowaniu pojedynczej <xref:System.Data.DataColumn> <xref:System.Data.DataTable.PrimaryKey%2A> jako dla elementu <xref:System.Data.DataTable>, w tabeli automatycznie ustawia <xref:System.Data.DataColumn.AllowDBNull%2A> właściwość kolumny na **false** i <xref:System.Data.DataColumn.Unique%2A> właściwość na **true**.</span><span class="sxs-lookup"><span data-stu-id="644a4-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="644a4-106">W przypadku kluczy podstawowych z wieloma kolumnami tylko właściwość **AllowDBNull** jest automatycznie ustawiana na **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="644a4-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="644a4-107">Właściwość <xref:System.Data.DataTable> PrimaryKey elementu otrzymuje jako wartość tablicę co najmniej jednego obiektu **DataColumn** , jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="644a4-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="644a4-108">Pierwszy przykład definiuje pojedynczą kolumnę jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="644a4-108">The first example defines a single column as the primary key.</span></span>  
  
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
  
 <span data-ttu-id="644a4-109">W poniższym przykładzie zdefiniowano dwie kolumny jako klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="644a4-109">The following example defines two columns as a primary key.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="644a4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="644a4-110">See also</span></span>

- <xref:System.Data.DataTable>
- [<span data-ttu-id="644a4-111">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="644a4-111">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="644a4-112">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="644a4-112">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="644a4-113">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="644a4-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
