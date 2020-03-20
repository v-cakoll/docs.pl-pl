---
title: Rozwiązywanie problemów "Nie można uruchomić tej aplikacji"
description: Dowiedz się, co zrobić, jeśli zostanie wyświetlone okno dialogowe "Nie można uruchomić tej aplikacji".
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965909"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="74d76-103">Rozwiązywanie problemów z komunikatem o błędzie "Nie można uruchomić tej aplikacji"</span><span class="sxs-lookup"><span data-stu-id="74d76-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="74d76-104">Aplikacje opracowane dla programu .NET Framework zazwyczaj wymagają zainstalowania określonej wersji programu .NET Framework w systemie.</span><span class="sxs-lookup"><span data-stu-id="74d76-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="74d76-105">W niektórych przypadkach można podjąć próbę uruchomienia aplikacji bez zainstalowanej wersji lub oczekiwanej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74d76-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="74d76-106">Często powoduje to wyświetlenie następującego okna dialogowego błędu:</span><span class="sxs-lookup"><span data-stu-id="74d76-106">This often produces an error dialog box like the following:</span></span>

![Nie można uruchomić tej aplikacji](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="74d76-108">Zazwyczaj wskazuje to na jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="74d76-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="74d76-109">Instalacja platformy .NET Framework w systemie została uszkodzona.</span><span class="sxs-lookup"><span data-stu-id="74d76-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="74d76-110">Nie można wykryć wersji programu .NET Framework wymaganej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="74d76-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="74d76-111">Aby rozwiązać ten problem, aby uruchomić aplikację, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="74d76-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="74d76-112">Pobierz [narzędzie do naprawy programu .NET Framework (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="74d76-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="74d76-113">Narzędzie działa automatycznie po zakończeniu pobierania.</span><span class="sxs-lookup"><span data-stu-id="74d76-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="74d76-114">Jeśli narzędzie do naprawy programu .NET Framework zaleca jakąkolwiek dodatkową akcję, taką jak ta przedstawiona na poniższym rysunku, wybierz przycisk **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="74d76-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Zalecane zmiany](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="74d76-116">Narzędzia naprawcze platformy .NET Framework są wyświetlane na poniższym rysunku, aby wskazać, że zmiany zostały zakończone.</span><span class="sxs-lookup"><span data-stu-id="74d76-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="74d76-117">Pozostaw otwarte okno dialogowe podczas próby ponownego uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="74d76-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="74d76-118">To powinno się udać, jeśli narzędzie do naprawy programu .NET Framework zidentyfikowało i poprawiło uszkodzoną instalację programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74d76-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Zalecane zmiany](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="74d76-120">Jeśli aplikacja działa pomyślnie, wybierz przycisk **Zakończ.**</span><span class="sxs-lookup"><span data-stu-id="74d76-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="74d76-121">W przeciwnym razie wybierz przycisk **Dalej.**</span><span class="sxs-lookup"><span data-stu-id="74d76-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="74d76-122">Jeśli wybrano przycisk **Dalej,** narzędzie .NET Framework Repair Tool wyświetla następujące okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="74d76-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="74d76-123">Wybierz przycisk **Zakończ,** aby wysłać informacje diagnostyczne do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="74d76-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Nie można rozwiązać problemu](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="74d76-125">Jeśli nadal nie można uruchomić aplikacji, zainstaluj najnowszą wersję programu .NET Framework obsługiwanego przez twoją wersję systemu Windows, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="74d76-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="74d76-126">Wersja systemu Windows</span><span class="sxs-lookup"><span data-stu-id="74d76-126">Windows version</span></span>|<span data-ttu-id="74d76-127">Instalacja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="74d76-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="74d76-128">Rocznicowa aktualizacja systemu Windows 10 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="74d76-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="74d76-129">.NET Framework 4.8 Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="74d76-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="74d76-130">Windows 10, Windows 10 Aktualizacja listopadowa</span><span class="sxs-lookup"><span data-stu-id="74d76-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="74d76-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="74d76-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="74d76-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="74d76-132">Windows 8.1</span></span>|[<span data-ttu-id="74d76-133">.NET Framework 4.8 Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="74d76-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="74d76-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="74d76-134">Windows 8</span></span>|[<span data-ttu-id="74d76-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="74d76-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="74d76-136">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="74d76-136">Windows 7 SP1</span></span>|[<span data-ttu-id="74d76-137">.NET Framework 4.8 Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="74d76-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="74d76-138">Windows Vista z dodatkiem SP2</span><span class="sxs-lookup"><span data-stu-id="74d76-138">Windows Vista SP2</span></span>|[<span data-ttu-id="74d76-139">Program .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="74d76-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="74d76-140">Program .NET Framework 4.8 jest preinstalowany w systemie Windows 10 May 2019 Update.</span><span class="sxs-lookup"><span data-stu-id="74d76-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="74d76-141">Spróbuj uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="74d76-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="74d76-142">W niektórych przypadkach może zostać wyświetlone okno dialogowe, takie jak następujące, w którym zostanie wyświetlony komunikat o zainstalowaniu programu .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="74d76-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="74d76-143">Wybierz **opcję Pobierz i zainstaluj tę funkcję,** aby zainstalować program .NET Framework 3.5, a następnie ponownie uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="74d76-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Nie można rozwiązać problemu](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="74d76-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74d76-145">See also</span></span>

- [<span data-ttu-id="74d76-146">Wymagania systemowe programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="74d76-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="74d76-147">Przewodnik po instalacji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="74d76-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="74d76-148">Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="74d76-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
