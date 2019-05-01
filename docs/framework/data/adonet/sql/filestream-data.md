---
title: Dane FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 1dea5d1e2f40c44e8f24bdbc9742288429d9933a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032490"
---
# <a name="filestream-data"></a><span data-ttu-id="540ee-102">Dane FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="540ee-102">FILESTREAM Data</span></span>

<span data-ttu-id="540ee-103">Atrybutu magazynowania FILESTREAM jest dla danych binarnych (BLOB) przechowywanego w kolumny typu varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="540ee-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="540ee-104">Przed FILESTREAM przechowywanie danych binarnych wymaga specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="540ee-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="540ee-105">Danych niestrukturalnych, takich jak dokumenty tekstowe, obrazy i wideo, często są przechowywane poza bazą danych, co utrudnia do zarządzania.</span><span class="sxs-lookup"><span data-stu-id="540ee-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="540ee-106">Należy zainstalować .NET Framework 3.5 z dodatkiem SP1 (lub nowszym) do pracy z danymi FILESTREAM przy użyciu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="540ee-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="540ee-107">Określając atrybut FILESTREAM kolumny typu varbinary(max) powoduje, że program SQL Server do przechowywania danych na lokalny system plików NTFS zamiast w pliku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="540ee-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="540ee-108">Chociaż były przechowywane osobno, możesz użyć takie same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, które są obsługiwane w przypadku pracy z danymi varbinary(max), która jest przechowywana w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="540ee-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="540ee-109">Obsługa SqlClient dla FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="540ee-109">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="540ee-110">[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Dostawcy danych programu SQL Server <xref:System.Data.SqlClient>, obsługuje Odczyt i zapis danych FILESTREAM przy użyciu <xref:System.Data.SqlTypes.SqlFileStream> klasy zdefiniowanej w <xref:System.Data.SqlTypes> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="540ee-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="540ee-111">`SqlFileStream` dziedziczy <xref:System.IO.Stream> klasy, która zawiera metody służące do odczytu i zapisu do strumieni danych.</span><span class="sxs-lookup"><span data-stu-id="540ee-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="540ee-112">Odczyt ze strumienia przesyła dane ze strumienia do struktury danych, takich jak tablica bajtów.</span><span class="sxs-lookup"><span data-stu-id="540ee-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="540ee-113">Zapisywanie przesyła dane z struktury danych w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="540ee-113">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="540ee-114">Tworzenie tabeli programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="540ee-114">Creating the SQL Server Table</span></span>

<span data-ttu-id="540ee-115">Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji tworzy tabelę o nazwie Pracownicy i wstawia wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="540ee-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="540ee-116">Po włączeniu magazynowania FILESTREAM można użyć tej tabeli, w połączeniu z przykładami kodu, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="540ee-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="540ee-117">Na końcu tego tematu znajdują się linki do zasobów programu SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="540ee-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

```sql
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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="540ee-118">Przykład: Odczytanie, zastępowanie i wstawianie danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="540ee-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="540ee-119">Poniższy przykład pokazuje, jak można odczytać danych z FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="540ee-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="540ee-120">Kod pobiera logiczne ścieżkę do pliku, ustawianie `FileAccess` do `Read` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="540ee-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="540ee-121">Kod następnie odczytuje bajtów z SqlFileStream w buforze.</span><span class="sxs-lookup"><span data-stu-id="540ee-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="540ee-122">Bajty są następnie zapisywane do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="540ee-122">The bytes are then written to the console window.</span></span>

<span data-ttu-id="540ee-123">W przykładzie pokazano również sposób zapisywania danych FILESTREAM, w którym wszystkie istniejące dane zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="540ee-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="540ee-124">Ten kod pobiera logiczne ścieżkę do pliku i tworzy `SqlFileStream`, ustawiając `FileAccess` do `Write` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="540ee-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="540ee-125">Jednobajtowych są zapisywane do `SqlFileStream`, zastępując wszystkie dane w pliku.</span><span class="sxs-lookup"><span data-stu-id="540ee-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="540ee-126">W przykładzie pokazano również sposób zapisywania danych FILESTREAM przy użyciu metody wyszukiwania, aby dołączyć dane do końca pliku.</span><span class="sxs-lookup"><span data-stu-id="540ee-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="540ee-127">Ten kod pobiera logiczne ścieżkę do pliku i tworzy `SqlFileStream`, ustawiając `FileAccess` do `ReadWrite` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="540ee-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="540ee-128">Kod używa metody wyszukiwania do wyszukania na końcu pliku, dodając jednobajtowych do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="540ee-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

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
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
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

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
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

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
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

<span data-ttu-id="540ee-129">Aby uzyskać inny przykład, zobacz [jak przechowywać i pobierać dane binarne do kolumny strumienia pliku](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="540ee-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="540ee-130">Zasoby programu SQL Server — książki Online</span><span class="sxs-lookup"><span data-stu-id="540ee-130">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="540ee-131">Pełną dokumentację dla FILESTREAM znajduje się w następujących sekcjach w dokumentacji SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="540ee-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="540ee-132">Temat</span><span class="sxs-lookup"><span data-stu-id="540ee-132">Topic</span></span>|<span data-ttu-id="540ee-133">Opis</span><span class="sxs-lookup"><span data-stu-id="540ee-133">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="540ee-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="540ee-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="540ee-135">Opisuje, kiedy należy używać magazynowania FILESTREAM i sposobu integracji aparatu bazy danych programu SQL Server w systemie plików NTFS.</span><span class="sxs-lookup"><span data-stu-id="540ee-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="540ee-136">Tworzenie aplikacji klienckich dla danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="540ee-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="540ee-137">Opisuje funkcje interfejsu Windows API do pracy z danymi FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="540ee-137">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="540ee-138">FILESTREAM i inne funkcje serwera SQL</span><span class="sxs-lookup"><span data-stu-id="540ee-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="540ee-139">Zawiera zagadnienia, wytyczne i ograniczenia dotyczące używania danych FILESTREAM z innymi funkcjami programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="540ee-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="540ee-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="540ee-140">See also</span></span>

- [<span data-ttu-id="540ee-141">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="540ee-141">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [<span data-ttu-id="540ee-142">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="540ee-142">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="540ee-143">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="540ee-143">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="540ee-144">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="540ee-144">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="540ee-145">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="540ee-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
