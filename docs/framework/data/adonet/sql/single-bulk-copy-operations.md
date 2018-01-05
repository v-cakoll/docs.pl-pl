---
title: Operacje kopiowania masowego pojedynczego
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 03b255f92ed7123c14116e148f23571d21561bfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="single-bulk-copy-operations"></a>Operacje kopiowania masowego pojedynczego
Najprostsza metoda wykonywanie operacji kopiowania zbiorczego SQL Server jest na wykonanie jednej operacji na bazie danych. Domyślnie kopiowania masowego odbywa się jako operacja izolowanego: operacja kopiowania odbywa się w sposób obsługi nietransakcyjnego z udostępnieniem jej nie możliwości tworzenia kopii.  
  
> [!NOTE]
>  Jeśli chcesz wycofać całość lub część kopiowania zbiorczego po wystąpieniu błędu, można użyć <xref:System.Data.SqlClient.SqlBulkCopy>-zarządzane transakcji lub wykonania operacji kopiowania zbiorczego w istniejącej transakcji. **SqlBulkCopy** będzie również współpracować z <xref:System.Transactions> Jeśli połączenie jest zarejestrowane (jawnie ani niejawnie) do **System.Transactions** transakcji.  
>   
>  Aby uzyskać więcej informacji, zobacz [transakcji i operacje kopiowania masowego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 Ogólne kroki do wykonania operacji kopiowania zbiorczego są następujące:  
  
1.  Nawiąż połączenie z serwerem źródłowym i uzyskać dane do skopiowania. Dane mogą również pochodzić z innych źródeł, jeśli będzie można pobrać z <xref:System.Data.IDataReader> lub <xref:System.Data.DataTable> obiektu.  
  
2.  Nawiąż połączenie z serwerem docelowym (chyba że chcesz **SqlBulkCopy** ustanowić połączenie dla Ciebie).  
  
3.  Utwórz <xref:System.Data.SqlClient.SqlBulkCopy> obiektu wszelkie wymagane właściwości.  
  
4.  Ustaw **DestinationTableName** Właściwość wskazująca tabeli docelowej do zbiorczego operacji wstawiania.  
  
5.  Wywoływanie jednego z **WriteToServer** metody.  
  
6.  Opcjonalnie, zaktualizuj właściwości i wywołanie **WriteToServer** ponownie w razie potrzeby.  
  
7.  Wywołanie <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, lub zawijać operacji kopiowania zbiorczego w obrębie `Using` instrukcji.  
  
> [!CAUTION]
>  Zaleca się, że typy danych kolumn źródłowa i docelowa są zgodne. Jeśli typy danych są niezgodne, **SqlBulkCopy** próbuje przekonwertować wartości każdego źródłowego na docelowy typ danych, przy użyciu reguł stosowanych przez <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Konwersje może wpłynąć na wydajność, a także może spowodować nieoczekiwane błędy. Na przykład `Double` można przekonwertować na typ danych `Decimal` większość typów danych o czasie, ale nie zawsze.  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji konsoli Pokazuje, jak załadować dane przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy. W tym przykładzie <xref:System.Data.SqlClient.SqlDataReader> służy do kopiowania danych z **Production.Product** tabeli w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] **AdventureWorks** bazy danych do tabeli podobne w tej samej bazy danych.  
  
> [!IMPORTANT]
>  W tym przykładzie nie będzie działać, jeśli nie utworzono tabel roboczych zgodnie z opisem w [Instalatora przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zaprezentowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze do używania języka Transact-SQL `INSERT … SELECT` instrukcji, aby skopiować dane.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Wykonywanie operacji kopiowania zbiorczego przy użyciu języka Transact-SQL i klasy poleceń  
 Poniższy przykład przedstawia sposób użycia <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metodę można wykonać instrukcji BULK INSERT.  
  
> [!NOTE]
>  Ścieżka pliku źródła danych jest określana względem serwera. Proces serwera musi mieć dostęp do tej ścieżki w kolejności dla operacji kopiowania zbiorczego powiodło się.  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje kopiowania masowego w programie SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
