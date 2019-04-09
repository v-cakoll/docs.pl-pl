---
title: DbConnection, DbCommand i DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 759b2f36f9d38cdac0cfe4ff8e451b38012493e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143835"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand i DbException
Po utworzeniu <xref:System.Data.Common.DbProviderFactory> i <xref:System.Data.Common.DbConnection>, następnie można pracować z czytniki danych i polecenia do pobierania danych ze źródła danych.  
  
## <a name="retrieving-data-example"></a>Przykład pobierania danych  
 W tym przykładzie pobiera `DbConnection` obiektu jako argumentu. A <xref:System.Data.Common.DbCommand> zostanie utworzony, aby wybrać dane z tabeli Kategorie, ustawiając <xref:System.Data.Common.DbCommand.CommandText%2A> do instrukcji SQL SELECT. W kodzie założono, że tabela kategorie istnieje w źródle danych. Połączenie jest otwarte, a dane są pobierane za pomocą <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Przykład polecenia wykonywania  
 W tym przykładzie pobiera `DbConnection` obiektu jako argumentu. Jeśli `DbConnection` jest prawidłowy, połączenie jest otwarte i <xref:System.Data.Common.DbCommand> zostanie utworzony i wykonywane. <xref:System.Data.Common.DbCommand.CommandText%2A> Jest ustawiony do instrukcji SQL INSERT, który wykonuje wstawiania do tabeli Kategorie w bazie danych Northwind. W kodzie założono, że bazy danych Northwind istnieje w źródle danych i czy składnia SQL używane w instrukcji INSERT jest prawidłowa dla określonego dostawcy. Błędy występujące w źródle danych są obsługiwane przez <xref:System.Data.Common.DbException> blok kodu i inne wyjątki są obsługiwane w <xref:System.Exception> bloku.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Obsługa błędów danych za pomocą DbException  
 <xref:System.Data.Common.DbException> Klasa jest klasą bazową dla wszystkich wyjątków generowanych w imieniu źródła danych. Można użyć go w swojej kodu obsługi wyjątków aby obsłużyć wyjątki wyrzucane przez różnych dostawców bez potrzeby odwołuje się do klasy określonego wyjątku. Poniższy fragment kodu pokazuje sposób użycia <xref:System.Data.Common.DbException> Aby wyświetlić informacje o błędzie zwrócony przy użyciu źródła danych <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, i <xref:System.Exception.Message%2A> właściwości. Dane wyjściowe będą wyświetlane typ błędu, źródło wskazującą nazwę dostawcy, kod błędu oraz komunikat skojarzony z powodu błędu.  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Uzyskiwanie DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [Modyfikowanie danych za pomocą obiektu DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
