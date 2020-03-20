---
title: Przewodnik programowania
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 542567cf07e86b642a23a879fa6e5476253005b8
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848941"
---
# <a name="programming-guide"></a><span data-ttu-id="62a1c-102">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="62a1c-102">Programming Guide</span></span>
<span data-ttu-id="62a1c-103">Ta sekcja zawiera informacje dotyczące sposobu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzenia i używania modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="62a1c-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="62a1c-104">Jeśli używasz programu Visual Studio, można również użyć Projektanta relacyjnego obiektu do wykonywania wielu z tych samych zadań.</span><span class="sxs-lookup"><span data-stu-id="62a1c-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="62a1c-105">Można również wyszukać Microsoft Docs dla konkretnych problemów, a także uczestniczyć w [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), gdzie można omówić bardziej złożone tematy szczegółowo z ekspertami.</span><span class="sxs-lookup"><span data-stu-id="62a1c-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="62a1c-106">Na koniec [LINQ do SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, wraz z przykładami kodu języka Visual Basic i C#.</span><span class="sxs-lookup"><span data-stu-id="62a1c-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62a1c-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="62a1c-107">In This Section</span></span>  
 [<span data-ttu-id="62a1c-108">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="62a1c-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="62a1c-109">W tym artykule opisano sposób generowania modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="62a1c-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="62a1c-110">Komunikacja z bazą danych</span><span class="sxs-lookup"><span data-stu-id="62a1c-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="62a1c-111">W tym artykule opisano sposób używania <xref:System.Data.Linq.DataContext> obiektu jako przewodu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="62a1c-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="62a1c-112">Wykonywanie zapytania w bazie danych</span><span class="sxs-lookup"><span data-stu-id="62a1c-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="62a1c-113">Opisuje sposób wykonywania zapytań w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], i zawiera wiele przykładów.</span><span class="sxs-lookup"><span data-stu-id="62a1c-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="62a1c-114">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="62a1c-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="62a1c-115">Opisuje, jak zmienić dane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="62a1c-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="62a1c-116">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="62a1c-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="62a1c-117">W tym artykule opisano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługę dostępnych dla projektów debugowania.</span><span class="sxs-lookup"><span data-stu-id="62a1c-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="62a1c-118">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="62a1c-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="62a1c-119">Zawiera dodatkowe elementy, takie jak rozwiązywanie konfliktów współbieżności, tworzenie nowych baz danych i inne, dla bardziej zaawansowanych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="62a1c-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="62a1c-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="62a1c-120">Related Sections</span></span>  
 [<span data-ttu-id="62a1c-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="62a1c-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="62a1c-122">Zawiera łącza do tematów, które wyjaśniają technologię [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] i demonstrują funkcje.</span><span class="sxs-lookup"><span data-stu-id="62a1c-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="62a1c-123">Procedury przechowywane</span><span class="sxs-lookup"><span data-stu-id="62a1c-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="62a1c-124">Zawiera łącza do tematów, które ilustrują sposób korzystania z procedur przechowywanych.</span><span class="sxs-lookup"><span data-stu-id="62a1c-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="62a1c-125">Wprowadzenie do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="62a1c-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="62a1c-126">Udostępnia zasoby ułatwiające rozpoczęcie nauki o LINQ do SQL przy użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="62a1c-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="62a1c-127">Wprowadzenie do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62a1c-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="62a1c-128">Udostępnia zasoby ułatwiające rozpoczęcie nauki o linq do sql przy użyciu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="62a1c-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
