---
title: Instalowanie programu .NET Core w systemie RHEL — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie RHEL.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7ae55f881cd0c877cf1db24be7a4ee23320e21a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603042"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a><span data-ttu-id="e6cd4-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie RHEL</span><span class="sxs-lookup"><span data-stu-id="e6cd4-103">Install .NET Core SDK or .NET Core Runtime on RHEL</span></span>

<span data-ttu-id="e6cd4-104">Platforma .NET Core jest obsługiwana w systemie RHEL.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-104">.NET Core is supported on RHEL.</span></span> <span data-ttu-id="e6cd4-105">W tym artykule opisano sposób instalowania programu .NET Core w systemie RHEL.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-105">This article describes how to install .NET Core on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="e6cd4-106">Zarejestruj swoją subskrypcję Red Hat</span><span class="sxs-lookup"><span data-stu-id="e6cd4-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="e6cd4-107">Aby zainstalować platformę .NET Core z Red Hat na RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="e6cd4-108">Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="e6cd4-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="e6cd4-109">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="e6cd4-109">Supported distributions</span></span>

<span data-ttu-id="e6cd4-110">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach RHEL 7 i RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-110">The following table is a list of currently supported .NET Core releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="e6cd4-111">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu RHEL nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="e6cd4-112">✔️ wskazuje, że wersja programu RHEL lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-112">A ✔️ indicates that the version of RHEL or .NET Core is still supported.</span></span>
- <span data-ttu-id="e6cd4-113">❌Wskazuje, że wersja RHEL lub .NET Core nie jest obsługiwana w tej wersji RHEL.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-113">A ❌ indicates that the version of RHEL or .NET Core isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="e6cd4-114">Gdy wersja RHEL i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-114">When both a version of RHEL and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="e6cd4-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="e6cd4-115">RHEL</span></span>                   | <span data-ttu-id="e6cd4-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e6cd4-116">.NET Core 2.1</span></span> | <span data-ttu-id="e6cd4-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e6cd4-117">.NET Core 3.1</span></span> | <span data-ttu-id="e6cd4-118">.NET 5 (wersja zapoznawcza) (tylko instalacja ręczna)</span><span class="sxs-lookup"><span data-stu-id="e6cd4-118">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="e6cd4-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="e6cd4-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="e6cd4-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e6cd4-120">✔️ 2.1</span></span>        | <span data-ttu-id="e6cd4-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e6cd4-121">✔️ 3.1</span></span>        | <span data-ttu-id="e6cd4-122">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="e6cd4-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="e6cd4-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="e6cd4-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="e6cd4-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="e6cd4-124">✔️ 2.1</span></span>        | <span data-ttu-id="e6cd4-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="e6cd4-125">✔️ 3.1</span></span>        | <span data-ttu-id="e6cd4-126">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="e6cd4-126">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="e6cd4-127">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-127">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="e6cd4-128">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="e6cd4-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="e6cd4-129">3.0</span><span class="sxs-lookup"><span data-stu-id="e6cd4-129">3.0</span></span>
- <span data-ttu-id="e6cd4-130">2.2</span><span class="sxs-lookup"><span data-stu-id="e6cd4-130">2.2</span></span>
- <span data-ttu-id="e6cd4-131">2.0</span><span class="sxs-lookup"><span data-stu-id="e6cd4-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e6cd4-132">Jak zainstalować inne wersje</span><span class="sxs-lookup"><span data-stu-id="e6cd4-132">How to install other versions</span></span>

<span data-ttu-id="e6cd4-133">Zapoznaj się z [dokumentacją firmy Red Hat dla platformy .NET Core w przypadku](https://access.redhat.com/documentation/net_core/) czynności wymaganych do zainstalowania innych wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-133">Consult the [Red Hat documentation for .NET Core](https://access.redhat.com/documentation/net_core/) on the steps required to install other releases of .NET Core.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="e6cd4-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="e6cd4-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="e6cd4-135">Platforma .NET Core jest dołączona do repozytoriów AppStream dla RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-135">.NET Core is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="e6cd4-136">RHEL ✔️ 7</span><span class="sxs-lookup"><span data-stu-id="e6cd4-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="e6cd4-137">Następujące polecenie instaluje `scl-utils` pakiet:</span><span class="sxs-lookup"><span data-stu-id="e6cd4-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="e6cd4-138">Instalacja zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="e6cd4-138">Install the SDK</span></span>

<span data-ttu-id="e6cd4-139">Zestaw .NET Core SDK umożliwia tworzenie aplikacji przy użyciu platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-139">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="e6cd4-140">W przypadku zainstalowania zestaw .NET Core SDK nie trzeba instalować odpowiedniego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-140">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="e6cd4-141">Aby zainstalować zestaw .NET Core SDK, uruchom następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="e6cd4-141">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="e6cd4-142">Red Hat nie zaleca trwałego włączania `rh-dotnet31` , ponieważ może to mieć wpływ na inne programy.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-142">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="e6cd4-143">Program zawiera na przykład `rh-dotnet31` wersję `libcurl` , która różni się od bazowej wersji RHEL.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-143">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="e6cd4-144">Może to prowadzić do problemów z programami, które nie oczekują innej wersji programu `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="e6cd4-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="e6cd4-145">Jeśli chcesz `rh-dotnet` trwale włączyć, Dodaj następujący wiersz do pliku _~/.bashrc._ .</span><span class="sxs-lookup"><span data-stu-id="e6cd4-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="e6cd4-146">Instalowanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="e6cd4-146">Install the runtime</span></span>

<span data-ttu-id="e6cd4-147">Środowisko uruchomieniowe programu .NET Core umożliwia uruchamianie aplikacji, które zostały wykonane przy użyciu platformy .NET Core, które nie zawierały środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-147">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="e6cd4-148">Poniższe polecenia instalują środowisko uruchomieniowe ASP.NET Core, które jest najbardziej zgodnym środowiskiem uruchomieniowym dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-148">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="e6cd4-149">W terminalu uruchom następujące polecenia.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-149">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="e6cd4-150">Red Hat nie zaleca trwałego włączania `rh-dotnet31-aspnetcore-runtime-3.1` , ponieważ może to mieć wpływ na inne programy.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-150">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="e6cd4-151">Program zawiera na przykład `rh-dotnet31-aspnetcore-runtime-3.1` wersję `libcurl` , która różni się od bazowej wersji RHEL.</span><span class="sxs-lookup"><span data-stu-id="e6cd4-151">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="e6cd4-152">Może to prowadzić do problemów z programami, które nie oczekują innej wersji programu `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="e6cd4-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="e6cd4-153">Jeśli chcesz `rh-dotnet31-aspnetcore-runtime-3.1` trwale włączyć, Dodaj następujący wiersz do pliku _~/.bashrc._ .</span><span class="sxs-lookup"><span data-stu-id="e6cd4-153">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="e6cd4-154">Jako alternatywę dla środowiska uruchomieniowego ASP.NET Core można zainstalować środowisko uruchomieniowe programu .NET Core, które nie obejmuje ASP.NET Core Support: Zastąp `rh-dotnet31-aspnetcore-runtime-3.1` w poleceniach powyżej `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="e6cd4-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="e6cd4-155">Przystawki</span><span class="sxs-lookup"><span data-stu-id="e6cd4-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="e6cd4-156">Zależności</span><span class="sxs-lookup"><span data-stu-id="e6cd4-156">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="e6cd4-157">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="e6cd4-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="e6cd4-158">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="e6cd4-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="e6cd4-159">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e6cd4-159">Next steps</span></span>

- [<span data-ttu-id="e6cd4-160">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e6cd4-160">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
