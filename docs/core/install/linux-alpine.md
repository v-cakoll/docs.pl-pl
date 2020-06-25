---
title: Instalowanie platformy .NET Core na platformie Alpine-.NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core na platformie Alpine.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 92753933cbcedae28867b66293d1044f700d7baa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324826"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="b1e4b-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core na platformie Alpine</span><span class="sxs-lookup"><span data-stu-id="b1e4b-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="b1e4b-104">W tym artykule opisano sposób instalowania programu .NET Core w witrynie Alpine.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="b1e4b-105">Gdy wersja Alpine nie jest objęta pomocą techniczną, program .NET Core nie jest już obsługiwany w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="b1e4b-106">Te instrukcje mogą jednak ułatwić uzyskanie programu .NET Core działającego w tych wersjach, chociaż nie jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="b1e4b-107">Brak instalatorów dla Alpine.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-107">There are no installers for Alpine.</span></span> <span data-ttu-id="b1e4b-108">Musisz użyć [skryptu instalacji](#scripted-install) lub instrukcji [instalacji ręcznej](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="b1e4b-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="b1e4b-109">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="b1e4b-109">Supported distributions</span></span>

<span data-ttu-id="b1e4b-110">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core i wersje Alpine, w których są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="b1e4b-111">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Alp osiągnie koniec cyklu życia](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="b1e4b-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="b1e4b-112">✔️ wskazuje, że wersja Alpine lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="b1e4b-113">❌Wskazuje, że wersja Alpine lub .NET Core nie jest obsługiwana w tej wersji Alpine.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="b1e4b-114">Gdy wersja Alpine i wersja platformy .NET Core ma ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="b1e4b-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="b1e4b-115">Alpine</span></span>                   | <span data-ttu-id="b1e4b-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-116">.NET Core 2.1</span></span> | <span data-ttu-id="b1e4b-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-117">.NET Core 3.1</span></span> | <span data-ttu-id="b1e4b-118">.NET 5 (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="b1e4b-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="b1e4b-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="b1e4b-119">✔️ 3.12</span></span>  | <span data-ttu-id="b1e4b-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-120">✔️ 2.1</span></span>        | <span data-ttu-id="b1e4b-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-121">✔️ 3.1</span></span>        | <span data-ttu-id="b1e4b-122">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b1e4b-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b1e4b-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="b1e4b-123">✔️ 3.11</span></span>  | <span data-ttu-id="b1e4b-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-124">✔️ 2.1</span></span>        | <span data-ttu-id="b1e4b-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-125">✔️ 3.1</span></span>        | <span data-ttu-id="b1e4b-126">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b1e4b-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b1e4b-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="b1e4b-127">✔️ 3.10</span></span>  | <span data-ttu-id="b1e4b-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-128">✔️ 2.1</span></span>        | <span data-ttu-id="b1e4b-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-129">✔️ 3.1</span></span>        | <span data-ttu-id="b1e4b-130">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b1e4b-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b1e4b-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="b1e4b-131">✔️ 3.9</span></span>   | <span data-ttu-id="b1e4b-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-132">✔️ 2.1</span></span>        | <span data-ttu-id="b1e4b-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-133">✔️ 3.1</span></span>        | <span data-ttu-id="b1e4b-134">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="b1e4b-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="b1e4b-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="b1e4b-135">❌ 3.8</span></span>   | <span data-ttu-id="b1e4b-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-136">✔️ 2.1</span></span>        | <span data-ttu-id="b1e4b-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="b1e4b-137">❌ 3.1</span></span>        | <span data-ttu-id="b1e4b-138">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="b1e4b-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="b1e4b-139">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b1e4b-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="b1e4b-140">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="b1e4b-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="b1e4b-141">3.0</span><span class="sxs-lookup"><span data-stu-id="b1e4b-141">3.0</span></span>
- <span data-ttu-id="b1e4b-142">2.2</span><span class="sxs-lookup"><span data-stu-id="b1e4b-142">2.2</span></span>
- <span data-ttu-id="b1e4b-143">2.0</span><span class="sxs-lookup"><span data-stu-id="b1e4b-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="b1e4b-144">Zależności</span><span class="sxs-lookup"><span data-stu-id="b1e4b-144">Dependencies</span></span>

<span data-ttu-id="b1e4b-145">Platforma .NET Core w systemie Alpine Linux wymaga zainstalowanych następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="b1e4b-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="b1e4b-146">ICU — libs</span><span class="sxs-lookup"><span data-stu-id="b1e4b-146">icu-libs</span></span>
- <span data-ttu-id="b1e4b-147">krb5 — libs</span><span class="sxs-lookup"><span data-stu-id="b1e4b-147">krb5-libs</span></span>
- <span data-ttu-id="b1e4b-148">libintl</span><span class="sxs-lookup"><span data-stu-id="b1e4b-148">libintl</span></span>
- <span data-ttu-id="b1e4b-149">libssl 1.1 (Alpine v lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b1e4b-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="b1e4b-150">libssl 1.0 (Alpine v 3.8)</span><span class="sxs-lookup"><span data-stu-id="b1e4b-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="b1e4b-151">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="b1e4b-151">libstdc++</span></span>
- <span data-ttu-id="b1e4b-152">LTTng — zespół sklepu uniwersalnego</span><span class="sxs-lookup"><span data-stu-id="b1e4b-152">lttng-ust</span></span>
- <span data-ttu-id="b1e4b-153">numactl (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b1e4b-153">numactl (optional)</span></span>
- <span data-ttu-id="b1e4b-154">zlib</span><span class="sxs-lookup"><span data-stu-id="b1e4b-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="b1e4b-155">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="b1e4b-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="b1e4b-156">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="b1e4b-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="b1e4b-157">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b1e4b-157">Next steps</span></span>

- [<span data-ttu-id="b1e4b-158">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b1e4b-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
