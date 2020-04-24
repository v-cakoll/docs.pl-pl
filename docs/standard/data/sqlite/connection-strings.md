---
title: Parametry połączeń
ms.date: 12/13/2019
description: Obsługiwane słowa kluczowe i wartości parametrów połączenia.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400450"
---
# <a name="connection-strings"></a><span data-ttu-id="6a2f1-103">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="6a2f1-103">Connection strings</span></span>

<span data-ttu-id="6a2f1-104">Parametry połączenia służą do określania sposobu łączenia się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="6a2f1-105">Parametry połączenia w firmie Microsoft. Data. sqlite są zgodne ze standardową [składnią ADO.NET](../../../framework/data/adonet/connection-strings.md) jako listę słów kluczowych i wartości rozdzielonych średnikami.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="6a2f1-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6a2f1-106">Keywords</span></span>

<span data-ttu-id="6a2f1-107">Następujące słowa kluczowe parametrów połączenia mogą być używane z firmą Microsoft. Data. sqlite:</span><span class="sxs-lookup"><span data-stu-id="6a2f1-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="6a2f1-108">Źródło danych</span><span class="sxs-lookup"><span data-stu-id="6a2f1-108">Data source</span></span>

<span data-ttu-id="6a2f1-109">Ścieżka do pliku bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-109">The path to the database file.</span></span> <span data-ttu-id="6a2f1-110">*Źródła danych* (bez spacji) i *filename* są aliasami tego słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="6a2f1-111">SQLite traktuje ścieżki względem bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="6a2f1-112">Można również określić ścieżki bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="6a2f1-113">Jeśli ta wartość jest **pusta**, program SQLite tworzy tymczasową bazę danych na dysku, która jest usuwana po zamknięciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="6a2f1-114">Jeśli `:memory:`używana jest baza danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="6a2f1-115">Aby uzyskać więcej informacji, zobacz [bazy danych w pamięci](in-memory-databases.md).</span><span class="sxs-lookup"><span data-stu-id="6a2f1-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="6a2f1-116">Ścieżki, które zaczynają `|DataDirectory|` się od ciągu podstawiania są traktowane tak samo jak ścieżki względne.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="6a2f1-117">W przypadku ustawienia ścieżki są tworzone względem wartości właściwości domena aplikacji usługi DataDirectory.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="6a2f1-118">To słowo kluczowe obsługuje również [nazwy plików URI](https://www.sqlite.org/uri.html).</span><span class="sxs-lookup"><span data-stu-id="6a2f1-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="6a2f1-119">Tryb</span><span class="sxs-lookup"><span data-stu-id="6a2f1-119">Mode</span></span>

<span data-ttu-id="6a2f1-120">Tryb połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-120">The connection mode.</span></span>

| <span data-ttu-id="6a2f1-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="6a2f1-121">Value</span></span>           | <span data-ttu-id="6a2f1-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6a2f1-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="6a2f1-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="6a2f1-123">ReadWriteCreate</span></span> | <span data-ttu-id="6a2f1-124">Otwiera bazę danych do odczytu i zapisu, a następnie tworzy ją, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="6a2f1-125">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-125">This is the default.</span></span> |
| <span data-ttu-id="6a2f1-126">Odczyt/zapis</span><span class="sxs-lookup"><span data-stu-id="6a2f1-126">ReadWrite</span></span>       | <span data-ttu-id="6a2f1-127">Otwiera bazę danych do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="6a2f1-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6a2f1-128">ReadOnly</span></span>        | <span data-ttu-id="6a2f1-129">Otwiera bazę danych w trybie tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="6a2f1-130">Memory (Pamięć)</span><span class="sxs-lookup"><span data-stu-id="6a2f1-130">Memory</span></span>          | <span data-ttu-id="6a2f1-131">Otwiera bazę danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="6a2f1-132">Pamięć podręczna</span><span class="sxs-lookup"><span data-stu-id="6a2f1-132">Cache</span></span>

<span data-ttu-id="6a2f1-133">Tryb buforowania używany przez połączenie.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="6a2f1-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="6a2f1-134">Value</span></span>   | <span data-ttu-id="6a2f1-135">Opis</span><span class="sxs-lookup"><span data-stu-id="6a2f1-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="6a2f1-136">Domyślne</span><span class="sxs-lookup"><span data-stu-id="6a2f1-136">Default</span></span> | <span data-ttu-id="6a2f1-137">Używa domyślnego trybu podstawowej biblioteki programu SQLite.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="6a2f1-138">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-138">This is the default.</span></span>                   |
| <span data-ttu-id="6a2f1-139">Private</span><span class="sxs-lookup"><span data-stu-id="6a2f1-139">Private</span></span> | <span data-ttu-id="6a2f1-140">Każde połączenie używa prywatnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="6a2f1-141">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="6a2f1-141">Shared</span></span>  | <span data-ttu-id="6a2f1-142">Połączenia korzystają z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-142">Connections share a cache.</span></span> <span data-ttu-id="6a2f1-143">Ten tryb pozwala zmienić zachowanie blokowania transakcji i tabel.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="6a2f1-144">Hasło</span><span class="sxs-lookup"><span data-stu-id="6a2f1-144">Password</span></span>

<span data-ttu-id="6a2f1-145">Klucz szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-145">The encryption key.</span></span> <span data-ttu-id="6a2f1-146">Gdy ta wartość `PRAGMA key` jest określona, jest wysyłana natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="6a2f1-147">Hasło nie ma znaczenia, jeśli szyfrowanie nie jest obsługiwane przez natywną bibliotekę oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="6a2f1-148">Klucze obce</span><span class="sxs-lookup"><span data-stu-id="6a2f1-148">Foreign Keys</span></span>

<span data-ttu-id="6a2f1-149">Wartość wskazująca, czy należy włączyć ograniczenia klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="6a2f1-150">Wartość</span><span class="sxs-lookup"><span data-stu-id="6a2f1-150">Value</span></span>   | <span data-ttu-id="6a2f1-151">Opis</span><span class="sxs-lookup"><span data-stu-id="6a2f1-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="6a2f1-152">True</span><span class="sxs-lookup"><span data-stu-id="6a2f1-152">True</span></span>    | <span data-ttu-id="6a2f1-153">Wysyła `PRAGMA foreign_keys = 1` natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="6a2f1-154">False</span><span class="sxs-lookup"><span data-stu-id="6a2f1-154">False</span></span>   | <span data-ttu-id="6a2f1-155">Wysyła `PRAGMA foreign_keys = 0` natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="6a2f1-156">ciągiem</span><span class="sxs-lookup"><span data-stu-id="6a2f1-156">(empty)</span></span> | <span data-ttu-id="6a2f1-157">Nie wysyła `PRAGMA foreign_keys`.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="6a2f1-158">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-158">This is the default.</span></span> |

<span data-ttu-id="6a2f1-159">Nie ma potrzeby włączania kluczy obcych, jeśli tak, jak w e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS został użyty do skompilowania natywnej biblioteki programu SQLite.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="6a2f1-160">Wyzwalacze cykliczne</span><span class="sxs-lookup"><span data-stu-id="6a2f1-160">Recursive triggers</span></span>

<span data-ttu-id="6a2f1-161">Wartość wskazująca, czy włączyć Wyzwalacze cykliczne.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="6a2f1-162">Wartość</span><span class="sxs-lookup"><span data-stu-id="6a2f1-162">Value</span></span> | <span data-ttu-id="6a2f1-163">Opis</span><span class="sxs-lookup"><span data-stu-id="6a2f1-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="6a2f1-164">True</span><span class="sxs-lookup"><span data-stu-id="6a2f1-164">True</span></span>  | <span data-ttu-id="6a2f1-165">Wysyła `PRAGMA recursive_triggers` natychmiast po otwarciu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="6a2f1-166">False</span><span class="sxs-lookup"><span data-stu-id="6a2f1-166">False</span></span> | <span data-ttu-id="6a2f1-167">Nie wysyła `PRAGMA recursive_triggers`.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="6a2f1-168">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="6a2f1-169">Konstruktor parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="6a2f1-169">Connection string builder</span></span>

<span data-ttu-id="6a2f1-170">Można użyć <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako jednoznacznie określonego sposobu tworzenia parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="6a2f1-171">Można go również użyć, aby zapobiec atakom polegającym na iniekcji parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="6a2f1-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6a2f1-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="6a2f1-173">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="6a2f1-173">Basic</span></span>

<span data-ttu-id="6a2f1-174">Podstawowe parametry połączenia z udostępnioną pamięcią podręczną w celu zwiększenia współbieżności.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="6a2f1-175">Zaszyfrowane</span><span class="sxs-lookup"><span data-stu-id="6a2f1-175">Encrypted</span></span>

<span data-ttu-id="6a2f1-176">Zaszyfrowana baza danych.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-176">An encrypted database.</span></span>

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="6a2f1-177">Tylko odczyt</span><span class="sxs-lookup"><span data-stu-id="6a2f1-177">Read-only</span></span>

<span data-ttu-id="6a2f1-178">Baza danych tylko do odczytu, która nie może być modyfikowana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-178">A read-only database that cannot be modified by the app.</span></span>

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="6a2f1-179">W pamięci</span><span class="sxs-lookup"><span data-stu-id="6a2f1-179">In-memory</span></span>

<span data-ttu-id="6a2f1-180">Prywatna baza danych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-180">A private, in-memory database.</span></span>

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="6a2f1-181">Współużytkowana pamięć</span><span class="sxs-lookup"><span data-stu-id="6a2f1-181">Sharable in-memory</span></span>

<span data-ttu-id="6a2f1-182">Współużytkowana baza danych w pamięci identyfikowana przy użyciu nazwy, którą można *udostępniać*.</span><span class="sxs-lookup"><span data-stu-id="6a2f1-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="6a2f1-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a2f1-183">See also</span></span>

* [<span data-ttu-id="6a2f1-184">Parametry połączenia w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6a2f1-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="6a2f1-185">Bazy danych w pamięci</span><span class="sxs-lookup"><span data-stu-id="6a2f1-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="6a2f1-186">Transakcje</span><span class="sxs-lookup"><span data-stu-id="6a2f1-186">Transactions</span></span>](transactions.md)
