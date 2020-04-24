---
title: Sprawdź zainstalowane wersje .NET Core w systemach Windows, Linux i macOS - .NET Core
description: Dowiedz się, jak wyświetlić listę wersji programu .NET Core zainstalowanych na komputerze. Obejmuje to środowisko uruchomieniowe .NET Core i zestaw SDK.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3a78acee6cf427085e98f14353fc2c0ac65d3d80
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645335"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="ce8fa-104">Jak sprawdzić, czy program .NET Core jest już zainstalowany</span><span class="sxs-lookup"><span data-stu-id="ce8fa-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="ce8fa-105">W tym artykule opisano, jak sprawdzić, które wersje środowiska uruchomieniowego .NET Core i SDK są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="ce8fa-106">.NET core może już zostały zainstalowane, jeśli masz zintegrowane środowisko programistyczne, takie jak Visual Studio lub Visual Studio dla komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="ce8fa-107">Zainstalowanie zestawu SDK instaluje odpowiednie środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="ce8fa-108">Jeśli dowolne polecenie w tym artykule nie powiedzie się, nie masz zainstalowanego środowiska wykonawczego lub SDK.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="ce8fa-109">Aby uzyskać więcej informacji, zobacz [Pobieranie i instalowanie programu .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="ce8fa-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="ce8fa-110">Sprawdź wersje SDK</span><span class="sxs-lookup"><span data-stu-id="ce8fa-110">Check SDK versions</span></span>

<span data-ttu-id="ce8fa-111">Możesz zobaczyć, które wersje .NET Core SDK są obecnie zainstalowane z terminalem.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="ce8fa-112">Otwórz terminal i uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="ce8fa-113">Otrzymujesz dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
2.2.101 [C:\program files\dotnet\sdk]
3.0.100 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
2.2.101 [/home/user/dotnet/sdk]
3.0.100 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
2.2.101 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="ce8fa-114">Sprawdzanie wersji środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="ce8fa-114">Check runtime versions</span></span>

<span data-ttu-id="ce8fa-115">Można zobaczyć, które wersje środowiska uruchomieniowego .NET Core są obecnie zainstalowane za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="ce8fa-116">Otrzymujesz dane wyjściowe podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="ce8fa-117">Sprawdzanie folderów instalacyjnych</span><span class="sxs-lookup"><span data-stu-id="ce8fa-117">Check for install folders</span></span>

<span data-ttu-id="ce8fa-118">Możliwe, że program .NET Core jest zainstalowany, ale nie został dodany do zmiennej `PATH` dla systemu operacyjnego lub profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="ce8fa-119">Uruchamianie poleceń z poprzednich sekcji może nie działać.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="ce8fa-120">Alternatywnie można sprawdzić, czy istnieją foldery instalacyjne .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="ce8fa-121">Po zainstalowaniu programu .NET Core z instalatora lub skryptu jest on instalowany w folderze standardowym.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="ce8fa-122">Przez większość czasu instalator lub skrypt używany do instalowania programu .NET Core umożliwia zainstalowanie w innym folderze.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="ce8fa-123">Jeśli zdecydujesz się zainstalować do innego folderu, dostosuj początek ścieżki folderu.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="ce8fa-124">**plik wykonywalny dotnet**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-124">**dotnet executable**</span></span>\
<span data-ttu-id="ce8fa-125">_C:\\pliki\\programu\\dotnet dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="ce8fa-126">**Plik SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-126">**.NET SDK**</span></span>\
<span data-ttu-id="ce8fa-127">_C:\\pliki\\programu\\dotnet\\sdk {version}\\_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="ce8fa-128">**Środowisko wykonawcze platformy .NET**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-128">**.NET Runtime**</span></span>\
<span data-ttu-id="ce8fa-129">_C:\\pliki\\programu\\dotnet udostępnione\\{runtime-type}\\{version}\\_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="ce8fa-130">**plik wykonywalny dotnet**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-130">**dotnet executable**</span></span>\
<span data-ttu-id="ce8fa-131">_/strona główna/użytkownik/udział/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="ce8fa-132">**Plik SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-132">**.NET SDK**</span></span>\
<span data-ttu-id="ce8fa-133">_/strona główna/użytkownik/udział/dotnet/sdk/{wersja}/_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="ce8fa-134">**Środowisko wykonawcze platformy .NET**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-134">**.NET Runtime**</span></span>\
<span data-ttu-id="ce8fa-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="ce8fa-136">**plik wykonywalny dotnet**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-136">**dotnet executable**</span></span>\
<span data-ttu-id="ce8fa-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="ce8fa-138">**Plik SDK .NET**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-138">**.NET SDK**</span></span>\
<span data-ttu-id="ce8fa-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="ce8fa-140">**Środowisko wykonawcze platformy .NET**</span><span class="sxs-lookup"><span data-stu-id="ce8fa-140">**.NET Runtime**</span></span>\
<span data-ttu-id="ce8fa-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="ce8fa-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="ce8fa-142">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ce8fa-142">More information</span></span>

<span data-ttu-id="ce8fa-143">Za pomocą polecenia `dotnet --info`można zobaczyć zarówno wersje SDK, jak i wersje środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="ce8fa-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="ce8fa-144">Otrzymasz również inne informacje związane ze środowiskiem, takie jak wersja systemu operacyjnego i identyfikator środowiska uruchomieniowego (RID).</span><span class="sxs-lookup"><span data-stu-id="ce8fa-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ce8fa-145">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ce8fa-145">Next steps</span></span>

- <span data-ttu-id="ce8fa-146">[Zainstaluj program .NET Core Runtime](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="ce8fa-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="ce8fa-147">[Zainstaluj pakiet .NET Core SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="ce8fa-147">[Install the .NET Core SDK](sdk.md).</span></span>
