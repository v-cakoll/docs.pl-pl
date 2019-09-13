---
title: Obsługa SqlClient w bazie danych LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: d02524cd5901adeca7bc36d6fd13c7abdc46c69b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894401"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="dc1b1-102">Obsługa SqlClient w bazie danych LocalDB</span><span class="sxs-lookup"><span data-stu-id="dc1b1-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="dc1b1-103">Począwszy od SQL Server nazwy Denali, zostanie udostępniona uproszczona wersja SQL Server o nazwie LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="dc1b1-104">W tym temacie omówiono sposób nawiązywania połączenia z bazą danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc1b1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc1b1-105">Remarks</span></span>  
 <span data-ttu-id="dc1b1-106">Aby uzyskać więcej informacji na temat LocalDB, w tym sposobu instalowania LocalDB i konfigurowania wystąpienia LocalDB, zobacz SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="dc1b1-107">Aby podsumować, co możesz zrobić z LocalDB:</span><span class="sxs-lookup"><span data-stu-id="dc1b1-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="dc1b1-108">Twórz i uruchamiaj wystąpienia LocalDB za pomocą SqlLocalDB. exe lub pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="dc1b1-109">Użyj narzędzia sqlcmd. exe do dodawania i modyfikowania baz danych w wystąpieniu LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="dc1b1-110">Na przykład `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="dc1b1-111">Użyj słowa `AttachDBFilename` kluczowego Connection, aby dodać bazę danych do wystąpienia usługi LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="dc1b1-112">Jeśli używasz `AttachDBFilename`, jeśli nie określisz nazwy bazy danych `Database` za pomocą słowa kluczowego Connection, baza danych zostanie usunięta z wystąpienia LocalDB, gdy aplikacja zostanie zamknięta.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="dc1b1-113">Określ wystąpienie LocalDB w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="dc1b1-114">Na przykład nazwa wystąpienia to `myInstance`, ciąg połączenia:</span><span class="sxs-lookup"><span data-stu-id="dc1b1-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="dc1b1-115">`User Instance=True`nie jest dozwolone podczas nawiązywania połączenia z bazą danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="dc1b1-116">Możesz pobrać LocalDB z [pakietu Feature Pack Microsoft SQL Server 2012](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="dc1b1-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="dc1b1-117">Jeśli użyjesz narzędzia sqlcmd. exe do modyfikacji danych w wystąpieniu usługi LocalDB, będziesz potrzebować narzędzia sqlcmd z SQL Server 2012, które można również uzyskać z pakietu SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="dc1b1-118">Programowe tworzenie nazwanego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="dc1b1-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="dc1b1-119">Aplikacja może utworzyć nazwane wystąpienie i określić bazę danych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dc1b1-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="dc1b1-120">Określ wystąpienia LocalDB do utworzenia w pliku App. config w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="dc1b1-121">Numer wersji wystąpienia powinien być taki sam jak numer wersji instalacji programu LocalDB.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="dc1b1-122">Określ nazwę wystąpienia za pomocą `server` słowa kluczowego parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="dc1b1-123">Nazwa wystąpienia określona w `server` słowie kluczowym parametrów połączenia musi być zgodna z nazwą określoną w pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="dc1b1-124">Użyj słowa `AttachDBFilename` kluczowego Connection, aby określić. Plik MDF.</span><span class="sxs-lookup"><span data-stu-id="dc1b1-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1b1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc1b1-125">See also</span></span>

- [<span data-ttu-id="dc1b1-126">Funkcje Serwera SQL i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc1b1-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="dc1b1-127">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dc1b1-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
