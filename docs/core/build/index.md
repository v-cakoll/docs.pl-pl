---
title: Kompilacja platformy .NET Core ze źródła
description: Dowiedz się, jak utworzyć platformę .NET Core i interfejs wiersza polecenia platformy .NET Core z kodu źródłowego.
author: bleroy
ms.date: 06/28/2017
ms.openlocfilehash: fe5431667d861d830c2ec56252e6e3e2ca08a866
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740919"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="07f33-103">Kompilacja platformy .NET Core ze źródła</span><span class="sxs-lookup"><span data-stu-id="07f33-103">Build .NET Core from source</span></span>

<span data-ttu-id="07f33-104">Możliwość tworzenia programu .NET Core z jego kodu źródłowego jest ważna na wiele sposobów: ułatwia to przenoszenie platformy .NET Core na nowe platformy, umożliwia wprowadzanie wkładów i poprawek do produktu, a także umożliwia tworzenie niestandardowych wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="07f33-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="07f33-105">Ten artykuł zawiera wskazówki dla deweloperów, którzy chcą kompilować i rozpowszechniać własne wersje platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07f33-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="07f33-106">Kompiluj środowisko CLR ze źródła</span><span class="sxs-lookup"><span data-stu-id="07f33-106">Build the CLR from source</span></span>

