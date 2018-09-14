---
title: Kompilacja platformy .NET Core ze źródła
description: Dowiedz się, jak tworzyć oprogramowanie .NET Core i .NET Core interfejsu wiersza polecenia z kodu źródłowego.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 2623c5d21121b71960d174301c35bdd0d7f8558a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618522"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="e8655-103">Kompilacja platformy .NET Core ze źródła</span><span class="sxs-lookup"><span data-stu-id="e8655-103">Build .NET Core from source</span></span>

<span data-ttu-id="e8655-104">Kompilacja platformy .NET Core z jego kod źródłowy jest ważne na wiele sposobów: ułatwia port platformy .NET Core do nowych platform, umożliwia wkładu i poprawek dotyczących produktu, i umożliwia tworzenie niestandardowych wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e8655-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="e8655-105">Ten artykuł zawiera wskazówki dla deweloperów, którzy chcą dystrybucję własnych wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8655-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="e8655-106">Tworzenie środowiska CLR ze źródła</span><span class="sxs-lookup"><span data-stu-id="e8655-106">Build the CLR from source</span></span>

<span data-ttu-id="e8655-107">Kod źródłowy w programie CoreCLR .NET można znaleźć w [dotnet/coreclr](https://github.com/dotnet/coreclr/) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="e8655-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="e8655-108">Kompilacja obecnie zależy od następujących wymagań wstępnych:</span><span class="sxs-lookup"><span data-stu-id="e8655-108">The build currently depends on the following prerequisites:</span></span>

* [<span data-ttu-id="e8655-109">Git</span><span class="sxs-lookup"><span data-stu-id="e8655-109">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="e8655-110">Narzędzia CMake</span><span class="sxs-lookup"><span data-stu-id="e8655-110">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="e8655-111">Python</span><span class="sxs-lookup"><span data-stu-id="e8655-111">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="e8655-112">kompilator języka C++.</span><span class="sxs-lookup"><span data-stu-id="e8655-112">a C++ compiler.</span></span>

<span data-ttu-id="e8655-113">Po zainstalowaniu wymagań wstępnych, można tworzyć środowiska CLR, wywołując skrypt kompilacji (`build.cmd` na Windows, lub `build.sh` w systemie Linux i macOS) u dołu [dotnet/coreclr](https://github.com/dotnet/coreclr/) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="e8655-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="e8655-114">Instalowanie składników różnią się zależnie od systemu operacyjnego (OS).</span><span class="sxs-lookup"><span data-stu-id="e8655-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="e8655-115">Zapoznaj się z instrukcjami kompilacji dla swojego określonego systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="e8655-115">See the build instructions for your specific OS:</span></span>

* [<span data-ttu-id="e8655-116">Windows</span><span class="sxs-lookup"><span data-stu-id="e8655-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [<span data-ttu-id="e8655-117">Linux</span><span class="sxs-lookup"><span data-stu-id="e8655-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [<span data-ttu-id="e8655-118">macOS</span><span class="sxs-lookup"><span data-stu-id="e8655-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [<span data-ttu-id="e8655-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="e8655-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [<span data-ttu-id="e8655-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="e8655-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="e8655-121">Nie ma żadnych tworzenie wielu różnych systemów operacyjnych (tylko dla ARM, która jest oparta na X64).</span><span class="sxs-lookup"><span data-stu-id="e8655-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="e8655-122">Muszą znajdować się na konkretnej platformie do tworzenia tej platformy.</span><span class="sxs-lookup"><span data-stu-id="e8655-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="e8655-123">Kompilacja ma dwa główne `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="e8655-123">The build has two main `buildTypes`:</span></span>

* <span data-ttu-id="e8655-124">Debugowanie (ustawienie domyślne) — kompiluje środowiska uruchomieniowego przy użyciu minimalnego optymalizacje i kontrole dodatkowe środowiska uruchomieniowego (potwierdza).</span><span class="sxs-lookup"><span data-stu-id="e8655-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="e8655-125">Takie zmniejszenie poziom optymalizacji i dodatkowe kontrole spowolnić wykonywanie środowiska uruchomieniowego, ale są przydatne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="e8655-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="e8655-126">To ustawienie zalecane dla środowisk programowania i testowania.</span><span class="sxs-lookup"><span data-stu-id="e8655-126">This is the recommended setting for development and testing environments.</span></span>
* <span data-ttu-id="e8655-127">Release — kompiluje środowiska uruchomieniowego za pomocą pełnego optymalizacje i bez testy dodatkowe środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e8655-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="e8655-128">Umożliwia to uzyskanie wydajności znacznie szybciej czas wykonywania, ale może trwać nieco dłużej, tworzyć i może być trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="e8655-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="e8655-129">Przekaż `release` do kompilacji skrypt, aby wybrać tę opcję, typ kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e8655-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="e8655-130">Ponadto domyślnie kompilacji tworzy nie tylko pliki wykonywalne środowiska uruchomieniowego, ale sprzyja wytwarzaniu wszystkie testy.</span><span class="sxs-lookup"><span data-stu-id="e8655-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="e8655-131">Istnieje kilka testów, biorąc znaczną ilość czasu, który nie jest konieczne, jeśli chcesz, aby eksperymentować z zmiany.</span><span class="sxs-lookup"><span data-stu-id="e8655-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="e8655-132">Możesz pominąć kompilacje testów przez dodanie `skiptests` argument skrypt kompilacji, jak pokazano w poniższym przykładzie (Zastąp `.\build` z `./build.sh` na komputerach z systemem Unix):</span><span class="sxs-lookup"><span data-stu-id="e8655-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="e8655-133">W poprzednim przykładzie pokazano sposób tworzenia `Debug` smak ma sprawdzania w trakcie rozwoju (potwierdza) włączone i wyłączone optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="e8655-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="e8655-134">Aby skompilować wersję (z pełną prędkością) wersji, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e8655-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="e8655-135">Można znaleźć więcej kompilacji opcje kompilacji przy użyciu?</span><span class="sxs-lookup"><span data-stu-id="e8655-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="e8655-136">lub - help kwalifikator.</span><span class="sxs-lookup"><span data-stu-id="e8655-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="e8655-137">Za pomocą kompilacji</span><span class="sxs-lookup"><span data-stu-id="e8655-137">Using Your Build</span></span>

<span data-ttu-id="e8655-138">Kompilacja umieszcza wszystkich wygenerowanych plików w obszarze `bin` katalogu z podstawową repozytorium.</span><span class="sxs-lookup"><span data-stu-id="e8655-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="e8655-139">Brak *bin\Log* katalog zawierający pliki dziennika generowane podczas kompilacji (najbardziej przydatne w przypadku niepowodzenia kompilacji).</span><span class="sxs-lookup"><span data-stu-id="e8655-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="e8655-140">Rzeczywiste wyniki są umieszczane w *bin\Product\[platformy]. [ Architektura Procesora]. [typ kompilacji]*  katalogu, takie jak *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="e8655-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="e8655-141">Chociaż czasami przydaje "raw" dane wyjściowe kompilacji, zwykle interesuje Cię tylko pakiety NuGet, które są umieszczane w `.nuget\pkg` podkatalogu poprzedniego katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="e8655-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="e8655-142">Istnieją dwie podstawowe metody za pomocą Twojego nowego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="e8655-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="e8655-143">**Tworzenie aplikacji za pomocą dotnet.exe i NuGet**.</span><span class="sxs-lookup"><span data-stu-id="e8655-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="e8655-144">Zobacz [przy użyciu kompilacji](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) instrukcje dotyczące tworzenia program, który używa Twojego nowego środowiska uruchomieniowego przy użyciu pakietu NuGet pakietów właśnie utworzony i interfejsu wiersza polecenia "dotnet" (CLI).</span><span class="sxs-lookup"><span data-stu-id="e8655-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="e8655-145">Ta technika jest oczekiwany sposób deweloperzy innych środowiska uruchomieniowego są mogących korzystać z nowego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e8655-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="e8655-146">**Użyj corerun.exe, aby uruchomić aplikację przy użyciu biblioteki DLL rozpakowanych**.</span><span class="sxs-lookup"><span data-stu-id="e8655-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="e8655-147">To repozytorium definiuje również proste hosta o nazwie corerun.exe który nie ma żadnych zależności dla narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="e8655-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="e8655-148">Należy przekazać do uzyskania wymaganych bibliotek DLL faktycznie używać hosta i musisz ręcznie zebrać je ze sobą.</span><span class="sxs-lookup"><span data-stu-id="e8655-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="e8655-149">Ta technika jest używany przez wszystkie testy w [dotnet/coreclr](https://github.com/dotnet/coreclr) repozytorium i jest przydatne w przypadku pętli szybkiego lokalnego "Edycja kompilacji debug" takich jak testy jednostkowe wstępnego.</span><span class="sxs-lookup"><span data-stu-id="e8655-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="e8655-150">Zobacz [wykonywania aplikacji programu .NET Core za pomocą CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) Aby uzyskać szczegółowe informacje na temat korzystania z tej techniki.</span><span class="sxs-lookup"><span data-stu-id="e8655-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="e8655-151">Tworzenie interfejsu wiersza polecenia ze źródła</span><span class="sxs-lookup"><span data-stu-id="e8655-151">Build the CLI from source</span></span>

<span data-ttu-id="e8655-152">Kod źródłowy dla platformy .NET Core interfejsu wiersza polecenia można znaleźć w [interfejsu wiersza poleceniadotnet/](https://github.com/dotnet/cli/) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="e8655-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="e8655-153">Aby można było utworzyć interfejsu wiersza polecenia platformy .NET Core, potrzebne będą zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e8655-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="e8655-154">Windows i Linux:</span><span class="sxs-lookup"><span data-stu-id="e8655-154">Windows & Linux:</span></span>
  * <span data-ttu-id="e8655-155">git na ŚCIEŻCE</span><span class="sxs-lookup"><span data-stu-id="e8655-155">git on the PATH</span></span>
* <span data-ttu-id="e8655-156">System macOS:</span><span class="sxs-lookup"><span data-stu-id="e8655-156">macOS:</span></span>
  * <span data-ttu-id="e8655-157">git na ŚCIEŻCE</span><span class="sxs-lookup"><span data-stu-id="e8655-157">git on the PATH</span></span>
  * <span data-ttu-id="e8655-158">Środowisko Xcode</span><span class="sxs-lookup"><span data-stu-id="e8655-158">Xcode</span></span>
  * <span data-ttu-id="e8655-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="e8655-159">OpenSSL</span></span>

<span data-ttu-id="e8655-160">Aby skompilować, uruchom `build.cmd` na Windows, lub `build.sh` w systemie Linux i macOS z katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="e8655-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="e8655-161">Jeśli nie chcesz wykonać testy, należy uruchomić `build.cmd /t:Compile` lub `./build.sh /t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="e8655-161">If you don't want to execute tests, run `build.cmd /t:Compile` or `./build.sh /t:Compile`.</span></span> <span data-ttu-id="e8655-162">Aby utworzyć interfejs wiersza polecenia w systemie macOS Sierra, musisz ustawić zmienną środowiskową DOTNET_RUNTIME_ID, uruchamiając `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="e8655-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="e8655-163">Za pomocą kompilacji</span><span class="sxs-lookup"><span data-stu-id="e8655-163">Using your build</span></span>

<span data-ttu-id="e8655-164">Użyj `dotnet` z *artefaktów / {os}-{arch} / stage2* do wypróbowania nowo zbudowany interfejs wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e8655-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="e8655-165">Jeśli chcesz używać dane wyjściowe podczas wywoływania kompilacji `dotnet` z bieżącą konsolę, można również dodać *artefaktów / {os}-{arch} / stage2* do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="e8655-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8655-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8655-166">See also</span></span>

* [<span data-ttu-id="e8655-167">.NET core środowiska uruchomieniowego języka wspólnego (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="e8655-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="e8655-168">Przewodnik dewelopera programu .NET core interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="e8655-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="e8655-169">Tworzenie pakietów dystrybucji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="e8655-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
