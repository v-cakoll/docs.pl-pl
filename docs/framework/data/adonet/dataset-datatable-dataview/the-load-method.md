---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: da0695aff9447355b1fc44a033c1b4a1cc224435
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785882"
---
# <a name="the-load-method"></a><span data-ttu-id="59ac3-102">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="59ac3-102">The Load Method</span></span>
<span data-ttu-id="59ac3-103">Możesz użyć <xref:System.Data.DataTable.Load%2A> metody do <xref:System.Data.DataTable> załadowania z wierszami ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="59ac3-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="59ac3-104">Jest to przeciążona metoda, która w najprostszej postaci akceptuje pojedynczy parametr, element **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="59ac3-105">W tym formularzu po prostu ładuje **DataTable** z wierszami.</span><span class="sxs-lookup"><span data-stu-id="59ac3-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="59ac3-106">Opcjonalnie można określić parametr **LoadOption** , aby kontrolować sposób dodawania danych do obiektu **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="59ac3-107">Parametr **LoadOption** jest szczególnie przydatny w przypadkach, gdy element **DataTable** zawiera już wiersze danych, ponieważ opisuje sposób, w jaki dane przychodzące ze źródła danych będą łączone z danymi znajdującymi się już w tabeli.</span><span class="sxs-lookup"><span data-stu-id="59ac3-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="59ac3-108">Na przykład **PreserveCurrentValues** (wartość domyślna) określa, że w przypadkach, gdy wiersz jest oznaczony jako **dodany** w **tabeli DataTable**, **oryginalna** wartość lub każda kolumna jest ustawiona na zawartość pasującego wiersza ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="59ac3-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="59ac3-109">**Bieżąca** wartość spowoduje zachowanie wartości przypisanych, gdy wiersz został dodany, a **RowState** wierszy zostanie ustawiona na wartość **zmienione**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="59ac3-110">Poniższa tabela zawiera krótki opis <xref:System.Data.LoadOption> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="59ac3-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="59ac3-111">LoadOption wartość</span><span class="sxs-lookup"><span data-stu-id="59ac3-111">LoadOption value</span></span>|<span data-ttu-id="59ac3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="59ac3-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="59ac3-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="59ac3-113">**OverwriteRow**</span></span>|<span data-ttu-id="59ac3-114">Jeśli wiersze przychodzące mają tę samą wartość **PrimaryKey** jak wiersz już w **tabeli DataTable**, **pierwotne** i **bieżące** wartości każdej kolumny są zastępowane wartościami w wierszu przychodzące, a właściwość **RowState** jest ustawiona na **Bez zmian**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="59ac3-115">Wiersze ze źródła danych, które jeszcze nie istnieją w tabeli **DataTable** , są dodawane z **niezmienionym**wartością **RowState** .</span><span class="sxs-lookup"><span data-stu-id="59ac3-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="59ac3-116">Ta opcja powoduje odświeżenie zawartości **elementu DataTable** tak, aby odpowiadał zawartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="59ac3-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="59ac3-117">**PreserveCurrentValues (domyślnie)**</span><span class="sxs-lookup"><span data-stu-id="59ac3-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="59ac3-118">Jeśli wiersze przychodzące mają taką samą wartość **PrimaryKey** jak wiersz już w **tabeli DataTable**, **oryginalna** wartość jest ustawiana na zawartość wiersza przychodzącego, a **Bieżąca** wartość nie jest zmieniana.</span><span class="sxs-lookup"><span data-stu-id="59ac3-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="59ac3-119">Jeśli **RowState** jest **dodawany** lub **modyfikowany**, jest ustawiony na wartość **zmodyfikowano**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="59ac3-120">Jeśli **RowState** został **usunięty**, pozostanie **usunięty**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="59ac3-121">Wiersze ze źródła danych, które jeszcze nie istnieją w tabeli **DataTable** , są dodawane, a **RowState** jest ustawiona na wartość **Unchanged**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="59ac3-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="59ac3-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="59ac3-123">Jeśli wiersze przychodzące mają tę samą wartość **PrimaryKey** jak wiersz już w **tabeli DataTable**, **Bieżąca** wartość jest kopiowana do **pierwotnej** wartości, a **Bieżąca** wartość jest ustawiana na zawartość wiersza przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="59ac3-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="59ac3-124">Jeśli **RowState** w **elemencie DataTable** został **dodany**, **RowState** zostanie **dodana**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="59ac3-125">W przypadku wierszy oznaczonych jako **zmodyfikowane** lub usunięte **RowState** jest **modyfikowany**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="59ac3-126">Wiersze ze źródła danych, które nie znajdują się jeszcze w **elemencie DataTable** , są dodawane i **RowState** jest ustawiony na wartość **dodana**.</span><span class="sxs-lookup"><span data-stu-id="59ac3-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="59ac3-127">Poniższy przykład używa metody **Load** do wyświetlania listy urodzin dla pracowników w bazie danych **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="59ac3-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59ac3-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59ac3-128">See also</span></span>

- [<span data-ttu-id="59ac3-129">Operowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="59ac3-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="59ac3-130">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="59ac3-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
