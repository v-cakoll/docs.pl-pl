---
title: Zapytanie bazy danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e7f2c2a3936fc27e963867a4a4bf4bc210c6b7e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="querying-the-database"></a><span data-ttu-id="25dc7-102">Zapytanie bazy danych</span><span class="sxs-lookup"><span data-stu-id="25dc7-102">Querying the Database</span></span>
<span data-ttu-id="25dc7-103">Ta grupa tematów opisuje sposób rozwijać i wykonywanie zapytań w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektów.</span><span class="sxs-lookup"><span data-stu-id="25dc7-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25dc7-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="25dc7-104">In This Section</span></span>  
 [<span data-ttu-id="25dc7-105">Instrukcje: Zapytanie dotyczące informacji</span><span class="sxs-lookup"><span data-stu-id="25dc7-105">How to: Query for Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-query-for-information.md)  
 <span data-ttu-id="25dc7-106">Krótko przedstawiono sposób [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania są zasadniczo taki sam jak [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zazwyczaj zapytań.</span><span class="sxs-lookup"><span data-stu-id="25dc7-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries generally.</span></span>  
  
 [<span data-ttu-id="25dc7-107">Instrukcje: Pobieranie informacji jako tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="25dc7-107">How to: Retrieve Information As Read-Only</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="25dc7-108">Opisuje sposób zwiększa wydajność zapytań, jeśli jest planowane nie zmiany danych.</span><span class="sxs-lookup"><span data-stu-id="25dc7-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="25dc7-109">Instrukcje: kontrolowanie, ile jest pobieranych powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="25dc7-109">How to: Control How Much Related Data Is Retrieved</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="25dc7-110">Zawiera opis sposobu kontrolowania, które powiązane dane są pobierane wraz z głównego celu.</span><span class="sxs-lookup"><span data-stu-id="25dc7-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="25dc7-111">Instrukcje: Filtrowanie powiązanych danych</span><span class="sxs-lookup"><span data-stu-id="25dc7-111">How to: Filter Related Data</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-related-data.md)  
 <span data-ttu-id="25dc7-112">Opisuje sposób pobrać powiązanych danych za pomocą podzapytania.</span><span class="sxs-lookup"><span data-stu-id="25dc7-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="25dc7-113">Instrukcje: Wyłączanie odroczonego ładowania</span><span class="sxs-lookup"><span data-stu-id="25dc7-113">How to: Turn Off Deferred Loading</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="25dc7-114">Opisuje sposób wyłączyć odroczonego ładowania.</span><span class="sxs-lookup"><span data-stu-id="25dc7-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="25dc7-115">Instrukcje: Bezpośrednie wykonywanie zapytań SQL</span><span class="sxs-lookup"><span data-stu-id="25dc7-115">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="25dc7-116">Zawiera opis sposobu przesyłania zapytań przy użyciu języka SQL.</span><span class="sxs-lookup"><span data-stu-id="25dc7-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="25dc7-117">Instrukcje: Przechowywanie i ponowne użycie zapytań</span><span class="sxs-lookup"><span data-stu-id="25dc7-117">How to: Store and Reuse Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="25dc7-118">Opisuje sposób kompilowania zapytania jeden raz, ale jej używać wiele razy z różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="25dc7-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="25dc7-119">Instrukcje: Obsługa kluczy złożonych w zapytaniach</span><span class="sxs-lookup"><span data-stu-id="25dc7-119">How to: Handle Composite Keys in Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="25dc7-120">Opisuje sposób dołączanie więcej niż jedną kolumnę do kwerendy, gdzie operator przyjmuje tylko jeden argument.</span><span class="sxs-lookup"><span data-stu-id="25dc7-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="25dc7-121">Instrukcje: Pobieranie jednocześnie wielu obiektów</span><span class="sxs-lookup"><span data-stu-id="25dc7-121">How to: Retrieve Many Objects At Once</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="25dc7-122">Informacje dotyczące używania <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="25dc7-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="25dc7-123">Instrukcje: Filtrowanie na poziomie elementu DataContext</span><span class="sxs-lookup"><span data-stu-id="25dc7-123">How to: Filter at the DataContext Level</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="25dc7-124">W tym artykule opisano użycie innego <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="25dc7-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="25dc7-125">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="25dc7-125">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 <span data-ttu-id="25dc7-126">Przykłady wiele zapytań.</span><span class="sxs-lookup"><span data-stu-id="25dc7-126">Provides many examples of queries.</span></span>
