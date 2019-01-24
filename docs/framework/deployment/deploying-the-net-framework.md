---
title: Wdrażanie programu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2eb1898f03a52306a8a2763059cf198208b7b88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551842"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="c0d5e-102">Wdrażanie programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c0d5e-102">Deploying the .NET Framework</span></span>
<span data-ttu-id="c0d5e-103">Ta sekcja dokumentacji .NET Framework zawiera informacje dla deweloperów, którzy chcą zainstalować program .NET Framework za pomocą swoich aplikacji i administratorów, którzy chcą wdrożyć program .NET Framework w sieci.</span><span class="sxs-lookup"><span data-stu-id="c0d5e-103">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="c0d5e-104">Również w tym artykule omówiono aktywacji i ponownie uruchom problemów związanych z wdrażaniem i jak monitorować postęp instalacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0d5e-104">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0d5e-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c0d5e-105">In This Section</span></span>  
 [<span data-ttu-id="c0d5e-106">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="c0d5e-106">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 <span data-ttu-id="c0d5e-107">W tym artykule wyjaśniono, jak deweloperzy mogą zainstalować program .NET Framework na komputerach swoich użytkowników przy użyciu swoich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0d5e-107">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="c0d5e-108">Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="c0d5e-108">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
 <span data-ttu-id="c0d5e-109">W tym artykule wyjaśniono, jak administrator systemu może wdrożyć środowiska .NET Framework i jego zależności systemowe przez sieć przy użyciu programu System Center Configuration Manager (SCCM).</span><span class="sxs-lookup"><span data-stu-id="c0d5e-109">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>  
  
 [<span data-ttu-id="c0d5e-110">Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c0d5e-110">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
 <span data-ttu-id="c0d5e-111">W tym artykule opisano Menedżera ponownego uruchamiania co uniemożliwia ponowne uruchomienie, jeśli to możliwe i wyjaśniono, jak aplikacje, zainstaluj program .NET Framework, które można z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="c0d5e-111">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="c0d5e-112">Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c0d5e-112">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="c0d5e-113">Opisuje sposób dyskretnie Uruchom i Śledź proces instalacji programu .NET Framework podczas wyświetlania własnego widoku postępu instalacji.</span><span class="sxs-lookup"><span data-stu-id="c0d5e-113">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="c0d5e-114">Błędy inicjowania programu .NET framework: Zarządzanie wrażeniami użytkownika</span><span class="sxs-lookup"><span data-stu-id="c0d5e-114">.NET Framework Initialization Errors: Managing the User Experience</span></span>](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="c0d5e-115">Wyjaśnia, co się stanie, gdy aplikacja .NET Framework wymaga wersji środowiska CLR, która jest nieprawidłowa lub nie jest zainstalowana na komputerze użytkownika, jak naprawić te błędy i sposobie kontrolowania komunikat o błędzie wyświetlany dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0d5e-115">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="c0d5e-116">Instrukcje: Debugowanie problemów aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="c0d5e-116">How to: Debug CLR Activation Issues</span></span>](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="c0d5e-117">Przedstawia sposób wyświetlić i debugowania dzienniki aktywacji środowiska CLR, aby rozwiązać problemy, które można napotkać podczas pobierania aplikację do uruchamiania w odpowiedniej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c0d5e-117">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d5e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0d5e-118">See also</span></span>
- [<span data-ttu-id="c0d5e-119">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="c0d5e-119">Development Guide</span></span>](../../../docs/framework/development-guide.md)
