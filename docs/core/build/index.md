---
title: "Kompilacji platformy .NET Core ze źródła"
description: "Informacje o sposobie tworzenia .NET Core i .NET Core interfejsu wiersza polecenia z kodu źródłowego."
keywords: "Źródło .NET i .NET core, kompilacji"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.openlocfilehash: b2e62074992432dc5ee1360e17f87c782685dc35
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="b6a17-104">Kompilacji platformy .NET Core ze źródła</span><span class="sxs-lookup"><span data-stu-id="b6a17-104">Build .NET Core from source</span></span>

<span data-ttu-id="b6a17-105">Możliwość kompilacji platformy .NET Core z jego kod źródłowy jest ważne na wiele sposobów: ułatwi do portu .NET Core do nowych platform, umożliwia wkładów i poprawki produktu oraz umożliwia tworzenie niestandardowych wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b6a17-105">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="b6a17-106">Ten artykuł zawiera wskazówki dla deweloperów chcących do tworzenia i rozpowszechniania własnych wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6a17-106">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="b6a17-107">Tworzenie środowiska CLR ze źródła</span><span class="sxs-lookup"><span data-stu-id="b6a17-107">Build the CLR from source</span></span>

<span data-ttu-id="b6a17-108">Kod źródłowy środowisko CoreCLR .NET można znaleźć w [ `dotnet/coreclr` repozytorium w usłudze GitHub](https://github.com/dotnet/coreclr/).</span><span class="sxs-lookup"><span data-stu-id="b6a17-108">The source code for the .NET CoreCLR can be found in [the `dotnet/coreclr` repository on GitHub](https://github.com/dotnet/coreclr/).</span></span>

<span data-ttu-id="b6a17-109">Kompilacja zależy obecnie następujące wymagania wstępne:</span><span class="sxs-lookup"><span data-stu-id="b6a17-109">The build currently depends on the following prerequisites:</span></span>
* [<span data-ttu-id="b6a17-110">Git</span><span class="sxs-lookup"><span data-stu-id="b6a17-110">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="b6a17-111">CMake</span><span class="sxs-lookup"><span data-stu-id="b6a17-111">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="b6a17-112">Python</span><span class="sxs-lookup"><span data-stu-id="b6a17-112">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="b6a17-113">kompilator języka C++.</span><span class="sxs-lookup"><span data-stu-id="b6a17-113">a C++ compiler.</span></span>

<span data-ttu-id="b6a17-114">Po zainstalowaniu wymagań wstępnych są zainstalowane, CLR można tworzyć za pomocą skryptu kompilacji (`build.cmd` w systemie Windows, lub `build.sh` w systemie Linux i macOS) u dołu [repozytorium środowisko CoreCLR](https://github.com/dotnet/coreclr/).</span><span class="sxs-lookup"><span data-stu-id="b6a17-114">After you've installed these prerequisites are installed, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of [the CoreCLR repository](https://github.com/dotnet/coreclr/).</span></span>

<span data-ttu-id="b6a17-115">Instalowanie składników różnią się w zależności od systemu operacyjnego (systemu operacyjnego).</span><span class="sxs-lookup"><span data-stu-id="b6a17-115">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="b6a17-116">Zapoznaj się z instrukcjami kompilacji dla określonej system operacyjny:</span><span class="sxs-lookup"><span data-stu-id="b6a17-116">See the build instructions for your specific OS:</span></span>

 * [<span data-ttu-id="b6a17-117">Windows</span><span class="sxs-lookup"><span data-stu-id="b6a17-117">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [<span data-ttu-id="b6a17-118">Linux</span><span class="sxs-lookup"><span data-stu-id="b6a17-118">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [<span data-ttu-id="b6a17-119">System macOS</span><span class="sxs-lookup"><span data-stu-id="b6a17-119">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [<span data-ttu-id="b6a17-120">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="b6a17-120">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [<span data-ttu-id="b6a17-121">NetBSD</span><span class="sxs-lookup"><span data-stu-id="b6a17-121">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="b6a17-122">Nie ma żadnych budowania między przez system operacyjny (tylko dla ARM, który jest oparty na X64).</span><span class="sxs-lookup"><span data-stu-id="b6a17-122">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="b6a17-123">Muszą znajdować się w szczególności platformę do tworzenia tej platformy.</span><span class="sxs-lookup"><span data-stu-id="b6a17-123">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="b6a17-124">Kompilacja ma dwa główne `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="b6a17-124">The build has two main `buildTypes`:</span></span>

 * <span data-ttu-id="b6a17-125">Debugowania (domyślnie) — kompiluje obsługi z minimalnym optymalizacji i Sprawdzanie czasu wykonania dodatkowych (potwierdzeń).</span><span class="sxs-lookup"><span data-stu-id="b6a17-125">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="b6a17-126">Zmniejszenie poziomu optymalizacji i dodatkowe kontrole powolna wykonywania środowiska uruchomieniowego, ale są przydatne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b6a17-126">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="b6a17-127">To ustawienie zalecane dla środowisk projektowych i testowych.</span><span class="sxs-lookup"><span data-stu-id="b6a17-127">This is the recommended setting for development and testing environments.</span></span>
 * <span data-ttu-id="b6a17-128">Release — kompiluje środowiska uruchomieniowego z pełną optymalizacji i bez kontroli dodatkowe środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="b6a17-128">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="b6a17-129">Umożliwia to uzyskanie wydajności znacznie szybciej czas wykonywania, ale może zająć nieco dłużej i może być trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="b6a17-129">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="b6a17-130">Przekaż `release` do kompilacji skrypt, aby wybrać tę opcję, typ kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b6a17-130">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="b6a17-131">Ponadto domyślnie kompilacji nie tylko tworzy pliki wykonywalne środowiska uruchomieniowego, ale również tworzy wszystkie testy.</span><span class="sxs-lookup"><span data-stu-id="b6a17-131">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="b6a17-132">Istnieje kilka testy, biorąc znaczną ilość czasu, który nie jest konieczne, jeśli chcesz, aby wypróbować zmiany.</span><span class="sxs-lookup"><span data-stu-id="b6a17-132">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="b6a17-133">Kompilacje testów można pominąć, dodając `skiptests` argument skryptu kompilacji, takich jak w poniższym przykładzie (Zastąp `.\build` z `./build.sh` na komputerach Unix):</span><span class="sxs-lookup"><span data-stu-id="b6a17-133">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests 
```

<span data-ttu-id="b6a17-134">W poprzednim przykładzie pokazano sposób tworzenia `Debug` podtyp, którego rozwój sprawdzanie w trakcie wykonywania (potwierdzeń) włączone i wyłączone optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="b6a17-134">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="b6a17-135">Tworzenie wersji podtyp (pełnej szybkości), wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b6a17-135">To build the release (full speed) flavor, do the following:</span></span>

```bat 
    .\build release skiptests
```

<span data-ttu-id="b6a17-136">Można znaleźć opcje więcej kompilacji z kompilacją przy użyciu?</span><span class="sxs-lookup"><span data-stu-id="b6a17-136">You can find more build options with build by using the -?</span></span> <span data-ttu-id="b6a17-137">lub - help kwalifikatora.</span><span class="sxs-lookup"><span data-stu-id="b6a17-137">or -help qualifier.</span></span>   

### <a name="using-your-build"></a><span data-ttu-id="b6a17-138">Za pomocą kompilacji</span><span class="sxs-lookup"><span data-stu-id="b6a17-138">Using Your Build</span></span>

<span data-ttu-id="b6a17-139">Kompilacja umieszcza wszystkie jego pliki generowane w obszarze `bin` katalogu u podstawy repozytorium.</span><span class="sxs-lookup"><span data-stu-id="b6a17-139">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="b6a17-140">Brak *bin\Log* katalog zawierający pliki dziennika wygenerowanych podczas kompilacji (najbardziej przydatne w przypadku niepowodzenia kompilacji).</span><span class="sxs-lookup"><span data-stu-id="b6a17-140">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="b6a17-141">Rzeczywiste wyniki są umieszczane w *bin\Product\[platformy]. [ Architektura Procesora]. [typ kompilacji]*  katalogu, takie jak *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="b6a17-141">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="b6a17-142">Podczas gdy "raw" dane wyjściowe kompilacji czasami jest przydatne, zwykle interesuje Cię tylko pakietów NuGet, które są umieszczane w `.nuget\pkg` podkatalogu poprzedniej katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="b6a17-142">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="b6a17-143">Istnieją dwie podstawowe metody przy użyciu Twoje nowe środowisko uruchomieniowe:</span><span class="sxs-lookup"><span data-stu-id="b6a17-143">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="b6a17-144">**Umożliwia utworzenie aplikacji dotnet.exe i NuGet**.</span><span class="sxs-lookup"><span data-stu-id="b6a17-144">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="b6a17-145">Zobacz [przy użyciu Your kompilacji](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) instrukcje dotyczące tworzenia program, który używa Twoje nowe środowisko uruchomieniowe przy użyciu pakietów NuGet właśnie utworzony i "dotnet" interfejsu wiersza polecenia (CLI).</span><span class="sxs-lookup"><span data-stu-id="b6a17-145">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="b6a17-146">Ta technika jest najprawdopodobniej Twoje nowe środowisko uruchomieniowe to deweloperom runtime z systemem innym niż oczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="b6a17-146">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>    

 2. <span data-ttu-id="b6a17-147">**Użyj corerun.exe, aby uruchomić aplikację przy użyciu bibliotek DLL rozpakowanych**.</span><span class="sxs-lookup"><span data-stu-id="b6a17-147">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="b6a17-148">To repozytorium definiuje również proste hosta o nazwie corerun.exe, który nie przyjmuje żadnych zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="b6a17-148">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="b6a17-149">Należy określić hosta do uzyskania wymaganych bibliotek DLL rzeczywiście używane i musisz ręcznie zebrać je razem.</span><span class="sxs-lookup"><span data-stu-id="b6a17-149">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="b6a17-150">Ta technika jest używany przez wszystkie testy w [repozytorium środowisko CoreCLR](https://github.com/dotnet/coreclr)i ułatwia szybkie lokalnego "Edycja kompilacji debugowania" pętli takich jak wstępnego testowania jednostek.</span><span class="sxs-lookup"><span data-stu-id="b6a17-150">This technique is used by all the tests in [the CoreCLR repo](https://github.com/dotnet/coreclr), and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="b6a17-151">Zobacz [wykonywania aplikacji programu .NET Core z CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) szczegółowe informacje na temat używania tej metody.</span><span class="sxs-lookup"><span data-stu-id="b6a17-151">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="b6a17-152">Tworzenie interfejsu wiersza polecenia ze źródła</span><span class="sxs-lookup"><span data-stu-id="b6a17-152">Build the CLI from source</span></span>

<span data-ttu-id="b6a17-153">Kod źródłowy dla platformy .NET Core interfejsu wiersza polecenia można znaleźć w [ `dotnet/cli` repozytorium w usłudze GitHub](https://github.com/dotnet/cli/).</span><span class="sxs-lookup"><span data-stu-id="b6a17-153">The source code for the .NET Core CLI can be found in [the `dotnet/cli` repository on GitHub](https://github.com/dotnet/cli/).</span></span>

<span data-ttu-id="b6a17-154">Aby można było skompilować .NET Core interfejsu wiersza polecenia, należy spełnić następujące zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b6a17-154">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="b6a17-155">System Windows i Linux:</span><span class="sxs-lookup"><span data-stu-id="b6a17-155">Windows & Linux:</span></span>
    - <span data-ttu-id="b6a17-156">git w ŚCIEŻCE</span><span class="sxs-lookup"><span data-stu-id="b6a17-156">git on the PATH</span></span>
* <span data-ttu-id="b6a17-157">System macOS:</span><span class="sxs-lookup"><span data-stu-id="b6a17-157">macOS:</span></span>
    - <span data-ttu-id="b6a17-158">git w ŚCIEŻCE</span><span class="sxs-lookup"><span data-stu-id="b6a17-158">git on the PATH</span></span>
    - <span data-ttu-id="b6a17-159">Xcode</span><span class="sxs-lookup"><span data-stu-id="b6a17-159">Xcode</span></span>
    - <span data-ttu-id="b6a17-160">Openssl</span><span class="sxs-lookup"><span data-stu-id="b6a17-160">OpenSSL</span></span>

<span data-ttu-id="b6a17-161">Aby można było skompilować, uruchom `build.cmd` w systemie Windows, lub `build.sh` w systemie Linux i macOS z katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="b6a17-161">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="b6a17-162">Jeśli nie chcesz wykonywać testy, uruchom `build.cmd /t:Compile` lub `./build.sh /t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="b6a17-162">If you don't want to execute tests, run `build.cmd /t:Compile` or `./build.sh /t:Compile`.</span></span> <span data-ttu-id="b6a17-163">Aby utworzyć interfejsu wiersza polecenia w macOS Sierra, należy ustawić zmienną środowiskową DOTNET_RUNTIME_ID, uruchamiając `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="b6a17-163">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="b6a17-164">Za pomocą kompilacji</span><span class="sxs-lookup"><span data-stu-id="b6a17-164">Using your build</span></span>

<span data-ttu-id="b6a17-165">Użyj `dotnet` pliku wykonywalnego z *artefakty / {os}-{arch} / stage2* wypróbowanie nowo zbudowany interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b6a17-165">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="b6a17-166">Jeśli chcesz użyć kompilacji dane wyjściowe w przypadku wywoływania `dotnet` z bieżącą konsolę, można również dodać *artefakty / {os}-{arch} / stage2* do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b6a17-166">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6a17-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6a17-167">See also</span></span>

* [<span data-ttu-id="b6a17-168">.NET core środowisko uruchomieniowe języka wspólnego (środowisko CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="b6a17-168">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="b6a17-169">Przewodnik dewelopera po .NET core interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b6a17-169">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="b6a17-170">OPAKOWYWANIE dystrybucji .NET core</span><span class="sxs-lookup"><span data-stu-id="b6a17-170">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
