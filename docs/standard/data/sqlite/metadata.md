---
title: Metadane
ms.date: 12/13/2019
description: Dowiedz się, jak pobrać metadane dotyczące bazy danych.
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447196"
---
# <a name="metadata"></a><span data-ttu-id="f022d-103">Metadane</span><span class="sxs-lookup"><span data-stu-id="f022d-103">Metadata</span></span>

<span data-ttu-id="f022d-104">Istnieją dwa interfejsy API do pobierania metadanych w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f022d-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="f022d-105">Jeden pobiera metadane dotyczące wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="f022d-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="f022d-106">Pozostałe pobiera metadane dotyczące schematu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f022d-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="f022d-107">Metadane wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="f022d-107">Query result metadata</span></span>

<span data-ttu-id="f022d-108">Metadane dotyczące wyników zapytania można pobrać przy użyciu metody <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> w `SqliteDataReader`.</span><span class="sxs-lookup"><span data-stu-id="f022d-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="f022d-109">Zwrócony <xref:System.Data.DataTable> zawiera następujące kolumny:</span><span class="sxs-lookup"><span data-stu-id="f022d-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="f022d-110">Kolumna</span><span class="sxs-lookup"><span data-stu-id="f022d-110">Column</span></span>             | <span data-ttu-id="f022d-111">Typ</span><span class="sxs-lookup"><span data-stu-id="f022d-111">Type</span></span>    | <span data-ttu-id="f022d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f022d-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="f022d-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="f022d-113">Boolean</span></span> | <span data-ttu-id="f022d-114">Prawda, jeśli kolumna pierwotna może mieć wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="f022d-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="f022d-115">String</span><span class="sxs-lookup"><span data-stu-id="f022d-115">String</span></span>  | <span data-ttu-id="f022d-116">Nazwa bazy danych kolumny źródłowej.</span><span class="sxs-lookup"><span data-stu-id="f022d-116">The name of the origin column's database.</span></span> <span data-ttu-id="f022d-117">Zawsze wartość NULL dla wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="f022d-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="f022d-118">String</span><span class="sxs-lookup"><span data-stu-id="f022d-118">String</span></span>  | <span data-ttu-id="f022d-119">Niealiasowa nazwa kolumny źródła.</span><span class="sxs-lookup"><span data-stu-id="f022d-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="f022d-120">Zawsze wartość NULL dla wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="f022d-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="f022d-121">String</span><span class="sxs-lookup"><span data-stu-id="f022d-121">String</span></span>  | <span data-ttu-id="f022d-122">Zawsze wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="f022d-122">Always NULL.</span></span> <span data-ttu-id="f022d-123">SQLite nie obsługuje schematów.</span><span class="sxs-lookup"><span data-stu-id="f022d-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="f022d-124">String</span><span class="sxs-lookup"><span data-stu-id="f022d-124">String</span></span>  | <span data-ttu-id="f022d-125">Ścieżka do pliku bazy danych określona w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="f022d-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="f022d-126">String</span><span class="sxs-lookup"><span data-stu-id="f022d-126">String</span></span>  | <span data-ttu-id="f022d-127">Nazwa tabeli kolumny pierwotnej.</span><span class="sxs-lookup"><span data-stu-id="f022d-127">The name of the origin column's table.</span></span> <span data-ttu-id="f022d-128">Zawsze wartość NULL dla wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="f022d-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="f022d-129">String</span><span class="sxs-lookup"><span data-stu-id="f022d-129">String</span></span>  | <span data-ttu-id="f022d-130">Nazwa lub alias kolumny w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="f022d-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="f022d-131">Int32</span><span class="sxs-lookup"><span data-stu-id="f022d-131">Int32</span></span>   | <span data-ttu-id="f022d-132">Numer porządkowy kolumny w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="f022d-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="f022d-133">Int32</span><span class="sxs-lookup"><span data-stu-id="f022d-133">Int32</span></span>   | <span data-ttu-id="f022d-134">Zawsze-1.</span><span class="sxs-lookup"><span data-stu-id="f022d-134">Always -1.</span></span> <span data-ttu-id="f022d-135">Może to ulec zmianie w przyszłych wersjach `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="f022d-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="f022d-136">Typ</span><span class="sxs-lookup"><span data-stu-id="f022d-136">Type</span></span>    | <span data-ttu-id="f022d-137">Domyślny typ danych platformy .NET dla kolumny.</span><span class="sxs-lookup"><span data-stu-id="f022d-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="f022d-138">String</span><span class="sxs-lookup"><span data-stu-id="f022d-138">String</span></span>  | <span data-ttu-id="f022d-139">Typ danych programu SQLite w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="f022d-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="f022d-140">Boolean</span><span class="sxs-lookup"><span data-stu-id="f022d-140">Boolean</span></span> | <span data-ttu-id="f022d-141">True, jeśli nazwa kolumny jest aliasem w zestawie wyników.</span><span class="sxs-lookup"><span data-stu-id="f022d-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="f022d-142">Boolean</span><span class="sxs-lookup"><span data-stu-id="f022d-142">Boolean</span></span> | <span data-ttu-id="f022d-143">Ma wartość true, jeśli kolumna pierwotna została utworzona za pomocą słowa kluczowego AUTOINCREMENT.</span><span class="sxs-lookup"><span data-stu-id="f022d-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="f022d-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="f022d-144">Boolean</span></span> | <span data-ttu-id="f022d-145">Wartość true, jeśli kolumna pochodzi z wyrażenia w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="f022d-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="f022d-146">Boolean</span><span class="sxs-lookup"><span data-stu-id="f022d-146">Boolean</span></span> | <span data-ttu-id="f022d-147">Wartość true, jeśli kolumna pierwotna jest częścią klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="f022d-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="f022d-148">Boolean</span><span class="sxs-lookup"><span data-stu-id="f022d-148">Boolean</span></span> | <span data-ttu-id="f022d-149">Ma wartość true, jeśli kolumna pierwotna jest UNIKATOWa.</span><span class="sxs-lookup"><span data-stu-id="f022d-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="f022d-150">Int16</span><span class="sxs-lookup"><span data-stu-id="f022d-150">Int16</span></span>   | <span data-ttu-id="f022d-151">Zawsze wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="f022d-151">Always NULL.</span></span> <span data-ttu-id="f022d-152">Może to ulec zmianie w przyszłych wersjach `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="f022d-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="f022d-153">Int16</span><span class="sxs-lookup"><span data-stu-id="f022d-153">Int16</span></span>   | <span data-ttu-id="f022d-154">Zawsze wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="f022d-154">Always NULL.</span></span> <span data-ttu-id="f022d-155">Może to ulec zmianie w przyszłych wersjach `Microsoft.Data.Sqlite`.</span><span class="sxs-lookup"><span data-stu-id="f022d-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="f022d-156">Poniższy przykład pokazuje, jak za pomocą `GetSchemaTable` utworzyć ciąg debugowania, który pokazuje metadane dotyczące wyniku:</span><span class="sxs-lookup"><span data-stu-id="f022d-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="f022d-157">Na przykład to zapytanie wygenerowało następujący ciąg debugowania:</span><span class="sxs-lookup"><span data-stu-id="f022d-157">For example, this query would produce the following debug string:</span></span>

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a><span data-ttu-id="f022d-158">Metadane schematu</span><span class="sxs-lookup"><span data-stu-id="f022d-158">Schema metadata</span></span>

<span data-ttu-id="f022d-159">Microsoft. Data. sqlite nie implementuje metody GetSchema na DbConnection.</span><span class="sxs-lookup"><span data-stu-id="f022d-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="f022d-160">Zamiast tego można wykonywać zapytania bezpośrednio dotyczące informacji o schemacie, korzystając z tabeli [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) i instrukcji pragma, takich jak [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) i [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span><span class="sxs-lookup"><span data-stu-id="f022d-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="f022d-161">Na przykład to zapytanie spowoduje pobranie metadanych dotyczących wszystkich kolumn w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f022d-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="f022d-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f022d-162">See also</span></span>

* [<span data-ttu-id="f022d-163">Magazyn SQL Database schematu</span><span class="sxs-lookup"><span data-stu-id="f022d-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="f022d-164">PRAGMa — instrukcje</span><span class="sxs-lookup"><span data-stu-id="f022d-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="f022d-165">Typy danych</span><span class="sxs-lookup"><span data-stu-id="f022d-165">Data types</span></span>](types.md)
