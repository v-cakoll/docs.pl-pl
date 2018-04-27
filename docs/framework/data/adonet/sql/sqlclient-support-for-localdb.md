---
title: Obsługa SqlClient LocalDB
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e2564e49a90a1c8fd9fe2cc000ebf648cf90b4e7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="b7b3a-102">Obsługa SqlClient LocalDB</span><span class="sxs-lookup"><span data-stu-id="b7b3a-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="b7b3a-103">Począwszy od programu SQL Server o nazwie kodowej Denali to Uproszczona wersja programu SQL Server o nazwie LocalDB, będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="b7b3a-104">W tym temacie omówiono sposób nawiązywania połączenia z bazą danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7b3a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7b3a-105">Remarks</span></span>  
 <span data-ttu-id="b7b3a-106">Aby uzyskać więcej informacji na temat LocalDB, łącznie ze sposobem LocalDB zainstalować i skonfigurować wystąpienie bazy danych LocalDB zobacz dokumentację SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="b7b3a-107">Podsumowując, co można zrobić LocalDB:</span><span class="sxs-lookup"><span data-stu-id="b7b3a-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="b7b3a-108">Utwórz i uruchom wystąpień LocalDB sqllocaldb.exe lub pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="b7b3a-109">Użyj programu sqlcmd.exe, aby dodawać i modyfikować baz danych w wystąpieniu bazy danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="b7b3a-110">Na przykład `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="b7b3a-111">Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby dodać bazy danych do wystąpienia bazy danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="b7b3a-112">Korzystając z `AttachDBFilename`, jeśli nie określisz nazwy bazy danych z `Database` słowo kluczowe parametrów połączenia bazy danych zostaną usunięte z wystąpieniem LocalDB po zamknięciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="b7b3a-113">Określ wystąpienie bazy danych LocalDB w ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="b7b3a-114">Na przykład Twoja nazwa wystąpienia jest `myInstance`, to ciąg połączenia:</span><span class="sxs-lookup"><span data-stu-id="b7b3a-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="b7b3a-115">`User Instance=True` nie jest dozwolona podczas nawiązywania połączenia z bazą danych LocalDB.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="b7b3a-116">Możesz pobrać LocalDB z [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="b7b3a-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="b7b3a-117">Jeśli użyjesz sqlcmd.exe, aby modyfikować danych w wystąpieniu bazy danych LocalDB, konieczne będzie sqlcmd z programu SQL Server 2012, który możesz również pobrać ze strony programu SQL Server 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="b7b3a-118">Programowe tworzenie wystąpienia nazwanego</span><span class="sxs-lookup"><span data-stu-id="b7b3a-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="b7b3a-119">Aplikację można utworzyć wystąpienia nazwanego i Określ bazę danych, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b7b3a-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="b7b3a-120">Określ wystąpienia bazy danych LocalDB, utworzenie w pliku app.config, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="b7b3a-121">Numer wersji wystąpienia powinien być taki sam jak numer wersji instalacji bazy danych LocalDB programu.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
-   <span data-ttu-id="b7b3a-122">Określ nazwę wystąpienia, przy użyciu `server` słowo kluczowe parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="b7b3a-123">Podana nazwa wystąpienia w `server` słowo kluczowe parametrów połączenia musi pasować do nazwy określonej w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="b7b3a-124">Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby określić. Pliku MDF.</span><span class="sxs-lookup"><span data-stu-id="b7b3a-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b3a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7b3a-125">See Also</span></span>  
 [<span data-ttu-id="b7b3a-126">Funkcje Serwera SQL i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7b3a-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [<span data-ttu-id="b7b3a-127">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b7b3a-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
