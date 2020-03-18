---
title: Podwyższony dostęp dla poleceń dotnet
description: Poznaj najlepsze rozwiązania dotyczące poleceń dotnet, które wymagają podwyższonego dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156767"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="1b5f4-103">Podwyższony dostęp dla poleceń dotnet</span><span class="sxs-lookup"><span data-stu-id="1b5f4-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="1b5f4-104">Najlepsze rozwiązania dotyczące tworzenia oprogramowania prowadzą deweloperów do pisania oprogramowania, które wymaga najmniejszej ilości uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="1b5f4-105">Jednak niektóre programy, takie jak narzędzia do monitorowania wydajności, wymagają uprawnień administratora ze względu na reguły systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="1b5f4-106">W poniższych wskazówkach opisano obsługiwane scenariusze pisania takiego oprogramowania za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span>

<span data-ttu-id="1b5f4-107">Z podwyższonym poziomem uprawnień można uruchomić następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="1b5f4-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="1b5f4-108">`dotnet tool`polecenia, takie jak [instalacja narzędzia dotnet](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="1b5f4-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="1b5f4-109">Nie zaleca się uruchamiania innych poleceń z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="1b5f4-110">W szczególności nie zaleca się podniesienia uprawnień z poleceniami, które używają MSBuild, takie jak [przywracanie dotnet,](dotnet-restore.md) [kompilacja dotnet](dotnet-build.md)i [uruchamianie dotnet](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="1b5f4-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="1b5f4-111">Podstawowym problemem są problemy z zarządzaniem uprawnieniami, gdy użytkownik przechodzi tam iz powrotem między głównym i konta z ograniczeniami po wydaniu poleceń dotnet.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="1b5f4-112">Jako użytkownik z ograniczeniami może okazać się, że nie masz dostępu do pliku utworzonego przez użytkownika głównego.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="1b5f4-113">Istnieją sposoby, aby rozwiązać tę sytuację, ale są one niepotrzebne, aby dostać się w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="1b5f4-114">Polecenia można uruchamiać jako root tak długo, jak długo nie przechodzisz tam iz powrotem między głównym a kontem z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="1b5f4-115">Na przykład kontenery platformy Docker są domyślnie uruchamiane jako katalog główny, więc mają tę charakterystykę.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="1b5f4-116">Globalna instalacja narzędzi</span><span class="sxs-lookup"><span data-stu-id="1b5f4-116">Global tool installation</span></span>

<span data-ttu-id="1b5f4-117">Poniższe instrukcje pokazują zalecany sposób instalowania, uruchamiania i odinstalowywania narzędzi programu .NET Core, które wymagają uprawnień z podwyższonym poziomem uprawnień do wykonania.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="1b5f4-118">Windows</span><span class="sxs-lookup"><span data-stu-id="1b5f4-118">Windows</span></span>](#tab/windows)

### <a name="install-the-tool"></a><span data-ttu-id="1b5f4-119">Zainstaluj narzędzie</span><span class="sxs-lookup"><span data-stu-id="1b5f4-119">Install the tool</span></span>

<span data-ttu-id="1b5f4-120">Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj następujące czynności, aby sprawdzić, czy grupa "Użytkownicy" ma uprawnienia do zapisu lub modyfikowania tego katalogu:</span><span class="sxs-lookup"><span data-stu-id="1b5f4-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="1b5f4-121">Kliknij prawym `%ProgramFiles%\dotnet-tools` przyciskiem myszy folder i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="1b5f4-122">Zostanie otwarte okno dialogowe **Właściwości wspólne.**</span><span class="sxs-lookup"><span data-stu-id="1b5f4-122">The **Common Properties** dialog box opens.</span></span>
- <span data-ttu-id="1b5f4-123">Wybierz kartę **Zabezpieczenia.** W **obszarze Nazwy grup lub użytkowników**sprawdź, czy grupa "Użytkownicy" ma uprawnienia do zapisu lub modyfikowania katalogu.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span>
- <span data-ttu-id="1b5f4-124">Jeśli grupa "Użytkownicy" może zapisywać lub modyfikować katalog, podczas instalowania narzędzi należy użyć innej nazwy katalogu niż *narzędzi dotnet*.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="1b5f4-125">Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="1b5f4-126">Podczas instalacji utworzy folder *narzędzi dotnet.*</span><span class="sxs-lookup"><span data-stu-id="1b5f4-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="1b5f4-127">Uruchamianie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="1b5f4-127">Run the global tool</span></span>

<span data-ttu-id="1b5f4-128">**Wariant 1** Użyj pełnej ścieżki z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="1b5f4-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="1b5f4-129">**Wariant 2** Dodaj nowo utworzony folder `%Path%`do pliku .</span><span class="sxs-lookup"><span data-stu-id="1b5f4-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="1b5f4-130">Wystarczy wykonać tę operację tylko raz.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="1b5f4-131">I uruchomić z:</span><span class="sxs-lookup"><span data-stu-id="1b5f4-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="1b5f4-132">Odinstalowywanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="1b5f4-132">Uninstall the global tool</span></span>

<span data-ttu-id="1b5f4-133">W wierszu z podwyższonym poziomem uprawnień wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="1b5f4-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="1b5f4-134">Linux</span><span class="sxs-lookup"><span data-stu-id="1b5f4-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="1b5f4-135">Macos</span><span class="sxs-lookup"><span data-stu-id="1b5f4-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="1b5f4-136">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="1b5f4-136">Local tools</span></span>

<span data-ttu-id="1b5f4-137">Narzędzia lokalne są objęte zakresem dla drzewa podkatalogu, na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="1b5f4-138">Po uruchomieniu z podwyższonym poziomem uprawnień narzędzia lokalne współużytkują ograniczone środowisko użytkownika z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="1b5f4-139">W systemach Linux i macOS powoduje to ustawienie plików z dostępem tylko dla użytkownika głównego.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="1b5f4-140">Jeśli użytkownik przełączy się z powrotem na konto z ograniczeniami, użytkownik nie może już uzyskać dostępu do plików ani zapisywać ich.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="1b5f4-141">Dlatego nie zaleca się instalowania narzędzi wymagających podniesienia uprawnień jako narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="1b5f4-142">Zamiast tego `--tool-path` użyj opcji i poprzednich wytycznych dla narzędzi globalnych.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="1b5f4-143">Elewacja podczas rozwoju</span><span class="sxs-lookup"><span data-stu-id="1b5f4-143">Elevation during development</span></span>

<span data-ttu-id="1b5f4-144">Podczas tworzenia aplikacji może być konieczne podwyższony dostęp do testowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="1b5f4-145">Ten scenariusz jest typowy dla aplikacji IoT, na przykład.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="1b5f4-146">Zaleca się utworzenie aplikacji bez elewacji, a następnie uruchomienie jej z rzędną.</span><span class="sxs-lookup"><span data-stu-id="1b5f4-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="1b5f4-147">Istnieje kilka wzorców, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1b5f4-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="1b5f4-148">Przy użyciu wygenerowanego pliku wykonywalnego (zapewnia najlepszą wydajność uruchamiania):</span><span class="sxs-lookup"><span data-stu-id="1b5f4-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- <span data-ttu-id="1b5f4-149">Za pomocą polecenia [dotnet run](dotnet-run.md) z flagą, `—no-build` aby uniknąć generowania nowych plików binarnych:</span><span class="sxs-lookup"><span data-stu-id="1b5f4-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="1b5f4-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b5f4-150">See also</span></span>

- [<span data-ttu-id="1b5f4-151">Omówienie podstawowych narzędzi globalnych .NET</span><span class="sxs-lookup"><span data-stu-id="1b5f4-151">.NET Core Global Tools overview</span></span>](global-tools.md)
