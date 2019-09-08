---
title: Pobieranie danych binarnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 9acda6631e17031a81ba06d9530739a586fac7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794434"
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="7632c-102">Pobieranie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="7632c-102">Retrieving Binary Data</span></span>
<span data-ttu-id="7632c-103">Domyślnie element **DataReader** ładuje dane przychodzące jako wiersz zaraz po udostępnieniu całego wiersza danych.</span><span class="sxs-lookup"><span data-stu-id="7632c-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="7632c-104">Duże obiekty binarne (BLOB) wymagają innej obróbki, ale mogą zawierać gigabajty danych, które nie mogą być zawarte w pojedynczym wierszu.</span><span class="sxs-lookup"><span data-stu-id="7632c-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="7632c-105">Metoda **Command. ExecuteReader** ma Przeciążenie, które będzie miało <xref:System.Data.CommandBehavior> argument modyfikujący domyślne zachowanie elementu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="7632c-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="7632c-106">Można przekazać <xref:System.Data.CommandBehavior.SequentialAccess> do metody **ExecuteReader** , aby zmodyfikować domyślne zachowanie elementu **DataReader** , tak aby zamiast ładowania wierszy danych dane były ładowane sekwencyjnie po ich odebraniu.</span><span class="sxs-lookup"><span data-stu-id="7632c-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="7632c-107">Jest to idealne rozwiązanie w przypadku ładowania obiektów blob lub innych dużych struktur danych.</span><span class="sxs-lookup"><span data-stu-id="7632c-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="7632c-108">Należy zauważyć, że to zachowanie może zależeć od źródła danych.</span><span class="sxs-lookup"><span data-stu-id="7632c-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="7632c-109">Na przykład zwrócenie obiektu BLOB z programu Microsoft Access spowoduje załadowanie całego obiektu BLOB, który jest ładowany do pamięci, a nie sekwencyjnie po odebraniu.</span><span class="sxs-lookup"><span data-stu-id="7632c-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="7632c-110">Podczas ustawiania elementu **DataReader** do korzystania z **SequentialAccess**należy zwrócić uwagę na sekwencję, do której uzyskuje się dostęp do zwracanych pól.</span><span class="sxs-lookup"><span data-stu-id="7632c-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="7632c-111">Domyślne zachowanie elementu **DataReader**, który ładuje cały wiersz zaraz po jego udostępnieniu, umożliwia dostęp do pól zwracanych w dowolnej kolejności do momentu odczytania następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="7632c-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="7632c-112">W przypadku korzystania z **SequentialAccess** należy jednak uzyskać dostęp do pól zwracanych przez element **DataReader** w kolejności.</span><span class="sxs-lookup"><span data-stu-id="7632c-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="7632c-113">Na przykład, jeśli zapytanie zwróci trzy kolumny, trzecią, z której jest obiektem BLOB, należy zwrócić wartości pierwszego i drugiego pola przed uzyskaniem dostępu do danych obiektu BLOB w trzecim polu.</span><span class="sxs-lookup"><span data-stu-id="7632c-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="7632c-114">Jeśli uzyskujesz dostęp do trzeciego pola przed pierwszym lub drugim polem, wartości pierwszego i drugiego pola nie będą już dostępne.</span><span class="sxs-lookup"><span data-stu-id="7632c-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="7632c-115">Wynika to z faktu, że program **SequentialAccess** zmodyfikował element **DataReader** , aby zwracał dane w sekwencji, a dane nie są dostępne, gdy element **DataReader** zakończył jego poprzednią wartość.</span><span class="sxs-lookup"><span data-stu-id="7632c-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="7632c-116">Podczas uzyskiwania dostępu do danych w polu obiekt BLOB należy użyć typu metody dostępu **GetBytes** lub **GetChars** elementu **DataReader**, który wypełnia tablicę danymi.</span><span class="sxs-lookup"><span data-stu-id="7632c-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="7632c-117">Można również użyć **GetString** dla danych znakowych; ale.</span><span class="sxs-lookup"><span data-stu-id="7632c-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="7632c-118">Aby zaoszczędzić zasoby systemowe, możesz nie chcieć załadować całej wartości obiektu BLOB do pojedynczej zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="7632c-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="7632c-119">Zamiast tego można określić określony rozmiar buforu danych do zwrócenia oraz lokalizację początkową dla pierwszego bajtu lub znaku, który ma zostać odczytany z zwracanych danych.</span><span class="sxs-lookup"><span data-stu-id="7632c-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="7632c-120">**GetBytes** i **GetChars** zwróci `long` wartość, która reprezentuje liczbę zwracanych bajtów lub znaków.</span><span class="sxs-lookup"><span data-stu-id="7632c-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="7632c-121">Jeśli przejdziesz tablicę o wartości null do **GetBytes** lub **GetChars**, zwrócona wartość Long będzie całkowitą liczbą bajtów lub znaków w obiekcie blob.</span><span class="sxs-lookup"><span data-stu-id="7632c-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="7632c-122">Opcjonalnie można określić indeks w tablicy jako pozycję początkową dla odczytywanych danych.</span><span class="sxs-lookup"><span data-stu-id="7632c-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7632c-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="7632c-123">Example</span></span>  
 <span data-ttu-id="7632c-124">Poniższy przykład zwraca identyfikator wydawcy i logo z przykładowej bazy danych **pubs** w Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7632c-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="7632c-125">Identyfikator wydawcy (`pub_id`) to pole znaku, a logo jest obrazem, który jest obiektem BLOB.</span><span class="sxs-lookup"><span data-stu-id="7632c-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="7632c-126">Ponieważ pole **logo** jest mapą bitową, przykład zwraca dane binarne przy użyciu **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="7632c-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="7632c-127">Zwróć uwagę, że identyfikator wydawcy jest dostępny dla bieżącego wiersza danych przed logo, ponieważ pola muszą być dostępne sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="7632c-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7632c-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7632c-128">See also</span></span>

- [<span data-ttu-id="7632c-129">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="7632c-129">SQL Server Binary and Large-Value Data</span></span>](./sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="7632c-130">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7632c-130">ADO.NET Overview</span></span>](ado-net-overview.md)
