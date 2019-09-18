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
ms.openlocfilehash: f4cf91924e762495df6787a187e4295b69f2cd96
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045373"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="6de5a-102">Zmiany zabezpieczeń w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6de5a-102">Security Changes in the .NET Framework</span></span>

<span data-ttu-id="6de5a-103">Najważniejsze zmiany zabezpieczeń w .NET Framework 4,5 są w silnym nazewnictwie.</span><span class="sxs-lookup"><span data-stu-id="6de5a-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="6de5a-104">Aby uzyskać opis tych zmian, zobacz [ulepszona silna nazwa](../../standard/assembly/enhanced-strong-naming.md) .</span><span class="sxs-lookup"><span data-stu-id="6de5a-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
<span data-ttu-id="6de5a-105">.NET Framework zapewnia dwuwarstwowy model zabezpieczeń dla aplikacji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="6de5a-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="6de5a-106">aplikacje działają w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="6de5a-106">apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="6de5a-107">W tym kontenerze aplikacje zarządzane działają w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="6de5a-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="6de5a-108">Z punktu widzenia zabezpieczeń dostępu kodu (CAS) nie ma niczego, aby deweloperzy mogli podwyższyć poziom uprawnień.</span><span class="sxs-lookup"><span data-stu-id="6de5a-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="6de5a-109">Aby uzyskać informacje o uprawnieniach przyznanych przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze sklepu Windows)](https://go.microsoft.com/fwlink/?LinkId=230436) w centrum deweloperów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6de5a-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="6de5a-110">Aby uzyskać informacje na temat [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] tworzenia aplikacji, zobacz [Tworzenie pierwszej aplikacji do sklepu Windows C# przy użyciu lub Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="6de5a-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
