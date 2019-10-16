---
title: Rozwiązywanie problemów — nie można uruchomić tej aplikacji
description: Dowiedz się, co zrobić, Jeśli zobaczysz okno dialogowe "nie można uruchomić tej aplikacji".
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 8fa8381f1b05445f259b4e4af5cc17fa487b2ce0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319168"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="4e701-103">Rozwiązywanie problemów z komunikatem o błędzie "nie można uruchomić tej aplikacji"</span><span class="sxs-lookup"><span data-stu-id="4e701-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="4e701-104">Aplikacje opracowane dla .NET Framework zwykle wymagają, aby w systemie była zainstalowana określona wersja .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e701-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="4e701-105">W niektórych przypadkach może zostać podjęta próba uruchomienia aplikacji bez zainstalowanej wersji lub oczekiwanej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e701-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="4e701-106">Powoduje to często Generowanie okna dialogowego błędu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4e701-106">This often produces an error dialog box like the following:</span></span>

![Nie można uruchomić tej aplikacji](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="4e701-108">Zwykle wskazuje jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="4e701-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="4e701-109">Instalacja .NET Framework w systemie uległa uszkodzeniu.</span><span class="sxs-lookup"><span data-stu-id="4e701-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="4e701-110">Nie można wykryć wersji .NET Framework wymaganej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4e701-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="4e701-111">Aby rozwiązać ten problem, możesz uruchomić aplikację, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="4e701-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="4e701-112">Pobierz [Narzędzie do naprawy .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="4e701-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="4e701-113">Narzędzie jest uruchamiane automatycznie po zakończeniu pobierania.</span><span class="sxs-lookup"><span data-stu-id="4e701-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="4e701-114">Jeśli narzędzie do naprawy .NET Framework zaleca wykonanie dodatkowych czynności, takich jak pokazane na poniższej ilustracji, wybierz pozycję **dalej**.</span><span class="sxs-lookup"><span data-stu-id="4e701-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Zalecane zmiany](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="4e701-116">Narzędzia do naprawy .NET Frameworką wyświetla okno dialogowe pokazane na poniższym rysunku, aby wskazać, że zmiany zostały wykonane.</span><span class="sxs-lookup"><span data-stu-id="4e701-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="4e701-117">Pozostaw to okno dialogowe otwarte, aby spróbować ponownie uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="4e701-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="4e701-118">Powinno to powieść się, jeśli narzędzie do naprawy .NET Framework zidentyfikowała i naprawił uszkodzoną instalację .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e701-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Zalecane zmiany](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="4e701-120">Jeśli aplikacja zostanie uruchomiona pomyślnie, wybierz przycisk **Zakończ** .</span><span class="sxs-lookup"><span data-stu-id="4e701-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="4e701-121">W przeciwnym razie wybierz przycisk **dalej** .</span><span class="sxs-lookup"><span data-stu-id="4e701-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="4e701-122">W przypadku wybrania przycisku **dalej** narzędzie .NET Framework Repair wyświetli okno dialogowe podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="4e701-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="4e701-123">Wybierz przycisk **Zakończ** , aby wysłać informacje diagnostyczne do firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4e701-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Nie można rozwiązać problemu](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="4e701-125">Jeśli nadal nie można uruchomić aplikacji, zainstaluj najnowszą wersję .NET Framework obsługiwaną przez daną wersję systemu Windows, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4e701-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="4e701-126">Wersja systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4e701-126">Windows version</span></span>|<span data-ttu-id="4e701-127">Instalacja .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e701-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="4e701-128">Rocznicowa Aktualizacja systemu Windows 10 i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="4e701-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="4e701-129">Środowisko uruchomieniowe .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="4e701-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="4e701-130">Aktualizacja systemu Windows 10, Windows 10 listopad</span><span class="sxs-lookup"><span data-stu-id="4e701-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="4e701-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="4e701-131">.NET Framework 4.6.2</span></span>](https://www.microsoft.com/download/details.aspx?id=53345)|
   |<span data-ttu-id="4e701-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="4e701-132">Windows 8.1</span></span>|[<span data-ttu-id="4e701-133">Środowisko uruchomieniowe .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="4e701-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="4e701-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="4e701-134">Windows 8</span></span>|[<span data-ttu-id="4e701-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="4e701-135">.NET Framework 4.6.1</span></span>](https://www.microsoft.com/download/details.aspx?id=49981)|
   |<span data-ttu-id="4e701-136">Windows 7 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="4e701-136">Windows 7 SP1</span></span>|[<span data-ttu-id="4e701-137">Środowisko uruchomieniowe .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="4e701-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="4e701-138">Windows Vista z dodatkiem SP2</span><span class="sxs-lookup"><span data-stu-id="4e701-138">Windows Vista SP2</span></span>|[<span data-ttu-id="4e701-139">.NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="4e701-139">.NET Framework 4.6</span></span>](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   > <span data-ttu-id="4e701-140">.NET Framework 4,8 jest preinstalowany w systemie Windows 10 maja 2019 Update.</span><span class="sxs-lookup"><span data-stu-id="4e701-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="4e701-141">Podjęto próbę uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e701-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="4e701-142">W niektórych przypadkach może zostać wyświetlone okno dialogowe podobne do poniższego, które prosi o zainstalowanie .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="4e701-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="4e701-143">Wybierz pozycję **Pobierz i zainstaluj tę funkcję** , aby zainstalować .NET Framework 3,5, a następnie ponownie uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="4e701-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Nie można rozwiązać problemu](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="4e701-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e701-145">See also</span></span>

- [<span data-ttu-id="4e701-146">Wymagania systemowe .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e701-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="4e701-147">Przewodnik instalacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e701-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="4e701-148">Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4e701-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
