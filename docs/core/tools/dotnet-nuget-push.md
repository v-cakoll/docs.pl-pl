---
title: polecenia wypychania NuGet dotnet
description: Polecenie polecenia push NuGet narzędzia dotnet wypycha pakiet do serwera i opublikuje go.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 3299f79ec62aebdcdbef38f1e8b09a2dc5529ec4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117493"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="f467a-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="f467a-103">dotnet nuget push</span></span>

<span data-ttu-id="f467a-104">**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="f467a-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f467a-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f467a-105">Name</span></span>

<span data-ttu-id="f467a-106">`dotnet nuget push`— Wypchnij pakiet do serwera i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="f467a-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f467a-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="f467a-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f467a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f467a-108">Description</span></span>

<span data-ttu-id="f467a-109">`dotnet nuget push` Polecenie wypycha pakiet do serwera i opublikuje go.</span><span class="sxs-lookup"><span data-stu-id="f467a-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="f467a-110">Polecenie push używa informacji o serwerze i poświadczeniach znajdujących się w pliku konfiguracyjnym NuGet systemu lub w łańcuchu plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f467a-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="f467a-111">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="f467a-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="f467a-112">Domyślna konfiguracja narzędzia NuGet jest uzyskiwana przez załadowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$Home/.local/share* (Linux/macOS), a następnie załadowanie jakichkolwiek *NuGet. config* lub *. NuGet\NuGet.config* , począwszy od katalogu głównego dysk i zakończenie w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f467a-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="f467a-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f467a-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="f467a-114">Określa ścieżkę pliku do pakietu do wypchnięcia.</span><span class="sxs-lookup"><span data-stu-id="f467a-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="f467a-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="f467a-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="f467a-116">Wyłącza buforowanie podczas wypychania do serwera HTTP (S) w celu zmniejszenia użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="f467a-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="f467a-117">Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.</span><span class="sxs-lookup"><span data-stu-id="f467a-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="f467a-118">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="f467a-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="f467a-119">Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="f467a-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="f467a-120">Opcja dostępna od wersji .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f467a-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="f467a-121">Klucz interfejsu API dla serwera programu.</span><span class="sxs-lookup"><span data-stu-id="f467a-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="f467a-122">Nie Wypychaj symboli (nawet jeśli istnieją).</span><span class="sxs-lookup"><span data-stu-id="f467a-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="f467a-123">Nie dołącza "API/v2/Package" do źródłowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="f467a-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="f467a-124">Opcja dostępna od wersji .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f467a-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="f467a-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="f467a-125">Specifies the server URL.</span></span> <span data-ttu-id="f467a-126">Ta opcja jest wymagana, `DefaultPushSource` chyba że wartość konfiguracji jest ustawiona w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="f467a-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="f467a-127">Klucz interfejsu API dla serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="f467a-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="f467a-128">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="f467a-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="f467a-129">Określa limit czasu wypychania do serwera w sekundach.</span><span class="sxs-lookup"><span data-stu-id="f467a-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="f467a-130">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="f467a-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="f467a-131">Wartość domyślna to 0 (zero sekund).</span><span class="sxs-lookup"><span data-stu-id="f467a-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="f467a-132">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f467a-132">Examples</span></span>

* <span data-ttu-id="f467a-133">Wypchnięcie *foo. nupkg* do domyślnego źródła push, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="f467a-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="f467a-134">Wypychanie *foo. nupkg* do niestandardowego źródła `https://customsource`wypychania, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="f467a-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="f467a-135">Wypchnięcie *foo. nupkg* do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="f467a-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="f467a-136">Wypchnięcie *foo. Symbols. nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="f467a-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="f467a-137">Wypchnięcie *foo. nupkg* do domyślnego źródła push, określając 360-sekundowy limit czasu:</span><span class="sxs-lookup"><span data-stu-id="f467a-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="f467a-138">Wypycha wszystkie pliki *. nupkg* w bieżącym katalogu do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="f467a-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="f467a-139">Jeśli to polecenie nie działa, może to być spowodowane usterką, która istniała we wcześniejszych wersjach zestawu SDK (zestaw SDK programu .NET Core 2,1 i wcześniejsze wersje).</span><span class="sxs-lookup"><span data-stu-id="f467a-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="f467a-140">Aby rozwiązać ten problem, Uaktualnij wersję zestawu SDK lub zamiast tego Uruchom następujące polecenie:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="f467a-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
