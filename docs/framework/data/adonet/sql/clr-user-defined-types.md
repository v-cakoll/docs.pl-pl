---
title: Typy CLR zdefiniowane przez użytkownika
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: 4ea415a348375c52e42ddf26ea09a74e7de5e355
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45673769"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="40e65-102">Typy CLR zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="40e65-102">CLR User-Defined Types</span></span>
<span data-ttu-id="40e65-103">Microsoft SQL Server zapewnia obsługę typy zdefiniowane przez użytkownika (UDTs) implementowane za pomocą programu Microsoft .NET Framework środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="40e65-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="40e65-104">Środowisko CLR jest zintegrowana z programu SQL Server, a ten mechanizm pozwala rozszerzyć systemu typu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="40e65-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="40e65-105">Rozszerzeń UDT rozszerzalność użytkownika system typów danych programu SQL Server, a także możliwość definiowania typów złożonych ze strukturą.</span><span class="sxs-lookup"><span data-stu-id="40e65-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="40e65-106">Typów zdefiniowanych przez użytkownika zapewnia dwie kluczowe korzyści z punktu widzenia architektury aplikacji:</span><span class="sxs-lookup"><span data-stu-id="40e65-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
-   <span data-ttu-id="40e65-107">Silne hermetyzacji (zarówno na kliencie i serwerze) między stan wewnętrzny i zewnętrzny zachowania.</span><span class="sxs-lookup"><span data-stu-id="40e65-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
-   <span data-ttu-id="40e65-108">Ścisła integracja z innymi powiązanych funkcji serwera.</span><span class="sxs-lookup"><span data-stu-id="40e65-108">Deep integration with other related server features.</span></span> <span data-ttu-id="40e65-109">Po zdefiniowaniu własne UDT, można go we wszystkich kontekstach gdzie typ systemu w programie SQL Server, w tym definicje kolumn i służy jako zmiennych, parametrów, wyniki funkcji, kursorów, wyzwalaczy i replikacji.</span><span class="sxs-lookup"><span data-stu-id="40e65-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="40e65-110">Aby uzyskać więcej informacji, zobacz [dokumentacji programu SQL Server](/sql) dla wersji programu SQL Server jest używany.</span><span class="sxs-lookup"><span data-stu-id="40e65-110">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="40e65-111">**Dokumentacja programu SQL Server**</span><span class="sxs-lookup"><span data-stu-id="40e65-111">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="40e65-112">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="40e65-112">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="40e65-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40e65-113">See also</span></span>  

[<span data-ttu-id="40e65-114">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="40e65-114">ADO.NET Overview</span></span>](../ado-net-overview.md)  