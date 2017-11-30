---
title: "Przewodnik programowania w języku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03d4febc7e61425d0057c48949b18281ca3dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="programming-guide"></a><span data-ttu-id="27d77-102">Przewodnik programowania w języku</span><span class="sxs-lookup"><span data-stu-id="27d77-102">Programming Guide</span></span>
<span data-ttu-id="27d77-103">Ta sekcja zawiera informacje o sposobie tworzenia i używania programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="27d77-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="27d77-104">Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można również użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do wykonywania wielu z tych samych zadań.</span><span class="sxs-lookup"><span data-stu-id="27d77-104">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="27d77-105">Możesz również wyszukać Microsoft Docs określonych problemów i mogą uczestniczyć w [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), gdzie można omawiać bardziej złożonych tematów szczegółowo z ekspertami.</span><span class="sxs-lookup"><span data-stu-id="27d77-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="27d77-106">Na koniec [LINQ do SQL: .NET Language-Integrated zapytania dla danych relacyjnych](http://go.microsoft.com/fwlink/?LinkId=93205) oficjalny dokument zawierający szczegóły [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii, wraz z [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] i przykładów kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="27d77-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](http://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27d77-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="27d77-107">In This Section</span></span>  
 [<span data-ttu-id="27d77-108">Tworzenie modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="27d77-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="27d77-109">Opisuje sposób generowania modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="27d77-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="27d77-110">Podczas komunikacji z bazą danych</span><span class="sxs-lookup"><span data-stu-id="27d77-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="27d77-111">Informacje dotyczące używania <xref:System.Data.Linq.DataContext> obiektu jako kanał do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="27d77-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="27d77-112">Zapytanie bazy danych</span><span class="sxs-lookup"><span data-stu-id="27d77-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="27d77-113">Opisuje sposób wykonywania zapytania w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]i zawiera wiele przykładów.</span><span class="sxs-lookup"><span data-stu-id="27d77-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="27d77-114">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="27d77-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="27d77-115">Opisuje sposób zmiany danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="27d77-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="27d77-116">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="27d77-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="27d77-117">W tym artykule opisano obsługę niedostępna na potrzeby debugowania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektów.</span><span class="sxs-lookup"><span data-stu-id="27d77-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="27d77-118">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="27d77-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="27d77-119">Zawiera dodatkowe elementy, takie jak rozwiązywania konfliktów współbieżności, tworzenie nowych baz danych i więcej, aby uzyskać bardziej zaawansowanym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="27d77-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27d77-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="27d77-120">Related Sections</span></span>  
 [<span data-ttu-id="27d77-121">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="27d77-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="27d77-122">Zawiera łącza do tematów dotyczących [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii i zaprezentować funkcje.</span><span class="sxs-lookup"><span data-stu-id="27d77-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="27d77-123">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="27d77-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="27d77-124">Zawiera łącza do tematów, które przedstawiają sposób użycia procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="27d77-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="27d77-125">Wprowadzenie do LINQ</span><span class="sxs-lookup"><span data-stu-id="27d77-125">Introduction to LINQ</span></span>](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)  
 <span data-ttu-id="27d77-126">Zawiera zasoby, aby rozpocząć dowiedzieć się więcej o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27d77-126">Provides resources to help you begin to learn about [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
