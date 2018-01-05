---
title: Danych FILESTREAM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 77d6dbafc5a7c3afd9998fd8e9ae54ce60f90a45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="filestream-data"></a>Danych FILESTREAM
Atrybutu magazynowania FILESTREAM jest dla danych binarnych (BLOB) przechowywanych w kolumnie varbinary(max). Przed FILESTREAM przechowywanie danych binarnych wymaga specjalnej obsługi. Dane niemające struktury, takich jak dokumenty tekst, obrazy i wideo, jest często przechowywane poza bazą danych, co utrudnia zarządzanie.  
  
> [!NOTE]
>  .NET Framework 3.5 z dodatkiem SP1 należy zainstalować (lub nowsza) do pracy z danymi FILESTREAM przy użyciu SqlClient.  
  
 Określenie atrybut FILESTREAM kolumny varbinary(max) powoduje [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] do przechowywania danych na lokalnego systemu plików NTFS zamiast w pliku bazy danych. Mimo że jest on przechowywany oddzielnie, można używać tego samego [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, które są obsługiwane w przypadku pracy z danymi varbinary(max), który jest przechowywany w bazie danych.  
  
## <a name="sqlclient-support-for-filestream"></a>Obsługa SqlClient FILESTREAM  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Dostawcy danych dla [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, obsługuje Odczyt i zapis danych FILESTREAM przy użyciu <xref:System.Data.SqlTypes.SqlFileStream> klas zdefiniowanych w <xref:System.Data.SqlTypes> przestrzeni nazw. `SqlFileStream`dziedziczy <xref:System.IO.Stream> klasy, która udostępnia metody odczytu i zapisu do strumieni danych. Odczytywanie ze strumienia przesyła dane ze strumienia do struktury danych, takich jak tablicę bajtów. Zapisywanie przesyła dane ze struktury danych w strumieniu.  
  
### <a name="creating-the-includessnoversionincludesssnoversion-mdmd-table"></a>Tworzenie [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] tabeli  
 Następujące [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcje tworzy tabela o nazwie pracowników i wstawia wiersz danych. Po włączeniu magazynowania FILESTREAM, można użyć tej tabeli w połączeniu z przykładów kodu, które należy wykonać. Linki do zasobów w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online znajdują się na końcu tego tematu.  
  
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
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Przykład: Odczyt, zastępowanie i wstawianie danych FILESTREAM  
 W poniższym przykładzie pokazano, jak można odczytać danych z FILESTREAM. Ten kod pobiera logicznej ścieżkę do pliku, ustawienie `FileAccess` do `Read` i `FileOptions` do `SequentialScan`. Ten kod odczytuje następnie bajtów z SqlFileStream w buforze. Bajty następnie są zapisywane w oknie konsoli.  
  
 Próbka również pokazuje, jak zapisać danych FILESTREAM, w którym jest zastąpienie wszystkich istniejących danych. Ten kod pobiera logicznej ścieżkę do pliku i tworzy `SqlFileStream`, ustawienie `FileAccess` do `Write` i `FileOptions` do `SequentialScan`. Pojedynczy bajt jest zapisywany w `SqlFileStream`, zastępując żadnych danych w pliku.  
  
 Próbki także przedstawiono sposób zapisywania danych FILESTREAM przy użyciu metody wyszukiwania, aby dołączyć dane do końca pliku. Ten kod pobiera logicznej ścieżkę do pliku i tworzy `SqlFileStream`, ustawienie `FileAccess` do `ReadWrite` i `FileOptions` do `SequentialScan`. Kod używa metody Seek się na końcu pliku, dołączenie jednobajtowych do istniejącego pliku.  
  
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
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
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
} using (SqlConnection connection = new SqlConnection(  
    connStringBuilder.ToString()))  
{  
    connection.Open();  
  
    SqlCommand command = new SqlCommand("", connection);  
    command.CommandText = "select Top(1) Photo.PathName(), "  
    + "GET_FILESTREAM_TRANSACTION_CONTEXT () from employees";  
  
    SqlTransaction tran = connection.BeginTransaction(  
        System.Data.IsolationLevel.ReadCommitted);  
    command.Transaction = tran;  
  
    using (SqlDataReader reader = command.ExecuteReader())  
    {  
        while (reader.Read())  
        {  
            // Get the pointer for file  
            string path = reader.GetString(0);  
            byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
            FileStream fileStream = new SqlFileStream(path,  
                (byte[])reader.GetValue(1),  
                FileAccess.ReadWrite,  
                FileOptions.SequentialScan, 0);  
  
            // Seek to the end of the file  
            fs.Seek(0, SeekOrigin.End);  
  
            // Append a single byte   
            fileStream.WriteByte(0x01);  
            fileStream.Close();  
        }  
    }  
    tran.Commit();  
}  
```  
  
 Inny przykład, zobacz [sposób przechowywania i pobierania danych binarnych do kolumny strumienia pliku](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).  
  
## <a name="resources-in-includessnoversionincludesssnoversion-mdmd-books-online"></a>Zasoby w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online  
 Pełną dokumentację dla FILESTREAM znajduje się w następujących sekcjach w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Projektowanie i implementowanie magazynowania FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)|Zawiera linki do dokumentacji FILESTREAM i Tematy pokrewne.|  
|[Omówienie FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)|Opisuje, kiedy należy używać magazynowania FILESTREAM i sposobu integracji aparatu bazy danych programu SQL Server w systemie plików NTFS.|  
|[Wprowadzenie do magazynowania FILESTREAM](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)|Opisuje, jak włączyć funkcję FILESTREAM w wystąpieniu programu SQL Server, jak utworzyć bazę danych i tabelę, aby przechowywane dane FILESTREAM oraz manipulowanie wierszami zawierających dane FILESTREAM.|  
|[Za pomocą magazynowania FILESTREAM w aplikacjach klienckich](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)|Zawiera opis funkcji Win32 API do pracy z danymi FILESTREAM.|  
|[FILESTREAM i inne funkcje serwera SQL](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)|Udostępnia zagadnienia, wskazówki i ograniczenia dotyczące używania danych FILESTREAM z innymi funkcjami programu SQL Server.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Zabezpieczenia dostępu kodu i ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)  
 [Dane binarne i dużej wartości w programie SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