<span data-ttu-id="07f33-107">Kod źródłowy dla programu .NET CoreCLR można znaleźć w repozytorium [dotnet/Runtime](https://github.com/dotnet/runtime/) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="07f33-107">The source code for the .NET CoreCLR can be found in the [dotnet/runtime](https://github.com/dotnet/runtime/) repository on GitHub.</span></span>

<span data-ttu-id="07f33-108">Kompilacja zależy obecnie od następujących wymagań wstępnych:</span><span class="sxs-lookup"><span data-stu-id="07f33-108">The build currently depends on the following prerequisites:</span></span>

- [<span data-ttu-id="07f33-109">Git</span><span class="sxs-lookup"><span data-stu-id="07f33-109">Git</span></span>](https://git-scm.com/)
- [<span data-ttu-id="07f33-110">CMake</span><span class="sxs-lookup"><span data-stu-id="07f33-110">CMake</span></span>](https://cmake.org/)
- [<span data-ttu-id="07f33-111">Python</span><span class="sxs-lookup"><span data-stu-id="07f33-111">Python</span></span>](https://www.python.org/)
- <span data-ttu-id="07f33-112">C++ kompilator.</span><span class="sxs-lookup"><span data-stu-id="07f33-112">a C++ compiler.</span></span>

<span data-ttu-id="07f33-113">Po zainstalowaniu tych wymagań wstępnych można skompilować środowisko CLR, wywołując skrypt kompilacji (`build.cmd` w systemie Windows lub `build.sh` w systemie Linux i macOS) na podstawie bazy repozytorium [dotnet/Runtime](https://github.com/dotnet/runtime/) .</span><span class="sxs-lookup"><span data-stu-id="07f33-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/runtime](https://github.com/dotnet/runtime/) repository.</span></span>

<span data-ttu-id="07f33-114">Instalowanie składników różni się w zależności od systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="07f33-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="07f33-115">Zobacz instrukcje dotyczące kompilacji dla konkretnego systemu operacyjnego:</span><span class="sxs-lookup"><span data-stu-id="07f33-115">See the build instructions for your specific OS:</span></span>

- [<span data-ttu-id="07f33-116">Windows</span><span class="sxs-lookup"><span data-stu-id="07f33-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [<span data-ttu-id="07f33-117">Linux</span><span class="sxs-lookup"><span data-stu-id="07f33-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [<span data-ttu-id="07f33-118">macOS</span><span class="sxs-lookup"><span data-stu-id="07f33-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [<span data-ttu-id="07f33-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="07f33-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [<span data-ttu-id="07f33-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="07f33-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="07f33-121">W systemie operacyjnym nie ma między różnymi kompilacjami (tylko w przypadku platformy ARM, która jest oparta na architekturze x64).</span><span class="sxs-lookup"><span data-stu-id="07f33-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="07f33-122">Musisz mieć na konkretną platformę, aby skompilować tę platformę.</span><span class="sxs-lookup"><span data-stu-id="07f33-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="07f33-123">Kompilacja ma dwa główne `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="07f33-123">The build has two main `buildTypes`:</span></span>

- <span data-ttu-id="07f33-124">Debuguj (domyślnie) — kompiluje środowisko uruchomieniowe z minimalnymi optymalizacjami i dodatkowymi sprawdzeniami w czasie wykonywania (potwierdzenia).</span><span class="sxs-lookup"><span data-stu-id="07f33-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="07f33-125">To zmniejszenie poziomu optymalizacji i dodatkowych sprawdzeń w czasie wykonywania, ale są cenne dla debugowania.</span><span class="sxs-lookup"><span data-stu-id="07f33-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="07f33-126">Jest to zalecane ustawienie dla środowisk deweloperskich i testowych.</span><span class="sxs-lookup"><span data-stu-id="07f33-126">This is the recommended setting for development and testing environments.</span></span>
- <span data-ttu-id="07f33-127">Wydanie — kompiluje środowisko uruchomieniowe z pełną optymalizacją i bez dodatkowych kontroli środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="07f33-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="07f33-128">Spowoduje to przyspieszenie wydajności w czasie wykonywania, ale może to trochę potrwać i może być trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="07f33-128">This will yield much faster run-time performance, but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="07f33-129">Przekaż `release` do skryptu kompilacji, aby wybrać ten typ kompilacji.</span><span class="sxs-lookup"><span data-stu-id="07f33-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="07f33-130">Ponadto domyślnie kompilacja nie tylko tworzy pliki wykonywalne środowiska uruchomieniowego, ale również kompiluje wszystkie testy.</span><span class="sxs-lookup"><span data-stu-id="07f33-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="07f33-131">Istnieje kilka testów, które nie są potrzebne, jeśli chcesz tylko eksperymentować ze zmianami.</span><span class="sxs-lookup"><span data-stu-id="07f33-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="07f33-132">Możesz pominąć kompilacje testów, dodając argument `skiptests` do skryptu kompilacji, jak w poniższym przykładzie (Zastąp `.\build` `./build.sh` na komputerach z systemem UNIX):</span><span class="sxs-lookup"><span data-stu-id="07f33-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="07f33-133">W poprzednim przykładzie pokazano, jak utworzyć `Debug` wersja, która ma włączone sprawdzanie czasu projektowania (potwierdzenia), a optymalizacja została wyłączona.</span><span class="sxs-lookup"><span data-stu-id="07f33-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="07f33-134">Aby skompilować wersję wydania (Pełna szybkość), wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="07f33-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="07f33-135">Możesz znaleźć więcej opcji kompilacji z kompilacją, korzystając z-?</span><span class="sxs-lookup"><span data-stu-id="07f33-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="07f33-136">lub kwalifikator pomocy.</span><span class="sxs-lookup"><span data-stu-id="07f33-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="07f33-137">Korzystanie z kompilacji</span><span class="sxs-lookup"><span data-stu-id="07f33-137">Using Your Build</span></span>

<span data-ttu-id="07f33-138">Kompilacja umieszcza wszystkie wygenerowane pliki w katalogu `bin` w bazie repozytorium.</span><span class="sxs-lookup"><span data-stu-id="07f33-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="07f33-139">Istnieje katalog *bin\Log* , który zawiera pliki dziennika wygenerowane podczas kompilacji (najbardziej przydatne, gdy kompilacja zakończy się niepowodzeniem).</span><span class="sxs-lookup"><span data-stu-id="07f33-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="07f33-140">Rzeczywista wartość wyjściowa jest umieszczana w *bin\Product\[platformę]. [Architektura procesora]. [typ kompilacji]* Katalog, taki jak *bin\product\ Windows_NT. x64. Release*.</span><span class="sxs-lookup"><span data-stu-id="07f33-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="07f33-141">Chociaż nieprzetworzone dane wyjściowe kompilacji są czasami przydatne, zazwyczaj interesuje się tylko pakiety NuGet, które są umieszczane w podkatalogu `.nuget\pkg` poprzedniego katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="07f33-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="07f33-142">Istnieją dwie podstawowe techniki korzystania z nowego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="07f33-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="07f33-143">**Użyj programu dotnet. exe i NuGet, aby utworzyć aplikację**.</span><span class="sxs-lookup"><span data-stu-id="07f33-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="07f33-144">Zapoznaj się z instrukcjami dotyczącymi tworzenia [programu korzystającego](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) z nowego środowiska uruchomieniowego przy użyciu utworzonej przez siebie pakietów NuGet i interfejsu wiersza polecenia "dotnet" (CLI).</span><span class="sxs-lookup"><span data-stu-id="07f33-144">See [Using Your Build](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="07f33-145">Ta technika jest oczekiwanym sposobem, w jaki deweloperzy niebędący środowiskiem uruchomieniowym mogą korzystać z nowego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="07f33-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="07f33-146">**Użyj narzędzia do ponownego uruchomienia. exe, aby uruchomić aplikację przy użyciu nieopakowanych bibliotek DLL**.</span><span class="sxs-lookup"><span data-stu-id="07f33-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="07f33-147">To repozytorium definiuje również prostego hosta o nazwie współdziałanie. exe, który nie przyjmuje żadnej zależności od NuGet.</span><span class="sxs-lookup"><span data-stu-id="07f33-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="07f33-148">Musisz poinformować hosta, na którym mają zostać pobrane wymagane biblioteki DLL, i musisz ręcznie zebrać je razem.</span><span class="sxs-lookup"><span data-stu-id="07f33-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="07f33-149">Ta technika jest używana przez wszystkie testy w repozytorium [dotnet/Runtime](https://github.com/dotnet/runtime) i jest przydatna w przypadku szybkiej lokalnej pętli "Edit-Compile-debug", takiej jak wstępne testy jednostkowe.</span><span class="sxs-lookup"><span data-stu-id="07f33-149">This technique is used by all the tests in the [dotnet/runtime](https://github.com/dotnet/runtime) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="07f33-150">Aby uzyskać szczegółowe informacje na temat korzystania z tej techniki, zobacz [wykonywanie aplikacji platformy .NET Core za pomocą narzędzia do ponownego uruchomienia. exe](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md) .</span><span class="sxs-lookup"><span data-stu-id="07f33-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="07f33-151">Kompilowanie interfejsu wiersza polecenia ze źródła</span><span class="sxs-lookup"><span data-stu-id="07f33-151">Build the CLI from source</span></span>

<span data-ttu-id="07f33-152">Kod źródłowy interfejs wiersza polecenia platformy .NET Core można znaleźć w repozytorium [dotnet/CLI](https://github.com/dotnet/cli/) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="07f33-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="07f33-153">Aby można było skompilować interfejs wiersza polecenia platformy .NET Core, potrzebne są następujące elementy zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="07f33-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

- <span data-ttu-id="07f33-154">System Windows & Linux:</span><span class="sxs-lookup"><span data-stu-id="07f33-154">Windows & Linux:</span></span>
  - <span data-ttu-id="07f33-155">Git na ścieżce</span><span class="sxs-lookup"><span data-stu-id="07f33-155">git on the PATH</span></span>
- <span data-ttu-id="07f33-156">macOS:</span><span class="sxs-lookup"><span data-stu-id="07f33-156">macOS:</span></span>
  - <span data-ttu-id="07f33-157">Git na ścieżce</span><span class="sxs-lookup"><span data-stu-id="07f33-157">git on the PATH</span></span>
  - <span data-ttu-id="07f33-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="07f33-158">Xcode</span></span>
  - <span data-ttu-id="07f33-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="07f33-159">OpenSSL</span></span>

<span data-ttu-id="07f33-160">W celu kompilowania, uruchamiania `build.cmd` w systemie Windows lub `build.sh` w systemie Linux i macOS z poziomu katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="07f33-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="07f33-161">Jeśli nie chcesz wykonywać testów, uruchom `build.cmd -t:Compile` lub `./build.sh -t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="07f33-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="07f33-162">Aby skompilować interfejs wiersza polecenia w macOS Sierra, należy ustawić zmienną środowiskową DOTNET_RUNTIME_ID, uruchamiając polecenie `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="07f33-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="07f33-163">Korzystanie z kompilacji</span><span class="sxs-lookup"><span data-stu-id="07f33-163">Using your build</span></span>

<span data-ttu-id="07f33-164">Użyj `dotnet` pliku wykonywalnego z *artefaktów/{OS}-{Arch}/STAGE2* , aby wypróbować nowo utworzony interfejs wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="07f33-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="07f33-165">Jeśli chcesz użyć danych wyjściowych kompilacji podczas wywoływania `dotnet` z bieżącej konsoli, możesz również dodać *artefakty/{OS}-{Arch}/STAGE2* do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="07f33-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="07f33-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07f33-166">See also</span></span>

- [<span data-ttu-id="07f33-167">Środowisko uruchomieniowe platformy .NET</span><span class="sxs-lookup"><span data-stu-id="07f33-167">.NET Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/README.md)
- [<span data-ttu-id="07f33-168">Przewodnik dla deweloperów interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="07f33-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [<span data-ttu-id="07f33-169">Tworzenie pakietów dystrybucji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="07f33-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
