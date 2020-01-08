---
title: Ograniczenia ADO.NET
ms.date: 12/13/2019
description: W tym artykule opisano niektóre z ADO.NETych ograniczeń, które można napotkać.
ms.openlocfilehash: b58fd3a9ea324e9c17ad21479e53e45f5982db9d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447091"
---
# <a name="adonet-limitations"></a><span data-ttu-id="7dc12-103">Ograniczenia ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7dc12-103">ADO.NET limitations</span></span>

<span data-ttu-id="7dc12-104">Microsoft. Data. sqlite udostępnia implementacje wielu streszczeń ADO.NET, ale istnieją pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="7dc12-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="7dc12-105">Informacje o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="7dc12-105">Database schema information</span></span>

<span data-ttu-id="7dc12-106">Metadane dotyczące wyników zapytania są dostępne za pomocą metody <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="7dc12-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="7dc12-107">`DbConnection.GetSchema()` nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="7dc12-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="7dc12-108">Ten interfejs API nie jest dobrze zdefiniowany, dlatego zalecamy pobranie metadanych bazy danych bezpośrednio przy użyciu standardowych interfejsów API programu SQLite, takich jak tabela [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) i [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) pragma.</span><span class="sxs-lookup"><span data-stu-id="7dc12-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="7dc12-109">Aby uzyskać więcej informacji, zobacz [metadane](metadata.md).</span><span class="sxs-lookup"><span data-stu-id="7dc12-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="7dc12-110">System. Transactions</span><span class="sxs-lookup"><span data-stu-id="7dc12-110">System.Transactions</span></span>

<span data-ttu-id="7dc12-111">Firma Microsoft. Data. sqlite nie obsługuje jeszcze system. Transactions.</span><span class="sxs-lookup"><span data-stu-id="7dc12-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="7dc12-112">Zamiast tego użyj transakcji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7dc12-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="7dc12-113">Aby uzyskać więcej informacji, zobacz [transakcje](transactions.md).</span><span class="sxs-lookup"><span data-stu-id="7dc12-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="7dc12-114">Prześlij opinię na temat braku obsługi dla elementu System. Transactions w przypadku problemu [#13825](https://github.com/aspnet/EntityFrameworkCore/issues/13825).</span><span class="sxs-lookup"><span data-stu-id="7dc12-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/aspnet/EntityFrameworkCore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="7dc12-115">Karty danych</span><span class="sxs-lookup"><span data-stu-id="7dc12-115">Data adapters</span></span>

<span data-ttu-id="7dc12-116">`DbDataAdapter` nie została jeszcze zaimplementowana przez firmę Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="7dc12-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="7dc12-117">Oznacza to, że można używać ADO.NET `DataSet` i `DataTable` do ładowania danych i ich aktualizowania.</span><span class="sxs-lookup"><span data-stu-id="7dc12-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="7dc12-118">Użyj [#13838](https://github.com/aspnet/EntityFrameworkCore/issues/13838) problemu, aby przekazać opinię na temat implementowania `DbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="7dc12-118">Use issue [#13838](https://github.com/aspnet/EntityFrameworkCore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="7dc12-119">Parametry wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7dc12-119">Output parameters</span></span>

<span data-ttu-id="7dc12-120">Produkt SQLite nie obsługuje parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="7dc12-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="7dc12-121">Parametry pozycyjne</span><span class="sxs-lookup"><span data-stu-id="7dc12-121">Positional parameters</span></span>

<span data-ttu-id="7dc12-122">Microsoft. Data. sqlite obsługuje tylko nazwane [Parametry](parameters.md).</span><span class="sxs-lookup"><span data-stu-id="7dc12-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="7dc12-123">Parametry pozycyjne nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7dc12-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="7dc12-124">Procedury składowane</span><span class="sxs-lookup"><span data-stu-id="7dc12-124">Stored procedures</span></span>

<span data-ttu-id="7dc12-125">SQLite nie obsługuje procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="7dc12-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="7dc12-126">Poziomy izolacji</span><span class="sxs-lookup"><span data-stu-id="7dc12-126">Isolation levels</span></span>

<span data-ttu-id="7dc12-127">Poziomy izolacji `Chaos` i `Snapshot` nie są obsługiwane w transakcjach oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="7dc12-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="7dc12-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dc12-128">See also</span></span>

* [<span data-ttu-id="7dc12-129">Ograniczenia asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="7dc12-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="7dc12-130">Typy danych</span><span class="sxs-lookup"><span data-stu-id="7dc12-130">Data types</span></span>](types.md)
* [<span data-ttu-id="7dc12-131">Transakcje</span><span class="sxs-lookup"><span data-stu-id="7dc12-131">Transactions</span></span>](transactions.md)
