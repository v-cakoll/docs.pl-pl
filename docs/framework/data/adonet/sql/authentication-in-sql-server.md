---
title: Uwierzytelnianie programu SQL Server
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 1c918df5de4a66c00f6fd9b9dd1719ac05041ce1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="bc3d7-102">Uwierzytelnianie programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="bc3d7-102">Authentication in SQL Server</span></span>
<span data-ttu-id="bc3d7-103">SQL Server obsługuje dwa tryby uwierzytelniania, tryb uwierzytelniania systemu Windows i w trybie mieszanym.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
-   <span data-ttu-id="bc3d7-104">Uwierzytelnianie systemu Windows jest ustawieniem domyślnym i jest często określany jako zintegrowanych zabezpieczeń, ponieważ ten model zabezpieczeń programu SQL Server jest ściśle zintegrowany z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="bc3d7-105">Określonych kont użytkowników i grup systemu Windows są zaufane logować się do programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="bc3d7-106">Nie masz użytkowników systemu Windows, którzy już zostali uwierzytelnieni do prezentowania dodatkowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
-   <span data-ttu-id="bc3d7-107">Tryb mieszany obsługuje uwierzytelnianie zarówno przez system Windows i program SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="bc3d7-108">Pary nazwy i hasła użytkowników są obsługiwane w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc3d7-109">Firma Microsoft zaleca używanie uwierzytelniania systemu Windows, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="bc3d7-110">Uwierzytelnianie systemu Windows używa szereg zaszyfrowane wiadomości do uwierzytelniania użytkowników w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="bc3d7-111">Podczas logowania do programu SQL Server są używane, nazwy logowania programu SQL Server i hasła są przekazywane w sieci, dzięki czemu ich mniej bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-111">When SQL Server logins are used, SQL Server login names and passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="bc3d7-112">Z uwierzytelnianiem systemu Windows użytkownicy są już zalogowany do systemu Windows i nie trzeba oddzielnie logowania do programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="bc3d7-113">Następujące `SqlConnection.ConnectionString` Określa uwierzytelnianie systemu Windows bez konieczności wprowadzania nazwy użytkownika ani hasła.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring the a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  <span data-ttu-id="bc3d7-114">Logowania różnią się od użytkowników baz danych.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-114">Logins are distinct from database users.</span></span> <span data-ttu-id="bc3d7-115">Nazwy logowania lub grupy systemu Windows musi być zamapowany do bazy danych użytkowników lub ról w oddzielnych operacji.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="bc3d7-116">Następnie przydziel uprawnienia dla użytkowników lub ról, dostęp do obiektów bazy danych.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="bc3d7-117">Scenariusze uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="bc3d7-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="bc3d7-118">Uwierzytelnianie systemu Windows jest zwykle najlepszym rozwiązaniem w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="bc3d7-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
-   <span data-ttu-id="bc3d7-119">Jest kontrolerem domeny.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-119">There is a domain controller.</span></span>  
  
-   <span data-ttu-id="bc3d7-120">Aplikacji i bazy danych znajdują się na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-120">The application and the database are on the same computer.</span></span>  
  
-   <span data-ttu-id="bc3d7-121">Używasz wystąpienia programu SQL Server Express lub LocalDB.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="bc3d7-122">Logowania do programu SQL Server są często używane w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="bc3d7-122">SQL Server logins are often used in the following situations:</span></span>  
  
-   <span data-ttu-id="bc3d7-123">Jeśli masz grupy roboczej.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-123">If you have a workgroup.</span></span>  
  
-   <span data-ttu-id="bc3d7-124">Łączenie użytkowników z innej, niezaufanej domeny.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-124">Users connect from different, non-trusted domains.</span></span>  
  
