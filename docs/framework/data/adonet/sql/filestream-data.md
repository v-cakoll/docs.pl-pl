---
title: Dane FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: 87bed5dd345c240cc00b2c36aa976ec53fe63b93
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794094"
---
# <a name="filestream-data"></a><span data-ttu-id="16936-102">Dane FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="16936-102">FILESTREAM Data</span></span>

<span data-ttu-id="16936-103">Atrybut magazynu FILESTREAM jest przeznaczony dla danych binarnych (BLOB) przechowywanych w kolumnie varbinary (max).</span><span class="sxs-lookup"><span data-stu-id="16936-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="16936-104">Przed FILESTREAM przechowywanie danych binarnych wymagało specjalnej obsługi.</span><span class="sxs-lookup"><span data-stu-id="16936-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="16936-105">Dane bez struktury, takie jak dokumenty tekstowe, obrazy i wideo, często są przechowywane poza bazą danych, co utrudnia zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="16936-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>

> [!NOTE]
> <span data-ttu-id="16936-106">Aby można było korzystać z danych FILESTREAM przy użyciu programu SqlClient, należy zainstalować .NET Framework 3,5 SP1 (lub nowsze).</span><span class="sxs-lookup"><span data-stu-id="16936-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>

<span data-ttu-id="16936-107">Określenie atrybutu FILESTREAM w kolumnie varbinary (max) powoduje, że SQL Server do przechowywania danych w lokalnym systemie plików NTFS, a nie w pliku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="16936-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes SQL Server to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="16936-108">Chociaż jest przechowywany oddzielnie, można użyć tych samych instrukcji języka Transact-SQL, które są obsługiwane do pracy z danymi typu varbinary (max) przechowywanymi w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="16936-108">Although it is stored separately, you can use the same Transact-SQL statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>

## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="16936-109">Obsługa SqlClient dla FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="16936-109">SqlClient Support for FILESTREAM</span></span>

<span data-ttu-id="16936-110">.NET Framework dostawca danych do SQL Server, <xref:System.Data.SqlClient>obsługuje odczytywanie i zapisywanie danych FILESTREAM <xref:System.Data.SqlTypes.SqlFileStream> przy użyciu klasy zdefiniowanej w <xref:System.Data.SqlTypes> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="16936-110">The .NET Framework Data Provider for SQL Server, <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="16936-111">`SqlFileStream`dziedziczy z <xref:System.IO.Stream> klasy, która zapewnia metody odczytu i zapisu strumieni danych.</span><span class="sxs-lookup"><span data-stu-id="16936-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="16936-112">Odczyt ze strumienia przesyła dane ze strumienia do struktury danych, takiej jak tablica bajtów.</span><span class="sxs-lookup"><span data-stu-id="16936-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="16936-113">Zapisanie przenosi dane ze struktury danych do strumienia.</span><span class="sxs-lookup"><span data-stu-id="16936-113">Writing transfers the data from the data structure into a stream.</span></span>

### <a name="creating-the-sql-server-table"></a><span data-ttu-id="16936-114">Tworzenie tabeli SQL Server</span><span class="sxs-lookup"><span data-stu-id="16936-114">Creating the SQL Server Table</span></span>

<span data-ttu-id="16936-115">Poniższe instrukcje języka Transact-SQL tworzą tabelę o nazwie Employees i wstawiają wiersz danych.</span><span class="sxs-lookup"><span data-stu-id="16936-115">The following Transact-SQL statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="16936-116">Po włączeniu magazynu FILESTREAM można użyć tej tabeli w połączeniu z poniższymi przykładami kodu.</span><span class="sxs-lookup"><span data-stu-id="16936-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="16936-117">Linki do zasobów w SQL Server książki online znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="16936-117">The links to resources in SQL Server Books Online are located at the end of this topic.</span></span>

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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="16936-118">Przykład: Odczytywanie, zastępowanie i wstawianie danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="16936-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>

<span data-ttu-id="16936-119">Poniższy przykład demonstruje sposób odczytywania danych z FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="16936-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="16936-120">Kod pobiera ścieżkę logiczną do pliku, `FileAccess` ustawiając do `Read` i `FileOptions` do `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="16936-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="16936-121">Kod następnie odczytuje bajty z SqlFileStream do buforu.</span><span class="sxs-lookup"><span data-stu-id="16936-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="16936-122">Bajty są następnie zapisywane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="16936-122">The bytes are then written to the console window.</span></span>

