---
title: polecenie wypychania nuget DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie wypychania nuget dotnet wypchnięcia pakietu na serwerze i publikuje ją.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: c835b1b9d44b9ed12dc0ea4568414a83c926ae4f
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696497"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="78d11-103">wypychania nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="78d11-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="78d11-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="78d11-104">Name</span></span>

<span data-ttu-id="78d11-105">`dotnet nuget push` -Wypychanie pakietu do serwera i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="78d11-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="78d11-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="78d11-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78d11-107">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="78d11-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78d11-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78d11-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78d11-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78d11-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="78d11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="78d11-110">Description</span></span>

<span data-ttu-id="78d11-111">`dotnet nuget push` Polecenia wypchnięcia pakietu na serwerze i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="78d11-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="78d11-112">Polecenie wypychania używa serwera i szczegółów poświadczeń znalezionych w pliku konfiguracyjnym NuGet systemu lub łańcucha plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="78d11-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="78d11-113">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="78d11-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="78d11-114">Konfiguracja domyślna NuGet są uzyskiwane przez ładowanie *%AppData%\NuGet\NuGet.config* (system Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* rozpoczyna się od katalogu głównego dysku i kończy się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="78d11-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="78d11-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="78d11-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="78d11-116">Określa ścieżkę pliku do pakietu, który ma zostać przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="78d11-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="78d11-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="78d11-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="78d11-118">Oprogramowanie .NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="78d11-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="78d11-119">Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="78d11-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="78d11-120">Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="78d11-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="78d11-121">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="78d11-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="78d11-122">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="78d11-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="78d11-123">Nie push symboli (nawet, jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="78d11-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="78d11-124">Nie dołącza "interfejsu api w wersji 2/packages" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="78d11-124">Doesn't append "api/v2/packages" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="78d11-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="78d11-125">Specifies the server URL.</span></span> <span data-ttu-id="78d11-126">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="78d11-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="78d11-127">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="78d11-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="78d11-128">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="78d11-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="78d11-129">Określa limit czasu dla Wypychanie do serwera w sekundach.</span><span class="sxs-lookup"><span data-stu-id="78d11-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="78d11-130">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="78d11-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="78d11-131">Określanie 0 (zero sekund) jest stosowana wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="78d11-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="78d11-132">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="78d11-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="78d11-133">Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="78d11-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="78d11-134">Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="78d11-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="78d11-135">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="78d11-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="78d11-136">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="78d11-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="78d11-137">Nie push symboli (nawet, jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="78d11-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="78d11-138">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="78d11-138">Specifies the server URL.</span></span> <span data-ttu-id="78d11-139">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="78d11-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="78d11-140">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="78d11-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="78d11-141">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="78d11-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="78d11-142">Określa limit czasu dla Wypychanie do serwera w sekundach.</span><span class="sxs-lookup"><span data-stu-id="78d11-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="78d11-143">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="78d11-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="78d11-144">Określanie 0 (zero sekund) jest stosowana wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="78d11-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="78d11-145">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="78d11-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="78d11-146">Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="78d11-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="78d11-147">Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.</span><span class="sxs-lookup"><span data-stu-id="78d11-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="78d11-148">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="78d11-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="78d11-149">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="78d11-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="78d11-150">Nie push symboli (nawet, jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="78d11-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="78d11-151">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="78d11-151">Specifies the server URL.</span></span> <span data-ttu-id="78d11-152">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="78d11-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="78d11-153">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="78d11-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="78d11-154">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="78d11-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="78d11-155">Określa limit czasu dla Wypychanie do serwera w sekundach.</span><span class="sxs-lookup"><span data-stu-id="78d11-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="78d11-156">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="78d11-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="78d11-157">Określanie 0 (zero sekund) jest stosowana wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="78d11-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="78d11-158">Przykłady</span><span class="sxs-lookup"><span data-stu-id="78d11-158">Examples</span></span>

<span data-ttu-id="78d11-159">Wypchnięcia *foo.nupkg* źródłem wypychania domyślne, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="78d11-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="78d11-160">Wypychania *foo.nupkg* do źródła niestandardowego wypychania `http://customsource`, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="78d11-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="78d11-161">Wypchnięcia *foo.nupkg* źródłem wypychania domyślne:</span><span class="sxs-lookup"><span data-stu-id="78d11-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="78d11-162">Wypchnięcia *foo.symbols.nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="78d11-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="78d11-163">Wypchnięcia *foo.nupkg* w źródle wypychania domyślne Określanie sekundę 360 przekroczenie limitu czasu:</span><span class="sxs-lookup"><span data-stu-id="78d11-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="78d11-164">Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne:</span><span class="sxs-lookup"><span data-stu-id="78d11-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="78d11-165">Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne określenie pliku konfiguracji niestandardowej *./config/My.Config*:</span><span class="sxs-lookup"><span data-stu-id="78d11-165">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
