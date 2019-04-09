---
title: Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d87f2b89583747b80ef103f419bd9bd2e3b1e0da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089838"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="92511-102">Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="92511-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="92511-103">SQL Server 2005 wprowadzono integrację składnika wspólnego języka wspólnego (CLR) programu .NET Framework dla programu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="92511-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="92511-104">Oznacza to, że można napisać procedury składowane, wyzwalacze, typy zdefiniowane przez użytkownika, funkcje zdefiniowane przez użytkownika, agregacje zdefiniowane przez użytkownika i przesyłania strumieniowego funkcji z wartościami przechowywanymi w tabeli przy użyciu dowolnego języka .NET Framework, w tym programu Microsoft Visual Basic .NET i Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="92511-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="92511-105"><xref:Microsoft.SqlServer.Server> Przestrzeń nazw zawiera zestaw nowych interfejsów programowania aplikacji (API), aby kod zarządzany może wchodzić w interakcje ze środowiskiem programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92511-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="92511-106">W tej sekcji opisano, funkcji i zachowań, które są specyficzne dla integrację środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego programu SQL Server i programu SQL Server w trakcie określonego rozszerzenia do zestawu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="92511-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="92511-107">Ta sekcja ma zapewnić tylko wystarczających informacji, aby rozpocząć programowanie z użyciem integracji środowiska CLR programu SQL Server i nie jest przeznaczona do wyczerpująca.</span><span class="sxs-lookup"><span data-stu-id="92511-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="92511-108">Aby uzyskać szczegółowe informacje Zobacz wersję programu SQL Server — książki Online dla wersji programu SQL Server, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="92511-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="92511-109">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="92511-109">SQL Server Books Online</span></span>**  
  
1.  [<span data-ttu-id="92511-110">Koncepcje programowania integracji wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR)</span><span class="sxs-lookup"><span data-stu-id="92511-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="92511-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="92511-111">In This Section</span></span>  
 [<span data-ttu-id="92511-112">Wprowadzenie do integracji środowiska CLR programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="92511-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="92511-113">Wprowadzenie do integracji środowiska CLR programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92511-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="92511-114">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="92511-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="92511-115">Zdefiniowane przez użytkownika funkcje CLR</span><span class="sxs-lookup"><span data-stu-id="92511-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="92511-116">W tym artykule opisano sposób wdrażania i używać różnych typów funkcji CLR: wartościami przechowywanymi w tabeli, skalarną i zdefiniowanych przez użytkownika funkcji agregujących.</span><span class="sxs-lookup"><span data-stu-id="92511-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="92511-117">Zdefiniowane przez użytkownika typy CLR</span><span class="sxs-lookup"><span data-stu-id="92511-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="92511-118">Opisuje sposób wdrożenia i używania typy CLR zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="92511-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="92511-119">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="92511-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="92511-120">Procedury składowane CLR</span><span class="sxs-lookup"><span data-stu-id="92511-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="92511-121">W tym artykule opisano, jak implementować oraz procedury składowane CLR.</span><span class="sxs-lookup"><span data-stu-id="92511-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="92511-122">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="92511-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="92511-123">Wyzwalacze CLR</span><span class="sxs-lookup"><span data-stu-id="92511-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="92511-124">Opisuje sposób wdrożenia i używania wyzwalacze CLR.</span><span class="sxs-lookup"><span data-stu-id="92511-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="92511-125">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="92511-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="92511-126">Połączenie kontekstu</span><span class="sxs-lookup"><span data-stu-id="92511-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="92511-127">W tym artykule opisano połączenia kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92511-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="92511-128">Zachowanie w procesie specyficzne dla serwera SQL ADO.NET</span><span class="sxs-lookup"><span data-stu-id="92511-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="92511-129">Opisuje rozszerzenia określone w procesie programu SQL Server, ADO.NET i połączenia kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92511-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="92511-130">Zawiera łącza do dodatkowych tematów.</span><span class="sxs-lookup"><span data-stu-id="92511-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92511-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92511-131">See also</span></span>

- [<span data-ttu-id="92511-132">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="92511-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="92511-133">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="92511-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
