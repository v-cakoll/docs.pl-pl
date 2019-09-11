---
title: Pisanie dostawcy danych programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854161"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="2caca-102">Pisanie dostawcy danych programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2caca-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="2caca-103">W tej sekcji omówiono sposób pisania Entity Framework dostawcy w celu obsługi źródła danych innego niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2caca-103">This section discusses how to write an Entity Framework provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="2caca-104">Entity Framework zawiera dostawcę obsługującego SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2caca-104">The Entity Framework includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="2caca-105">Wprowadzenie do modelu dostawcy Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2caca-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="2caca-106">Entity Framework jest niezależna od bazy danych i można napisać dostawcę przy użyciu modelu dostawcy ADO.NET w celu nawiązania połączenia z różnorodnym zestawem źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="2caca-106">The Entity Framework is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="2caca-107">Dostawca danych Entity Framework (utworzony przy użyciu modelu Dostawca danych ADO.NET) wykonuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="2caca-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="2caca-108">Mapuje typy pierwotne Entity Data Model (EDM) na typy dostawców.</span><span class="sxs-lookup"><span data-stu-id="2caca-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="2caca-109">Opisuje funkcje specyficzne dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="2caca-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="2caca-110">Generuje polecenia specyficzne dla dostawcy dla danego DbQueryCommandTree do obsługi zapytań Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2caca-110">Generates provider-specific commands for a given DbQueryCommandTree to support Entity Framework queries.</span></span>  
  
- <span data-ttu-id="2caca-111">Generuje polecenia aktualizacji specyficzne dla dostawcy dla danego DbModificationCommandTree do obsługi aktualizacji za pomocą Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2caca-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the Entity Framework.</span></span>  
  
- <span data-ttu-id="2caca-112">Przedstawia mapowanie plików dla definicji schematu magazynu w celu obsługi generowania modelu opartego na bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2caca-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="2caca-113">Udostępnia metadane (na przykład tabele i widoki) za pośrednictwem modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="2caca-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="2caca-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="2caca-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="2caca-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2caca-115">Sample</span></span>  
 <span data-ttu-id="2caca-116">Zapoznaj się Entity Framework z przykładowym [dostawcą](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) Entity Framework, który obsługuje źródło danych inne niż SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2caca-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an Entity Framework provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2caca-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2caca-117">In This Section</span></span>  
 [<span data-ttu-id="2caca-118">Generowanie kodu SQL</span><span class="sxs-lookup"><span data-stu-id="2caca-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="2caca-119">Modyfikowanie generowania kodu SQL</span><span class="sxs-lookup"><span data-stu-id="2caca-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="2caca-120">Specyfikacja manifestu dostawcy</span><span class="sxs-lookup"><span data-stu-id="2caca-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="2caca-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2caca-121">See also</span></span>

- [<span data-ttu-id="2caca-122">Praca z dostawcami danymi</span><span class="sxs-lookup"><span data-stu-id="2caca-122">Working with Data Providers</span></span>](working-with-data-providers.md)
