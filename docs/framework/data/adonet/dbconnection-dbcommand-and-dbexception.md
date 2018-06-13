---
title: Obiektu DbConnection, polecenie DbCommand i dbexception —
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 419f152d45ec254efab9270f67ace6e46a6b96a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757128"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>Obiektu DbConnection, polecenie DbCommand i dbexception —
Po utworzeniu <xref:System.Data.Common.DbProviderFactory> i <xref:System.Data.Common.DbConnection>, następnie możesz pracować z czytniki danych i polecenia do pobierania danych ze źródła danych.  
  
## <a name="retrieving-data-example"></a>Przykład podczas pobierania danych  
 W tym przykładzie przyjmuje `DbConnection` obiektu jako argumentu. A <xref:System.Data.Common.DbCommand> jest tworzony, aby wybrać dane z tabeli Kategorie przez ustawienie <xref:System.Data.Common.DbCommand.CommandText%2A> do instrukcji SQL SELECT. Kod przyjęto założenie, że tabela kategorii istnieje w źródle danych. Połączenie jest otwarte, a dane są pobierane przy użyciu <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Przykład polecenia wykonywania  
 W tym przykładzie przyjmuje `DbConnection` obiektu jako argumentu. Jeśli `DbConnection` jest prawidłowy, jest otwarte połączenie i <xref:System.Data.Common.DbCommand> jest tworzony i wykonywane. <xref:System.Data.Common.DbCommand.CommandText%2A> Ustawiono instrukcji SQL INSERT, który wykonuje wstawiania do tabeli kategorii w bazie danych Northwind. Kod przyjęto założenie, że bazy danych Northwind istnieje w źródle danych i czy składnia SQL używane w instrukcji INSERT jest nieprawidłowa dla podanego dostawcy. Błędy występujące w źródle danych są obsługiwane przez <xref:System.Data.Common.DbException> blok kodu i pozostałe wyjątki są obsługiwane w <xref:System.Exception> bloku.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>Obsługa błędów danych z dbexception —  
 <xref:System.Data.Common.DbException> Klasa jest klasą bazową dla wszystkich wyjątków zgłoszonych w imieniu źródła danych. Użytkownik może być używany w kod obsługi wyjątku do obsługi wyjątków zgłaszanych przez różnych dostawców bez potrzeby odwołuje się do klasy specyficznego wyjątku. Poniższy fragment kodu przedstawiają sposób użycia <xref:System.Data.Common.DbException> Aby wyświetlić informacje o błędzie zwrócony przy użyciu źródła danych <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, i <xref:System.Exception.Message%2A> właściwości. Dane wyjściowe będą wyświetlane typ błędu, źródła wskazujący nazwę dostawcy, kod błędu i komunikat skojarzony z powodu błędu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Uzyskiwanie DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [Modyfikowanie danych za pomocą obiektu DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
