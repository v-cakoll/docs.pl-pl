---
title: Podczas pobierania danych binarnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 302c26571e9843a4b7c3c440969e4159ef2d10ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362579"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="d959a-102">Podczas pobierania danych binarnych</span><span class="sxs-lookup"><span data-stu-id="d959a-102">Retrieving Binary Data</span></span>
<span data-ttu-id="d959a-103">Domyślnie **DataReader** ładuje dane przychodzące jako wiersz, jak cały wiersz danych jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="d959a-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="d959a-104">Duże obiekty binarne (BLOB) wymagają innego podejścia, jednak ponieważ zawierają one GB danych, które nie mogą wchodzić w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="d959a-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="d959a-105">**Command.ExecuteReader** metoda ma przeciążenia, które będą wymaga <xref:System.Data.CommandBehavior> argumentu, aby zmodyfikować domyślne zachowanie **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="d959a-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="d959a-106">Można przekazać <xref:System.Data.CommandBehavior.SequentialAccess> do **ExecuteReader** metodę, aby zmodyfikować domyślne zachowanie **DataReader** tak, aby zamiast ładowania wierszy danych, jego ładowanie danych sekwencyjnie odbierane.</span><span class="sxs-lookup"><span data-stu-id="d959a-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="d959a-107">Jest to idealne rozwiązanie w przypadku ładowania obiektów blob lub inne struktury dużej ilości danych.</span><span class="sxs-lookup"><span data-stu-id="d959a-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="d959a-108">Należy pamiętać, że takie zachowanie może zależeć od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d959a-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="d959a-109">Na przykład zwracać obiekt BLOB z programu Microsoft Access załaduje całego obiektu BLOB ładowany do pamięci, a nie po kolei odbierane.</span><span class="sxs-lookup"><span data-stu-id="d959a-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="d959a-110">Podczas ustawiania **DataReader** do używania **SequentialAccess**, ważne jest, aby Zanotuj sekwencję dostęp pola zwracane.</span><span class="sxs-lookup"><span data-stu-id="d959a-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="d959a-111">Domyślne zachowanie **DataReader**, który ładuje cały wiersz, jak jest dostępna, pozwala na dostęp pola zwrócona w dowolnej kolejności, dopóki nie jest do odczytu następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="d959a-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="d959a-112">Korzystając z **SequentialAccess** musi jednak dostęp do pola zwrócony przez **DataReader** w kolejności.</span><span class="sxs-lookup"><span data-stu-id="d959a-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="d959a-113">Na przykład jeśli zapytanie zwraca trzy kolumny, trzecia jest obiektem BLOB, musi zwracać wartości pól pierwszego i drugiego przed uzyskaniem dostępu do danych obiektów BLOB w trzecim polu.</span><span class="sxs-lookup"><span data-stu-id="d959a-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="d959a-114">Jeśli dostęp do trzecim polu przed pierwszym lub drugim pól wartości pól pierwszego i drugiego nie będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="d959a-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="d959a-115">Jest to spowodowane **SequentialAccess** został zmodyfikowany **DataReader** zwrócić dane w sekwencji i dane nie są dostępne po **DataReader** ma odczytu poza go.</span><span class="sxs-lookup"><span data-stu-id="d959a-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="d959a-116">Podczas uzyskiwania dostępu do danych w polu obiektów BLOB, użyj **GetBytes** lub **GetChars** wpisane metod dostępu **DataReader**, który wypełnił tablicy z danymi.</span><span class="sxs-lookup"><span data-stu-id="d959a-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="d959a-117">Można również użyć **GetString** danych znakowych; jednak.</span><span class="sxs-lookup"><span data-stu-id="d959a-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="d959a-118">Aby oszczędzać zasoby systemu nie można załadować całą wartość obiektu BLOB do zmiennej będący pojedynczym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="d959a-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="d959a-119">Zamiast tego można określić rozmiar buforu określonych danych do zwrócenia i początkową lokalizację pierwszego bajtu lub znaków do odczytu zwróconych danych.</span><span class="sxs-lookup"><span data-stu-id="d959a-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="d959a-120">**GetBytes** i **GetChars** zwróci `long` wartość, która reprezentuje liczbę bajtów lub znaki zwrócone.</span><span class="sxs-lookup"><span data-stu-id="d959a-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="d959a-121">W przypadku przekazania tablicy o wartości null do **GetBytes** lub **GetChars**, długo wartość zwracana będzie całkowitą liczbę bajtów lub znaków w obiekcie BLOB.</span><span class="sxs-lookup"><span data-stu-id="d959a-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="d959a-122">Opcjonalnie można określić indeks w tablicy jako pozycja początkowa dla odczytywane dane.</span><span class="sxs-lookup"><span data-stu-id="d959a-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d959a-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="d959a-123">Example</span></span>  
 <span data-ttu-id="d959a-124">Poniższy przykład zwraca identyfikator wydawcy i logo z **pubs** przykładową bazą danych programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d959a-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="d959a-125">Identyfikator wydawcy (`pub_id`) jest polem znaku i logo to obraz, który jest obiektem BLOB.</span><span class="sxs-lookup"><span data-stu-id="d959a-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="d959a-126">Ponieważ **logo** pole jest mapą bitową, przykładzie zwraca dane binarne przy użyciu **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="d959a-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="d959a-127">Zwróć uwagę, że identyfikator wydawcy jest dostępne dla bieżącego wiersza danych przed logo, ponieważ pola muszą być dostępne po kolei.</span><span class="sxs-lookup"><span data-stu-id="d959a-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d959a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d959a-128">See Also</span></span>  
 [<span data-ttu-id="d959a-129">Praca z DataReaders</span><span class="sxs-lookup"><span data-stu-id="d959a-129">Working with DataReaders</span></span>](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="d959a-130">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="d959a-130">SQL Server Binary and Large-Value Data</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="d959a-131">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="d959a-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
