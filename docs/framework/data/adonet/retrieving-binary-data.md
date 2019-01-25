---
title: Pobieranie danych binarnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 2d1b88d25c5c2e94d86c1fed53c472e2b0af493e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643653"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="fae11-102">Pobieranie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="fae11-102">Retrieving Binary Data</span></span>
<span data-ttu-id="fae11-103">Domyślnie **DataReader** ładuje przychodzących danych jako wiersz, jak tylko cały wiersz danych jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="fae11-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="fae11-104">Duże obiekty binarne (BLOB) muszą jednak różnego traktowania, ponieważ zawierają one gigabajtów danych, który nie może się znajdować w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="fae11-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="fae11-105">**Command.ExecuteReader** metoda ma przeciążenia, które będą miały <xref:System.Data.CommandBehavior> argumentu, aby zmodyfikować domyślne zachowanie **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="fae11-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="fae11-106">Możesz przekazać <xref:System.Data.CommandBehavior.SequentialAccess> do **ExecuteReader** metodę, aby zmodyfikować domyślne zachowanie **DataReader** tak, aby zamiast ładowania wierszy danych, będzie on ładować dane sekwencyjnie po otrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="fae11-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="fae11-107">Jest to idealne rozwiązanie w przypadku ładowania obiektów blob lub innych struktur dużych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="fae11-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="fae11-108">Należy pamiętać, że takie zachowanie może zależeć od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="fae11-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="fae11-109">Na przykład zwracając obiekt BLOB z programu Microsoft Access załaduje cały obiekt BLOB ładowany do pamięci, a nie po kolei, gdy są odbierane.</span><span class="sxs-lookup"><span data-stu-id="fae11-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="fae11-110">Podczas ustawiania **DataReader** używać **SequentialAccess**, należy zauważyć kolejność, w którym uzyskujesz dostęp do pola, zwracany jest.</span><span class="sxs-lookup"><span data-stu-id="fae11-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="fae11-111">Domyślne zachowanie **DataReader**, który ładuje cały wiersz, jak jest dostępna, umożliwia dostęp do pola, zwracany w dowolnej kolejności, dopóki nie jest do odczytu następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="fae11-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="fae11-112">Korzystając z **SequentialAccess** musi jednak dostęp do pola, zwracany przez **DataReader** w kolejności.</span><span class="sxs-lookup"><span data-stu-id="fae11-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="fae11-113">Na przykład jeśli zapytanie zwraca trzy kolumny, w trzeciej jest obiektem BLOB, przed uzyskaniem dostępu do danych obiektów BLOB w trzecim polu musi zwracać wartości pól pierwszego i drugiego.</span><span class="sxs-lookup"><span data-stu-id="fae11-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="fae11-114">Jeśli uzyskujesz dostęp do trzecim polu przed pola pierwszej lub drugiej, wartości pierwszego i drugiego pola nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="fae11-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="fae11-115">Jest to spowodowane **SequentialAccess** zmodyfikował **DataReader** zwrócić dane w kolejności i dane nie są dostępne po **DataReader** zapoznał się poza jej.</span><span class="sxs-lookup"><span data-stu-id="fae11-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="fae11-116">Podczas uzyskiwania dostępu do danych w polu obiektów BLOB, użyj **GetBytes** lub **GetChars** wpisane metod dostępu **DataReader**, który Wypełnij tablicę przy użyciu danych.</span><span class="sxs-lookup"><span data-stu-id="fae11-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="fae11-117">Można również użyć **GetString —** danych znakowych; jednak.</span><span class="sxs-lookup"><span data-stu-id="fae11-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="fae11-118">pozwala zaoszczędzić zasoby systemowe nie można załadować całą wartość obiektu BLOB do zmiennej pojedynczy ciąg.</span><span class="sxs-lookup"><span data-stu-id="fae11-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="fae11-119">Zamiast tego można określić rozmiar buforu określone dane zwracane i początkową lokalizację pierwszego bajtu lub znaków do odczytu zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="fae11-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="fae11-120">**GetBytes** i **GetChars** zwróci `long` wartość, która reprezentuje liczbę bajtów lub znaków, zwracane.</span><span class="sxs-lookup"><span data-stu-id="fae11-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="fae11-121">W przypadku przekazania tablicę o wartości null do **GetBytes** lub **GetChars**, długa wartość zwracana będzie całkowita liczba bajtów lub znaków w obiekcie BLOB.</span><span class="sxs-lookup"><span data-stu-id="fae11-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="fae11-122">Opcjonalnie możesz określić indeks w tablicy jako pozycja początkowa odczytywanych danych.</span><span class="sxs-lookup"><span data-stu-id="fae11-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fae11-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="fae11-123">Example</span></span>  
 <span data-ttu-id="fae11-124">Poniższy przykład zwraca identyfikator wydawcy i logo z **pubs** przykładowej bazy danych w programie Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fae11-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="fae11-125">Identyfikator wydawcy (`pub_id`) jest polem znak i logo obraz, który jest obiektem BLOB.</span><span class="sxs-lookup"><span data-stu-id="fae11-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="fae11-126">Ponieważ **logo** pole jest mapy bitowej, w przykładzie zwracany jest przy użyciu danych binarnych **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="fae11-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="fae11-127">Należy zauważyć, że identyfikator wydawcy jest dostępne dla bieżącego wiersza danych przed logo, ponieważ pola, które muszą być dostępne po kolei.</span><span class="sxs-lookup"><span data-stu-id="fae11-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fae11-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fae11-128">See also</span></span>
- [<span data-ttu-id="fae11-129">Praca z DataReaders</span><span class="sxs-lookup"><span data-stu-id="fae11-129">Working with DataReaders</span></span>](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)
- [<span data-ttu-id="fae11-130">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="fae11-130">SQL Server Binary and Large-Value Data</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="fae11-131">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="fae11-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
