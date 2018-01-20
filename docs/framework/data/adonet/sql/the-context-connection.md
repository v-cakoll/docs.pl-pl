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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 40aa71a16c7a0616cfcf318901858da7587fa20b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="the-context-connection"></a><span data-ttu-id="b788e-102">Połączenie kontekstu</span><span class="sxs-lookup"><span data-stu-id="b788e-102">The Context Connection</span></span>
<span data-ttu-id="b788e-103">Problem dostępu do danych wewnętrznych jest dość typowy scenariusz.</span><span class="sxs-lookup"><span data-stu-id="b788e-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="b788e-104">Oznacza to, że mają dostęp do tego samego serwera Twoje środowisko uruchomieniowe języka wspólnego (CLR) procedury składowanej lub funkcji jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="b788e-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="b788e-105">Jedną z opcji jest utworzenie połączenia za pomocą <xref:System.Data.SqlClient.SqlConnection>, określ ciąg połączenia, który wskazuje na serwerze lokalnym i otwarcia połączenia.</span><span class="sxs-lookup"><span data-stu-id="b788e-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="b788e-106">Wymaga to podania poświadczeń do logowania.</span><span class="sxs-lookup"><span data-stu-id="b788e-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="b788e-107">Połączenie jest w sesji innej bazy danych niż procedura składowana lub funkcja, może mieć różne `SET` opcje, znajduje się w osobnej transakcji, nie zobaczą tabele tymczasowe, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b788e-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="b788e-108">Jeśli sieci zarządzanej procedury składowanej lub funkcji kod jest wykonywany w procesie programu SQL Server, to, że ktoś połączona z tym serwerem, a instrukcja SQL, można go wywołać.</span><span class="sxs-lookup"><span data-stu-id="b788e-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="b788e-109">Prawdopodobnie potrzebna będzie procedura składowana lub funkcja do wykonania w kontekście tego połączenia, wraz z jego transakcji `SET` opcje i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b788e-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="b788e-110">Jest to połączenie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b788e-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="b788e-111">Połączenie kontekstu umożliwia wykonanie instrukcji języka Transact-SQL w kontekście tego samego kodu wywołano w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b788e-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="b788e-112">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="b788e-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="b788e-113">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="b788e-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="b788e-114">Połączenie kontekstu</span><span class="sxs-lookup"><span data-stu-id="b788e-114">The Context Connection</span></span>](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## <a name="see-also"></a><span data-ttu-id="b788e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b788e-115">See Also</span></span>  
 [<span data-ttu-id="b788e-116">Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="b788e-116">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="b788e-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b788e-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
