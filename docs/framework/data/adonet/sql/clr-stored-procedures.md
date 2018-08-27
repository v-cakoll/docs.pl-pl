---
title: Procedury składowane CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: df323e2d1b50dcd1b2087141deefa1c86723b346
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930115"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="efe97-102">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="efe97-102">CLR Stored Procedures</span></span>
<span data-ttu-id="efe97-103">Procedury składowane są procedury, które nie mogą być używane w wyrażenia skalarne.</span><span class="sxs-lookup"><span data-stu-id="efe97-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="efe97-104">One zwrócenia jej klientowi wyniki tabelaryczne i komunikaty, wywołaj języka definicji danych (DDL) i instrukcje języka (DML) manipulacji danych i zwracać parametry wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="efe97-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efe97-105">Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, który Microsoft Visual C# wykonuje.</span><span class="sxs-lookup"><span data-stu-id="efe97-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="efe97-106">Należy określić, Przekaż parametr według odwołania, a następnie zastosować \<Out() > atrybut do reprezentowania parametr wyjściowy, co przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="efe97-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="efe97-107">Aby uzyskać szczegółowe informacje, zobacz wersję [dokumentacji programu SQL Server](/sql) dla wersji programu SQL Server jest używany.</span><span class="sxs-lookup"><span data-stu-id="efe97-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="efe97-108">**Dokumentacja programu SQL Server**</span><span class="sxs-lookup"><span data-stu-id="efe97-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="efe97-109">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="efe97-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="efe97-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efe97-110">See Also</span></span>  
 [<span data-ttu-id="efe97-111">Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="efe97-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="efe97-112">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="efe97-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
