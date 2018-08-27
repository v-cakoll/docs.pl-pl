---
title: Dane FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: fb7291fad15917614f5eebd31ad0e239c987a81d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931403"
---
# <a name="filestream-data"></a><span data-ttu-id="17030-102">Dane FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="17030-102">FILESTREAM Data</span></span>
<span data-ttu-id="17030-103">Atrybutu magazynowania FILESTREAM jest dla danych binarnych (BLOB) przechowywanego w kolumny typu varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="17030-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="17030-104">Przed FILESTREAM przechowywanie danych binarnych wymaga specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="17030-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="17030-105">Danych niestrukturalnych, takich jak dokumenty tekstowe, obrazy i wideo, często są przechowywane poza bazą danych, co utrudnia do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="17030-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17030-106">Należy zainstalować .NET Framework 3.5 z dodatkiem SP1 (lub nowszym) do pracy z danymi FILESTREAM przy użyciu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="17030-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="17030-107">Określając atrybut FILESTREAM kolumny typu varbinary(max) powoduje, że program SQL Server do przechowywania danych na lokalny system plików NTFS zamiast w pliku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="17030-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="17030-108">Chociaż były przechowywane osobno, możesz użyć takie same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, które są obsługiwane w przypadku pracy z danymi varbinary(max), która jest przechowywana w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="17030-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="17030-109">Obsługa SqlClient dla FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="17030-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="17030-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Dostawcy danych programu SQL Server <xref:System.Data.SqlClient>, obsługuje Odczyt i zapis danych FILESTREAM przy użyciu <xref:System.Data.SqlTypes.SqlFileStream> klasy zdefiniowanej w <xref:System.Data.SqlTypes> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="17030-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="17030-111">`SqlFileStream` dziedziczy <xref:System.IO.Stream> klasy, która zawiera metody służące do odczytu i zapisu do strumieni danych.</span><span class="sxs-lookup"><span data-stu-id="17030-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="17030-112">Odczyt ze strumienia przesyła dane ze strumienia do struktury danych, takich jak tablica bajtów.</span><span class="sxs-lookup"><span data-stu-id="17030-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="17030-113">Zapisywanie przesyła dane z struktury danych w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="17030-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-sql-server-table"></a><span data-ttu-id="17030-114">Tworzenie tabeli programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="17030-114">Creating the SQL Server Table</span></span>  
 <span data-ttu-id="17030-115">Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji tworzy tabelę o nazwie Pracownicy i wstawia wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="17030-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="17030-116">Po włączeniu magazynowania FILESTREAM można użyć tej tabeli, w połączeniu z przykładami kodu, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="17030-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="17030-117">Na końcu tego tematu znajdują się linki do zasobów programu SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="17030-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>  
  
```  
CREATE TABLE employees  
(  
  EmployeeId INT  NOT NULL  PRIMARY KEY,  
  Photo VARBINARY(MAX) FILESTREAM  NULL,  
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL  
  UNIQUE DEFAULT NEWID()  
)  
GO  
Insert into employees  
Values(1, 0x00, default)  
GO  
```  
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="17030-118">Przykład: Odczytu, zastępowanie i wstawianie danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="17030-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="17030-119">Poniższy przykład pokazuje, jak można odczytać danych z FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="17030-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="17030-120">Kod pobiera logiczne ścieżkę do pliku, ustawianie `FileAccess` do `Read` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="17030-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="17030-121">Kod następnie odczytuje bajtów z SqlFileStream w buforze.</span><span class="sxs-lookup"><span data-stu-id="17030-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="17030-122">Bajty są następnie zapisywane do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="17030-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="17030-123">W przykładzie pokazano również sposób zapisywania danych FILESTREAM, w którym wszystkie istniejące dane zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="17030-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="17030-124">Ten kod pobiera logiczne ścieżkę do pliku i tworzy `SqlFileStream`, ustawiając `FileAccess` do `Write` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="17030-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="17030-125">Jednobajtowych są zapisywane do `SqlFileStream`, zastępując wszystkie dane w pliku.</span><span class="sxs-lookup"><span data-stu-id="17030-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="17030-126">W przykładzie pokazano również sposób zapisywania danych FILESTREAM przy użyciu metody wyszukiwania, aby dołączyć dane do końca pliku.</span><span class="sxs-lookup"><span data-stu-id="17030-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="17030-127">Ten kod pobiera logiczne ścieżkę do pliku i tworzy `SqlFileStream`, ustawiając `FileAccess` do `ReadWrite` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="17030-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="17030-128">Kod używa metody wyszukiwania do wyszukania na końcu pliku, dodając jednobajtowych do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="17030-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Data;  
using System.IO;  
  
