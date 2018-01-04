---
title: 'Porady: dynamiczne tworzenie bazy danych'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27986236c6b693b2c89157229cd79f0de64266e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="a8542-102">Porady: dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="a8542-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="a8542-103">W składniku LINQ to SQL model obiektów jest mapowany relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a8542-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="a8542-104">Mapowanie jest włączane przy użyciu mapowania na podstawie atrybutów lub plik mapowania zewnętrznych do opisania struktury relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a8542-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="a8542-105">W obu przypadkach ma wystarczającej ilości informacji o relacyjnej bazy danych, możesz utworzyć nowe wystąpienie klasy przy użyciu bazy danych <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a8542-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a8542-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy repliki bazy danych tylko do danych zakodowanych w modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8542-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="a8542-107">Mapowanie pliki i atrybutów z modelu obiektów może nie Koduj wszystkie informacje o strukturze istniejącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a8542-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="a8542-108">Informacje o mapowaniu nie reprezentuje zawartości funkcje zdefiniowane przez użytkownika, procedury składowane, wyzwalacze lub ograniczenia sprawdzania.</span><span class="sxs-lookup"><span data-stu-id="a8542-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="a8542-109">To zachowanie jest wystarczająca dla różnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="a8542-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="a8542-110">Można użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody we wszystkich scenariuszach, zwłaszcza, jeśli dostawca znanych danych, takich jak Microsoft SQL Server 2008 jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="a8542-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="a8542-111">Typowe scenariusze są następujące:</span><span class="sxs-lookup"><span data-stu-id="a8542-111">Typical scenarios include the following:</span></span>  
  
-   <span data-ttu-id="a8542-112">Tworzysz aplikację, która automatycznie instaluje się na komputerze klienta.</span><span class="sxs-lookup"><span data-stu-id="a8542-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
-   <span data-ttu-id="a8542-113">Tworzysz aplikacji klienckiej, która wymaga lokalnej bazy danych można zapisać stanu w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="a8542-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="a8542-114">Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody z programem SQL Server przy użyciu pliku .mdf lub nazwę katalogu, w zależności od parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="a8542-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a8542-115">używa parametrów połączenia, aby zdefiniować bazy danych ma zostać utworzony, a na serwer, który ma być tworzony bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a8542-115"> uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8542-116">Jeśli to możliwe, Użyj zintegrowanych zabezpieczeń systemu Windows do łączenia z bazą danych, dzięki czemu hasła nie są wymagane w ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a8542-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8542-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8542-117">Example</span></span>  
 <span data-ttu-id="a8542-118">Następujący kod stanowi przykład tworzenia nowej bazy danych o nazwie MyDVDs.mdf.</span><span class="sxs-lookup"><span data-stu-id="a8542-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="a8542-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8542-119">Example</span></span>  
 <span data-ttu-id="a8542-120">Model obiektów służy do tworzenia bazy danych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a8542-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="a8542-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8542-121">Example</span></span>  
 <span data-ttu-id="a8542-122">Podczas tworzenia aplikacji, która automatycznie instaluje się na komputerze klienta, zobacz, czy baza danych już istnieje i Porzuć go przed utworzeniem nowego.</span><span class="sxs-lookup"><span data-stu-id="a8542-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="a8542-123"><xref:System.Data.Linq.DataContext> Klasa udostępnia <xref:System.Data.Linq.DataContext.DatabaseExists%2A> i <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metod, które zapewniają pomoc podczas tego procesu.</span><span class="sxs-lookup"><span data-stu-id="a8542-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="a8542-124">Poniższy przykład przedstawia sposób którą tych metod można użyć do wdrożenia tego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="a8542-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a8542-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8542-125">See Also</span></span>  
 [<span data-ttu-id="a8542-126">Mapowanie oparte na atrybutach</span><span class="sxs-lookup"><span data-stu-id="a8542-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="a8542-127">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="a8542-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="a8542-128">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="a8542-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="a8542-129">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="a8542-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="a8542-130">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="a8542-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
