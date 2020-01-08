---
title: Niestandardowe wersje programu SQLite
ms.date: 12/13/2019
description: Dowiedz się, jak używać niestandardowej wersji natywnej biblioteki programu SQLite.
ms.openlocfilehash: 8a2646138ea9dbecf412a2e8e0e347e2d71a5b0b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447147"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="3bcc5-103">Niestandardowe wersje programu SQLite</span><span class="sxs-lookup"><span data-stu-id="3bcc5-103">Custom SQLite versions</span></span>

<span data-ttu-id="3bcc5-104">Microsoft. Data. SQLite jest oparty na SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-104">Microsoft.Data.Sqlite is built on top of SQLitePCLRaw.</span></span> <span data-ttu-id="3bcc5-105">Możesz użyć niestandardowych wersji natywnej biblioteki programu SQLite przy użyciu pakietu lub przez skonfigurowanie dostawcy SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a SQLitePCLRaw provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="3bcc5-106">Pakiety</span><span class="sxs-lookup"><span data-stu-id="3bcc5-106">Bundles</span></span>

<span data-ttu-id="3bcc5-107">Program SQLitePCLRaw udostępnia pakiety pakietów, które ułatwiają wprowadzanie odpowiednich zależności między różnymi platformami.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-107">SQLitePCLRaw provides bundle packages that make it easy to bring in the right dependencies across different platforms.</span></span>

<span data-ttu-id="3bcc5-108">Główny pakiet Microsoft. Data. sqlite domyślnie znajduje się w SQLitePCLRaw. bundle_e_sqlite3.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-108">The main Microsoft.Data.Sqlite package brings in SQLitePCLRaw.bundle_e_sqlite3 by default.</span></span>

<span data-ttu-id="3bcc5-109">Aby użyć innego pakietu, zainstaluj pakiet `Microsoft.Data.Sqlite.Core` zamiast niego wraz z pakietem pakietu, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="3bcc5-110">Pakiety są automatycznie inicjowane przez firmę Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-110">Bundles are automatically initialized by Microsoft.Data.Sqlite.</span></span>

| <span data-ttu-id="3bcc5-111">Pakiet</span><span class="sxs-lookup"><span data-stu-id="3bcc5-111">Bundle</span></span> | <span data-ttu-id="3bcc5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3bcc5-112">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3bcc5-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="3bcc5-113">SQLitePCLRaw.bundle_e_sqlite3</span></span> | <span data-ttu-id="3bcc5-114">Zapewnia spójną wersję oprogramowania SQLite na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="3bcc5-115">Obejmuje FTS4, FTS5, JSON1 i</span><span class="sxs-lookup"><span data-stu-id="3bcc5-115">Includes the FTS4, FTS5, JSON1, and</span></span> | <span data-ttu-id="3bcc5-116">Rozszerzenia drzewa R \*.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-116">R\*Tree extensions.</span></span> <span data-ttu-id="3bcc5-117">Jest to domyślne ustawienie.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-117">This is the default.</span></span> |
| <span data-ttu-id="3bcc5-118">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="3bcc5-118">SQLitePCLRaw.bundle_green</span></span> | <span data-ttu-id="3bcc5-119">Analogicznie jak bundle_e_sqlite3, z wyjątkiem systemu iOS, gdzie używa biblioteki oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-119">Same as bundle_e_sqlite3, except on iOS where it uses the system SQLite library.</span></span> |
| <span data-ttu-id="3bcc5-120">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="3bcc5-120">SQLitePCLRaw.bundle_zetetic</span></span> | <span data-ttu-id="3bcc5-121">Używa oficjalnych kompilacji SQLCIPHER z Zetetic (nieuwzględnione).</span><span class="sxs-lookup"><span data-stu-id="3bcc5-121">Uses the official SQLCipher builds from Zetetic (not included).</span></span> |
| <span data-ttu-id="3bcc5-122">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="3bcc5-122">SQLitePCLRaw.bundle_winsqlite3</span></span> | <span data-ttu-id="3bcc5-123">Używa winsqlite3. dll, systemowej biblioteki oprogramowania SQLite w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-123">Uses winsqlite3.dll, the system SQLite library on Windows 10.</span></span> |
| <span data-ttu-id="3bcc5-124">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="3bcc5-124">SQLitePCLRaw.bundle_e_sqlcipher</span></span> | <span data-ttu-id="3bcc5-125">Zapewnia nieoficjalną kompilację SQLCIPHER typu open source.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-125">Provides an unofficial, open-source build of SQLCipher.</span></span> |

<span data-ttu-id="3bcc5-126">Na przykład, aby użyć nieoficjalnej kompilacji SQLCIPHER typu open source, użyj następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-126">For example, to use the unofficial, open-source build of SQLCipher use the following commands.</span></span>

### <a name="net-core-clitabnetcore-cli"></a>[<span data-ttu-id="3bcc5-127">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="3bcc5-127">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studiotabvisual-studio"></a>[<span data-ttu-id="3bcc5-128">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3bcc5-128">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a><span data-ttu-id="3bcc5-129">Dostawcy SQLitePCLRaw</span><span class="sxs-lookup"><span data-stu-id="3bcc5-129">SQLitePCLRaw providers</span></span>

<span data-ttu-id="3bcc5-130">Możesz użyć własnej kompilacji oprogramowania SQLite, wykorzystując pakiet `SQLitePCLRaw.provider.dynamic_cdecl`.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-130">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="3bcc5-131">W takim przypadku użytkownik jest odpowiedzialny za wdrożenie biblioteki natywnej w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-131">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="3bcc5-132">Uwaga Szczegóły wdrażania bibliotek macierzystych w aplikacji różnią się w zależności od używanej platformy .NET i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-132">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="3bcc5-133">Najpierw musisz zaimplementować IGetFunctionPointer.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-133">First, you'll need to implement IGetFunctionPointer.</span></span> <span data-ttu-id="3bcc5-134">Implementacja jest stosunkowo prosta w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-134">The implementation is fairly trivial on .NET Core.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="3bcc5-135">Następnie skonfiguruj dostawcę SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-135">Next, configure the SQLitePCLRaw provider.</span></span> <span data-ttu-id="3bcc5-136">Upewnij się, że w aplikacji jest używany program Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-136">Ensure this is done before Microsoft.Data.Sqlite is used in your app.</span></span> <span data-ttu-id="3bcc5-137">Należy również unikać używania pakietu pakietów SQLitePCLRaw, który może zastąpić dostawcę.</span><span class="sxs-lookup"><span data-stu-id="3bcc5-137">Also, avoid using a SQLitePCLRaw bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
