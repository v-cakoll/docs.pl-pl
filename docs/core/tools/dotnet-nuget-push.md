---
title: polecenie wypychania dotnet nuget
description: Polecenie wypychania dotnet nuget wypycha pakiet do serwera i publikuje go.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: d4ef8e58908fe488c712debff3b313ac0908b43e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503662"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="987f3-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="987f3-103">dotnet nuget push</span></span>

<span data-ttu-id="987f3-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="987f3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="987f3-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="987f3-105">Name</span></span>

<span data-ttu-id="987f3-106">`dotnet nuget push`- Wypycha paczkę na serwer i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="987f3-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="987f3-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="987f3-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="987f3-108">Opis</span><span class="sxs-lookup"><span data-stu-id="987f3-108">Description</span></span>

<span data-ttu-id="987f3-109">Polecenie `dotnet nuget push` wypycha pakiet do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="987f3-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="987f3-110">Polecenie push używa danych serwera i poświadczeń znalezionych w pliku konfiguracyjnym NuGet systemu lub łańcuchu plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="987f3-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="987f3-111">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="987f3-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="987f3-112">Domyślną konfigurację NuGet uzyskuje się przez wczytanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), a następnie ładowanie *dowolnego nuget.config* lub *.nuget\nuget.config,* zaczynając od katalogu głównego dysku, a kończąc w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="987f3-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="987f3-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="987f3-113">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="987f3-114">Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.</span><span class="sxs-lookup"><span data-stu-id="987f3-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="987f3-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="987f3-115">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="987f3-116">Wyłącza buforowanie podczas wypychania do serwera HTTP(S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="987f3-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="987f3-117">Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="987f3-117">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="987f3-118">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="987f3-118">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="987f3-119">Umożliwia blokowanie polecenia i wymaga ręcznego działania dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="987f3-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="987f3-120">Opcja dostępna od sdk .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="987f3-120">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="987f3-121">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="987f3-121">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="987f3-122">Nie wciska symboli (nawet jeśli są obecne).</span><span class="sxs-lookup"><span data-stu-id="987f3-122">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="987f3-123">Nie dołącza "api/v2/package" do źródłowego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="987f3-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="987f3-124">Opcja dostępna od sdk .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="987f3-124">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="987f3-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="987f3-125">Specifies the server URL.</span></span> <span data-ttu-id="987f3-126">Ta opcja jest wymagana, chyba `DefaultPushSource` że wartość konfiguratowa jest ustawiona w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="987f3-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="987f3-127">Podczas wypychania wielu pakietów do serwera HTTP(S) traktuje dowolną odpowiedź 409 Konflikt jako ostrzeżenie, dzięki czemu wypychanie można kontynuować.</span><span class="sxs-lookup"><span data-stu-id="987f3-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="987f3-128">Dostępne od sdk .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="987f3-128">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="987f3-129">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="987f3-129">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="987f3-130">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="987f3-130">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="987f3-131">Określa uchył czasu wypychania do serwera w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="987f3-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="987f3-132">Domyślnie 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="987f3-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="987f3-133">Określenie 0 (zero sekund) jest stosowane wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="987f3-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="987f3-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="987f3-134">Examples</span></span>

- <span data-ttu-id="987f3-135">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="987f3-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="987f3-136">Wypchnij *foo.nupkg* do oficjalnego serwera NuGet, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="987f3-136">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="987f3-137">Wypchnij *foo.nupkg* do niestandardowego źródła `https://customsource`wypychania, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="987f3-137">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="987f3-138">Popycha *foo.nupkg* do domyślnego źródła wypychania:</span><span class="sxs-lookup"><span data-stu-id="987f3-138">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="987f3-139">Wypycha *foo.symbols.nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="987f3-139">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="987f3-140">Popycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy timeout:</span><span class="sxs-lookup"><span data-stu-id="987f3-140">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="987f3-141">Wypycha wszystkie pliki *nupkg* w bieżącym katalogu do domyślnego źródła wypychania:</span><span class="sxs-lookup"><span data-stu-id="987f3-141">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="987f3-142">Jeśli to polecenie nie działa, może to być spowodowane błędem, który istniał w starszych wersjach sdk (.NET Core 2.1 SDK i wcześniejszych wersjach).</span><span class="sxs-lookup"><span data-stu-id="987f3-142">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="987f3-143">Aby rozwiązać ten problem, uaktualnij wersję sdk lub zamiast tego uruchom następujące polecenie:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="987f3-143">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="987f3-144">Wypycha wszystkie pliki *.nupkg,* nawet jeśli odpowiedź na konflikt 409 jest zwracana przez serwer HTTP(S):Pushes all .nupkg files even if a 409 Conflict response is returned by an HTTP(S) server:</span><span class="sxs-lookup"><span data-stu-id="987f3-144">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
