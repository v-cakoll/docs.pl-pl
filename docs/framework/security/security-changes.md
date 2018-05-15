---
title: Zmiany zabezpieczeń w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84e80b99ee6d872714180e73354d20770c21e144
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="c3836-102">Zmiany zabezpieczeń w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c3836-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="c3836-103">Najważniejsze zmiany zabezpieczeń w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] w silne nazwy.</span><span class="sxs-lookup"><span data-stu-id="c3836-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="c3836-104">Zobacz [rozszerzone silne nazewnictwo](../../../docs/framework/app-domains/enhanced-strong-naming.md) opis tych zmian.</span><span class="sxs-lookup"><span data-stu-id="c3836-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="c3836-105">.NET Framework oferuje model zabezpieczeń dwuwarstwowa zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3836-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="c3836-106"> aplikacje uruchomione w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="c3836-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="c3836-107">W tym kontenerze pełni zaufany Uruchom zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c3836-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="c3836-108">Z punktu widzenia zabezpieczeń (CAS) kod dostępu nie ma nic zrobić dewelopera podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="c3836-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="c3836-109">Aby uzyskać informacje o uprawnienia przyznane przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze Sklepu Windows)](http://go.microsoft.com/fwlink/?LinkId=230436) w Centrum deweloperów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c3836-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="c3836-110">Aby uzyskać informacje o tworzeniu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie pierwszej aplikacji Sklepu Windows przy użyciu języka C# lub Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="c3836-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
