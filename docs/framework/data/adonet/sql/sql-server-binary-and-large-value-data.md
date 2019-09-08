---
title: Dane binarne i dużej wartości w programie SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791676"
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="d8934-102">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="d8934-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="d8934-103">SQL Server zawiera `max` specyfikator, który rozszerza pojemność magazynu `varchar`dla, `nvarchar`i `varbinary` typów danych.</span><span class="sxs-lookup"><span data-stu-id="d8934-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="d8934-104">`varchar(max)`, `nvarchar(max)` i`varbinary(max)` są nazywane zbiorczo *typami danych o dużej wartości*.</span><span class="sxs-lookup"><span data-stu-id="d8934-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="d8934-105">Możesz użyć typów danych o dużej wartości do przechowywania maksymalnie 2 ^ 31-1 bajtów danych.</span><span class="sxs-lookup"><span data-stu-id="d8934-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="d8934-106">SQL Server 2008 wprowadza atrybut FILESTREAM, który nie jest typem danych, ale raczej atrybut, który można zdefiniować w kolumnie, umożliwiając przechowywanie danych dużych wartości w systemie plików, a nie w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d8934-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8934-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d8934-107">In This Section</span></span>  
 [<span data-ttu-id="d8934-108">Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8934-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](modifying-large-value-max-data.md)  
 <span data-ttu-id="d8934-109">Opisuje sposób pracy z typami danych o dużej wartości.</span><span class="sxs-lookup"><span data-stu-id="d8934-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="d8934-110">Dane FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="d8934-110">FILESTREAM Data</span></span>](filestream-data.md)  
 <span data-ttu-id="d8934-111">Opisuje sposób pracy z danymi o dużej wartości przechowywanych w SQL Server 2008 przy użyciu atrybutu FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="d8934-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8934-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8934-112">See also</span></span>

- [<span data-ttu-id="d8934-113">Typy danych programu SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8934-113">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="d8934-114">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8934-114">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="d8934-115">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8934-115">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="d8934-116">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d8934-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
