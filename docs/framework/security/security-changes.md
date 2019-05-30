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
ms.openlocfilehash: 61f9e68bcc554dc3e4a4878e575d3f046a8ef9f5
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378592"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="35901-102">Zmiany zabezpieczeń w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="35901-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="35901-103">Najważniejsze zmiany zabezpieczeń w programie .NET Framework 4.5 jest silne nazwy.</span><span class="sxs-lookup"><span data-stu-id="35901-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="35901-104">Zobacz [rozszerzone silne nazewnictwo](../../../docs/framework/app-domains/enhanced-strong-naming.md) opis tych zmian.</span><span class="sxs-lookup"><span data-stu-id="35901-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="35901-105">.NET Framework oferuje model zabezpieczeń dwuwarstwowej dla zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35901-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] <span data-ttu-id="35901-106">aplikacje działają w kontenerze zabezpieczeń Windows, który ogranicza dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="35901-106">apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="35901-107">W tym kontenerze zarządzane aplikacje są uruchamiane w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="35901-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="35901-108">Z punktu widzenia zabezpieczeń (CAS) kod dostępu nie ma nic zrobić przez dewelopera do podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="35901-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="35901-109">Aby uzyskać informacji na temat uprawnień przyznanych przez Windows, zobacz [deklaracje możliwości aplikacji (aplikacje Windows Store)](https://go.microsoft.com/fwlink/?LinkId=230436) w Centrum deweloperów Windows.</span><span class="sxs-lookup"><span data-stu-id="35901-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="35901-110">Aby uzyskać informacje o tworzeniu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie pierwszej aplikacji Windows Store przy użyciu języka C# lub Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="35901-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
