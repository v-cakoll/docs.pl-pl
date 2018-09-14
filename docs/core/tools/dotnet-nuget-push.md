---
title: polecenia DotNet do wypychania nuget — interfejs wiersza polecenia platformy .NET Core
description: Polecenie wypychania nuget dotnet wypycha pakietu do serwera i publikuje go.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: 23d27cef29008955850f9ed9f4a8baed9e7ad982
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527388"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="920cb-103">wypychane nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="920cb-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="920cb-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="920cb-104">Name</span></span>

<span data-ttu-id="920cb-105">`dotnet nuget push` -Wypycha pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="920cb-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="920cb-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="920cb-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="920cb-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="920cb-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="920cb-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="920cb-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="920cb-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="920cb-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="920cb-110">Opis</span><span class="sxs-lookup"><span data-stu-id="920cb-110">Description</span></span>

<span data-ttu-id="920cb-111">`dotnet nuget push` Polecenie wypycha pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="920cb-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="920cb-112">Używa polecenia push serwera i szczegóły poświadczeń znalezionych w pliku config NuGet systemu lub łańcucha plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="920cb-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="920cb-113">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania pakietu NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="920cb-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="920cb-114">Konfiguracja domyślna NuGet uzyskuje się przez ładowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* od katalogu głównego dysku i kończący się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="920cb-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="920cb-115">Argumenty</span><span class="sxs-lookup"><span data-stu-id="920cb-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="920cb-116">Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.</span><span class="sxs-lookup"><span data-stu-id="920cb-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="920cb-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="920cb-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="920cb-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="920cb-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="920cb-119">Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="920cb-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="920cb-120">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="920cb-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="920cb-121">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="920cb-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="920cb-122">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="920cb-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="920cb-123">Nie wypychania symbole (nawet jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="920cb-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="920cb-124">Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="920cb-124">Doesn't append "api/v2/package" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="920cb-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="920cb-125">Specifies the server URL.</span></span> <span data-ttu-id="920cb-126">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="920cb-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="920cb-127">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="920cb-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="920cb-128">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="920cb-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="920cb-129">Określa limit czasu Wypychanie do serwera w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="920cb-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="920cb-130">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="920cb-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="920cb-131">Określanie 0 (zero sekund) stosuje się wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="920cb-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="920cb-132">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="920cb-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="920cb-133">Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="920cb-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="920cb-134">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="920cb-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="920cb-135">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="920cb-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="920cb-136">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="920cb-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="920cb-137">Nie wypychania symbole (nawet jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="920cb-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="920cb-138">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="920cb-138">Specifies the server URL.</span></span> <span data-ttu-id="920cb-139">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="920cb-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="920cb-140">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="920cb-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="920cb-141">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="920cb-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="920cb-142">Określa limit czasu Wypychanie do serwera w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="920cb-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="920cb-143">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="920cb-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="920cb-144">Określanie 0 (zero sekund) stosuje się wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="920cb-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="920cb-145">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="920cb-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="920cb-146">Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="920cb-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="920cb-147">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="920cb-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="920cb-148">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="920cb-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="920cb-149">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="920cb-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="920cb-150">Nie wypychania symbole (nawet jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="920cb-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="920cb-151">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="920cb-151">Specifies the server URL.</span></span> <span data-ttu-id="920cb-152">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="920cb-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="920cb-153">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="920cb-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="920cb-154">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="920cb-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="920cb-155">Określa limit czasu Wypychanie do serwera w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="920cb-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="920cb-156">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="920cb-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="920cb-157">Określanie 0 (zero sekund) stosuje się wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="920cb-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="920cb-158">Przykłady</span><span class="sxs-lookup"><span data-stu-id="920cb-158">Examples</span></span>

<span data-ttu-id="920cb-159">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="920cb-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="920cb-160">Wypychania *foo.nupkg* do źródła niestandardowego wypychania `http://customsource`, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="920cb-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="920cb-161">Wypycha *foo.nupkg* do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="920cb-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="920cb-162">Wypycha *foo.symbols.nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="920cb-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="920cb-163">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy limit:</span><span class="sxs-lookup"><span data-stu-id="920cb-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="920cb-164">Wypychanie wszystkich *.nupkg* plików w bieżącym katalogu, do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="920cb-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`
