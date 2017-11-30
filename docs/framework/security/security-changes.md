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
# <a name="security-changes-in-the-net-framework"></a>Zmiany zabezpieczeń w programie .NET Framework
Najważniejsze zmiany zabezpieczeń w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] w silne nazwy. Zobacz [rozszerzone silne nazewnictwo](../../../docs/framework/app-domains/enhanced-strong-naming.md) opis tych zmian.  
  
 .NET Framework oferuje model zabezpieczeń dwuwarstwowa zarządzanych aplikacji. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]aplikacje uruchomione w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów. W tym kontenerze pełni zaufany Uruchom zarządzanych aplikacji. Z punktu widzenia zabezpieczeń (CAS) kod dostępu nie ma nic zrobić dewelopera podniesienia uprawnień. Aby uzyskać informacje o uprawnienia przyznane przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze Sklepu Windows)](http://go.microsoft.com/fwlink/?LinkId=230436) w Centrum deweloperów systemu Windows. Aby uzyskać informacje o tworzeniu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie pierwszej aplikacji Sklepu Windows przy użyciu języka C# lub Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).
