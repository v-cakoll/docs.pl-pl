---
title: Procedury składowane CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c02efa3f0a91d176b626761335bd2d5a2b96b966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917960"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="c0d5d-102">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="c0d5d-102">CLR Stored Procedures</span></span>
<span data-ttu-id="c0d5d-103">Procedury składowane są procedurami, których nie można używać w wyrażeniach skalarnych.</span><span class="sxs-lookup"><span data-stu-id="c0d5d-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="c0d5d-104">Mogą zwracać wyniki tabelaryczne i komunikaty do klienta, wywoływać instrukcje języka definicji danych (DDL) i języka manipulowania danymi oraz zwracać parametry wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c0d5d-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0d5d-105">Firma Microsoft Visual Basic nie obsługuje parametrów wyjściowych w taki sam sposób, jak C# w przypadku programu Microsoft Visual.</span><span class="sxs-lookup"><span data-stu-id="c0d5d-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="c0d5d-106">Należy określić, aby przekazać parametr przez odwołanie i zastosować \<atrybut out () > do reprezentowania parametru wyjściowego, tak jak w poniższym:</span><span class="sxs-lookup"><span data-stu-id="c0d5d-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="c0d5d-107">Aby uzyskać szczegółowe informacje, zobacz wersję [dokumentacji SQL Server](/sql) dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0d5d-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="c0d5d-108">**Dokumentacja SQL Server**</span><span class="sxs-lookup"><span data-stu-id="c0d5d-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="c0d5d-109">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="c0d5d-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="c0d5d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0d5d-110">See also</span></span>

- <span data-ttu-id="c0d5d-111">[Tworzenie obiektów SQL Server 2005 w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c0d5d-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="c0d5d-112">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c0d5d-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
