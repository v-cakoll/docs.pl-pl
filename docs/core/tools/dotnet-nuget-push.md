---
title: polecenie wypychania nuget DotNet
description: Polecenie wypychania nuget dotnet wypycha pakietu do serwera i publikuje go.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 7382cb93da3d7ed68f5731b3996c735c3f1461e4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631712"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="5af2f-103">wypychane nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="5af2f-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5af2f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5af2f-104">Name</span></span>

<span data-ttu-id="5af2f-105">`dotnet nuget push` -Wypycha pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="5af2f-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5af2f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5af2f-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5af2f-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="5af2f-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5af2f-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5af2f-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="5af2f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5af2f-109">Description</span></span>

<span data-ttu-id="5af2f-110">`dotnet nuget push` Polecenie wypycha pakietu do serwera i publikuje go.</span><span class="sxs-lookup"><span data-stu-id="5af2f-110">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="5af2f-111">Używa polecenia push serwera i szczegóły poświadczeń znalezionych w pliku config NuGet systemu lub łańcucha plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5af2f-111">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="5af2f-112">Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania pakietu NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="5af2f-112">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="5af2f-113">Konfiguracja domyślna NuGet uzyskuje się przez ładowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* od katalogu głównego dysku i kończący się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5af2f-113">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="5af2f-114">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5af2f-114">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="5af2f-115">Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.</span><span class="sxs-lookup"><span data-stu-id="5af2f-115">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="5af2f-116">Opcje</span><span class="sxs-lookup"><span data-stu-id="5af2f-116">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5af2f-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="5af2f-117">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="5af2f-118">Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="5af2f-118">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="5af2f-119">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="5af2f-119">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="5af2f-120">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5af2f-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="5af2f-121">Umożliwia polecenie, aby zablokować i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="5af2f-121">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="5af2f-122">Opcja dostępna od zestawu SDK programu .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="5af2f-122">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="5af2f-123">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5af2f-123">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="5af2f-124">Nie wypychania symbole (nawet jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="5af2f-124">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="5af2f-125">Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="5af2f-125">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="5af2f-126">Opcja dostępna od zestawu SDK programu .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="5af2f-126">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="5af2f-127">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5af2f-127">Specifies the server URL.</span></span> <span data-ttu-id="5af2f-128">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="5af2f-128">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="5af2f-129">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="5af2f-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="5af2f-130">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="5af2f-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="5af2f-131">Określa limit czasu Wypychanie do serwera w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="5af2f-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="5af2f-132">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="5af2f-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="5af2f-133">Określanie 0 (zero sekund) stosuje się wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="5af2f-133">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5af2f-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5af2f-134">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="5af2f-135">Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="5af2f-135">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="5af2f-136">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="5af2f-136">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="5af2f-137">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="5af2f-137">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="5af2f-138">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5af2f-138">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="5af2f-139">Nie wypychania symbole (nawet jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="5af2f-139">Doesn't push symbols (even if present).</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="5af2f-140">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="5af2f-140">Specifies the server URL.</span></span> <span data-ttu-id="5af2f-141">Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.</span><span class="sxs-lookup"><span data-stu-id="5af2f-141">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="5af2f-142">Klucz interfejsu API serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="5af2f-142">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="5af2f-143">Określa adres URL serwera symboli.</span><span class="sxs-lookup"><span data-stu-id="5af2f-143">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="5af2f-144">Określa limit czasu Wypychanie do serwera w ciągu kilku sekund.</span><span class="sxs-lookup"><span data-stu-id="5af2f-144">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="5af2f-145">Wartość domyślna to 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="5af2f-145">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="5af2f-146">Określanie 0 (zero sekund) stosuje się wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="5af2f-146">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="5af2f-147">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5af2f-147">Examples</span></span>

* <span data-ttu-id="5af2f-148">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="5af2f-148">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="5af2f-149">Wypychania *foo.nupkg* do źródła niestandardowego wypychania `https://customsource`, określając klucz interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="5af2f-149">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="5af2f-150">Wypycha *foo.nupkg* do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="5af2f-150">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="5af2f-151">Wypycha *foo.symbols.nupkg* do domyślnego źródła symboli:</span><span class="sxs-lookup"><span data-stu-id="5af2f-151">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="5af2f-152">Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy limit:</span><span class="sxs-lookup"><span data-stu-id="5af2f-152">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="5af2f-153">Wypychanie wszystkich *.nupkg* plików w bieżącym katalogu, do domyślnego źródła push:</span><span class="sxs-lookup"><span data-stu-id="5af2f-153">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```
