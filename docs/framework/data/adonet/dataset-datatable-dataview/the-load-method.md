---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 82f840ab7dd26a4888ebf024d696f2c70701eb18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173293"
---
# <a name="the-load-method"></a><span data-ttu-id="118e4-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="118e4-102">The Load Method</span></span>
<span data-ttu-id="118e4-103">Możesz użyć <xref:System.Data.DataTable.Load%2A> metodę, aby załadować <xref:System.Data.DataTable> wierszy ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="118e4-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="118e4-104">To jest przeciążona metoda, która w najprostszej postaci przyjmuje jeden parametr **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="118e4-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="118e4-105">W tym formularzu, po prostu ładuje **DataTable** wierszy.</span><span class="sxs-lookup"><span data-stu-id="118e4-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="118e4-106">Opcjonalnie można określić **LoadOption** parametru, aby kontrolować, jak dane są dodawane do **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="118e4-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="118e4-107">**LoadOption** parametr jest szczególnie przydatne w przypadkach, gdzie **DataTable** już zawiera wiersze danych, ponieważ opisuje jak przychodzące dane ze źródła danych, które mają zostać połączone z danymi już w tabeli.</span><span class="sxs-lookup"><span data-stu-id="118e4-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="118e4-108">Na przykład **PreserveCurrentValues** (opcja domyślna) określa, że w przypadku, gdy wiersz jest oznaczony jako **dodano** w **DataTable**, **oryginalnego** wartość lub każda kolumna jest równa zawartości zgodnego wiersza ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="118e4-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="118e4-109">**Bieżącego** wartość zachowają wartości przypisane, gdy wiersz został dodany, a **RowState** wiersza zostanie ustawiony na **zmieniono**.</span><span class="sxs-lookup"><span data-stu-id="118e4-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="118e4-110">W poniższej tabeli przedstawiono krótki opis <xref:System.Data.LoadOption> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="118e4-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="118e4-111">Wartość LoadOption</span><span class="sxs-lookup"><span data-stu-id="118e4-111">LoadOption value</span></span>|<span data-ttu-id="118e4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="118e4-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="118e4-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="118e4-113">**OverwriteRow**</span></span>|<span data-ttu-id="118e4-114">Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz w już **DataTable**, **oryginalnego** i **bieżącego** wartości każdego z nich kolumny są zastępowane wartości w wierszu przychodzących i **RowState** właściwość jest ustawiona na **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="118e4-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="118e4-115">Wiersze ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane przy użyciu **RowState** wartość **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="118e4-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="118e4-116">Ta opcja w praktyce Odświeża zawartość **DataTable** tak, aby pasuje do zawartości ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="118e4-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="118e4-117">**PreserveCurrentValues (ustawienie domyślne)**</span><span class="sxs-lookup"><span data-stu-id="118e4-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="118e4-118">Jeśli przychodzący mają takie same **PrimaryKey** wartość jako wiersz już w **DataTable**, **oryginalnego** wartość zostanie ustawiona na zawartość wiersza przychodzących i **Bieżącego** wartość nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="118e4-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="118e4-119">Jeśli **RowState** jest **dodano** lub **zmodyfikowane**, jest równa **zmodyfikowane**.</span><span class="sxs-lookup"><span data-stu-id="118e4-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="118e4-120">Jeśli **RowState** został **usunięte**, pozostaje **usunięte**.</span><span class="sxs-lookup"><span data-stu-id="118e4-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="118e4-121">Wiersze ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="118e4-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="118e4-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="118e4-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="118e4-123">Jeśli przychodzący mają takie same **PrimaryKey** wartość jako wiersz już w **DataTable**, **bieżącego** wartość jest kopiowany do **oryginalny**wartości, a **bieżącego** następnie wartość na zawartość wiersza przychodzących.</span><span class="sxs-lookup"><span data-stu-id="118e4-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="118e4-124">Jeśli **RowState** w **DataTable** został **dodano**, **RowState** pozostaje **dodano**.</span><span class="sxs-lookup"><span data-stu-id="118e4-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="118e4-125">Dla wierszy oznaczone jako **zmodyfikowane** lub **usunięte**, **RowState** jest **zmodyfikowane**.</span><span class="sxs-lookup"><span data-stu-id="118e4-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="118e4-126">Wiersze ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **dodano**.</span><span class="sxs-lookup"><span data-stu-id="118e4-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="118e4-127">Następujące przykładowe używa **obciążenia** metodę, aby wyświetlić listę dat urodzenia dla pracowników w **Northwind** bazy danych.</span><span class="sxs-lookup"><span data-stu-id="118e4-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="118e4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="118e4-128">See also</span></span>

- [<span data-ttu-id="118e4-129">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="118e4-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="118e4-130">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="118e4-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
