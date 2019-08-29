---
title: Instalowanie .NET Framework w systemie Windows 10
description: Dowiedz się, jak zainstalować .NET Framework w systemie Windows 10 lub Windows Server 2016.
author: rlander
ms.author: mairaw
ms.date: 04/18/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 33805230e0aa6c75443773d60e73f9463ee1fde5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106545"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016-and-later"></a><span data-ttu-id="6c5d8-103">Instalowanie .NET Framework w systemach Windows 10 i Windows Server 2016 i nowszych</span><span class="sxs-lookup"><span data-stu-id="6c5d8-103">Install the .NET Framework on Windows 10 and Windows Server 2016 and later</span></span>

<span data-ttu-id="6c5d8-104">.NET Framework jest wymagane do uruchamiania wielu aplikacji w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="6c5d8-105">Instrukcje zawarte w tym artykule powinny pomóc w zainstalowaniu wymaganych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-105">The instructions in this article should help you install the .NET Framework versions that you need.</span></span> <span data-ttu-id="6c5d8-106">[.NET Framework 4,8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) jest najnowszą dostępną wersją.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-106">The [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) is the latest available version.</span></span>

<span data-ttu-id="6c5d8-107">Na tej stronie może nastąpić próba uruchomienia aplikacji i wyświetlenia okna dialogowego na maszynie podobnej do następującego:</span><span class="sxs-lookup"><span data-stu-id="6c5d8-107">You may have arrived on this page after trying to run an application and seeing a dialog on your machine similar to the following one:</span></span>

![Nie można uruchomić tej aplikacji](./media/this-application-could-not-be-started.png)

## <a name="net-framework-48"></a><span data-ttu-id="6c5d8-109">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="6c5d8-109">.NET Framework 4.8</span></span>

<span data-ttu-id="6c5d8-110">.NET Framework 4,8 jest dołączony do:</span><span class="sxs-lookup"><span data-stu-id="6c5d8-110">The .NET Framework 4.8 is included with:</span></span>

