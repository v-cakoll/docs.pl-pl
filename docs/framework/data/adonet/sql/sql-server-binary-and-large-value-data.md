---
title: Binarne i dużej wartości danych programu SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 9ebbe23dfbcac7825ce449dd40f62b921d13ab4a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209163"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="08f78-102">Binarne i dużej wartości danych programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="08f78-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="08f78-103">SQL Server udostępnia `max` specyfikator, który zwiększa pojemność `varchar`, `nvarchar`, i `varbinary` typów danych.</span><span class="sxs-lookup"><span data-stu-id="08f78-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="08f78-104">`varchar(max)`, `nvarchar(max)`, i `varbinary(max)` są nazywane *typów danych dużych wartości*.</span><span class="sxs-lookup"><span data-stu-id="08f78-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="08f78-105">Typy danych dużej wartości można użyć do przechowywania maksymalnie 2 ^ 31-1 bajtów danych.</span><span class="sxs-lookup"><span data-stu-id="08f78-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="08f78-106">Program SQL Server 2008 wprowadzono atrybut FILESTREAM, który jest typem danych, ale raczej atrybut, który może być zdefiniowany dla kolumny, dzięki czemu duża wartość danych mają być przechowywane w systemie plików zamiast w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="08f78-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08f78-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="08f78-107">In This Section</span></span>  
 [<span data-ttu-id="08f78-108">Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08f78-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="08f78-109">W tym artykule opisano sposób pracy z typami danych duża wartość.</span><span class="sxs-lookup"><span data-stu-id="08f78-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="08f78-110">Dane FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="08f78-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="08f78-111">W tym artykule opisano sposób pracy z dużą wartość — dane przechowywane w programie SQL Server 2008 mających atrybut FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="08f78-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f78-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08f78-112">See Also</span></span>  
 [<span data-ttu-id="08f78-113">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08f78-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="08f78-114">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08f78-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="08f78-115">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08f78-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="08f78-116">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="08f78-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
