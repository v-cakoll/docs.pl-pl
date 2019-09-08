---
title: 'Instrukcje: Dynamiczne tworzenie bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 4cadf20cdadb39483f26a29619cae058eac47e50
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793655"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="fc765-102">Instrukcje: Dynamiczne tworzenie bazy danych</span><span class="sxs-lookup"><span data-stu-id="fc765-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="fc765-103">W LINQ to SQL model obiektów jest mapowany do relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fc765-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="fc765-104">Mapowanie jest włączane przy użyciu mapowania opartego na atrybutach lub zewnętrznego pliku mapowania, aby opisać strukturę relacyjnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fc765-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="fc765-105">W obu scenariuszach jest wystarczająco dużo informacji o relacyjnej bazie danych, którą można utworzyć nowe wystąpienie bazy danych przy użyciu <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fc765-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="fc765-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy replikę bazy danych tylko do zakresu informacji zakodowanych w modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="fc765-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="fc765-107">Mapowanie plików i atrybutów z modelu obiektów może nie zakodować wszystkiego o strukturze istniejącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fc765-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="fc765-108">Informacje o mapowaniu nie reprezentują zawartości funkcji zdefiniowanych przez użytkownika, procedur składowanych, wyzwalaczy ani ograniczeń check.</span><span class="sxs-lookup"><span data-stu-id="fc765-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="fc765-109">To zachowanie jest wystarczające dla różnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="fc765-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="fc765-110"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metody można użyć w dowolnej liczbie scenariuszy, zwłaszcza jeśli znany dostawca danych, taki jak Microsoft SQL Server 2008 jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="fc765-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="fc765-111">Typowe scenariusze obejmują:</span><span class="sxs-lookup"><span data-stu-id="fc765-111">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="fc765-112">Tworzysz aplikację, która automatycznie instaluje się w systemie klienta.</span><span class="sxs-lookup"><span data-stu-id="fc765-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="fc765-113">Tworzysz aplikację kliencką, która wymaga lokalnej bazy danych do zapisania stanu offline.</span><span class="sxs-lookup"><span data-stu-id="fc765-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="fc765-114">Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody z SQL Server przy użyciu pliku. mdf lub nazwy wykazu, w zależności od parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="fc765-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="fc765-115">program używa parametrów połączenia w celu zdefiniowania bazy danych, która ma zostać utworzona, oraz na serwerze, na którym ma zostać utworzona baza danych.</span><span class="sxs-lookup"><span data-stu-id="fc765-115">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc765-116">Jeśli to możliwe, Użyj zintegrowanych zabezpieczeń systemu Windows do łączenia się z bazą danych, tak aby hasła nie były wymagane w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="fc765-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc765-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc765-117">Example</span></span>  
 <span data-ttu-id="fc765-118">Poniższy kod przedstawia przykład sposobu tworzenia nowej bazy danych o nazwie moje DVD. mdf.</span><span class="sxs-lookup"><span data-stu-id="fc765-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="fc765-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc765-119">Example</span></span>  
 <span data-ttu-id="fc765-120">Aby utworzyć bazę danych, można użyć modelu obiektów, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fc765-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="fc765-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc765-121">Example</span></span>  
 <span data-ttu-id="fc765-122">Podczas kompilowania aplikacji, która automatycznie instaluje się w systemie klienta, sprawdź, czy baza danych już istnieje i upuść ją przed utworzeniem nowej.</span><span class="sxs-lookup"><span data-stu-id="fc765-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="fc765-123">Klasa zawiera metody<xref:System.Data.Linq.DataContext.DeleteDatabase%2A> i, które ułatwiają przetworzenie tego procesu. <xref:System.Data.Linq.DataContext.DatabaseExists%2A> <xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="fc765-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="fc765-124">W poniższym przykładzie pokazano jeden z metod, których można użyć do wdrożenia tego podejścia:</span><span class="sxs-lookup"><span data-stu-id="fc765-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="fc765-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc765-125">See also</span></span>

- [<span data-ttu-id="fc765-126">Mapowanie oparte na atrybutach</span><span class="sxs-lookup"><span data-stu-id="fc765-126">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="fc765-127">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="fc765-127">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="fc765-128">Mapowania typów środowiska SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="fc765-128">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="fc765-129">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="fc765-129">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="fc765-130">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="fc765-130">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
