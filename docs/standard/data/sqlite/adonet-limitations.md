---
title: Ograniczenia ADO.NET
ms.date: 12/13/2019
description: W tym artykule opisano niektóre z ADO.NETych ograniczeń, które można napotkać.
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901250"
---
# <a name="adonet-limitations"></a><span data-ttu-id="c7b20-103">Ograniczenia ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c7b20-103">ADO.NET limitations</span></span>

<span data-ttu-id="c7b20-104">Microsoft. Data. sqlite udostępnia implementacje wielu streszczeń ADO.NET, ale istnieją pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="c7b20-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="c7b20-105">Informacje o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="c7b20-105">Database schema information</span></span>

<span data-ttu-id="c7b20-106">Metadane dotyczące wyników zapytania są dostępne za pomocą <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7b20-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="c7b20-107">`DbConnection.GetSchema()`nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="c7b20-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="c7b20-108">Ten interfejs API nie jest dobrze zdefiniowany, dlatego zalecamy pobranie metadanych bazy danych bezpośrednio przy użyciu standardowych interfejsów API programu SQLite, takich jak tabela [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) i [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) pragma.</span><span class="sxs-lookup"><span data-stu-id="c7b20-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="c7b20-109">Aby uzyskać więcej informacji, zobacz [metadane](metadata.md).</span><span class="sxs-lookup"><span data-stu-id="c7b20-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="c7b20-110">System. Transactions</span><span class="sxs-lookup"><span data-stu-id="c7b20-110">System.Transactions</span></span>

<span data-ttu-id="c7b20-111">Firma Microsoft. Data. sqlite nie obsługuje jeszcze system. Transactions.</span><span class="sxs-lookup"><span data-stu-id="c7b20-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="c7b20-112">Zamiast tego użyj transakcji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="c7b20-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="c7b20-113">Aby uzyskać więcej informacji, zobacz [transakcje](transactions.md).</span><span class="sxs-lookup"><span data-stu-id="c7b20-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="c7b20-114">Prześlij opinię na temat braku obsługi dla elementu System. Transactions w przypadku problemu [#13825](https://github.com/dotnet/efcore/issues/13825).</span><span class="sxs-lookup"><span data-stu-id="c7b20-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/dotnet/efcore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="c7b20-115">Karty danych</span><span class="sxs-lookup"><span data-stu-id="c7b20-115">Data adapters</span></span>

<span data-ttu-id="c7b20-116">`DbDataAdapter`jeszcze nie zaimplementowano przez Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="c7b20-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="c7b20-117">Oznacza to, że można używać tylko `DataSet` ADO.NET `DataTable` i ładować dane, a ich nie aktualizować.</span><span class="sxs-lookup"><span data-stu-id="c7b20-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="c7b20-118">Użyj [#13838](https://github.com/dotnet/efcore/issues/13838) problemu, aby przekazać opinię na `DbDataAdapter`temat wdrażania.</span><span class="sxs-lookup"><span data-stu-id="c7b20-118">Use issue [#13838](https://github.com/dotnet/efcore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="c7b20-119">Parametry wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c7b20-119">Output parameters</span></span>

<span data-ttu-id="c7b20-120">Produkt SQLite nie obsługuje parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c7b20-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="c7b20-121">Parametry pozycyjne</span><span class="sxs-lookup"><span data-stu-id="c7b20-121">Positional parameters</span></span>

<span data-ttu-id="c7b20-122">Microsoft. Data. sqlite obsługuje tylko nazwane [Parametry](parameters.md).</span><span class="sxs-lookup"><span data-stu-id="c7b20-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="c7b20-123">Parametry pozycyjne nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c7b20-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="c7b20-124">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="c7b20-124">Stored procedures</span></span>

<span data-ttu-id="c7b20-125">SQLite nie obsługuje procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="c7b20-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="c7b20-126">Poziomy izolacji</span><span class="sxs-lookup"><span data-stu-id="c7b20-126">Isolation levels</span></span>

<span data-ttu-id="c7b20-127">Poziomy `Chaos` izolacji `Snapshot` i nie są obsługiwane w transakcjach oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="c7b20-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7b20-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7b20-128">See also</span></span>

* [<span data-ttu-id="c7b20-129">Ograniczenia asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="c7b20-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="c7b20-130">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c7b20-130">Data types</span></span>](types.md)
* [<span data-ttu-id="c7b20-131">Transakcje</span><span class="sxs-lookup"><span data-stu-id="c7b20-131">Transactions</span></span>](transactions.md)
