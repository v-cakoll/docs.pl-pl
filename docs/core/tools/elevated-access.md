---
title: Dostęp z podwyższonym poziomem uprawnień dla poleceń dotnet
description: Zapoznaj się z najlepszymi rozwiązaniami dotyczącymi poleceń dotnet wymagających podwyższonego poziomu dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: cf7c93a0adcae7092a61a6fc6046cd45cf00bf58
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216306"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="2f1a3-103">Dostęp z podwyższonym poziomem uprawnień dla poleceń dotnet</span><span class="sxs-lookup"><span data-stu-id="2f1a3-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="2f1a3-104">Wskazówki dotyczące tworzenia oprogramowania — Przewodnik po tworzeniu oprogramowania wymagającego najmniejszego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="2f1a3-105">Jednak niektóre programy, takie jak narzędzia do monitorowania wydajności, wymagają uprawnień administratora z powodu reguł systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="2f1a3-106">Poniższe wskazówki opisują obsługiwane scenariusze pisania oprogramowania przy użyciu programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="2f1a3-107">Następujące polecenia można uruchomić z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="2f1a3-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="2f1a3-108">`dotnet tool`polecenia, takie jak [Instalacja narzędzia dotnet](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="2f1a3-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="2f1a3-109">Nie zalecamy uruchamiania innych poleceń z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="2f1a3-110">W szczególności nie zaleca się podniesienia uprawnień za pomocą poleceń korzystających z programu MSBuild, takich jak [dotnet Restore](dotnet-restore.md), [kompilacja dotnet](dotnet-build.md)i [uruchomienie dotnet](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="2f1a3-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="2f1a3-111">Podstawowym problemem jest problemy z zarządzaniem uprawnieniami, gdy użytkownik przechodzi między głównym i ograniczonym kontem po wydaniu polecenia dotnet.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="2f1a3-112">Może się okazać, że użytkownik z ograniczeniami nie ma dostępu do pliku skompilowanego przez użytkownika root.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="2f1a3-113">Istnieją sposoby rozwiązania tej sytuacji, ale nie są one potrzebne do pierwszego miejsca.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="2f1a3-114">Polecenia można uruchamiać jako główne, o ile nie przechodzą z powrotem między głównym i ograniczonym kontem.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="2f1a3-115">Na przykład kontenery platformy Docker są domyślnie uruchamiane jako główne, więc mają tę cechę.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="2f1a3-116">Instalacja narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="2f1a3-116">Global tool installation</span></span>

<span data-ttu-id="2f1a3-117">Poniższe instrukcje przedstawiają zalecaną metodę instalowania, uruchamiania i odinstalowywania narzędzi .NET Core, które wymagają podniesionych uprawnień do wykonania.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="2f1a3-118">Windows</span><span class="sxs-lookup"><span data-stu-id="2f1a3-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="2f1a3-119">Instalowanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="2f1a3-119">Install the global tool</span></span>

<span data-ttu-id="2f1a3-120">Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj poniższe czynności, aby sprawdzić, czy grupa "Użytkownicy" ma uprawnienia do zapisywania lub modyfikowania tego katalogu:</span><span class="sxs-lookup"><span data-stu-id="2f1a3-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="2f1a3-121">Kliknij prawym przyciskiem `%ProgramFiles%\dotnet-tools` myszy folder i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="2f1a3-122">Zostanie otwarte okno dialogowe **wspólne właściwości** .</span><span class="sxs-lookup"><span data-stu-id="2f1a3-122">The **Common Properties** dialog box opens.</span></span> 
- <span data-ttu-id="2f1a3-123">Wybierz kartę **zabezpieczenia** . W obszarze **nazwy grup lub użytkowników**Sprawdź, czy grupa "Użytkownicy" ma uprawnienia do zapisywania lub modyfikowania katalogu.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
- <span data-ttu-id="2f1a3-124">Jeśli grupa "Użytkownicy" może zapisywać lub modyfikować katalog, użyj innej nazwy katalogu podczas instalowania narzędzi, a nie *narzędzi dotnet*.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="2f1a3-125">Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="2f1a3-126">Podczas instalacji zostanie utworzony folder *narzędzi dotnet* .</span><span class="sxs-lookup"><span data-stu-id="2f1a3-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="2f1a3-127">Uruchamianie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="2f1a3-127">Run the global tool</span></span>

<span data-ttu-id="2f1a3-128">**Opcja 1** Użyj pełnej ścieżki z podniesionym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="2f1a3-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="2f1a3-129">**Opcja 2** Dodaj nowo utworzony folder do `%Path%`programu.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="2f1a3-130">Tę operację należy wykonać tylko raz.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="2f1a3-131">I uruchom z:</span><span class="sxs-lookup"><span data-stu-id="2f1a3-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="2f1a3-132">Odinstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="2f1a3-132">Uninstall the global tool</span></span>

<span data-ttu-id="2f1a3-133">W wierszu polecenia z podwyższonym poziomem uprawnień wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="2f1a3-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="2f1a3-134">Linux</span><span class="sxs-lookup"><span data-stu-id="2f1a3-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[<span data-ttu-id="2f1a3-135">macOS</span><span class="sxs-lookup"><span data-stu-id="2f1a3-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="2f1a3-136">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="2f1a3-136">Local tools</span></span>

<span data-ttu-id="2f1a3-137">Narzędzia lokalne są objęte zakresem drzewa dla każdego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="2f1a3-138">W przypadku korzystania z podwyższonego poziomu uprawnień narzędzia lokalne udostępniają środowisko użytkownika z ograniczeniami do środowiska z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="2f1a3-139">W systemie Linux i macOS w wyniku tego są ustawiane pliki z dostępem tylko do użytkownika root.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="2f1a3-140">Jeśli użytkownik przełączy się z powrotem do konta z ograniczeniami, użytkownik nie będzie mógł uzyskać dostępu do plików ani zapisywać do nich.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="2f1a3-141">Instalowanie narzędzi wymagających podniesienia uprawnień jako lokalnych narzędzi nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="2f1a3-142">Zamiast tego należy użyć `--tool-path` opcji i poprzednich wytycznych dla narzędzi globalnych.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="2f1a3-143">Podniesienie uprawnień podczas opracowywania</span><span class="sxs-lookup"><span data-stu-id="2f1a3-143">Elevation during development</span></span>

<span data-ttu-id="2f1a3-144">Podczas programowania może być potrzebny podwyższony poziom dostępu do testowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="2f1a3-145">Ten scenariusz jest typowy dla aplikacji IoT, na przykład.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="2f1a3-146">Zalecamy, aby skompilować aplikację bez podniesienia uprawnień, a następnie uruchomić ją z podniesionymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="2f1a3-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="2f1a3-147">Istnieje kilka wzorców:</span><span class="sxs-lookup"><span data-stu-id="2f1a3-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="2f1a3-148">Przy użyciu wygenerowanego pliku wykonywalnego (zapewnia najlepszą wydajność uruchamiania):</span><span class="sxs-lookup"><span data-stu-id="2f1a3-148">Using generated executable (it provides the best startup performance):</span></span>

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="2f1a3-149">Za pomocą polecenia [dotnet Run](dotnet-run.md) z `—no-build` flagą, aby uniknąć generowania nowych plików binarnych:</span><span class="sxs-lookup"><span data-stu-id="2f1a3-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="2f1a3-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f1a3-150">See also</span></span>

- [<span data-ttu-id="2f1a3-151">Globalne narzędzia platformy .NET Core — Omówienie</span><span class="sxs-lookup"><span data-stu-id="2f1a3-151">.NET Core Global Tools overview</span></span>](global-tools.md)
