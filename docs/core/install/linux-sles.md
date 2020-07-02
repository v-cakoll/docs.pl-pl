---
title: Instalowanie programu .NET Core w systemie SLES — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie SLES.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 8f64efcc8206b47855871104e5b6914570c06da0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619419"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="b361b-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie SLES</span><span class="sxs-lookup"><span data-stu-id="b361b-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="b361b-104">Platforma .NET Core jest obsługiwana w systemie SLES.</span><span class="sxs-lookup"><span data-stu-id="b361b-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="b361b-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie SLES.</span><span class="sxs-lookup"><span data-stu-id="b361b-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="b361b-106">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="b361b-106">Supported distributions</span></span>

<span data-ttu-id="b361b-107">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach SLES 12 SP2 i SLES 15.</span><span class="sxs-lookup"><span data-stu-id="b361b-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="b361b-108">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu SLES nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="b361b-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="b361b-109">✔️ wskazuje, że wersja programu SLES lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="b361b-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="b361b-110">❌Wskazuje, że wersja SLES lub .NET Core nie jest obsługiwana w tej wersji SLES.</span><span class="sxs-lookup"><span data-stu-id="b361b-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="b361b-111">Gdy wersja SLES i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="b361b-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="b361b-112">SLES</span><span class="sxs-lookup"><span data-stu-id="b361b-112">SLES</span></span>                   | <span data-ttu-id="b361b-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b361b-113">.NET Core 2.1</span></span> | <span data-ttu-id="b361b-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b361b-114">.NET Core 3.1</span></span> | <span data-ttu-id="b361b-115">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="b361b-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="b361b-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="b361b-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="b361b-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b361b-117">✔️ 2.1</span></span>        | <span data-ttu-id="b361b-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b361b-118">✔️ 3.1</span></span>        | <span data-ttu-id="b361b-119">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b361b-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b361b-120">✔️ [12 z dodatkiem SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="b361b-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="b361b-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b361b-121">✔️ 2.1</span></span>        | <span data-ttu-id="b361b-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b361b-122">✔️ 3.1</span></span>        | <span data-ttu-id="b361b-123">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b361b-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="b361b-124">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b361b-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="b361b-125">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="b361b-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="b361b-126">3.0</span><span class="sxs-lookup"><span data-stu-id="b361b-126">3.0</span></span>
- <span data-ttu-id="b361b-127">2.2</span><span class="sxs-lookup"><span data-stu-id="b361b-127">2.2</span></span>
- <span data-ttu-id="b361b-128">2.0</span><span class="sxs-lookup"><span data-stu-id="b361b-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b361b-129">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="b361b-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="b361b-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="b361b-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="b361b-131">Obecnie pakiet instalacyjny usługi Microsoft Repository SLES 15 zainstaluje plik *Microsoft-prod.* Repository w niewłaściwym katalogu, uniemożliwiając użyciu narzędzia zypper znalezienie pakietów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b361b-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="b361b-132">Aby rozwiązać ten problem, Utwórz link symboliczny w poprawnym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b361b-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="b361b-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="b361b-133">SLES 12 ✔️</span></span>

<span data-ttu-id="b361b-134">Program .NET Core wymaga programu SP2 jako minimum dla rodziny SLES 12.</span><span class="sxs-lookup"><span data-stu-id="b361b-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="b361b-135">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="b361b-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="b361b-136">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b361b-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="b361b-137">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="b361b-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="b361b-138">Zależności</span><span class="sxs-lookup"><span data-stu-id="b361b-138">Dependencies</span></span>

<span data-ttu-id="b361b-139">Po zainstalowaniu programu przy użyciu Menedżera pakietów te biblioteki są instalowane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="b361b-139">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="b361b-140">Jeśli jednak ręcznie zainstalujesz platformę .NET Core lub opublikujesz aplikację, musisz upewnić się, że te biblioteki są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="b361b-140">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="b361b-141">krb5</span><span class="sxs-lookup"><span data-stu-id="b361b-141">krb5</span></span>
- <span data-ttu-id="b361b-142">libicu</span><span class="sxs-lookup"><span data-stu-id="b361b-142">libicu</span></span>
- <span data-ttu-id="b361b-143">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="b361b-143">libopenssl1_1</span></span>

<span data-ttu-id="b361b-144">Jeśli docelowa wersja OpenSSL środowiska uruchomieniowego to 1,1 lub nowsza, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="b361b-144">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="b361b-145">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="b361b-145">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="b361b-146">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="b361b-146">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="b361b-147">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="b361b-147">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="b361b-148">Aby zainstalować najnowszą wersję programu *libgdiplus* , można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="b361b-148">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="b361b-149">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="b361b-149">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="b361b-150">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="b361b-150">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="b361b-151">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="b361b-151">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="b361b-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b361b-152">Next steps</span></span>

- [<span data-ttu-id="b361b-153">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b361b-153">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
