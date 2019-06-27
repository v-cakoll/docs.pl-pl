---
title: Podwyższonego poziomu dostępu dla polecenia dotnet
description: Poznaj najlepsze rozwiązania dla polecenia dotnet, wymagających podwyższonego poziomu dostępu.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410645"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="9d01c-103">Podwyższonego poziomu dostępu dla polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="9d01c-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="9d01c-104">Najlepszych praktyk tworzenia oprogramowania przewodnik deweloperów oprogramowania, wymagającego najmniejszą ilością uprawnień do zapisu.</span><span class="sxs-lookup"><span data-stu-id="9d01c-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="9d01c-105">Jednak niektóre programy, takie jak narzędzia monitorowania wydajności, wymaga uprawnień administratora z powodu zasad systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9d01c-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="9d01c-106">Poniższe wskazówki opisano obsługiwane scenariusze dotyczące pisania oprogramowania za pomocą programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d01c-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="9d01c-107">Następujące polecenia mogą być uruchamiane z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="9d01c-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="9d01c-108">`dotnet tool` polecenia takie jak [instalacji narzędzi dotnet](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="9d01c-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="9d01c-109">Nie zaleca się uruchamiania innych poleceń z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="9d01c-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="9d01c-110">W szczególności, nie zaleca się podniesienie uprawnień za pomocą poleceń korzystających z programu MSBuild, takich jak [dotnet restore](dotnet-restore.md), [kompilacji dotnet](dotnet-build.md), i [dotnet, uruchom](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="9d01c-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="9d01c-111">Podstawowym problemem jest problemów z zarządzaniem uprawnieniami, gdy użytkownik przechodzi i z powrotem między głównym i ograniczeniami konta po wydaniu polecenia dotnet.</span><span class="sxs-lookup"><span data-stu-id="9d01c-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="9d01c-112">Może się okazać jako użytkowników z ograniczeniami, nie masz dostępu do pliku, utworzone przez użytkownika głównego.</span><span class="sxs-lookup"><span data-stu-id="9d01c-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="9d01c-113">Sposoby, aby rozwiązać ten problem, ale są one zbędne zagłębieniem się w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="9d01c-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="9d01c-114">Możesz uruchamiać polecenia jako użytkownik główny, tak długo, jak nie przejścia i z powrotem między głównym i konta z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="9d01c-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="9d01c-115">Na przykład kontenery platformy Docker jako użytkownik główny domyślnie uruchamiane, dzięki czemu mają one Cecha ta.</span><span class="sxs-lookup"><span data-stu-id="9d01c-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="9d01c-116">Instalowanie narzędzi globalne</span><span class="sxs-lookup"><span data-stu-id="9d01c-116">Global tool installation</span></span>

<span data-ttu-id="9d01c-117">Poniższe instrukcje przedstawiają zalecaną metodą instalacji, uruchom i odinstalować narzędzia platformy .NET Core, które wymagają podniesionego poziomu uprawnień do wykonania.</span><span class="sxs-lookup"><span data-stu-id="9d01c-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="9d01c-118">Windows</span><span class="sxs-lookup"><span data-stu-id="9d01c-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="9d01c-119">Zainstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="9d01c-119">Install the global tool</span></span>

<span data-ttu-id="9d01c-120">Jeśli folder `%ProgramFiles%\dotnet-tools` już istnieje, wykonaj następujące czynności, aby sprawdzić, czy grupa "Użytkownicy", ma uprawnienia do zapisu lub modyfikowania tego katalogu:</span><span class="sxs-lookup"><span data-stu-id="9d01c-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

* <span data-ttu-id="9d01c-121">Kliknij prawym przyciskiem myszy `%ProgramFiles%\dotnet-tools` i wybierz polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9d01c-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="9d01c-122">**Wspólne właściwości** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="9d01c-122">The **Common Properties** dialog box opens.</span></span> 
* <span data-ttu-id="9d01c-123">Wybierz **zabezpieczeń** kartę. W obszarze **nazwy grupy lub użytkownika**, sprawdź, czy grupa "Użytkownicy", ma uprawnienia do zapisu lub modyfikowania katalogu.</span><span class="sxs-lookup"><span data-stu-id="9d01c-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
* <span data-ttu-id="9d01c-124">Jeśli grupy "Użytkownicy" można zapisać lub zmodyfikować katalogu, należy użyć nazwy z innym katalogiem podczas instalowania narzędzi zamiast *narzędzi dotnet*.</span><span class="sxs-lookup"><span data-stu-id="9d01c-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="9d01c-125">Aby zainstalować narzędzia, uruchom następujące polecenie w wierszu polecenia z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="9d01c-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="9d01c-126">Utworzy on *narzędzi dotnet* folderu podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="9d01c-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="9d01c-127">Uruchom narzędzie globalnej</span><span class="sxs-lookup"><span data-stu-id="9d01c-127">Run the global tool</span></span>

<span data-ttu-id="9d01c-128">**Opcja 1** użycie pełnej ścieżki w wierszu polecenia z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="9d01c-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="9d01c-129">**Opcja 2** Dodaj nowo utworzony folder do `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="9d01c-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="9d01c-130">Wystarczy wykonać tę operację na raz.</span><span class="sxs-lookup"><span data-stu-id="9d01c-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="9d01c-131">A następnie uruchom za pomocą:</span><span class="sxs-lookup"><span data-stu-id="9d01c-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="9d01c-132">Odinstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="9d01c-132">Uninstall the global tool</span></span>

<span data-ttu-id="9d01c-133">W wierszu polecenia z podwyższonym poziomem uprawnień wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9d01c-133">In an elevated prompt, type the following command:</span></span>

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="9d01c-134">Linux</span><span class="sxs-lookup"><span data-stu-id="9d01c-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[<span data-ttu-id="9d01c-135">macOS</span><span class="sxs-lookup"><span data-stu-id="9d01c-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="9d01c-136">Narzędzia do lokalnego</span><span class="sxs-lookup"><span data-stu-id="9d01c-136">Local tools</span></span>

<span data-ttu-id="9d01c-137">Lokalne narzędzia są w zakresie na drzewie podkatalogu dla poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9d01c-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="9d01c-138">Po uruchomieniu z podwyższonym poziomem uprawnień, lokalnego narzędzia udostępnianie środowisku użytkowników z ograniczeniami do środowiska z podniesionymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="9d01c-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="9d01c-139">W systemie Linux i macOS powoduje to pliki, ustawiania z dostępem tylko do użytkownika głównego.</span><span class="sxs-lookup"><span data-stu-id="9d01c-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="9d01c-140">Gdy użytkownik przejdzie do konta z ograniczeniami, użytkownik nie jest już można uzyskać dostęp lub zapisu do plików.</span><span class="sxs-lookup"><span data-stu-id="9d01c-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="9d01c-141">Dlatego zainstalowanie narzędzi, które wymagają podniesionych uprawnień jako narzędzia do lokalnego nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="9d01c-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="9d01c-142">Zamiast tego należy użyć `--tool-path` opcja i poprzedniej wskazówki dotyczące narzędzi globalnego.</span><span class="sxs-lookup"><span data-stu-id="9d01c-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="9d01c-143">Podniesienie uprawnień w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="9d01c-143">Elevation during development</span></span>

<span data-ttu-id="9d01c-144">Podczas tworzenia aplikacji może być konieczne podwyższonego poziomu dostępu, aby przetestować aplikację.</span><span class="sxs-lookup"><span data-stu-id="9d01c-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="9d01c-145">Ten scenariusz jest typowe w przypadku aplikacji IoT, np.</span><span class="sxs-lookup"><span data-stu-id="9d01c-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="9d01c-146">Firma Microsoft zaleca tworzenie aplikacji bez podniesienia uprawnień, a następnie uruchom go z podniesionymi.</span><span class="sxs-lookup"><span data-stu-id="9d01c-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="9d01c-147">Istnieje kilka wzorców w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9d01c-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="9d01c-148">Przy użyciu wygenerowany plik wykonywalny (zapewnia najlepszą wydajność uruchamiania):</span><span class="sxs-lookup"><span data-stu-id="9d01c-148">Using generated executable (it provides the best startup performance):</span></span>

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="9d01c-149">Za pomocą [dotnet, uruchom](dotnet-run.md) polecenia `—no-build` flagę, aby uniknąć generowania nowych danych binarnych:</span><span class="sxs-lookup"><span data-stu-id="9d01c-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="9d01c-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d01c-150">See also</span></span>

* [<span data-ttu-id="9d01c-151">Omówienie narzędzia globalnej platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="9d01c-151">.NET Core Global Tools overview</span></span>](global-tools.md)
