---
title: Pojedyncze operacje kopiowania zbiorczego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 274a6e87b272002a567fd92605c4e690c03b6e26
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565175"
---
# <a name="single-bulk-copy-operations"></a>Pojedyncze operacje kopiowania zbiorczego
Najprostszą metodą do wykonywania operacji kopiowania zbiorczego SQL Server jest na wykonanie jednej operacji w bazie danych. Domyślnie operacji kopiowania zbiorczego jest wykonywane jako operacja izolowane: operacja kopiowania odbywa się w sposób nietransakcyjnej ma możliwości, aby przerzucić go na tworzeniu kopii.  
  
> [!NOTE]
>  Jeśli musisz wycofać całość lub część kopiowania masowego po wystąpieniu błędu, można użyć <xref:System.Data.SqlClient.SqlBulkCopy>-managed transakcji lub wykonywać operacji kopiowania zbiorczego w ramach istniejącej transakcji. **SqlBulkCopy** współdziałają z usługą <xref:System.Transactions> Jeśli połączenie jest zarejestrowany (jawnie lub niejawnie) na **System.Transactions** transakcji.  
>   
>  Aby uzyskać więcej informacji, zobacz [transakcja i operacje kopiowania masowego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).  
  
 Ogólne kroki umożliwiające wykonywanie operacji kopiowania zbiorczego są następujące:  
  
1.  Połącz się na serwerze źródłowym i uzyskać dane do skopiowania. Dane mogą pochodzić również z innych źródeł, jeśli można go pobrać z <xref:System.Data.IDataReader> lub <xref:System.Data.DataTable> obiektu.  
  
2.  Połączenie z serwerem docelowym (chyba że chcesz **SqlBulkCopy** ustanowić połączenie dla Ciebie).  
  
3.  Utwórz <xref:System.Data.SqlClient.SqlBulkCopy> obiektu, ustawienie wszelkie wymagane właściwości.  
  
4.  Ustaw **DestinationTableName** operacji wstawiania właściwości, aby wskazać, tabela docelowa dla zbiorczego.  
  
5.  Wywołanie jednej z **WriteToServer** metody.  
  
6.  Opcjonalnie można zaktualizować właściwości i wywołania **WriteToServer** ponownie zgodnie z potrzebami.  
  
7.  Wywołaj <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, lub zawijania operacje kopiowania masowego w ramach `Using` instrukcji.  
  
> [!CAUTION]
>  Zaleca się, że są zgodne typy danych kolumn źródłowych i docelowych. Jeśli nie są zgodne z typami danych, **SqlBulkCopy** stara się przekonwertować wartość każdego źródłowego na docelowy typ danych, za pomocą reguł stosowanych przez <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Konwersje może wpłynąć na wydajność, a także może spowodować nieoczekiwane błędy. Na przykład `Double` można przekonwertować na typ danych `Decimal` — typ danych większość czasu, ale nie zawsze.  
  
## <a name="example"></a>Przykład  
 Następująca aplikacja konsoli Pokazuje, jak załadować dane przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy. W tym przykładzie <xref:System.Data.SqlClient.SqlDataReader> służy do kopiowania danych z **Production.Product** tabeli w programie SQL Server**AdventureWorks** bazy danych do tabeli podobne w tej samej bazy danych.  
  
> [!IMPORTANT]
>  W tym przykładzie nie będzie działać, chyba że utworzonego tabelami pracy zgodnie z opisem w [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zademonstrowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze użyj instrukcji Transact-SQL `INSERT … SELECT` instrukcję, aby skopiować dane.  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Wykonywanie operacji kopiowania zbiorczego, przy użyciu języka Transact-SQL i klasy poleceń  
 Poniższy przykład ilustruje sposób używania <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody, które można wykonać instrukcji BULK INSERT.  
  
> [!NOTE]
>  Ścieżka pliku źródła danych jest określana względem serwera. Proces serwera musi mieć dostęp do tej ścieżki, aby jako warunek powodzenia operacji kopiowania zbiorczego.  
  
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
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
