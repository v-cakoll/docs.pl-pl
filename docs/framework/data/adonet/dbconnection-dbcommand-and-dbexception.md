---
title: DbConnection, DbCommand i DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 09526f111adeecb817ce4c4e587ca3713e0d8cde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785203"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand i DbException
Po utworzeniu <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbConnection>i a można następnie korzystać z poleceń i czytników danych w celu pobierania danych ze źródła danych.  
  
## <a name="retrieving-data-example"></a>Przykład pobierania danych  
 Ten przykład pobiera `DbConnection` obiekt jako argument. Jest tworzony w celu wybrania danych z tabeli Kategorie przez <xref:System.Data.Common.DbCommand.CommandText%2A> ustawienie instrukcji SELECT języka SQL. <xref:System.Data.Common.DbCommand> W kodzie założono, że tabela kategorie istnieje w źródle danych. Połączenie jest otwierane, a dane są pobierane przy użyciu <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Wykonywanie przykładowego polecenia  
 Ten przykład pobiera `DbConnection` obiekt jako argument. Jeśli jest prawidłowy, połączenie zostanie otwarte <xref:System.Data.Common.DbCommand> i zostanie utworzone i wykonane. `DbConnection` <xref:System.Data.Common.DbCommand.CommandText%2A> Jest ustawiona na instrukcję SQL INSERT, która wykonuje Wstawianie do tabeli Categories w bazie danych Northwind. W kodzie założono, że baza danych Northwind istnieje w źródle danych i że składnia SQL używana w instrukcji INSERT jest prawidłowa dla określonego dostawcy. Błędy występujące w źródle danych są obsługiwane przez <xref:System.Data.Common.DbException> blok kodu, a wszystkie inne wyjątki są obsługiwane <xref:System.Exception> w bloku.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Obsługa błędów danych przy użyciu DbException  
 <xref:System.Data.Common.DbException> Klasa jest klasą bazową dla wszystkich wyjątków zgłoszonych w imieniu źródła danych. Można jej użyć w kodzie obsługi wyjątków do obsługi wyjątków zgłoszonych przez różnych dostawców bez konieczności odwoływania się do określonej klasy wyjątków. Poniższy fragment kodu pokazuje, jak <xref:System.Data.Common.DbException> używać do wyświetlania informacji o błędach zwracanych przez źródło danych przy użyciu <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> <xref:System.Exception.GetType%2A>właściwości, <xref:System.Exception.Message%2A> <xref:System.Exception.Source%2A>, i. W danych wyjściowych zostanie wyświetlony typ błędu, Źródło wskazujące nazwę dostawcy, kod błędu i komunikat skojarzony z błędem.  
  
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

- [DbProviderFactories](dbproviderfactories.md)
- [Uzyskiwanie DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [Modyfikowanie danych za pomocą obiektu DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Omówienie ADO.NET](ado-net-overview.md)
