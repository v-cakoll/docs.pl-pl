---
title: Zainstaluj program .NET Framework w systemie Windows 10
description: Dowiedz się, jak zainstalować program .NET Framework w systemie Windows 10 lub Windows Server 2016.
author: rlander
ms.author: mairaw
ms.date: 04/10/2018
ms.custom: updateeachrelease
ms.openlocfilehash: cf374f9d1fd7e343e5eba868d3f686784428a2d0
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270451"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016"></a><span data-ttu-id="b3295-103">Zainstaluj program .NET Framework w systemie Windows 10 i Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b3295-103">Install the .NET Framework on Windows 10 and Windows Server 2016</span></span>

<span data-ttu-id="b3295-104">.NET Framework jest wymagana do uruchamiania wielu aplikacji w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="b3295-104">The .NET Framework is required to run many applications on Windows.</span></span> <span data-ttu-id="b3295-105">Instrukcje w tym artykule powinny pomóc w instalacji wersji systemu .NET Framework, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b3295-105">The instructions in this article should help you install the .NET Framework versions that you need.</span></span> <span data-ttu-id="b3295-106">[.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) jest najnowszej dostępnej wersji.</span><span class="sxs-lookup"><span data-stu-id="b3295-106">The [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) is the latest available version.</span></span>

<span data-ttu-id="b3295-107">Użytkownik może następować na tej stronie po próby uruchomienia aplikacji i wyświetlanie okna dialogowego na tym komputerze podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="b3295-107">You may have arrived on this page after trying to run an application and seeing a dialog on your machine similar to the following one:</span></span>

![Nie można uruchomić tej aplikacji](./media/this-application-could-not-be-started.png)

## <a name="net-framework-472"></a><span data-ttu-id="b3295-109">.NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b3295-109">.NET Framework 4.7.2</span></span>

<span data-ttu-id="b3295-110">.NET Framework 4.7.2 jest dołączana do:</span><span class="sxs-lookup"><span data-stu-id="b3295-110">The .NET Framework 4.7.2 is included with:</span></span>

