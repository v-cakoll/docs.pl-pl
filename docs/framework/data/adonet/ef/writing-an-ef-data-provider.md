---
title: Pisanie dostawca danych programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 578de94aa191d7302b762f1cdc87d4a6810037e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762637"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="4d7f2-102">Pisanie dostawca danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4d7f2-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="4d7f2-103">W tej sekcji omówiono sposób zapisania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy do obsługi źródła danych inne niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="4d7f2-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje dostawcę, który obsługuje program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="4d7f2-105">Wprowadzenie do modelu dostawcy programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4d7f2-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="4d7f2-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest niezależna bazy danych i może zapisywać dostawcę przy użyciu modelu dostawcy ADO.NET nawiązać połączenia z różnorodnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="4d7f2-107">Dostawca danych programu Entity Framework (utworzona przy użyciu dostawcy danych ADO.NET modelu) wykonuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="4d7f2-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="4d7f2-108">Mapuje typy dostawców typów pierwotnych modelu danych jednostki (EDM).</span><span class="sxs-lookup"><span data-stu-id="4d7f2-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="4d7f2-109">Opisuje funkcje właściwe dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="4d7f2-110">Generuje poleceń specyficznych dla dostawcy dla danego DbQueryCommandTree do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="4d7f2-111">Generuje poleceń specyficznych dla dostawcy aktualizacji dla danego DbModificationCommandTree do obsługi aktualizacji za pomocą [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d7f2-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="4d7f2-112">Udostępnia mapowanie plików dla definicji schematu magazynu do obsługi generowania modelu na podstawie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="4d7f2-113">Przedstawia metadanych (tabele i widoki, na przykład) za pomocą modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="4d7f2-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="4d7f2-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="4d7f2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d7f2-115">Sample</span></span>  
 <span data-ttu-id="4d7f2-116">Zobacz [Entity Framework próbki dostawcy](http://go.microsoft.com/fwlink/?LinkId=180616) przykładowe [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy, który obsługuje źródła danych inne niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4d7f2-116">See the [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4d7f2-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4d7f2-117">In This Section</span></span>  
 [<span data-ttu-id="4d7f2-118">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="4d7f2-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="4d7f2-119">Modyfikowanie generowania kodu SQL</span><span class="sxs-lookup"><span data-stu-id="4d7f2-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="4d7f2-120">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="4d7f2-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d7f2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d7f2-121">See Also</span></span>  
 [<span data-ttu-id="4d7f2-122">Praca z dostawcami danymi</span><span class="sxs-lookup"><span data-stu-id="4d7f2-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