<span data-ttu-id="16936-123">W przykładzie pokazano również, jak zapisywać dane do typu FILESTREAM, w którym zostaną zastąpione wszystkie istniejące dane.</span><span class="sxs-lookup"><span data-stu-id="16936-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="16936-124">Kod pobiera ścieżkę logiczną do pliku i tworzy `SqlFileStream`, `FileAccess` ustawiając ustawienia do `Write` i `FileOptions`. `SequentialScan`</span><span class="sxs-lookup"><span data-stu-id="16936-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="16936-125">Pojedynczy bajt jest zapisywana `SqlFileStream`w, zastępując wszystkie dane w pliku.</span><span class="sxs-lookup"><span data-stu-id="16936-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>

<span data-ttu-id="16936-126">W przykładzie pokazano również, jak napisać dane do obiektu FILESTREAM przy użyciu metody Seek do dołączania danych na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="16936-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="16936-127">Kod pobiera ścieżkę logiczną do pliku i tworzy `SqlFileStream`, `FileAccess` ustawiając ustawienia do `ReadWrite` i `FileOptions`. `SequentialScan`</span><span class="sxs-lookup"><span data-stu-id="16936-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="16936-128">Kod używa metody Seek, aby przejść do końca pliku, dołączając pojedynczy bajt do istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="16936-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>

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

<span data-ttu-id="16936-129">Aby uzyskać inny przykład, zobacz [Jak przechowywać i pobierać dane binarne do kolumny strumień pliku](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="16936-129">For another sample, see [How to store and fetch binary data into a file stream column](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>

## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="16936-130">Zasoby w SQL Server książki online</span><span class="sxs-lookup"><span data-stu-id="16936-130">Resources in SQL Server Books Online</span></span>

<span data-ttu-id="16936-131">Kompletna dokumentacja dotycząca usługi FILESTREAM znajduje się w następujących sekcjach w temacie SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="16936-131">The complete documentation for FILESTREAM is located in the following sections in SQL Server Books Online.</span></span>

|<span data-ttu-id="16936-132">Temat</span><span class="sxs-lookup"><span data-stu-id="16936-132">Topic</span></span>|<span data-ttu-id="16936-133">Opis</span><span class="sxs-lookup"><span data-stu-id="16936-133">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="16936-134">FILESTREAM (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="16936-134">FILESTREAM (SQL Server)</span></span>](/sql/relational-databases/blob/filestream-sql-server)|<span data-ttu-id="16936-135">Opisuje, kiedy używać magazynu FILESTREAM i jak integruje aparat bazy danych SQL Server z systemem plików NTFS.</span><span class="sxs-lookup"><span data-stu-id="16936-135">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|
|[<span data-ttu-id="16936-136">Tworzenie aplikacji klienckich dla danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="16936-136">Create Client Applications for FILESTREAM Data</span></span>](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|<span data-ttu-id="16936-137">Opisuje funkcje interfejsu API systemu Windows do pracy z danymi FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="16936-137">Describes the Windows API functions for working with FILESTREAM data.</span></span>|
|[<span data-ttu-id="16936-138">FILESTREAM i inne funkcje SQL Server</span><span class="sxs-lookup"><span data-stu-id="16936-138">FILESTREAM and Other SQL Server Features</span></span>](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|<span data-ttu-id="16936-139">Zawiera zagadnienia, wytyczne i ograniczenia dotyczące używania danych FILESTREAM z innymi funkcjami SQL Server.</span><span class="sxs-lookup"><span data-stu-id="16936-139">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|

## <a name="see-also"></a><span data-ttu-id="16936-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16936-140">See also</span></span>

- [<span data-ttu-id="16936-141">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16936-141">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="16936-142">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16936-142">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="16936-143">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16936-143">Code Access Security and ADO.NET</span></span>](../code-access-security.md)
- [<span data-ttu-id="16936-144">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="16936-144">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="16936-145">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16936-145">ADO.NET Overview</span></span>](../ado-net-overview.md)
