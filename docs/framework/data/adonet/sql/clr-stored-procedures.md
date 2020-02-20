---
title: Procedury składowane CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: ca0fd2d33f0ad56c96fb63530e6ba3f7f7890f81
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450365"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="64522-102">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="64522-102">CLR Stored Procedures</span></span>
<span data-ttu-id="64522-103">Procedury składowane są procedurami, których nie można używać w wyrażeniach skalarnych.</span><span class="sxs-lookup"><span data-stu-id="64522-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="64522-104">Mogą zwracać wyniki tabelaryczne i komunikaty do klienta, wywoływać instrukcje języka definicji danych (DDL) i języka manipulowania danymi oraz zwracać parametry wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="64522-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64522-105">Firma Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, jak C# w przypadku programu Microsoft Visual.</span><span class="sxs-lookup"><span data-stu-id="64522-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="64522-106">Należy określić, aby przekazać parametr przez odwołanie i zastosować atrybut \<out () > do reprezentowania parametru wyjściowego, jak w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="64522-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="64522-107">Aby uzyskać szczegółowe informacje, zobacz wersję [dokumentacji SQL Server](/sql) dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="64522-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="64522-108">**SQL Server documentation (Dokumentacja programu SQL Server)**</span><span class="sxs-lookup"><span data-stu-id="64522-108">**SQL Server documentation**</span></span>

1. <span data-ttu-id="64522-109">[Procedury składowane CLR](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="64522-109">[CLR Stored Procedures](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64522-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64522-110">See also</span></span>

- <span data-ttu-id="64522-111">[Tworzenie obiektów SQL Server 2005 w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="64522-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="64522-112">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="64522-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
