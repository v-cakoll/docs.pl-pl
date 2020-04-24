---
title: Błędy bazy danych
ms.date: 12/13/2019
description: Opisuje sposób obsługi błędów bazy danych i ich wykonywania przez bibliotekę.
ms.openlocfilehash: 9a613b6f94a89dc40e627c14f46836be77080035
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447273"
---
# <a name="database-errors"></a><span data-ttu-id="48487-103">Błędy bazy danych</span><span class="sxs-lookup"><span data-stu-id="48487-103">Database errors</span></span>

<span data-ttu-id="48487-104"><xref:Microsoft.Data.Sqlite.SqliteException>jest generowany w przypadku napotkania błędu oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="48487-104"><xref:Microsoft.Data.Sqlite.SqliteException> is thrown when a SQLite error is encountered.</span></span> <span data-ttu-id="48487-105">Komunikat jest dostarczany przez program SQLite.</span><span class="sxs-lookup"><span data-stu-id="48487-105">The message is provided by SQLite.</span></span> <span data-ttu-id="48487-106">Właściwości `SqliteErrorCode` i `SqliteExtendedErrorCode` zawierają [kod wyniku](https://www.sqlite.org/rescode.html) programu SQLite błędu.</span><span class="sxs-lookup"><span data-stu-id="48487-106">The `SqliteErrorCode` and `SqliteExtendedErrorCode` properties contain the SQLite [result code](https://www.sqlite.org/rescode.html) of the error.</span></span>

<span data-ttu-id="48487-107">Błędy mogą wystąpić w dowolnym momencie, gdy firma Microsoft. Data. sqlite współdziała z natywną biblioteką oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="48487-107">Errors may be encountered any time the Microsoft.Data.Sqlite interacts with the native SQLite library.</span></span> <span data-ttu-id="48487-108">Na poniższej liście przedstawiono typowe scenariusze, w których mogą wystąpić błędy:</span><span class="sxs-lookup"><span data-stu-id="48487-108">The following list shows the common scenarios where errors can occur:</span></span>

* <span data-ttu-id="48487-109">Otwieranie połączenia.</span><span class="sxs-lookup"><span data-stu-id="48487-109">Opening a connection.</span></span>
* <span data-ttu-id="48487-110">Rozpoczęcie transakcji.</span><span class="sxs-lookup"><span data-stu-id="48487-110">Beginning a transaction.</span></span>
* <span data-ttu-id="48487-111">Wykonywanie polecenia.</span><span class="sxs-lookup"><span data-stu-id="48487-111">Executing a command.</span></span>
* <span data-ttu-id="48487-112">Wywoływanie <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span><span class="sxs-lookup"><span data-stu-id="48487-112">Calling <xref:Microsoft.Data.Sqlite.SqliteDataReader.NextResult%2A>.</span></span>

<span data-ttu-id="48487-113">Rozważ uważnie, jak aplikacja będzie obsługiwać te błędy.</span><span class="sxs-lookup"><span data-stu-id="48487-113">Consider carefully how your app will handle these errors.</span></span>

## <a name="locking-retries-and-timeouts"></a><span data-ttu-id="48487-114">Blokowanie, ponawianie próby i limity czasu</span><span class="sxs-lookup"><span data-stu-id="48487-114">Locking, retries, and timeouts</span></span>

<span data-ttu-id="48487-115">W przypadku zablokowania tabel i plików bazy danych w programie SQLite jest agresywne.</span><span class="sxs-lookup"><span data-stu-id="48487-115">SQLite is aggressive when it comes to locking tables and database files.</span></span> <span data-ttu-id="48487-116">Jeśli aplikacja umożliwia równoczesny dostęp do bazy danych, prawdopodobnie wystąpią błędy zajęte i zablokowane.</span><span class="sxs-lookup"><span data-stu-id="48487-116">If your app enables any concurrent database access, you'll likely encounter busy and locked errors.</span></span> <span data-ttu-id="48487-117">Możesz złagodzić wiele błędów, używając [udostępnionej pamięci podręcznej](connection-strings.md#cache) i [rejestrowania z wyprzedzeniem](async.md).</span><span class="sxs-lookup"><span data-stu-id="48487-117">You can mitigate many errors by using a [shared cache](connection-strings.md#cache) and [write-ahead logging](async.md).</span></span>

<span data-ttu-id="48487-118">Za każdym razem, gdy Microsoft. Data. sqlite napotka błąd zajęty lub zablokowany, nastąpi automatyczne ponowienie próby do momentu pomyślnego lub przekroczenie limitu czasu polecenia.</span><span class="sxs-lookup"><span data-stu-id="48487-118">Whenever Microsoft.Data.Sqlite encounters a busy or locked error, it will automatically retry until it succeeds or the command timeout is reached.</span></span>

<span data-ttu-id="48487-119">Można zwiększyć limit czasu polecenia według ustawienia <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="48487-119">You can increase the timeout of command by setting <xref:Microsoft.Data.Sqlite.SqliteCommand.CommandTimeout%2A>.</span></span> <span data-ttu-id="48487-120">Domyślny limit czasu wynosi 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="48487-120">The default timeout is 30 seconds.</span></span> <span data-ttu-id="48487-121">Wartość `0` oznacza brak limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="48487-121">A value of `0` means no timeout.</span></span>

```csharp
// Retry for 60 seconds while locked
command.CommandTimeout = 60;
```

<span data-ttu-id="48487-122">Microsoft. Data. sqlite czasami musi utworzyć obiekt polecenia niejawnego.</span><span class="sxs-lookup"><span data-stu-id="48487-122">Microsoft.Data.Sqlite sometimes needs to create an implicit command object.</span></span> <span data-ttu-id="48487-123">Na przykład podczas BeginTransaction.</span><span class="sxs-lookup"><span data-stu-id="48487-123">For example, during BeginTransaction.</span></span> <span data-ttu-id="48487-124">Aby ustawić limit czasu dla tych poleceń, użyj <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>polecenia.</span><span class="sxs-lookup"><span data-stu-id="48487-124">To set the timeout for these commands, use <xref:Microsoft.Data.Sqlite.SqliteConnection.DefaultTimeout%2A>.</span></span>

```csharp
// Set the default timeout of all commands on this connection
connection.DefaultTimeout = 60;
```

## <a name="see-also"></a><span data-ttu-id="48487-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48487-125">See also</span></span>

* [<span data-ttu-id="48487-126">Kody błędów oprogramowania SQLite</span><span class="sxs-lookup"><span data-stu-id="48487-126">SQLite Error Codes</span></span>](https://www.sqlite.org/rescode.html)
* [<span data-ttu-id="48487-127">Blokowanie plików w programie SQLite</span><span class="sxs-lookup"><span data-stu-id="48487-127">File Locking In SQLite</span></span>](https://www.sqlite.org/lockingv3.html)
* [<span data-ttu-id="48487-128">Tryb udostępnionej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="48487-128">Shared-Cache Mode</span></span>](https://www.sqlite.org/sharedcache.html)
* [<span data-ttu-id="48487-129">Rejestrowanie przed zapisem</span><span class="sxs-lookup"><span data-stu-id="48487-129">Write-Ahead Logging</span></span>](https://www.sqlite.org/wal.html)
