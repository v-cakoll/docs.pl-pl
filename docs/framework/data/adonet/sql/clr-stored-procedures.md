---
title: Procedury składowane CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 9b31d93c1ebc0af9aa8e41b3a4c328af62da7e23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230814"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="33613-102">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="33613-102">CLR Stored Procedures</span></span>
<span data-ttu-id="33613-103">Procedury składowane są procedury, które nie mogą być używane w wyrażenia skalarne.</span><span class="sxs-lookup"><span data-stu-id="33613-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="33613-104">One zwrócenia jej klientowi wyniki tabelaryczne i komunikaty, wywołaj języka definicji danych (DDL) i instrukcje języka (DML) manipulacji danych i zwracać parametry wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="33613-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33613-105">Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, który Microsoft Visual C# wykonuje.</span><span class="sxs-lookup"><span data-stu-id="33613-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="33613-106">Należy określić, Przekaż parametr według odwołania, a następnie zastosować \<Out() > atrybut do reprezentowania parametr wyjściowy, co przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="33613-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="33613-107">Aby uzyskać szczegółowe informacje, zobacz wersję [dokumentacji programu SQL Server](/sql) dla wersji programu SQL Server jest używany.</span><span class="sxs-lookup"><span data-stu-id="33613-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="33613-108">**Dokumentacja programu SQL Server**</span><span class="sxs-lookup"><span data-stu-id="33613-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="33613-109">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="33613-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="33613-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33613-110">See also</span></span>

- <span data-ttu-id="33613-111">[Tworzenie obiekty programu SQL Server 2005 w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="33613-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="33613-112">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="33613-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
