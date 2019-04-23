---
title: Zabezpieczenia integracji CLR w programie SQL Server
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 946401211d515df9ba5b9e38d7cfd10730973b64
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165818"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="25c2e-102">Zabezpieczenia integracji CLR w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="25c2e-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="25c2e-103">Microsoft SQL Server zapewnia integrację składnika wspólnego języka wspólnego (CLR) programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25c2e-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="25c2e-104">Integracja środowiska CLR umożliwia pisanie procedur składowanych, wyzwalaczy, typy zdefiniowane przez użytkownika, funkcje zdefiniowane przez użytkownika, agregacje zdefiniowane przez użytkownika i przesyłania strumieniowego funkcje wartościami przechowywanymi w tabeli, w dowolnym języku .NET Framework, takich jak Microsoft Visual Basic .NET lub Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="25c2e-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="25c2e-105">Środowisko CLR obsługuje model zabezpieczeń o nazwie zabezpieczenia dostępu kodu (CAS) dla kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="25c2e-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="25c2e-106">W tym modelu uprawnienia są przyznawane zestawów w oparciu o dowody dostarczone przez kod w metadanych.</span><span class="sxs-lookup"><span data-stu-id="25c2e-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="25c2e-107">Program SQL Server integruje modelu zabezpieczeń opartych na użytkownika programu SQL Server z modelem zabezpieczeń dostępu kodu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="25c2e-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="25c2e-108">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="25c2e-108">External Resources</span></span>  
 <span data-ttu-id="25c2e-109">Aby uzyskać więcej informacji na temat integracji CLR z programem SQL Server zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="25c2e-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="25c2e-110">Zasób</span><span class="sxs-lookup"><span data-stu-id="25c2e-110">Resource</span></span>|<span data-ttu-id="25c2e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="25c2e-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="25c2e-112">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="25c2e-112">Code Access Security</span></span>](../../../../../docs/framework/misc/code-access-security.md)|<span data-ttu-id="25c2e-113">Zawiera tematy opisujące urzędów certyfikacji w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25c2e-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="25c2e-114">Zabezpieczenia integracji CLR</span><span class="sxs-lookup"><span data-stu-id="25c2e-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="25c2e-115">W tym artykule omówiono model zabezpieczeń dla kodu zarządzanego wykonania wewnątrz programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="25c2e-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25c2e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25c2e-116">See also</span></span>

- [<span data-ttu-id="25c2e-117">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="25c2e-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="25c2e-118">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="25c2e-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="25c2e-119">Integracja aparatu plików wykonywalnych języka wspólnego z programem SQL Server</span><span class="sxs-lookup"><span data-stu-id="25c2e-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="25c2e-120">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="25c2e-120">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
