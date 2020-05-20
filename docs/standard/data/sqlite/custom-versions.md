---
title: Niestandardowe wersje programu SQLite
ms.date: 05/14/2020
description: Dowiedz się, jak używać niestandardowej wersji natywnej biblioteki programu SQLite.
ms.openlocfilehash: 15db10db26bc7c5017313ca020a0e1e528ba207a
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83440840"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="cbf2e-103">Niestandardowe wersje programu SQLite</span><span class="sxs-lookup"><span data-stu-id="cbf2e-103">Custom SQLite versions</span></span>

<span data-ttu-id="cbf2e-104">`Microsoft.Data.Sqlite`jest zbudowany w oparciu o `SQLitePCLRaw` .</span><span class="sxs-lookup"><span data-stu-id="cbf2e-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="cbf2e-105">Możesz użyć niestandardowych wersji natywnej biblioteki programu SQLite przy użyciu pakietu lub przez skonfigurowanie `SQLitePCLRaw` dostawcy.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="cbf2e-106">Pakiety</span><span class="sxs-lookup"><span data-stu-id="cbf2e-106">Bundles</span></span>

<span data-ttu-id="cbf2e-107">`SQLitePCLRaw`zapewnia wygodną obsługę pakietów pakietu, dzięki czemu można łatwo korzystać z odpowiednich zależności na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="cbf2e-108">Pakiet główny domyślnie jest przypisuje `Microsoft.Data.Sqlite` `SQLitePCLRaw.bundle_e_sqlite3` .</span><span class="sxs-lookup"><span data-stu-id="cbf2e-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="cbf2e-109">Aby użyć innego pakietu, zainstaluj `Microsoft.Data.Sqlite.Core` pakiet wraz z pakietem pakietu, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="cbf2e-110">Pakiety są automatycznie inicjowane przez `Microsoft.Data.Sqlite` .</span><span class="sxs-lookup"><span data-stu-id="cbf2e-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="cbf2e-111">Pakiet</span><span class="sxs-lookup"><span data-stu-id="cbf2e-111">Bundle</span></span> | <span data-ttu-id="cbf2e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cbf2e-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="cbf2e-113">SQLitePCLRaw. bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="cbf2e-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="cbf2e-114">Zapewnia spójną wersję oprogramowania SQLite na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="cbf2e-115">Obejmuje rozszerzenia drzewa FTS4, FTS5, JSON1 i R \*.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="cbf2e-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-116">This is the default.</span></span> |
| [<span data-ttu-id="cbf2e-117">SQLitePCLRaw. bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="cbf2e-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="cbf2e-118">Zapewnia nieoficjalną kompilację typu open source `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="cbf2e-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="cbf2e-119">SQLitePCLRaw. bundle_green</span><span class="sxs-lookup"><span data-stu-id="cbf2e-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="cbf2e-120">Analogicznie jak `bundle_e_sqlite3` w przypadku systemu iOS, gdzie używa biblioteki oprogramowania SQLite.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="cbf2e-121">SQLitePCLRaw. bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="cbf2e-121">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="cbf2e-122">`winsqlite3.dll`Program używa biblioteki SQLite systemu w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-122">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="cbf2e-123">SQLitePCLRaw. bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="cbf2e-123">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="cbf2e-124">Używa oficjalnych `SQLCipher` kompilacji z Zetetic (nieuwzględnione).</span><span class="sxs-lookup"><span data-stu-id="cbf2e-124">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="cbf2e-125">Na przykład, aby użyć nieoficjalnej kompilacji typu "open source", `SQLCipher` Użyj następujących poleceń.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-125">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="cbf2e-126">interfejs wiersza polecenia programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="cbf2e-126">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="cbf2e-127">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cbf2e-127">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="cbf2e-128">SQLitePCLRaw dostępne dostawcy</span><span class="sxs-lookup"><span data-stu-id="cbf2e-128">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="cbf2e-129">Jeśli nie korzystasz z pakietu, możesz użyć dostępnych dostawców oprogramowania SQLite z zestawem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-129">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="cbf2e-130">Dostawca</span><span class="sxs-lookup"><span data-stu-id="cbf2e-130">Provider</span></span> | <span data-ttu-id="cbf2e-131">Opis</span><span class="sxs-lookup"><span data-stu-id="cbf2e-131">Description</span></span> |
|--|--|
| [<span data-ttu-id="cbf2e-132">SQLitePCLRaw. Provider. Dynamic</span><span class="sxs-lookup"><span data-stu-id="cbf2e-132">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="cbf2e-133">`dynamic`Dostawca ładuje bibliotekę natywną zamiast używać <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-133">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="cbf2e-134">Aby uzyskać więcej informacji na temat korzystania z tego dostawcy, zobacz [Korzystanie z dostawcy dynamicznego](#use-the-dynamic-provider).</span><span class="sxs-lookup"><span data-stu-id="cbf2e-134">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="cbf2e-135">SQLitePCLRaw. Provider. e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="cbf2e-135">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="cbf2e-136">`e_sqlite3`Jest to domyślny dostawca.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-136">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="cbf2e-137">SQLitePCLRaw. Provider. e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="cbf2e-137">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="cbf2e-138">`e_sqlcipher`Dostawca jest nieoficjalny i nieobsługiwany `SQLCipher` .</span><span class="sxs-lookup"><span data-stu-id="cbf2e-138">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="cbf2e-139">SQLitePCLRaw. Provider. sqlite3</span><span class="sxs-lookup"><span data-stu-id="cbf2e-139">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="cbf2e-140">`sqlite3`Dostawca jest systemem `SQLite` dla systemów iOS, MacOS i Linux.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-140">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="cbf2e-141">SQLitePCLRaw. Provider. SQLCIPHER</span><span class="sxs-lookup"><span data-stu-id="cbf2e-141">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="cbf2e-142">`sqlcipher`Dostawca jest przeznaczony do oficjalnych `SQLCipher` kompilacji z `Zetetic` .</span><span class="sxs-lookup"><span data-stu-id="cbf2e-142">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="cbf2e-143">SQLitePCLRaw. Provider. winsqlite3</span><span class="sxs-lookup"><span data-stu-id="cbf2e-143">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="cbf2e-144">`winsqlite3`Dostawca dotyczy środowisk systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-144">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="cbf2e-145">Aby użyć `sqlite3` dostawcy, użyj następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="cbf2e-145">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="cbf2e-146">interfejs wiersza polecenia programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="cbf2e-146">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="cbf2e-147">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cbf2e-147">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="cbf2e-148">Po zainstalowaniu pakietów należy ustawić dostawcę na `sqlite3` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-148">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="cbf2e-149">Korzystanie z dostawcy dynamicznego</span><span class="sxs-lookup"><span data-stu-id="cbf2e-149">Use the dynamic provider</span></span>

<span data-ttu-id="cbf2e-150">Możesz użyć własnej kompilacji oprogramowania SQLite, wykorzystując `SQLitePCLRaw.provider.dynamic_cdecl` pakiet.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-150">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="cbf2e-151">W takim przypadku użytkownik jest odpowiedzialny za wdrożenie biblioteki natywnej w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-151">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="cbf2e-152">Uwaga Szczegóły wdrażania bibliotek macierzystych w aplikacji różnią się w zależności od używanej platformy .NET i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-152">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="cbf2e-153">Najpierw należy zaimplementować `IGetFunctionPointer` .</span><span class="sxs-lookup"><span data-stu-id="cbf2e-153">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="cbf2e-154">Implementacja programu .NET Core jest następująca:</span><span class="sxs-lookup"><span data-stu-id="cbf2e-154">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="cbf2e-155">Następnie skonfiguruj `SQLitePCLRaw` dostawcę.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-155">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="cbf2e-156">Upewnij się, że jest to gotowe `Microsoft.Data.Sqlite` do użycia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-156">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="cbf2e-157">Należy również unikać używania `SQLitePCLRaw` pakietu zbiorczego, który może zastąpić dostawcę.</span><span class="sxs-lookup"><span data-stu-id="cbf2e-157">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
