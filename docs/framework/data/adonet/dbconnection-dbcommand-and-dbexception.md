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
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="58fcf-102">Obiektu DbConnection, polecenie DbCommand i dbexception —</span><span class="sxs-lookup"><span data-stu-id="58fcf-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="58fcf-103">Po utworzeniu <xref:System.Data.Common.DbProviderFactory> i <xref:System.Data.Common.DbConnection>, następnie możesz pracować z czytniki danych i polecenia do pobierania danych ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="58fcf-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="58fcf-104">Przykład podczas pobierania danych</span><span class="sxs-lookup"><span data-stu-id="58fcf-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="58fcf-105">W tym przykładzie przyjmuje `DbConnection` obiektu jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="58fcf-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="58fcf-106">A <xref:System.Data.Common.DbCommand> jest tworzony, aby wybrać dane z tabeli Kategorie przez ustawienie <xref:System.Data.Common.DbCommand.CommandText%2A> do instrukcji SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="58fcf-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="58fcf-107">Kod przyjęto założenie, że tabela kategorii istnieje w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="58fcf-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="58fcf-108">Połączenie jest otwarte, a dane są pobierane przy użyciu <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="58fcf-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="58fcf-109">Przykład polecenia wykonywania</span><span class="sxs-lookup"><span data-stu-id="58fcf-109">Executing a Command Example</span></span>  
 <span data-ttu-id="58fcf-110">W tym przykładzie przyjmuje `DbConnection` obiektu jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="58fcf-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="58fcf-111">Jeśli `DbConnection` jest prawidłowy, jest otwarte połączenie i <xref:System.Data.Common.DbCommand> jest tworzony i wykonywane.</span><span class="sxs-lookup"><span data-stu-id="58fcf-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="58fcf-112"><xref:System.Data.Common.DbCommand.CommandText%2A> Ustawiono instrukcji SQL INSERT, który wykonuje wstawiania do tabeli kategorii w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="58fcf-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="58fcf-113">Kod przyjęto założenie, że bazy danych Northwind istnieje w źródle danych i czy składnia SQL używane w instrukcji INSERT jest nieprawidłowa dla podanego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="58fcf-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="58fcf-114">Błędy występujące w źródle danych są obsługiwane przez <xref:System.Data.Common.DbException> blok kodu i pozostałe wyjątki są obsługiwane w <xref:System.Exception> bloku.</span><span class="sxs-lookup"><span data-stu-id="58fcf-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="58fcf-115">Obsługa błędów danych z dbexception —</span><span class="sxs-lookup"><span data-stu-id="58fcf-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="58fcf-116"><xref:System.Data.Common.DbException> Klasa jest klasą bazową dla wszystkich wyjątków zgłoszonych w imieniu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="58fcf-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="58fcf-117">Użytkownik może być używany w kod obsługi wyjątku do obsługi wyjątków zgłaszanych przez różnych dostawców bez potrzeby odwołuje się do klasy specyficznego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="58fcf-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="58fcf-118">Poniższy fragment kodu przedstawiają sposób użycia <xref:System.Data.Common.DbException> Aby wyświetlić informacje o błędzie zwrócony przy użyciu źródła danych <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, i <xref:System.Exception.Message%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="58fcf-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="58fcf-119">Dane wyjściowe będą wyświetlane typ błędu, źródła wskazujący nazwę dostawcy, kod błędu i komunikat skojarzony z powodu błędu.</span><span class="sxs-lookup"><span data-stu-id="58fcf-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58fcf-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58fcf-120">See Also</span></span>  
 [<span data-ttu-id="58fcf-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="58fcf-121">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="58fcf-122">Uzyskiwanie DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="58fcf-122">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="58fcf-123">Modyfikowanie danych za pomocą obiektu DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="58fcf-123">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="58fcf-124">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="58fcf-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