-   <span data-ttu-id="bc3d7-125">Aplikacje internetowe, takich jak [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc3d7-125">Internet applications, such as [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc3d7-126">Określanie uwierzytelniania systemu Windows nie wyłączać logowania do programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="bc3d7-127">Użyj polecenia ALTER LOGIN Wyłącz [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] instrukcji, aby wyłączyć uprawnieniach logowania programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-127">Use the ALTER LOGIN DISABLE [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="bc3d7-128">Typy logowania</span><span class="sxs-lookup"><span data-stu-id="bc3d7-128">Login Types</span></span>  
 <span data-ttu-id="bc3d7-129">SQL Server obsługuje trzy typy logowania:</span><span class="sxs-lookup"><span data-stu-id="bc3d7-129">SQL Server supports three types of logins:</span></span>  
  
-   <span data-ttu-id="bc3d7-130">Lokalne konto użytkownika systemu Windows lub konto domeny zaufanej.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="bc3d7-131">Program SQL Server korzysta z systemu Windows do uwierzytelniania kont użytkowników systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
-   <span data-ttu-id="bc3d7-132">Grupy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-132">Windows group.</span></span> <span data-ttu-id="bc3d7-133">Udzielanie dostępu do grupy systemu Windows daje dostęp do wszystkich logowania użytkownika do systemu Windows, które są elementami członkowskimi grupy.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
-   <span data-ttu-id="bc3d7-134">Logowanie do serwera SQL.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-134">SQL Server login.</span></span> <span data-ttu-id="bc3d7-135">Program SQL Server przechowuje zarówno nazwa użytkownika oraz skrót hasła w bazie danych master, przy użyciu metody uwierzytelniania wewnętrznego, aby sprawdzić prób logowania.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc3d7-136">Program SQL Server stanowi logowania utworzone na podstawie certyfikaty lub klucze asymetryczne, które są używane tylko w przypadku podpisywania kodu.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="bc3d7-137">Ich nie można nawiązać połączenia z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="bc3d7-138">Uwierzytelnianie w trybie mieszanym</span><span class="sxs-lookup"><span data-stu-id="bc3d7-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="bc3d7-139">Jeśli należy użyć uwierzytelniania w trybie mieszanym, należy utworzyć logowania do programu SQL Server, które są przechowywane w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="bc3d7-140">Następnie należy podać nazwę użytkownika serwera SQL i hasło w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc3d7-141">Instaluje program SQL Server z danych logowania SQL Server o nazwie `sa` (skrót od "administrator systemu").</span><span class="sxs-lookup"><span data-stu-id="bc3d7-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="bc3d7-142">Przypisz silne hasło, aby `sa` logowania i nie używaj `sa` logowania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="bc3d7-143">`sa` Logowania mapowany na `sysadmin` stałej roli serwera, mającej nieodwołalną poświadczeń administracyjnych na całego serwera.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="bc3d7-144">Nie ma żadnych limitów w celu potencjalne szkody, jeśli osoba atakująca uzyska dostęp administrator systemu.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="bc3d7-145">Wszystkie elementy członkowskie systemu Windows `BUILTIN\Administrators` grupy (grupy administratorów lokalnych) są elementami członkowskimi `sysadmin` roli domyślnie, ale można ją usunąć z tej roli.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="bc3d7-146">Program SQL Server stanowi mechanizmów zasad haseł systemu Windows dla logowania do programu SQL Server uruchomionej [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-146">SQL Server provides Windows password policy mechanisms for SQL Server logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="bc3d7-147">Zasady złożoności haseł są przeznaczone do ograniczanie ataków siłowych przez odpowiednie zwiększenie liczby możliwych haseł.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="bc3d7-148">SQL Server można zastosować te same zasady złożoności i wygaśnięcia używane w [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] do hasła używane w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-148">SQL Server can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc3d7-149">Łączenie ciągów połączenia z danych wejściowych użytkownika może sprawić, że użytkownik narażony na atak iniekcji ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="bc3d7-150">Użyj <xref:System.Data.SqlClient.SqlConnectionStringBuilder> Aby utworzyć parametry połączenia nieprawidłową składnię w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="bc3d7-151">Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="bc3d7-151">For more information, see [Connection String Builders](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="bc3d7-152">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="bc3d7-152">External Resources</span></span>  
 <span data-ttu-id="bc3d7-153">Aby uzyskać więcej informacji zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="bc3d7-154">Zasób</span><span class="sxs-lookup"><span data-stu-id="bc3d7-154">Resource</span></span>|<span data-ttu-id="bc3d7-155">Opis</span><span class="sxs-lookup"><span data-stu-id="bc3d7-155">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="bc3d7-156">[Podmioty zabezpieczeń](http://msdn.microsoft.com/library/bb543165.aspx) w dokumentacji SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="bc3d7-156">[Principals](http://msdn.microsoft.com/library/bb543165.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="bc3d7-157">Opisuje logowania i innych podmiotów zabezpieczeń w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bc3d7-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc3d7-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc3d7-158">See Also</span></span>  
 [<span data-ttu-id="bc3d7-159">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="bc3d7-159">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="bc3d7-160">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="bc3d7-160">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="bc3d7-161">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="bc3d7-161">Connecting to a Data Source</span></span>](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="bc3d7-162">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="bc3d7-162">Connection Strings</span></span>](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="bc3d7-163">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="bc3d7-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
