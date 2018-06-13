---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 04defffc724875e691fd7b87331c28e6b6c0cd28
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758311"
---
# <a name="the-load-method"></a><span data-ttu-id="5c82f-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="5c82f-102">The Load Method</span></span>
<span data-ttu-id="5c82f-103">Można użyć <xref:System.Data.DataTable.Load%2A> metodę, aby załadować <xref:System.Data.DataTable> z wierszy ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5c82f-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="5c82f-104">To jest przeciążona metoda, która w swojej najprostszej formie przyjmuje jeden parametr, **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="5c82f-105">W tym formularzu, po prostu ładuje **DataTable** z wierszami.</span><span class="sxs-lookup"><span data-stu-id="5c82f-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="5c82f-106">Opcjonalnie można określić **LoadOption** parametr, aby kontrolować sposób dodawania danych do **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="5c82f-107">**LoadOption** parametr jest szczególnie przydatne w sytuacjach, gdy **DataTable** już zawiera wiersze danych, ponieważ opisuje sposób przychodzących danych ze źródła danych zostaną połączone z danymi już w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5c82f-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="5c82f-108">Na przykład **PreserveCurrentValues** (opcja domyślna) określa, że w przypadku, gdy wiersz jest oznaczony jako **Added** w **DataTable**, **oryginalne** wartość lub każdej kolumny ustawiono zawartość pasującego wiersza ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5c82f-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="5c82f-109">**Bieżącego** wartości zostaną zachowane wartości przypisane, gdy wiersz został dodany i **RowState** wiersza zostanie ustawiona do **zmienione**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="5c82f-110">W poniższej tabeli przedstawiono krótki opis <xref:System.Data.LoadOption> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5c82f-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="5c82f-111">Wartość LoadOption</span><span class="sxs-lookup"><span data-stu-id="5c82f-111">LoadOption value</span></span>|<span data-ttu-id="5c82f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5c82f-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="5c82f-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="5c82f-113">**OverwriteRow**</span></span>|<span data-ttu-id="5c82f-114">Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz już **DataTable**, **oryginalnego** i **bieżącego** wartości każdego z nich kolumny są zamieniane na wartości w wierszu przychodzące i **RowState** właściwość jest ustawiona na **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5c82f-115">Wierszy ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane z **RowState** wartość **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="5c82f-116">Ta opcja skutkuje Odświeża zawartość **DataTable** tak, aby było zgodne zawartość źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5c82f-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="5c82f-117">**PreserveCurrentValues (ustawienie domyślne)**</span><span class="sxs-lookup"><span data-stu-id="5c82f-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="5c82f-118">Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz już **DataTable**, **oryginalnego** wartość jest ustawiona na zawartość wiersza przychodzące i **Bieżącego** wartość nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="5c82f-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="5c82f-119">Jeśli **RowState** jest **Added** lub **zmodyfikowane**, jest równa **zmodyfikowane**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="5c82f-120">Jeśli **RowState** został **usunięte**, pozostaje **usunięte**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="5c82f-121">Wierszy ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="5c82f-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="5c82f-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="5c82f-123">Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz już **DataTable**, **bieżącego** wartość jest kopiowany do **oryginalne**wartości i **bieżącego** następnie ustawiono wartość zawartości wiersza przychodzących.</span><span class="sxs-lookup"><span data-stu-id="5c82f-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="5c82f-124">Jeśli **RowState** w **DataTable** został **Added**, **RowState** pozostaje **Added**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="5c82f-125">Do wierszy oznaczony jako **zmodyfikowane** lub **usunięte**, **RowState** jest **zmodyfikowane**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="5c82f-126">Wierszy ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **Added**.</span><span class="sxs-lookup"><span data-stu-id="5c82f-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="5c82f-127">Następujące przykładowe używa **obciążenia** metodę, aby wyświetlić listę dat urodzenia pracowników **Northwind** bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5c82f-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c82f-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c82f-128">See Also</span></span>  
 [<span data-ttu-id="5c82f-129">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="5c82f-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="5c82f-130">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="5c82f-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
