---
title: 'Instrukcje: Dynamiczne tworzenie bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 92db9bdb209a542cc4fa269b35bfa98f8f20d2b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940089"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="105c6-102">Instrukcje: Dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="105c6-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="105c6-103">W LINQ to SQL model obiektów jest mapowany do relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="105c6-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="105c6-104">Mapowanie jest włączane przy użyciu mapowania opartego na atrybutach lub zewnętrznego pliku mapowania, aby opisać strukturę relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="105c6-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="105c6-105">W obu scenariuszach jest wystarczająco dużo informacji o relacyjnej bazie danych, którą można utworzyć nowe wystąpienie bazy danych przy użyciu <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="105c6-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="105c6-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy replikę bazy danych tylko do zakresu informacji zakodowanych w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="105c6-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="105c6-107">Mapowanie plików i atrybutów z modelu obiektów może nie zakodować wszystkiego o strukturze istniejącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="105c6-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="105c6-108">Informacje o mapowaniu nie reprezentują zawartości funkcji zdefiniowanych przez użytkownika, procedur składowanych, wyzwalaczy ani ograniczeń check.</span><span class="sxs-lookup"><span data-stu-id="105c6-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="105c6-109">To zachowanie jest wystarczające dla różnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="105c6-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="105c6-110"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metody można użyć w dowolnej liczbie scenariuszy, zwłaszcza jeśli znany dostawca danych, taki jak Microsoft SQL Server 2008 jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="105c6-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="105c6-111">Typowe scenariusze obejmują:</span><span class="sxs-lookup"><span data-stu-id="105c6-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="105c6-112">Tworzysz aplikację, która automatycznie instaluje się w systemie klienta.</span><span class="sxs-lookup"><span data-stu-id="105c6-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="105c6-113">Tworzysz aplikację kliencką, która wymaga lokalnej bazy danych do zapisania stanu offline.</span><span class="sxs-lookup"><span data-stu-id="105c6-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="105c6-114">Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody z SQL Server przy użyciu pliku. mdf lub nazwy wykazu, w zależności od parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="105c6-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="105c6-115">program używa parametrów połączenia w celu zdefiniowania bazy danych, która ma zostać utworzona, oraz na serwerze, na którym ma zostać utworzona baza danych.</span><span class="sxs-lookup"><span data-stu-id="105c6-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="105c6-116">Jeśli to możliwe, Użyj zintegrowanych zabezpieczeń systemu Windows do łączenia się z bazą danych, tak aby hasła nie były wymagane w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="105c6-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="105c6-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="105c6-117">Example</span></span>  
 <span data-ttu-id="105c6-118">Poniższy kod przedstawia przykład sposobu tworzenia nowej bazy danych o nazwie moje DVD. mdf.</span><span class="sxs-lookup"><span data-stu-id="105c6-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="105c6-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="105c6-119">Example</span></span>  
 <span data-ttu-id="105c6-120">Aby utworzyć bazę danych, można użyć modelu obiektów, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="105c6-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="105c6-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="105c6-121">Example</span></span>  
 <span data-ttu-id="105c6-122">Podczas kompilowania aplikacji, która automatycznie instaluje się w systemie klienta, sprawdź, czy baza danych już istnieje i upuść ją przed utworzeniem nowej.</span><span class="sxs-lookup"><span data-stu-id="105c6-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="105c6-123">Klasa zawiera metody<xref:System.Data.Linq.DataContext.DeleteDatabase%2A> i, które ułatwiają przetworzenie tego procesu. <xref:System.Data.Linq.DataContext.DatabaseExists%2A> <xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="105c6-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="105c6-124">W poniższym przykładzie pokazano jeden z metod, których można użyć do wdrożenia tego podejścia:</span><span class="sxs-lookup"><span data-stu-id="105c6-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="105c6-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="105c6-125">See also</span></span>

- [<span data-ttu-id="105c6-126">Mapowanie oparte na atrybutach</span><span class="sxs-lookup"><span data-stu-id="105c6-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="105c6-127">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="105c6-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [<span data-ttu-id="105c6-128">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="105c6-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [<span data-ttu-id="105c6-129">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="105c6-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="105c6-130">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="105c6-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
