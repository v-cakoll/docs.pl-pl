---
title: Parametry połączeń
ms.date: 12/13/2019
description: Obsługiwane słowa kluczowe i wartości ciągów połączeń.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400450"
---
# <a name="connection-strings"></a><span data-ttu-id="8c276-103">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="8c276-103">Connection strings</span></span>

<span data-ttu-id="8c276-104">Ciąg połączenia służy do określania sposobu łączenia się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="8c276-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="8c276-105">Parametry połączenia w programie Microsoft.Data.Sqlite są zgodne ze standardową [składnią ADO.NET](../../../framework/data/adonet/connection-strings.md) jako oddzieloną średnikami listą słów kluczowych i wartości.</span><span class="sxs-lookup"><span data-stu-id="8c276-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="8c276-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8c276-106">Keywords</span></span>

<span data-ttu-id="8c276-107">Z plikami microsoft.Data.sqlite można używać następujących słów kluczowych ciągu połączenia:</span><span class="sxs-lookup"><span data-stu-id="8c276-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="8c276-108">Źródło danych</span><span class="sxs-lookup"><span data-stu-id="8c276-108">Data source</span></span>

<span data-ttu-id="8c276-109">Ścieżka do pliku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8c276-109">The path to the database file.</span></span> <span data-ttu-id="8c276-110">*DataSource* (bez spacji) i *Nazwa pliku* są aliasami tego słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="8c276-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="8c276-111">SQLite traktuje ścieżki względem bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="8c276-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="8c276-112">Można również określić ścieżki bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="8c276-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="8c276-113">Jeśli **jest pusta**, SQLite tworzy tymczasową bazę danych na dysku, która jest usuwana po zamknięciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c276-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="8c276-114">Jeśli `:memory:`używana jest baza danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c276-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="8c276-115">Aby uzyskać więcej informacji, zobacz [Bazy danych w pamięci](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8c276-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="8c276-116">Ścieżki rozpoczynające `|DataDirectory|` się od ciągu podstawienia są traktowane tak samo jak ścieżki względne.</span><span class="sxs-lookup"><span data-stu-id="8c276-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="8c276-117">Jeśli jest ustawiona, ścieżki są dokonywane względem wartości właściwości domeny aplikacji DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="8c276-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="8c276-118">To słowo kluczowe obsługuje również [nazwy plików URI](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="8c276-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="8c276-119">Tryb</span><span class="sxs-lookup"><span data-stu-id="8c276-119">Mode</span></span>

<span data-ttu-id="8c276-120">Tryb połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c276-120">The connection mode.</span></span>

| <span data-ttu-id="8c276-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c276-121">Value</span></span>           | <span data-ttu-id="8c276-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8c276-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="8c276-123">ReadWriteCreate (Tworzenie zapisu wuzw</span><span class="sxs-lookup"><span data-stu-id="8c276-123">ReadWriteCreate</span></span> | <span data-ttu-id="8c276-124">Otwiera bazę danych do odczytu i zapisu i tworzy ją, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="8c276-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="8c276-125">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="8c276-125">This is the default.</span></span> |
| <span data-ttu-id="8c276-126">Odczyt/zapis</span><span class="sxs-lookup"><span data-stu-id="8c276-126">ReadWrite</span></span>       | <span data-ttu-id="8c276-127">Otwiera bazę danych do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="8c276-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="8c276-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="8c276-128">ReadOnly</span></span>        | <span data-ttu-id="8c276-129">Otwiera bazę danych w trybie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="8c276-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="8c276-130">Memory (Pamięć)</span><span class="sxs-lookup"><span data-stu-id="8c276-130">Memory</span></span>          | <span data-ttu-id="8c276-131">Otwiera bazę danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c276-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="8c276-132">Pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="8c276-132">Cache</span></span>

<span data-ttu-id="8c276-133">Tryb buforowania używany przez połączenie.</span><span class="sxs-lookup"><span data-stu-id="8c276-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="8c276-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c276-134">Value</span></span>   | <span data-ttu-id="8c276-135">Opis</span><span class="sxs-lookup"><span data-stu-id="8c276-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="8c276-136">Domyślne</span><span class="sxs-lookup"><span data-stu-id="8c276-136">Default</span></span> | <span data-ttu-id="8c276-137">Używa trybu domyślnego podstawowej biblioteki SQLite.</span><span class="sxs-lookup"><span data-stu-id="8c276-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="8c276-138">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="8c276-138">This is the default.</span></span>                   |
| <span data-ttu-id="8c276-139">Private</span><span class="sxs-lookup"><span data-stu-id="8c276-139">Private</span></span> | <span data-ttu-id="8c276-140">Każde połączenie używa prywatnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8c276-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="8c276-141">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="8c276-141">Shared</span></span>  | <span data-ttu-id="8c276-142">Połączenia współużytkują pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="8c276-142">Connections share a cache.</span></span> <span data-ttu-id="8c276-143">Ten tryb można zmienić zachowanie transakcji i blokowania tabeli.</span><span class="sxs-lookup"><span data-stu-id="8c276-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="8c276-144">Hasło</span><span class="sxs-lookup"><span data-stu-id="8c276-144">Password</span></span>

<span data-ttu-id="8c276-145">Klucz szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="8c276-145">The encryption key.</span></span> <span data-ttu-id="8c276-146">Po określeniu `PRAGMA key` jest wysyłany natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c276-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="8c276-147">Hasło nie ma wpływu, gdy szyfrowanie nie jest obsługiwane przez natywną bibliotekę SQLite.</span><span class="sxs-lookup"><span data-stu-id="8c276-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="8c276-148">Klucze obce</span><span class="sxs-lookup"><span data-stu-id="8c276-148">Foreign Keys</span></span>

<span data-ttu-id="8c276-149">Wartość wskazująca, czy włączyć ograniczenia klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="8c276-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="8c276-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c276-150">Value</span></span>   | <span data-ttu-id="8c276-151">Opis</span><span class="sxs-lookup"><span data-stu-id="8c276-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="8c276-152">True</span><span class="sxs-lookup"><span data-stu-id="8c276-152">True</span></span>    | <span data-ttu-id="8c276-153">Wysyła `PRAGMA foreign_keys = 1` natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c276-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="8c276-154">False</span><span class="sxs-lookup"><span data-stu-id="8c276-154">False</span></span>   | <span data-ttu-id="8c276-155">Wysyła `PRAGMA foreign_keys = 0` natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c276-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="8c276-156">(pusty)</span><span class="sxs-lookup"><span data-stu-id="8c276-156">(empty)</span></span> | <span data-ttu-id="8c276-157">Nie wysyła `PRAGMA foreign_keys`.</span><span class="sxs-lookup"><span data-stu-id="8c276-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="8c276-158">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="8c276-158">This is the default.</span></span> |

<span data-ttu-id="8c276-159">Nie ma potrzeby włączania kluczy obcych, jeśli, jak w e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS został użyty do skompilowania natywnej biblioteki SQLite.</span><span class="sxs-lookup"><span data-stu-id="8c276-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="8c276-160">Wyzwalacze cykliczne</span><span class="sxs-lookup"><span data-stu-id="8c276-160">Recursive triggers</span></span>

<span data-ttu-id="8c276-161">Wartość, która wskazuje, czy włączyć wyzwalacze cykliczne.</span><span class="sxs-lookup"><span data-stu-id="8c276-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="8c276-162">Wartość</span><span class="sxs-lookup"><span data-stu-id="8c276-162">Value</span></span> | <span data-ttu-id="8c276-163">Opis</span><span class="sxs-lookup"><span data-stu-id="8c276-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="8c276-164">True</span><span class="sxs-lookup"><span data-stu-id="8c276-164">True</span></span>  | <span data-ttu-id="8c276-165">Wysyła `PRAGMA recursive_triggers` natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c276-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="8c276-166">False</span><span class="sxs-lookup"><span data-stu-id="8c276-166">False</span></span> | <span data-ttu-id="8c276-167">Nie wysyła `PRAGMA recursive_triggers`.</span><span class="sxs-lookup"><span data-stu-id="8c276-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="8c276-168">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="8c276-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="8c276-169">Konstruktor ciągów połączeń</span><span class="sxs-lookup"><span data-stu-id="8c276-169">Connection string builder</span></span>

<span data-ttu-id="8c276-170">Można użyć <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako silnie typizony sposób tworzenia ciągów połączeń.</span><span class="sxs-lookup"><span data-stu-id="8c276-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="8c276-171">Może być również używany do zapobiegania atakom iniekcji ciągu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c276-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="8c276-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8c276-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="8c276-173">Podstawowa (Basic)</span><span class="sxs-lookup"><span data-stu-id="8c276-173">Basic</span></span>

<span data-ttu-id="8c276-174">Podstawowy ciąg połączenia z udostępnionej pamięci podręcznej dla poprawy współbieżności.</span><span class="sxs-lookup"><span data-stu-id="8c276-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="8c276-175">Zaszyfrowane</span><span class="sxs-lookup"><span data-stu-id="8c276-175">Encrypted</span></span>

<span data-ttu-id="8c276-176">Zaszyfrowana baza danych.</span><span class="sxs-lookup"><span data-stu-id="8c276-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="8c276-177">Tylko odczyt</span><span class="sxs-lookup"><span data-stu-id="8c276-177">Read-only</span></span>

<span data-ttu-id="8c276-178">Baza danych tylko do odczytu, która nie może być modyfikowana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8c276-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="8c276-179">W pamięci</span><span class="sxs-lookup"><span data-stu-id="8c276-179">In-memory</span></span>

<span data-ttu-id="8c276-180">Prywatna baza danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8c276-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="8c276-181">Sharable in-memory</span><span class="sxs-lookup"><span data-stu-id="8c276-181">Sharable in-memory</span></span>

<span data-ttu-id="8c276-182">Sharable, w pamięci bazy danych identyfikowane przez nazwę *Sharable*.</span><span class="sxs-lookup"><span data-stu-id="8c276-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="8c276-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c276-183">See also</span></span>

* [<span data-ttu-id="8c276-184">Parametry połączenia w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c276-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="8c276-185">Bazy danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="8c276-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="8c276-186">Transakcje</span><span class="sxs-lookup"><span data-stu-id="8c276-186">Transactions</span></span>](transactions.md)
