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
# <a name="security-changes-in-the-net-framework"></a>Zmiany zabezpieczeń w programie .NET Framework
Najważniejsze zmiany zabezpieczeń w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] w silne nazwy. Zobacz [rozszerzone silne nazewnictwo](../../../docs/framework/app-domains/enhanced-strong-naming.md) opis tych zmian.  
  
 .NET Framework oferuje model zabezpieczeń dwuwarstwowa zarządzanych aplikacji. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje uruchomione w kontenerze zabezpieczeń systemu Windows, który ogranicza dostęp do zasobów. W tym kontenerze pełni zaufany Uruchom zarządzanych aplikacji. Z punktu widzenia zabezpieczeń (CAS) kod dostępu nie ma nic zrobić dewelopera podniesienia uprawnień. Aby uzyskać informacje o uprawnienia przyznane przez system Windows, zobacz [deklaracje możliwości aplikacji (aplikacje ze Sklepu Windows)](http://go.microsoft.com/fwlink/?LinkId=230436) w Centrum deweloperów systemu Windows. Aby uzyskać informacje o tworzeniu [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [tworzenie pierwszej aplikacji Sklepu Windows przy użyciu języka C# lub Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).
