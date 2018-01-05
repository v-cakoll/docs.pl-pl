---
title: Pisanie dostawca danych programu Entity Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a316ae288d677a0ad5bd602399e27389839ef092
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="c6f0b-102">Pisanie dostawca danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c6f0b-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="c6f0b-103">W tej sekcji omówiono sposób zapisania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy do obsługi źródłem danych innego niż [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6f0b-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c6f0b-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje dostawcę, który obsługuje [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6f0b-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="c6f0b-105">Wprowadzenie do modelu dostawcy programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c6f0b-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="c6f0b-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest niezależna bazy danych i może zapisywać dostawcę przy użyciu modelu dostawcy ADO.NET nawiązać połączenia z różnorodnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="c6f0b-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="c6f0b-107">Dostawca danych programu Entity Framework (utworzona przy użyciu dostawcy danych ADO.NET modelu) wykonuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="c6f0b-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="c6f0b-108">Mapuje typy dostawców typów pierwotnych modelu danych jednostki (EDM).</span><span class="sxs-lookup"><span data-stu-id="c6f0b-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="c6f0b-109">Opisuje funkcje właściwe dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="c6f0b-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="c6f0b-110">Generuje poleceń specyficznych dla dostawcy dla danego DbQueryCommandTree do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="c6f0b-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="c6f0b-111">Generuje poleceń specyficznych dla dostawcy aktualizacji dla danego DbModificationCommandTree do obsługi aktualizacji za pomocą [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6f0b-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="c6f0b-112">Udostępnia mapowanie plików dla definicji schematu magazynu do obsługi generowania modelu na podstawie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c6f0b-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="c6f0b-113">Przedstawia metadanych (tabele i widoki, na przykład) za pomocą modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="c6f0b-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="c6f0b-114">![b42a7a5c &#45; 0ac0 &#45;4911 &#45; 86be &#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="c6f0b-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="c6f0b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6f0b-115">Sample</span></span>  
 <span data-ttu-id="c6f0b-116">Zobacz [Entity Framework próbki dostawcy](http://go.microsoft.com/fwlink/?LinkId=180616) przykładowe [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy, który obsługuje źródłem danych innego niż [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6f0b-116">See the [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6f0b-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c6f0b-117">In This Section</span></span>  
 [<span data-ttu-id="c6f0b-118">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="c6f0b-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="c6f0b-119">Modyfikowanie generowania kodu SQL</span><span class="sxs-lookup"><span data-stu-id="c6f0b-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="c6f0b-120">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="c6f0b-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6f0b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6f0b-121">See Also</span></span>  
 [<span data-ttu-id="c6f0b-122">Praca z dostawcami danymi</span><span class="sxs-lookup"><span data-stu-id="c6f0b-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
