---
title: Omówienie
ms.date: 12/13/2019
description: Omówienie programu Microsoft. Data. sqlite
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447231"
---
# <a name="microsoftdatasqlite-overview"></a><span data-ttu-id="0fc98-103">Microsoft. Data. sqlite — Omówienie</span><span class="sxs-lookup"><span data-stu-id="0fc98-103">Microsoft.Data.Sqlite overview</span></span>

<span data-ttu-id="0fc98-104">Microsoft. Data. sqlite to lekki dostawca [ADO.NET](../../../framework/data/adonet/index.md) dla oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="0fc98-104">Microsoft.Data.Sqlite is a lightweight [ADO.NET](../../../framework/data/adonet/index.md) provider for SQLite.</span></span> <span data-ttu-id="0fc98-105">Dostawca [Entity Framework Core](/ef/core/) dla oprogramowania SQLite został utworzony na podstawie tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0fc98-105">The [Entity Framework Core](/ef/core/) provider for SQLite is built on top of this library.</span></span> <span data-ttu-id="0fc98-106">Można go również używać niezależnie lub z innymi bibliotekami dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="0fc98-106">However, it can also be used independently or with other data access libraries.</span></span>

## <a name="installation"></a><span data-ttu-id="0fc98-107">Instalacja programu</span><span class="sxs-lookup"><span data-stu-id="0fc98-107">Installation</span></span>

<span data-ttu-id="0fc98-108">Najnowsza stabilna wersja jest dostępna w programie [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span><span class="sxs-lookup"><span data-stu-id="0fc98-108">The latest stable version is available on [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite).</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="0fc98-109">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="0fc98-109">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="0fc98-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0fc98-110">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a><span data-ttu-id="0fc98-111">Pomiar</span><span class="sxs-lookup"><span data-stu-id="0fc98-111">Usage</span></span>

<span data-ttu-id="0fc98-112">Ta biblioteka implementuje typowe abstrakcje ADO.NET dla połączeń, poleceń, czytników danych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0fc98-112">This library implements the common ADO.NET abstractions for connections, commands, data readers, and so on.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a><span data-ttu-id="0fc98-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fc98-113">See also</span></span>

* [<span data-ttu-id="0fc98-114">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="0fc98-114">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="0fc98-115">Odwołanie do biblioteki API</span><span class="sxs-lookup"><span data-stu-id="0fc98-115">API Reference</span></span>](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [<span data-ttu-id="0fc98-116">Składnia języka SQL</span><span class="sxs-lookup"><span data-stu-id="0fc98-116">SQL Syntax</span></span>](https://www.sqlite.org/lang.html)
