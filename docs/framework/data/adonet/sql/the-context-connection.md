---
title: "Połączenie kontekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3bb732644bf9373d847eb14b63e69a756cb3ac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-context-connection"></a><span data-ttu-id="8f956-102">Połączenie kontekstu</span><span class="sxs-lookup"><span data-stu-id="8f956-102">The Context Connection</span></span>
<span data-ttu-id="8f956-103">Problem dostępu do danych wewnętrznych jest dość typowy scenariusz.</span><span class="sxs-lookup"><span data-stu-id="8f956-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="8f956-104">Oznacza to, że mają dostęp do tego samego serwera Twoje środowisko uruchomieniowe języka wspólnego (CLR) procedury składowanej lub funkcji jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="8f956-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="8f956-105">Jedną z opcji jest utworzenie połączenia za pomocą <xref:System.Data.SqlClient.SqlConnection>, określ ciąg połączenia, który wskazuje na serwerze lokalnym i otwarcia połączenia.</span><span class="sxs-lookup"><span data-stu-id="8f956-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="8f956-106">Wymaga to podania poświadczeń do logowania.</span><span class="sxs-lookup"><span data-stu-id="8f956-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="8f956-107">Połączenie jest w sesji innej bazy danych niż procedura składowana lub funkcja, może mieć różne `SET` opcje, znajduje się w osobnej transakcji, nie zobaczą tabele tymczasowe, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8f956-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="8f956-108">Jeśli sieci zarządzanej procedury składowanej lub funkcji kod jest wykonywany w procesie programu SQL Server, to, że ktoś połączona z tym serwerem, a instrukcja SQL, można go wywołać.</span><span class="sxs-lookup"><span data-stu-id="8f956-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="8f956-109">Prawdopodobnie potrzebna będzie procedura składowana lub funkcja do wykonania w kontekście tego połączenia, wraz z jego transakcji `SET` opcje i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8f956-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="8f956-110">Jest to połączenie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8f956-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="8f956-111">Połączenie kontekstu umożliwia wykonanie instrukcji języka Transact-SQL w kontekście tego samego kodu wywołano w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8f956-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="8f956-112">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="8f956-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="8f956-113">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="8f956-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="8f956-114">Połączenie kontekstu</span><span class="sxs-lookup"><span data-stu-id="8f956-114">The Context Connection</span></span>](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a><span data-ttu-id="8f956-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f956-115">See Also</span></span>  
 [<span data-ttu-id="8f956-116">Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="8f956-116">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="8f956-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="8f956-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
