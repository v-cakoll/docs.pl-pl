---
title: Kompilacji platformy .NET Core ze źródła
description: Informacje o sposobie tworzenia .NET Core i .NET Core interfejsu wiersza polecenia z kodu źródłowego.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 55a35223a4bc11156e056cceb7f86365c4906222
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216029"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="b7756-103">Kompilacji platformy .NET Core ze źródła</span><span class="sxs-lookup"><span data-stu-id="b7756-103">Build .NET Core from source</span></span>

<span data-ttu-id="b7756-104">Możliwość kompilacji platformy .NET Core z jego kod źródłowy jest ważne na wiele sposobów: ułatwi do portu .NET Core do nowych platform, umożliwia wkładów i poprawki produktu oraz umożliwia tworzenie niestandardowych wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b7756-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="b7756-105">Ten artykuł zawiera wskazówki dla deweloperów chcących do tworzenia i rozpowszechniania własnych wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7756-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="b7756-106">Tworzenie środowiska CLR ze źródła</span><span class="sxs-lookup"><span data-stu-id="b7756-106">Build the CLR from source</span></span>

<span data-ttu-id="b7756-107">Kod źródłowy środowisko CoreCLR .NET można znaleźć w [dotnet/środowisko coreclr](https://github.com/dotnet/coreclr/) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="b7756-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="b7756-108">Kompilacja zależy obecnie następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="b7756-108">The build currently depends on the following prerequisites:</span></span>
* [<span data-ttu-id="b7756-109">Git</span><span class="sxs-lookup"><span data-stu-id="b7756-109">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="b7756-110">CMake</span><span class="sxs-lookup"><span data-stu-id="b7756-110">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="b7756-111">Python</span><span class="sxs-lookup"><span data-stu-id="b7756-111">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="b7756-112">kompilator języka C++.</span><span class="sxs-lookup"><span data-stu-id="b7756-112">a C++ compiler.</span></span>

<span data-ttu-id="b7756-113">Po zainstalowaniu wymagań wstępnych są zainstalowane, CLR można tworzyć za pomocą skryptu kompilacji (`build.cmd` w systemie Windows, lub `build.sh` w systemie Linux i macOS) u dołu [dotnet/środowisko coreclr](https://github.com/dotnet/coreclr/) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="b7756-113">After you've installed these prerequisites are installed, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="b7756-114">Instalowanie składników różnią się w zależności od systemu operacyjnego (systemu operacyjnego).</span><span class="sxs-lookup"><span data-stu-id="b7756-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="b7756-115">Zapoznaj się z instrukcjami kompilacji dla określonej system operacyjny:</span><span class="sxs-lookup"><span data-stu-id="b7756-115">See the build instructions for your specific OS:</span></span>

 * [<span data-ttu-id="b7756-116">Windows</span><span class="sxs-lookup"><span data-stu-id="b7756-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [<span data-ttu-id="b7756-117">Linux</span><span class="sxs-lookup"><span data-stu-id="b7756-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [<span data-ttu-id="b7756-118">macOS</span><span class="sxs-lookup"><span data-stu-id="b7756-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [<span data-ttu-id="b7756-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="b7756-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [<span data-ttu-id="b7756-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="b7756-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="b7756-121">Nie ma żadnych budowania między przez system operacyjny (tylko dla ARM, który jest oparty na X64).</span><span class="sxs-lookup"><span data-stu-id="b7756-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="b7756-122">Muszą znajdować się w szczególności platformę do tworzenia tej platformy.</span><span class="sxs-lookup"><span data-stu-id="b7756-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="b7756-123">Kompilacja ma dwa główne `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="b7756-123">The build has two main `buildTypes`:</span></span>

 * <span data-ttu-id="b7756-124">Debugowania (domyślnie) — kompiluje obsługi z minimalnym optymalizacji i Sprawdzanie czasu wykonania dodatkowych (potwierdzeń).</span><span class="sxs-lookup"><span data-stu-id="b7756-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="b7756-125">Zmniejszenie poziomu optymalizacji i dodatkowe kontrole powolna wykonywania środowiska uruchomieniowego, ale są przydatne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b7756-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="b7756-126">To ustawienie zalecane dla środowisk projektowych i testowych.</span><span class="sxs-lookup"><span data-stu-id="b7756-126">This is the recommended setting for development and testing environments.</span></span>
 * <span data-ttu-id="b7756-127">Release — kompiluje środowiska uruchomieniowego z pełną optymalizacji i bez kontroli dodatkowe środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="b7756-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="b7756-128">Umożliwia to uzyskanie wydajności znacznie szybciej czas wykonywania, ale może zająć nieco dłużej i może być trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b7756-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="b7756-129">Przekaż `release` do kompilacji skrypt, aby wybrać tę opcję, typ kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b7756-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="b7756-130">Ponadto domyślnie kompilacji nie tylko tworzy pliki wykonywalne środowiska uruchomieniowego, ale również tworzy wszystkie testy.</span><span class="sxs-lookup"><span data-stu-id="b7756-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="b7756-131">Istnieje kilka testy, biorąc znaczną ilość czasu, który nie jest konieczne, jeśli chcesz, aby wypróbować zmiany.</span><span class="sxs-lookup"><span data-stu-id="b7756-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="b7756-132">Kompilacje testów można pominąć, dodając `skiptests` argument skryptu kompilacji, takich jak w poniższym przykładzie (Zastąp `.\build` z `./build.sh` na komputerach Unix):</span><span class="sxs-lookup"><span data-stu-id="b7756-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests 
```

<span data-ttu-id="b7756-133">W poprzednim przykładzie pokazano sposób tworzenia `Debug` podtyp, którego rozwój sprawdzanie w trakcie wykonywania (potwierdzeń) włączone i wyłączone optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="b7756-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="b7756-134">Tworzenie wersji podtyp (pełnej szybkości), wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b7756-134">To build the release (full speed) flavor, do the following:</span></span>

```bat 
    .\build release skiptests
```

<span data-ttu-id="b7756-135">Można znaleźć opcje więcej kompilacji z kompilacją przy użyciu?</span><span class="sxs-lookup"><span data-stu-id="b7756-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="b7756-136">lub - help kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="b7756-136">or -help qualifier.</span></span>   

### <a name="using-your-build"></a><span data-ttu-id="b7756-137">Za pomocą kompilacji</span><span class="sxs-lookup"><span data-stu-id="b7756-137">Using Your Build</span></span>

<span data-ttu-id="b7756-138">Kompilacja umieszcza wszystkie jego pliki generowane w obszarze `bin` katalogu u podstawy repozytorium.</span><span class="sxs-lookup"><span data-stu-id="b7756-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="b7756-139">Brak *bin\Log* katalog zawierający pliki dziennika wygenerowanych podczas kompilacji (najbardziej przydatne w przypadku niepowodzenia kompilacji).</span><span class="sxs-lookup"><span data-stu-id="b7756-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="b7756-140">Rzeczywiste wyniki są umieszczane w *bin\Product\[platformy]. [ Architektura Procesora]. [typ kompilacji]*  katalogu, takie jak *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="b7756-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="b7756-141">Podczas gdy "raw" dane wyjściowe kompilacji czasami jest przydatne, zwykle interesuje Cię tylko pakietów NuGet, które są umieszczane w `.nuget\pkg` podkatalogu poprzedniej katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="b7756-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="b7756-142">Istnieją dwie podstawowe metody przy użyciu Twoje nowe środowisko uruchomieniowe:</span><span class="sxs-lookup"><span data-stu-id="b7756-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="b7756-143">**Umożliwia utworzenie aplikacji dotnet.exe i NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b7756-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="b7756-144">Zobacz [przy użyciu Your kompilacji](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) instrukcje dotyczące tworzenia program, który używa Twoje nowe środowisko uruchomieniowe przy użyciu pakietów NuGet właśnie utworzony i "dotnet" interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="b7756-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="b7756-145">Ta technika jest najprawdopodobniej Twoje nowe środowisko uruchomieniowe to deweloperom runtime z systemem innym niż oczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="b7756-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>    

 2. <span data-ttu-id="b7756-146">**Użyj corerun.exe, aby uruchomić aplikację przy użyciu bibliotek DLL rozpakowanych**.</span><span class="sxs-lookup"><span data-stu-id="b7756-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="b7756-147">To repozytorium definiuje również proste hosta o nazwie corerun.exe, który nie przyjmuje żadnych zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="b7756-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="b7756-148">Należy określić hosta do uzyskania wymaganych bibliotek DLL rzeczywiście używane i musisz ręcznie zebrać je razem.</span><span class="sxs-lookup"><span data-stu-id="b7756-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="b7756-149">Ta technika jest używany przez wszystkie testy w [dotnet/środowisko coreclr](https://github.com/dotnet/coreclr) repozytorium i ułatwia szybkie lokalnego "Edycja kompilacji debugowania" pętli takich jak wstępnego testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="b7756-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="b7756-150">Zobacz [wykonywania aplikacji programu .NET Core z CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) szczegółowe informacje na temat używania tej metody.</span><span class="sxs-lookup"><span data-stu-id="b7756-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="b7756-151">Tworzenie interfejsu wiersza polecenia ze źródła</span><span class="sxs-lookup"><span data-stu-id="b7756-151">Build the CLI from source</span></span>

<span data-ttu-id="b7756-152">Kod źródłowy dla platformy .NET Core interfejsu wiersza polecenia można znaleźć w [dotnet/cli](https://github.com/dotnet/cli/) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="b7756-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="b7756-153">Aby można było skompilować .NET Core interfejsu wiersza polecenia, należy spełnić następujące zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b7756-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="b7756-154">System Windows i Linux:</span><span class="sxs-lookup"><span data-stu-id="b7756-154">Windows & Linux:</span></span>
    - <span data-ttu-id="b7756-155">git w ŚCIEŻCE</span><span class="sxs-lookup"><span data-stu-id="b7756-155">git on the PATH</span></span>
* <span data-ttu-id="b7756-156">System macOS:</span><span class="sxs-lookup"><span data-stu-id="b7756-156">macOS:</span></span>
    - <span data-ttu-id="b7756-157">git w ŚCIEŻCE</span><span class="sxs-lookup"><span data-stu-id="b7756-157">git on the PATH</span></span>
    - <span data-ttu-id="b7756-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="b7756-158">Xcode</span></span>
    - <span data-ttu-id="b7756-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="b7756-159">OpenSSL</span></span>

<span data-ttu-id="b7756-160">Aby można było skompilować, uruchom `build.cmd` w systemie Windows, lub `build.sh` w systemie Linux i macOS z katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="b7756-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="b7756-161">Jeśli nie chcesz wykonywać testy, uruchom `build.cmd /t:Compile` lub `./build.sh /t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="b7756-161">If you don't want to execute tests, run `build.cmd /t:Compile` or `./build.sh /t:Compile`.</span></span> <span data-ttu-id="b7756-162">Aby utworzyć interfejsu wiersza polecenia w macOS Sierra, należy ustawić zmienną środowiskową DOTNET_RUNTIME_ID, uruchamiając `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="b7756-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="b7756-163">Za pomocą kompilacji</span><span class="sxs-lookup"><span data-stu-id="b7756-163">Using your build</span></span>

<span data-ttu-id="b7756-164">Użyj `dotnet` pliku wykonywalnego z *artefakty / {os}-{arch} / stage2* wypróbowanie nowo zbudowany interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b7756-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="b7756-165">Jeśli chcesz użyć kompilacji dane wyjściowe w przypadku wywoływania `dotnet` z bieżącą konsolę, można również dodać *artefakty / {os}-{arch} / stage2* do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b7756-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7756-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7756-166">See also</span></span>

* [<span data-ttu-id="b7756-167">.NET core środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="b7756-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="b7756-168">Przewodnik dewelopera po .NET core interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b7756-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="b7756-169">Tworzenie pakietów dystrybucji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7756-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
