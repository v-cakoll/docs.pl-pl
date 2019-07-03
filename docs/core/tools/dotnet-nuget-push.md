---
title: polecenie wypychania nuget DotNet
description: Polecenie wypychania nuget dotnet wypycha pakietu do serwera i publikuje go.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4d5efa94c6a4494158aea447be98256d2a307cd6
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539132"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="38b2f-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="38b2f-103">dotnet nuget push</span></span>

<span data-ttu-id="38b2f-104">**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="38b2f-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="38b2f-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="38b2f-105">Name</span></span>

<span data-ttu-id="38b2f-106">`dotnet nuget push` -Wypycha pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="38b2f-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="38b2f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="38b2f-107">Synopsis</span></span>

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="38b2f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="38b2f-108">Description</span></span>

<span data-ttu-id="38b2f-109">`dotnet nuget push` Polecenie wypycha pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="38b2f-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="38b2f-110">Używa polecenia push serwera i szczegóły poświadczeń znalezionych w pliku config NuGet systemu lub łańcucha plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="38b2f-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="38b2f-111">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania pakietu NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="38b2f-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="38b2f-112">Konfiguracja domyślna NuGet uzyskuje się przez ładowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* od katalogu głównego dysku i kończący się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="38b2f-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="38b2f-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="38b2f-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="38b2f-114">Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.</span><span class="sxs-lookup"><span data-stu-id="38b2f-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="38b2f-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="38b2f-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="38b2f-116">Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="38b2f-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="38b2f-117">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="38b2f-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="38b2f-118">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="38b2f-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="38b2f-119">Umożliwia polecenie, aby zablokować i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="38b2f-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="38b2f-120">Opcja dostępna od zestawu SDK programu .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="38b2f-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="38b2f-121">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="38b2f-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="38b2f-122">Nie wypychania symbole (nawet jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="38b2f-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="38b2f-123">Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="38b2f-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="38b2f-124">Opcja dostępna od zestawu SDK programu .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="38b2f-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="38b2f-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="38b2f-125">Specifies the server URL.</span></span> <span data-ttu-id="38b2f-126">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="38b2f-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="38b2f-127">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="38b2f-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="38b2f-128">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="38b2f-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="38b2f-129">Określa limit czasu Wypychanie do serwera w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="38b2f-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="38b2f-130">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="38b2f-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="38b2f-131">Określanie 0 (zero sekund) stosuje się wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="38b2f-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="38b2f-132">Przykłady</span><span class="sxs-lookup"><span data-stu-id="38b2f-132">Examples</span></span>

* <span data-ttu-id="38b2f-133">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="38b2f-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="38b2f-134">Wypychania *foo.nupkg* do źródła niestandardowego wypychania `https://customsource`, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="38b2f-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="38b2f-135">Wypycha *foo.nupkg* do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="38b2f-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="38b2f-136">Wypycha *foo.symbols.nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="38b2f-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="38b2f-137">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy limit:</span><span class="sxs-lookup"><span data-stu-id="38b2f-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="38b2f-138">Wypychanie wszystkich *.nupkg* plików w bieżącym katalogu, do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="38b2f-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="38b2f-139">To polecenie nie działa, prawdopodobnie z powodu błędów, które istniały w starszych wersjach zestawu SDK (zestaw SDK programu .NET Core 2.1 i wcześniejszych wersjach).</span><span class="sxs-lookup"><span data-stu-id="38b2f-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="38b2f-140">Aby rozwiązać ten problem, Uaktualnij używanej wersji zestawu SDK lub zamiast tego uruchom następujące polecenie: `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="38b2f-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
