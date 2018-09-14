---
title: Obsługa SqlClient dla LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 1ef75def3f3de44b5e23cb1197a4410dcf6b547f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569089"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="ae96e-102">Obsługa SqlClient dla LocalDB</span><span class="sxs-lookup"><span data-stu-id="ae96e-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="ae96e-103">Począwszy od programu SQL Server o nazwie kodowej Denali Uproszczona wersja programu SQL Server, o nazwie LocalDB, będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="ae96e-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="ae96e-104">W tym temacie omówiono sposób nawiązywania połączeń z bazą danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ae96e-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae96e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae96e-105">Remarks</span></span>  
 <span data-ttu-id="ae96e-106">Aby uzyskać więcej informacji dotyczących programu LocalDB, na przykład zainstaluj LocalDB i skonfiguruj wystąpienia LocalDB zobacz dokumentację SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="ae96e-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="ae96e-107">Aby podsumować, co można zrobić z bazą danych LocalDB:</span><span class="sxs-lookup"><span data-stu-id="ae96e-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="ae96e-108">Tworzenie i uruchamianie wystąpienia LocalDB sqllocaldb.exe lub pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="ae96e-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="ae96e-109">Użyj programu sqlcmd.exe, aby dodawać i modyfikować baz danych w wystąpieniu LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ae96e-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="ae96e-110">Na przykład `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="ae96e-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="ae96e-111">Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby dodać bazę danych do wystąpienia LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ae96e-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="ae96e-112">Korzystając z `AttachDBFilename`, jeśli nie określisz nazwę bazy danych za pomocą `Database` słowo kluczowe parametrów połączenia bazy danych zostaną usunięte z wystąpienia LocalDB po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae96e-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="ae96e-113">Określ wystąpienie programu LocalDB w ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ae96e-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="ae96e-114">Na przykład, Twoja nazwa wystąpienia jest `myInstance`, obejmują parametry połączenia:</span><span class="sxs-lookup"><span data-stu-id="ae96e-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="ae96e-115">`User Instance=True` nie jest dozwolone podczas nawiązywania połączenia z bazą danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ae96e-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="ae96e-116">Możesz pobrać LocalDB z [programu Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="ae96e-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="ae96e-117">Jeśli sqlcmd.exe będzie używać do modyfikacji danych w ramach wystąpienia LocalDB, konieczne będzie sqlcmd z programu SQL Server 2012, którą możesz również pobrać z programu SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="ae96e-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="ae96e-118">Programowe tworzenie nazwanego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="ae96e-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="ae96e-119">Aplikację można utworzenia nazwanego wystąpienia i Określ bazę danych, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ae96e-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="ae96e-120">Określ wystąpienia LocalDB do tworzenia w pliku app.config, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ae96e-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="ae96e-121">Numer wersji wystąpienia powinien być taki sam jak numer wersji instalacji programu LocalDB.</span><span class="sxs-lookup"><span data-stu-id="ae96e-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="ae96e-122">Określ nazwę wystąpienia przy użyciu `server` słowo kluczowe parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="ae96e-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="ae96e-123">Nazwa wystąpienia określonego w `server` słowo kluczowe parametrów połączenia musi pasować do nazwy określonej w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="ae96e-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="ae96e-124">Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby określić. Plik MDF.</span><span class="sxs-lookup"><span data-stu-id="ae96e-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae96e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae96e-125">See Also</span></span>  
 [<span data-ttu-id="ae96e-126">Funkcje Serwera SQL i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ae96e-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [<span data-ttu-id="ae96e-127">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ae96e-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
