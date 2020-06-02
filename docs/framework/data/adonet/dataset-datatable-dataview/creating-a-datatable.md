---
title: Tworzenie elementu DataTable
description: Dowiedz się, jak utworzyć element DataTable w ADO.NET, który reprezentuje jedną tabelę danych relacyjnych w pamięci, która będzie używana niezależnie lub przez inne obiekty .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 335137eeef02e590539c6d83e46cb39901a1e03f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286924"
---
# <a name="creating-a-datatable"></a><span data-ttu-id="32870-103">Tworzenie elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="32870-103">Creating a DataTable</span></span>
<span data-ttu-id="32870-104">A <xref:System.Data.DataTable> , który reprezentuje jedną tabelę danych relacyjnych w pamięci, może być tworzony i używany niezależnie lub może być używany przez inne obiekty .NET Framework, najczęściej jako element członkowski <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="32870-104">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="32870-105">Obiekt **DataTable** można utworzyć przy użyciu odpowiedniego konstruktora **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="32870-105">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="32870-106">Możesz dodać go do **zestawu danych** za pomocą metody **Add** , aby dodać go do kolekcji **tabel** obiektu **DataTable** .</span><span class="sxs-lookup"><span data-stu-id="32870-106">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="32870-107">Można również tworzyć obiekty **DataTable** w ramach **zestawu danych** przy użyciu metod **Fill** lub **FillSchema** obiektu **DataAdapter** lub ze wstępnie zdefiniowanego lub wywnioskowanego schematu XML przy użyciu metod **ReadXml**, **ReadXmlSchema**lub **InferXmlSchema** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="32870-107">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="32870-108">Należy pamiętać, że po dodaniu **DataTable** jako członka kolekcji **tabel** jednego **zestawu danych**nie można dodać go do kolekcji tabel innego **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="32870-108">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="32870-109">Podczas pierwszej tworzenia **elementu DataTable**nie ma schematu (czyli struktury).</span><span class="sxs-lookup"><span data-stu-id="32870-109">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="32870-110">Aby zdefiniować schemat tabeli, należy utworzyć i dodać <xref:System.Data.DataColumn> obiekty do kolekcji **kolumn** tabeli.</span><span class="sxs-lookup"><span data-stu-id="32870-110">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="32870-111">Istnieje również możliwość zdefiniowania kolumny klucza podstawowego dla tabeli oraz utworzenia i dodania obiektów **ograniczeń** do kolekcji **ograniczenia** tabeli.</span><span class="sxs-lookup"><span data-stu-id="32870-111">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="32870-112">Po zdefiniowaniu schematu dla **elementu DataTable**można dodać wiersze danych do tabeli przez dodanie obiektów **DataRow** do kolekcji **Rows** tabeli.</span><span class="sxs-lookup"><span data-stu-id="32870-112">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="32870-113">Nie trzeba podawać wartości <xref:System.Data.DataTable.TableName%2A> właściwości podczas tworzenia **elementu DataTable**; można określić właściwość w innym czasie lub pozostawić ją pustą.</span><span class="sxs-lookup"><span data-stu-id="32870-113">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="32870-114">Jednak po dodaniu tabeli bez wartości **TableName** do **zestawu danych**w tabeli zostanie nadana przyrostowa domyślna nazwa tabeli*N*, rozpoczynając od "Tabela" dla TABLE0.</span><span class="sxs-lookup"><span data-stu-id="32870-114">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32870-115">Zalecamy uniknięcie konwencji nazewnictwa "Table*N*" w przypadku podania wartości **TableName** , ponieważ wprowadzona nazwa może powodować konflikt z istniejącą domyślną nazwą tabeli w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="32870-115">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="32870-116">Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="32870-116">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="32870-117">Poniższy przykład tworzy wystąpienie obiektu **DataTable** i przypisuje mu nazwę "Customers".</span><span class="sxs-lookup"><span data-stu-id="32870-117">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="32870-118">Poniższy przykład tworzy wystąpienie **elementu DataTable** przez dodanie go do kolekcji **Tables** **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="32870-118">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="32870-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32870-119">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [<span data-ttu-id="32870-120">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="32870-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="32870-121">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="32870-121">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="32870-122">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="32870-122">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="32870-123">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="32870-123">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="32870-124">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="32870-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
