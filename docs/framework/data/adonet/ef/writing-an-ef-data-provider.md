---
title: Pisanie dostawcy danych programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248188"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="a5c39-102">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a5c39-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="a5c39-103">W tej sekcji omówiono sposób pisania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy w celu obsługi źródła danych innego niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5c39-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="a5c39-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera dostawcę, który obsługuje SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5c39-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="a5c39-105">Wprowadzenie do modelu dostawcy Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a5c39-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="a5c39-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest niezależna od bazy danych i można napisać dostawcę przy użyciu modelu dostawcy ADO.NET, aby połączyć się z różnorodnymi źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="a5c39-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="a5c39-107">Dostawca danych Entity Framework (utworzony przy użyciu modelu Dostawca danych ADO.NET) wykonuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="a5c39-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="a5c39-108">Mapuje typy pierwotne Entity Data Model (EDM) na typy dostawców.</span><span class="sxs-lookup"><span data-stu-id="a5c39-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="a5c39-109">Opisuje funkcje specyficzne dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="a5c39-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="a5c39-110">Generuje polecenia specyficzne dla dostawcy dla danego DbQueryCommandTree do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zapytań.</span><span class="sxs-lookup"><span data-stu-id="a5c39-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
- <span data-ttu-id="a5c39-111">Generuje polecenia aktualizacji specyficzne dla dostawcy dla danego DbModificationCommandTree do obsługi aktualizacji za pomocą programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5c39-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="a5c39-112">Przedstawia mapowanie plików dla definicji schematu magazynu w celu obsługi generowania modelu opartego na bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a5c39-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="a5c39-113">Udostępnia metadane (na przykład tabele i widoki) za pośrednictwem modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="a5c39-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="a5c39-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="a5c39-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="a5c39-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5c39-115">Sample</span></span>  
 <span data-ttu-id="a5c39-116">Zapoznaj się z przykładowym [dostawcą Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , aby [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uzyskać przykład dostawcy obsługującego źródło danych inne niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a5c39-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5c39-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a5c39-117">In This Section</span></span>  
 [<span data-ttu-id="a5c39-118">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="a5c39-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="a5c39-119">Modyfikowanie generowania kodu SQL</span><span class="sxs-lookup"><span data-stu-id="a5c39-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="a5c39-120">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="a5c39-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="a5c39-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5c39-121">See also</span></span>

- [<span data-ttu-id="a5c39-122">Praca z dostawcami danymi</span><span class="sxs-lookup"><span data-stu-id="a5c39-122">Working with Data Providers</span></span>](working-with-data-providers.md)