namespace FileStreamTest  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");  
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for the file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Read the contents as bytes and write them to the console  
                            for (long index = 0; index < fileStream.Length; index++)  
                            {  
                                Console.WriteLine(fileStream.ReadByte());  
                            }  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file   
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Write a single byte to the file. This will  
                            // replace any data in the file.  
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Seek to the end of the file  
                            fileStream.Seek(0, SeekOrigin.End);  
  
                            // Append a single byte   
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
  
        }  
    }  
}
```  
  
 <span data-ttu-id="17030-129">Aby uzyskać inny przykład, zobacz [jak przechowywać i pobierać dane binarne do kolumny strumienia pliku](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="17030-129">For another sample, see [How to store and fetch binary data into a file stream column](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="17030-130">Zasoby programu SQL Server — książki Online</span><span class="sxs-lookup"><span data-stu-id="17030-130">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="17030-131">Pełną dokumentację dla FILESTREAM znajduje się w następujących sekcjach w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="17030-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="17030-132">Temat</span><span class="sxs-lookup"><span data-stu-id="17030-132">Topic</span></span>|<span data-ttu-id="17030-133">Opis</span><span class="sxs-lookup"><span data-stu-id="17030-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17030-134">[Projektowanie i implementowanie magazynowania FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="17030-134">[Designing and Implementing FILESTREAM Storage](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span></span>|<span data-ttu-id="17030-135">Zawiera łącza do dokumentacji FILESTREAM i Tematy pokrewne.</span><span class="sxs-lookup"><span data-stu-id="17030-135">Provides links to FILESTREAM documentation and related topics.</span></span>|  
|<span data-ttu-id="17030-136">[Omówienie FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="17030-136">[FILESTREAM Overview](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span></span>|<span data-ttu-id="17030-137">Opisuje, kiedy należy używać magazynowania FILESTREAM i sposobu integracji aparatu bazy danych programu SQL Server w systemie plików NTFS.</span><span class="sxs-lookup"><span data-stu-id="17030-137">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|<span data-ttu-id="17030-138">[Wprowadzenie do magazynowania FILESTREAM](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="17030-138">[Getting Started with FILESTREAM Storage](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span></span>|<span data-ttu-id="17030-139">W tym artykule opisano, jak włączyć funkcję FILESTREAM w wystąpieniu programu SQL Server, jak utworzyć bazę danych i tabelę, do przechowywanych danych FILESTREAM i sposoby manipulowania wiersze zawierające dane FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="17030-139">Describes how to enable FILESTREAM on an instance of SQL Server, how to create a database and a table to stored FILESTREAM data, and how to manipulate rows containing FILESTREAM data.</span></span>|  
|<span data-ttu-id="17030-140">[Za pomocą magazynowania FILESTREAM w aplikacjach klienckich](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="17030-140">[Using FILESTREAM Storage in Client Applications](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span></span>|<span data-ttu-id="17030-141">Zawiera opis funkcji Win32 API do pracy z danymi FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="17030-141">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|[<span data-ttu-id="17030-142">FILESTREAM i inne funkcje serwera SQL</span><span class="sxs-lookup"><span data-stu-id="17030-142">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="17030-143">Zawiera zagadnienia, wytyczne i ograniczenia dotyczące używania danych FILESTREAM z innymi funkcjami programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17030-143">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17030-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17030-144">See Also</span></span>  
 [<span data-ttu-id="17030-145">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17030-145">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="17030-146">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17030-146">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="17030-147">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17030-147">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="17030-148">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="17030-148">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="17030-149">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="17030-149">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
