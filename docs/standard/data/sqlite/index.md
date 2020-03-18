---
title: Omówienie
ms.date: 12/13/2019
description: Omówienie pliku Microsoft.Data.Sqlite
ms.openlocfilehash: e84c68f0615f187e8dea7ab87ac917c0ad796a1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543602"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="370a6-103">Omówienie programu Microsoft.Data.Sqlite</span><span class="sxs-lookup"><span data-stu-id="370a6-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="370a6-104">Microsoft.Data.Sqlite jest lekkim [dostawcą ADO.NET](../../../framework/data/adonet/index.md) dla SQLite.</span><span class="sxs-lookup"><span data-stu-id="370a6-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="370a6-105">Dostawca [entity framework core](/ef/core/) dla SQLite jest zbudowany na tej bibliotece.</span><span class="sxs-lookup"><span data-stu-id="370a6-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="370a6-106">Jednak może być również używany niezależnie lub z innymi bibliotekami dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="370a6-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="370a6-107">Instalacja</span><span class="sxs-lookup"><span data-stu-id="370a6-107">Installation</span></span>

<span data-ttu-id="370a6-108">Najnowsza stabilna wersja jest dostępna na [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="370a6-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="370a6-109">Interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="370a6-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studio"></a>[<span data-ttu-id="370a6-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="370a6-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="370a6-111">Sposób użycia</span><span class="sxs-lookup"><span data-stu-id="370a6-111">Usage</span></span>

<span data-ttu-id="370a6-112">Ta biblioteka implementuje wspólne abstrakcje ADO.NET dla połączeń, poleceń, czytników danych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="370a6-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="370a6-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="370a6-113">See also</span></span>

* [<span data-ttu-id="370a6-114">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="370a6-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="370a6-115">Dokumentacja interfejsu API</span><span class="sxs-lookup"><span data-stu-id="370a6-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0)
* [<span data-ttu-id="370a6-116">Składnia SQL</span><span class="sxs-lookup"><span data-stu-id="370a6-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
