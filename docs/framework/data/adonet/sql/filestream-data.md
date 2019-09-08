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
# <a name="filestream-data"></a>Dane FILESTREAM

Atrybut magazynu FILESTREAM jest przeznaczony dla danych binarnych (BLOB) przechowywanych w kolumnie varbinary (max). Przed FILESTREAM przechowywanie danych binarnych wymagało specjalnej obsługi. Dane bez struktury, takie jak dokumenty tekstowe, obrazy i wideo, często są przechowywane poza bazą danych, co utrudnia zarządzanie nimi.

> [!NOTE]
> Aby można było korzystać z danych FILESTREAM przy użyciu programu SqlClient, należy zainstalować .NET Framework 3,5 SP1 (lub nowsze).

Określenie atrybutu FILESTREAM w kolumnie varbinary (max) powoduje, że SQL Server do przechowywania danych w lokalnym systemie plików NTFS, a nie w pliku bazy danych. Chociaż jest przechowywany oddzielnie, można użyć tych samych instrukcji języka Transact-SQL, które są obsługiwane do pracy z danymi typu varbinary (max) przechowywanymi w bazie danych programu.

## <a name="sqlclient-support-for-filestream"></a>Obsługa SqlClient dla FILESTREAM

.NET Framework dostawca danych do SQL Server, <xref:System.Data.SqlClient>obsługuje odczytywanie i zapisywanie danych FILESTREAM <xref:System.Data.SqlTypes.SqlFileStream> przy użyciu klasy zdefiniowanej w <xref:System.Data.SqlTypes> przestrzeni nazw. `SqlFileStream`dziedziczy z <xref:System.IO.Stream> klasy, która zapewnia metody odczytu i zapisu strumieni danych. Odczyt ze strumienia przesyła dane ze strumienia do struktury danych, takiej jak tablica bajtów. Zapisanie przenosi dane ze struktury danych do strumienia.

### <a name="creating-the-sql-server-table"></a>Tworzenie tabeli SQL Server

Poniższe instrukcje języka Transact-SQL tworzą tabelę o nazwie Employees i wstawiają wiersz danych. Po włączeniu magazynu FILESTREAM można użyć tej tabeli w połączeniu z poniższymi przykładami kodu. Linki do zasobów w SQL Server książki online znajdują się na końcu tego tematu.

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

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Przykład: Odczytywanie, zastępowanie i wstawianie danych FILESTREAM

Poniższy przykład demonstruje sposób odczytywania danych z FILESTREAM. Kod pobiera ścieżkę logiczną do pliku, `FileAccess` ustawiając do `Read` i `FileOptions` do `SequentialScan`. Kod następnie odczytuje bajty z SqlFileStream do buforu. Bajty są następnie zapisywane w oknie konsoli.

W przykładzie pokazano również, jak zapisywać dane do typu FILESTREAM, w którym zostaną zastąpione wszystkie istniejące dane. Kod pobiera ścieżkę logiczną do pliku i tworzy `SqlFileStream`, `FileAccess` ustawiając ustawienia do `Write` i `FileOptions`. `SequentialScan` Pojedynczy bajt jest zapisywana `SqlFileStream`w, zastępując wszystkie dane w pliku.

W przykładzie pokazano również, jak napisać dane do obiektu FILESTREAM przy użyciu metody Seek do dołączania danych na końcu pliku. Kod pobiera ścieżkę logiczną do pliku i tworzy `SqlFileStream`, `FileAccess` ustawiając ustawienia do `ReadWrite` i `FileOptions`. `SequentialScan` Kod używa metody Seek, aby przejść do końca pliku, dołączając pojedynczy bajt do istniejącego pliku.

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

Aby uzyskać inny przykład, zobacz [Jak przechowywać i pobierać dane binarne do kolumny strumień pliku](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).

## <a name="resources-in-sql-server-books-online"></a>Zasoby w SQL Server książki online

Kompletna dokumentacja dotycząca usługi FILESTREAM znajduje się w następujących sekcjach w temacie SQL Server Books Online.

|Temat|Opis|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](/sql/relational-databases/blob/filestream-sql-server)|Opisuje, kiedy używać magazynu FILESTREAM i jak integruje aparat bazy danych SQL Server z systemem plików NTFS.|
|[Tworzenie aplikacji klienckich dla danych FILESTREAM](/sql/relational-databases/blob/create-client-applications-for-filestream-data)|Opisuje funkcje interfejsu API systemu Windows do pracy z danymi FILESTREAM.|
|[FILESTREAM i inne funkcje SQL Server](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|Zawiera zagadnienia, wytyczne i ograniczenia dotyczące używania danych FILESTREAM z innymi funkcjami SQL Server.|

## <a name="see-also"></a>Zobacz także

- [Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../retrieving-and-modifying-data.md)
- [Zabezpieczenia dostępu kodu i ADO.NET](../code-access-security.md)
- [Dane binarne i dużej wartości w programie SQL Server](sql-server-binary-and-large-value-data.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
