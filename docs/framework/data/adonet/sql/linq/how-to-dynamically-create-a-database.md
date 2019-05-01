---
title: 'Instrukcje: Dynamiczne tworzenie bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: ab5e2867ce85fcc82e1114696c129aae878bbee6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877269"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="09b95-102">Instrukcje: Dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="09b95-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="09b95-103">W składniku LINQ to SQL na model obiektów jest mapowany w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="09b95-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="09b95-104">Mapowanie jest włączane przy użyciu opartych na atrybutach mapowania lub pliku mapowania zewnętrznych do opisania struktury relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="09b95-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="09b95-105">W obu przypadkach jest za mało informacji na temat relacyjnej bazy danych, możesz utworzyć nowe wystąpienie bazy danych przy użyciu <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="09b95-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="09b95-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy replikę bazy danych, w jakim informacji zakodowane w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="09b95-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="09b95-107">Mapowanie plików i atrybuty z modelu obiektów może nie kodowania wszystkie informacje o strukturze istniejącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="09b95-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="09b95-108">Informacji o mapowaniu nie reprezentują zawartości, funkcje zdefiniowane przez użytkownika, procedury składowane, wyzwalacze lub ograniczenia check.</span><span class="sxs-lookup"><span data-stu-id="09b95-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="09b95-109">To zachowanie jest wystarczająca dla różnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="09b95-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="09b95-110">Możesz użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody w dowolnej liczbie scenariuszy, zwłaszcza, jeśli dostawca znanych danych, takich jak Microsoft SQL Server 2008 jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="09b95-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="09b95-111">Typowe scenariusze obejmują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="09b95-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="09b95-112">Tworzysz aplikację, która automatycznie instaluje się w systemie klienta.</span><span class="sxs-lookup"><span data-stu-id="09b95-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="09b95-113">Tworzysz aplikację kliencką, która wymaga lokalnej bazy danych można zapisać stanu offline.</span><span class="sxs-lookup"><span data-stu-id="09b95-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="09b95-114">Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody z programem SQL Server przy użyciu pliku MDF lub nazwę katalogu, w zależności od parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="09b95-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="09b95-115">używa parametrów połączenia Aby zdefiniować utworzenie bazy danych i bazy danych na serwer, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="09b95-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09b95-116">Możliwe, używaj zintegrowanych zabezpieczeń Windows do łączenia z bazą danych, dzięki czemu hasła nie są wymagane w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="09b95-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09b95-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="09b95-117">Example</span></span>  
 <span data-ttu-id="09b95-118">Poniższy kod zawiera przykład sposobu tworzenia nowej bazy danych o nazwie MyDVDs.mdf.</span><span class="sxs-lookup"><span data-stu-id="09b95-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="09b95-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="09b95-119">Example</span></span>  
 <span data-ttu-id="09b95-120">Model obiektów umożliwia tworzenie bazy danych, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="09b95-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="09b95-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="09b95-121">Example</span></span>  
 <span data-ttu-id="09b95-122">Podczas tworzenia aplikacji, które automatycznie instaluje się w systemie klienta, zobacz, czy baza danych już istnieje i upuść go przed utworzeniem nowej.</span><span class="sxs-lookup"><span data-stu-id="09b95-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="09b95-123"><xref:System.Data.Linq.DataContext> Klasa udostępnia <xref:System.Data.Linq.DataContext.DatabaseExists%2A> i <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metody ułatwiające przeprowadzenie tego procesu.</span><span class="sxs-lookup"><span data-stu-id="09b95-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="09b95-124">Poniższy przykład przedstawia jeden ze sposobów osiągnięcia tych metod może służyć do wdrożenia tego rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="09b95-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="09b95-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09b95-125">See also</span></span>

- [<span data-ttu-id="09b95-126">Mapowanie oparte na atrybutach</span><span class="sxs-lookup"><span data-stu-id="09b95-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="09b95-127">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="09b95-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="09b95-128">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="09b95-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="09b95-129">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="09b95-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="09b95-130">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="09b95-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
