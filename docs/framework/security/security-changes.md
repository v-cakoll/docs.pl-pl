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
ms.openlocfilehash: bfc48d4fed127b288353f0295f2de1ca33e0a8fe
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971209"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="43fe4-102">Zmiany zabezpieczeń w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43fe4-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="43fe4-103">Najważniejsze zmiany zabezpieczeń w .NET Framework 4,5 są w silnym nazewnictwie.</span><span class="sxs-lookup"><span data-stu-id="43fe4-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="43fe4-104">Aby uzyskać opis tych zmian, zobacz [ulepszona silna nazwa](../../standard/assembly/enhanced-strong-naming.md) .</span><span class="sxs-lookup"><span data-stu-id="43fe4-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="43fe4-105">.NET Framework zapewnia dwuwarstwowy model zabezpieczeń dla aplikacji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="43fe4-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="43fe4-106">aplikacje działają w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="43fe4-106">apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="43fe4-107">W tym kontenerze aplikacje zarządzane działają w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="43fe4-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="43fe4-108">Z punktu widzenia zabezpieczeń dostępu kodu (CAS) nie ma niczego, aby deweloperzy mogli podwyższyć poziom uprawnień.</span><span class="sxs-lookup"><span data-stu-id="43fe4-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="43fe4-109">Aby uzyskać informacje o uprawnieniach przyznanych przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze sklepu Windows)](https://go.microsoft.com/fwlink/?LinkId=230436) w centrum deweloperów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="43fe4-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="43fe4-110">Aby uzyskać informacje na temat [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] tworzenia aplikacji, zobacz [Tworzenie pierwszej aplikacji do sklepu Windows C# przy użyciu lub Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="43fe4-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
