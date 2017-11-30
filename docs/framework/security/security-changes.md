---
title: "Zmiany zabezpieczeń w programie .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: "52"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c1a96e30527aa3da4274ed55059b24aa5a7eeb47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="a28c7-102">Zmiany zabezpieczeń w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a28c7-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="a28c7-103">Najważniejsze zmiany zabezpieczeń w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] w silne nazwy.</span><span class="sxs-lookup"><span data-stu-id="a28c7-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="a28c7-104">Zobacz [rozszerzone silne nazewnictwo](../../../docs/framework/app-domains/enhanced-strong-naming.md) opis tych zmian.</span><span class="sxs-lookup"><span data-stu-id="a28c7-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="a28c7-105">.NET Framework oferuje model zabezpieczeń dwuwarstwowa zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a28c7-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]<span data-ttu-id="a28c7-106">aplikacje uruchomione w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="a28c7-106"> apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="a28c7-107">W tym kontenerze pełni zaufany Uruchom zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a28c7-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="a28c7-108">Z punktu widzenia zabezpieczeń (CAS) kod dostępu nie ma nic zrobić dewelopera podniesienia uprawnień.</span><span class="sxs-lookup"><span data-stu-id="a28c7-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="a28c7-109">Aby uzyskać informacje o uprawnienia przyznane przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze Sklepu Windows)](http://go.microsoft.com/fwlink/?LinkId=230436) w Centrum deweloperów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a28c7-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="a28c7-110">Aby uzyskać informacje o tworzeniu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie pierwszej aplikacji Sklepu Windows przy użyciu języka C# lub Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="a28c7-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
