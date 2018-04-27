---
title: Danych FILESTREAM
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 757c64fdc66d9c564fc151bc78fdbda23d9b6705
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="filestream-data"></a><span data-ttu-id="0e628-102">Danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="0e628-102">FILESTREAM Data</span></span>
<span data-ttu-id="0e628-103">Atrybutu magazynowania FILESTREAM jest dla danych binarnych (BLOB) przechowywanych w kolumnie varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="0e628-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="0e628-104">Przed FILESTREAM przechowywanie danych binarnych wymaga specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="0e628-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="0e628-105">Dane niemające struktury, takich jak dokumenty tekst, obrazy i wideo, jest często przechowywane poza bazą danych, co utrudnia zarządzanie.</span><span class="sxs-lookup"><span data-stu-id="0e628-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e628-106">.NET Framework 3.5 z dodatkiem SP1 należy zainstalować (lub nowsza) do pracy z danymi FILESTREAM przy użyciu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="0e628-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="0e628-107">Określenie atrybutu FILESTREAM w kolumnie varbinary(max) powoduje, że program SQL Server do przechowywania danych na lokalnego systemu plików NTFS zamiast w pliku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="0e628-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="0e628-108">Mimo że jest on przechowywany oddzielnie, można używać tego samego [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, które są obsługiwane w przypadku pracy z danymi varbinary(max), który jest przechowywany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0e628-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="0e628-109">Obsługa SqlClient FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="0e628-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="0e628-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Dostawcy danych programu SQL Server <xref:System.Data.SqlClient>, obsługuje Odczyt i zapis danych FILESTREAM przy użyciu <xref:System.Data.SqlTypes.SqlFileStream> klas zdefiniowanych w <xref:System.Data.SqlTypes> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0e628-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="0e628-111">`SqlFileStream` dziedziczy <xref:System.IO.Stream> klasy, która udostępnia metody odczytu i zapisu do strumieni danych.</span><span class="sxs-lookup"><span data-stu-id="0e628-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="0e628-112">Odczytywanie ze strumienia przesyła dane ze strumienia do struktury danych, takich jak tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="0e628-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="0e628-113">Zapisywanie przesyła dane ze struktury danych w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="0e628-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-sql-server-table"></a><span data-ttu-id="0e628-114">Tworzenie tabeli programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e628-114">Creating the SQL Server Table</span></span>  
 <span data-ttu-id="0e628-115">Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcje tworzy tabela o nazwie pracowników i wstawia wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="0e628-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="0e628-116">Po włączeniu magazynowania FILESTREAM, można użyć tej tabeli w połączeniu z przykładów kodu, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="0e628-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="0e628-117">Linki do zasobów w podręcznikach Online programu SQL Server znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0e628-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="0e628-118">Przykład: Odczyt, zastępowanie i wstawianie danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="0e628-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="0e628-119">W poniższym przykładzie pokazano, jak można odczytać danych z FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="0e628-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="0e628-120">Ten kod pobiera logicznej ścieżkę do pliku, ustawienie `FileAccess` do `Read` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="0e628-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="0e628-121">Ten kod odczytuje następnie bajtów z SqlFileStream w buforze.</span><span class="sxs-lookup"><span data-stu-id="0e628-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="0e628-122">Bajty następnie są zapisywane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="0e628-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="0e628-123">Próbka również pokazuje, jak zapisać danych FILESTREAM, w którym jest zastąpienie wszystkich istniejących danych.</span><span class="sxs-lookup"><span data-stu-id="0e628-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="0e628-124">Ten kod pobiera logicznej ścieżkę do pliku i tworzy `SqlFileStream`, ustawienie `FileAccess` do `Write` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="0e628-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="0e628-125">Pojedynczy bajt jest zapisywany w `SqlFileStream`, zastępując żadnych danych w pliku.</span><span class="sxs-lookup"><span data-stu-id="0e628-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="0e628-126">Próbki także przedstawiono sposób zapisywania danych FILESTREAM przy użyciu metody wyszukiwania, aby dołączyć dane do końca pliku.</span><span class="sxs-lookup"><span data-stu-id="0e628-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="0e628-127">Ten kod pobiera logicznej ścieżkę do pliku i tworzy `SqlFileStream`, ustawienie `FileAccess` do `ReadWrite` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="0e628-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="0e628-128">Kod używa metody Seek się na końcu pliku, dołączenie jednobajtowych do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="0e628-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
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
  
 <span data-ttu-id="0e628-129">Inny przykład, zobacz [sposób przechowywania i pobierania danych binarnych do kolumny strumienia pliku](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="0e628-129">For another sample, see [How to store and fetch binary data into a file stream column](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="0e628-130">Zasoby programu SQL Server — książki Online</span><span class="sxs-lookup"><span data-stu-id="0e628-130">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="0e628-131">Pełną dokumentację dla FILESTREAM znajduje się w następujących sekcjach w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="0e628-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="0e628-132">Temat</span><span class="sxs-lookup"><span data-stu-id="0e628-132">Topic</span></span>|<span data-ttu-id="0e628-133">Opis</span><span class="sxs-lookup"><span data-stu-id="0e628-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e628-134">[Projektowanie i implementowanie magazynowania FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0e628-134">[Designing and Implementing FILESTREAM Storage](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span></span>|<span data-ttu-id="0e628-135">Zawiera linki do dokumentacji FILESTREAM i Tematy pokrewne.</span><span class="sxs-lookup"><span data-stu-id="0e628-135">Provides links to FILESTREAM documentation and related topics.</span></span>|  
|<span data-ttu-id="0e628-136">[Omówienie FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0e628-136">[FILESTREAM Overview](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span></span>|<span data-ttu-id="0e628-137">Opisuje, kiedy należy używać magazynowania FILESTREAM i sposobu integracji aparatu bazy danych programu SQL Server w systemie plików NTFS.</span><span class="sxs-lookup"><span data-stu-id="0e628-137">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|<span data-ttu-id="0e628-138">[Wprowadzenie do magazynowania FILESTREAM](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0e628-138">[Getting Started with FILESTREAM Storage](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span></span>|<span data-ttu-id="0e628-139">Opisuje, jak włączyć funkcję FILESTREAM w wystąpieniu programu SQL Server, jak utworzyć bazę danych i tabelę, aby przechowywane dane FILESTREAM oraz manipulowanie wierszami zawierających dane FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="0e628-139">Describes how to enable FILESTREAM on an instance of SQL Server, how to create a database and a table to stored FILESTREAM data, and how to manipulate rows containing FILESTREAM data.</span></span>|  
|<span data-ttu-id="0e628-140">[Za pomocą magazynowania FILESTREAM w aplikacjach klienckich](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0e628-140">[Using FILESTREAM Storage in Client Applications](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span></span>|<span data-ttu-id="0e628-141">Zawiera opis funkcji Win32 API do pracy z danymi FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="0e628-141">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|<span data-ttu-id="0e628-142">[FILESTREAM i inne funkcje serwera SQL](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0e628-142">[FILESTREAM and Other SQL Server Features](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span></span>|<span data-ttu-id="0e628-143">Udostępnia zagadnienia, wskazówki i ograniczenia dotyczące używania danych FILESTREAM z innymi funkcjami programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0e628-143">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0e628-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e628-144">See Also</span></span>  
 [<span data-ttu-id="0e628-145">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0e628-145">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="0e628-146">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0e628-146">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="0e628-147">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0e628-147">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [<span data-ttu-id="0e628-148">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="0e628-148">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="0e628-149">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="0e628-149">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
