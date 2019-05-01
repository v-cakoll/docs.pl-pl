---
title: Zdefiniowane przez użytkownika typy CLR
ms.date: 03/30/2017
ms.assetid: 9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2
ms.openlocfilehash: b946a87e49d8bf496fb215eb95f9db9cb453c13c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878101"
---
# <a name="clr-user-defined-types"></a><span data-ttu-id="192a8-102">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="192a8-102">CLR User-Defined Types</span></span>
<span data-ttu-id="192a8-103">Microsoft SQL Server zapewnia obsługę typy zdefiniowane przez użytkownika (UDTs) implementowane za pomocą programu Microsoft .NET Framework środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="192a8-103">Microsoft SQL Server provides support for user-defined types (UDTs) implemented with the Microsoft .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="192a8-104">Środowisko CLR jest zintegrowana z programu SQL Server, a ten mechanizm pozwala rozszerzyć systemu typu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="192a8-104">The CLR is integrated into SQL Server, and this mechanism enables you to extend the type system of the database.</span></span> <span data-ttu-id="192a8-105">Rozszerzeń UDT rozszerzalność użytkownika system typów danych programu SQL Server, a także możliwość definiowania typów złożonych ze strukturą.</span><span class="sxs-lookup"><span data-stu-id="192a8-105">UDTs provide user extensibility of the SQL Server data type system, and also the ability to define complex structured types.</span></span>  
  
 <span data-ttu-id="192a8-106">Typów zdefiniowanych przez użytkownika zapewnia dwie kluczowe korzyści z punktu widzenia architektury aplikacji:</span><span class="sxs-lookup"><span data-stu-id="192a8-106">UDTs can provide two key benefits from an application architecture perspective:</span></span>  
  
- <span data-ttu-id="192a8-107">Silne hermetyzacji (zarówno na kliencie i serwerze) między stan wewnętrzny i zewnętrzny zachowania.</span><span class="sxs-lookup"><span data-stu-id="192a8-107">Strong encapsulation (both in the client and the server) between the internal state and the external behaviors.</span></span>  
  
- <span data-ttu-id="192a8-108">Ścisła integracja z innymi powiązanych funkcji serwera.</span><span class="sxs-lookup"><span data-stu-id="192a8-108">Deep integration with other related server features.</span></span> <span data-ttu-id="192a8-109">Po zdefiniowaniu własne UDT, można go we wszystkich kontekstach gdzie typ systemu w programie SQL Server, w tym definicje kolumn i służy jako zmiennych, parametrów, wyniki funkcji, kursorów, wyzwalaczy i replikacji.</span><span class="sxs-lookup"><span data-stu-id="192a8-109">Once you define your own UDT, you can use it in all contexts where you can use a system type in SQL Server, including column definitions, and as variables, parameters, function results, cursors, triggers, and replication.</span></span>  
  
 <span data-ttu-id="192a8-110">Aby uzyskać więcej informacji, zobacz [dokumentacji programu SQL Server](/sql) dla wersji programu SQL Server jest używany.</span><span class="sxs-lookup"><span data-stu-id="192a8-110">For more detailed information, see the [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="192a8-111">**Dokumentacja programu SQL Server**</span><span class="sxs-lookup"><span data-stu-id="192a8-111">**SQL Server documentation**</span></span>
  
1. [<span data-ttu-id="192a8-112">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="192a8-112">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="see-also"></a><span data-ttu-id="192a8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="192a8-113">See also</span></span>

- [<span data-ttu-id="192a8-114">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="192a8-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
