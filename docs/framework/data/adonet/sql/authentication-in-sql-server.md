---
title: Uwierzytelnianie w programie SQL Server
description: Dowiedz się więcej o uwierzytelnianiu SQL Server ADO.NET, w tym trybem uwierzytelniania systemu Windows i trybem mieszanym.
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: e9915598acfbdefb59069d6a9c6ef4b7c824e4c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286549"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="57a1a-103">Uwierzytelnianie w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="57a1a-103">Authentication in SQL Server</span></span>
<span data-ttu-id="57a1a-104">SQL Server obsługuje dwa tryby uwierzytelniania, tryb uwierzytelniania systemu Windows i tryb mieszany.</span><span class="sxs-lookup"><span data-stu-id="57a1a-104">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="57a1a-105">Uwierzytelnianie systemu Windows jest ustawieniem domyślnym i jest często określane jako zabezpieczenia zintegrowane, ponieważ ten SQL Server model zabezpieczeń jest ściśle zintegrowany z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="57a1a-105">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="57a1a-106">Określone konta użytkowników i grup systemu Windows są zaufane, aby zalogować się do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-106">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="57a1a-107">Użytkownicy systemu Windows, którzy zostali już uwierzytelnieni, nie muszą przedstawić dodatkowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="57a1a-107">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="57a1a-108">Tryb mieszany obsługuje uwierzytelnianie zarówno w systemie Windows, jak i przez SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-108">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="57a1a-109">Pary nazwa użytkownika i hasło są utrzymywane w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-109">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="57a1a-110">Zalecamy używanie uwierzytelniania systemu Windows wszędzie tam, gdzie to możliwe.</span><span class="sxs-lookup"><span data-stu-id="57a1a-110">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="57a1a-111">Uwierzytelnianie systemu Windows korzysta z serii zaszyfrowanych komunikatów do uwierzytelniania użytkowników w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-111">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="57a1a-112">Gdy są używane SQL Server logowania, nazwy logowania SQL Server i szyfrowane hasła są przesyłane przez sieć, co sprawia, że są one mniej bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="57a1a-112">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="57a1a-113">W przypadku uwierzytelniania systemu Windows użytkownicy są już zalogowani do systemu Windows i nie muszą logować się oddzielnie do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-113">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="57a1a-114">Poniżej `SqlConnection.ConnectionString` określono uwierzytelnianie systemu Windows bez konieczności podawania nazwy użytkownika lub hasła.</span><span class="sxs-lookup"><span data-stu-id="57a1a-114">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="57a1a-115">Nazwy logowania różnią się od użytkowników bazy danych.</span><span class="sxs-lookup"><span data-stu-id="57a1a-115">Logins are distinct from database users.</span></span> <span data-ttu-id="57a1a-116">Musisz zamapować nazwy logowania lub grupy systemu Windows na użytkowników lub role bazy danych w osobnej operacji.</span><span class="sxs-lookup"><span data-stu-id="57a1a-116">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="57a1a-117">Następnie Udziel uprawnień użytkownikom lub rolom dostępu do obiektów bazy danych.</span><span class="sxs-lookup"><span data-stu-id="57a1a-117">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="57a1a-118">Scenariusze uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="57a1a-118">Authentication Scenarios</span></span>  
 <span data-ttu-id="57a1a-119">Uwierzytelnianie systemu Windows jest zazwyczaj najlepszym wyborem w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="57a1a-119">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="57a1a-120">Istnieje kontroler domeny.</span><span class="sxs-lookup"><span data-stu-id="57a1a-120">There is a domain controller.</span></span>  
  