* [<span data-ttu-id="b3295-111">Usługa Windows Update 10 kwietnia 2018</span><span class="sxs-lookup"><span data-stu-id="b3295-111">Windows 10 April 2018 Update</span></span>](https://www.microsoft.com/software-download/windows10)

> [!div class="button"]
[<span data-ttu-id="b3295-112">.NET Framework 4.7.2 pobrać</span><span class="sxs-lookup"><span data-stu-id="b3295-112">Download .NET Framework 4.7.2</span></span>](https://www.microsoft.com/net/download/thank-you/net472?utm_source=ms-docs&utm_medium=referral)

<span data-ttu-id="b3295-113">[.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) może służyć do uruchamiania aplikacji utworzonych dla programu .NET Framework 4.0 za pośrednictwem 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b3295-113">The [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) can be used to run applications built for the .NET Framework 4.0 through 4.7.1.</span></span>

<span data-ttu-id="b3295-114">Można zainstalować [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) na:</span><span class="sxs-lookup"><span data-stu-id="b3295-114">You can install the [.NET Framework 4.7.2](http://go.microsoft.com/fwlink/?LinkID=863255) on:</span></span>

* <span data-ttu-id="b3295-115">Windows 10 spadek twórców aktualizację (wersja 1709)</span><span class="sxs-lookup"><span data-stu-id="b3295-115">Windows 10 Fall Creators Update (version 1709)</span></span>
* <span data-ttu-id="b3295-116">Windows 10 twórców aktualizację (wersja 1703)</span><span class="sxs-lookup"><span data-stu-id="b3295-116">Windows 10 Creators Update (version 1703)</span></span>
* <span data-ttu-id="b3295-117">Windows 10 Anniversary Update (w wersji 1607)</span><span class="sxs-lookup"><span data-stu-id="b3295-117">Windows 10 Anniversary Update (version 1607)</span></span>
* <span data-ttu-id="b3295-118">W systemie Windows Server w wersji 1709</span><span class="sxs-lookup"><span data-stu-id="b3295-118">Windows Server, version 1709</span></span>
* <span data-ttu-id="b3295-119">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b3295-119">Windows Server 2016</span></span>

<span data-ttu-id="b3295-120">.NET Framework 4.7.2 nie jest obsługiwane na:</span><span class="sxs-lookup"><span data-stu-id="b3295-120">The .NET Framework 4.7.2 is not supported on:</span></span>

* <span data-ttu-id="b3295-121">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="b3295-121">Windows 10 1507</span></span>
* <span data-ttu-id="b3295-122">Windows 10 1511</span><span class="sxs-lookup"><span data-stu-id="b3295-122">Windows 10 1511</span></span>

<span data-ttu-id="b3295-123">Jeśli używasz systemu Windows 10 1507 lub 1511 i chcesz zainstalować program .NET Framework 4.7.2, należy najpierw uaktualnić do nowszej wersji systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b3295-123">If you're using Windows 10 1507 or 1511 and you want to install the .NET Framework 4.7.2, you first need to upgrade to a later Windows 10 version.</span></span>

## <a name="net-framework-462"></a><span data-ttu-id="b3295-124">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b3295-124">.NET Framework 4.6.2</span></span>

<span data-ttu-id="b3295-125">[.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) jest najnowsza wersja obsługiwana wersja platformy .NET w systemie Windows 10 1507 i 1511.</span><span class="sxs-lookup"><span data-stu-id="b3295-125">The [.NET Framework 4.6.2](https://www.microsoft.com/en-us/download/details.aspx?id=53345) is the latest supported .NET Framework version on Windows 10 1507 and 1511.</span></span>

<span data-ttu-id="b3295-126">.NET Framework 4.6.2 obsługuje aplikacje dla programu .NET Framework 4.0 za pośrednictwem 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="b3295-126">The .NET Framework 4.6.2 supports apps built for the .NET Framework 4.0 through 4.6.2.</span></span>

## <a name="net-framework-35"></a><span data-ttu-id="b3295-127">Program .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="b3295-127">.NET Framework 3.5</span></span>

<span data-ttu-id="b3295-128">Postępuj zgodnie z instrukcjami, aby zainstalować [.NET Framework 3.5 w systemie Windows 10](dotnet-35-windows-10.md).</span><span class="sxs-lookup"><span data-stu-id="b3295-128">Follow the instructions to install the [.NET Framework 3.5 on Windows 10](dotnet-35-windows-10.md).</span></span>

<span data-ttu-id="b3295-129">.NET Framework 3.5 obsługuje aplikacje dla programu .NET Framework 1.0 za pośrednictwem 3.5.</span><span class="sxs-lookup"><span data-stu-id="b3295-129">The .NET Framework 3.5 supports apps built for the .NET Framework 1.0 through 3.5.</span></span>

## <a name="additional-information"></a><span data-ttu-id="b3295-130">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="b3295-130">Additional information</span></span>

<span data-ttu-id="b3295-131">Wersje programu .NET framework 4.x, to aktualizacje w miejscu do wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="b3295-131">.NET Framework 4.x versions are in-place updates to earlier versions.</span></span> <span data-ttu-id="b3295-132">Oznacza to następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b3295-132">That means the following:</span></span>

- <span data-ttu-id="b3295-133">Może mieć tylko jedną wersję systemu .NET Framework 4.x na komputerze jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="b3295-133">You can only have one version of the .NET Framework 4.x installed on your machine.</span></span>

- <span data-ttu-id="b3295-134">Nie można zainstalować starszej wersji programu .NET Framework na komputerze, jeśli jest już zainstalowana nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="b3295-134">You cannot install an earlier version of the .NET Framework on your machine if a later version is already installed.</span></span>

- <span data-ttu-id="b3295-135">wersje programu .NET Framework 4.x może służyć do uruchamiania aplikacji utworzonych dla programu .NET Framework 4.0, za pomocą tej wersji.</span><span class="sxs-lookup"><span data-stu-id="b3295-135">4.x versions of the .NET Framework can be used to run applications built for the .NET Framework 4.0 through that version.</span></span> <span data-ttu-id="b3295-136">Na przykład .NET Framework 4.7 może służyć do uruchamiania aplikacji utworzonych dla programu .NET Framework 4.0 za pośrednictwem 4.7.</span><span class="sxs-lookup"><span data-stu-id="b3295-136">For example, .NET Framework 4.7 can be used to run applications built for the .NET Framework 4.0 through 4.7.</span></span> <span data-ttu-id="b3295-137">Najnowszą wersję (.NET Framework 4.7.2) może służyć do uruchamiania aplikacji skompilowanej za pomocą wszystkich wersji platformy .NET, począwszy od 4.0.</span><span class="sxs-lookup"><span data-stu-id="b3295-137">The latest version (the .NET Framework 4.7.2) can be used to run applications built with all versions of the .NET Framework starting with 4.0.</span></span>

<span data-ttu-id="b3295-138">Aby uzyskać listę wszystkich wersji programu .NET Framework dostępnych do pobrania, zobacz [pobiera .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) strony.</span><span class="sxs-lookup"><span data-stu-id="b3295-138">For a list of all the versions of the .NET Framework available to download, see the [.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) page.</span></span>

## <a name="help"></a><span data-ttu-id="b3295-139">Pomoc</span><span class="sxs-lookup"><span data-stu-id="b3295-139">Help</span></span>

<span data-ttu-id="b3295-140">Jeśli nie można pobrać poprawna wersja Framework .NET zainstalowany, możesz [kontakt z firmą Microsoft w celu uzyskania pomocy](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span><span class="sxs-lookup"><span data-stu-id="b3295-140">If you cannot get the correct version of the .NET Framework installed, you can [contact Microsoft for help](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3295-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3295-141">See also</span></span>

<span data-ttu-id="b3295-142">[Pobieranie .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span><span class="sxs-lookup"><span data-stu-id="b3295-142">[.NET Downloads](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) </span></span>  
<span data-ttu-id="b3295-143">[Rozwiązywanie problemów z zablokowaną .NET Framework i odinstalowywaniem programu](troubleshoot-blocked-installations-and-uninstallations.md) </span><span class="sxs-lookup"><span data-stu-id="b3295-143">[Troubleshoot blocked .NET Framework installations and uninstallations](troubleshoot-blocked-installations-and-uninstallations.md) </span></span>  
[<span data-ttu-id="b3295-144">Zainstaluj program .NET Framework dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="b3295-144">Install the .NET Framework for developers</span></span>](guide-for-developers.md)
