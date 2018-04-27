---
title: Zabezpieczenia w składniku LINQ to SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 96951b3b3c8a6ee93a83ba24f6c6a19c3e36381c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="security-in-linq-to-sql"></a><span data-ttu-id="5ea24-102">Zabezpieczenia w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5ea24-102">Security in LINQ to SQL</span></span>
<span data-ttu-id="5ea24-103">Zagrożenia bezpieczeństwa są zawsze wtedy, gdy połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="5ea24-103">Security risks are always present when you connect to a database.</span></span> <span data-ttu-id="5ea24-104">Chociaż LINQ do SQL może zawierać niektóre nowe sposoby pracy z danymi w programie SQL Server, nie ma żadnych dodatkowe mechanizmy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5ea24-104">Although LINQ to SQL may include some new ways to work with data in SQL Server, it does not provide any additional security mechanisms.</span></span>  
  
## <a name="access-control-and-authentication"></a><span data-ttu-id="5ea24-105">Kontrola dostępu i uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="5ea24-105">Access Control and Authentication</span></span>  
 <span data-ttu-id="5ea24-106">LINQ do SQL nie ma własne mechanizmy modelu lub uwierzytelniania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5ea24-106">LINQ to SQL does not have its own user model or authentication mechanisms.</span></span> <span data-ttu-id="5ea24-107">Użyj zabezpieczeń serwera SQL, aby kontrolować dostęp do bazy danych, tabele bazy danych, widoków i procedur składowanych, które są mapowane do modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ea24-107">Use SQL Server Security to control access to the database, database tables, views, and stored procedures that are mapped to your object model.</span></span> <span data-ttu-id="5ea24-108">Minimalny wymagany udostępnić użytkownikom i wymagają silnego hasła do uwierzytelnienia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5ea24-108">Grant the minimally required access to users and require strong passwords for user authentication.</span></span>  
  
## <a name="mapping-and-schema-information"></a><span data-ttu-id="5ea24-109">Mapowania i informacje o schemacie</span><span class="sxs-lookup"><span data-stu-id="5ea24-109">Mapping and Schema Information</span></span>  
 <span data-ttu-id="5ea24-110">SQL CLR typu bazy danych schematu informacji dotyczących mapowania i w modelu obiektów lub zewnętrznego mapowania pliku jest dostępna dla wszystkich dostęp do tych plików w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="5ea24-110">SQL-CLR type mapping and database schema information in your object model or external mapping file is available for all with access to those files in the file system.</span></span> <span data-ttu-id="5ea24-111">Załóżmy, że informacje o schemacie będą dostępne dla wszystkich, kto ma dostęp do modelu obiektu lub plik mapowania zewnętrznych. Aby zapobiec szerszego dostępu do informacji o schemacie, umożliwia ochronę plików źródłowych i mapowania plików mechanizmy zabezpieczeń pliku.</span><span class="sxs-lookup"><span data-stu-id="5ea24-111">Assume that schema information will be available to all who can access the object model or external mapping file.To prevent more widespread access to schema information, use file security mechanisms to secure source files and mapping files.</span></span>  
  
## <a name="connection-strings"></a><span data-ttu-id="5ea24-112">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="5ea24-112">Connection Strings</span></span>  
 <span data-ttu-id="5ea24-113">Za pomocą hasła w parametrach połączenia należy unikać zawsze, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="5ea24-113">Using passwords in connection strings should be avoided whenever possible.</span></span> <span data-ttu-id="5ea24-114">Nie jest ciąg połączenia w sobie stanowić ryzyko dla bezpieczeństwa tylko parametry połączenia mogą również dodać w postaci zwykłego tekstu w modelu obiektu lub plik mapowania zewnętrznych przy użyciu narzędzia Projektant obiektów relacyjnych lub SQLMetal wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5ea24-114">Not only is a connection string a security risk in its own right, but the connection string may also be added in clear text to the object model or external mapping file when using the Object Relational Designer or SQLMetal command-line tool.</span></span> <span data-ttu-id="5ea24-115">Każda osoba mająca dostęp do modelu obiektu lub plik mapowania zewnętrznej za pośrednictwem systemu plików można zobacz hasło połączenia (jeśli znajduje się on w parametrach połączenia).</span><span class="sxs-lookup"><span data-stu-id="5ea24-115">Anyone with access to the object model or external mapping file via the file system could see the connection password (if it is included in the connection string).</span></span>  
  
 <span data-ttu-id="5ea24-116">Aby zminimalizować ryzyko, Użyj zintegrowanych zabezpieczeń, aby wprowadzić zaufanego połączenia z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5ea24-116">To minimize such risks, use integrated security to make a trusted connection with SQL Server.</span></span> <span data-ttu-id="5ea24-117">Przy użyciu tej metody, nie trzeba przechowywać hasła w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="5ea24-117">By using this approach, you do not have to store a password in the connection string.</span></span> <span data-ttu-id="5ea24-118">Aby uzyskać więcej informacji, zobacz [zabezpieczeń serwera SQL](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span><span class="sxs-lookup"><span data-stu-id="5ea24-118">For more information, see [SQL Server Security](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).</span></span>  
  
 <span data-ttu-id="5ea24-119">W przypadku braku zintegrowane zabezpieczenia hasła w postaci zwykłego tekstu będą potrzebne w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="5ea24-119">In the absence of integrated security, a clear-text password will be needed in the connection string.</span></span> <span data-ttu-id="5ea24-120">Najlepszy sposób, aby pomóc w zabezpieczeniu parametrów połączenia, rosnąco ryzyka, jest następujący:</span><span class="sxs-lookup"><span data-stu-id="5ea24-120">The best way to help secure your connection string, in increasing order of risk, is as follows:</span></span>  
  
-   <span data-ttu-id="5ea24-121">Użyj zintegrowanych zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5ea24-121">Use integrated security.</span></span>  
  
-   <span data-ttu-id="5ea24-122">Zabezpieczenie parametry połączenia przy użyciu haseł i zminimalizować przekazywanie ciągi połączenia.</span><span class="sxs-lookup"><span data-stu-id="5ea24-122">Secure connection strings with passwords and minimize passing around connection strings.</span></span>  
  
-   <span data-ttu-id="5ea24-123">Użyj <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> klasy zamiast ciągu połączenia, ponieważ ogranicza czas trwania zagrożeń.</span><span class="sxs-lookup"><span data-stu-id="5ea24-123">Use a <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> class instead of a connection string since it limits the duration of exposure.</span></span> <span data-ttu-id="5ea24-124">LINQ do SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> klasy można wdrożyć przy użyciu <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="5ea24-124">The LINQ to SQL <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> class can be instantiated using a <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
-   <span data-ttu-id="5ea24-125">Zminimalizować okresy istnienia i touch punkty dla wszystkich ciągów połączenia.</span><span class="sxs-lookup"><span data-stu-id="5ea24-125">Minimize lifetimes and touch points for all connection strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea24-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ea24-126">See Also</span></span>  
 [<span data-ttu-id="5ea24-127">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="5ea24-127">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="5ea24-128">Często zadawane pytania</span><span class="sxs-lookup"><span data-stu-id="5ea24-128">Frequently Asked Questions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
