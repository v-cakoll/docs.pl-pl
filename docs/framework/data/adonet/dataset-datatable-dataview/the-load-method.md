---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150730"
---
# <a name="the-load-method"></a><span data-ttu-id="ef871-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="ef871-102">The Load Method</span></span>
<span data-ttu-id="ef871-103">Za pomocą <xref:System.Data.DataTable.Load%2A> metody można <xref:System.Data.DataTable> załadować wiersze z ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ef871-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="ef871-104">Jest to przeciążona metoda, która w najprostszej formie akceptuje pojedynczy parametr, **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="ef871-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="ef871-105">W tej formie po prostu ładuje **DataTable** z wierszami.</span><span class="sxs-lookup"><span data-stu-id="ef871-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="ef871-106">Opcjonalnie można określić **parametr LoadOption,** aby kontrolować sposób dodawania danych do **tabeli DataTable**.</span><span class="sxs-lookup"><span data-stu-id="ef871-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="ef871-107">**Parametr LoadOption** jest szczególnie przydatny w przypadkach, gdy **datatable** zawiera już wiersze danych, ponieważ opisuje, jak przychodzące dane ze źródła danych zostaną połączone z danymi już w tabeli.</span><span class="sxs-lookup"><span data-stu-id="ef871-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="ef871-108">Na przykład **PreserveCurrentValues** (domyślnie) określa, że w przypadkach, gdy wiersz jest oznaczony jako **Dodany** w **Tabeli danych,** wartość **Oryginalna** lub każda kolumna jest ustawiona na zawartość pasującego wiersza ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ef871-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="ef871-109">**Bieżąca** wartość zachowa wartości przypisane po dodaniu wiersza, a **stan wiersza** wiersza zostanie ustawiony na **Zmieniono**.</span><span class="sxs-lookup"><span data-stu-id="ef871-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="ef871-110">W poniższej tabeli przedstawiono krótki opis wartości wyliczenia. <xref:System.Data.LoadOption></span><span class="sxs-lookup"><span data-stu-id="ef871-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="ef871-111">Wartość LoadOption</span><span class="sxs-lookup"><span data-stu-id="ef871-111">LoadOption value</span></span>|<span data-ttu-id="ef871-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ef871-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="ef871-113">**Zastąprowrow**</span><span class="sxs-lookup"><span data-stu-id="ef871-113">**OverwriteRow**</span></span>|<span data-ttu-id="ef871-114">Jeśli przychodzące wiersze mają taką samą wartość **PrimaryKey** jak wiersz już w **Tabeli data,** oryginalne **i** **bieżące** wartości każdej kolumny są zastępowane wartościami w wierszu przychodzącym, a właściwość **RowState** jest ustawiona na **Niezmieniona**.</span><span class="sxs-lookup"><span data-stu-id="ef871-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="ef871-115">Wiersze ze źródła danych, które jeszcze nie istnieją w **tabeli DataTable,** są dodawane z wartością **RowState** **niezmienioną**.</span><span class="sxs-lookup"><span data-stu-id="ef871-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="ef871-116">Ta opcja w efekcie odświeża zawartość **DataTable** tak, aby była zgodna z zawartością źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ef871-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="ef871-117">**Zachowajwartości bieżące (domyślnie)**</span><span class="sxs-lookup"><span data-stu-id="ef871-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="ef871-118">Jeśli przychodzące wiersze mają taką samą wartość **PrimaryKey** jak wiersz już w **Tabeli Data,** **oryginalna** wartość jest ustawiona na zawartość wiersza przychodzącego, a **bieżąca** wartość nie zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="ef871-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="ef871-119">Jeśli **stan wiersza** zostanie **dodany** lub **zmodyfikowany,** jest on ustawiony na **Zmodyfikowany**.</span><span class="sxs-lookup"><span data-stu-id="ef871-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="ef871-120">Jeśli **stan wiersza** został **usunięty,** pozostaje **usunięty**.</span><span class="sxs-lookup"><span data-stu-id="ef871-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="ef871-121">Wiersze ze źródła danych, które jeszcze nie istnieją w **Tabeli danych,** są dodawane, a **stan wiersza** jest ustawiony na **Niezmieniony**.</span><span class="sxs-lookup"><span data-stu-id="ef871-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="ef871-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="ef871-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="ef871-123">Jeśli przychodzące wiersze mają taką samą wartość **PrimaryKey** jak wiersz już w **Tabeli data,** **bieżąca** wartość jest kopiowana do **oryginalnej** wartości, a wartość **Bieżąca** jest następnie ustawiana na zawartość wiersza przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="ef871-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="ef871-124">Jeśli **wiersz Stan** w **DataTable** został **dodany**, **RowState** pozostaje **dodany**.</span><span class="sxs-lookup"><span data-stu-id="ef871-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="ef871-125">W przypadku wierszy oznaczonych jako **Zmodyfikowane** lub **Usunięte** **stan wiersza** jest **modyfikowany**.</span><span class="sxs-lookup"><span data-stu-id="ef871-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="ef871-126">Wiersze ze źródła danych, które jeszcze nie istnieją w **Tabeli danych,** są dodawane, a **stan wiersza** jest ustawiony na **Dodano**.</span><span class="sxs-lookup"><span data-stu-id="ef871-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="ef871-127">W poniższym przykładzie użyto **Load** metody do wyświetlania listy urodzin dla pracowników w bazie danych **Northwind.**</span><span class="sxs-lookup"><span data-stu-id="ef871-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef871-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef871-128">See also</span></span>

- [<span data-ttu-id="ef871-129">Operowanie na danych w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="ef871-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="ef871-130">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ef871-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
