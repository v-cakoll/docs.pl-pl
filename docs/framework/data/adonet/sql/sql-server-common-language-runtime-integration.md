---
title: Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 77b40c6a1576b87d9bb4a7eb4b1ee3df8828b892
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780862"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="0930b-102">Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="0930b-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="0930b-103">W SQL Server 2005 wprowadzono integrację składnika środowiska uruchomieniowego języka wspólnego (CLR) .NET Framework dla systemu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="0930b-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="0930b-104">Oznacza to, że można napisać procedury składowane, wyzwalacze, typy zdefiniowane przez użytkownika, funkcje zdefiniowane przez użytkownika, agregacje zdefiniowane przez użytkownika i funkcję przesyłania strumieniowego z wartościami przechowywanymi w tabeli przy użyciu dowolnego .NET Framework języka, w tym Microsoft Visual Basic .NET i Microsoft Wizualizacja C#.</span><span class="sxs-lookup"><span data-stu-id="0930b-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="0930b-105"><xref:Microsoft.SqlServer.Server> Przestrzeń nazw zawiera zestaw nowych interfejsów programowania aplikacji (API), dzięki czemu kod zarządzany może współdziałać ze środowiskiem Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0930b-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="0930b-106">W tej sekcji opisano funkcje i zachowania, które są specyficzne SQL Server dla integracji środowiska uruchomieniowego języka wspólnego (CLR) i SQL Server w procesie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0930b-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="0930b-107">Ta sekcja ma na celu dostarczenie tylko wystarczającej ilości informacji, aby rozpocząć programowanie przy użyciu integracji środowiska CLR SQL Server i nie jest to wszechstronne.</span><span class="sxs-lookup"><span data-stu-id="0930b-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="0930b-108">Aby uzyskać bardziej szczegółowe informacje, zapoznaj się z wersją usługi SQL Server Books Online dla używanej wersji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0930b-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="0930b-109">**Książka SQL Server online**</span><span class="sxs-lookup"><span data-stu-id="0930b-109">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="0930b-110">Pojęcia dotyczące programowania integracji środowiska uruchomieniowego języka wspólnego (CLR)</span><span class="sxs-lookup"><span data-stu-id="0930b-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="0930b-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0930b-111">In This Section</span></span>  
 [<span data-ttu-id="0930b-112">Wprowadzenie do integracja środowiska CLR programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="0930b-112">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="0930b-113">Zawiera wprowadzenie do SQL Server integracji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0930b-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="0930b-114">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="0930b-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0930b-115">Zdefiniowane przez użytkownika funkcje CLR</span><span class="sxs-lookup"><span data-stu-id="0930b-115">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="0930b-116">Opisuje sposób implementacji i używania różnych typów funkcji CLR: funkcji agregujących zwracającej tabelę, skalarnej i zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0930b-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="0930b-117">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="0930b-117">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="0930b-118">Opisuje sposób implementacji i używania typów CLR zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0930b-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="0930b-119">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="0930b-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0930b-120">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="0930b-120">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="0930b-121">Opisuje sposób implementacji i używania procedur składowanych CLR.</span><span class="sxs-lookup"><span data-stu-id="0930b-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="0930b-122">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="0930b-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0930b-123">Wyzwalacze CLR</span><span class="sxs-lookup"><span data-stu-id="0930b-123">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="0930b-124">Opisuje sposób implementacji i używania wyzwalaczy CLR.</span><span class="sxs-lookup"><span data-stu-id="0930b-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="0930b-125">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="0930b-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="0930b-126">Połączenie kontekstu</span><span class="sxs-lookup"><span data-stu-id="0930b-126">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="0930b-127">Opisuje połączenie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0930b-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="0930b-128">Zachowanie w procesie specyficzne dla serwera SQL ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0930b-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="0930b-129">W tym artykule opisano SQL Server specyficzne dla procesu rozszerzenia ADO.NET i połączenia kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0930b-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="0930b-130">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="0930b-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0930b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0930b-131">See also</span></span>

- [<span data-ttu-id="0930b-132">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0930b-132">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="0930b-133">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0930b-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
