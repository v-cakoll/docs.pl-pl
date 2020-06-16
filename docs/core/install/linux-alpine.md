---
title: Instalowanie platformy .NET Core na platformie Alpine-.NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core na platformie Alpine.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771504"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="c7dab-103">Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core na platformie Alpine</span><span class="sxs-lookup"><span data-stu-id="c7dab-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="c7dab-104">W tym artykule opisano sposób instalowania programu .NET Core w witrynie Alpine.</span><span class="sxs-lookup"><span data-stu-id="c7dab-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="c7dab-105">Gdy wersja Alpine nie jest objęta pomocą techniczną, program .NET Core nie jest już obsługiwany w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="c7dab-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="c7dab-106">Te instrukcje mogą jednak ułatwić uzyskanie programu .NET Core działającego w tych wersjach, chociaż nie jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c7dab-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="c7dab-107">Brak instalatorów dla Alpine.</span><span class="sxs-lookup"><span data-stu-id="c7dab-107">There are no installers for Alpine.</span></span> <span data-ttu-id="c7dab-108">Musisz użyć [skryptu instalacji](#scripted-install) lub instrukcji [instalacji ręcznej](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="c7dab-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="c7dab-109">Obsługiwane dystrybucje</span><span class="sxs-lookup"><span data-stu-id="c7dab-109">Supported distributions</span></span>

<span data-ttu-id="c7dab-110">Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core i wersje Alpine, w których są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c7dab-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="c7dab-111">Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Alp osiągnie koniec cyklu życia](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="c7dab-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="c7dab-112">✔️ wskazuje, że wersja Alpine lub .NET Core jest nadal obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="c7dab-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="c7dab-113">❌Wskazuje, że wersja Alpine lub .NET Core nie jest obsługiwana w tej wersji Alpine.</span><span class="sxs-lookup"><span data-stu-id="c7dab-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="c7dab-114">Gdy wersja Alpine i wersja platformy .NET Core ma ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.</span><span class="sxs-lookup"><span data-stu-id="c7dab-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="c7dab-115">Alp</span><span class="sxs-lookup"><span data-stu-id="c7dab-115">Alpine</span></span>                   | <span data-ttu-id="c7dab-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c7dab-116">.NET Core 2.1</span></span> | <span data-ttu-id="c7dab-117">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-117">.NET Core 3.1</span></span> | <span data-ttu-id="c7dab-118">.NET 5 (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="c7dab-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c7dab-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="c7dab-119">✔️ 3.12</span></span>  | <span data-ttu-id="c7dab-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-120">✔️ 2.1</span></span>        | <span data-ttu-id="c7dab-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-121">✔️ 3.1</span></span>        | <span data-ttu-id="c7dab-122">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="c7dab-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c7dab-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="c7dab-123">✔️ 3.11</span></span>  | <span data-ttu-id="c7dab-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-124">✔️ 2.1</span></span>        | <span data-ttu-id="c7dab-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-125">✔️ 3.1</span></span>        | <span data-ttu-id="c7dab-126">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="c7dab-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c7dab-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="c7dab-127">✔️ 3.10</span></span>  | <span data-ttu-id="c7dab-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-128">✔️ 2.1</span></span>        | <span data-ttu-id="c7dab-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-129">✔️ 3.1</span></span>        | <span data-ttu-id="c7dab-130">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="c7dab-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c7dab-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="c7dab-131">✔️ 3.9</span></span>   | <span data-ttu-id="c7dab-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-132">✔️ 2.1</span></span>        | <span data-ttu-id="c7dab-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-133">✔️ 3.1</span></span>        | <span data-ttu-id="c7dab-134">✔️ 5,0 — wersja zapoznawcza</span><span class="sxs-lookup"><span data-stu-id="c7dab-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="c7dab-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="c7dab-135">❌ 3.8</span></span>   | <span data-ttu-id="c7dab-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-136">✔️ 2.1</span></span>        | <span data-ttu-id="c7dab-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="c7dab-137">❌ 3.1</span></span>        | <span data-ttu-id="c7dab-138">❌wersja zapoznawcza 5,0</span><span class="sxs-lookup"><span data-stu-id="c7dab-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="c7dab-139">Następujące wersje programu .NET Core nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c7dab-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="c7dab-140">Pliki do pobrania dla tych nadal są publikowane:</span><span class="sxs-lookup"><span data-stu-id="c7dab-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c7dab-141">3.0</span><span class="sxs-lookup"><span data-stu-id="c7dab-141">3.0</span></span>
- <span data-ttu-id="c7dab-142">2.2</span><span class="sxs-lookup"><span data-stu-id="c7dab-142">2.2</span></span>
- <span data-ttu-id="c7dab-143">2.0</span><span class="sxs-lookup"><span data-stu-id="c7dab-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="c7dab-144">Zależności</span><span class="sxs-lookup"><span data-stu-id="c7dab-144">Dependencies</span></span>

<span data-ttu-id="c7dab-145">Platforma .NET Core w systemie Alpine Linux wymaga zainstalowanych następujących zależności:</span><span class="sxs-lookup"><span data-stu-id="c7dab-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="c7dab-146">ICU — libs</span><span class="sxs-lookup"><span data-stu-id="c7dab-146">icu-libs</span></span>
- <span data-ttu-id="c7dab-147">krb5 — libs</span><span class="sxs-lookup"><span data-stu-id="c7dab-147">krb5-libs</span></span>
- <span data-ttu-id="c7dab-148">libintl</span><span class="sxs-lookup"><span data-stu-id="c7dab-148">libintl</span></span>
- <span data-ttu-id="c7dab-149">libssl 1.1 (Alpine v lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="c7dab-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="c7dab-150">libssl 1.0 (Alpine v 3.8)</span><span class="sxs-lookup"><span data-stu-id="c7dab-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="c7dab-151">libstdc + +</span><span class="sxs-lookup"><span data-stu-id="c7dab-151">libstdc++</span></span>
- <span data-ttu-id="c7dab-152">LTTng — zespół sklepu uniwersalnego</span><span class="sxs-lookup"><span data-stu-id="c7dab-152">lttng-ust</span></span>
- <span data-ttu-id="c7dab-153">numactl (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="c7dab-153">numactl (optional)</span></span>
- <span data-ttu-id="c7dab-154">zlib</span><span class="sxs-lookup"><span data-stu-id="c7dab-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="c7dab-155">Instalacja z skryptami</span><span class="sxs-lookup"><span data-stu-id="c7dab-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c7dab-156">Instalacja ręczna</span><span class="sxs-lookup"><span data-stu-id="c7dab-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c7dab-157">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c7dab-157">Next steps</span></span>

- [<span data-ttu-id="c7dab-158">Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c7dab-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
