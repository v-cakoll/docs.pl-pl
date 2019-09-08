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
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="c714f-102">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="c714f-102">DbConnection, DbCommand and DbException</span></span>
<span data-ttu-id="c714f-103">Po utworzeniu <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbConnection>i a można następnie korzystać z poleceń i czytników danych w celu pobierania danych ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c714f-103">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="c714f-104">Przykład pobierania danych</span><span class="sxs-lookup"><span data-stu-id="c714f-104">Retrieving Data Example</span></span>  
 <span data-ttu-id="c714f-105">Ten przykład pobiera `DbConnection` obiekt jako argument.</span><span class="sxs-lookup"><span data-stu-id="c714f-105">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="c714f-106">Jest tworzony w celu wybrania danych z tabeli Kategorie przez <xref:System.Data.Common.DbCommand.CommandText%2A> ustawienie instrukcji SELECT języka SQL. <xref:System.Data.Common.DbCommand></span><span class="sxs-lookup"><span data-stu-id="c714f-106">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="c714f-107">W kodzie założono, że tabela kategorie istnieje w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="c714f-107">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="c714f-108">Połączenie jest otwierane, a dane są pobierane przy użyciu <xref:System.Data.Common.DbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="c714f-108">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="c714f-109">Wykonywanie przykładowego polecenia</span><span class="sxs-lookup"><span data-stu-id="c714f-109">Executing a Command Example</span></span>  
 <span data-ttu-id="c714f-110">Ten przykład pobiera `DbConnection` obiekt jako argument.</span><span class="sxs-lookup"><span data-stu-id="c714f-110">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="c714f-111">Jeśli jest prawidłowy, połączenie zostanie otwarte <xref:System.Data.Common.DbCommand> i zostanie utworzone i wykonane. `DbConnection`</span><span class="sxs-lookup"><span data-stu-id="c714f-111">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="c714f-112"><xref:System.Data.Common.DbCommand.CommandText%2A> Jest ustawiona na instrukcję SQL INSERT, która wykonuje Wstawianie do tabeli Categories w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="c714f-112">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="c714f-113">W kodzie założono, że baza danych Northwind istnieje w źródle danych i że składnia SQL używana w instrukcji INSERT jest prawidłowa dla określonego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="c714f-113">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="c714f-114">Błędy występujące w źródle danych są obsługiwane przez <xref:System.Data.Common.DbException> blok kodu, a wszystkie inne wyjątki są obsługiwane <xref:System.Exception> w bloku.</span><span class="sxs-lookup"><span data-stu-id="c714f-114">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="c714f-115">Obsługa błędów danych przy użyciu DbException</span><span class="sxs-lookup"><span data-stu-id="c714f-115">Handling Data Errors with DbException</span></span>  
 <span data-ttu-id="c714f-116"><xref:System.Data.Common.DbException> Klasa jest klasą bazową dla wszystkich wyjątków zgłoszonych w imieniu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c714f-116">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="c714f-117">Można jej użyć w kodzie obsługi wyjątków do obsługi wyjątków zgłoszonych przez różnych dostawców bez konieczności odwoływania się do określonej klasy wyjątków.</span><span class="sxs-lookup"><span data-stu-id="c714f-117">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="c714f-118">Poniższy fragment kodu pokazuje, jak <xref:System.Data.Common.DbException> używać do wyświetlania informacji o błędach zwracanych przez źródło danych przy użyciu <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> <xref:System.Exception.GetType%2A>właściwości, <xref:System.Exception.Message%2A> <xref:System.Exception.Source%2A>, i.</span><span class="sxs-lookup"><span data-stu-id="c714f-118">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="c714f-119">W danych wyjściowych zostanie wyświetlony typ błędu, Źródło wskazujące nazwę dostawcy, kod błędu i komunikat skojarzony z błędem.</span><span class="sxs-lookup"><span data-stu-id="c714f-119">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c714f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c714f-120">See also</span></span>

- [<span data-ttu-id="c714f-121">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="c714f-121">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="c714f-122">Uzyskiwanie DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="c714f-122">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="c714f-123">Modyfikowanie danych za pomocą obiektu DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="c714f-123">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="c714f-124">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c714f-124">ADO.NET Overview</span></span>](ado-net-overview.md)
