---
title: Dane FILESTREAM
ms.date: 03/30/2017
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.openlocfilehash: eef03d171d288cb2bc62c3aaa477a95a5ce718c3
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130607"
---
# <a name="filestream-data"></a>Dane FILESTREAM
Atrybutu magazynowania FILESTREAM jest dla danych binarnych (BLOB) przechowywanego w kolumny typu varbinary(max). Przed FILESTREAM przechowywanie danych binarnych wymaga specjalnej obsługi. Danych niestrukturalnych, takich jak dokumenty tekstowe, obrazy i wideo, często są przechowywane poza bazą danych, co utrudnia do zarządzania.  
  
> [!NOTE]
>  Należy zainstalować .NET Framework 3.5 z dodatkiem SP1 (lub nowszym) do pracy z danymi FILESTREAM przy użyciu SqlClient.  
  
 Określając atrybut FILESTREAM kolumny typu varbinary(max) powoduje, że program SQL Server do przechowywania danych na lokalny system plików NTFS zamiast w pliku bazy danych. Chociaż były przechowywane osobno, możesz użyć takie same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, które są obsługiwane w przypadku pracy z danymi varbinary(max), która jest przechowywana w bazie danych.  
  
## <a name="sqlclient-support-for-filestream"></a>Obsługa SqlClient dla FILESTREAM  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Dostawcy danych programu SQL Server <xref:System.Data.SqlClient>, obsługuje Odczyt i zapis danych FILESTREAM przy użyciu <xref:System.Data.SqlTypes.SqlFileStream> klasy zdefiniowanej w <xref:System.Data.SqlTypes> przestrzeni nazw. `SqlFileStream` dziedziczy <xref:System.IO.Stream> klasy, która zawiera metody służące do odczytu i zapisu do strumieni danych. Odczyt ze strumienia przesyła dane ze strumienia do struktury danych, takich jak tablica bajtów. Zapisywanie przesyła dane z struktury danych w strumieniu.  
  
### <a name="creating-the-sql-server-table"></a>Tworzenie tabeli programu SQL Server  
 Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji tworzy tabelę o nazwie Pracownicy i wstawia wiersz danych. Po włączeniu magazynowania FILESTREAM można użyć tej tabeli, w połączeniu z przykładami kodu, które należy wykonać. Na końcu tego tematu znajdują się linki do zasobów programu SQL Server — książki Online.  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Przykład: Odczytu, zastępowanie i wstawianie danych FILESTREAM  
 Poniższy przykład pokazuje, jak można odczytać danych z FILESTREAM. Kod pobiera logiczne ścieżkę do pliku, ustawianie `FileAccess` do `Read` i `FileOptions` do `SequentialScan`. Kod następnie odczytuje bajtów z SqlFileStream w buforze. Bajty są następnie zapisywane do okna konsoli.  
  
 W przykładzie pokazano również sposób zapisywania danych FILESTREAM, w którym wszystkie istniejące dane zostaną zastąpione. Ten kod pobiera logiczne ścieżkę do pliku i tworzy `SqlFileStream`, ustawiając `FileAccess` do `Write` i `FileOptions` do `SequentialScan`. Jednobajtowych są zapisywane do `SqlFileStream`, zastępując wszystkie dane w pliku.  
  
 W przykładzie pokazano również sposób zapisywania danych FILESTREAM przy użyciu metody wyszukiwania, aby dołączyć dane do końca pliku. Ten kod pobiera logiczne ścieżkę do pliku i tworzy `SqlFileStream`, ustawiając `FileAccess` do `ReadWrite` i `FileOptions` do `SequentialScan`. Kod używa metody wyszukiwania do wyszukania na końcu pliku, dodając jednobajtowych do istniejącego pliku.  
  
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
  
 Aby uzyskać inny przykład, zobacz [jak przechowywać i pobierać dane binarne do kolumny strumienia pliku](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).  
  
## <a name="resources-in-sql-server-books-online"></a>Zasoby programu SQL Server — książki Online  
 Pełną dokumentację dla FILESTREAM znajduje się w następujących sekcjach w dokumentacji SQL Server — książki Online.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Projektowanie i implementowanie magazynowania FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)|Zawiera łącza do dokumentacji FILESTREAM i Tematy pokrewne.|  
|[Omówienie FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)|Opisuje, kiedy należy używać magazynowania FILESTREAM i sposobu integracji aparatu bazy danych programu SQL Server w systemie plików NTFS.|  
|[Wprowadzenie do magazynowania FILESTREAM](https://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)|W tym artykule opisano, jak włączyć funkcję FILESTREAM w wystąpieniu programu SQL Server, jak utworzyć bazę danych i tabelę, do przechowywanych danych FILESTREAM i sposoby manipulowania wiersze zawierające dane FILESTREAM.|  
|[Za pomocą magazynowania FILESTREAM w aplikacjach klienckich](https://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)|Zawiera opis funkcji Win32 API do pracy z danymi FILESTREAM.|  
|[FILESTREAM i inne funkcje serwera SQL](/sql/relational-databases/blob/filestream-compatibility-with-other-sql-server-features)|Zawiera zagadnienia, wytyczne i ograniczenia dotyczące używania danych FILESTREAM z innymi funkcjami programu SQL Server.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [Dane binarne i dużej wartości w programie SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
