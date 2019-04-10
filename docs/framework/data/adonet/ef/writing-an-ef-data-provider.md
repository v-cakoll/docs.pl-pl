---
title: Pisanie dostawcy danych programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 2aa27475c28bed521c636139b19454b0720960ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228747"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="90a5a-102">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="90a5a-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="90a5a-103">W tej sekcji omówiono sposób pisania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy w celu obsługi źródła danych inne niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90a5a-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="90a5a-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje dostawcę, który obsługuje program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90a5a-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="90a5a-105">Wprowadzenie do modelu dostawcy programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="90a5a-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="90a5a-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zależy od bazy danych i dostawcę można pisać przy użyciu modelu dostawcy ADO.NET połączyć się z różnorodnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="90a5a-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="90a5a-107">Dostawca danych programu Entity Framework (utworzone przy użyciu modelu dostawcy danych ADO.NET) wykonuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="90a5a-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="90a5a-108">Mapuje typy dostawców typów pierwotnych modelu Entity Data Model (EDM).</span><span class="sxs-lookup"><span data-stu-id="90a5a-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="90a5a-109">Uwidacznia funkcje właściwe dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="90a5a-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="90a5a-110">Generuje polecenia specyficzne dla dostawcy dla danego DbQueryCommandTree do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="90a5a-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="90a5a-111">Generuje polecenia aktualizacji specyficzne dla dostawcy dla danego DbModificationCommandTree do obsługi aktualizacji za pośrednictwem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90a5a-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="90a5a-112">Udostępnia mapowanie plików dla definicji schematu magazynu do obsługi generowania modelu, w oparciu o bazę danych.</span><span class="sxs-lookup"><span data-stu-id="90a5a-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="90a5a-113">Udostępnia metadane (tabele i widoki, na przykład) za pośrednictwem modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="90a5a-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="90a5a-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="90a5a-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="90a5a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="90a5a-115">Sample</span></span>  
 <span data-ttu-id="90a5a-116">Zobacz [dostawcy programu Entity Framework przykładowe](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) przykładowego [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy, który obsługuje źródła danych inne niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90a5a-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90a5a-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="90a5a-117">In This Section</span></span>  
 [<span data-ttu-id="90a5a-118">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="90a5a-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="90a5a-119">Modyfikowanie generowania kodu SQL</span><span class="sxs-lookup"><span data-stu-id="90a5a-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="90a5a-120">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="90a5a-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="90a5a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90a5a-121">See also</span></span>

- [<span data-ttu-id="90a5a-122">Praca z dostawcami danymi</span><span class="sxs-lookup"><span data-stu-id="90a5a-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