- <span data-ttu-id="57a1a-121">Aplikacja i baza danych znajdują się na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="57a1a-121">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="57a1a-122">Używasz wystąpienia SQL Server Express lub LocalDB.</span><span class="sxs-lookup"><span data-stu-id="57a1a-122">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="57a1a-123">Identyfikatory logowania SQL Server często są używane w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="57a1a-123">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="57a1a-124">Jeśli masz grupę roboczą.</span><span class="sxs-lookup"><span data-stu-id="57a1a-124">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="57a1a-125">Użytkownicy łączą się z różnych domen niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="57a1a-125">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="57a1a-126">Aplikacje internetowe, takie jak ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="57a1a-126">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57a1a-127">Określenie uwierzytelniania systemu Windows nie powoduje wyłączenia logowania SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-127">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="57a1a-128">Użyj instrukcji ALTER LOGIN DISABLE Transact-SQL, aby wyłączyć logowanie o wysokim poziomie uprawnień SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-128">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="57a1a-129">Typy logowania</span><span class="sxs-lookup"><span data-stu-id="57a1a-129">Login Types</span></span>  
 <span data-ttu-id="57a1a-130">SQL Server obsługuje trzy typy logowań:</span><span class="sxs-lookup"><span data-stu-id="57a1a-130">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="57a1a-131">Lokalne konto użytkownika systemu Windows lub zaufane konto domeny.</span><span class="sxs-lookup"><span data-stu-id="57a1a-131">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="57a1a-132">SQL Server opiera się na systemie Windows do uwierzytelniania kont użytkowników systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57a1a-132">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="57a1a-133">Grupa systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="57a1a-133">Windows group.</span></span> <span data-ttu-id="57a1a-134">Przyznanie dostępu do grupy systemu Windows umożliwia dostęp do wszystkich logowań użytkowników systemu Windows, które są członkami tej grupy.</span><span class="sxs-lookup"><span data-stu-id="57a1a-134">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="57a1a-135">SQL Server logowania.</span><span class="sxs-lookup"><span data-stu-id="57a1a-135">SQL Server login.</span></span> <span data-ttu-id="57a1a-136">SQL Server przechowuje zarówno nazwę użytkownika, jak i skrót hasła w bazie danych Master, przy użyciu wewnętrznych metod uwierzytelniania do weryfikowania prób logowania.</span><span class="sxs-lookup"><span data-stu-id="57a1a-136">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57a1a-137">SQL Server udostępnia nazwy logowania utworzone na podstawie certyfikatów lub kluczy asymetrycznych, które są używane tylko do podpisywania kodu.</span><span class="sxs-lookup"><span data-stu-id="57a1a-137">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="57a1a-138">Nie można ich używać do nawiązywania połączenia z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-138">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="57a1a-139">Uwierzytelnianie w trybie mieszanym</span><span class="sxs-lookup"><span data-stu-id="57a1a-139">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="57a1a-140">Jeśli konieczne jest użycie uwierzytelniania w trybie mieszanym, należy utworzyć SQL Server nazwy logowania, które są przechowywane w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-140">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="57a1a-141">Następnie należy podać nazwę użytkownika SQL Server i hasło w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="57a1a-141">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="57a1a-142">SQL Server instalowany przy użyciu SQL Server logowania o nazwie `sa` (skrót "administrator systemu").</span><span class="sxs-lookup"><span data-stu-id="57a1a-142">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="57a1a-143">Przypisz silne hasło do `sa` nazwy logowania i nie używaj `sa` nazwy logowania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57a1a-143">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="57a1a-144">Dane `sa` logowania są mapowane na `sysadmin` stałą rolę serwera, która ma nieodwołalne poświadczenia administracyjne na całym serwerze.</span><span class="sxs-lookup"><span data-stu-id="57a1a-144">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="57a1a-145">Jeśli osoba atakująca uzyska dostęp jako administrator systemu, nie ma żadnych ograniczeń dotyczących potencjalnego uszkodzenia.</span><span class="sxs-lookup"><span data-stu-id="57a1a-145">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="57a1a-146">Wszyscy członkowie grupy systemu Windows `BUILTIN\Administrators` (grupa administratorów lokalnych) są `sysadmin` Domyślnie członkami roli, ale można ją usunąć z tej roli.</span><span class="sxs-lookup"><span data-stu-id="57a1a-146">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="57a1a-147">SQL Server zapewnia mechanizmy zasad haseł systemu Windows dla SQL Server logowania.</span><span class="sxs-lookup"><span data-stu-id="57a1a-147">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="57a1a-148">Zasady złożoności haseł zaprojektowano w celu powstrzymania ataków na ataki przez zwiększenie liczby możliwych haseł.</span><span class="sxs-lookup"><span data-stu-id="57a1a-148">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="57a1a-149">SQL Server mogą zastosować te same zasady złożoności i wygasania do haseł używanych wewnątrz SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-149">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="57a1a-150">Łączenie parametrów połączenia z danymi wejściowymi użytkownika może spowodować zagrożenie dla ataku polegającego na iniekcji parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="57a1a-150">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="57a1a-151">Użyj, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> Aby utworzyć składniowo prawidłowe parametry połączenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="57a1a-151">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="57a1a-152">Aby uzyskać więcej informacji, zobacz [konstruktory parametrów połączenia](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="57a1a-152">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="57a1a-153">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="57a1a-153">External Resources</span></span>  
 <span data-ttu-id="57a1a-154">Więcej informacji zawierają poniższe zasoby.</span><span class="sxs-lookup"><span data-stu-id="57a1a-154">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="57a1a-155">Zasób</span><span class="sxs-lookup"><span data-stu-id="57a1a-155">Resource</span></span>|<span data-ttu-id="57a1a-156">Opis</span><span class="sxs-lookup"><span data-stu-id="57a1a-156">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="57a1a-157">Podmioty zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="57a1a-157">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="57a1a-158">Opisuje nazwy logowania i inne podmioty zabezpieczeń w SQL Server.</span><span class="sxs-lookup"><span data-stu-id="57a1a-158">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57a1a-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57a1a-159">See also</span></span>

- [<span data-ttu-id="57a1a-160">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="57a1a-160">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="57a1a-161">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="57a1a-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="57a1a-162">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="57a1a-162">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="57a1a-163">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="57a1a-163">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="57a1a-164">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="57a1a-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
