---
title: Pojedyncze operacje kopiowania zbiorczego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 07c705b9daeeb043ef36f1e3272a3bf259a3c23e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043880"
---
# <a name="single-bulk-copy-operations"></a>Pojedyncze operacje kopiowania zbiorczego

Najprostszym podejściem do wykonywania SQL Server operacji kopiowania zbiorczego jest wykonanie pojedynczej operacji w bazie danych. Domyślnie operacja kopiowania zbiorczego jest wykonywana jako operacja izolowana: operacja kopiowania odbywa się w sposób nietransakcyjny, bez możliwości przywrócenia jej z powrotem.

> [!NOTE]
> Jeśli chcesz wycofać całość lub część kopiowania zbiorczego, gdy wystąpi błąd, możesz użyć <xref:System.Data.SqlClient.SqlBulkCopy>transakcji zarządzanej lub wykonać operację kopiowania zbiorczego w ramach istniejącej transakcji. **SqlBulkCopy** również będzie współdziałać z usługą <xref:System.Transactions> , jeśli połączenie zostanie zarejestrowane (niejawnie lub jawnie) w transakcji **System. Transactions** .
>
> Aby uzyskać więcej informacji, zobacz [operacje transakcji i kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).

Ogólne kroki wykonywania operacji kopiowania zbiorczego są następujące:

1. Nawiąż połączenie z serwerem źródłowym i uzyskaj dane, które mają zostać skopiowane. Dane mogą również pochodzić z innych źródeł, jeśli można je pobrać z <xref:System.Data.IDataReader> obiektu lub. <xref:System.Data.DataTable>

2. Nawiąż połączenie z serwerem docelowym (chyba że chcesz, aby **SqlBulkCopy** się nawiązać połączenie).

3. <xref:System.Data.SqlClient.SqlBulkCopy> Utwórz obiekt, ustawiając wszelkie niezbędne właściwości.

4. Ustaw właściwość **DestinationTableName** , aby wskazać tabelę docelową dla operacji wstawiania zbiorczego.

5. Wywołaj jedną z metod **WriteToServer** .

6. Opcjonalnie należy zaktualizować właściwości i ponownie wywołać **WriteToServer** w razie potrzeby.

7. Wywołaj <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>lub zawiń operacje kopiowania zbiorczego `Using` w instrukcji.

> [!CAUTION]
> Zalecamy, aby typy danych kolumny źródłowej i docelowej były zgodne. Jeśli typy danych nie są zgodne, **SqlBulkCopy** próbuje skonwertować każdą wartość źródłową na docelowy typ danych przy użyciu reguł używanych przez <xref:System.Data.SqlClient.SqlParameter.Value%2A>. Konwersje mogą mieć wpływ na wydajność, a także powodować nieoczekiwane błędy. Na przykład `Double` typ danych można przekonwertować `Decimal` na typ danych w większości czasu, ale nie zawsze.

## <a name="example"></a>Przykład

W poniższej aplikacji konsolowej pokazano, <xref:System.Data.SqlClient.SqlBulkCopy> jak załadować dane przy użyciu klasy. W tym przykładzie <xref:System.Data.SqlClient.SqlDataReader> jest używany do kopiowania danych z tabeli Production **. Product** w bazie danych SQL Server **AdventureWorks** do podobnej tabeli w tej samej bazie danych.

> [!IMPORTANT]
> Ten przykład nie zostanie uruchomiony, jeśli nie utworzono tabel roboczych, zgodnie z opisem w [przykładowej konfiguracji kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany w celu przedstawienia składni tylko za pomocą **SqlBulkCopy** . Jeśli tabele źródłowe i docelowe znajdują się w tym samym wystąpieniu SQL Server, łatwiej i szybciej można używać instrukcji języka Transact-SQL `INSERT … SELECT` do kopiowania danych.

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Wykonywanie operacji kopiowania zbiorczego za pomocą języka Transact-SQL i klasy poleceń

Poniższy przykład ilustruje sposób używania <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody do wykonywania instrukcji BULK INSERT.

> [!NOTE]
> Ścieżka pliku dla źródła danych jest określana względem serwera. Proces serwera musi mieć dostęp do tej ścieżki w celu pomyślnego wykonania operacji kopiowania zbiorczego.

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

## <a name="see-also"></a>Zobacz także

- [Operacje kopiowania masowego w programie SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