- [<span data-ttu-id="6c5d8-111">Aktualizacja systemu Windows 10 maja 2019</span><span class="sxs-lookup"><span data-stu-id="6c5d8-111">Windows 10 May 2019 Update</span></span>](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

> [!div class="button"]
> [<span data-ttu-id="6c5d8-112">Pobierz .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="6c5d8-112">Download .NET Framework 4.8</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="6c5d8-113">[.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) może służyć do uruchamiania aplikacji skompilowanych dla .NET Framework 4,0 za pomocą 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-113">[.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) can be used to run applications built for the .NET Framework 4.0 through 4.7.2.</span></span>

<span data-ttu-id="6c5d8-114">[.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) można zainstalować w:</span><span class="sxs-lookup"><span data-stu-id="6c5d8-114">You can install [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) on:</span></span>

- <span data-ttu-id="6c5d8-115">Aktualizacja systemu Windows 10 październik 2018 (wersja 1809)</span><span class="sxs-lookup"><span data-stu-id="6c5d8-115">Windows 10 October 2018 Update (version 1809)</span></span>
- <span data-ttu-id="6c5d8-116">Aktualizacja systemu Windows 10 z kwietnia 2018 (wersja 1803)</span><span class="sxs-lookup"><span data-stu-id="6c5d8-116">Windows 10 April 2018 Update (version 1803)</span></span>
- <span data-ttu-id="6c5d8-117">Aktualizacja systemu Windows 10 dla twórców (wersja 1709)</span><span class="sxs-lookup"><span data-stu-id="6c5d8-117">Windows 10 Fall Creators Update (version 1709)</span></span>
- <span data-ttu-id="6c5d8-118">Aktualizacja systemu Windows 10 dla twórców (wersja 1703)</span><span class="sxs-lookup"><span data-stu-id="6c5d8-118">Windows 10 Creators Update (version 1703)</span></span>
- <span data-ttu-id="6c5d8-119">Rocznicowa Aktualizacja systemu Windows 10 (wersja 1607)</span><span class="sxs-lookup"><span data-stu-id="6c5d8-119">Windows 10 Anniversary Update (version 1607)</span></span>
- <span data-ttu-id="6c5d8-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="6c5d8-120">Windows Server 2019</span></span>
- <span data-ttu-id="6c5d8-121">System Windows Server w wersji 1809</span><span class="sxs-lookup"><span data-stu-id="6c5d8-121">Windows Server, version 1809</span></span>
- <span data-ttu-id="6c5d8-122">System Windows Server w wersji 1803</span><span class="sxs-lookup"><span data-stu-id="6c5d8-122">Windows Server, version 1803</span></span>
- <span data-ttu-id="6c5d8-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="6c5d8-123">Windows Server 2016</span></span>

<span data-ttu-id="6c5d8-124">.NET Framework 4,8 nie jest obsługiwana w:</span><span class="sxs-lookup"><span data-stu-id="6c5d8-124">The .NET Framework 4.8 is not supported on:</span></span>

- <span data-ttu-id="6c5d8-125">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="6c5d8-125">Windows 10 1507</span></span>
- <span data-ttu-id="6c5d8-126">Windows 10 1511</span><span class="sxs-lookup"><span data-stu-id="6c5d8-126">Windows 10 1511</span></span>

<span data-ttu-id="6c5d8-127">Jeśli używasz systemu Windows 10 1507 lub 1511 i chcesz zainstalować .NET Framework 4,8, musisz najpierw przeprowadzić uaktualnienie do nowszej wersji systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-127">If you're using Windows 10 1507 or 1511 and you want to install the .NET Framework 4.8, you first need to upgrade to a later Windows 10 version.</span></span>

## <a name="net-framework-462"></a><span data-ttu-id="6c5d8-128">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="6c5d8-128">.NET Framework 4.6.2</span></span>

<span data-ttu-id="6c5d8-129">[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345) to najnowsza obsługiwana wersja .NET Framework w systemach Windows 10 1507 i 1511.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-129">The [.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345) is the latest supported .NET Framework version on Windows 10 1507 and 1511.</span></span>

<span data-ttu-id="6c5d8-130">.NET Framework 4.6.2 obsługuje aplikacje skompilowane dla .NET Framework 4,0 do 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-130">The .NET Framework 4.6.2 supports apps built for the .NET Framework 4.0 through 4.6.2.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="6c5d8-131">Program .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="6c5d8-131">.NET Framework 3.5</span></span>

<span data-ttu-id="6c5d8-132">Postępuj zgodnie z instrukcjami, aby zainstalować [.NET Framework 3,5 w systemie Windows 10](dotnet-35-windows-10.md).</span><span class="sxs-lookup"><span data-stu-id="6c5d8-132">Follow the instructions to install the [.NET Framework 3.5 on Windows 10](dotnet-35-windows-10.md).</span></span>

<span data-ttu-id="6c5d8-133">.NET Framework 3,5 obsługuje aplikacje skompilowane dla .NET Framework 1,0 do 3,5.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-133">The .NET Framework 3.5 supports apps built for the .NET Framework 1.0 through 3.5.</span></span>

## <a name="additional-information"></a><span data-ttu-id="6c5d8-134">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="6c5d8-134">Additional information</span></span>

<span data-ttu-id="6c5d8-135">Wersje .NET Framework 4. x są aktualizacjami w miejscu do wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-135">.NET Framework 4.x versions are in-place updates to earlier versions.</span></span> <span data-ttu-id="6c5d8-136">Oznacza to następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="6c5d8-136">That means the following:</span></span>

- <span data-ttu-id="6c5d8-137">Na maszynie może być zainstalowana tylko jedna wersja .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-137">You can only have one version of the .NET Framework 4.x installed on your machine.</span></span>

- <span data-ttu-id="6c5d8-138">Jeśli nowsza wersja jest już zainstalowana, nie można zainstalować starszej wersji .NET Framework na maszynie.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-138">You cannot install an earlier version of the .NET Framework on your machine if a later version is already installed.</span></span>

- <span data-ttu-id="6c5d8-139">4. x wersje .NET Framework mogą służyć do uruchamiania aplikacji skompilowanych dla .NET Framework 4,0 za pomocą tej wersji.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-139">4.x versions of the .NET Framework can be used to run applications built for the .NET Framework 4.0 through that version.</span></span> <span data-ttu-id="6c5d8-140">Na przykład .NET Framework 4,7 może służyć do uruchamiania aplikacji skompilowanych dla .NET Framework 4,0 do 4,7.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-140">For example, .NET Framework 4.7 can be used to run applications built for the .NET Framework 4.0 through 4.7.</span></span> <span data-ttu-id="6c5d8-141">Najnowsza wersja (.NET Framework 4,8) może służyć do uruchamiania aplikacji skompilowanych ze wszystkimi wersjami .NET Framework, począwszy od 4,0.</span><span class="sxs-lookup"><span data-stu-id="6c5d8-141">The latest version (the .NET Framework 4.8) can be used to run applications built with all versions of the .NET Framework starting with 4.0.</span></span>

<span data-ttu-id="6c5d8-142">Aby uzyskać listę wszystkich wersji .NET Framework dostępnych do pobrania, zobacz stronę [pliki do pobrania platformy .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) .</span><span class="sxs-lookup"><span data-stu-id="6c5d8-142">For a list of all the versions of the .NET Framework available to download, see the [.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) page.</span></span>

## <a name="help"></a><span data-ttu-id="6c5d8-143">Help</span><span class="sxs-lookup"><span data-stu-id="6c5d8-143">Help</span></span>

<span data-ttu-id="6c5d8-144">Jeśli nie możesz uzyskać zainstalowanej poprawnej wersji .NET Framework, możesz [skontaktować się z firmą Microsoft w celu uzyskania pomocy](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span><span class="sxs-lookup"><span data-stu-id="6c5d8-144">If you cannot get the correct version of the .NET Framework installed, you can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c5d8-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c5d8-145">See also</span></span>

- [<span data-ttu-id="6c5d8-146">Pliki do pobrania dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6c5d8-146">.NET Downloads</span></span>](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)
- [<span data-ttu-id="6c5d8-147">Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6c5d8-147">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
- [<span data-ttu-id="6c5d8-148">Zainstaluj .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="6c5d8-148">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
