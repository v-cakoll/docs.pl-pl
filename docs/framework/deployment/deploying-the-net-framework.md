---
title: "Wdrażanie programu .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b3a33b57ee7cf38e06195244023e8bb918dea02b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="cf06c-102">Wdrażanie programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cf06c-102">Deploying the .NET Framework</span></span>
<span data-ttu-id="cf06c-103">Ta sekcja dokumentacji programu .NET Framework informacje dla deweloperów, którzy chcą zainstalować program .NET Framework z ich aplikacji i administratorów, którzy chcą do wdrożenia programu .NET Framework w sieci.</span><span class="sxs-lookup"><span data-stu-id="cf06c-103">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="cf06c-104">Również w tym artykule omówiono aktywacji i uruchom ponownie problemów związanych z wdrażaniem i jak monitorować postęp instalacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cf06c-104">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf06c-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cf06c-105">In This Section</span></span>  
 [<span data-ttu-id="cf06c-106">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="cf06c-106">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 <span data-ttu-id="cf06c-107">W tym artykule wyjaśniono, jak deweloperzy można zainstalować środowiska .NET Framework na ich komputerów z ich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cf06c-107">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="cf06c-108">Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="cf06c-108">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
 <span data-ttu-id="cf06c-109">W tym artykule wyjaśniono, jak administrator systemu może wdrożenia programu .NET Framework i jego zależności systemu w sieci za pomocą programu System Center Configuration Manager (SCCM).</span><span class="sxs-lookup"><span data-stu-id="cf06c-109">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>  
  
 [<span data-ttu-id="cf06c-110">Zmniejszenie liczby systemu ponownych uruchomień podczas .NET Framework 4.5 instalacji</span><span class="sxs-lookup"><span data-stu-id="cf06c-110">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
 <span data-ttu-id="cf06c-111">Opisano Menedżera ponownego uruchomienia, co uniemożliwia uruchamiany ponownie, jeśli to możliwe i wyjaśniono, jak aplikacje, które Zainstaluj program .NET Framework mogą wykorzystać go.</span><span class="sxs-lookup"><span data-stu-id="cf06c-111">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="cf06c-112">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="cf06c-112">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="cf06c-113">Opisuje sposób dyskretnie uruchamianie i śledzić proces instalacji platformy .NET Framework podczas pokazywania widoku postęp instalacji.</span><span class="sxs-lookup"><span data-stu-id="cf06c-113">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="cf06c-114">Błędy inicjowania programu .NET framework: Zarządzanie wrażeniami użytkownika</span><span class="sxs-lookup"><span data-stu-id="cf06c-114">.NET Framework Initialization Errors: Managing the User Experience</span></span>](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="cf06c-115">Wyjaśniono, co się stanie w przypadku aplikacji .NET Framework wymaga wersji środowiska CLR, która jest nieprawidłowa lub nie jest zainstalowana na komputerze użytkownika, jak rozwiązać te błędy i sterowanie wyświetlony dla użytkownika komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="cf06c-115">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="cf06c-116">Porady: debugowanie problemów aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="cf06c-116">How to: Debug CLR Activation Issues</span></span>](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="cf06c-117">Wyjaśniono, jak można wyświetlać i debugowanie CLR aktywacji dzienniki, aby rozwiązać problemy, które można napotkać podczas pobierania aplikacji do uruchamiania w odpowiedniej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="cf06c-117">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf06c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf06c-118">See Also</span></span>  
 [<span data-ttu-id="cf06c-119">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="cf06c-119">Development Guide</span></span>](../../../docs/framework/development-guide.md)
