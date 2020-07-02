---
title: Wdrażanie programu .NET Framework
description: Dowiedz się, jak wdrożyć platformę .NET dla deweloperów, którzy chcą zainstalować program .NET z aplikacjami oraz dla administratorów, którzy chcą wdrożyć platformę .NET w sieci.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
ms.openlocfilehash: 9e9fef2af56ca278b0e326c15546ca9f849a3253
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622773"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="90d8d-103">Wdrażanie programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90d8d-103">Deploying the .NET Framework</span></span>
<span data-ttu-id="90d8d-104">Ta sekcja dokumentacji .NET Framework zawiera informacje dla deweloperów, którzy chcą zainstalować .NET Framework z aplikacjami, a także administratorów, którzy chcą wdrożyć .NET Framework w sieci.</span><span class="sxs-lookup"><span data-stu-id="90d8d-104">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="90d8d-105">Omówiono w nim również problemy dotyczące aktywacji i ponownego uruchomienia związane z wdrożeniem oraz sposób monitorowania postępu instalacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90d8d-105">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90d8d-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="90d8d-106">In This Section</span></span>  
 [<span data-ttu-id="90d8d-107">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="90d8d-107">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)  
 <span data-ttu-id="90d8d-108">Wyjaśnia, w jaki sposób deweloperzy mogą instalować .NET Framework na komputerach użytkowników przy użyciu ich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="90d8d-108">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="90d8d-109">Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="90d8d-109">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)  
 <span data-ttu-id="90d8d-110">Wyjaśnia, w jaki sposób administrator systemu może wdrożyć .NET Framework i zależności systemu w sieci za pomocą usługi Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="90d8d-110">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>  
  
 [<span data-ttu-id="90d8d-111">Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="90d8d-111">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)  
 <span data-ttu-id="90d8d-112">Opisuje Menedżera ponownego uruchamiania, który uniemożliwia ponowne uruchomienie w miarę możliwości, i wyjaśnia, jak aplikacje instalujące .NET Framework mogą korzystać z tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="90d8d-112">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="90d8d-113">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="90d8d-113">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="90d8d-114">Opisuje sposób dyskretnego uruchamiania i śledzenia procesu instalacji .NET Framework podczas wyświetlania własnego widoku postępu instalacji.</span><span class="sxs-lookup"><span data-stu-id="90d8d-114">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="90d8d-115">Błędy inicjowania programu .NET Framework: zarządzanie wrażeniami użytkownika</span><span class="sxs-lookup"><span data-stu-id="90d8d-115">.NET Framework Initialization Errors: Managing the User Experience</span></span>](initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="90d8d-116">Wyjaśnia, co się stanie, gdy aplikacja .NET Framework wymaga wersji środowiska CLR, która jest nieprawidłowa lub niezainstalowana na komputerze użytkownika, jak rozwiązać te błędy i jak kontrolować komunikat o błędzie wyświetlany użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="90d8d-116">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="90d8d-117">Instrukcje: Debugowanie problemów aktywacji środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="90d8d-117">How to: Debug CLR Activation Issues</span></span>](how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="90d8d-118">Wyjaśnia, jak można wyświetlać i debugować dzienniki aktywacji środowiska CLR w celu rozwiązywania problemów, które mogą wystąpić podczas uruchamiania aplikacji z poprawną wersją środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="90d8d-118">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90d8d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90d8d-119">See also</span></span>

- [<span data-ttu-id="90d8d-120">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="90d8d-120">Development Guide</span></span>](../development-guide.md)
