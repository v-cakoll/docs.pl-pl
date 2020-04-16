---
title: dotnet nuget push, polecenie
description: Polecenie dotnet nuget push wypycha pakiet do serwera i publikuje go.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 96f8d008c8306a0782d5149360a24bb4097a1ec4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463518"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="cb71f-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="cb71f-103">dotnet nuget push</span></span>

<span data-ttu-id="cb71f-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="cb71f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cb71f-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cb71f-105">Name</span></span>

<span data-ttu-id="cb71f-106">`dotnet nuget push`- Wciska paczkę na serwer i go publikuje.</span><span class="sxs-lookup"><span data-stu-id="cb71f-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb71f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cb71f-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="cb71f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cb71f-108">Description</span></span>

<span data-ttu-id="cb71f-109">Polecenie `dotnet nuget push` wypycha pakiet do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="cb71f-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="cb71f-110">Polecenie wypychania używa szczegółów serwera i poświadczeń znalezionych w pliku konfiguracyjnym nuget systemu lub łańcuchu plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="cb71f-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="cb71f-111">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania nuget .](/nuget/consume-packages/configuring-nuget-behavior)</span><span class="sxs-lookup"><span data-stu-id="cb71f-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="cb71f-112">Domyślną konfigurację NuGet uzyskuje się przez załadowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), a następnie załadowanie *dowolnego nuget.config* lub *.nuget\nuget.config,* zaczynając od katalogu głównego dysku, a kończąc na bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cb71f-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="cb71f-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cb71f-113">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="cb71f-114">Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.</span><span class="sxs-lookup"><span data-stu-id="cb71f-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="cb71f-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="cb71f-115">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="cb71f-116">Wyłącza buforowanie podczas wypychania na serwer HTTP(S) w celu zmniejszenia użycia pamięci.</span><span class="sxs-lookup"><span data-stu-id="cb71f-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="cb71f-117">Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="cb71f-117">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cb71f-118">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="cb71f-118">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="cb71f-119">Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="cb71f-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="cb71f-120">Opcja dostępna od pliku .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb71f-120">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="cb71f-121">Klucz interfejsu API serwera.</span><span class="sxs-lookup"><span data-stu-id="cb71f-121">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="cb71f-122">Nie wypycha symboli (nawet jeśli są obecne).</span><span class="sxs-lookup"><span data-stu-id="cb71f-122">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="cb71f-123">Nie dołącza "api/v2/package" do źródłowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="cb71f-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="cb71f-124">Opcja dostępna od pliku .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb71f-124">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="cb71f-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="cb71f-125">Specifies the server URL.</span></span> <span data-ttu-id="cb71f-126">Ta opcja jest `DefaultPushSource` wymagana, chyba że wartość konfiguracyjny jest ustawiona w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="cb71f-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="cb71f-127">Podczas wypychania wielu pakietów na serwer HTTP(S) traktuje dowolną odpowiedź konfliktu 409 jako ostrzeżenie, aby wypychanie było kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="cb71f-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="cb71f-128">Dostępne od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="cb71f-128">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="cb71f-129">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="cb71f-129">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="cb71f-130">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="cb71f-130">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="cb71f-131">Określa limit czasu do wypychania do serwera w sekundach.</span><span class="sxs-lookup"><span data-stu-id="cb71f-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="cb71f-132">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="cb71f-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="cb71f-133">Określenie wartości 0 (zero sekund) powoduje zastosowanie wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="cb71f-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="cb71f-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cb71f-134">Examples</span></span>

- <span data-ttu-id="cb71f-135">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="cb71f-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="cb71f-136">Wypychaj *foo.nupkg* do oficjalnego serwera NuGet, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="cb71f-136">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="cb71f-137">Wypychanie *foo.nupkg* do `https://customsource`niestandardowego źródła wypychania , określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="cb71f-137">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="cb71f-138">Popycha *foo.nupkg* do domyślnego źródła wypychania:</span><span class="sxs-lookup"><span data-stu-id="cb71f-138">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="cb71f-139">Popycha *foo.symbols.nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="cb71f-139">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="cb71f-140">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy limit czasu:</span><span class="sxs-lookup"><span data-stu-id="cb71f-140">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="cb71f-141">Wypycha wszystkie pliki *nupkg* w bieżącym katalogu do domyślnego źródła wypychania:</span><span class="sxs-lookup"><span data-stu-id="cb71f-141">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="cb71f-142">Jeśli to polecenie nie działa, może to być spowodowane błędem, który istniał w starszych wersjach SDK (.NET Core 2.1 SDK i wcześniejszych wersjach).</span><span class="sxs-lookup"><span data-stu-id="cb71f-142">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="cb71f-143">Aby rozwiązać ten problem, należy uaktualnić wersję SDK lub zamiast tego uruchomić następujące polecenie:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="cb71f-143">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="cb71f-144">Wypycha wszystkie pliki nupkg, nawet jeśli odpowiedź na konflikt 409 jest zwracana przez serwer HTTP(S):Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span><span class="sxs-lookup"><span data-stu-id="cb71f-144">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
