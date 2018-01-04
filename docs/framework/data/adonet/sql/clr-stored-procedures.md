---
title: "Procedury składowane CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dfed0124c33c90427c9b888f5aa7bb191aea0400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="f29e1-102">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="f29e1-102">CLR Stored Procedures</span></span>
<span data-ttu-id="f29e1-103">Procedury składowane są procedury, których nie można używać w wyrażeniach skalarne.</span><span class="sxs-lookup"><span data-stu-id="f29e1-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="f29e1-104">Mogą zwracać wyniki tabelaryczne i komunikaty do klienta, wywołania języka definicji danych (DDL) i instrukcji języka manipulacji danych oraz zwraca parametry wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="f29e1-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f29e1-105">Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, który wykonuje Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="f29e1-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="f29e1-106">Należy określić parametr jest przekazywany za pomocą odwołania i stosowanie \<Out() > atrybut do reprezentowania parametru wyjściowego, co przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="f29e1-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="f29e1-107">Aby uzyskać szczegółowe informacje Zobacz wersji programu SQL Server — książki Online dla wersji programu SQL Server są przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="f29e1-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="f29e1-108">**SQL Server — książki Online**</span><span class="sxs-lookup"><span data-stu-id="f29e1-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="f29e1-109">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="f29e1-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="f29e1-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f29e1-110">See Also</span></span>  
 [<span data-ttu-id="f29e1-111">Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="f29e1-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="f29e1-112">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="f29e1-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
