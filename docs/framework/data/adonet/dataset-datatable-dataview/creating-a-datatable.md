---
title: Tworzenie DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: a374c7c6e7dfc04cd8828208d6762f8d8665072e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-datatable"></a><span data-ttu-id="1ac29-102">Tworzenie DataTable</span><span class="sxs-lookup"><span data-stu-id="1ac29-102">Creating a DataTable</span></span>
<span data-ttu-id="1ac29-103">A <xref:System.Data.DataTable>, który reprezentuje jednej tabeli w pamięci relacyjnej bazie danych, może być tworzone i używane są niezależnie lub może być używany przez inne obiekty .NET Framework najczęściej jako element członkowski <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1ac29-103">A <xref:System.Data.DataTable>, which represents one table of in-memory relational data, can be created and used independently, or can be used by other .NET Framework objects, most commonly as a member of a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="1ac29-104">Można utworzyć **DataTable** obiektu przy użyciu odpowiednich **DataTable** konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1ac29-104">You can create a **DataTable** object by using the appropriate **DataTable** constructor.</span></span> <span data-ttu-id="1ac29-105">Można dodać go do **DataSet** za pomocą **Dodaj** metodę, aby dodać go do **DataTable** obiektu **tabel** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1ac29-105">You can add it to the **DataSet** by using the **Add** method to add it to the **DataTable** object's **Tables** collection.</span></span>  
  
 <span data-ttu-id="1ac29-106">Można również utworzyć **DataTable** obiektów w ramach **DataSet** za pomocą **wypełnienia** lub **FillSchema** metody  **Element DataAdapter** obiekt, lub wstępnie zdefiniowanych lub wnioskowany XML schematu używającego **ReadXml**, **ReadXmlSchema**, lub **InferXmlSchema** metody **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="1ac29-106">You can also create **DataTable** objects within a **DataSet** by using the **Fill** or **FillSchema** methods of the **DataAdapter** object, or from a predefined or inferred XML schema using the **ReadXml**, **ReadXmlSchema**, or **InferXmlSchema** methods of the **DataSet**.</span></span> <span data-ttu-id="1ac29-107">Należy pamiętać, że po dodaniu **DataTable** jako element członkowski **tabel** kolekcji jednego **DataSet**, nie można dodać go do kolekcji tabel innych **Zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="1ac29-107">Note that after you have added a **DataTable** as a member of the **Tables** collection of one **DataSet**, you cannot add it to the collection of tables of any other **DataSet**.</span></span>  
  
 <span data-ttu-id="1ac29-108">Po utworzeniu **DataTable**, nie ma schematu (struktury).</span><span class="sxs-lookup"><span data-stu-id="1ac29-108">When you first create a **DataTable**, it does not have a schema (that is, a structure).</span></span> <span data-ttu-id="1ac29-109">Aby zdefiniować schemat tabeli, należy utworzyć i dodać <xref:System.Data.DataColumn> obiekty do **kolumn** kolekcji tabeli.</span><span class="sxs-lookup"><span data-stu-id="1ac29-109">To define the schema of the table, you must create and add <xref:System.Data.DataColumn> objects to the **Columns** collection of the table.</span></span> <span data-ttu-id="1ac29-110">Można również zdefiniować kolumna klucza podstawowego dla tabeli i Utwórz i Dodaj **ograniczenia** obiekty do **ograniczenia** kolekcji tabeli.</span><span class="sxs-lookup"><span data-stu-id="1ac29-110">You can also define a primary key column for the table, and create and add **Constraint** objects to the **Constraints** collection of the table.</span></span> <span data-ttu-id="1ac29-111">Po zdefiniowaniu schematu **DataTable**, można dodać wiersze danych do tabeli przez dodanie **DataRow** obiekty do **wierszy** kolekcji tabeli.</span><span class="sxs-lookup"><span data-stu-id="1ac29-111">After you have defined the schema for a **DataTable**, you can add rows of data to the table by adding **DataRow** objects to the **Rows** collection of the table.</span></span>  
  
 <span data-ttu-id="1ac29-112">Nie musisz podać wartość <xref:System.Data.DataTable.TableName%2A> właściwości po utworzeniu **DataTable**; można określić właściwości w późniejszym terminie, lub pozostawić pusty.</span><span class="sxs-lookup"><span data-stu-id="1ac29-112">You are not required to supply a value for the <xref:System.Data.DataTable.TableName%2A> property when you create a **DataTable**; you can specify the property at another time, or you can leave it empty.</span></span> <span data-ttu-id="1ac29-113">Jednak podczas dodawania tabeli bez **TableName** do wartości **DataSet**, tabela zostanie podana przyrostowe domyślną nazwę tabeli*N*począwszy Table0 "tabeli".</span><span class="sxs-lookup"><span data-stu-id="1ac29-113">However, when you add a table without a **TableName** value to a **DataSet**, the table will be given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ac29-114">Firma Microsoft zaleca, aby uniknąć "Tabela*N*" konwencji nazewnictwa, jeśli podasz **TableName** wartości, ponieważ musisz podać nazwę może spowodować konflikt z istniejącą nazwą tabeli domyślne w **zestawu danych** .</span><span class="sxs-lookup"><span data-stu-id="1ac29-114">We recommend that you avoid the "Table*N*" naming convention when you supply a **TableName** value, because the name you supply may conflict with an existing default table name in the **DataSet**.</span></span> <span data-ttu-id="1ac29-115">Jeśli podanej nazwie już istnieje, jest zwracany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1ac29-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="1ac29-116">Poniższy przykład tworzy wystąpienie **DataTable** obiektów i przypisuje mu nazwę "Klienci".</span><span class="sxs-lookup"><span data-stu-id="1ac29-116">The following example creates an instance of a **DataTable** object and assigns it the name "Customers."</span></span>  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 <span data-ttu-id="1ac29-117">Poniższy przykład tworzy wystąpienie **DataTable** przez dodanie go do **tabel** Kolekcja **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="1ac29-117">The following example creates an instance of a **DataTable** by adding it to the **Tables** collection of a **DataSet**.</span></span>  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ac29-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ac29-118">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [<span data-ttu-id="1ac29-119">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="1ac29-119">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="1ac29-120">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="1ac29-120">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="1ac29-121">Ładowanie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1ac29-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="1ac29-122">Ładowanie informacji o schemacie elementu DataSet z pliku XML</span><span class="sxs-lookup"><span data-stu-id="1ac29-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="1ac29-123">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="1ac29-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
