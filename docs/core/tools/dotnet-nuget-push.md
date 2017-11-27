---
title: polecenie wypychania nuget DotNet - .NET Core interfejsu wiersza polecenia
description: "Polecenie wypychania nuget dotnet wypchnięcia pakietu na serwerze i publikuje ją."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 6721615e4df820ab50ea4f79fbba30daeffe8165
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="5e322-103">wypychania nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="5e322-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5e322-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5e322-104">Name</span></span>

<span data-ttu-id="5e322-105">`dotnet nuget push`-Wypychanie pakietu do serwera i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="5e322-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5e322-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5e322-106">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="5e322-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5e322-107">Description</span></span>

<span data-ttu-id="5e322-108">`dotnet nuget push` Polecenia wypchnięcia pakietu na serwerze i publikuje ją.</span><span class="sxs-lookup"><span data-stu-id="5e322-108">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="5e322-109">Polecenie wypychania używa serwera i szczegółów poświadczeń znalezionych w pliku konfiguracyjnym NuGet systemu lub łańcucha plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5e322-109">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="5e322-110">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="5e322-110">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="5e322-111">Konfiguracja domyślna NuGet są uzyskiwane przez ładowanie *%AppData%\NuGet\NuGet.config* (system Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* rozpoczyna się od katalogu głównego dysku i kończy się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5e322-111">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="5e322-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5e322-112">Arguments</span></span>

`ROOT`

<span data-ttu-id="5e322-113">Określ ścieżkę do pakietu i klucz interfejsu API do dystrybuowania pakietu do serwera.</span><span class="sxs-lookup"><span data-stu-id="5e322-113">Specify the path to the package and your API key to push the package to the server.</span></span>

## <a name="options"></a><span data-ttu-id="5e322-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="5e322-114">Options</span></span>

`-h|--help`

<span data-ttu-id="5e322-115">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e322-115">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="5e322-116">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5e322-116">Specifies the server URL.</span></span> <span data-ttu-id="5e322-117">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="5e322-117">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbols-source <SOURCE>`

<span data-ttu-id="5e322-118">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="5e322-118">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="5e322-119">Określa limit czasu dla Wypychanie do serwera w sekundach.</span><span class="sxs-lookup"><span data-stu-id="5e322-119">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="5e322-120">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="5e322-120">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="5e322-121">Określanie 0 (zero sekund) jest stosowana wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="5e322-121">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="5e322-122">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5e322-122">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="5e322-123">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="5e322-123">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="5e322-124">Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="5e322-124">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="5e322-125">Nie push symboli (nawet, jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="5e322-125">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="5e322-126">Wymusza rejestrowane dane wyjściowe w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="5e322-126">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="5e322-127">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5e322-127">Examples</span></span>

<span data-ttu-id="5e322-128">Wypchnięcia *foo.nupkg* źródłem wypychania domyślne, zapewniając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="5e322-128">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="5e322-129">Wypychania *foo.nupkg* do źródła niestandardowego wypychania `http://customsource`, zapewniając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="5e322-129">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="5e322-130">Wypchnięcia *foo.nupkg* źródłem wypychania domyślne:</span><span class="sxs-lookup"><span data-stu-id="5e322-130">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="5e322-131">Wypchnięcia *foo.symbols.nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="5e322-131">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="5e322-132">Wypchnięcia *foo.nupkg* w źródle wypychania domyślne Określanie 360 drugi limitu czasu:</span><span class="sxs-lookup"><span data-stu-id="5e322-132">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="5e322-133">Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne:</span><span class="sxs-lookup"><span data-stu-id="5e322-133">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="5e322-134">Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne określenie pliku konfiguracji niestandardowej *./config/My.Config*:</span><span class="sxs-lookup"><span data-stu-id="5e322-134">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

<span data-ttu-id="5e322-135">Wszystkie push *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne z maksymalną szczegółowość:</span><span class="sxs-lookup"><span data-stu-id="5e322-135">Push all *.nupkg* files in the current directory to the default push source with maximum verbosity:</span></span>

`dotnet nuget push *.nupkg --verbosity detailed`
