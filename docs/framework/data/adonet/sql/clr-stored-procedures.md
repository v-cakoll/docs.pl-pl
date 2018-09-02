---
title: Procedury składowane CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 1f8aa6fb9243706d07caa4527af0c4c880aa70a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424337"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="579cf-102">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="579cf-102">CLR Stored Procedures</span></span>
<span data-ttu-id="579cf-103">Procedury składowane są procedury, które nie mogą być używane w wyrażenia skalarne.</span><span class="sxs-lookup"><span data-stu-id="579cf-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="579cf-104">One zwrócenia jej klientowi wyniki tabelaryczne i komunikaty, wywołaj języka definicji danych (DDL) i instrukcje języka (DML) manipulacji danych i zwracać parametry wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="579cf-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="579cf-105">Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, który Microsoft Visual C# wykonuje.</span><span class="sxs-lookup"><span data-stu-id="579cf-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="579cf-106">Należy określić, Przekaż parametr według odwołania, a następnie zastosować \<Out() > atrybut do reprezentowania parametr wyjściowy, co przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="579cf-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="579cf-107">Aby uzyskać szczegółowe informacje, zobacz wersję [dokumentacji programu SQL Server](/sql) dla wersji programu SQL Server jest używany.</span><span class="sxs-lookup"><span data-stu-id="579cf-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="579cf-108">**Dokumentacja programu SQL Server**</span><span class="sxs-lookup"><span data-stu-id="579cf-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="579cf-109">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="579cf-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="579cf-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="579cf-110">See Also</span></span>  
 [<span data-ttu-id="579cf-111">Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="579cf-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="579cf-112">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="579cf-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
