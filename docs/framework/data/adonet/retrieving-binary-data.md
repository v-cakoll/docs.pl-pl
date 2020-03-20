---
title: Pobieranie danych binarnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: c914a9b0780e2e87e177502b0f9faff0e7c4b617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149053"
---
# <a name="retrieving-binary-data"></a>Pobieranie danych binarnych
Domyślnie **DataReader** ładuje dane przychodzące jako wiersz, gdy tylko cały wiersz danych jest dostępny. Binarne dużych obiektów (BLOB) wymagają innego traktowania, jednak ponieważ mogą one zawierać gigabajty danych, które nie mogą być zawarte w jednym wierszu. **Command.ExecuteReader** Metoda ma przeciążenie, <xref:System.Data.CommandBehavior> które zajmie argument, aby zmodyfikować domyślne zachowanie **DataReader**. Można przekazać <xref:System.Data.CommandBehavior.SequentialAccess> do **ExecuteReader** metody, aby zmodyfikować domyślne zachowanie **DataReader** tak, aby zamiast ładowania wierszy danych, będzie ładować dane sekwencyjnie, jak to jest odbierane. Jest to idealne rozwiązanie do ładowania bloków BLOB lub innych struktur dużych danych. Należy zauważyć, że to zachowanie może zależeć od źródła danych. Na przykład zwracanie obiektu BLOB z programu Microsoft Access spowoduje załadowanie całego obiektu BLOB ładowanego do pamięci, a nie sekwencyjnie w miarę jego odnośności.  
  
 Podczas **ustawiania DataReader** używać **SequentialAccess**, ważne jest, aby zanotować sekwencję, w której można uzyskać dostęp do zwróconych pól. Domyślne zachowanie **DataReader**, który ładuje cały wiersz, jak tylko jest dostępny, umożliwia dostęp do pól zwracanych w dowolnej kolejności, aż do odczytu następnego wiersza. Podczas korzystania **sekwencyjneaccess** jednak należy uzyskać dostęp do pól zwróconych przez **DataReader** w kolejności. Na przykład jeśli kwerenda zwraca trzy kolumny, z których trzecia jest obiektem BLOB, należy zwrócić wartości pierwszego i drugiego pola przed dostępem do danych obiektu BLOB w trzecim polu. Jeśli dostęp do trzeciego pola przed pierwszym lub drugim polem jest niedostępny, wartości pierwszego i drugiego pola nie są już dostępne. Jest to spowodowane **SequentialAccess zmodyfikował** **DataReader** do zwracania danych w sekwencji i dane nie są dostępne po **DataReader** odczytu przeszłości.  
  
 Podczas uzyskiwania dostępu do danych w polu BLOB należy użyć akcesorów **getbytes** lub **GetChars** wpisanych w **programie DataReader**, które wypełniają tablicę danymi. Można również użyć **GetString** dla danych znaków; Jednak. aby oszczędzać zasoby systemowe, możesz nie chcieć załadować całej wartości obiektu BLOB do zmiennej pojedynczego ciągu. Zamiast tego można określić określony rozmiar buforu danych do zwrotu i lokalizację początkową dla pierwszego bajtu lub znaku do odczytu z zwróconych danych. **GetBytes** i **GetChars** `long` zwróci wartość, która reprezentuje liczbę bajtów lub znaków zwróconych. Jeśli przekażesz tablicę null do **GetBytes** lub **GetChars,** zwrócona wartość długoterminowa będzie całkowitą liczbą bajtów lub znaków w obiekcie BLOB. Opcjonalnie można określić indeks w tablicy jako pozycję początkową dla odczytywanych danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca identyfikator wydawcy i logo z przykładowej bazy danych **pubów** w programie Microsoft SQL Server. Identyfikator wydawcy`pub_id`( ) jest polem znaków, a logo jest obrazem, który jest obiektem BLOB. Ponieważ pole **logo** jest bitmapą, w przykładzie zwraca dane binarne przy użyciu **pliku GetBytes**. Należy zauważyć, że identyfikator wydawcy jest dostępny dla bieżącego wiersza danych przed logo, ponieważ pola muszą być dostępne sekwencyjnie.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Dane binarne i dużej wartości w programie SQL Server](./sql/sql-server-binary-and-large-value-data.md)
- [Omówienie ADO.NET](ado-net-overview.md)
