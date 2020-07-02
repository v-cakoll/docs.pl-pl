---
title: Instalowanie programu .NET Core w systemie openSUSE — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619471"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="e6cfd-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie openSUSE</span><span class="sxs-lookup"><span data-stu-id="e6cfd-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="e6cfd-104">Platforma .NET Core jest obsługiwana w systemie openSUSE.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="e6cfd-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie openSUSE.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="e6cfd-106">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="e6cfd-106">Supported distributions</span></span>

<span data-ttu-id="e6cfd-107">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemie openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="e6cfd-108">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu openSUSE nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="e6cfd-109">✔️ wskazuje, że wersja programu openSUSE lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="e6cfd-110">❌Wskazuje, że wersja openSUSE lub .NET Core nie jest obsługiwana w tej wersji openSUSE.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="e6cfd-111">Gdy wersja openSUSE i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="e6cfd-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e6cfd-112">openSUSE</span></span>                   | <span data-ttu-id="e6cfd-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e6cfd-113">.NET Core 2.1</span></span> | <span data-ttu-id="e6cfd-114">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e6cfd-114">.NET Core 3.1</span></span> | <span data-ttu-id="e6cfd-115">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="e6cfd-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="e6cfd-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="e6cfd-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="e6cfd-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e6cfd-117">✔️ 2.1</span></span>        | <span data-ttu-id="e6cfd-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e6cfd-118">✔️ 3.1</span></span>        | <span data-ttu-id="e6cfd-119">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="e6cfd-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="e6cfd-120">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="e6cfd-121">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="e6cfd-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="e6cfd-122">3.0</span><span class="sxs-lookup"><span data-stu-id="e6cfd-122">3.0</span></span>
- <span data-ttu-id="e6cfd-123">2.2</span><span class="sxs-lookup"><span data-stu-id="e6cfd-123">2.2</span></span>
- <span data-ttu-id="e6cfd-124">2.0</span><span class="sxs-lookup"><span data-stu-id="e6cfd-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e6cfd-125">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="e6cfd-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="e6cfd-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="e6cfd-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="e6cfd-127">Rozwiązywanie problemów z menedżerem pakietów</span><span class="sxs-lookup"><span data-stu-id="e6cfd-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="e6cfd-128">Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="e6cfd-129">Nie można pobrać</span><span class="sxs-lookup"><span data-stu-id="e6cfd-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="e6cfd-130">Przystawki</span><span class="sxs-lookup"><span data-stu-id="e6cfd-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="e6cfd-131">Zależności</span><span class="sxs-lookup"><span data-stu-id="e6cfd-131">Dependencies</span></span>

<span data-ttu-id="e6cfd-132">Po zainstalowaniu programu przy użyciu Menedżera pakietów te biblioteki są instalowane dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-132">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="e6cfd-133">Jeśli jednak ręcznie zainstalujesz platformę .NET Core lub opublikujesz aplikację, musisz upewnić się, że te biblioteki są zainstalowane:</span><span class="sxs-lookup"><span data-stu-id="e6cfd-133">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="e6cfd-134">krb5</span><span class="sxs-lookup"><span data-stu-id="e6cfd-134">krb5</span></span>
- <span data-ttu-id="e6cfd-135">libicu</span><span class="sxs-lookup"><span data-stu-id="e6cfd-135">libicu</span></span>
- <span data-ttu-id="e6cfd-136">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="e6cfd-136">libopenssl1_0_0</span></span>

<span data-ttu-id="e6cfd-137">Jeśli docelowa wersja OpenSSL środowiska uruchomieniowego to 1,1 lub nowsza, należy zainstalować polecenie **COMPAT-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-137">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="e6cfd-138">Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="e6cfd-138">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="e6cfd-139">W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="e6cfd-139">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="e6cfd-140">libgdiplus (wersja 6.0.1 lub nowsza)</span><span class="sxs-lookup"><span data-stu-id="e6cfd-140">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="e6cfd-141">Aby zainstalować najnowszą wersję programu *libgdiplus* , można dodać do systemu repozytorium mono.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-141">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="e6cfd-142">Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="e6cfd-142">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="e6cfd-143">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="e6cfd-143">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="e6cfd-144">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="e6cfd-144">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="e6cfd-145">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e6cfd-145">Next steps</span></span>

- [<span data-ttu-id="e6cfd-146">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e6cfd-146">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
