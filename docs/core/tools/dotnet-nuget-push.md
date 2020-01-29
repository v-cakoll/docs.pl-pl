---
title: polecenia wypychania NuGet dotnet
description: Polecenie polecenia push NuGet narzędzia dotnet wypycha pakiet do serwera i opublikuje go.
author: karann-msft
ms.date: 12/04/2019
ms.openlocfilehash: a483c559dee8b4a82cc2c792f5c2c5e4a8ff3f87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733110"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="aed59-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="aed59-103">dotnet nuget push</span></span>

<span data-ttu-id="aed59-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="aed59-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="aed59-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="aed59-105">Name</span></span>

<span data-ttu-id="aed59-106">`dotnet nuget push` — wypchnij pakiet do serwera i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="aed59-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="aed59-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="aed59-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="aed59-108">Opis</span><span class="sxs-lookup"><span data-stu-id="aed59-108">Description</span></span>

<span data-ttu-id="aed59-109">`dotnet nuget push` polecenie wypycha pakiet do serwera i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="aed59-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="aed59-110">Polecenie push używa informacji o serwerze i poświadczeniach znajdujących się w pliku konfiguracyjnym NuGet systemu lub w łańcuchu plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aed59-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="aed59-111">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="aed59-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="aed59-112">Domyślna konfiguracja narzędzia NuGet jest uzyskiwana przez załadowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$Home/.local/share* (Linux/macOS), a następnie załadowanie jakichkolwiek *NuGet. config* lub *. NuGet\NuGet.config* , począwszy od katalogu głównego dysku i kończącego się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="aed59-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="aed59-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="aed59-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="aed59-114">Określa ścieżkę pliku do pakietu do wypchnięcia.</span><span class="sxs-lookup"><span data-stu-id="aed59-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="aed59-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="aed59-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="aed59-116">Wyłącza buforowanie podczas wypychania do serwera HTTP (S) w celu zmniejszenia użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="aed59-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="aed59-117">Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.</span><span class="sxs-lookup"><span data-stu-id="aed59-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="aed59-118">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="aed59-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="aed59-119">Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="aed59-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="aed59-120">Opcja dostępna od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="aed59-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="aed59-121">Klucz interfejsu API dla serwera programu.</span><span class="sxs-lookup"><span data-stu-id="aed59-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="aed59-122">Nie Wypychaj symboli (nawet jeśli istnieją).</span><span class="sxs-lookup"><span data-stu-id="aed59-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="aed59-123">Nie dołącza "API/v2/Package" do źródłowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="aed59-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="aed59-124">Opcja dostępna od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="aed59-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="aed59-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="aed59-125">Specifies the server URL.</span></span> <span data-ttu-id="aed59-126">Ta opcja jest wymagana, chyba że w pliku konfiguracyjnym NuGet zostanie ustawiona wartość `DefaultPushSource` konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="aed59-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`--skip-duplicate`**

  <span data-ttu-id="aed59-127">Podczas wypychania wielu pakietów do serwera HTTP (S) program traktuje wszystkie 409 odpowiedzi w konflikcie jako ostrzeżenie, aby można było kontynuować wypychanie.</span><span class="sxs-lookup"><span data-stu-id="aed59-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="aed59-128">Dostępne od wersji .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="aed59-128">Available since .NET Core 3.1 SDK.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="aed59-129">Klucz interfejsu API dla serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="aed59-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="aed59-130">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="aed59-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="aed59-131">Określa limit czasu wypychania do serwera w sekundach.</span><span class="sxs-lookup"><span data-stu-id="aed59-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="aed59-132">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="aed59-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="aed59-133">Wartość domyślna to 0 (zero sekund).</span><span class="sxs-lookup"><span data-stu-id="aed59-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="aed59-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="aed59-134">Examples</span></span>

* <span data-ttu-id="aed59-135">Wypchnięcie *foo. nupkg* do domyślnego źródła push, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="aed59-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="aed59-136">Wypchnij *foo. nupkg* do niestandardowego źródła push `https://customsource`, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="aed59-136">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="aed59-137">Wypchnięcie *foo. nupkg* do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="aed59-137">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="aed59-138">Wypchnięcie *foo. Symbols. nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="aed59-138">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="aed59-139">Wypchnięcie *foo. nupkg* do domyślnego źródła push, określając 360-sekundowy limit czasu:</span><span class="sxs-lookup"><span data-stu-id="aed59-139">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="aed59-140">Wypycha wszystkie pliki *. nupkg* w bieżącym katalogu do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="aed59-140">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="aed59-141">Jeśli to polecenie nie działa, może to być spowodowane usterką, która istniała we wcześniejszych wersjach zestawu SDK (zestaw SDK programu .NET Core 2,1 i wcześniejsze wersje).</span><span class="sxs-lookup"><span data-stu-id="aed59-141">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="aed59-142">Aby rozwiązać ten problem, Uaktualnij wersję zestawu SDK lub zamiast tego Uruchom następujące polecenie: `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="aed59-142">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

* <span data-ttu-id="aed59-143">Wypychanie wszystkich plików *. nupkg* , nawet jeśli odpowiedź na 409 jest zwracana przez serwer http (S):</span><span class="sxs-lookup"><span data-stu-id="aed59-143">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
