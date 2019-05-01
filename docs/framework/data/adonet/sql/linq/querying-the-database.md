---
title: wykonywanie zapytania w bazie danych
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: fdcfaa3fc0d08df07027d44399612fb688b920d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918037"
---
# <a name="querying-the-database"></a><span data-ttu-id="71427-102">wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="71427-102">Querying the Database</span></span>
<span data-ttu-id="71427-103">Ta grupa tematów w tym artykule opisano sposób tworzenia i wykonywanie zapytań w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektów.</span><span class="sxs-lookup"><span data-stu-id="71427-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71427-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="71427-104">In This Section</span></span>  
 [<span data-ttu-id="71427-105">Instrukcje: Zapytanie dotyczące informacji</span><span class="sxs-lookup"><span data-stu-id="71427-105">How to: Query for Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-query-for-information.md)  
 <span data-ttu-id="71427-106">Krótko przedstawiono sposób [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania są zasadniczo takie same, jak [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] ogólnie zapytania.</span><span class="sxs-lookup"><span data-stu-id="71427-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="71427-107">Instrukcje: Pobieranie informacji jako tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="71427-107">How to: Retrieve Information As Read-Only</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="71427-108">Opisuje sposób zwiększyć wydajność zapytań, gdy planowane jest wprowadzenie nie wprowadzono zmian w danych.</span><span class="sxs-lookup"><span data-stu-id="71427-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="71427-109">Instrukcje: Kontrolowanie, ile powiązane dane są pobierane.</span><span class="sxs-lookup"><span data-stu-id="71427-109">How to: Control How Much Related Data Is Retrieved</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="71427-110">W tym artykule opisano sposób kontrolowania powiązane dane, które są pobierane wraz z główny element docelowy.</span><span class="sxs-lookup"><span data-stu-id="71427-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="71427-111">Instrukcje: Filtrowanie powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="71427-111">How to: Filter Related Data</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-related-data.md)  
 <span data-ttu-id="71427-112">Opisuje sposób pobierania powiązanych danych przy użyciu podzapytaniu.</span><span class="sxs-lookup"><span data-stu-id="71427-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="71427-113">Instrukcje: Wyłączanie odroczonego ładowania</span><span class="sxs-lookup"><span data-stu-id="71427-113">How to: Turn Off Deferred Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="71427-114">Opisuje sposób wyłączanie odroczonego ładowania.</span><span class="sxs-lookup"><span data-stu-id="71427-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="71427-115">Instrukcje: Bezpośrednie wykonywanie zapytań SQL</span><span class="sxs-lookup"><span data-stu-id="71427-115">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="71427-116">W tym artykule opisano sposób przesyłania zapytań przy użyciu języka SQL.</span><span class="sxs-lookup"><span data-stu-id="71427-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="71427-117">Instrukcje: Store i ponowne użycie zapytań</span><span class="sxs-lookup"><span data-stu-id="71427-117">How to: Store and Reuse Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="71427-118">Opisuje sposób kompilowania zapytania jeden raz, ale jej używać wiele razy z różnymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="71427-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="71427-119">Instrukcje: Obsługa kluczy złożonych w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="71427-119">How to: Handle Composite Keys in Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="71427-120">W tym artykule opisano jak dołączyć więcej niż jedną kolumnę w zapytaniu, w której operator przyjmuje jeden argument.</span><span class="sxs-lookup"><span data-stu-id="71427-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="71427-121">Instrukcje: Pobieranie jednocześnie wielu obiektów</span><span class="sxs-lookup"><span data-stu-id="71427-121">How to: Retrieve Many Objects At Once</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="71427-122">Opisuje sposób używania <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="71427-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="71427-123">Instrukcje: Filtrowanie na poziomie elementu DataContext</span><span class="sxs-lookup"><span data-stu-id="71427-123">How to: Filter at the DataContext Level</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="71427-124">W tym artykule opisano używanie innego <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="71427-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="71427-125">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="71427-125">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="71427-126">Przykłady wiele kwerend.</span><span class="sxs-lookup"><span data-stu-id="71427-126">Provides many examples of queries.</span></span>
